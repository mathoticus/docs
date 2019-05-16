---
id: architecture
title: CKB Architecture
---

![data-structure](assets/ckb-structure.png)



There are four major data structures in CKB: Cell, Transaction, Script, and Block. You can find detailed explanations of each of them in [RFC#0019](https://github.com/nervosnetwork/rfcs/blob/master/rfcs/0019-data-structures/0019-data-structures.md).

 
## Cell

> More information about the 'Cell' data structure can be found in the [Nervos whitepaper](https://github.com/nervosnetwork/rfcs/blob/master/rfcs/0002-ckb/0002-ckb.md#42-cell).

Cell is the most basic element in CKB system. A cell can be used to store state or a script. 

A state cell may contain the data of an application or a UDT (User-Defined-Asset), such as the balance of a user's UDT. A script cell may contain the logic of an application or the rules of a UDT, such as a rule that states the balance of a UDT cannot be negative. 

> It is possible to store both the state and logic of an application in a single cell, but if the application wants to leverage the power of [layer2 solutions](https://github.com/Awesome-Layer-2/Awesome-Layer-2), this is not recommended. This design pattern may result in the same problem of [why it is hard to implement EVM on Plasma](https://medium.com/@kelvinfichter/why-is-evm-on-plasma-hard-bf2d99c48df7).


In a single cell, the `capacity` field limits the size of this cell. The `data`, `type` and `lock` are the three fields a developer needs to consider about when designing an application. 
* `data` stores the data of state or scripts. 
* `type` defines the type of cell by defining how the `data` field can be modified. 
* `lock` defines the ownership of a cell. 

We will explain how these fields operate together in the following section.

## Transaction

> More information about the 'Transaction' data structure of Nervos CKB can be found in [whitepaper](https://github.com/nervosnetwork/rfcs/blob/master/rfcs/0002-ckb/0002-ckb.md#44-transaction).

### Structure
Transaction is for updating the cells on-chain (i.e., the state on-chain). Each transaction has a group of input cells (existing states) and a group of output cells (new states). A transaction should be sent to a CKB node for verification and confirmation by the whole blockchain system, so that the new cells can become valid on-chain.

> This is a different transaction process than that of Ethereum, in which transactions only contain events that will initiate a state transition of data that is stored on-chain. After receiving a transaction, an Ethereum node would calculate the new state based on the transaction data and the old state on the blockchain, and then replace the old state with the newly calculated state. This basically means that Ethereum generates state on-chain, while state generation on CKB is an off-chain process.

To assemble a transaction, three fields need to be filled in: input cells (`inputs`),  output cells (`outputs`), and dependency cells (`deps`). Now let's talk about how a transaction is verified, and hope it can help you to make sense of how these three fields should be filled in.

### Transaction Verification

> [Here is an RFC](https://github.com/nervosnetwork/rfcs/pull/80) that lists all the transaction verification rules defined by the CKB protocol.

After a CKB node receives a transaction, the transaction will be first validated against rules defined by the CKB protocol, such as 'the sum capacity (in bytes) of output cells should be lower or equal to sum capacity of input cells'.

> The sum capacity difference of input and output cells are collected by the miner as mining fees. It is also possible to pay mining fees with UDTs as long as a miner agrees to accept the UDT as a means of fee payment.

Another example validation rule is 'only live cells can be used as transaction inputs'. Cells can either be: live (unspent) or dead (spent). After a transaction is mined and confirmed on-chain, the input cells become "dead", and the output cells are issued the status of "live". This is the mechanism that prevents double-spending on CKB.


## Scripts

Apart from the validation rules of the CKB, a transaction also needs to pass validation logic specified by the `lock` script of the input cells and the `type` script of the output cells. This part is crucial to understanding how to define the transition behavior of the on-chain state.

### `lock` script
As mentioned above, the `lock` script defines the ownership of a cell. 

In a transaction, there is a group of `inputs`, input cells. Each of the `inputs` has two values: an input cell and an array of `args`. 

> The input cell here is actually named as `previous_output`. It is an outpoint that points to a previous transaction's output cell. This is analogous to Bitcoin's UTXO.

In the transaction, there is also a field named `witnesses`, which is an array of witnesses that correspond to each of the `inputs`. This field is for implementing [SegWit protocol](https://en.bitcoin.it/wiki/Segregated_Witness) that can help to solve the [malleability problem](https://en.bitcoin.it/wiki/Transaction_malleability).

Upon transaction verification, the `lock` script will be executed with the `args` in `inputs` and the corresponding witness arguments in `witnesses`. Only after the script is successfully executed (returns 0), will the transaction be recognized as valid.

A typical `lock` script may contain the information of the public key of the cell owner. To unlock the cell, the user would need to provide a signature of the transaction in the `witnesses` part. In this case, during the verification process, the `lock` script recovers the signature and verifies it matches the stored public key, ensuring the transaction is indeed signed by the owner of the input cells.

> The signature function and the hash function used by `lock` script (or `type` script) is not defined by CKB protocol. Developers are free to design and implement their own signature functions in the `lock` script.

### `type` script

`type` script defines how the `data` of a cell can be modified. In a transaction, when a group of input cells and output cells have  the same `type` field value, the modification of the `data` fields from input cells to output cells must comply with the rules defined by the `type` script. 

For example, Alice has a cell, with a `data` field that stores the balance of a particular UDT, with a `type` script that defines the rules and logic of this UDT. If Alice wants to send some of this UDT to Bob, she would use this cell as an input cell, and include another cell with the exact same `type` field as an output cell, but use Bob's `lock` script for the output cell. Alice can then assemble the transaction and send it to the CKB node. (Alice would need to include another output cell for herself as change) 

### Script Verification

After receiving the transaction, the CKB node would first verify the `lock` script with the `args` of the input cell, as well as the `witness`, to make sure that Alice indeed owns the cell. The node would then verify the `type` script of the output cell, which is same as the `type` script of the input cell, to make sure the UDT transaction is valid according to the rules defined by the `type` script.


> In practice, the script's code is NOT included in the `type` or `lock` field directly. The actual code would be stored in another cell and that is referred to by hash in the `type` and `lock` fields . This is accomplished by referring to these required cells in the dependency cells field (`deps`) in the transaction using their `outpoint`, and including the hash of their `data` fields in the `code_hash` field of `type` or `lock`.


During the verification process, the specified scripts are loaded and executed in a CKB-VM instance. Check the [CKB-VM RFC](https://github.com/nervosnetwork/rfcs/tree/master/rfcs/0003-ckb-vm) to learn more about how this works in the CKB-VM.


To learn more about how to write `script` in practice, please refer [write script section](../dev-guide/scripts).


## Block

Block contains a pack of transactions and a block header with some meta-data. It is the miner's job to pack transactions into a block and do the Proof-of-Work calculation to find a "seal" to seal the block, then broadcast it to the whole network. Other miners would receive this block, verify it, collect transactions and start to mine a new block based on this received block. 

In CKB, a block also contains the information of uncle blocks in the block structure. Block includes the complete uncle block header as well, as part of the transaction information. Please refer to the [RFC#0019](https://github.com/nervosnetwork/rfcs/blob/master/rfcs/0019-data-structures/0019-data-structures.md#uncleblock) for more details.


### Computing Cycles and Transaction Size

There are two limitations for miners to consider when selecting transactions to pack into a block: computing cycles and transaction size.

In CKB, computation resources consumed by transaction verification, specifically the script's execution, is measured with `cycles`. Each instruction in CKB-VM may [cost different cycles](https://github.com/nervosnetwork/rfcs/blob/master/rfcs/0014-vm-cycle-limits/0014-vm-cycle-limits.md#instruction-cycles). The sum cycles cost by all scripts executed in transaction verification in a block is limited to a value defined by the CKB protocol called `MAX_BLOCK_CYCLES`.

The size of a transaction is measured in bytes. The sum size of all the transactions in a block should be lower than `MAX_BLOCK_BYTES`.
