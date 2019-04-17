# Access DEXON Network

There are a few options on how to access DEXON networks. The first is to use the public DEXON RPC endpoint, the second one is to run a fullnode and sync the fullnode locally.

## Public RPC Endpoints

The public RPC endpoints are available at:

|Network|RESTful|WebSocket|Chain ID|
|---|---|---|---|
|Mainnet|https://mainnet-rpc.dexon.org|wss://mainnet-rpc.dexon.org/ws|237|
|Testnet|https://testnet-rpc.dexon.org|wss://testnet-rpc.dexon.org/ws|238|
|Taipei Testnet|https://taipei-rpc.dexon.org|wss://taipei-rpc.dexon.org/ws|239|

Point your DEXON/Ethereum client to this RPC endpoint and you should be able to read from and send transactions to DEXON networks.
 
## Syncing Fullnode

The testnet could be synchronized with the following command:

```
gdex --testnet
```

If you don't know how to build the `gdex` binary, please follow the wiki page [here](https://github.com/dexon-foundation/wiki/wiki/Building-DEXON).

It may take a few hours before your fullnode is fully-synchronised.  When it does, you can now point your DEXON/Ethereum client to http://localhost:8545

Note: DEXON's current testnet is still unstable, it might be reset at some point. If it does, you might have to remove the data directory (`$HOME/.dexon` on Linux, and `$HOME/Library/Dexon` on MacOS) and re-sync the node.
