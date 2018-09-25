Governance Contract Params
==============================
```
min_supported_version (string, "0.0.1")
min_block_time (ms, uint32, 500ms)
block_proposal_waiting_period (ms, uint 32, 250ms)
transaction_timeout (ms, uint32, 5000ms)
min_validator_stake_self_deposit (DEX, uint32, 5000)
min_validator_stake_total_deposit (DEX, uint32, 25000)
validator_stake_deposit_lock_up_period  (s, uint32, 86400s)
validator_stake_withdrawal_lock_up_period (s, uint32, 86400s)
validator_set_change_period (s, uint32, 3600s)
snapshot_period (s, uint32, 3600s)
reward_per_block (DEX token, uint64)
tx_fee (DEX token, uint64)
account_creation_fee (DEX token, uint64)
governance_council_change_period (s, uint32, 30 days)

max_call_stack (uint32, 1024)
max_tx_gas_consumption (DEX, uint32, ?)
tx_rate_limit (uint32, 1024, per contract / per account TX rate limit)
```

Governance Contract Methods
==============================
```
// DKG Complaint is required for light nodes to verify TSIG.
AddDKGComplaint(complaint DKGComplaint, round uint64)
DKGComplaints(round uint64) []DKGComplaint
// DKGMasterPublicKey is required to verify the DKG complaint.
AddDKGMasterPublicKey(masterPublicKey DKGMasterPublicKey, round uint64)
DKGMasterPublicKeys(round uint64) []DKGMasterPublicKey
// NodeSet
NodeSet(round uint64) []Node
// NotarySet are committee sampled from NodeSet.
NotarySet(round uint64) []Node
// RoundRange (fixme if you have better name)
// This function is used to query the block heights of each chain
// allowed to proposed by the notary set of this round.
// Consensus layer would also rely on this info to decide how many
// chains required in this round.
RoundRange(round uint64) []uint64
```