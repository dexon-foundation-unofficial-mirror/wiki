Access to Testnet

There are a few options on how to access the current testnet. The first is to use the public DEXON RPC endpoint,  the second one is to sync the fullnode locally.

## Public RPC Endpoint

The public testnet endpoints is available at:

    Testnet:
        http: https://testnet-rpc.dexon.org
        websocket: wss://testnet-rpc.dexon.org/ws

    Taipei testnet:
        http: https://taipei-rpc.dexon.org
        websocket: wss://taipei-rpc.dexon.org/ws


Just point your DEXON/Ethereum client to this endpoint, and you should be able to send transactions and query account info.
 
## Syncing Fullnode

The testnet could be synchronized with the following command:

```
gdex --testnet
```

If you don't know how to build the `gdex` binary, please follow the wiki page [here](https://github.com/dexon-foundation/wiki/wiki/Building-DEXON).

It may take a few hours before your fullnode is fully-synchronised.  When it does, you can now point your DEXON/Ethereum client to http://localhost:8545

Note: DEXON's current testnet is still unstable, it might be reset at some point. If it does, you might have to remove the data directory (`$HOME/.dexon` on Linux, and `$HOME/Library/Dexon` on MacOS) and re-sync the node.
