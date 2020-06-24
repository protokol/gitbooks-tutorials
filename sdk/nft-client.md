---
description: A Light Typescript Client Supporting NFT and Public ARK REST API
---

# NFT Client

## Prerequisites <a id="prerequisites"></a>

Before we get started we need to make sure that all of the required dependencies are installed.

### [yarn](https://classic.yarnpkg.com/lang/en/)

```text
yarn add @protokol/nft-client
```

## Initialization

```typescript
import { NFTConnection } from "./nft-connection";

const connection = new NFTConnection("http://nft.protokol.com:4003/api");
```

## NFT Base Endpoints

## Collections

### List All Collections

```typescript
const response = connection.NFTBaseApi("collections").all();

>>> Promise<ApiResponseWithPagination<CollectionsResource[]>>
```

### Get Collection By Id

```typescript
const response = connection.NFTBaseApi("collections").get("VALID_ID");

>>> Promise<ApiResponse<CollectionsResource>>
```

### Get Schema By Id 

```typescript
const response = connection.NFTBaseApi("collections").getSchema("VALID_ID");

>>> Promise<ApiResponse<Schema>>
```

### Get Collections Wallet 

```typescript
const response = connection.NFTBaseApi("collections").wallet("VALID_ID");

>>> Promise<ApiResponse<CollectionsWallet>>
```

### Search Collections

```typescript
const response = connection.NFTBaseApi("collections").searchByCollections({
     jsonSchema: {
      "VALID_JSON_OBJECT"
      },
});
    
    >>> Promise<ApiResponseWithPagination<CollectionsResource[]>>
```

### Search Asset By Collection Id 

```typescript
const response = connection.NFTBaseApi("collections").assetByCollectionId("VALID_ID");

>>> Promise<ApiResponseWithPagination<CollectionsAsset[]>>
```

## Assets

### Return All Assets

```typescript
const response = connection.NFTBaseApi("assets").all();

>>> Promise<ApiResponseWithPagination<AssetsResource[]>>
```

### Return Asset By Id

```typescript
const response = connection.NFTBaseApi("assets").get("VALID_ID");

>>> Promise<ApiResponse<AssetsResource>> 
```

### Return Assets Wallet

```typescript
const response = connection.NFTBaseApi("assets").wallet("VALID_ID");

>>> Promise<ApiResponse<AssetsWallet>>
```

### Search By Asset

```typescript
const response = connection.NFTBaseApi("assets").searchByAsset({
    "VALID_JSON_OBJECT"
});

>>> Promise<ApiResponseWithPagination<AssetsResource[]>>
```

## Transfers

### Return All Transfers

```typescript
const response = connection.NFTBaseApi("transfers").all();

>>> Promise<ApiResponseWithPagination<TransfersResource[]>>
```

### Return Transfer By Id

```typescript
const response = connection.NFTBaseApi("transfers").get("VALID_ID");

>>> Promise<ApiResponse<TransfersResource>>
```

## Burns

### Return All Burns

```typescript
const response = connection.NFTBaseApi("burns").all();

>>> Promise<ApiResponseWithPagination<BurnsResource[]>>
```

### Return Burn By Id

```typescript
const response = connection.NFTBaseApi("burns").get("VALID_ID");

>>> Promise<ApiResponse<BurnsResource>> 
```

## Configurations

### Return Base Configurations

```typescript
const response = connection.NFTBaseApi("configurations").index();

>>> Promise<ApiResponse<ConfigurationsResource>>
```



## NFT Exchange Endpoints

## Auctions

### Return All Auctions

```typescript
const response = connection.NFTExchangeApi("auctions").getAllAuctions();

>>> Promise<ApiResponseWithPagination<AuctionsResource[]>>
```

### Return Auction By Id

```typescript
const response = connection.NFTExchangeApi("auctions").getAuctionById("VALID_ID");

>>>  Promise<ApiResponse<AuctionsResource>>
```

### Return Auctions Wallet

```typescript
const response = connection.NFTExchangeApi("auctions").getAuctionsWallets("VALID_ID");

>>> Promise<ApiResponse<AuctionsWallet>>
```

### Search By Asset

```typescript
    const response = connection.NFTExchangeApi("auctions").searchByAsset({
        nftIds: ["VALID_NFT_IDS"],
        senderPublicKey: "VALID_SENDER_PUBLIC_KEY",
        startAmount: "START_AMOUNT",
        expiration: {
            blockHeight: BLOCK_HEIGHT,
        },
    });
    
    >>> Promise<ApiResponseWithPagination<AuctionsResource[]>>
```

### Return All Canceled Auctions

```typescript
const response = connection.NFTExchangeApi("auctions").getAllCanceledAuctions();

>>> Promise<ApiResponseWithPagination<AuctionCanceled[]>>
```

### Return Canceled Auction By Id

```typescript
const response = connection.NFTExchangeApi("auctions").getCanceledAuctionById("VALID_ID");

>>> Promise<ApiResponse<AuctionCanceled>>
```

## Bids

### Return All Bids

```typescript
const response = connection.NFTExchangeApi("bids").getAllBids();

>>> Promise<ApiResponse<BidsResource>> 
```

### Return Bid By Id

```typescript
const response = connection.NFTExchangeApi("bids").getBidById("VALID_ID");

>>> Promise<ApiResponse<BidsResource>>
```

### Return Bids Wallet

```typescript
const response = connection.NFTExchangeApi("bids").getBidsWallets("VALID_ID");

>>> Promise<ApiResponse<BidsWallet>>
```

### Search Bid

```typescript
const response = connection.NFTExchangeApi("bids").searchByBid({
        auctionId: "VALID_AUCTION_ID",
        senderPublicKey: "VALID_SENDER_PUBLIC_KEY",
        bidAmount: "BID_AMOUNT",
});

>>> Promise<ApiResponse<BidCanceled>>
```

### Return All Canceled Bids

```typescript
const response = connection.NFTExchangeApi("bids").getCanceledBidById("VALID_ID");

>>> Promise<ApiResponse<BidCanceled>>
```

## Trades

### Return All Trades

```typescript
const response = connection.NFTExchangeApi("trades").all();

>>> Promise<ApiResponse<TradesResource>>
```

### Return Trade By Id 

```typescript
const response = connection.NFTExchangeApi("trades").get("VALID_ID");

>>> Promise<ApiResponse<TradeById>>
```

### Search Trade

```typescript
const response = connection.NFTExchangeApi("trades").search({
        auctionId: "VALID_AUCTION_ID",
        bidId: "VALID_BID_ID",
        senderPublicKey: "VALID_SENDER_PUBLIC_KEY",
});

>>> Promise<ApiResponseWithPagination<TradesResource[]>>
```

## Configurations

```typescript
const response = connection.NFTExchangeApi("configurations").index();

>>> Promise<ApiResponse<ConfigurationsResource>>
```

