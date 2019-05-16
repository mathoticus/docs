---
id: nervos-intro
title: What is Nervos?
---

Nervos envisions a decentralized economy, where users' assets are represented by different kinds of tokens that are traded in an open and programmable financial system. In this world, the friction of trading different assets is significantly lower than traditional systems and resources are allocated more faster and more effectively, eventually making the world a better place.

Realizing this vision will require infrastructure to securely store users' assets (tokens), as well as making them programmable. This provides the ability to design different types of tokens and the means to transact with them intelligently.

The mission of Nervos is to build this infrastructure.

![nervos-log](assets/nervos-layers.png)

Nervos has a layered architecture, with a single Layer 1 and many Layer 2 systems. Layer 1 is referred to as the 'Common Knowledge Base' or CKB, which is focused on providing security and decentralization. Developers are able to construct their own Layer 2 systems, focused on functionality and performance, utlizing the CKB to provide underlying security and interoperability with other protocols running on CKB.

> To learn more about the layered architecture of Nervos, please refer to [Nervos Whitepaper](https://github.com/nervosnetwork/rfcs/blob/master/rfcs/0002-ckb/0002-ckb.md).

In Nervos, there is a utility token named CKB (or CK Bytes) that represents rights to store data on CKB. Issuing or storing any asset on the CKB requires holding an appropriate amount of the CKB token. For example, 100 CKB would allow a user to store 100 bytes on the blockchain. Issuance of this token also secures the blockchain, incentivizing miners to compete for block rewards.

> To learn more about the CKB token, please refer to [Nervos Token Economics paper](https://github.com/nervosnetwork/rfcs/blob/master/rfcs/0015-ckb-cryptoeconomics/0015-ckb-cryptoeconomics.md).

> CKB is both the token name and the name of the Layer 1 blockchain.

## Nervos CKB

The Nervos Common Knowledge Base (CKB) is a permissionless public blockchain. On the CKB platform, both the Native Token (CKB) and User Defined Tokens (UDT) can be programmed with Turing-complete scripts.

In a blockchain context, 'common knowledge' refers to states verified by global consensus. Similar to Bitcoin, Nervos CKB is designed to be a state verification system.

Comparing with Bitcoin, which was designed to be programmable money, CKB is designed to be a programmable assets platform. User Defined Tokens (UDTs) can be programmed with Turing complete scripts the same way the CKB token can be.

Ethereum was designed to be a world computer that provides the function of a programmable escrow account. On Ethereum, users can program the behavior of non-custodian accounts (i.e. smart contracts) to make UDTs such as ERC20 or ERC721 tokens. In contrast, CKB allows users to program tokens directly, without going through an account. This design philosophy creates a new programming model, which will be cover in later parts of this documentation.


## CKB Features

Here we introduce features of CKB that make it different from other public blockchain platforms in terms of the protocol design.

### Nakamoto Consensus Max
Nervos CKB adopts an improved Nakamoto Consensus algorithm called NC-Max as the consensus mechanism. NC-Max uses orphan block rate as an on-chain network bandwidth status indicator and dynamically adjusts the block interval to achieve better network bandwidth usage efficiency, as well as making selfish mining unprofitable.

To learn more about NC-Max, please refer to [this presentation video](https://www.youtube.com/watch?v=HSXzbgVRH_M).

### Cell Model

Nervos CKB adopts a generalized UTXO model called the 'Cell model' for describing and programming both the native token CKB and User Defined Tokens (UDT).

You can find this concept explained in a [latter section](../basic-concepts/architecture.md#cell), or you can refer to the [Nervos Whitepaper](https://github.com/nervosnetwork/rfcs/blob/master/rfcs/0002-ckb/0002-ckb.md) where you can find a high-level comprehensive explanation.

### RISC-V Based CKB-VM
CKB-VM is a virtual machine designed for the CKB blockchain. It is a software simulator based on the [RISC-V](https://riscv.org/) instruction set. With CKB-VM, you can program in any language that has a compiler supported by RISC-V, such as C/C++ and other high-level programming languages such as Javascript, Python, and Ruby. Moreover, with CKB-VM you can execute any kind of hash function or signature function on-chain, meaning you will be able to define your own private key verification function for your assets/tokens, instead of being limited by a set of predefined crypto primitives.

To learn more about CKB-VM, please refer to [CKB-VM paper](https://github.com/nervosnetwork/rfcs/tree/master/rfcs/0003-ckb-vm).

### Token Economics
The CKB economic model focuses on the state. The native token (CK Bytes) represents rights to occupy state storage. For example: holding 1000 CK Bytes would allow the user to create a cell with 1000 bytes in capacity, or multiple cells that add up to 1000 bytes in capacity.

Owners utilize their CK Bytes to store state or can lend capacity to others. To resolve the long-standing 'state bloat' problem, CKB utilizes targeted inflation. A secondary issuance is issued to miners along with block rewards, if a user holds CK Bytes and is utilizing them to store data on the CKB, their portion of the secondary issuance will go to the miners. 

If a user holds CK Bytes but is not utilizing them to store data on the CKB, these tokens can be locked in the onchain NervosDAO and the owners can then receive a proportional share of the secondary issuance. This inflation model creates an implicit storage cost proportional to space and time if an owner utilizes their cell to store state.

To learn more about the CKB token economics, please refer to [token economics paper](https://github.com/nervosnetwork/rfcs/blob/master/rfcs/0015-ckb-cryptoeconomics/0015-ckb-cryptoeconomics.md).
