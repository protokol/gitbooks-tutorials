# Crypto Examples

## NFT Base Builders

### Initialization

```typescript
import { Builders } from "@protokol/nft-base-crypto";
```

### NFTRegisterCollection - Builder

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

### NFTCreate - Builder

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

### NFTTransfer - Builder

```typescript
new Builders.NFTTransferBuilder()
        .NFTTransferAsset({
            recipientId: "RECIPIENT_ADDRESS",
            nftIds: ["7373bbe5524898faec40bfcd12c6161981771f3be6426404208784831f4b0d02"],
        })
        .nonce("1")
        .sign("SENDER_PASSPHRASE");

```

### NFTBurn - Builder

```typescript
 new Builders.NFTBurnBuilder()
        .NFTBurnAsset({
            nftId: "6f252f11b119e00a5364d37670623d1b6be562f577984c819237ca4668e2897e",
        })
        .nonce("1")
        .sign("SENDER_PASSPHRASE");
```

## NFT Exchange Builders

### Initialization

```typescript
import { Builders } from "@protokol/nft-exchange-crypto";
```

### NFTAuction - Builder

```typescript
new Builders.NFTAuctionBuilder()
        .NFTAuctionAsset({
            startAmount: Utils.BigNumber.make("1000"),
            expiration: {
                blockHeight: 1000000,
            },
            nftIds: ["77c0cc9bbb26c69c95e7bd12ca7e2590ea70417eaf8f593905fd30b440ec8458"],
        })
        .nonce("1")
        .sign("SENDER_PASSPHRASE");
```

### NFTAuctionCancel - Builder

```typescript
new Builders.NFTAuctionCancelBuilder()
        .NFTAuctionCancelAsset({
            auctionId: "58dc9625ff7190dc3ff2dbf541a2bb2c8a85366f2cbe95d21ec9b8970f41d086",
        })
        .nonce("1")
        .sign("SENDER_PASSPHRASE");

```

### NFTBid - Builder

```typescript
new Builders.NFTBidBuilder()
        .NFTBidAsset({
            bidAmount: Utils.BigNumber.make("1100"),
            auctionId: "717ce9f6dff858c4972b067a1fce8ea72fb1c4ac60c4a75cc8e9993dbbe7541a",
        })
        .nonce("1")
        .sign("SENDER_PASSPHRASE");
```

### NFTBidCancel - Builder

```typescript
new Builders.NFTBidCancelBuilder()
        .NFTBidCancelAsset({
            bidId: "c67beef6edc35f81334e8bf825dbc735e8d579f8297509d74980756b9b9ff8fe",
        })
        .nonce("1")
        .sign("SENDER_PASSPHRASE");
```

### NFTAcceptTrade - Builder

```typescript
new Builders.NftAcceptTradeBuilder()
        .NFTAcceptTradeAsset({
            auctionId: "d8177d5c2a3eee46aea48fa5a8ce7c58c43c71909ac6cf9568e11065dc1f544a",
            bidId: "032383b3f5c541c117c3409fdb1545e7b34deb0f6922ef7a42c40867d24402d8",
        })
        .nonce("1")
        .sign("SENDER_PASSPHRASE");
```

