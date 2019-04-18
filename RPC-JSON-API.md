Due to DEXON is compatible with ethereum, this page shows the extend APIs from [ethereum JSON RPC API](https://github.com/ethereum/wiki/wiki/JSON-RPC).

**Contents**

- [Extend JSON RPC API Reference](#extend-json-rpc-api-reference)
  - [eth_sendRawTransactions](#eth_sendRawTransactions)
    - [Parameters](#parameters)
    - [Returns](#returns)
    - [Example](#example)
  - [eth_getBlockReceiptsByHash](#eth_getBlockReceiptsByHash)
    - [Parameters](#parameters-1)
    - [Returns](#returns-1)
    - [Example](#example-1)

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
