---
description: Examples Showing How To Create Digital Assets (NFTs)
---

# How To Create Digital Assets

## **STEP 1. Register A New Collection Of Digital Assets**

NFTRegisterCollection Transaction Types enables us to define a new type of digitial assets by defining its structure. The structure is defined in the form of a standard JSONSchema \(see example below\). After the digital asset collection is registered we can create\(mine\) tokens with the help of NFTCreate transaction type. We need to define:

* asset name
* asset description
* maximum supply \(optional\)
* jsonSchema
* allowedIssuers - if empty anyone can create/mine a new asset

### How To Use NFTRegisterCollection Example:

#### Initialization

```typescript
import { Builders } from "@protokol/nft-base-crypto";
```

#### NFTRegisterCollection - Builder

```typescript
new Builders.NFTRegisterCollectionBuilder()
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
    .nonce("1")
    .sign("SENDER_PASSPHRASE");
```

## STEP 2. Create New Digital Assets

We can create \(mine\) new digital assets from the genesis wallet \(the wallet that registered the new collection in STEP 1. To create a digital asset we need its asset type, that is the collection id we registered with NFTRegisterCollection transaction. We need to specify:

* collection id
* token attributes \(need to comply with the registered JSONSchema from collection id\)

After token is created it lives inside the genesis wallet, until it is transfered to a trading address, or to a new owner. 

### How To Use NFTCreate Transaction:

```typescript
new Builders.NFTCreateBuilder()
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
        .nonce("1")
        .sign("SENDER_PASSPHRASE");
```

## STEP 3. Transfer Digital Assets

We can transfer multiple owned digital assets. See example below for NFT Transfer Transaction Type.

### How To Use NFTTransfer Transaction:

```typescript
new Builders.NFTTransferBuilder()
        .NFTTransferAsset({
            recipientId: "RECIPIENT_ADDRESS",
            nftIds: ["7373bbe5524898faec40bfcd12c6161981771f3be6426404208784831f4b0d02"],
        })
        .nonce("1")
        .sign("SENDER_PASSPHRASE");

```

## STEP 4. Burn Digital Assets

Our NFT plugin set also enables burning capability for digital assets. This is usefull with loyalty programs and expiring trading cards or gaming card functionality - where asset is destroyed when used. Only token owner can burn/destroy a digital assets. Digital asset or usage history is still visible on the blockchain. 

### How To Use NFTBurn Transaction:

```typescript
 new Builders.NFTBurnBuilder()
        .NFTBurnAsset({
            nftId: "6f252f11b119e00a5364d37670623d1b6be562f577984c819237ca4668e2897e",
        })
        .nonce("1")
        .sign("SENDER_PASSPHRASE");
```

## 
