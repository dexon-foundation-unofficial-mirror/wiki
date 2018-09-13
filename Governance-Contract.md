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
AddBAConfirmVote(vote Vote, position Position)
BAConfirmVotes(position Position) []Vote
AddDKGComplaint(complaint Complaint, round uint64)
DKGComplaints(round uint64) []Complaint
NodeSet(round uint64) []Node
NotarySet(round uint64) []Node
```