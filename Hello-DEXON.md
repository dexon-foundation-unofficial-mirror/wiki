# Hello DEXON

> This section walks you through the [Hello-DEXON Project](https://github.com/dexon-foundation/hello-dexon).  

You will learn how to:
- Compile and deploy smart contracts, on
  - Local mocked DEXON
  - DEXON testnet

- Run contract tests
- Run a web UI to interact with the contracts

Let's get started.

## Prerequisites

You need to have these installed on your system first:
- [Node.js](https://nodejs.org/en/) @^8.10.0
- [git](https://git-scm.com/downloads)
- [Chrome](https://www.google.com/chrome/)
- [DEXON Wallet Extension](https://dexon.org/faucet)

## Setup Project

```sh
# Download from github
git clone git@github.com:dexon-foundation/hello-dexon.git

# Get inside project directory
cd hello-dexon

# Install dependencies
npm install

# Setup mnemonic phrases (copy from DEXON Wallet Extension)
cp secret.js.sample secret.js
```
Then you have to put your mnenonic phrases from DEXON Wallet into `secret.js`

## Project Structure

- `./contracts`  
The smart contracts of the project. The one you should care about is `Hello.sol`.

- `./src`  
JavaScript code for interacting with the smart contract.

- `./test`  
Contract test cases.

## Compile Smart Contract

```sh
npm run compile
```
This will compile your smart contracts and generate `./build/contracts/Hello.json`. You can see the bytecode and ABI compiled from `Hello.sol`.

## Test Smart Contract

```sh
# Run local Ganache RPC
npm run rpc

# Deploy and test on local RPC
npm run test
```
This will deploy your contracts onto local Ganache RPC and perform tests on them.

## Run Smart Contract on Local Ganache

```sh
# Run local Ganache RPC
npm run rpc

# Deploy compiled contracts to local Ganache RPC
npm run migrate:development

# Start web UI
npm run watch
```
Now, you should have the smart contract running on local Ganache RPC, and have a web UI running on `http://localhost:8080`

You can start your Chrome browser and navigate to `http://localhost:8080` and you should be able to interact with the smart contract.

Remember to choose the network in DEXON Wallet. You should be pointing to `http://localhost:8545`, which is your local Ganache RPC.

## Run Smart Contract on DEXON testnet

```sh
# Deploy compiled contracts to DEXON testnet
npm run migrate:testnet

# Start web UI
npm run watch
```
Now, you should have the smart contract running on DEXON testnet, and, the same as before, have a web UI running on `http://localhost:8080`

You can start your Chrome browser and navigate to `http://localhost:8080` and you should be able to interact with the smart contract.

The difference is that now the contract is running on public network and everyone else in the world can also see your contract on DEXON testnet!
