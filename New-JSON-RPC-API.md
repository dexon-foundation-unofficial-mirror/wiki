<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Contents**

- [JSON RPC API](#json-rpc-api)
  - [JavaScript API](#javascript-api)
  - [JSON-RPC Endpoint](#json-rpc-endpoint)
    - [Go](#go)
  - [JSON-RPC support](#json-rpc-support)
  - [HEX value encoding](#hex-value-encoding)
  - [The default block parameter](#the-default-block-parameter)
  - [Curl Examples Explained](#curl-examples-explained)
  - [JSON-RPC methods](#json-rpc-methods)
  - [JSON RPC API Reference](#json-rpc-api-reference)
      - [web3_clientVersion](#web3_clientversion)
        - [Parameters](#parameters)
        - [Returns](#returns)
        - [Example](#example)
      - [web3_sha3](#web3_sha3)
        - [Parameters](#parameters-1)
        - [Example Parameters](#example-parameters)
        - [Returns](#returns-1)
        - [Example](#example-1)
      - [net_version](#net_version)
        - [Parameters](#parameters-2)
        - [Returns](#returns-2)
        - [Example](#example-2)
      - [net_listening](#net_listening)
        - [Parameters](#parameters-3)
        - [Returns](#returns-3)
        - [Example](#example-3)
      - [net_peerCount](#net_peercount)
        - [Parameters](#parameters-4)
        - [Returns](#returns-4)
        - [Example](#example-4)
      - [eth_protocolVersion](#eth_protocolversion)
        - [Parameters](#parameters-5)
        - [Returns](#returns-5)
        - [Example](#example-5)
      - [eth_syncing](#eth_syncing)
        - [Parameters](#parameters-6)
        - [Returns](#returns-6)
        - [Example](#example-6)
      - [eth_coinbase](#eth_coinbase)
        - [Parameters](#parameters-7)
        - [Returns](#returns-7)
        - [Example](#example-7)
      - [eth_gasPrice](#eth_gasprice)
        - [Parameters](#parameters-8)
        - [Returns](#returns-8)
        - [Example](#example-8)
      - [eth_accounts](#eth_accounts)
        - [Parameters](#parameters-9)
        - [Returns](#returns-9)
        - [Example](#example-9)
      - [eth_blockNumber](#eth_blocknumber)
        - [Parameters](#parameters-10)
        - [Returns](#returns-10)
        - [Example](#example-10)
      - [eth_getBalance](#eth_getbalance)
        - [Parameters](#parameters-11)
        - [Example Parameters](#example-parameters-1)
        - [Returns](#returns-11)
        - [Example](#example-11)
      - [eth_getStorageAt](#eth_getstorageat)
        - [Parameters](#parameters-12)
        - [Returns](#returns-12)
        - [Example](#example-12)
      - [eth_getTransactionCount](#eth_gettransactioncount)
        - [Parameters](#parameters-13)
        - [Example Parameters](#example-parameters-2)
        - [Returns](#returns-13)
        - [Example](#example-13)
      - [eth_getBlockTransactionCountByHash](#eth_getblocktransactioncountbyhash)
        - [Parameters](#parameters-14)
        - [Example Parameters](#example-parameters-3)
        - [Returns](#returns-14)
        - [Example](#example-14)
      - [eth_getBlockTransactionCountByNumber](#eth_getblocktransactioncountbynumber)
        - [Parameters](#parameters-15)
        - [Example Parameters](#example-parameters-4)
        - [Returns](#returns-15)
        - [Example](#example-15)
      - [eth_getCode](#eth_getcode)
        - [Parameters](#parameters-16)
        - [Example Parameters](#example-parameters-5)
        - [Returns](#returns-16)
        - [Example](#example-16)
      - [eth_sign](#eth_sign)
        - [Parameters](#parameters-17)
        - [Returns](#returns-17)
        - [Example](#example-17)
      - [eth_sendTransaction](#eth_sendtransaction)
        - [Parameters](#parameters-18)
        - [Example Parameters](#example-parameters-6)
        - [Returns](#returns-18)
        - [Example](#example-18)
      - [eth_sendRawTransaction](#eth_sendrawtransaction)
        - [Parameters](#parameters-19)
        - [Example Parameters](#example-parameters-7)
        - [Returns](#returns-19)
        - [Example](#example-19)
      - [eth_call](#eth_call)
        - [Parameters](#parameters-20)
        - [Returns](#returns-20)
        - [Example](#example-20)
      - [eth_estimateGas](#eth_estimategas)
        - [Parameters](#parameters-21)
        - [Returns](#returns-21)
        - [Example](#example-21)
      - [eth_getBlockByHash](#eth_getblockbyhash)
        - [Parameters](#parameters-22)
        - [Example Parameters](#example-parameters-8)
        - [Returns](#returns-22)
        - [Example](#example-22)
      - [eth_getBlockByNumber](#eth_getblockbynumber)
        - [Parameters](#parameters-23)
        - [Example Parameters](#example-parameters-9)
        - [Returns](#returns-23)
        - [Example](#example-23)
      - [eth_getTransactionByHash](#eth_gettransactionbyhash)
        - [Parameters](#parameters-24)
        - [Example Parameters](#example-parameters-10)
        - [Returns](#returns-24)
        - [Example](#example-24)
      - [eth_getTransactionByBlockHashAndIndex](#eth_gettransactionbyblockhashandindex)
        - [Parameters](#parameters-25)
        - [Example Parameters](#example-parameters-11)
        - [Returns](#returns-25)
        - [Example](#example-25)
      - [eth_getTransactionByBlockNumberAndIndex](#eth_gettransactionbyblocknumberandindex)
        - [Parameters](#parameters-26)
        - [Example Parameters](#example-parameters-12)
        - [Returns](#returns-26)
        - [Example](#example-26)
      - [eth_getTransactionReceipt](#eth_gettransactionreceipt)
        - [Parameters](#parameters-27)
        - [Example Parameters](#example-parameters-13)
        - [Returns](#returns-27)
        - [Example](#example-27)
      - [eth_pendingTransactions](#eth_pendingtransactions)
        - [Parameters](#parameters-28)
        - [Example Parameters](#example-parameters-14)
        - [Returns](#returns-28)
        - [Example](#example-28)
      - [eth_getUncleByBlockHashAndIndex](#eth_getunclebyblockhashandindex)
        - [Parameters](#parameters-32)
        - [Returns](#returns-32)
        - [Example](#example-32)
      - [eth_getUncleByBlockNumberAndIndex](#eth_getunclebyblocknumberandindex)
        - [Parameters](#parameters-33)
        - [Example Parameters](#example-parameters-15)
        - [Returns](#returns-33)
        - [Example](#example-33)
      - [eth_newFilter](#eth_newfilter)
        - [A note on specifying topic filters:](#a-note-on-specifying-topic-filters)
        - [Parameters](#parameters-34)
        - [Example Parameters](#example-parameters-16)
        - [Returns](#returns-34)
        - [Example](#example-34)
      - [eth_newBlockFilter](#eth_newblockfilter)
        - [Parameters](#parameters-35)
        - [Returns](#returns-35)
        - [Example](#example-35)
      - [eth_newPendingTransactionFilter](#eth_newpendingtransactionfilter)
        - [Parameters](#parameters-36)
        - [Returns](#returns-36)
        - [Example](#example-36)
      - [eth_uninstallFilter](#eth_uninstallfilter)
        - [Parameters](#parameters-37)
        - [Example Parameters](#example-parameters-17)
        - [Returns](#returns-37)
        - [Example](#example-37)
      - [eth_getFilterChanges](#eth_getfilterchanges)
        - [Parameters](#parameters-38)
        - [Example Parameters](#example-parameters-18)
        - [Returns](#returns-38)
        - [Example](#example-38)
      - [eth_getFilterLogs](#eth_getfilterlogs)
        - [Parameters](#parameters-39)
        - [Example Parameters](#example-parameters-19)
        - [Returns](#returns-39)
        - [Example](#example-39)
      - [eth_getLogs](#eth_getlogs)
        - [Parameters](#parameters-40)
        - [Example Parameters](#example-parameters-20)
        - [Returns](#returns-40)
        - [Example](#example-40)
      - [eth_getWork](#eth_getwork)
        - [Parameters](#parameters-41)
        - [Returns](#returns-41)
        - [Example](#example-41)
      - [eth_submitWork](#eth_submitwork)
        - [Parameters](#parameters-42)
        - [Example Parameters](#example-parameters-21)
        - [Returns](#returns-42)
        - [Example](#example-42)
      - [eth_submitHashrate](#eth_submithashrate)
        - [Parameters](#parameters-43)
        - [Example Parameters](#example-parameters-22)
        - [Returns](#returns-43)
        - [Example](#example-43)
      - [db_putString](#db_putstring)
        - [Parameters](#parameters-44)
        - [Example Parameters](#example-parameters-23)
        - [Returns](#returns-44)
        - [Example](#example-44)
      - [db_getString](#db_getstring)
        - [Parameters](#parameters-45)
        - [Example Parameters](#example-parameters-24)
        - [Returns](#returns-45)
        - [Example](#example-45)
      - [db_putHex](#db_puthex)
        - [Parameters](#parameters-46)
        - [Example Parameters](#example-parameters-25)
        - [Returns](#returns-46)
        - [Example](#example-46)
      - [db_getHex](#db_gethex)
        - [Parameters](#parameters-47)
        - [Example Parameters](#example-parameters-26)
        - [Returns](#returns-47)
        - [Example](#example-47)
      - [shh_version](#shh_version)
        - [Parameters](#parameters-48)
        - [Returns](#returns-48)
        - [Example](#example-48)
      - [shh_post](#shh_post)
        - [Parameters](#parameters-49)
        - [Example Parameters](#example-parameters-27)
        - [Returns](#returns-49)
        - [Example](#example-49)
      - [shh_newIdentity](#shh_newidentity)
        - [Parameters](#parameters-50)
        - [Returns](#returns-50)
        - [Example](#example-50)
      - [shh_hasIdentity](#shh_hasidentity)
        - [Parameters](#parameters-51)
        - [Example Parameters](#example-parameters-28)
        - [Returns](#returns-51)
        - [Example](#example-51)
      - [shh_newGroup](#shh_newgroup)
        - [Parameters](#parameters-52)
        - [Returns](#returns-52)
        - [Example](#example-52)
      - [shh_addToGroup](#shh_addtogroup)
        - [Parameters](#parameters-53)
        - [Example Parameters](#example-parameters-29)
        - [Returns](#returns-53)
        - [Example](#example-53)
      - [shh_newFilter](#shh_newfilter)
        - [Parameters](#parameters-54)
        - [Example Parameters](#example-parameters-30)
        - [Returns](#returns-54)
        - [Example](#example-54)
      - [shh_uninstallFilter](#shh_uninstallfilter)
        - [Parameters](#parameters-55)
        - [Example Parameters](#example-parameters-31)
        - [Returns](#returns-55)
        - [Example](#example-55)
      - [shh_getFilterChanges](#shh_getfilterchanges)
        - [Parameters](#parameters-56)
        - [Example Parameters](#example-parameters-32)
        - [Returns](#returns-56)
        - [Example](#example-56)
      - [shh_getMessages](#shh_getmessages)
        - [Parameters](#parameters-57)
        - [Example Parameters](#example-parameters-33)
        - [Returns](#returns-57)
        - [Example](#example-57)
  - [Extend JSON-RPC methods](#extend-json-rpc-methods)
  - [Extend JSON RPC API Reference](#extend-json-rpc-api-reference)
    - [eth_sendRawTransactions](#eth_sendRawTransactions)
      - [Parameters](#parameters-58)
      - [Returns](#returns-58)
      - [Example](#example-58)
    - [eth_getBlockReceiptsByHash](#eth_getBlockReceiptsByHash)
      - [Parameters](#parameters-59)
      - [Returns](#returns-59)
      - [Example](#example-59)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# JSON RPC API

[JSON](http://json.org/) is a lightweight data-interchange format. It can represent numbers, strings, ordered sequences of values, and collections of name/value pairs.

[JSON-RPC](http://www.jsonrpc.org/specification) is a stateless, light-weight remote procedure call (RPC) protocol. Primarily this specification defines several data structures and the rules around their processing. It is transport agnostic in that the concepts can be used within the same process, over sockets, over HTTP, or in many various message passing environments. It uses JSON ([RFC 4627](http://www.ietf.org/rfc/rfc4627.txt)) as data format.

Geth 1.4 has experimental pub/sub support. See [this](https://github.com/ethereum/go-ethereum/wiki/RPC-PUB-SUB) page for more information.

## JavaScript API

To talk to an dexon node from inside a JavaScript application use the [web3.js](https://github.com/ethereum/web3.js) library, which gives a convenient interface for the RPC methods.
See the [JavaScript API](https://github.com/ethereum/wiki/wiki/JavaScript-API) for more.
Extend API will support in the future.

## JSON-RPC Endpoint

Default JSON-RPC endpoints:

| Client | URL |
|-------|:------------:|
| Go |http://localhost:8545 | 

### Go

You can start the HTTP JSON-RPC with the `--rpc` flag
```bash
gdex --rpc
```

change the default port (8545) and listing address (localhost) with:

```bash
gdex --rpc --rpcaddr <ip> --rpcport <portnumber>
```

If accessing the RPC from a browser, CORS will need to be enabled with the appropriate domain set. Otherwise, JavaScript calls are limit by the same-origin policy and requests will fail:

```bash
gdex --rpc --rpccorsdomain "http://localhost:3000"
```

The JSON RPC can also be started from the [gdex console](https://github.com/ethereum/go-ethereum/wiki/JavaScript-Console) using the `admin.startRPC(addr, port)` command.

## HEX value encoding

At present there are two key datatypes that are passed over JSON: unformatted byte arrays and quantities. Both are passed with a hex encoding, however with different requirements to formatting:

When encoding **QUANTITIES** (integers, numbers): encode as hex, prefix with "0x", the most compact representation (slight exception: zero should be represented as "0x0"). Examples:
- 0x41 (65 in decimal)
- 0x400 (1024 in decimal)
- WRONG: 0x (should always have at least one digit - zero is "0x0")
- WRONG: 0x0400 (no leading zeroes allowed)
- WRONG: ff (must be prefixed 0x)

When encoding **UNFORMATTED DATA** (byte arrays, account addresses, hashes, bytecode arrays): encode as hex, prefix with "0x", two hex digits per byte. Examples:
- 0x41 (size 1, "A")
- 0x004200 (size 3, "\0B\0")
- 0x (size 0, "")
- WRONG: 0xf0f0f (must be even number of digits)
- WRONG: 004200 (must be prefixed 0x)

## The default block parameter

The following methods have an extra default block parameter:

- [eth_getBalance](#eth_getbalance)
- [eth_getCode](#eth_getcode)
- [eth_getTransactionCount](#eth_gettransactioncount)
- [eth_getStorageAt](#eth_getstorageat)
- [eth_call](#eth_call)

When requests are made that act on the state of dexon, the last default block parameter determines the height of the block.

The following options are possible for the defaultBlock parameter:

- `HEX String` - an integer block number
- `String "earliest"` for the earliest/genesis block
- `String "latest"` - for the latest mined block
- `String "pending"` - for the pending state/transactions

## Curl Examples Explained

The curl options below might return a response where the node complains about the content type, this is because the --data option sets the content type to application/x-www-form-urlencoded . If your node does complain, manually set the header by placing -H "Content-Type: application/json" at the start of the call.

The examples also do not include the URL/IP & port combination which must be the last argument given to curl e.x. 127.0.0.1:8545

## JSON-RPC methods

* [web3_clientVersion](#web3_clientversion)
* [web3_sha3](#web3_sha3)
* [net_version](#net_version)
* [net_peerCount](#net_peercount)
* [net_listening](#net_listening)
* [eth_protocolVersion](#eth_protocolversion)
* [eth_syncing](#eth_syncing)
* [eth_gasPrice](#eth_gasprice)
* [eth_accounts](#eth_accounts)
* [eth_blockNumber](#eth_blocknumber)
* [eth_getBalance](#eth_getbalance)
* [eth_getStorageAt](#eth_getstorageat)
* [eth_getTransactionCount](#eth_gettransactioncount)
* [eth_getBlockTransactionCountByHash](#eth_getblocktransactioncountbyhash)
* [eth_getBlockTransactionCountByNumber](#eth_getblocktransactioncountbynumber)
* [eth_getCode](#eth_getcode)
* [eth_sign](#eth_sign)
* [eth_sendTransaction](#eth_sendtransaction)
* [eth_sendRawTransaction](#eth_sendrawtransaction)
* [eth_call](#eth_call)
* [eth_estimateGas](#eth_estimategas)
* [eth_getBlockByHash](#eth_getblockbyhash)
* [eth_getBlockByNumber](#eth_getblockbynumber)
* [eth_getTransactionByHash](#eth_gettransactionbyhash)
* [eth_getTransactionByBlockHashAndIndex](#eth_gettransactionbyblockhashandindex)
* [eth_getTransactionByBlockNumberAndIndex](#eth_gettransactionbyblocknumberandindex)
* [eth_getTransactionReceipt](#eth_gettransactionreceipt)
* [eth_pendingTransactions](#eth_pendingtransactions)
* [eth_newFilter](#eth_newfilter)
* [eth_newBlockFilter](#eth_newblockfilter)
* [eth_newPendingTransactionFilter](#eth_newpendingtransactionfilter)
* [eth_uninstallFilter](#eth_uninstallfilter)
* [eth_getFilterChanges](#eth_getfilterchanges)
* [eth_getFilterLogs](#eth_getfilterlogs)
* [eth_getLogs](#eth_getlogs)
* [db_putString](#db_putstring)
* [db_getString](#db_getstring)
* [db_putHex](#db_puthex)
* [db_getHex](#db_gethex) 
* [shh_post](#shh_post)
* [shh_version](#shh_version)
* [shh_newIdentity](#shh_newidentity)
* [shh_hasIdentity](#shh_hasidentity)
* [shh_newGroup](#shh_newgroup)
* [shh_addToGroup](#shh_addtogroup)
* [shh_newFilter](#shh_newfilter)
* [shh_uninstallFilter](#shh_uninstallfilter)
* [shh_getFilterChanges](#shh_getfilterchanges)
* [shh_getMessages](#shh_getmessages)

## JSON RPC API Reference

***

#### web3_clientVersion

Returns the current client version.

##### Parameters
none

##### Returns

`String` - The current client version.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"web3_clientVersion","params":[],"id":67}'

// Result
{
  "id":67,
  "jsonrpc":"2.0",
  "result": "Mist/v0.9.3/darwin/go1.4.1"
}
```

***

#### web3_sha3

Returns Keccak-256 (*not* the standardized SHA3-256) of the given data.

##### Parameters

1. `DATA` - the data to convert into a SHA3 hash.

##### Example Parameters
```js
params: [
  "0x68656c6c6f20776f726c64"
]
```

##### Returns

`DATA` - The SHA3 result of the given string.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"web3_sha3","params":["0x68656c6c6f20776f726c64"],"id":64}'

// Result
{
  "id":64,
  "jsonrpc": "2.0",
  "result": "0x47173285a8d7341e5e972fc677286384f802f8ef42a5ec5f03bbfa254cb01fad"
}
```

***

#### net_version

Returns the current network id.

##### Parameters
none

##### Returns

`String` - The current network id.
- `"237"`: Dexon Mainnet
- `"238"`: Dexon Testnet
- `"239"`: Taipei Testnet
- `"240"`: Yilan Testnet

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"net_version","params":[],"id":67}'

// Result
{
  "id":67,
  "jsonrpc": "2.0",
  "result": "3"
}
```

***

#### net_listening

Returns `true` if client is actively listening for network connections.

##### Parameters
none

##### Returns

`Boolean` - `true` when listening, otherwise `false`.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"net_listening","params":[],"id":67}'

// Result
{
  "id":67,
  "jsonrpc":"2.0",
  "result":true
}
```

***

#### net_peerCount

Returns number of peers currently connected to the client.

##### Parameters
none

##### Returns

`QUANTITY` - integer of the number of connected peers.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"net_peerCount","params":[],"id":74}'

// Result
{
  "id":74,
  "jsonrpc": "2.0",
  "result": "0x2" // 2
}
```

***

#### eth_protocolVersion

Returns the current dexon protocol version.

##### Parameters
none

##### Returns

`String` - The current dexon protocol version.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_protocolVersion","params":[],"id":67}'

// Result
{
  "id":67,
  "jsonrpc": "2.0",
  "result": "0x40"
}
```

***

#### eth_syncing

Returns an object with data about the sync status or `false`.


##### Parameters
none

##### Returns

`Object|Boolean`, An object with sync status data or `FALSE`, when not syncing:
  - `startingBlock`: `QUANTITY` - The block at which the import started (will only be reset, after the sync reached his head)
  - `currentBlock`: `QUANTITY` - The current block, same as eth_blockNumber
  - `highestBlock`: `QUANTITY` - The estimated highest block

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_syncing","params":[],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": {
    startingBlock: '0x384',
    currentBlock: '0x386',
    highestBlock: '0x454'
  }
}
// Or when not syncing
{
  "id":1,
  "jsonrpc": "2.0",
  "result": false
}
```
***

#### eth_gasPrice

Returns the current price per gas in wei.

##### Parameters
none

##### Returns

`QUANTITY` - integer of the current gas price in dal.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_gasPrice","params":[],"id":73}'

// Result
{
  "id":73,
  "jsonrpc": "2.0",
  "result": "0x09184e72a000" // 10000000000000
}
```

***

#### eth_accounts

Returns a list of addresses owned by client.


##### Parameters
none

##### Returns

`Array of DATA`, 20 Bytes - addresses owned by the client.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_accounts","params":[],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": ["0xc94770007dda54cF92009BFF0dE90c06F603a09f"]
}
```

***

#### eth_blockNumber

Returns the number of most recent block.

##### Parameters
none

##### Returns

`QUANTITY` - integer of the current block number the client is on.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":1}'

// Result
{
  "id":83,
  "jsonrpc": "2.0",
  "result": "0xc94" // 1207
}
```

***

#### eth_getBalance

Returns the balance of the account of given address.

##### Parameters

1. `DATA`, 20 Bytes - address to check for balance.
2. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](#the-default-block-parameter)

##### Example Parameters
```js
params: [
   '0xc94770007dda54cF92009BFF0dE90c06F603a09f',
   'latest'
]
```

##### Returns

`QUANTITY` - integer of the current balance in dal.


##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getBalance","params":["0xc94770007dda54cF92009BFF0dE90c06F603a09f", "latest"],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0x0234c8a3397aab58" // 158972490234375000
}
```

***

#### eth_getStorageAt

Returns the value from a storage position at a given address. 

##### Parameters

1. `DATA`, 20 Bytes - address of the storage.
2. `QUANTITY` - integer of the position in the storage.
3. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](#the-default-block-parameter)

##### Returns

`DATA` - the value at this storage position.

##### Example
Calculating the correct position depends on the storage to retrieve. Consider the following contract deployed at `0x295a70b2de5e3953354a6a8344e616ed314d7251` by address `0x391694e7e0b0cce554cb130d723a9d27458f9298`.

```
contract Storage {
    uint pos0;
    mapping(address => uint) pos1;
    
    function Storage() {
        pos0 = 1234;
        pos1[msg.sender] = 5678;
    }
}
```

Retrieving the value of pos0 is straight forward:

```js
curl -X POST --data '{"jsonrpc":"2.0", "method": "eth_getStorageAt", "params": ["0x295a70b2de5e3953354a6a8344e616ed314d7251", "0x0", "latest"], "id": 1}' localhost:8545

{"jsonrpc":"2.0","id":1,"result":"0x00000000000000000000000000000000000000000000000000000000000004d2"}
```

Retrieving an element of the map is harder. The position of an element in the map is calculated with:
```js
keccack(LeftPad32(key, 0), LeftPad32(map position, 0))
```

This means to retrieve the storage on pos1["0x391694e7e0b0cce554cb130d723a9d27458f9298"] we need to calculate the position with:
```js
keccak(decodeHex("000000000000000000000000391694e7e0b0cce554cb130d723a9d27458f9298" + "0000000000000000000000000000000000000000000000000000000000000001"))
```
The geth console which comes with the web3 library can be used to make the calculation:
```js
> var key = "000000000000000000000000391694e7e0b0cce554cb130d723a9d27458f9298" + "0000000000000000000000000000000000000000000000000000000000000001"
undefined
> web3.sha3(key, {"encoding": "hex"})
"0x6661e9d6d8b923d5bbaab1b96e1dd51ff6ea2a93520fdc9eb75d059238b8c5e9"
```
Now to fetch the storage:
```js
curl -X POST --data '{"jsonrpc":"2.0", "method": "eth_getStorageAt", "params": ["0x295a70b2de5e3953354a6a8344e616ed314d7251", "0x6661e9d6d8b923d5bbaab1b96e1dd51ff6ea2a93520fdc9eb75d059238b8c5e9", "latest"], "id": 1}' localhost:8545

{"jsonrpc":"2.0","id":1,"result":"0x000000000000000000000000000000000000000000000000000000000000162e"}

```

***

#### eth_getTransactionCount

Returns the number of transactions *sent* from an address.


##### Parameters

1. `DATA`, 20 Bytes - address.
2. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](#the-default-block-parameter)

##### Example Parameters
```js
params: [
   '0xc94770007dda54cF92009BFF0dE90c06F603a09f',
   'latest' // state at the latest block
]
```

##### Returns

`QUANTITY` - integer of the number of transactions send from this address.


##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getTransactionCount","params":["0xc94770007dda54cF92009BFF0dE90c06F603a09f","latest"],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0x1" // 1
}
```

***

#### eth_getBlockTransactionCountByHash

Returns the number of transactions in a block from a block matching the given block hash.


##### Parameters

1. `DATA`, 32 Bytes - hash of a block.

##### Example Parameters
```js
params: [
   '0xb903239f8543d04b5dc1ba6579132b143087c68db1b2168786408fcbce568238'
]
```

##### Returns

`QUANTITY` - integer of the number of transactions in this block.


##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getBlockTransactionCountByHash","params":["0xc94770007dda54cF92009BFF0dE90c06F603a09f"],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0xc" // 11
}
```

***

#### eth_getBlockTransactionCountByNumber
> > 
Returns the number of transactions in a block matching the given block number.


##### Parameters

1. `QUANTITY|TAG` - integer of a block number, or the string `"earliest"`, `"latest"` or `"pending"`, as in the [default block parameter](#the-default-block-parameter).

##### Example Parameters
```js
params: [
   '0xe8', // 232
]
```

##### Returns

`QUANTITY` - integer of the number of transactions in this block.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getBlockTransactionCountByNumber","params":["0xe8"],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0xa" // 10
}
```
***

#### eth_getCode

Returns code at a given address.


##### Parameters

1. `DATA`, 20 Bytes - address.
2. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](#the-default-block-parameter).

##### Example Parameters
```js
params: [
   '0xa94f5374fce5edbc8e2a8697c15331677e6ebf0b',
   '0x2'  // 2
]
```

##### Returns

`DATA` - the code from the given address.


##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getCode","params":["0xa94f5374fce5edbc8e2a8697c15331677e6ebf0b", "0x2"],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0x600160008035811a818181146012578301005b601b6001356025565b8060005260206000f25b600060078202905091905056"
}
```

***

#### eth_sign

The sign method calculates an Dexon specific signature with: `sign(keccak256("\x19Dexon Signed Message:\n" + len(message) + message)))`.

By adding a prefix to the message makes the calculated signature recognisable as an Dexon specific signature. This prevents misuse where a malicious DApp can sign arbitrary data (e.g. transaction) and use the signature to impersonate the victim.

**Note** the address to sign with must be unlocked. 

##### Parameters
account, message

1. `DATA`, 20 Bytes - address.
2. `DATA`, N Bytes - message to sign.

##### Returns

`DATA`: Signature

##### Example

```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_sign","params":["0x9b2055d370f73ec7d8a03e965129118dc8f5bf83", "0xdeadbeaf"],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0xa3f20717a250c2b0b729b7e5becbff67fdaef7e0699da4de7ca5895b02a170a12d887fd3b17bfdce3481f10bea41f45ba9f709d39ce8325427b57afcfc994cee1b"
}
```

***

#### eth_sendTransaction

Creates new message call transaction or a contract creation, if the data field contains code.

##### Parameters

1. `Object` - The transaction object
  - `from`: `DATA`, 20 Bytes - The address the transaction is send from.
  - `to`: `DATA`, 20 Bytes - (optional when creating new contract) The address the transaction is directed to.
  - `gas`: `QUANTITY`  - (optional, default: 90000) Integer of the gas provided for the transaction execution. It will return unused gas.
  - `gasPrice`: `QUANTITY`  - (optional, default: To-Be-Determined) Integer of the gasPrice used for each paid gas
  - `value`: `QUANTITY`  - (optional) Integer of the value sent with this transaction
  - `data`: `DATA`  - The compiled code of a contract OR the hash of the invoked method signature and encoded parameters. For details see [Dexon Contract ABI](https://github.com/ethereum/wiki/wiki/Ethereum-Contract-ABI)
  - `nonce`: `QUANTITY`  - (optional) Integer of a nonce. This allows to overwrite your own pending transactions that use the same nonce.

##### Example Parameters
```js
params: [{
  "from": "0xb60e8dd61c5d32be8058bb8eb970870f07233155",
  "to": "0xd46e8dd67c5d32be8058bb8eb970870f07244567",
  "gas": "0x76c0", // 30400
  "gasPrice": "0x9184e72a000", // 10000000000000
  "value": "0x9184e72a", // 2441406250
  "data": "0xd46e8dd67c5d32be8d46e8dd67c5d32be8058bb8eb970870f072445675058bb8eb970870f072445675"
}]
```

##### Returns

`DATA`, 32 Bytes - the transaction hash, or the zero hash if the transaction is not yet available.

Use [eth_getTransactionReceipt](#eth_gettransactionreceipt) to get the contract address, after the transaction was mined, when you created a contract.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_sendTransaction","params":[{see above}],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0xe670ec64341771606e55d6b4ca35a1a6b75ee3d5145a99d05921026d1527331"
}
```

***

#### eth_sendRawTransaction

Creates new message call transaction or a contract creation for signed transactions.

##### Parameters

1. `DATA`, The signed transaction data.

##### Example Parameters
```js
params: ["0xd46e8dd67c5d32be8d46e8dd67c5d32be8058bb8eb970870f072445675058bb8eb970870f072445675"]
```

##### Returns

`DATA`, 32 Bytes - the transaction hash, or the zero hash if the transaction is not yet available.

Use [eth_getTransactionReceipt](#eth_gettransactionreceipt) to get the contract address, after the transaction was mined, when you created a contract.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_sendRawTransaction","params":[{see above}],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0xe670ec64341771606e55d6b4ca35a1a6b75ee3d5145a99d05921026d1527331"
}
```

***

#### eth_call

Executes a new message call immediately without creating a transaction on the block chain.


##### Parameters

1. `Object` - The transaction call object
  - `from`: `DATA`, 20 Bytes - (optional) The address the transaction is sent from.
  - `to`: `DATA`, 20 Bytes  - The address the transaction is directed to.
  - `gas`: `QUANTITY`  - (optional) Integer of the gas provided for the transaction execution. eth_call consumes zero gas, but this parameter may be needed by some executions.
  - `gasPrice`: `QUANTITY`  - (optional) Integer of the gasPrice used for each paid gas
  - `value`: `QUANTITY`  - (optional) Integer of the value sent with this transaction
  - `data`: `DATA`  - (optional) Hash of the method signature and encoded parameters. For details see [Ethereum Contract ABI](https://github.com/ethereum/wiki/wiki/Ethereum-Contract-ABI)
2. `QUANTITY|TAG` - integer block number, or the string `"latest"`, `"earliest"` or `"pending"`, see the [default block parameter](#the-default-block-parameter)

##### Returns

`DATA` - the return value of executed contract.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_call","params":[{see above}],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0x"
}
```

***

#### eth_estimateGas

Generates and returns an estimate of how much gas is necessary to allow the transaction to complete. The transaction will not be added to the blockchain. Note that the estimate may be significantly more than the amount of gas actually used by the transaction, for a variety of reasons including EVM mechanics and node performance.

##### Parameters

See [eth_call](#eth_call) parameters, expect that all properties are optional. If no gas limit is specified geth uses the block gas limit from the pending block as an upper bound. As a result the returned estimate might not be enough to executed the call/transaction when the amount of gas is higher than the pending block gas limit.

##### Returns

`QUANTITY` - the amount of gas used.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_estimateGas","params":[{see above}],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0x5208" // 21000
}
```

***

#### eth_getBlockByHash

Returns information about a block by hash.


##### Parameters

1. `DATA`, 32 Bytes - Hash of a block.
2. `Boolean` - If `true` it returns the full transaction objects, if `false` only the hashes of the transactions.

##### Example Parameters
```js
params: [
   '0xe670ec64341771606e55d6b4ca35a1a6b75ee3d5145a99d05921026d1527331',
   true
]
```

##### Returns

`Object` - A block object, or `null` when no block was found:

  - `number`: `QUANTITY` - the block number. `null` when its pending block.
  - `hash`: `DATA`, 32 Bytes - hash of the block. `null` when its pending block.
  - `parentHash`: `DATA`, 32 Bytes - hash of the parent block.
  - `nonce`: `DATA`, 8 Bytes - hash of the generated proof-of-work. `null` when its pending block.
  - `sha3Uncles`: `DATA`, 32 Bytes - SHA3 of the uncles data in the block.
  - `logsBloom`: `DATA`, 256 Bytes - the bloom filter for the logs of the block. `null` when its pending block.
  - `transactionsRoot`: `DATA`, 32 Bytes - the root of the transaction trie of the block.
  - `stateRoot`: `DATA`, 32 Bytes - the root of the final state trie of the block.
  - `receiptsRoot`: `DATA`, 32 Bytes - the root of the receipts trie of the block.
  - `miner`: `DATA`, 20 Bytes - the address of the beneficiary to whom the mining rewards were given.
  - `difficulty`: `QUANTITY` - integer of the difficulty for this block.
  - `totalDifficulty`: `QUANTITY` - integer of the total difficulty of the chain until this block.
  - `extraData`: `DATA` - the "extra data" field of this block.
  - `size`: `QUANTITY` - integer the size of this block in bytes.
  - `gasLimit`: `QUANTITY` - the maximum gas allowed in this block.
  - `gasUsed`: `QUANTITY` - the total used gas by all transactions in this block.
  - `timestamp`: `QUANTITY` - the unix timestamp for when the block was collated.
  - `transactions`: `Array` - Array of transaction objects, or 32 Bytes transaction hashes depending on the last given parameter.
  - `uncles`: `Array` - Array of uncle hashes.


##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getBlockByHash","params":["0xe670ec64341771606e55d6b4ca35a1a6b75ee3d5145a99d05921026d1527331", true],"id":1}'

// Result
{
"id":1,
"jsonrpc":"2.0",
"result": {
    "number": "0x1b4", // 436
    "hash": "0xe670ec64341771606e55d6b4ca35a1a6b75ee3d5145a99d05921026d1527331",
    "parentHash": "0x9646252be9520f6e71339a8df9c55e4d7619deeb018d2a3f2d21fc165dde5eb5",
    "nonce": "0xe04d296d2460cfb8472af2c5fd05b5a214109c25688d3704aed5484f9a7792f2",
    "sha3Uncles": "0x1dcc4de8dec75d7aab85b567b6ccd41ad312451b948a7413f0a142fd40d49347",
    "logsBloom": "0xe670ec64341771606e55d6b4ca35a1a6b75ee3d5145a99d05921026d1527331",
    "transactionsRoot": "0x56e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
    "stateRoot": "0xd5855eb08b3387c0af375e9cdb6acfc05eb8f519e419b874b6ff2ffda7ed1dff",
    "miner": "0x4e65fda2159562a496f9f3522f89122a3088497a",
    "difficulty": "0x027f07", // 163591
    "totalDifficulty":  "0x027f07", // 163591
    "extraData": "0x0000000000000000000000000000000000000000000000000000000000000000",
    "size":  "0x027f07", // 163591
    "gasLimit": "0x9f759", // 653145
    "gasUsed": "0x9f759", // 653145
    "timestamp": "0x54e34e8e" // 1424182926
    "transactions": [{...},{ ... }] 
    "uncles": ["0x1606e5...", "0xd5145a9..."]
  }
}
```

***

#### eth_getBlockByNumber

Returns information about a block by block number.

##### Parameters

1. `QUANTITY|TAG` - integer of a block number, or the string `"earliest"`, `"latest"` or `"pending"`, as in the [default block parameter](#the-default-block-parameter).
2. `Boolean` - If `true` it returns the full transaction objects, if `false` only the hashes of the transactions.

##### Example Parameters
```js
params: [
   '0x1b4', // 436
   true
]
```

##### Returns

See [eth_getBlockByHash](#eth_getblockbyhash)

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getBlockByNumber","params":["0x1b4", true],"id":1}'
```

Result see [eth_getBlockByHash](#eth_getblockbyhash)

***

#### eth_getTransactionByHash

Returns the information about a transaction requested by transaction hash.


##### Parameters

1. `DATA`, 32 Bytes - hash of a transaction

##### Example Parameters
```js
params: [
   "0x88df016429689c079f3b2f6ad39fa052532c56795b733da78a91ebe6a713944b"
]
```

##### Returns

`Object` - A transaction object, or `null` when no transaction was found:

  - `blockHash`: `DATA`, 32 Bytes - hash of the block where this transaction was in. `null` when its pending.
  - `blockNumber`: `QUANTITY` - block number where this transaction was in. `null` when its pending.
  - `from`: `DATA`, 20 Bytes - address of the sender.
  - `gas`: `QUANTITY` - gas provided by the sender.
  - `gasPrice`: `QUANTITY` - gas price provided by the sender in Wei.
  - `hash`: `DATA`, 32 Bytes - hash of the transaction.
  - `input`: `DATA` - the data send along with the transaction.
  - `nonce`: `QUANTITY` - the number of transactions made by the sender prior to this one.
  - `to`: `DATA`, 20 Bytes - address of the receiver. `null` when its a contract creation transaction.
  - `transactionIndex`: `QUANTITY` - integer of the transaction's index position in the block. `null` when its pending.
  - `value`: `QUANTITY` - value transferred in Wei.
  - `v`: `QUANTITY` - ECDSA recovery id
  - `r`: `DATA`, 32 Bytes - ECDSA signature r
  - `s`: `DATA`, 32 Bytes - ECDSA signature s

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getTransactionByHash","params":["0x88df016429689c079f3b2f6ad39fa052532c56795b733da78a91ebe6a713944b"],"id":1}'

// Result
{
  "jsonrpc":"2.0",
  "id":1,
  "result":{
    "blockHash":"0x1d59ff54b1eb26b013ce3cb5fc9dab3705b415a67127a003c3e61eb445bb8df2",
    "blockNumber":"0x5daf3b", // 6139707
    "from":"0xa7d9ddbe1f17865597fbd27ec712455208b6b76d",
    "gas":"0xc350", // 50000
    "gasPrice":"0x4a817c800", // 20000000000
    "hash":"0x88df016429689c079f3b2f6ad39fa052532c56795b733da78a91ebe6a713944b",
    "input":"0x68656c6c6f21",
    "nonce":"0x15", // 21
    "to":"0xf02c1c8e6114b1dbe8937a39260b5b0a374432bb",
    "transactionIndex":"0x41", // 65
    "value":"0xf3dbb76162000", // 4290000000000000
    "v":"0x25", // 37
    "r":"0x1b5e176d927f8e9ab405058b2d2457392da3e20f328b16ddabcebc33eaac5fea",
    "s":"0x4ba69724e8f69de52f0125ad8b3c5c2cef33019bac3249e2c0a2192766d1721c"
  }
}
```

***

#### eth_getTransactionByBlockHashAndIndex

Returns information about a transaction by block hash and transaction index position.


##### Parameters

1. `DATA`, 32 Bytes - hash of a block.
2. `QUANTITY` - integer of the transaction index position.

##### Example Parameters
```js
params: [
   '0xe670ec64341771606e55d6b4ca35a1a6b75ee3d5145a99d05921026d1527331',
   '0x0' // 0
]
```

##### Returns

See [eth_getTransactionByHash](#eth_gettransactionbyhash)

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getTransactionByBlockHashAndIndex","params":["0xc6ef2fc5426d6ad6fd9e2a26abeab0aa2411b7ab17f30a99d3cb96aed1d1055b", "0x0"],"id":1}'
```

Result see [eth_getTransactionByHash](#eth_gettransactionbyhash)

***

#### eth_getTransactionByBlockNumberAndIndex

Returns information about a transaction by block number and transaction index position.


##### Parameters

1. `QUANTITY|TAG` - a block number, or the string `"earliest"`, `"latest"` or `"pending"`, as in the [default block parameter](#the-default-block-parameter).
2. `QUANTITY` - the transaction index position.

##### Example Parameters
```js
params: [
   '0x29c', // 668
   '0x0' // 0
]
```

##### Returns

See [eth_getTransactionByHash](#eth_gettransactionbyhash)

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getTransactionByBlockNumberAndIndex","params":["0x29c", "0x0"],"id":1}'
```

Result see [eth_getTransactionByHash](#eth_gettransactionbyhash)

***

#### eth_getTransactionReceipt

Returns the receipt of a transaction by transaction hash.

**Note** That the receipt is not available for pending transactions.


##### Parameters

1. `DATA`, 32 Bytes - hash of a transaction

##### Example Parameters
```js
params: [
   '0xb903239f8543d04b5dc1ba6579132b143087c68db1b2168786408fcbce568238'
]
```

##### Returns

`Object` - A transaction receipt object, or `null` when no receipt was found:

  - `transactionHash `: `DATA`, 32 Bytes - hash of the transaction.
  - `transactionIndex`: `QUANTITY` - integer of the transaction's index position in the block.
  - `blockHash`: `DATA`, 32 Bytes - hash of the block where this transaction was in.
  - `blockNumber`: `QUANTITY` - block number where this transaction was in.
  - `from`: `DATA`, 20 Bytes - address of the sender.
  - `to`: `DATA`, 20 Bytes - address of the receiver. null when it's a contract creation transaction.
  - `cumulativeGasUsed `: `QUANTITY ` - The total amount of gas used when this transaction was executed in the block.
  - `gasUsed `: `QUANTITY ` - The amount of gas used by this specific transaction alone.
  - `contractAddress `: `DATA`, 20 Bytes - The contract address created, if the transaction was a contract creation, otherwise `null`.
  - `logs`: `Array` - Array of log objects, which this transaction generated.
  - `logsBloom`: `DATA`, 256 Bytes - Bloom filter for light clients to quickly retrieve related logs.
  
It also returns _either_ :

  - `root` : `DATA` 32 bytes of post-transaction stateroot (pre Byzantium)
  - `status`: `QUANTITY` either `1` (success) or `0` (failure) 


##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getTransactionReceipt","params":["0xb903239f8543d04b5dc1ba6579132b143087c68db1b2168786408fcbce568238"],"id":1}'

// Result
{
"id":1,
"jsonrpc":"2.0",
"result": {
     transactionHash: '0xb903239f8543d04b5dc1ba6579132b143087c68db1b2168786408fcbce568238',
     transactionIndex:  '0x1', // 1
     blockNumber: '0xb', // 11
     blockHash: '0xc6ef2fc5426d6ad6fd9e2a26abeab0aa2411b7ab17f30a99d3cb96aed1d1055b',
     cumulativeGasUsed: '0x33bc', // 13244
     gasUsed: '0x4dc', // 1244
     contractAddress: '0xb60e8dd61c5d32be8058bb8eb970870f07233155', // or null, if none was created
     logs: [{
         // logs as returned by getFilterLogs, etc.
     }, ...],
     logsBloom: "0x00...0", // 256 byte bloom filter
     status: '0x1'
  }
}
```

***

#### eth_pendingTransactions

Returns the pending transactions list.

##### Parameters
none

##### Returns

`Array` - A list of pending transactions.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_pendingTransactions","params":[],"id":1}'

// Result
{
"id":1,
"jsonrpc":"2.0",
"result": [{ 
    blockHash: '0x0000000000000000000000000000000000000000000000000000000000000000',
    blockNumber: null,
    from: '0x28bdb9c230f4d5e45435e4d006326ee32e46cb31',
    gas: '0x204734',
    gasPrice: '0x4a817c800',
    hash: '0x8dfa6a59307a490d672494a171feee09db511f05e9c097e098edc2881f9ca4f6',
    input: '0x6080604052600',
    nonce: '0x12',
    to: null,
    transactionIndex: '0x0',
    value: '0x0',
    v: '0x3d',
    r: '0xaabc9ddafffb2ae0bac4107697547d22d9383667d9e97f5409dd6881ce08f13f',
    s: '0x69e43116be8f842dcd4a0b2f760043737a59534430b762317db21d9ac8c5034' 
   },....,{ 
    blockHash: '0x0000000000000000000000000000000000000000000000000000000000000000',
    blockNumber: null,
    from: '0x28bdb9c230f4d5e45435e4d006326ee32e487b31',
    gas: '0x205940',
    gasPrice: '0x4a817c800',
    hash: '0x8e4340ea3983d86e4b6c44249362f716ec9e09849ef9b6e3321140581d2e4dac',
    input: '0xe4b6c4424936',
    nonce: '0x14',
    to: null,
    transactionIndex: '0x0',
    value: '0x0',
    v: '0x3d',
    r: '0x1ec191ef20b0e9628c4397665977cbe7a53a263c04f6f185132b77fa0fd5ca44',
    s: '0x8a58e00c63e05cfeae4f1cf19f05ce82079dc4d5857e2cc281b7797d58b5faf' 
   }]
}
```
***

#### eth_newFilter

Creates a filter object, based on filter options, to notify when the state changes (logs).
To check if the state has changed, call [eth_getFilterChanges](#eth_getfilterchanges).

##### A note on specifying topic filters:
Topics are order-dependent. A transaction with a log with topics [A, B] will be matched by the following topic filters:
* `[]` "anything"
* `[A]` "A in first position (and anything after)"
* `[null, B]` "anything in first position AND B in second position (and anything after)"
* `[A, B]` "A in first position AND B in second position (and anything after)"
* `[[A, B], [A, B]]` "(A OR B) in first position AND (A OR B) in second position (and anything after)"

##### Parameters

1. `Object` - The filter options:
  - `fromBlock`: `QUANTITY|TAG` - (optional, default: `"latest"`) Integer block number, or `"latest"` for the last mined block or `"pending"`, `"earliest"` for not yet mined transactions.
  - `toBlock`: `QUANTITY|TAG` - (optional, default: `"latest"`) Integer block number, or `"latest"` for the last mined block or `"pending"`, `"earliest"` for not yet mined transactions.
  - `address`: `DATA|Array`, 20 Bytes - (optional) Contract address or a list of addresses from which logs should originate.
  - `topics`: `Array of DATA`,  - (optional) Array of 32 Bytes `DATA` topics. Topics are order-dependent. Each topic can also be an array of DATA with "or" options.

##### Example Parameters
```js
params: [{
  "fromBlock": "0x1",
  "toBlock": "0x2",
  "address": "0x8888f1f195afa192cfee860698584c030f4c9db1",
  "topics": ["0x000000000000000000000000a94f5374fce5edbc8e2a8697c15331677e6ebf0b", null, ["0x000000000000000000000000a94f5374fce5edbc8e2a8697c15331677e6ebf0b", "0x0000000000000000000000000aff3454fce5edbc8cca8697c15331677e6ebccc"]]
}]
```

##### Returns

`QUANTITY` - A filter id.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_newFilter","params":[{"topics":["0x0000000000000000000000000000000000000000000000000000000012341234"]}],"id":73}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0x1" // 1
}
```

***

#### eth_newBlockFilter

Creates a filter in the node, to notify when a new block arrives.
To check if the state has changed, call [eth_getFilterChanges](#eth_getfilterchanges).

##### Parameters
None

##### Returns

`QUANTITY` - A filter id.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_newBlockFilter","params":[],"id":73}'

// Result
{
  "id":1,
  "jsonrpc":  "2.0",
  "result": "0x1" // 1
}
```

***

#### eth_newPendingTransactionFilter

Creates a filter in the node, to notify when new pending transactions arrive.
To check if the state has changed, call [eth_getFilterChanges](#eth_getfilterchanges).

##### Parameters
None

##### Returns

`QUANTITY` - A filter id.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_newPendingTransactionFilter","params":[],"id":73}'

// Result
{
  "id":1,
  "jsonrpc":  "2.0",
  "result": "0x1" // 1
}
```

***

#### eth_uninstallFilter

Uninstalls a filter with given id. Should always be called when watch is no longer needed.
Additonally Filters timeout when they aren't requested with [eth_getFilterChanges](#eth_getfilterchanges) for a period of time.


##### Parameters

1. `QUANTITY` - The filter id.

##### Example Parameters
```js
params: [
  "0xb" // 11
]
```

##### Returns

`Boolean` - `true` if the filter was successfully uninstalled, otherwise `false`.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_uninstallFilter","params":["0xb"],"id":73}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": true
}
```

***

#### eth_getFilterChanges

Polling method for a filter, which returns an array of logs which occurred since last poll.


##### Parameters

1. `QUANTITY` - the filter id.

##### Example Parameters
```js
params: [
  "0x16" // 22
]
```

##### Returns

`Array` - Array of log objects, or an empty array if nothing has changed since last poll.

- For filters created with `eth_newBlockFilter` the return are block hashes (`DATA`, 32 Bytes), e.g. `["0x3454645634534..."]`.
- For filters created with `eth_newPendingTransactionFilter ` the return are transaction hashes (`DATA`, 32 Bytes), e.g. `["0x6345343454645..."]`.
- For filters created with `eth_newFilter` logs are objects with following params:

  - `removed`: `TAG` - `true` when the log was removed, due to a chain reorganization. `false` if its a valid log.
  - `logIndex`: `QUANTITY` - integer of the log index position in the block. `null` when its pending log.
  - `transactionIndex`: `QUANTITY` - integer of the transactions index position log was created from. `null` when its pending log.
  - `transactionHash`: `DATA`, 32 Bytes - hash of the transactions this log was created from. `null` when its pending log.
  - `blockHash`: `DATA`, 32 Bytes - hash of the block where this log was in. `null` when its pending. `null` when its pending log.
  - `blockNumber`: `QUANTITY` - the block number where this log was in. `null` when its pending. `null` when its pending log.
  - `address`: `DATA`, 20 Bytes - address from which this log originated.
  - `data`: `DATA` - contains the non-indexed arguments of the log.
  - `topics`: `Array of DATA` - Array of 0 to 4 32 Bytes `DATA` of indexed log arguments. (In *solidity*: The first topic is the *hash* of the signature of the event (e.g. `Deposit(address,bytes32,uint256)`), except you declared the event with the `anonymous` specifier.)

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getFilterChanges","params":["0x16"],"id":73}'

// Result
{
  "id":1,
  "jsonrpc":"2.0",
  "result": [{
    "logIndex": "0x1", // 1
    "blockNumber":"0x1b4", // 436
    "blockHash": "0x8216c5785ac562ff41e2dcfdf5785ac562ff41e2dcfdf829c5a142f1fccd7d",
    "transactionHash":  "0xdf829c5a142f1fccd7d8216c5785ac562ff41e2dcfdf5785ac562ff41e2dcf",
    "transactionIndex": "0x0", // 0
    "address": "0x16c5785ac562ff41e2dcfdf829c5a142f1fccd7d",
    "data":"0x0000000000000000000000000000000000000000000000000000000000000000",
    "topics": ["0x59ebeb90bc63057b6515673c3ecf9438e5058bca0f92585014eced636878c9a5"]
    },{
      ...
    }]
}
```

***

#### eth_getFilterLogs

Returns an array of all logs matching filter with given id.


##### Parameters

1. `QUANTITY` - The filter id.

##### Example Parameters
```js
params: [
  "0x16" // 22
]
```

##### Returns

See [eth_getFilterChanges](#eth_getfilterchanges)

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getFilterLogs","params":["0x16"],"id":74}'
```

Result see [eth_getFilterChanges](#eth_getfilterchanges)

***

#### eth_getLogs

Returns an array of all logs matching a given filter object.

##### Parameters

1. `Object` - The filter options:
  - `fromBlock`: `QUANTITY|TAG` - (optional, default: `"latest"`) Integer block number, or `"latest"` for the last mined block or `"pending"`, `"earliest"` for not yet mined transactions.
  - `toBlock`: `QUANTITY|TAG` - (optional, default: `"latest"`) Integer block number, or `"latest"` for the last mined block or `"pending"`, `"earliest"` for not yet mined transactions.
  - `address`: `DATA|Array`, 20 Bytes - (optional) Contract address or a list of addresses from which logs should originate.
  - `topics`: `Array of DATA`,  - (optional) Array of 32 Bytes `DATA` topics. Topics are order-dependent. Each topic can also be an array of DATA with "or" options.
  - `blockhash`:  `DATA`, 32 Bytes - (optional) With the addition of EIP-234 (Geth >= v1.8.13 or Parity >= v2.1.0), `blockHash` is a new filter option which restricts the logs returned to the single block with the 32-byte hash `blockHash`.  Using `blockHash` is equivalent to `fromBlock` = `toBlock` = the block number with hash `blockHash`.  If `blockHash` is present in the filter criteria, then neither `fromBlock` nor `toBlock` are allowed.

##### Example Parameters
```js
params: [{
  "topics": ["0x000000000000000000000000a94f5374fce5edbc8e2a8697c15331677e6ebf0b"]
}]
```

##### Returns

See [eth_getFilterChanges](#eth_getfilterchanges)

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getLogs","params":[{"topics":["0x000000000000000000000000a94f5374fce5edbc8e2a8697c15331677e6ebf0b"]}],"id":74}'
```

Result see [eth_getFilterChanges](#eth_getfilterchanges)

***

#### db_putString

Stores a string in the local database.

**Note** this function is deprecated and will be removed in the future.

##### Parameters

1. `String` - Database name.
2. `String` - Key name.
3. `String` - String to store.

##### Example Parameters
```js
params: [
  "testDB",
  "myKey",
  "myString"
]
```

##### Returns

`Boolean` - returns `true` if the value was stored, otherwise `false`.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"db_putString","params":["testDB","myKey","myString"],"id":73}'

// Result
{
  "id":1,
  "jsonrpc":"2.0",
  "result": true
}
```

***

#### db_getString

Returns string from the local database.

**Note** this function is deprecated and will be removed in the future.

##### Parameters

1. `String` - Database name.
2. `String` - Key name.

##### Example Parameters
```js
params: [
  "testDB",
  "myKey",
]
```

##### Returns

`String` - The previously stored string.


##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"db_getString","params":["testDB","myKey"],"id":73}'

// Result
{
  "id":1,
  "jsonrpc":"2.0",
  "result": "myString"
}
```

***

#### db_putHex

Stores binary data in the local database.

**Note** this function is deprecated and will be removed in the future.


##### Parameters

1. `String` - Database name.
2. `String` - Key name.
3. `DATA` - The data to store.

##### Example Parameters
```js
params: [
  "testDB",
  "myKey",
  "0x68656c6c6f20776f726c64"
]
```

##### Returns

`Boolean` - returns `true` if the value was stored, otherwise `false`.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"db_putHex","params":["testDB","myKey","0x68656c6c6f20776f726c64"],"id":73}'

// Result
{
  "id":1,
  "jsonrpc":"2.0",
  "result": true
}
```

***

#### db_getHex

Returns binary data from the local database.

**Note** this function is deprecated and will be removed in the future.


##### Parameters

1. `String` - Database name.
2. `String` - Key name.

##### Example Parameters
```js
params: [
  "testDB",
  "myKey",
]
```

##### Returns

`DATA` - The previously stored data.


##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"db_getHex","params":["testDB","myKey"],"id":73}'

// Result
{
  "id":1,
  "jsonrpc":"2.0",
  "result": "0x68656c6c6f20776f726c64"
}
```

***

#### shh_version

Returns the current whisper protocol version.

##### Parameters
none

##### Returns

`String` - The current whisper protocol version

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"shh_version","params":[],"id":67}'

// Result
{
  "id":67,
  "jsonrpc": "2.0",
  "result": "2"
}
```

***

#### shh_post

Sends a whisper message.

##### Parameters

1. `Object` - The whisper post object:
  - `from`: `DATA`, 60 Bytes - (optional) The identity of the sender.
  - `to`: `DATA`, 60 Bytes - (optional) The identity of the receiver. When present whisper will encrypt the message so that only the receiver can decrypt it.
  - `topics`: `Array of DATA` - Array of `DATA` topics, for the receiver to identify messages.
  - `payload`: `DATA` - The payload of the message.
  - `priority`: `QUANTITY` - The integer of the priority in a range from ... (?).
  - `ttl`: `QUANTITY` - integer of the time to live in seconds.

##### Example Parameters
```js
params: [{
  from: "0x04f96a5e25610293e42a73908e93ccc8c4d4dc0edcfa9fa872f50cb214e08ebf61a03e245533f97284d442460f2998cd41858798ddfd4d661997d3940272b717b1",
  to: "0x3e245533f97284d442460f2998cd41858798ddf04f96a5e25610293e42a73908e93ccc8c4d4dc0edcfa9fa872f50cb214e08ebf61a0d4d661997d3940272b717b1",
  topics: ["0x776869737065722d636861742d636c69656e74", "0x4d5a695276454c39425154466b61693532"],
  payload: "0x7b2274797065223a226d6",
  priority: "0x64",
  ttl: "0x64",
}]
```

##### Returns

`Boolean` - returns `true` if the message was send, otherwise `false`.


##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"shh_post","params":[{"from":"0xc931d93e97ab07fe42d923478ba2465f2..","topics": ["0x68656c6c6f20776f726c64"],"payload":"0x68656c6c6f20776f726c64","ttl":0x64,"priority":0x64}],"id":73}'

// Result
{
  "id":1,
  "jsonrpc":"2.0",
  "result": true
}
```

***

#### shh_newIdentity

Creates new whisper identity in the client.

##### Parameters
none

##### Returns

`DATA`, 60 Bytes - the address of the new identiy.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"shh_newIdentity","params":[],"id":73}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0xc931d93e97ab07fe42d923478ba2465f283f440fd6cabea4dd7a2c807108f651b7135d1d6ca9007d5b68aa497e4619ac10aa3b27726e1863c1fd9b570d99bbaf"
}
```

***

#### shh_hasIdentity

Checks if the client hold the private keys for a given identity.


##### Parameters

1. `DATA`, 60 Bytes - The identity address to check.

##### Example Parameters
```js
params: [  "0x04f96a5e25610293e42a73908e93ccc8c4d4dc0edcfa9fa872f50cb214e08ebf61a03e245533f97284d442460f2998cd41858798ddfd4d661997d3940272b717b1"
]
```

##### Returns

`Boolean` - returns `true` if the client holds the privatekey for that identity, otherwise `false`.


##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"shh_hasIdentity","params":["0x04f96a5e25610293e42a73908e93ccc8c4d4dc0edcfa9fa872f50cb214e08ebf61a03e245533f97284d442460f2998cd41858798ddfd4d661997d3940272b717b1"],"id":73}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": true
}
```

***

#### shh_newGroup

Creates a new group.

##### Parameters
none

##### Returns

`DATA`, 60 Bytes - the address of the new group.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"shh_newGroup","params":[],"id":73}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": "0xc65f283f440fd6cabea4dd7a2c807108f651b7135d1d6ca90931d93e97ab07fe42d923478ba2407d5b68aa497e4619ac10aa3b27726e1863c1fd9b570d99bbaf"
}
```

***

#### shh_addToGroup

Adds a whisper identity to the group.

##### Parameters

1. `DATA`, 60 Bytes - The identity address to add to a group.

##### Example Parameters
```js
params: [ "0x04f96a5e25610293e42a73908e93ccc8c4d4dc0edcfa9fa872f50cb214e08ebf61a03e245533f97284d442460f2998cd41858798ddfd4d661997d3940272b717b1"
]
```

##### Returns

`Boolean` - returns `true` if the identity was successfully added to the group, otherwise `false`.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"shh_addToGroup","params":["0x04f96a5e25610293e42a73908e93ccc8c4d4dc0edcfa9fa872f50cb214e08ebf61a03e245533f97284d442460f2998cd41858798ddfd4d661997d3940272b717b1"],"id":73}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": true
}
```

***

#### shh_newFilter

Creates filter to notify, when client receives whisper message matching the filter options.


##### Parameters

1. `Object` - The filter options:
  - `to`: `DATA`, 60 Bytes - (optional) Identity of the receiver. *When present it will try to decrypt any incoming message if the client holds the private key to this identity.*
  - `topics`: `Array of DATA` - Array of `DATA` topics which the incoming message's topics should match.  You can use the following combinations:
    - `[A, B] = A && B`
    - `[A, [B, C]] = A && (B || C)`
    - `[null, A, B] = ANYTHING && A && B` `null` works as a wildcard

##### Example Parameters
```js
params: [{
   "topics": ['0x12341234bf4b564f'],
   "to": "0x04f96a5e25610293e42a73908e93ccc8c4d4dc0edcfa9fa872f50cb214e08ebf61a03e245533f97284d442460f2998cd41858798ddfd4d661997d3940272b717b1"
}]
```

##### Returns

`QUANTITY` - The newly created filter.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"shh_newFilter","params":[{"topics": ['0x12341234bf4b564f'],"to": "0x2341234bf4b2341234bf4b564f..."}],"id":73}'

// Result
{
  "id":1,
  "jsonrpc":"2.0",
  "result": "0x7" // 7
}
```

***

#### shh_uninstallFilter

Uninstalls a filter with given id. Should always be called when watch is no longer needed.
Additonally Filters timeout when they aren't requested with [shh_getFilterChanges](#shh_getfilterchanges) for a period of time.


##### Parameters

1. `QUANTITY` - The filter id.

##### Example Parameters
```js
params: [
  "0x7" // 7
]
```

##### Returns

`Boolean` - `true` if the filter was successfully uninstalled, otherwise `false`.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"shh_uninstallFilter","params":["0x7"],"id":73}'

// Result
{
  "id":1,
  "jsonrpc":"2.0",
  "result": true
}
```

***

#### shh_getFilterChanges

Polling method for whisper filters. Returns new messages since the last call of this method.

**Note** calling the [shh_getMessages](#shh_getmessages) method, will reset the buffer for this method, so that you won't receive duplicate messages.


##### Parameters

1. `QUANTITY` - The filter id.

##### Example Parameters
```js
params: [
  "0x7" // 7
]
```

##### Returns

`Array` - Array of messages received since last poll:

  - `hash`: `DATA`, 32 Bytes (?) - The hash of the message.
  - `from`: `DATA`, 60 Bytes - The sender of the message, if a sender was specified.
  - `to`: `DATA`, 60 Bytes - The receiver of the message, if a receiver was specified.
  - `expiry`: `QUANTITY` - Integer of the time in seconds when this message should expire (?).
  - `ttl`: `QUANTITY` -  Integer of the time the message should float in the system in seconds (?).
  - `sent`: `QUANTITY` -  Integer of the unix timestamp when the message was sent.
  - `topics`: `Array of DATA` - Array of `DATA` topics the message contained.
  - `payload`: `DATA` - The payload of the message.
  - `workProved`: `QUANTITY` - Integer of the work this message required before it was send (?).

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"shh_getFilterChanges","params":["0x7"],"id":73}'

// Result
{
  "id":1,
  "jsonrpc":"2.0",
  "result": [{
    "hash": "0x33eb2da77bf3527e28f8bf493650b1879b08c4f2a362beae4ba2f71bafcd91f9",
    "from": "0x3ec052fc33..",
    "to": "0x87gdf76g8d7fgdfg...",
    "expiry": "0x54caa50a", // 1422566666
    "sent": "0x54ca9ea2", // 1422565026
    "ttl": "0x64", // 100
    "topics": ["0x6578616d"],
    "payload": "0x7b2274797065223a226d657373616765222c2263686...",
    "workProved": "0x0"
    }]
}
```

***

#### shh_getMessages

Get all messages matching a filter. Unlike `shh_getFilterChanges` this returns all messages.

##### Parameters

1. `QUANTITY` - The filter id.

##### Example Parameters
```js
params: [
  "0x7" // 7
]
```

##### Returns

See [shh_getFilterChanges](#shh_getfilterchanges)

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"shh_getMessages","params":["0x7"],"id":73}'
```

Result see [shh_getFilterChanges](#shh_getfilterchanges)

## Extend JSON-RPC methods

* [eth_sendRawTransactions](#eth_sendrawtransactions)
* [eth_getBlockReceiptsByHash](#eth_getblockreceiptsbyhash)

## Extend JSON RPC API Reference

#### eth_sendRawTransactions

Batch creation with new message call transaction or a contract creation for signed transactions.

##### Parameters

1. `Array`, Array of signed transaction data.

##### Example Parameters
```js
params: [[
"0xd46e8dd67c5d32be8d46e8dd67c5d32be8058bb8eb970870f072445675058bb8eb970870f072445675",
"0x8eb970870f0724456758bb8eb970870f072445675058bbe8dd67c5d32be8d46e8dd67c5d32d46be805",
]]
```

##### Returns

`Array`, 32 Bytes - Array of available transaction hash.

Use [eth_getTransactionReceipt](#eth_gettransactionreceipt) to get the contract address, after the transaction was mined, when you created a contract.

##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_sendRawTransactions","params":[{see above}],"id":1}'

// Result
{
  "id":1,
  "jsonrpc": "2.0",
  "result": ["0xe670ec64341771606e55d6b4ca35a1a6b75ee3d5145a99d05921026d1527331"]
}
```

***

#### eth_getBlockReceiptsByHash

Returns all transaction receipts of a block by block hash.

##### Parameters

1. `DATA`, 32 Bytes - hash of a block

##### Example Parameters
```js
params: [
   '0xe670ec64341771606e55d6b4ca35a1a6b75ee3d5145a99d05921026d1527331'
]
```

##### Returns

`Array` - Array of transaction receipt object:
  - `Object`
    - `transactionHash `: `DATA`, 32 Bytes - hash of the transaction.
    - `transactionIndex`: `QUANTITY` - integer of the transaction's index position in the block.
    - `blockHash`: `DATA`, 32 Bytes - hash of the block where this transaction was in.
    - `blockNumber`: `QUANTITY` - block number where this transaction was in.
    - `from`: `DATA`, 20 Bytes - address of the sender.
    - `to`: `DATA`, 20 Bytes - address of the receiver. null when it's a contract creation transaction.
    - `cumulativeGasUsed `: `QUANTITY ` - The total amount of gas used when this transaction was executed in the block.
    - `gasUsed `: `QUANTITY ` - The amount of gas used by this specific transaction alone.
    - `contractAddress `: `DATA`, 20 Bytes - The contract address created, if the transaction was a contract creation, otherwise `null`.
    - `logs`: `Array` - Array of log objects, which this transaction generated.
    - `logsBloom`: `DATA`, 256 Bytes - Bloom filter for light clients to quickly retrieve related logs.
  - It also returns _either_ :
    - `root` : `DATA` 32 bytes of post-transaction stateroot (pre Byzantium)
    - `status`: `QUANTITY` either `1` (success) or `0` (failure) 


##### Example
```js
// Request
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_getTransactionReceipt","params":["0xb903239f8543d04b5dc1ba6579132b143087c68db1b2168786408fcbce568238"],"id":1}'

// Result
{
"id":1,
"jsonrpc":"2.0",
"result": [
    {
       transactionHash: '0xb903239f8543d04b5dc1ba6579132b143087c68db1b2168786408fcbce568238',
       transactionIndex:  '0x1', // 1
       blockNumber: '0xb', // 11
       blockHash: '0xc6ef2fc5426d6ad6fd9e2a26abeab0aa2411b7ab17f30a99d3cb96aed1d1055b',
       cumulativeGasUsed: '0x33bc', // 13244
       gasUsed: '0x4dc', // 1244
       contractAddress: '0xb60e8dd61c5d32be8058bb8eb970870f07233155', // or null, if none was created
       logs: [{
           // logs as returned by getFilterLogs, etc.
       }, ...],
       logsBloom: "0x00...0", // 256 byte bloom filter
       status: '0x1'
    },
  ]
}
```

