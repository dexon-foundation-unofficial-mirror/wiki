# Exchange Integration Guide

This guide provides all the necessary details for integrating DEXON with your exchange.

## RPC
DEXON RPC is compatible with Ethereum. In theory, you can use existing Ethereum module with DEXON by replacing the RPC endpoint:

|Network|RESTful|WebSocket|Chain ID|
|---|---|---|---|
|Mainnet|https://mainnet-rpc.dexon.org|wss://mainnet-rpc.dexon.org/ws|237|
|Testnet|https://testnet-rpc.dexon.org|wss://testnet-rpc.dexon.org/ws|238|
|Taipei Testnet|https://taipei-rpc.dexon.org|wss://taipei-rpc.dexon.org/ws|239|