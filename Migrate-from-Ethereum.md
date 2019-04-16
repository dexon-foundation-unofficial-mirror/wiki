# Migrate from Ethereum

DEXON's version of EVM is almost the same as the original EVM, therefore DEXON version of Solidity is almost the same as the original Solidity. If you have built a smart contract on Ethereum, you can usually deploy the exact same contract onto DEXON without any modification.

However, there are still some minor differences between the DEXON's version of Solidity and its Ethereum counterpart to look out for, as listed below:

## Timestamp

The granularity of time is increased in DEXON's version of EVM. Due to the improved performance of DEXON, we may have multiple blocks produced in the same second.

Therefore, in DEXON, we use `milliseconds` instead of `seconds` for timestamp. For example
```
pragma solidity ^0.5.2;

contract Time {

    function getNow() public view returns (uint256)
    {
        return now;
    }
}
```
calling `getNow()` of the contract returns a time in `milliseconds` in DEXON, while in Ethereum, a time in `seconds` is returned.

Also, the time constants in DEXON's Solidity is also change accordingly.
- `1 second` yields `1000`
- `1 minute` yields `60000`
- `1 hour` yields `3600000`
- `1 day` yields `86400000`
- `1 week` yeilds `604800000`
- `1 year` yields `31536000000`

## Gas Limit

In DEXON, **there is no unspent gas**.

If the actual execution of a transaction costs less gas than the set amount, **you still have to pay for the gas amount you've set**. So please set the gas amount wisely.

The reason for this is that in DEXON, transaction are not executed at the time they get packed into a block. So the number of transactions that can get into a block depends on the gas amount set in the transactions, not the actual gas amount consumed while executing the transactions.

## On-Chain Random Oracle

This is more of an additional feature than Ethereum's EVM.

DEXON provides [On-chain Random Oracle](On-Chain-Random-Oracle.md). This means you can get unbiased random seeds in your smart contract easily and at low cost.

Here's a simple Solidity smart contract that utilizes DEXON's on-chain randomness,
```
pragma solidity ^0.5.2;

contract Hello {
    uint256 public value;

    event UpdateNumber(uint256 _value);

    function update() public {
        value = rand;
        emit UpdateNumber(value);
    }

    function get() public view returns (uint256) {
        return value;
    }
}
```
The `rand` keyword used in the contract gives you the random seed generated from the threshold signature of a group of block producing nodes.
