# Virtual Machine Layer Specification

The Design Principle of DEXON is to allow multi virtual machine running in the system. The current ethereum codebase already allow this by adding multiple interpreters and identify which interpreter can run given a contract code. There will be 3 major VMs in DEXON:

1. EVM: to provide backward compatibility, but adding some custom opCodes and improve concurrency.
2. DVM: design TBD, but ideally just use WASM.
3. Fixed-pipeline VM: Think of it as ASIC (pre-determined logic written in native code).


## EVM Improvements

1. The end goal is to at least able to execute 50000 TX / sec (benchmark using standard ERC20 token transfer)
2. Improve concurrency: currently go-ethereum's EVM implementation does not allow re-entry, so one can not execute multiple transactions at the same time. Probably need to consider conflict serialization problem, to make sure state root is the same after TXs are applied in different order.

## DVM Specification

1. Could be based on eWASM.
2. Need to execute at least 200000 TX / sec.
3. Functional programming language on the top layer, supports formal verification.