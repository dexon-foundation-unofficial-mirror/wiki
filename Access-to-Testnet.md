There are a few options on how to access the current testnet. The first is to use the public DEXON RPC endpoint,  the second one is to sync the fullnode locally.

## Public RPC Endpoint

The public testnet endpoint is available at: https://api-testnet.dexscan.org/v1/network/rpc

Just point your DEXON/Ethereum client to this endpoint, and you should be able to send transactions and query account info.
 
## Syncing Fullnode

The testnet could be synchronised with the following command:

```
gdex --testnet
```

It may take a few hours before your fullnode is fully-synchronised.  When it does, you can now point your DEXON/Ethereum client to http://localhost:8545

Note: DEXON's current testnet is still unstable, it might be reset at some point. If it does, you might have to remove the data directory (`$HOME/.dexon` on Linux, and `Library/Dexon` on MacOS) and re-sync the node.
