# Rule for the DEXON node set
  We introduce the rule for node set and give a brief explanation to the functions in DEXON [governance contract](https://testnet.dexscan.org/address/0x63751838D6485578B23e8b051d40861eCC416794).

  
## Active condition (permission to be in notary set)
  You must deposit enough stake in the governance contract to get the qualification to be selected in the notary set.
  Sometimes nodes who violate the rule for notary set will be fined some coin. This leads nodes unqualified to be selected in the notary set. Nodes can be re-qualify after paying the fine.

## Reward
  The reward of each block is calculated as

    block_Reward = mining_Velocity * total_Staked * round_Interval / (365*24*60*60)

  For example, 100 nodes with each staked 1M DXN and mining velocity is 18.75%, the reward of each block is
  
    100 * 1M * 18.75% * 1 / (365*24*60*60) = 0.5945586 DXN

  You can find the parameter information via [governance statistic](https://testnet.dexscan.app/governance) page.

  From the description above, the expected reward for each node in 1 day is

    100 * 1M * 18.75% * 1 / 365 /100 = 513.7 DXN

## Penalty
Nodes shall not engage in any of the following conducts:

1. Forking or trying to fork blocks at the same height by proposing multiple blocks
2. Forking or trying to fork votes by submitting multiple votes in the same iteration in the Byzantine Agreement (BA)
3. Engaging in malicious behaviors in Distributed Key Generation, including without limitation sending wrong secret shares to other nodes, and such behaviors have been complained by other nodes
4. Producing wrong Share-Sig by sending wrong share signature to common reference string (CRS) or in commit-vote
5. Failing to finish distributed key generation (DKG)
6. Failing to propose any blocks during a whole epoch

For 1. to 4., the entire stake will be confiscated immediately by DEXON Foundation. For 5., a fine of the `1 DXN` will be imposed and no blocks can be produced until such fine is paid under the governance contract.  For 6., a fine of the `Block Reward*86400/total Node` will be imposed and no blocks can be produced until such fine is paid under the governance contract.