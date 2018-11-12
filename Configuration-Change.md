### Overview
The configuration for DEXON is round based configuration, which is allowed to be changed and applied in upcoming rounds on the fly without shutdowning/forking the system. Configurable parameters including:
- NumChains: the number of chains in blocklattice.
- K: the `K` parameter used in total ordering algorithm.
- PhiRatio: the `Phi` parameter used in total ordering algorithm with this equation: `Phi = NumChains * PhiRation`.
- NotarySetSize: the number of nodes in one notary set for one chain.
- DKGSetSize: the number of nodes in DKG set.
- RoundInterval: the interval for this round.
- MinBlockInterval: the minimum interval of timestamps between blocks on the same chain.

### Configuration Change for Byzantine Agreement
The round for agreement module on each chain is unique. Therefore, the only configuration change needs to be handled in this module is adding new chains.

### Configuration Change for Blocklattice
There would be blocks from multiple rounds in blocklattice at the same time. Thus the simplest way to make it supports various numbers of chains is to make it support the maximum number of chains. The blocklattice module would resize its internal structure to fulfill the largest number of chains it sees.

### Configuration Change for Total Ordering
We can't tolerant more than one set of parameters (K, Phi, NumChains) in this module, they are basis for the potential functions used in total ordering thus should be global and unique in total ordering module. The configuration switching procedure used in DEXON for total ordering is `Flush`.

#### Flush Procedures
- When there are configuration change at round `R+1`, the `flush setup procedure` would be triggered when the first **ending block** on some chain for round R is delivered by total ordering.
- Once `flush setup procedure` triggered, no blocks would be delivered until all **ending blocks** for round R on each chain is received by total ordering module. Once this condition is met, the total ordering would enter `flush main procedure`.
- In `flush main procedure`, all blocks in round `R` would be delivered directly in topological order based on their acking relationships. Blocks at round `R+1` would be skipped during flush. Since the acking relations between blocks in different rounds are restricted, the causality between blocks is preserved.
- Once all blocks in round `R` is flushed, the total ordering module switches back to normal delivery mode, that is, delivered by total ordering algorithm.

#### Rules for acking relations for blocks between rounds
No block in round R should ack blocks in future round (R+1, R+2, ...), even if their are proposed earlier. This rule is required because:
- We would deliver blocks without rounds interleave when flushing, to maintain the causality between blocks, all blocks delivered ealier should not ack blocks delivered later.
- Blocks in R+1 round might be picked as candidates when flushing. We would ignore those candidates from R+1 directly, based on the causality preserved by this rule.


