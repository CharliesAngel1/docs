---
title: "How to get all transactions of an address"
slug: "../how-to-get-all-transactions-of-an-address"
description: "Learn how to get all the transactions of an address using the Moralis Transaction API."
---
## Prerequisites

Before getting started, make sure you have the following ready:

- Node v.14+ or Python
- NPM/Yarn/PNPM or Pip

## Step 1: Setup Moralis

First [register](/docs/quickstart) your Moralis account and get your Moralis API Key.

Once you have your Moralis API Key, install [Moralis SDK](/docs/moralis-sdk) in your project.

```shell npm
npm install moralis @moralisweb3/common-evm-util
```
```shell yarn
yarn add moralis @moralisweb3/common-evm-util
```
```shell pnpm
pnpm add moralis @moralisweb3/common-evm-util
```
```python pip
pip install moralis
```



## Step 2: Get all transactions for an address

In order to get all the transactions for an address, Moralis provides you a `getWalletTransactions` endpoint to do so.

Here you'll need two parameters: `address` and `chain`.

Once you've obtained both the `address` and `chain`, you can copy the following code:

```javascript index.js
const Moralis = require("moralis").default;
const { EvmChain } = require("@moralisweb3/common-evm-util");

const runApp = async () => {
  await Moralis.start({
    apiKey: "YOUR_API_KEY",
    // ...and any other configuration
  });
  
  const address = "0xd8da6bf26964af9d7eed9e03e53415d37aa96045";

	const chain = EvmChain.ETHEREUM;

  const response = await Moralis.EvmApi.transaction.getWalletTransactions({
    	address,
    	chain,
	});
  
  console.log(response.toJSON());
}

runApp();
```
```typescript index.ts
import Moralis from "moralis";
import { EvmChain } from "@moralisweb3/common-evm-util";

const runApp = async () => {
  await Moralis.start({
    apiKey: "YOUR_API_KEY",
    // ...and any other configuration
  });
  
  const address = "0xd8da6bf26964af9d7eed9e03e53415d37aa96045";

	const chain = EvmChain.ETHEREUM;

  const response = await Moralis.EvmApi.transaction.getWalletTransactions({
   	  address,
   	  chain,
	});
  
  console.log(response.toJSON());
}

runApp();
```
```python index.py
from moralis import evm_api

api_key = "YOUR_API_KEY"

params = {
    "address": "0xd8da6bf26964af9d7eed9e03e53415d37aa96045", 
    "chain": "eth", 
}

result = evm_api.transaction.get_wallet_transactions(
    api_key=api_key,
    params=params,
)

print(result)
```



To execute the program, run the following command:

```shell Shell (JavaScript)
node index.js
```
```Text Shell (TypeScript)
npx ts-node index.ts
```
```python Shell (Python)
python index.py
```



In your terminal, you should see the following response:

```json
{
  "total": "2000",
  "page": "2",
  "page_size": "100",
  "result": [
    {
      "hash": "0x057Ec652A4F150f7FF94f089A38008f49a0DF88e",
      "nonce": 326595425,
      "transaction_index": 25,
      "from_address": "0xd4a3BebD824189481FC45363602b83C9c7e9cbDf",
      "to_address": "0xa71db868318f0a0bae9411347cd4a6fa23d8d4ef",
      "value": 650000000000000000,
      "gas": 6721975,
      "gas_price": 20000000000,
      "input": "string",
      "receipt_cumulative_gas_used": 1340925,
      "receipt_gas_used": 1340925,
      "receipt_contract_address": "0x1d6a4cf64b52f6c73f201839aded7379ce58059c",
      "receipt_root": "string",
      "receipt_status": 1,
      "block_timestamp": "2021-04-02T10:07:54.000Z",
      "block_number": 12526958,
      "block_hash": "0x0372c302e3c52e8f2e15d155e2c545e6d802e479236564af052759253b20fd86"
    }
  ]
}
```



Congratulations 🥳 you just got all the transactions for a wallet address with only a few lines of code using the Moralis Transaction API!

## Youtube Video

`oembed: https://www.youtube.com/watch?v=kpxgYuC4uyA

## API Reference

If you want to know more details on the endpoint and optional parameters, check out:

- [getWalletTransactions](https://docs.moralis.io/reference/getwallettransactions)

## Support

If you face any trouble following the tutorial, feel free to reach out to our community engineers in our [Discord](https://moralis.io/discord) or [Forum](https://forum.moralis.io) to get 24/7 developer support.