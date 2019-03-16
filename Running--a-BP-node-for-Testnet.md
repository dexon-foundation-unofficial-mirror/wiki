# Run DEXON

Instructions to run a DEXON block proposer node.

## Generate Node Key

A node key is required to operate a BP node. Run the following command to
generate a node key:

    docker run -v $PWD:/mnt -it dexonfoundation/dexon-tools nodekey generate /mnt/node.key

This show output content similar to the following

    Node Address: 0x93aA8C9C77De627E665F0b4015B7271B9Be89E83
    Public Key: 0x046272a157cbffa00677be00b08c9d47f295539b07e53360754579ad5e933a638ba58dcf850484e7d40b8bc163a920082b2500ee54968db7155c6231c7e4eed592

A file `node.key` can be found under current working directory. `node.key` is
very important as it contains the node private key. Please save this file
securely.

## Register your node

1. Send some DXN to your node key address, 100 DXN should suffice. These DXN are required for the node to send transaction and interact with the consensus protocol. You need to replenish them if it ran out.
2. Goto the [Governance contract page on DEXSCAN](https://testnet.dexscan.org/address/0x63751838D6485578B23e8b051d40861eCC416794).
3. Navigate to the write tab and select `register` from the dropdown menu.
4. Fill in the information like below, currently, you need 1M DXN to run a BP node. If you don't have enough testnet DXN, ask @wnhuang (telegram) for it.

![Register in Governance Contract Page](https://i.imgur.com/bc2vDgA.png)

5. Hit send to reigster your node.

After this your node should be staked.

Note that after staked, the configuration will start to take effect after 2
rounds (2400 blocks).

## Start the BP node

Use the following command to start the BP node:

    docker run -v $PWD:/mnt -it dexonfoundation/dexon:testnet \
        --testnet \
        --bp \
        --nodekey=/mnt/node.key \
        --datadir=/mnt/datadir \
        --syncmode=full \
        --cache=1024 \
        --gcmode=archive

Please make sure you have enough diskspace in the current working directory.
