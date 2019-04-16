# Solidity

## What is Solidity?

Solidity is an object-oriented, high-level language for implementing smart contracts. Smart contracts are programs which govern the behaviour of accounts within the Ethereum state.

Solidity was influenced by C++, Python and JavaScript and is designed to target the Ethereum Virtual Machine (EVM).

Solidity is statically typed, supports inheritance, libraries and complex user-defined types among other features.

With Solidity you can create contracts for uses such as voting, crowdfunding, blind auctions, and multi-signature wallets.

When deploying contracts, you should use the latest released version of Solidity. This is because breaking changes as well as new features and bug fixes are introduced regularly. We currently use a 0.x version number [to indicate this fast pace of change](https://semver.org/#spec-item-4).

## Sample Solidity Contract

Here's a simple Solidity smart contract,
```
pragma solidity ^0.5.0;

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

There are two methods available for interaction in this contract: `update` and `get`.
- When `update` is called, an on-chain random seed is read from `rand` and stored into the contract variable `value`.
- When `get` is called, the `value` is read from the contract storage and returned to the caller.

You can find the complete Github repository [HERE](https://github.com/dexon-foundation/hello-dexon/blob/master/contracts/Hello.sol).

## Language Documentation

For more information, check out the full language documentation of [Solidity](https://solidity.readthedocs.io)
