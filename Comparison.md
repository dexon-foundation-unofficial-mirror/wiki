DEXON Comparison to Other Blockchain 
==
### Introduction
This document explains how DEXON is different compared to other blockchain infrastructures. We do our best to explain the main differences, but still, we have the following principles:
1. We will not dive into details of other projects. We only focus on the differences. For the details, please refer to their websites and whitepapers.
2. The comparison is based on our up-to-date understanding, and projects can be updated frequently. We will update this document if necessary.

### Definition
- Node in this document is a validator or a full node in the network.
- <img src="https://latex.codecogs.com/svg.latex?T_{network}" />: network delay between nodes
- <img src="https://latex.codecogs.com/svg.latex?n" />: number of nodes
- <img src="https://latex.codecogs.com/svg.latex?b" />: number of blocks to be confirmed
- <img src="https://latex.codecogs.com/svg.latex?f" />: ack frequency
- For smart contract column:
    - O: Supprted
    - X: Not supported
    - △: Not supported for now, but is able to support
### Table of Contents
| Project | Throughput (TPS) | Latency (seconds) | Data Structure | Consensus | Smart Contract |
| --- | --- | --- | ------------- | --- | --- |
|[DEXON](#dexon)|1M+|2|DAG|total ordering|O|
|[Algorand](#algorand)|875|< 60|chain|Byzantine agreement|△|
|[Bitcoin](#bitcoin)|7|3600|chain|longest chain rule|X|
|[Cardano](#cardano)|250|300|chain|Ouroboros|O|
|[Conflux](#conflux)|6400|270|DAG|GHOST|△|
|[Dfinity](#dfinity)|500 ~ 1000|5 ~ 10|chain|Dfinity|O|
|[EOS](#eos)|3K|165|chain|longest chain & Byzantine fault tolerance|O|
|[Ethereum](#ethereum)|20|360|chain|longest chain|O|
|[Hashgraph](#hashgraph)|200K|20|DAG|Hedera|O|
|[Hyperledger](#hyperledger)|4K|< 1|chain|pluggable|O|
|[IOTA](#iota)|500 ~ 800|> 180|DAG|longest chain rule|X|
|[Kadena](#kadena)|10K|20|DAG|Chainweb|O|
|[NANO](#nano)|7000|1|DAG|DPoS voting|X|
|[Omniledger](#omniledger)|6K|10|chain|ByzCoinX|△|
|[Ontology](#ontology)|5K|20|DAG|Ontorand|O|
|[Orbs Helix](#orbs-helix)|10|NA|chain|PBFT|O|
|[Phantom](#phantom)|NA|NA|DAG|greedy selection algorithm|△|
|[Radix](#radix)|3.5|5|chain|logical clock|O|
|[Snowflake](#snowflake)|1300|4|DAG|Avalanche|△|
|[Spectre](#spectre)|NA|1 ~ 10|DAG|block voting algorithm|X|
|[Stellar](#stellar)|1K ~ 10K|2 ~ 5|chain|Stellar Consensus|O|
|[Tendermint](#tendermint)|NA|1 ~ 3|chain|PBFT|△|
|[Thunderella](#tendermint)|NA|1.5|chain|BFT + longest chain|△|
|[TON](#ton)|M+|5|DAG|BFT|O|
|[Vite](#vite)|NA|10|DAG|longest chain|O|
|[Zilliqa](#zilliqa)|3K|10 ~ 20|chain|PBFT|O|

## DEXON
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|1M+|2|DAG|total ordering|O|

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

## Conflux
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|6400|270|DAG|GHOST|△|

Conflux is a graph-based PoW consensus based on GHOST protocol that fixed the Phantom blockchain. Conflux uses GHOST protocol to select the main chain in a graph, and produces total ordering of the graph by the main chain. Thus, it is generalized Bitcoin consensus, and they also points out that the bias problem in Phantom blockchain.

However, the latency is bounded by its PoW mechanism. It needs to wait for a period of time to select the correct and consistent main chain with high probability. Even if it switched to PoS mechanism, the latency would still be unacceptably long since the GHOST protocol is a kind of longest chain rule consensus.

## Dfinity
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|500 ~ 1000|5 ~ 10|chain|Dfinity|O|

Dfinity is a permissioned blockchain and is designed for large population (around 10K of nodes). Dfinity contains a randomness beacon which generates new randomness by a VRF (verifiable random function) with information from new confirmed block. They use the randomness to select a leader and electors for a round. By hypergeometric distribution, Dfinity only samples hundred of nodes to notary a block instead of using all nodes, and this is correct with high probability. But this reduces the tolerance ability to Byzantine nodes. For example, to achieve the majority of nodes is non-Byzantine with probability less than <img src="https://latex.codecogs.com/svg.latex?2^{-40}">, it needs to sample at least 423 nodes from 10K nodes with maximum 1/3 Byzantine nodes.
However, Dfinity is chain-based, so its throughput is limited.

## EOS
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|3K|165|chain|longest chain & Byzantine fault tolerance|O|

EOS reaches high throughput and low latency. They have 21 so-called "supernodes", which are considered not decentralized. Also, at the time of writing, its Byzantine fault tolerance consensus is not implemented yet, so the confirmation time is about 165 seconds, not 1 or 2 seconds as they claimed.

## Ethereum
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|20|360|chain|longest chain|O|

Ethereum is the first blockchain system that has a complete DApp ecosystem. It has a throughput higher and latency lower than Bitcoin, but still not enough for daily usage such as payment or gaming. A popular DApp can block the whole system, causing high transaction fee. Also, the latency now (several minutes) is not acceptable for real-time application. 

## Hashgraph
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|200K|20|DAG|Hedera|O|

The consensus of Hashgraph is adapted Byzantine agreement on graph, on the other hand, the core of DEXON consensus is based on total ordering algorithm. Their round-based structure costs a latency of <img src="https://latex.codecogs.com/svg.latex?O(log(n))*T_{network}" /> for each round, which means its confirmation time becomes longer when the number of nodes increases. With this limitation, it cannot be fully decentralized, or the confirmation time can be minutes. Also, the liveness is not guaranteed in Hashgraph. Only correctness proof is provided. With Byzantine nodes presented in its network, it is possible that Hashgraph does not output any block. Meanwhile, DEXON's confirmation time remain constant when the number of nodes increases.

## Hyperledger
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|4K|< 1|chain|pluggable|O|

Hyperledger (specifically, Hyperledger Fabric) is a distributed ledger designed for enterprise use. It should be permissioned, low-latency, high-throughput and provides private transaction functionalities. Its consensus is modularized and pluggable. It can choose among consensus engines/algorithms such as Tendermint, PBFT, Kafka ordering or RAFT.

It is much easier to address consensus problem in a permissioned consortium settings with high throughput and low latency because the assumption of the environment is: the number of nodes is fixed, each identity is known, the goal of all nodes is the same, and the network environment is stable and fast but the node does not fully trust to each other. It does fit for enterprises to use such settings, while DEXON aims to be more open and decentralized, providing high throughput and low latency at the same time.

## IOTA
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|500 ~ 800|> 180|DAG|longest chain rule|X|

IOTA follows the longest chain rule on a graph: a node randomly chooses and verifies two previous blocks and attaches its block to them. A block is confirmed if enough number of blocks followed it and the length of the connected chain is the longest.
However, the rule is inefficient because the confirmation time is not guaranteed by a specific bound. Moreover, a block might be invalid if it is attached to a block that contains conflict transaction. That block has to be re-attached to other blocks. This causes a very long confirmation time. Furthermore, IOTA does not support smart contract due to the lack of total ordering among all blocks. 

## Kadena
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|10K|20|DAG|Chainweb|O|

Kadena aims to solve scalability issue of blockchain. It uses Chainweb to process transaction in parallel. Each chain includes others' block headers, forming a DAG similar to DEXON blocklattice. To perform cross-chain transaction, one has to provide Merkle proof to smart contract, and assets will be deleted from source chain and re-created on destination chain. Kadena also analyzes peer header relationships and uses specially designed graph that has small diameter and large order to achieved low latency and high throughput.

The latency of Chainweb is <img src="https://latex.codecogs.com/svg.latex?O(r)"/>, where <img src="https://latex.codecogs.com/svg.latex?r"/> is the diameter of a graph. When it scales up and increases the number of chain, the diameter of graph also becomes larger, causing the latency to increase. Another problem is when proposing a block on a chain, the block has to include its peer's block headers. This means block proposing is blocking and not efficient, while in DEXON, a block actively acks any other newly proposed blocks, achieving fast non-blocking block proposing.

## NANO
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|7000|1|DAG|DPoS voting|X|

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

## Ontology
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|5K|20|DAG|Ontorand|O|

Ontology consensus algorithm Ontorand uses randomness from the last block to generate new block proposer and validators. Its Byzantine agreement voting process (although not detailed enough) looks extremely similar to Algorand. Its verifiable random function which generates randomness in a block is exactly the same as Algorand. Without any citation and improvement from Algorand, Ontorand is nothing but a copycat. For the comparison to Algorand please reference [here](#algorand).

## Orbs Helix
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|10|NA|chain|PBFT|O|

The top priority of Helix is fairness. It uses VRF (verifiable random function) as an unbiased random source to elect committee and leader. When running its core consensus (PBFT), all transactions are encrypted by user using threshold encryption. This means there is no way a node can cencor or prioritize any transaction. After consensus is reached, content of a block is then decrypted, and transactions are executed. Thus, the order of transactions can not be biased, achieving fairness. Helix also uses VRF to decide which transaction can be put into a block. Because node can not decide which transactions to be put into a block, transaction fee can be set to a constant. 

Unfortunantely, fairness does not come without cost. Threshold encryption not only increases computational cost, but needs an extra phase of decryption. This increase the latency. What's worse, its chain structure is not scalable. To solve the scalability problem, Orbs introduces "intelligent sharding" (which we did not find any technical detail). Recent simulation shows that Helix has only 10 TPS (with unknown latency). With 100 shard, it can reach 1000 TPS, while DEXON has 1M+ TPS with a hundred nodes in one shard. 

## Phantom
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|NA|NA|DAG|greedy selection algorithm|△|

Phantom is a DAG-based blockchain which is generalized from Bitcoin's longest chain rule on a chain to a DAG. Phantom is a proposal for Spectre, and they proposed a greedy algorithm called ghostDAG protocol to achieve total ordering. However, they didn't proof the correctness and liveness of their algorithm or provide the simulation results about Phantom in the distributed setting. A liveness attack on Phantom was individually proposed by the work from Li et al. and the work from Kiayias and Panagiotakos. They also claimed they will try to combine Phantom and Spectre in the future. We will update the information if they provide new and correct results. 

On the other hand, the total ordering in DEXON consensus is guaranteed. Moreover, the correctness and liveness of DEXON consensus are both proved.

## Radix
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|3.5|5|chain|logical clock|O|

Radix uses sharding technique to increase throughput. To reach consensus among different shards, a transcation needs to be gossipped and be validated by many nodes. Each node provides its local logical clock and appends its value to the transaction. Nodes can then use this logical clock vector to decide partial ordering between two conflict transactions. In case of a concurrent set, a node find other transactions from its local storage or from its peer trying to decide partial ordering of transactions. 

There is a foundamental problem in Radix: a partial ordering can never become total ordering without consensus algorithm. Some partial ordering of transactions in Radix can be decided by vector timestamps, but no matter how many transactions are involved, there always exists some cases that concurrent set can never be resolved. In other words, orders of some transactions may never be decided and will not be output by the system. What's worse, when a network is shortly partitioned, or has a long delay, nodes can have different local views. Since a node decides ordering from other transactions from its local view, this will cause different ordering among nodes, resulting a fork, and there is no consensus algorithm in Radix to address this issue. 

To sum up, Radix does not have consensus. It can be used in private / permissioned settings but will not work in real network environment.

## Snowflake
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|1300|4|DAG|Avalanche|△|

Snowflake consensus starts from a simple coloring method, adds additional counters and rules, and finally ends up a provably probabilistic secure consensus algorithm, Avalanche. All nodes converge to the same color, which means that they will agree on the same transaction set when conflict happens.

To resolve conflict transactions, nodes need to execute Avalanche algorithm on every transaction in a conflict set. So an attacker can spam the system with large amount of conflict transactions, resulting the system to execute Avalanche algorithm hundreds of thousands of times, and the latency will grow significantly. DEXON will not suffer from such an attack. After total order being decided, the first transaction in the conflict set will be executed, while other conflict transactions are ignored.

## Spectre
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|NA|1 ~ 10|DAG|block voting algorithm|X|

Spectre is a DAG-based digital ledger system that uses recursive block voting to decide which conflict block should be finalized. This consensus algorithm allows participants to propose block arbitrarily fast, which means its scalability and latency is bounded by the network. However, its lack of total ordering of blocks makes it impossible to execute smart contract. That is the reason why they propose "Phantom", a consensus that is also DAG-based but with total ordering properties. We also compare DEXON to [Phantom](#phantom).

## Stellar
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|1K ~ 10K|2 ~ 5|chain|Stellar Consensus|O|

Stellar uses a generalized version of traditional Byzantine agreement protocol, which they called "federated Byzantine agreement". This consensus algorithm requires participants to choose their own quorum slices. If quorum intersection is satisfied, it is proved that all intact participants will reach consensus.

The only concern about this kind of consensus is that whether you can remain intact (not affected by Byzantine nodes) depends on the choice of your quorum slices. To have a secure configuration with fast response and stable service, it is better for a node to choose nodes set up by reliable companies or banks as quorum slices, which may lead to semi-centralization.

## Tendermint
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|NA|1 ~ 3|chain|PBFT|△|

Tendermint uses PBFT as their consensus algorithm. Although PBFT has low latency in permissioned settings, it can not be permissionless, because PBFT has a heavy communication cost of <img src="https://latex.codecogs.com/svg.latex?O(b*n^2)" /> due to its two phase commit. This means when the number of nodes increases, the required bandwidth of network will also increase quadratically, limiting the number nodes. DEXON uses cryptographic sortition sharding technique and configurable ack frequency to reduce the communication cost to <img src="https://latex.codecogs.com/svg.latex?O(f*n*log(n))" />.

## Thunderella
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|NA|1.5|chain|BFT + longest chain|△|

Thunderella combines two different consensus algorithms and tries to achieve high security with good performance. With less than one forth of committee is Byzantine node, it can achieve low latency with BFT algorithm. With more than one forth, it can fall back to any blockchain system that can tolerate less than <img src="https://latex.codecogs.com/svg.latex?\frac{1}{2}n" /> Byzantine nodes.

If more than one forth of the committee is Byzantine node, Thunderella becomes as slow as a blockchain, while DEXON remains its low latency. Also, Thunderella is a chain-based system and it can not scale.

## TON
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|M+|5|DAG|BFT|O|
TON (Telegram Open Network) is a blockchain system featuring high throughput with short confirmation time. To achieve this, they propose a new point of view called "Infinite Sharding Paradigm", which tries to push sharding to its extreme. In TON, there is a masterchain for general state finalization. Under masterchain, there are several workchains to perform specific tasks for different cryptocurrencies and services. If a workchain is overloaded, under that it can have several shardchain to increase throupghput. In each chain, validators run a BFT-based consensus algorithm with DPoS mechanism to propose blocks. With this sharding design, TON claims it can reach several millions TPS with 5 seconds latency.

One major difference between TON and DEXON is that TON needs to run BFT consensus algorithm on different level of chain. For masterchain, it requires all validators to participate in BFT algorithm. Since BFT algorithm is typically not scalable, we can only have limited number of nodes to participate in masterchain. This can be considered a bit centralized. In DEXON, we do not require all nodes to run a single BFT algorithm, thus we can have hundreds of thousands of nodes participating in our system.

TON also has a finalization problem. It allows validators to modify invalid blocks without forking, since it is more efficient and will only effect some history blocks. However, this design also allows attacker to modify arbitrary history blocks if they can compromise the validator set. Normally in a system with BFT finalization, it should be impossible to modify history even if current validator set is compromised. Even in traditional PoW scheme, launching a 51% attack and modifying history blocks has a much higher cost with low probability to success. This design may cause security issue in TON.

## Vite
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|NA|10|DAG|longest chain|O|

Vite basically fixes NANO's problem we mentioned in our [comparison to NANO](#nano). It uses the same blocklattice with NANO, but additionally adds a new consensus mechanism (HDPoS) to construct a snapshot chain. This not only solves security issues in NANO, but also orders transactions, making it capible to run smart contract. What's more, Vite inherits NANO's advantages, including nearly instant transaction with high TPS.

One of the difficult challenges to use a DAG structure is to decide the ordering of transactions. Vite has a global consensus group to run a consensus algorithm to create snapshot chain. This algorithm is important because it is the key to improve NANO's disadvantages on security and lack of total ordering. Unfortunately, we can not find any detail about the algorithm in their paper and do not know how transactions on blocklattice are picked and put into snapshot chain. Is this critical process secure and fair? To address this challenges, DEXON develops total ordering algorithm to compact blocklattice into compaction chain. This algorithm is provably secure and reasonably fair.

## Zilliqa
|Throughput (TPS)|Latency (seconds)|Data Structure|Consensus|Smart Contract|
|-|-|-|-|-|
|3K|10 ~ 20|chain|PBFT|O|

Zilliqa is an optimized PBFT. It uses EC-Schnorr multi-signature to aggregate signatures from nodes. This reduces communication cost from <img src="https://latex.codecogs.com/svg.latex?O(n^2)" /> to <img src="https://latex.codecogs.com/svg.latex?O(n)" />. To address limited throughput in a chain-based system, Zilliqa uses sharding technique to process transactions in parallel. A special shard collects micro blocks from normal shards to produce final blocks.

There are several drawbacks in Zilliqa. First of all, multi-signature aggregation is computaionally costly. This is not a problem with ten-second finalization time, but in sub-second finalization time, it is not feasible with large amount of nodes in a shard. Second, Zilliqa uses a special shard running consensus protocol to combine micro blocks from other shards. This doubles the latency. In DEXON, there is no special shard to run another redundant consensus protocol. DEXON sharding mechanism is symmetric. We use consensus timestamp computed by total ordering algorithm to form compaction chain, which each shard can computed by itself when receiving finalized blocks from other shards.



