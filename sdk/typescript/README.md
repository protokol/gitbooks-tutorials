---
description: >-
  Complementary Examples of NFT Base Crypto SDK and NFT Exchange Crypto SDK with
  the NFT Client SDK to get your transactions out to the network and verified.
---

# TypeScript

## Prerequisites <a id="prerequisites"></a>

Before we get started we need to make sure that all of the required dependencies are installed.

### [yarn](https://classic.yarnpkg.com/lang/en/)

```text
yarn add @protokol/nft-base-crypto
yarn add @protokol/nft-exchange-crypto
yarn add @protokol/nft-client
```

### [pnpm](https://pnpm.js.org/)

```text
pnpm add @protokol/nft-base-crypto
pnpm add @protokol/nft-exchange-crypto
pnpm add @protokol/nft-client
```

### [npm](https://www.npmjs.com/)

```text
npm install @protokol/nft-base-crypto
npm install @protokol/nft-exchange-crypto
npm install @protokol/nft-client
```

## Troubleshooting

For troubleshooting see [this section from ARK Core Official SDK Documentation.](https://sdk.ark.dev/typescript/complementary-examples#troubleshooting)

## How To Create And Broadcast NFT Base Transactions

### NFTRegisterCollection - Creating and Broadcasting

```typescript
import { Identities, Managers, Transactions, Utils } from "@arkecosystem/crypto";
import { Builders, Transactions as NFTTransactions } from "@protokol/nft-base-crypto";
import { NFTConnection } from "@protokol/nft-client";

export const NFTRegisterCollection = async () => {
    // Configure manager and register transaction type
    Managers.configManager.setFromPreset("testnet");
    Managers.configManager.setHeight(2);
    Transactions.TransactionRegistry.registerTransactionType(NFTTransactions.NFTRegisterCollectionTransaction);

    // Configure our API client
    const client = new NFTConnection("http://nft.protokol.com:4003/api");
    const passphrase = "clay harbor enemy utility margin pretty hub comic piece aerobic umbrella acquire";

    // Step 1: Retrieve the nonce of the sender wallet
    const senderWallet = await client.api("wallets").get(Identities.Address.fromPassphrase(passphrase));
    const senderNonce = Utils.BigNumber.make(senderWallet.body.data.nonce).plus(1);

    // Step 2: Create the transaction
    const transaction = new Builders.NFTRegisterCollectionBuilder()
        .NFTRegisterCollectionAsset({
            name: "FIFA-20-PLAYERS",
            description: "FIFA 2020 Players",
            maximumSupply: 100,
            jsonSchema: {
                properties: {
                    name: {
                        type: "string",
                    },
                    pac: {
                        type: "number",
                    },
                    sho: {
                        type: "number",
                    },
                    pas: {
                        type: "number",
                    },
                    dri: {
                        type: "number",
                    },
                    def: {
                        type: "number",
                    },
                    phy: {
                        type: "number",
                    },
                },
            },
        })
        .nonce(senderNonce.toFixed())
        .sign(passphrase);

    // Step 3: Broadcast the transaction
    const broadcastResponse = await client.api("transactions").create({ transactions: [transaction.build().toJson()] });

    // Step 4: Log the response
    console.log(JSON.stringify(broadcastResponse.body.data, null, 4));
};
```

### NFTCreate - Creating and Broadcasting

```typescript
import { Identities, Managers, Transactions, Utils } from "@arkecosystem/crypto";
import { Builders, Transactions as NFTTransactions } from "@protokol/nft-base-crypto";
import { NFTConnection } from "@protokol/nft-client";

export const NFTCreate = async () => {
    // Configure manager and register transaction type
    Managers.configManager.setFromPreset("testnet");
    Managers.configManager.setHeight(2);
    Transactions.TransactionRegistry.registerTransactionType(NFTTransactions.NFTCreateTransaction);

    // Configure our API client
    const client = new NFTConnection("http://nft.protokol.com:4003/api");
    const passphrase = "clay harbor enemy utility margin pretty hub comic piece aerobic umbrella acquire";

    // Step 1: Retrieve the nonce of the sender wallet
    const senderWallet = await client.api("wallets").get(Identities.Address.fromPassphrase(passphrase));
    const senderNonce = Utils.BigNumber.make(senderWallet.body.data.nonce).plus(1);

    // Step 2: Create the transaction
    const transaction = new Builders.NFTCreateBuilder()
        .NFTCreateToken({
            collectionId: "c23b4a9e07329861422df43631d7aa72153cabcca3067941b94a69016ae8723b",
            attributes: {
                name: "Antonio Caracciolo",
                pac: 90,
                sho: 90,
                pas: 90,
                dri: 90,
                def: 90,
                phy: 90,
            },
        })
        .nonce(senderNonce.toFixed())
        .sign(passphrase);

    // Step 3: Broadcast the transaction
    const broadcastResponse = await client.api("transactions").create({ transactions: [transaction.build().toJson()] });

    // Step 4: Log the response
    console.log(JSON.stringify(broadcastResponse.body.data, null, 4));
};
```

### NFTTransfer - Creating and Broadcasting

```typescript
import { Identities, Managers, Transactions, Utils } from "@arkecosystem/crypto";
import { Builders, Transactions as NFTTransactions } from "@protokol/nft-base-crypto";
import { NFTConnection } from "@protokol/nft-client";

export const NFTTransfer = async () => {
    // Configure manager and register transaction type
    Managers.configManager.setFromPreset("testnet");
    Managers.configManager.setHeight(2);
    Transactions.TransactionRegistry.registerTransactionType(NFTTransactions.NFTTransferTransaction);

    // Configure our API client
    const client = new NFTConnection("http://nft.protokol.com:4003/api");
    const passphrase = "clay harbor enemy utility margin pretty hub comic piece aerobic umbrella acquire";

    // Step 1: Retrieve the nonce of the sender wallet
    const senderWallet = await client.api("wallets").get(Identities.Address.fromPassphrase(passphrase));
    const senderNonce = Utils.BigNumber.make(senderWallet.body.data.nonce).plus(1);

    // Step 2: Create the transaction
    const transaction = new Builders.NFTTransferBuilder()
        .NFTTransferAsset({
            recipientId: Identities.Address.fromPassphrase(passphrase),
            nftIds: ["7373bbe5524898faec40bfcd12c6161981771f3be6426404208784831f4b0d02"],
        })
        .nonce(senderNonce.toFixed())
        .sign(passphrase);

    // Step 3: Broadcast the transaction
    const broadcastResponse = await client.api("transactions").create({ transactions: [transaction.build().toJson()] });

    // Step 4: Log the response
    console.log(JSON.stringify(broadcastResponse.body.data, null, 4));
};

```

### NFTBurn - Creating and Broadcasting

```typescript
import { Identities, Managers, Transactions, Utils } from "@arkecosystem/crypto";
import { Builders, Transactions as NFTTransactions } from "@protokol/nft-base-crypto";
import { NFTConnection } from "@protokol/nft-client";

export const NFTBurn = async () => {
    // Configure manager and register transaction type
    Managers.configManager.setFromPreset("testnet");
    Managers.configManager.setHeight(2);
    Transactions.TransactionRegistry.registerTransactionType(NFTTransactions.NFTBurnTransaction);

    // Configure our API client
    const client = new NFTConnection("http://nft.protokol.com:4003/api");
    const passphrase = "clay harbor enemy utility margin pretty hub comic piece aerobic umbrella acquire";

    // Step 1: Retrieve the nonce of the sender wallet
    const senderWallet = await client.api("wallets").get(Identities.Address.fromPassphrase(passphrase));
    const senderNonce = Utils.BigNumber.make(senderWallet.body.data.nonce).plus(1);

    // Step 2: Create the transaction
    const transaction = new Builders.NFTBurnBuilder()
        .NFTBurnAsset({
            nftId: "6f252f11b119e00a5364d37670623d1b6be562f577984c819237ca4668e2897e",
        })
        .nonce(senderNonce.toFixed())
        .sign(passphrase);

    // Step 3: Broadcast the transaction
    const broadcastResponse = await client.api("transactions").create({ transactions: [transaction.build().toJson()] });

    // Step 4: Log the response
    console.log(JSON.stringify(broadcastResponse.body.data, null, 4));
};

```

## How To Create And Broadcast NFT Exchange Transactions

### NFTAuction - Creating and Broadcasting

```typescript
import { Identities, Managers, Transactions, Utils } from "@arkecosystem/crypto";
import { NFTConnection } from "@protokol/nft-client";
import { Builders, Transactions as NFTTransactions } from "@protokol/nft-exchange-crypto";

export const NFTAuction = async () => {
    // Configure manager and register transaction type
    Managers.configManager.setFromPreset("testnet");
    Managers.configManager.setHeight(2);
    Transactions.TransactionRegistry.registerTransactionType(NFTTransactions.NFTAuctionTransaction);

    // Configure our API client
    const client = new NFTConnection("http://nft.protokol.com:4003/api");
    const passphrase = "clay harbor enemy utility margin pretty hub comic piece aerobic umbrella acquire";

    // Step 1: Retrieve the nonce of the sender wallet
    const senderWallet = await client.api("wallets").get(Identities.Address.fromPassphrase(passphrase));
    const senderNonce = Utils.BigNumber.make(senderWallet.body.data.nonce).plus(1);

    // Step 2: Create the transaction
    const transaction = new Builders.NFTAuctionBuilder()
        .NFTAuctionAsset({
            startAmount: Utils.BigNumber.make("1000"),
            expiration: {
                blockHeight: 1000000,
            },
            nftIds: ["77c0cc9bbb26c69c95e7bd12ca7e2590ea70417eaf8f593905fd30b440ec8458"],
        })
        .nonce(senderNonce.toFixed())
        .sign(passphrase);

    // Step 3: Broadcast the transaction
    const broadcastResponse = await client.api("transactions").create({ transactions: [transaction.build().toJson()] });

    // Step 4: Log the response
    console.log(JSON.stringify(broadcastResponse.body.data, null, 4));
};

```

### NFTAuctionCancel - Creating and Broadcasting

```typescript
import { Identities, Managers, Transactions, Utils } from "@arkecosystem/crypto";
import { NFTConnection } from "@protokol/nft-client";
import { Builders, Transactions as NFTTransactions } from "@protokol/nft-exchange-crypto";

export const NFTAuctionCancel = async () => {
    // Configure manager and register transaction type
    Managers.configManager.setFromPreset("testnet");
    Managers.configManager.setHeight(2);
    Transactions.TransactionRegistry.registerTransactionType(NFTTransactions.NFTAuctionCancelTransaction);

    // Configure our API client
    const client = new NFTConnection("http://nft.protokol.com:4003/api");
    const passphrase = "clay harbor enemy utility margin pretty hub comic piece aerobic umbrella acquire";

    // Step 1: Retrieve the nonce of the sender wallet
    const senderWallet = await client.api("wallets").get(Identities.Address.fromPassphrase(passphrase));
    const senderNonce = Utils.BigNumber.make(senderWallet.body.data.nonce).plus(1);

    // Step 2: Create the transaction
    const transaction = new Builders.NFTAuctionCancelBuilder()
        .NFTAuctionCancelAsset({
            auctionId: "58dc9625ff7190dc3ff2dbf541a2bb2c8a85366f2cbe95d21ec9b8970f41d086",
        })
        .nonce(senderNonce.toFixed())
        .sign(passphrase);

    // Step 3: Broadcast the transaction
    const broadcastResponse = await client.api("transactions").create({ transactions: [transaction.build().toJson()] });

    // Step 4: Log the response
    console.log(JSON.stringify(broadcastResponse.body.data, null, 4));
};

```

### NFTBid - Creating and Broadcasting

```typescript
import { Identities, Managers, Transactions, Utils } from "@arkecosystem/crypto";
import { NFTConnection } from "@protokol/nft-client";
import { Builders, Transactions as NFTTransactions } from "@protokol/nft-exchange-crypto";

export const NFTBid = async () => {
    // Configure manager and register transaction type
    Managers.configManager.setFromPreset("testnet");
    Managers.configManager.setHeight(2);
    Transactions.TransactionRegistry.registerTransactionType(NFTTransactions.NFTBidTransaction);

    // Configure our API client
    const client = new NFTConnection("http://nft.protokol.com:4003/api");
    const passphrase = "clay harbor enemy utility margin pretty hub comic piece aerobic umbrella acquire";

    // Step 1: Retrieve the nonce of the sender wallet
    const senderWallet = await client.api("wallets").get(Identities.Address.fromPassphrase(passphrase));
    const senderNonce = Utils.BigNumber.make(senderWallet.body.data.nonce).plus(1);

    // Step 2: Create the transaction
    const transaction = new Builders.NFTBidBuilder()
        .NFTBidAsset({
            bidAmount: Utils.BigNumber.make("1100"),
            auctionId: "717ce9f6dff858c4972b067a1fce8ea72fb1c4ac60c4a75cc8e9993dbbe7541a",
        })
        .nonce(senderNonce.toFixed())
        .sign(passphrase);

    // Step 3: Broadcast the transaction
    const broadcastResponse = await client.api("transactions").create({ transactions: [transaction.build().toJson()] });

    // Step 4: Log the response
    console.log(JSON.stringify(broadcastResponse.body.data, null, 4));
};

```

### NFTBidCancel - Creating and Broadcasting

```typescript
import { Identities, Managers, Transactions, Utils } from "@arkecosystem/crypto";
import { NFTConnection } from "@protokol/nft-client";
import { Builders, Transactions as NFTTransactions } from "@protokol/nft-exchange-crypto";

export const NFTBidCancel = async () => {
    // Configure manager and register transaction type
    Managers.configManager.setFromPreset("testnet");
    Managers.configManager.setHeight(2);
    Transactions.TransactionRegistry.registerTransactionType(NFTTransactions.NFTBidCancelTransaction);

    // Configure our API client
    const client = new NFTConnection("http://nft.protokol.com:4003/api");
    const passphrase = "clay harbor enemy utility margin pretty hub comic piece aerobic umbrella acquire";

    // Step 1: Retrieve the nonce of the sender wallet
    const senderWallet = await client.api("wallets").get(Identities.Address.fromPassphrase(passphrase));
    const senderNonce = Utils.BigNumber.make(senderWallet.body.data.nonce).plus(1);

    // Step 2: Create the transaction
    const transaction = new Builders.NFTBidCancelBuilder()
        .NFTBidCancelAsset({
            bidId: "c67beef6edc35f81334e8bf825dbc735e8d579f8297509d74980756b9b9ff8fe",
        })
        .nonce(senderNonce.toFixed())
        .sign(passphrase);

    // Step 3: Broadcast the transaction
    const broadcastResponse = await client.api("transactions").create({ transactions: [transaction.build().toJson()] });

    // Step 4: Log the response
    console.log(JSON.stringify(broadcastResponse.body.data, null, 4));
};

```

### NFTAcceptTrade - Creating and Broadcasting

```typescript
import { Identities, Managers, Transactions, Utils } from "@arkecosystem/crypto";
import { NFTConnection } from "@protokol/nft-client";
import { Builders, Transactions as NFTTransactions } from "@protokol/nft-exchange-crypto";

export const NFTAcceptTrade = async () => {
    // Configure manager and register transaction type
    Managers.configManager.setFromPreset("testnet");
    Managers.configManager.setHeight(2);
    Transactions.TransactionRegistry.registerTransactionType(NFTTransactions.NFTAcceptTradeTransaction);

    // Configure our API client
    const client = new NFTConnection("http://nft.protokol.com:4003/api");
    const passphrase = "clay harbor enemy utility margin pretty hub comic piece aerobic umbrella acquire";

    // Step 1: Retrieve the nonce of the sender wallet
    const senderWallet = await client.api("wallets").get(Identities.Address.fromPassphrase(passphrase));
    const senderNonce = Utils.BigNumber.make(senderWallet.body.data.nonce).plus(1);

    // Step 2: Create the transaction
    const transaction = new Builders.NftAcceptTradeBuilder()
        .NFTAcceptTradeAsset({
            auctionId: "d8177d5c2a3eee46aea48fa5a8ce7c58c43c71909ac6cf9568e11065dc1f544a",
            bidId: "032383b3f5c541c117c3409fdb1545e7b34deb0f6922ef7a42c40867d24402d8",
        })
        .nonce(senderNonce.toFixed())
        .sign(passphrase);

    // Step 3: Broadcast the transaction
    const broadcastResponse = await client.api("transactions").create({ transactions: [transaction.build().toJson()] });

    // Step 4: Log the response
    console.log(JSON.stringify(broadcastResponse.body.data, null, 4));
};

```

