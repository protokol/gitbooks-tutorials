---
description: Scenarios Showing Transaction Creation And Broadcasting Best Practices
---

# Complementary Examples

You can find runnable example in the following link

{% embed url="https://github.com/protokol/nameservice/tree/develop/packages/nameservice-examples" %}

### Prerequisites

Before we get started we need to make sure that all of the required dependencies are installed.

{% hint style="warning" %}
We recommend the usage of Yarn, but you can choose any other package manager you want!
{% endhint %}

### [yarn](https://classic.yarnpkg.com/lang/en/)

```text
yarn add @arkecosystem/crypto
yarn add @protokol/nameservice-crypto
yarn add @protokol/client
```

### [pnpm](https://pnpm.js.org/)

```text
pnpm add @arkecosystem/crypto
pnpm add @protokol/nameservice-crypto
pnpm add @protokol/client
```

### [npm](https://www.npmjs.com/)

```text
npm install @arkecosystem/crypto
npm install @protokol/nameservice-crypto
npm install @protokol/client
```

## How To Create And Broadcast Nameservice Transactions

### Nameservice - Creating and Broadcasting

```typescript
import { Identities, Managers, Transactions, Utils } from "@arkecosystem/crypto";
import { ProtokolConnection } from "@protokol/client";
import { Builders, Transactions as NameserviceTransactions } from "@protokol/nameservice-crypto";

export const Nameservice = async (): Promise<void> => {
    // Configure our API client
    const client = new ProtokolConnection("http://localhost:4003/api");
    const passphrase = "clay harbor enemy utility margin pretty hub comic piece aerobic umbrella acquire";

    // Configure manager and register transaction type
    const configs = await client.api("node").crypto();
    const {
        body: {
            data: {
                block: { height },
            },
        },
    } = await client.get("blockchain");

    Managers.configManager.setConfig({ ...configs.body.data } as any);
    Managers.configManager.setHeight(height);
    Transactions.TransactionRegistry.registerTransactionType(NameserviceTransactions.NameserviceTransaction);

    // Step 1: Retrieve the nonce of the sender wallet
    const senderWallet = await client.api("wallets").get(Identities.Address.fromPassphrase(passphrase));
    const senderNonce = Utils.BigNumber.make(senderWallet.body.data.nonce).plus(1);

    // Step 2: Create the transaction
    const transaction = new Builders.NameserviceBuilder()
        .Nameservice({
            name: "zan",
        })
        .nonce(senderNonce.toFixed())
        .sign(passphrase);

    // Step 3: Broadcast the transaction
    const broadcastResponse = await client.api("transactions").create({ transactions: [transaction.build().toJson()] });

    // Step 4: Log the response
    console.log(JSON.stringify(broadcastResponse.body, null, 4));
};

Nameservice()
    .then(() => process.exit(0))
    .catch((error) => {
        console.error(error);
        process.exit(1);
    });
```

