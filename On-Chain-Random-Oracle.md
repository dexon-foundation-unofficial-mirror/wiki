Most blockchains do not have a random source since they are not able to generate an on-chain random number that can not be predicted beforehand. DEXON solves this problem by using threshold signature with BLS scheme. Since this final threshold signature is only known after they are being gathered together, one can not predict the signature before sending the transaction that would be included in the given block.

If you look at the block result using the RPC:
```
{
    "jsonrpc": "2.0",
    "id": 1,
    "result": {
        "dexconMeta": "...",
        "extraData": "0x",
        "gasLimit": "0x7a1200",
        "gasUsed": "0x238f8",
        "hash": "0x78ba157ae54a4784e1f0edbdac2b14e1f38f519d34d3d3164d75016ac90e8227",
        "logsBloom": "...",
        "miner": "0xb6a2e270b54f19b4002d6535a71cfdd1ca1f5fc1",
        "mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
        "nonce": "0x0000000000000000",
        "number": "0x100",
        "parentHash": "0x8da90bea16f9a6edf022030766950636caad7fbd0ef296e7d34da052d0fa4ca7",
        "randomness": "0x895736dfafa3ce4e0f051fac7cc218cb092b67e88b7c25f4cf90e496e91c7d10e55a251e0ff6e655fdc8d866b85fe30c",
        "receiptsRoot": "0xc627d0acef6f0592ffd775e05b4f6b36dce8065a217bf4c9fec0c538b8b46b7d",
        "sha3Uncles": "0x1dcc4de8dec75d7aab85b567b6ccd41ad312451b948a7413f0a142fd40d49347",
        "size": "0x67b",
        "stateRoot": "0xb728e453a70d2c6d5f9a00857aa697740c16770a696dd8a6594876c2b6f85a84",
        "timestamp": "0x5bcf0935",
        "totalDifficulty": "0x20100",
        "transactions": [
          ...
        ],
        "transactionsRoot": "0x1b1e6b2a70de752b563fbeedb0461dca4af0c56e8dd3147b7a7ea3b2a701f6e6",
        "uncles": []
    }
}
```

You can see there is a `randomness` field which standard Ethereum RPC does not have. This `randomness` field is actually the threshold signature of the block signed by the DKG set.

The DEXON blockchain exposes this randomness source in Solidity with the `rand` variable, which when accessed, generates a deterministic random number. 'deterministic' means that all nodes will generate the same random number when running the EVM using the block randomness source. The `rand` variable compiles to a new opcode `RAND (0x2f)` 
we added into EVM. The random number is calculated with the following formula:

```
rand = Keccak( Randomness . Caller . Nonce . Gas )
```

* `Randomness` is the block randomness signed by DKG set, unique for each block.
* `Caller` is the address of the contract caller.
* `Nonce` is the account nonce of the caller.
* `Gas` current gas level. This ensures the random number is different each time when called.