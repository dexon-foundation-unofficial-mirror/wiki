# Rule for the DEXON node set
  We introduce the rule for node set and give a brief explanation to the functions in DEXON [governance contract](https://testnet.dexscan.org/address/0x63751838D6485578B23e8b051d40861eCC416794).

  
## Active condition (permission to be in notary set)
  You must deposit enough stake in the governance contract to get the qualification to be selected in the notary set.
  Sometimes nodes who violate the rule for notary set will be fined some coin. This leads nodes unqualified to be selected in the notary set. Nodes can be re-qualify if paying the fined such that 
  
    stake - fine >= 1M DXN

## Reward
  The reward of each block is calculated as

    block_Reward = mining_Velocity * total_Staked * round_Interval / (365*24*60*60)

  For example, 100 nodes with each staked 1M DXN and mining velocity is 18.75%, the reward of each block is
  
      100 * 1M * 18.75% * 1 / (365*24*60*60) = 0.5945586 DXN
  You can find the parameter information via [governance statistic](https://testnet.dexscan.app/governance) page.


## Penalty
  The following behavior violates the rule and will be fined.
  1. `fork blocks` in the same height (propose more than one blocks)
  2. `fork votes` (send more than one votes in the same iteration in BA)
  3. `DKG complained` by others (send wrong secret shares to others)
  4. `wrong Share-Sig` (send wrong share signature to CRS or in commit-vote)
  5. `No block proposing` in a whole epoch
  
  If a node violates 1-4, the entire stake will be confiscated.
  If a node violates 5, the fine is `blockReward*86400/totalNode`.

## Contract Write function 
In this section, we briefly introduce some functions that DEXON governance provides to write in.

### Register
1. In DekuSan wallet, switch to the `owner's account`.
2. Navigate to the `Write` tab of the governance contract and select `register` from the dropdown menu.
3. Fill in the information like below; currently, you need 1M DXN to run a BP node.
  - Node Public Key (you must hold the corresponding secret key)
  - Name of the node
  - Contact email
  - Node Location
  - Website URL 
4. Click `Send` and `confirm` in DekuSan wallet.

### Stake/Unstake
After registering, each node owner can continue depositing more stake into DEXON governance contract.  This is super easy to achieve in DEXON governance contract. 
 1. Switch to the `owner account` in DekuSan wallet. 
 2. Navigate to the `Write` tab and select `stake` from the dropdown menu.
 3. Fill the amount of stake in the contract.
 4. Click `Send` and `confirm` in DekuSan wallet.

On the other hand, each node owner can also unstake from DEXON governance contract. This is almost identical to operating stake function.
 1. Switch to the `owner account` in DekuSan wallet.
 2. Navigate to the `Write` tab and select `unstake` from the dropdown menu.
 3. Fill the amount of unstake in the contract.
 4. Click `Send` and `confirm` in DekuSan wallet.

To ensure the stability of DEXON blockchain, the duration to withdraw the unstake coin is set 24 epochs, which corresponds around 1 day in real-world time. In the duration, the node can still propose block and earn the reward, but the node sill can be fined if violating any rule.
Note that, each node can only unstake once until the unstake is withdrawn.

### Withdraw
After unstaking and wait for 24 epochs, the node can withdraw the stake.
 1. Switch to the `owner account` in DekuSan wallet.
 2. Navigate to the `Write` tab and select `withdraw` from the dropdown menu.
 3. Click `Send` and `confirm` in DekuSan wallet.


### Transfer Node Owner 
A node owner can also transfer the owner right to others. 
 1. Switch to the `owner account` in DekuSan wallet. 
 2. Navigate to the `Write` tab and select `register` from the dropdown menu.
 3. Fill the `address` of the new owner.
 4. Click `Send` and `confirm` in DekuSan wallet.

> WARNING: This is an IRREDUCIBLE operation. No one can recover if you transfer to a wrong address. Please double-check the address is correct.

## Contract Read function
<!-- Most of the information can be found in DEXONSCAN website. To prevent in case, we introduce a method to read the status of DEXON blockchain. -->

The latest system parameters can be found in the governance contract. We introduce some fruquently used functions.

### nodes
`nodes` returns the status of a node, where the input is the order of the node. The order of a node can be query by the function `nodesOffsetByAddress`.


### nodeLength
`nodeLength` returns the current size of the node set.

### nodesOffsetByAddress
`nodesOffsetByAddress` returns the order of a node, where the input is the address of the node.


