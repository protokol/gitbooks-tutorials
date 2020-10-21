---
description: Scenarios Showing Transaction Creation And Broadcasting Best Practices
---

# Guardian Examples

Complementary Examples of Guardian SDK used in conjunction with the Client to get your transactions out to the network and verified.

Runnable implementation of all the examples listed can be found here:

{% embed url="https://github.com/protokol/examples/tree/develop/packages/examples" %}



Edit the `src/index.ts` file to run a specific example.

### Prerequisites

Before we get started we need to make sure that all of the required dependencies are installed.

### [yarn](https://classic.yarnpkg.com/lang/en/)

```text
yarn add @protokol/guardian-crypto
yarn add @protokol/client
```

### [pnpm](https://pnpm.js.org/)

```text
yarn add @protokol/guardian-crypto
yarn add @protokol/client
```

### [npm](https://www.npmjs.com/)

```text
yarn add @protokol/guardian-crypto
yarn add @protokol/client
```

## How To Create And Broadcast Guardian Transactions

### GuardianUserPermissions - Creating and Broadcasting

```typescript
import { ProtokolConnection } from "@protokol/client";
import { ARKCrypto, Builders, Enums, Transactions as GuardianTransactions } from "@protokol/guardian-crypto";

export const guardianUserPermission = async () => {
    // Configure manager and register transaction type
    ARKCrypto.Managers.configManager.setFromPreset("testnet");
    ARKCrypto.Managers.configManager.setHeight(2);
    ARKCrypto.Transactions.TransactionRegistry.registerTransactionType(
        GuardianTransactions.GuardianUserPermissionsTransaction,
    );

    // Configure our API client
    const client = new ProtokolConnection("https://api.protokol.com/api");
    const passphrase = "clay harbor enemy utility margin pretty hub comic piece aerobic umbrella acquire";

    // Step 1: Retrieve the nonce of the sender wallet
    const senderWallet = await client.api("wallets").get(ARKCrypto.Identities.Address.fromPassphrase(passphrase));
    const senderNonce = ARKCrypto.Utils.BigNumber.make(senderWallet.body.data.nonce).plus(1);

    // Step 2: Create the transaction
    const transaction = new Builders.GuardianUserPermissionsBuilder()
        .GuardianUserPermissions({
            groupNames: ["Test Guardian Permission Group"],
            allow: [{ transactionTypeGroup: 1, transactionType: 2 }],
            publicKey: ARKCrypto.Identities.PublicKey.fromPassphrase("This is my passphrase"),
        })
        .nonce(senderNonce.toFixed())
        .sign(passphrase);

    // Step 3: Broadcast the transaction
    const broadcastResponse = await client.api("transactions").create({ transactions: [transaction.build().toJson()] });

    // Step 4: Log the response
    console.log(JSON.stringify(broadcastResponse.body.data, null, 4));
};

```



### GuardianGroupPermissions - Creating and Broadcasting

```typescript
import { ProtokolConnection } from "@protokol/client";
import { ARKCrypto, Builders, Enums, Transactions as GuardianTransactions } from "@protokol/guardian-crypto";

export const guardianGroupPermission = async () => {
    // Configure manager and register transaction type
    ARKCrypto.Managers.configManager.setFromPreset("testnet");
    ARKCrypto.Managers.configManager.setHeight(2);
    ARKCrypto.Transactions.TransactionRegistry.registerTransactionType(
        GuardianTransactions.GuardianGroupPermissionsTransaction,
    );

    // Configure our API client
    const client = new ProtokolConnection("https://api.protokol.com/api");
    const passphrase = "clay harbor enemy utility margin pretty hub comic piece aerobic umbrella acquire";

    // Step 1: Retrieve the nonce of the sender wallet
    const senderWallet = await client.api("wallets").get(ARKCrypto.Identities.Address.fromPassphrase(passphrase));
    const senderNonce = ARKCrypto.Utils.BigNumber.make(senderWallet.body.data.nonce).plus(1);

    // Step 2: Create the transaction
    const transaction = new Builders.GuardianGroupPermissionsBuilder()
        .GuardianGroupPermissions({
            name: "Test Guardian Permission Group",
            allow: [{ transactionType: 1, transactionTypeGroup: 1 }],
            deny: [{ transactionType: 1, transactionTypeGroup: 2 }],
            priority: 1,
            active: true,
            default: false,
        })
        .nonce(senderNonce.toFixed())
        .sign(passphrase);

    // Step 3: Broadcast the transaction
    const broadcastResponse = await client.api("transactions").create({ transactions: [transaction.build().toJson()] });

    // Step 4: Log the response
    console.log(JSON.stringify(broadcastResponse.body.data, null, 4));
};

```

