# DApp Development Guide

> #### Hands-on: Hello DEXON
> Prefer to learn by examples? follow the steps in [Hello-DEXON Project](https://github.com/dexon-foundation/hello-dexon) to get a quick grasp of how **smart contract**, **web app** and **wallet extension** all work together as a DApp. 

> #### Migrate from Ethereum
> If you have already developed DApps on Ethereum, you can skip to [Migrate from Ethereum](Migrate-DApp-from-Ethereum.md) and learn what the differences between DEXON and Ethereum are. 

## Introduction

DApps are decentralized applications built on top of blockchain platforms like DEXON or Ethereum. At the heart of every DApps are smart contracts. Smart contracts are programs compiled into VM bytecode and deployed onto the blockchain platform.

After deployment, a smart contract resides on an address, just like any other regular account. Everyone in the system can interact with the smart contract by sending transactions to the contract address.

Currently, DEXON uses the same account system as Ethereum. DEXON also has its default VM built from VM Ethereum's virtual machine (EVM). So DApp development on DEXON is *almost* the same as on Ethereum.

## Solidity

The most commonly used language to develop a DEXON/Ethereum DApp is Solidity, which we will introduce briefly in the [next section](Solidity.md).

DEXON's version of EVM is almost the same as the original EVM, therefore DEXON version of Solidity is almost the same as the original Solidity. If you have built a smart contract on Ethereum, you can usually deploy the exact same contract onto DEXON without any modification.

However, there are still some minor differences between the DEXON's version of Solidity and its Ethereum counterpart, because of the boost in performance and the [On-chain Random Oracle](On-Chain-Random-Oracle.md) that DEXON provides. We will cover these differences in [Migrate from Ethereum](Migrate-DApp-from-Ethereum.md).

## DEXON Remix IDE

Remix is a web-based integrated development environment, originally built for Ethereum. The DEXON version of Remix is available [HERE](https://remix.dexon.org) ([Github Repository](https://github.com/dexon-foundation/remix-ide)).

With Remix IDE, you can develop, compile, deploy and debug your smart contracts easily from the same interface.

There are other tools for developing and testing smart contracts. However, if you are a beginner in DApp development, we suggest that you [try out Remix IDE first](Remix-IDE.md).

## Interact With Smart Contracts

Once you have deployed your smart contracts on chain, the next step is to interact with your contract from your UI, which can either be a web app or a native mobile app. [This section](Interact-with-Contracts.md) shows you how it's done.

## Tools and Libraries

DEXON provides a wide range of tools and libraries for DApp development, listed [HERE](Tools-and-Libraries.md).
