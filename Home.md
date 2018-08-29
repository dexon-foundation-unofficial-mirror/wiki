DEXON Comparison to Other Blockchain 
==
### Introduction
This document explains how DEXON is different compared to other blockchain infrastructures. We do our best to explain the main differences, but still, we have the following principles:
1. We will not dive into details of other projects. We only focus on the differences. For the details, please refer to their websites and whitepapers.
2. The comparison is based on our up-to-date understanding, and projects can be updated frequently. We will update this document if necessary.

### Definition
- Node in this document is a validator or a full node in the network.
- DAG-blocklattice: a DAG that every vertex has at least one edge and will not diverge (DAG width remains proportional to number of nodes)
- DAG-tangle-lattice: a DAG that every vertex has exactly two edges and will not diverge
- DAG-tangle: a DAG that every vertex has exactly two edges
- <img src="https://latex.codecogs.com/svg.latex?T_{network}" />: network delay between nodes
- <img src="https://latex.codecogs.com/svg.latex?n" />: number of nodes
- <img src="https://latex.codecogs.com/svg.latex?b" />: number of blocks to be confirmed
- <img src="https://latex.codecogs.com/svg.latex?f" />: ack frequency
- For smart contract column:
    - O: Supprted
    - X: Not supported
    - △: Not supported for now, but is able to support
### Contents
- [DEXON](#dexon)
- [Algorand](#algorand)
- [Bitcoin](#bitcoin)
- [Cardano](#cardano)
- [Dfinity](#dfinity)
- [EOS](#eos)
- [Ethereum](#ethereum)
- [Hashgraph](#hashgraph)
- [Hyperledger](#hyperledger)
- [IOTA](#iota)
- [NANO](#nano)
- [Omniledger](#omniledger)
- [Phantom](#phantom)
- [Snowflake](#snowflake)
- [Spectre](#spectre)
- [Stellar](#stellar)
- [Tendermint](#tendermint)

## DEXON
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|1M+|2|DAG-blocklattice|total ordering|O|

DEXON is a scalable, low-latency, energy efficient and inter-chain operable DApp ecosystem. DEXON uses total ordering as its main consensus algorithm, of which throughput can scale linearly with the number of nodes while latency remains nearly constant. Instead of processing blocks sequentially like traditional blockchain, DEXON blocklattice data structure processes blocks in parallel. With such high throughput and low latency, practical DApp can finally be developed and widely-used. 

## Algorand
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|875|< 60|chain|Byzantine agreement|△|

Algorand is designed for large population ( ~ 500K nodes). They use a verifiable random function to protect nodes from DDos attack, and it is the lottery that decides who have the right to propose a block or to vote for each round. 

The consensus of Algorand is based on Byzantine agreement among samples from the whole set of nodes. This is the reason why Algorand can only tolerate less than one third of total number of nodes. For example, if it sets 1/5 as maximum ratio of Byzantine nodes among all nodes, the ratio of Byzantine nodes in samples can be bounded by 1/3 with high probability.

They use gossip mechanism that costs a latency of <img src="https://latex.codecogs.com/svg.latex?O(log(n))*T_{network}" /> for each message, which means its confirmation time becomes longer when the number of nodes increases and scatters around the world. With this limitation, the confirmation time will be around one minute if the number of nodes is expected to be 500K. Another factor that will affect the confirmation time is Byzantine behavior. If a Byzantine node wins the lottery and becomes a leader, the process of Byzantine agreement will need more round to converge. On the other hand, DEXON's confirmation time is not affcted by Byzantine behavior as long as the number of Byzantine nodes is less than one third of total nodes. 

If Algorand wants to increase its throughput, it must increase block size. However, increasing block size causes a longer network delay, increasing the confirmation time. This means Algorand is lack of scalability. On the other hand, DEXON increases throughput by means of increasing the number of nodes without affecting the confirmation time. 

## Bitcoin
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|7|3600|chain|longest chain rule|X|

Bitcoin is the first cryptocurrency that starts the era of blockchain. It is the most well-known and widely used cryptocurrency. However, it is infamous for its long confirmation time, low TPS and high transaction fee. DEXON solves all of them and at the same time provides DApp functionality, which Bitcoin does not have.

## Cardano
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|250|300|chain|Ouroboros|O|

Cardano is the first project that provides a concrete mathematical proof on security of PoS blockchain. Besides PoS, they also proposes other promising ideas such as unbiased randomness with commit-reveal scheme and using Nash Equilibrium to prevent selfish mining attack. However, its chain-based structure naturally limits its throughput, since chain-based structure can only process block linearly, and can be proved that it can not scale.

Another problem in Cardano consensus is that it highly depends on time synchronization. If some honest nodes are desynchronized (for example, NTP service hijack by an attacker), they don't know when is the starting time of a slot and will be treated as fail-stop node. They claimed desynchronized nodes can be corrected by some method introduced in the future, but it is not implemented yet.

## Dfinity
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|500 ~ 1000|5 ~ 10|dual-chain|Dfinity|△|

Dfinity is a permissioned blockchain and is designed for large population (around 10K of nodes). Dfinity contains a randomness beacon which generates new randomness by a VRF (verifiable random function) with information from new confirmed block. They use the randomness to select a leader and electors for a round. By hypergeometric distribution, Dfinity only samples hundred of nodes to notary a block instead of using all nodes, and this is correct with high probability. But this reduces the tolerance ability to Byzantine nodes. For example, to achieve the majority of nodes is non-Byzantine with probability less than <img src="https://latex.codecogs.com/svg.latex?2^{-40}">, it needs to sample at least 423 nodes from 10K nodes with maximum 1/3 Byzantine nodes.
However, Dfinity is chain-based, so its throughput is limited.

## EOS
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|100K|165|chain|longest chain & Byzantine fault tolerance|O|

EOS reaches high throughput and low latency. They have 21 so-called "supernodes", which are considered not decentralized. Also, at the time of writing, its Byzantine fault tolerance consensus is not implemented yet, so the confirmation time is about 165 seconds, not 1 or 2 seconds as they claimed.

## Ethereum
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|20|360|chain|longest chain|O|

Ethereum is the first blockchain system that has a complete DApp ecosystem. It has a throughput higher and latency lower than Bitcoin, but still not enough for daily usage such as payment or gaming. A popular DApp can block the whole system, causing high transaction fee. Also, the latency now (several minutes) is not acceptable for real-time application. 

## Hashgraph
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|200K|20|DAG-tangle-lattice|Hedera|O|

The consensus of Hashgraph is adapted Byzantine agreement on graph. Their round-based structure costs a latency of <img src="https://latex.codecogs.com/svg.latex?O(log(n))*T_{network}" /> for each round, which means its confirmation time becomes longer when the number of nodes increases. With this limitation, it cannot be fully decentralized, or the confirmation time can be minutes. Also, the liveness is not guaranteed and proved in Hashgraph. Only security proof is provided. With Byzantine nodes presented in its network, it is possible that Hashgraph does not output any block. Meanwhile, DEXON's confirmation time remain constant when the number of nodes increases.

## Hyperledger
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|4K|< 1|chain|Pluggable|O|

Hyperledger (specifically, Hyperledger Fabric) is a distributed ledger designed for enterprise use. It should be permissioned, low-latency, high-throughput and provides private transaction functionalities. Its consensus is modularized and pluggable. It can choose among consensus engines/algorithms such as Tendermint, PBFT, Kafka ordering or RAFT.

It is much easier to address consensus problem in a permissioned settings with high throughput and low latency. There is no strong Byzantine participants, and network environment is stable and fast. It does fit for enterprises to use such settings, while DEXON aims to be more open and decentralized, providing high throughput and low latency at the same time.

## IOTA
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|500 ~ 800|> 180|DAG-tangle|longest chain rule|X|

IOTA follows the longest chain rule on a graph: a node randomly chooses and verifies two previous blocks and attaches its block to them. A block is confirmed if enough number of blocks follow it and the length of the connected chain is the longest.
However, the rule is inefficient because the confirmation time is not guaranteed by a specific bound. Moreover, a block might be invalid if it is attached to a block that contains conflict transaction. That block has to be re-attached to other blocks. This causes a very long confirmation time. Furthermore, IOTA does not support smart contract due to the lack of total ordering among all blocks. 

## NANO
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|7000|1|DAG-tangle-lattice|DPoS|X|

NANO is the first project that introduces blocklattice as their data structure. Each account has its own blockchain, and a transaction it proposed is recorded on its blockchain. When a blockchain fork happens, NANO starts a DPoS voting to resolve it.

DEXON's blocklattice is completely different from NANO's. In DEXON, instead of every account having its own blockchain, each validator has a blockchain. This could save a lot of memory space. In our blocklattice, each vertex is a block, while in NANO, each vertex is half of a transaction (send tx or recv tx). From our view point, their blocklattice is more like "tx-lattice", not blocklattice, and we consider blocklattice a general term that can be used by other projects, just like blockchain, since it is just a type of DAG. 

DEXON's consensus algorithm is also completely different from NANO's. We use total ordering algorithm to decide order of blocks and transactions, while NANO does not have consensus on order of transactions. Without ordering transactions, it can not support smart contract. Another problem is its DPoS to resolve fork. The voting process NANO used to resolve fork is mysterious. In its whitepaper, there is no detail about the voting process. The only thing we know is a majority voting with 4 rounds. Without further detail and security proof, we find it hard to believe that NANO is secure. Also, NANO needs PoW to prevent spam (penny) attack, increasing the cost of attack but also limiting its throughput and increasing its latency.  

## Omniledger
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|6K|10|chain|ByzCoinX|△|

Omniledger aims to solve scalability problem without sacrificing security and decentralization. Its main approach is sharding, which allows the throughput to scale linearly with the number of nodes. Omliledger also provides nice features such as ledger pruning, cross-shard transaction and trust-but-verify validation.

The problem of Omniledger is that its latency could be large in a fully decentralized setting. The reason is that it uses ByzCoinX (which is an optimization of PBFT-like consensus algorithm) for intra-shard consensus and Atomix (DB-like atomic broadcast) for inter-shard transaction. This means the group size in a shard for communication can not be too large, or the communication cost and latency will be large. To increase the number of nodes with limited shard size, number of shards will increase, and the needs for cross-shard transaction will also increase. With atomic broadcast, a cross-shard transaction has to wait for every involved shard to be confirmed, and even a single shard failed will cause the transaction to fail. In DEXON, transaction only needs to enter one shard and will be output immediately. 

Omniledger also sacrifice some of the security. According to hypergeometric distribution, if the sampled Byzantine nodes in a shard must be less than one third, one can only tolerate Byzantine nodes much less than one third in the whole network, or sampling can not be success with high probability. This is why the number of Byzantine nodes Omniledger can tolerate is one fourth, not one third of total nodes. 

## Phantom
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|NA|NA|DAG-blocklattice|greedy selection algorithm|△|

Phantom is a DAG-based blockchain which is generalized from Bitcoin's longest chain rule on a chain to a DAG. Phantom is a proposal for Spectre, and they proposed a greedy algorithm called ghostDAG protocol to achieve total ordering. However, they didn't proof the correctness and liveness of their algorithm or provide the simulation results about Phantom in the distributed setting. A liveness attack on Phantom was individually proposed by the work from Li et al. and the work from Kiayias and Panagiotakos. They also claimed they will try to combine Phantom and Spectre in the future. We will update the information if they provide new and correct results. 

On the other hand, the total ordering in DEXON consensus is guaranteed. Moreover, the correctness and liveness of DEXON consensus are both proved.
## Snowflake
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|1300|4|DAG-blocklattice|Avalanche|△|

Snowflake consensus starts from a simple coloring method, adds additional counters and rules, and finally ends up a provably probabilistically secure consensus algorithm, Avalanche. All nodes converge to the same color, which means that they will agree on the same transaction set when conflict happens.

To resolve conflict transactions, nodes need to execute Avalanche algorithm on every transaction in a conflict set. So an attacker can spam the system with large amount of conflict transactions, resulting the system to execute Avalanche algorithm hundreds of thousands of times, and the latency will grow significantly. DEXON will not suffer from such an attack. After total order being decided, the first transaction in the conflict set will be executed, while other conflict transactions are ignored.

## Spectre
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|NA|1 ~ 10|DAG-blocklattice|block voting algorithm|X|

Spectre is a DAG-based digital ledger system that uses recursive block voting to decide which conflict block should be finalized. This consensus algorithm allows participants to propose block arbitrarily fast, which means its scalability and latency is bounded by the network. However, its lack of total ordering of blocks makes it impossible to execute smart contract. That is the reason why they propose "Phantom", a consensus that is also DAG-based but with total ordering properties. We also [compare](#phantom) DEXON to Phantom.

## Stellar
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|1K ~ 10K|2 ~ 5|Chain|Stellar Consensus|O|

Stellar uses a generalized version of traditional Byzantine agreement protocol, which they called "federated Byzantine agreement". This consensus algorithm requires participant to choose their own quorum slices. If quorum intersection is satisfied, it is proved that all intact participants will reach consensus.

The only concern about this kind of consensus is that whether your can remain intact depends on the choice of your quorum slices. To have a secure configuration and faster response, it is better for a node to choose nodes of reliable companies or banks as quorum slices, which may lead to semi-centralization.

## Tendermint
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|NA|1 ~ 3|Chain|PBFT|△|

Tendermint uses PBFT as their consensus algorithm. Although PBFT has low latency in permissioned settings, it can not be permissionless, because PBFT has a heavy communication cost of <img src="https://latex.codecogs.com/svg.latex?O(b*n^2)" /> due to its two phase commit. That means when the number of nodes increases, the required bandwidth of network will also increase quadratically, limiting the number nodes. DEXON uses cryptographic sortition sharding technique and configurable ack frequency to reduce this communication cost to <img src="https://latex.codecogs.com/svg.latex?O(f*n*log(n))" />.


