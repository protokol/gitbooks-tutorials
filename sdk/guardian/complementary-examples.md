---
description: Scenarios Showing Transaction Creation And Broadcasting Best Practices
---

# Complementary Examples

You can find runnable example in the following link



### Prerequisites

Before we get started we need to make sure that all of the required dependencies are installed.

{% hint style="warning" %}
We recommend the usage of Yarn, but you can choose any other package manager you want!
{% endhint %}

### [yarn](https://classic.yarnpkg.com/lang/en/)

```text
yarn add @arkecosystem/crypto
yarn add @protokol/guardian-crypto
yarn add @protokol/client
```

### [pnpm](https://pnpm.js.org/)

```text
pnpm add @arkecosystem/crypto
pnpm add @protokol/guardian-crypto
pnpm add @protokol/client
```

### [npm](https://www.npmjs.com/)

```text
npm install @arkecosystem/crypto
npm install @protokol/guardian-crypto
npm install @protokol/client
```

## How To Create And Broadcast Guardian Transactions

### GroupPermissions - Creating and Broadcasting

```typescript
import { Identities, Managers, Transactions, Utils } from "@arkecosystem/crypto";
import { ProtokolConnection } from "@protokol/client";
import { Builders, Transactions as GuardianTransactions } from "@protokol/guardian-crypto";

export const GroupPermissions = async (): Promise<void> => {
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
	Transactions.TransactionRegistry.registerTransactionType(GuardianTransactions.GuardianGroupPermissionsTransaction);

	// Step 1: Retrieve the nonce of the sender wallet
	const senderWallet = await client.api("wallets").get(Identities.Address.fromPassphrase(passphrase));
	const senderNonce = Utils.BigNumber.make(senderWallet.body.data.nonce).plus(1);

	// Step 2: Create the transaction
	const transaction = new Builders.GuardianGroupPermissionsBuilder()
		.GuardianGroupPermissions({
			name: "Test Guardian Permission Group",
			allow: [{ transactionType: 1, transactionTypeGroup: 1 }],
			deny: [{ transactionType: 2, transactionTypeGroup: 1 }],
			priority: 1,
			active: true,
			default: false,
		})
		.nonce(senderNonce.toFixed())
		.sign(passphrase);

	// Step 3: Broadcast the transaction
	const broadcastResponse = await client.api("transactions").create({ transactions: [transaction.build().toJson()] });

	// Step 4: Log the response
	console.log(JSON.stringify(broadcastResponse.body, null, 4));
};

GroupPermissions()
	.then(() => process.exit(0))
	.catch((error) => {
		console.error(error);
		process.exit(1);
	});

```

### UserPermissions - Creating and Broadcasting

```typescript
import { Identities, Managers, Transactions, Utils } from "@arkecosystem/crypto";
import { ProtokolConnection } from "@protokol/client";
import { Builders, Transactions as GuardianTransactions } from "@protokol/guardian-crypto";

export const UserPermissions = async (): Promise<void> => {
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
	Transactions.TransactionRegistry.registerTransactionType(GuardianTransactions.GuardianUserPermissionsTransaction);

	// Step 1: Retrieve the nonce of the sender wallet
	const senderWallet = await client.api("wallets").get(Identities.Address.fromPassphrase(passphrase));
	const senderNonce = Utils.BigNumber.make(senderWallet.body.data.nonce).plus(1);

	// Step 2: Create the transaction
	const transaction = new Builders.GuardianUserPermissionsBuilder()
		.GuardianUserPermissions({
			groupNames: ["Test Guardian Permission Group"],
			allow: [{ transactionTypeGroup: 1, transactionType: 2 }],
			publicKey: Identities.PublicKey.fromPassphrase("This is banned public key passphrase"),
		})
		.nonce(senderNonce.toFixed())
		.sign(passphrase);

	// Step 3: Broadcast the transaction
	const broadcastResponse = await client.api("transactions").create({ transactions: [transaction.build().toJson()] });

	// Step 4: Log the response
	console.log(JSON.stringify(broadcastResponse.body, null, 4));
};

UserPermissions()
	.then(() => process.exit(0))
	.catch((error) => {
		console.error(error);
		process.exit(1);
	});

```

