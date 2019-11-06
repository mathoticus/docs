---
id: nervos-intro
title: What is Nervos?
---

The Nervos Network is infrastructure to support a future cryptoeconomy, where users' assets are represented by different kinds of cryptographic tokens and are traded in a financial system that is open and programmable. In such a world, trading friction between assets is lowered and resources can be allocated faster and more efficiently. In essence, a better world.

To realize this vision, we will need a blockchain to securely store users' assets (tokens). This blockchain also has to be programmable, so that we can design different tokens and transact them intelligently.

The mission of Nervos is to build this infrastructure.

![nervos-log](assets/nervos-layers.png)

The Nervos Network is constructed with a layered architecture, consisting of a single Layer 1 blockchain, as well as many Layer 2 systems. The Layer 1 blockchain is the Nervos Common Knowledge Base (CKB), from which developers can construct their own Layer 2 systems secured by CKB and interact with CKB. The CKB is designed to prioritize security and decentralization, while Layer 2 systems focus on functionality, performance and scalability.

> To learn more about the layered architecture of Nervos, please refer to [Nervos CKB RFC](https://github.com/nervosnetwork/rfcs/blob/master/rfcs/0002-ckb/0002-ckb.md).

The native currency of the Nervos Network, is the CKByte. Users use CKBytes to store data on the blockchain, and they are required to issue and store assets. This token also secures the blockchain system by providing incentives (in the form of block rewards) to miners.

> To learn more about the CKBytes, please refer to [Nervos Cryptoeconomics RFC](https://github.com/nervosnetwork/rfcs/blob/master/rfcs/0015-ckb-cryptoeconomics/0015-ckb-cryptoeconomics.md).

> CKB is both the token name and the name of the Layer 1 blockchain.


## Nervos CKB

The Nervos Common Knowledge Base (CKB) is a permissionless public blockchain system. On the CKB platform, both the Native Token(CKB) and the User Defined Tokens (UDT) can be programmed with Turing complete scripts.

In a blockchain context, common knowledge refers to states verified by global consensus. The role of Nervos CKB is to verify state and store state on-chain, where the state will be secure and censorship resistant.

Comparing with Bitcoin, which was designed to be programmable money, CKB is designed to be a programmable asset platform.

Ethereum was designed to be a world computer that supports a programmable escrow account. On Ethereum, you can also program the behavior of non-custodian accounts (i.e. smart contracts) to make UDTs such as ERC20 or ERC721. Comparatively, CKB supports the same functionality but lets users program the operation of assets directly (without going through an account), conveying benefits when users are interacting with Layer 2 solutions or Decentralized Exchanges (DEXs).


## CKB Features

Here we introduce features of CKB that make it different from other public blockchain platforms.

### Nakamoto Consensus Max
Nervos CKB adopts an improved Nakamoto Consensus algorithm called NC-Max as the consensus mechanism. NC-Max uses orphan block rate as an on-chain network bandwidth status indicator and dynamically adjusts the block interval to achieve better network bandwidth efficiency and make selfish mining unprofitable.

To learn more about NC-Max, please refer to [this presentation video](https://www.youtube.com/watch?v=HSXzbgVRH_M).

### Cell Model

Nervos CKB adopts a generalized UTXO model called the Cell model for its state model. A Cell is a representation of CKBytes in practice, just like the UTXO is the representation of BTC. Cells are also containers for storing state on-chain, cells can be used to create and program user-defined tokens.

You can find this concept explained in detail in a [latter section](../basic-concepts/architecture.md#cell), or you can refer to the [Nervos Whitepaper](https://github.com/nervosnetwork/rfcs/blob/master/rfcs/0002-ckb/0002-ckb.md) where you can find a high-level comprehensive explanation.

### RISC-V Based CKB-VM
CKB-VM is a virtual machine designed for the CKB blockchain. It is a software simulator based on the [RISC-V](https://riscv.org/) instruction set. With CKB-VM, programming is supported in any language that has a RISC-V compiler, such as C/C++, as well as high-level programming languages such as Javascript, Python, and Ruby. Moreover, CKB-VM allows for permissionless deployment of any hash function or signature function on-chain, allowing developers to define their own private key verification function for assets/tokens, instead of being limited by a set of predefined crypto primitives.

To learn more about CKB-VM, please refer to [Nervos CKB-VM RFC](https://github.com/nervosnetwork/rfcs/tree/master/rfcs/0003-ckb-vm).

### Token Economics
The CKB economic model is focused on state, with the native CKByte token representing rights to occupy state storage. For example: holding 1000 CK Bytes would allow a user to create a Cell with 1000 bytes in capacity, or multiple Cells that add up to 1000 bytes in capacity.

Owners utilize their CKBytes to store state, or can lend CKBytes to others. While CKBytes are being used to store data on CKB, they will lose some value to inflation that is paid to miners securing the platform. Users can at anytime remove the state from the blockchain and lock their CKBytes in the NervosDAO to receive these inflation rewards and preserve the value of their CKBytes. 

To learn more about the CKB token economics, please refer to [Nervos Cryptoeconomics RFC](https://github.com/nervosnetwork/rfcs/blob/master/rfcs/0015-ckb-cryptoeconomics/0015-ckb-cryptoeconomics.md).
