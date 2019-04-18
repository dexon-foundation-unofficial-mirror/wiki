# Exchange Integration Guide

This guide provides all the necessary details for integrating DEXON with your exchange.

## Wallet
DEXON TX signature algorithm is exactly the same as Ethereum (secp256k1), you can use existing Ethereum wallet with DEXON.

## RPC
DEXON RPC is compatible with Ethereum. In theory, you can use existing Ethereum module with DEXON by replacing the RPC endpoint:

|Network|RESTful|WebSocket|Chain ID|
|---|---|---|---|
|Mainnet|https://mainnet-rpc.dexon.org|wss://mainnet-rpc.dexon.org/ws|237|
|Testnet|https://testnet-rpc.dexon.org|wss://testnet-rpc.dexon.org/ws|238|
|Taipei Testnet|https://taipei-rpc.dexon.org|wss://taipei-rpc.dexon.org/ws|239|

Since DEXON produce around 1 block per second, it may incur a heavier load on your database infrastructure. Make sure you have enough DB instance to handle the load.

## Starting a RPC Node
The command line interface of the fullnode program `gdex` is also similar to `geth` of `go-ethereum`. You can start a mainnet RPC node with the following command:

```
docker run -v $PWD:/mnt -it dexonfoundation/dexon:latest \
    --datadir=/mnt/datadir \
    --syncmode=fast \
    --cache=1024 \
    --gcmode=archive
```

To start a testnet RPC node:

```
docker run -v $PWD:/mnt -it dexonfoundation/dexon:testnet \
    --testnet \
    --datadir=/mnt/datadir \
    --syncmode=fast \
    --cache=1024 \
    --gcmode=archive
```

Make sure tcp/30303 and udp/30303 is not blocked by the firewall.

## Deposit Confirmation

DEXON consensus algorithm has explicit finality, meaning you only need to wait for **1 block confirmation** to credit the deposit. If you really want to make sure, you can wait for 2 confirmations to be sure.

## Explorer

Explorer link is as follows:

|Network|Explorer|
|---|---|
|Mainnet|https://dexscan.org|
|Testnet|https://testnet.dexscan.org|
|Taipei Testnet|https://taipei.dexscan.org|