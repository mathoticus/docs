---
id: node-mining
title: Node and Mining
---

Here we will introduce the concepts of node and mining in CKB.

### Node
CKB is structured as a peer-to-peer network on top of the existing internet. Here the term "peer-to-peer" means that all the computers that participate in the network are peers to each other. In this context, we refer to each of these computers as a node.

Every computer in this world that has sufficient capability (this basically means all modern computers) would be able to run a CKB node and join the CKB network freely. 

Being a node in the network means you will synchronize the existing blocks, transactions, and states as well as receive new ones from other peer nodes. You will also be able to verify transactions and broadcast your own transactions to other nodes.

### Mining

Miners are a kind of node that constructs new blocks with a set of transactions in it. 

In CKB, miners need to compete with each other in a game called Proof-of-Work. After a miner constructs a block, the miner will need to calculate the hash of the block (with a nonce) to get a hash that is smaller than a specific target number (difficulty). Whoever successfully figures out the correct hash will have the right to broadcast the new block to the whole network. Other nodes will receive the block, verify it, and start to mine a new block on top of it.

> The hash function for CKB mining has not been decided yet.


