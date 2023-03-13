---
title: "How to get SPL token balance of an address"
slug: "../how-to-get-spl-token-balance-of-an-address"
description: "Learn how to get SPL token balance of an address using Moralis Solana API."
sidebar_label: "Get SPL token balance of address"
---

## Prerequisites

Before getting started, make sure you have the following ready:

- Node v.14+ or Python
- NPM/Yarn or Pip

## Step 1: Setup Moralis

import SetupMoralis from '/docs/partials/\_install-moralis-sdk.mdx';

<SetupMoralis node="moralis @moralisweb3/common-sol-utils" python="moralis" />

## Step 2: Get SPL token balance of an address

In order to get the SPL token balance of a wallet address, Moralis provides you the [getSPL](/web3-data-api/solana/reference/get-spl) API endpoint to do so.

Here you'll need two parameters: `address` and `network`.

Once you have obtained both the `address` and `network`, you can copy the following code:

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Tabs groupId="programming-language">
  <TabItem value="javascript" label="index.js (JavaScript)" default>

```javascript index.js
const Moralis = require("moralis").default;
const { SolNetwork } = require("@moralisweb3/common-sol-utils");

const runApp = async () => {
  await Moralis.start({
    apiKey: "YOUR_API_KEY",
    // ...and any other configuration
  });

  const address = "BWeBmN8zYDXgx2tnGj72cA533GZEWAVeqR9Eu29txaen";

  const network = SolNetwork.MAINNET;

  const response = await Moralis.SolApi.account.getSPL({
    address,
    network,
  });

  console.log(response.toJSON());
};

runApp();
```

</TabItem>
<TabItem value="typescript" label="index.ts (TypeScript)">

```typescript index.ts
import Moralis from "moralis";
import { SolNetwork } from "@moralisweb3/common-sol-utils";

const runApp = async () => {
  await Moralis.start({
    apiKey: "YOUR_API_KEY",
    // ...and any other configuration
  });

  const address = "BWeBmN8zYDXgx2tnGj72cA533GZEWAVeqR9Eu29txaen";

  const network = SolNetwork.MAINNET;

  const response = await Moralis.SolApi.account.getSPL({
    address,
    network,
  });

  console.log(response.toJSON());
};

runApp();
```

</TabItem>
<TabItem value="python" label="index.py (Python)">

```python index.py
from moralis import sol_api

api_key = "YOUR_API_KEY"
params = {
    "network": "mainnet",
    "address": "BWeBmN8zYDXgx2tnGj72cA533GZEWAVeqR9Eu29txaen",
}

result = sol_api.account.get_spl(
    api_key=api_key,
    params=params,
)

print(result)
```

</TabItem>
</Tabs>

## Step 3: Run the script

import RunTheScript from '/docs/partials/\_run-the-script.mdx';

<RunTheScript />

In your terminal, you should see the following JSON response:

```json
[
  {
    "associatedTokenAddress": "Dpmpwm93Amvj4uEFpYhjv8ZzfpgARq6zxKTi6mrj97gW",
    "mint": "BXWuzb3jEuGsGUe29xdApu8Z3jVgrFbr3wWdsZmLWYk9",
    "amountRaw": "100000000000",
    "amount": "100",
    "decimals": "9"
  }
]
```

Congratulations 🥳 You just got the SPL token balance of a wallet address with just a few lines of code using the Moralis Solana API!

## API Reference

If you want to know more details on the endpoint and optional parameters, check out:

- [getSPL](/web3-data-api/solana/reference/get-spl)

## Youtube Video

https://www.youtube.com/watch?v=A31n28GjwHE

## Support

If you face any trouble following the tutorial, feel free to reach out to our community engineers in our [Discord](https://moralis.io/discord) or [Forum](https://forum.moralis.io) to get 24/7 developer support.
