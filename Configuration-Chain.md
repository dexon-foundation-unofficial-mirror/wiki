## Governance Contract
```
NodeSet map[Round][]Node
NotarySet map[Round][]Node
``` 

## ProposeConfigBlock()
### t = 0(Genesis Config Block)
```
block.SnapshotHash = 0
block.NodeSet = Gov.GenesisNodeSet
block.NotarySet = Gov.GenesisNotarySet

ConfigBlock[0] = block
```

### t = (N-1):30
```
Gov[N-1].NodeSet = GetRegisteredNodeSet()
Gov[N-1].NotarySet = CalculateNotarySet(NodeSet, CRS[N-1])
```

### t = N:00
Get the first block `b` output from total ordering.
```
block.SnapshotHash = b.Hash
block.NodeSet = Gov.NodeSet[N-1]
block.NotarySet = Gov.NotarySet[N-1]

ConfigBlock[N] = block
```