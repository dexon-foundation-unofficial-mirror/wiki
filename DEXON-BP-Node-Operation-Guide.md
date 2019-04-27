<p align="center">
  <img src="https://imgur.com/0p5xQsi.png" width="400">
</p>

## Content

- [Objective](#objective)
- [Background](#background)
- [Overview](#overview)
- [Environment Setup](#environment-setup)
- [System Requirement](#system-requirement)
- [Software Instruction](#software-instruction)
- [Mining Mechanism](#mining-mechanism)


## Objective
The document will contain essential instructions and knowledge for a node operator to successfully run a DEXON BP node. 

## Background
For node operator to easily establish a DEXON BP node and continuously run the node for mining rewards, DEXON foundation provides the well-designed software supporting the mining mechanism on DEXON blockchain.

## Overview
The guide has 3 sections, providing the required knowledge for a node operator to: Set up node, run software, and collect mining rewards.

## Environment Setup
How to set up AWS/GCP server?

For AWS, please follow https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/welcome.html

For GCP, please follow https://cloud.google.com/compute/docs/quickstart-linux

### System Requirement
Running DEXON BP node has the following requirement:

### Hardware Requirement

| Tier | CPU | Memory | Bandwidth | Estimated Cost |
| ---  | --- | ---    | ---       | ---            |
| Minimum  | 4 Cores 2.0+ GHz | 8 GB | 200Mbps | 200~400 USD/mth |
| Recommend| 8 Cores 2.0+ GHz | 16 GB| 200Mbps | 600~800 USD/mth |

### Software requirement
 - OS: Linux 64 bit.
 - Docker image: dexonfoundation/dexon
 - Docker
 - Go compiler
 - C++ compiler
 - Library: gmp, openssl, pkg-config

Follow the appropriate link below to find installation instructions for your platform.
 - [Installation Instructions for Mac](https://github.com/dexon-foundation/wiki/wiki/Installation-Instructions-for-Mac)
 - [Installation Instructions for Ubuntu](https://github.com/dexon-foundation/wiki/wiki/Installation-Instructions-for-Ubuntu)

## Software Instruction

### Generate Node Key
A node key is required to operate a BP node. Run the following command to generate a node key:

    docker run -v $PWD:/mnt -it dexonfoundation/dexon-tools \
        nodekey generate /mnt/node.key

This show output content similar to the following

    Node Address: 0x93aA8C9C77De627E665F0b4015B7271B9Be89E83
    Public Key:0x046272a157cbffa00677be00b08c9d47f295539b07e53360754579ad5e933a638ba58dcf850484e7d40b8bc163a920082b2500ee54968db7155c6231c7e4eed592

Please store the address and public key which will be used to register a fullnode.
A file node.key can be found under the current working directory. node.key is very important as it contains the node private key. Please save this file securely.

### Register your node
1. Sync DEXON blockchain. Use the following command to download all the blocks in DEXON blockchain.
```
docker run --restart always -v $PWD:/mnt -it dexonfoundation/dexon:latest \
        --bp \
        --nodekey=/mnt/node.key \
        --datadir=/mnt/datadir \
        --syncmode=fast\
        --cache=1024 \
        --gcmode=archive
```
When you see `commit pivot`, press `control + c`.

2. Send some DXN to your node key address, 500 DXN should suffice. These DXN are required for the node to send transaction and interact with the consensus protocol. You need to replenish them if it ran out.
3. Send 5 ETH (Ethereum mainnet Ether) to your node key address. This is a very **important** step. Since DEXON relies on Ethereum mainnet to recover itself in case there is a catastrophic network failure. There are penalties if a BP node failed to propose recovery vote due to insufficient Ether in their node key address, see [Rules for node set](Rule-for-the-DEXON-node-set.md) for more details.
4. Goto the [Governance contract page on DEXONSCAN](https://testnet.dexscan.app/address/0x63751838D6485578B23e8b051d40861eCC416794).
5. Navigate to the `Write` tab and select `register` from the dropdown menu.

6. Fill in the information like below; currently, you need 1M DXN to run a BP node. If you don't have enough testnet DXN, ask @wnhuang (telegram) for it.

  - Node Public Key (the public key generated above and should not duplicate)
  - Name of the node (maximum length: 32 bytes)
  - Contact email (maximum length: 32 bytes)
  - Node Location (maximum length: 32 bytes)
  - Website URL (maximum length: 128 bytes)

![Register in Governance Contract Page](https://i.imgur.com/bc2vDgA.png)
The user whose stake is locked (bought DXN coin in private-sale), please contact DEXON Foundation and provide the information below.

7. Hit send to register your node.

After this, you are successfully staked and the configuration will start to take effect after 2 epochs (2400 blocks).

Note that, the account of node.key and the account to send DXN coin to governance contract are not necessary to be the same. We strongly suggest using different keys to manage the risk.

### Start the BP node
Use the following command to start the BP node:

    docker run --restart always -v $PWD:/mnt -it dexonfoundation/dexon:latest \
        --bp \
        --nodekey=/mnt/node.key \
        --datadir=/mnt/datadir \
        --syncmode=full \
        --cache=1024 \
        --gcmode=archive

Please make sure you have enough disk space in the current working directory

For more detail instruction about `gdex`, go to https://github.com/dexon-foundation/dexon or use 

    docker run -v $PWD:/mnt -it dexonfoundation/dexon --help



## Mining Mechanism

### [DEXON Mining Economy and Mining Rewards](https://github.com/dexon-foundation/wiki/wiki/DEXON-Cryptoeconomics)
Please read this document, https://github.com/dexon-foundation/wiki/wiki/DEXON-Cryptoeconomics

As an example, initially, each node can expectedly mine 1M * 18.75% = 187.5K DXN coin per year (before total minted tokens hit 1.5B DXN).

