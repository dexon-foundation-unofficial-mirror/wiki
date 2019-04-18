# Remix IDE

Remix is a browser-based compiler and IDE that enables users to build Ethereum contracts with Solidity language and to debug transactions.

To try it out, visit https://remix.dexon.org.

https://github.com/dexon-foundation/remix-ide/releases also gives others ways to use Remix locally. Please check it out.

## Documentation
To see details about how to use Remix for developing and/or debugging Solidity contracts, please see this [documentation pages](https://remix.readthedocs.io/en/latest/index.html). The document pages covers instructions on how to use Remix IDE to develop, deploy, test, debug smart contracts and some tutorials and examples to help you get started.


## On chain randomness
One of the most interesting features of DEXON is that it has an on-chain random oracle. An “on-chain” random oracle means that the random source is retrieved directly on the chain itself, instead of having to feed it in by external sources.

Remix IDE also supports this feature
You can use the `rand` keyword in Remix IDE.

Sample code:
```
pragma solidity ^0.5.0;
contract Rand {
    uint256 value;
    function update() public {
        value = rand;
    }
    function get() view public returns (uint256) {
        return value;
    }
}
```