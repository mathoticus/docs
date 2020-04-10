---
id: glossary
title: Glossary
---

<!--
Notes:
- Synonyms, Not To Be Confused With, and See Also should be omitted when they are empty.
- Avoid links in the definition. Add them to the sections in the note above.
- Definitions should be descriptive but brief. The Glossary is not a tutorial. 
-->

## Active cell

---

## Aggron
The name of the main public testnet for Nervos CKB.

#### Synonyms
- [Testnet](#testnet)

#### Not To Be Confused With
- [Lina](#lina)
- [Mainnet](#mainnet)

---

## Animagus

---

## Args

---

## Axon

---

## Blake2b
A general purpose cryptographic hashing algorithm that created a succinct data fingerprint for any type of data.

#### See Also
- [Blake Hash Function on Wikipedia](https://en.wikipedia.org/wiki/BLAKE_(hash_function))
- [Hash Function on Wikipedia](https://en.wikipedia.org/wiki/Hash_function)

---

## First-Class Assets
A unique property of CKB wherein ownership of a Cell, and the data contained within, is not assigned by the issuer, developer, or smart contract. The user owns the cell and is responsible for costs associated with persistence on CKB.

#### See Also
- [Cell](#cell)
- [Cell Model](#cell-model)
- [First-Class Asset on the Nervos Network Blog](https://medium.com/nervosnetwork/first-class-asset-ff4feaf370c4)

---

## Capacity
The maximum amount of space (in bytes) that a Cell can occupy on the CKB blockchain.

#### Synonyms
- [CKByte](#ckbyte)

#### See Also
- [CKB](#ckb)
- [Common Knowledge Base](#common-knowledge-base)
- [Common Knowledge Byte](#common-knowledge-byte)

---

## Cell
A simple structure used hold a piece of state or data on the Nervos CKB.

A Cell is similar in concept to a Bitcoin UTXO.

#### See Also
- [Dead Cell](#dead-cell)
- [Live Cell](#live-cell)
- [Nervos CKB](#nervos-ckb)
- [UTXO on Bitcoin.org](https://bitcoin.org/en/glossary/unspent-transaction-output)

---

## Cell Model
A representation of how state is managed on Nervos CKB.

#### See Also
- [Cell Model on the Nervos Blog](https://medium.com/nervosnetwork/https-medium-com-nervosnetwork-cell-model-7323fca57571)
- [Lock Script](#lock-script)
- [Nervos CKB](#nervos-ckb)
- [Type Script](#type-script)
- [UTXO on Bitcoin.org](https://bitcoin.org/en/glossary/unspent-transaction-output)

---

## Cell Collection

---

## Cellbase

--- 

## CKB
An abbreviation which can have different meanings depending on the context:

- Common Knowledge Base - The layer 1 blockchain of the Nervos Network.
- Common Knowledge Byte - The native token of the Nervos Common Knowledge Base.

#### Synonyms
- [Common Knowledge Base](#common-knowledge-base)
- [Common Knowledge Byte](#common-knowledge-byte)

---

## CKByte
A shorthand name for Common Knowledge Byte.

CKByte is also sometimes shortened to CKB. Exchanges often use CKB as the ticker symbol.

#### Synonyms
- [CKB](#ckb)
- [Common Knowledge Byte](#common-knowledge-byte)

#### Not To Be Confused With
- [Common Knowledge Base](#common-knowledge-base)

---

## CKB-VM
The virtual machine used to execute Scripts on Nervos CKB.

The instruction set of CKB-VM is RISC-V.

#### See Also
- [Nervos CKB](#nervos-ckb)
- [RISC-V](#risc-v)
- [Script](#script)
- [Virtual Machine on Wikipedia](https://en.wikipedia.org/wiki/Virtual_machine)

---

## Commitment Zone

---

## Common Knowledge Base
A layer 1 proof of work blockchain that serves as the storage persistence layer for the Nervos Network.

#### Synonyms
- [CKB](#ckb)
- [Nervos CKB](#nervos-ckb)

#### Not To Be Confused With
- [Common Knowledge Byte](#common-knowledge-byte)

#### See Also
- [Nervos CKB on Nervos.org](https://www.nervos.org/ckb/)

---

## Common Knowledge Byte
The native token of the Nervos layer 1 blockchain, the Common Knowledge Base.

Common Knowledge Byte is often abbreviated as CKByte or CKB.

Owning a CKByte entitles the holder to store one byte of data on the Nervos CKB.

#### Synonyms
- [CKB](#ckb)
- [CKByte](#ckbyte)

#### Not To Be Confused With
- [Common Knowledge Base](#common-knowledge-base)

#### See Also
- [Capacity](#capacity)
- [Nervos CKB](#nervos-ckb)
- [Shannon](#shannon)

---

## Consume
The process of using a Live Cell as an input to a transaction.

This process of consumption marks the Live Cell as a Dead Cell.

This is the equivalent of marking a UTXO as spent in Bitcoin.

#### See Also
- [Cell](#cell)
- [Cell Model](#cell-model)
- [Dead Cell](#dead-cell)
- [Live Cell](#live-cell)
- [UTXO on Bitcoin.org](https://bitcoin.org/en/glossary/unspent-transaction-output)

---

## Crypto Primitives

---

## Cycles
The number of RISC-V computational cycles required by a script to execute.

This is a similar concept to Ethereum's Gas.

#### See Also
- [Gas on the Ethereum Wiki](https://github.com/ethereum/wiki/wiki/Glossary)
- [Script](#script)
- [RISC-V](#risc-v)

---

## Dead Cell
A Cell that has been consumed and is no longer usable.

#### See Also
- [Cell](#cell)
- [Cell Model](#cell-model)
- [Consume](#consume)

---

## Deps
A shorthand name for dependencies.

#### Synonyms
- [Dependencies](#dependencies)

---

## Dep Group

---

## Dep Type

---

## Dependencies

---

## Eaglesong

---

## Epoch

---

## Generator

---

## Governance Script
A Type Script which defines the monetary policy of a User Defined Token (UDT).

#### See Also
- [Governance Script Hash](#governance-script-hash)
- [UDT](#udt)
- [User Defined Token](#user-defined-token)
- [Type Script](#type-script)

---

## Governance Script Hash
A Blake2b hash of a Type Script which is used as an identifier for the Script when referenced by a Cell.

#### Synonyms
- [Type Script Hash](#type-script-hash)

#### See Also
- [Governance Script](#governance-script)
- [UDT](#udt)
- [User Defined Token](#user-defined-token)
- [Type Script](#type-script)

---

## Historical Cell

---

## Input

---

## Keyper

---

## Layer 1
A proof of work blockchain known as the Common Knowledge Base (CKB) that serves as the storage persistence layer for the Nervos Network.

#### Synonyms
- [CKB](#ckb)
- [Common Knowledge Base](#common-knowledge-base)

---

## Layer 2

---

## Light Client

---

## Lina
The name of public Mainnet of the Nervos CKB.

#### Synonyms
- [Mainnet](#mainnet)

#### Not To Be Confused With
- [Aggron](#aggron)
- [Testnet](#testnet)

---

## Live Cell
A Cell that has not been consumed and is available for use.

This is similar to an unspent transaction output (UTXO) in Bitcoin.

#### See Also
- [Cell](#cell)
- [Cell Model](#cell-model)
- [UTXO on Bitcoin.org](https://bitcoin.org/en/glossary/unspent-transaction-output)

---

## Lock Script
A Script that enforces access and ownership of a Cell. This Script controls who has permission to use the Cell as an input. 

#### See Also
- [Cell](#cell)
- [Type Script](#type-script)
- [Script](#script)

---

## Lock Script Hash
A Blake2b hash of a Lock Script which is used as an identifier for the Script when referenced by a Cell.

---

## Long Address

---

## Mainnet
The public blockchain of the Nervos CKB.

The name of the Nervos CKB Mainnet is Lina.

#### Synonyms
- [CKB](#ckb)
- [Common Knowledge Base](#common-knowledge-base)
- [Lina](#lina)
- [Nervos CKB](#nervos-ckb)

#### Not To Be Confused With
- [Aggron](#aggron)
- [Testnet](#testnet)

---

## Molecule

---

## Muta Framework

---

## Nervos CKB
The layer 1 blockchain of the Nervos Network, the Common Knowledge Base.

#### See Also
- [Common Knowledge Base](#common-knowledge-base)

---

## Nervos DAO

---

## Off-Chain State

---

## Off-Chain Computation

---

## On-Chain State

---

## Open Transaction

---

## Outpoint

---

## Output

---

## Proposal Zone

---

## RISC-V
An open standard instruction set architecture (ISA) for general computing.

#### See Also
- [CKB-VM](#ckb-vm)
- [RISC-V on Wikipedia](https://en.wikipedia.org/wiki/RISC-V)

---

## Script
A program that executes on the CKB-VM. A Script can be one of two types:

- Lock Script - Used to control ownership and access to a Cell.
- Type Script - Used to control how a Cell is used in a transaction.

A Script is a binary executable in the ELF format for the RISC-V architecture.

#### See Also
- [CKB-VM](#ckb-vm)
- [ELF on Wikipedia](https://en.wikipedia.org/wiki/Executable_and_Linkable_Format)
- [Lock Script](#lock-script)
- [RISC-V](#risc-v)
- [Type Script](#type-script)

---

## Secondary Issuance

---

## Shannon
A fractional denomination of CKBytes. One CKByte is equal to 100,000,000 Shannons.

A Shannon is the equivalent of a Bitcoin Satoshi.

#### See Also
- [CKByte](#ckbyte)
- [Common Knowledge Byte](#common-knowledge-byte)
- [Satoshi (denomination) on Bitcoin.org](https://bitcoin.org/en/glossary/denominations)

---

## Since

---

## State Rent

---

## Store of Value

---

## SUDT

---

## Testnet
The public blockchain of the Nervos CKB used for testing purposes. All tokens and data on the testnet have no value.

The name of the Nervos CKB Testnet is Aggron.

#### Synonyms
- [Aggron](#aggron)

#### Not To Be Confused With
- [Lina](#lina)
- [Mainnet](#mainnet)

---

## Transaction

---

## Type ID

---

## Type Script
A Script that enforces the rules that must be followed in a transaction for a Cell to be consumed as an input or for a Cell to be created as an output.

#### See Also
- [Cell](#cell)
- [Lock Script](#lock-script)
- [Script](#script)
- [Type Script Hash](#type-script-hash)

---

## Type Script Hash
A Blake2b hash of a Type Script which is used as an identifier for the Script when referenced by a Cell.

#### See Also
- [Cell](#cell)
- [Script](#script)
- [Type Script](#type-script)

---

## UDT
An abbreviation of User-Defined Token.

#### Synonyms
- [User-Defined Token](#user-defined-token)

---

## User-Defined Token
A unique non-fungible token with properties defined by the user.

A UDT is equivalent of an Ethereum ERC20 token or ER777 token.

#### See Also
- [ERC20 on Ethereum.org](https://eips.ethereum.org/EIPS/eip-20)
- [ERC777 on Ethereum.org](https://eips.ethereum.org/EIPS/eip-777)

---

## Validator

---

## Witness

---
