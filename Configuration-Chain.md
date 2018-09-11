## Governance Contract
```
NodeSet map[Round][]Node
NotarySet map[Round][]Node
```

## ProposeConfigBlock()
`Round = Gov.ChainNumber() * (3600 / Gov.ProposalInterval())`
### H = 0(Genesis Config Block)
```
block.SnapshotHash = Gov.GenesisBlock.Hash
block.PrevHash = 0
block.NodeSet = Gov.GenesisNodeSet
block.NotarySet = Gov.GenesisNotarySet
block.Hash = Hash(block)
block.Signature = TSIG(block.Hash, block.NotarySet)

ConfigBlock[0] = block
```

### H = (N-1)*Round + Round/2
```
Gov[N-1].NodeSet = GetRegisteredNodeSet()
Gov[N-1].NotarySet = CalculateNotarySet(NodeSet, CRS[N-1])
```

### H = N * Round
Get block `b` at compaction position `H`
```
block.SnapshotHash = b.Hash
block.PrevHash = ConfigBlock[N-1].Hash
block.NodeSet = Gov.NodeSet[N-1]
block.NotarySet = Gov.NotarySet[N-1]
block.Hash = Hash(block)
block.Signature = TSIG(block.Hash, block.NotarySet)

ConfigBlock[N] = block
```
## GetCommittee()
```
Committee[N] = ConfigBlock[N-1].NotarySet
```
