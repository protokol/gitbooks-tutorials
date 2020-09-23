---
description: Simple Examples Showing How To Trade Digital Assets
---

# How To Trade Digital Assets

Protokol NFT set comes with full trading capabilities built-in and tracked on the digital ledger. In the following section we are going to explain the basic trading process supported with code examples. 

## STEP 1. Auction Creation And Cancellation

We can open a new auction by using the NFTAuction Transaction Type. Auction can set the following fields:

* startAmount - minimal starting amount
* expiration - set in block height \(when we stop accepting bid for our items\)
* nftIds - list of owned items we want to auction

Only an auction owner can cancel an auction.

### How To Create An Auction

{% embed url="https://github.com/protokol/nft-plugins/blob/develop/packages/examples/src/exchange/nft-auction.ts" caption="NFTAuction Runnable Example" %}

#### Initialization

```typescript
import { Builders } from "@protokol/nft-exchange-crypto";
```

#### NFTAuction - Builder

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

### How To Cancel An Auction

{% embed url="https://github.com/protokol/nft-plugins/blob/develop/packages/examples/src/exchange/nft-auction-cancel.ts" caption="NFTAuctionCancel Runnable Example" %}

To cancel an auction we need to specify **auctionId** and be **owners** of the specific auction.

#### NFTAuctionCancel - Builder

```typescript
new Builders.NFTAuctionCancelBuilder()
        .NFTAuctionCancelAsset({
            auctionId: "58dc9625ff7190dc3ff2dbf541a2bb2c8a85366f2cbe95d21ec9b8970f41d086",
        })
        .nonce("1")
        .sign("SENDER_PASSPHRASE");

```

## STEP 2. Biding On Auction Items

We can create a bid for NFT items being available for sale via NFTAuctions \(Step 1\). To bid on a specific auction we need to define the following fields:

* bidAmount \(our bidAmount\) - needs to be higher that auction start Amount
* auctionId - id of auction we are bidding for.

{% hint style="info" %}
When a bid is issued, the users balance is locked for the duration of this bid. The user can always check their locked balance on the wallet endpoint via exchange endpoints. 
{% endhint %}

### How To Create A Bid

{% embed url="https://github.com/protokol/nft-plugins/blob/develop/packages/examples/src/exchange/nft-bid-cancel.ts" caption="NFTBid Runnable Example" %}

#### NFTBid - Builder

```typescript
new Builders.NFTBidBuilder()
        .NFTBidAsset({
            bidAmount: Utils.BigNumber.make("1100"),
            auctionId: "717ce9f6dff858c4972b067a1fce8ea72fb1c4ac60c4a75cc8e9993dbbe7541a",
        })
        .nonce("1")
        .sign("SENDER_PASSPHRASE");
```

### How To Cancel A Bid

{% embed url="https://github.com/protokol/nft-plugins/blob/develop/packages/examples/src/exchange/nft-bid-cancel.ts" caption="NFTBidCancel Runnable Example" %}

To cancel a bid we need to specify a **bidId** and be **owners** of the specific bid.

#### NFTBidCancel - Builder

```typescript
new Builders.NFTBidCancelBuilder()
        .NFTBidCancelAsset({
            bidId: "c67beef6edc35f81334e8bf825dbc735e8d579f8297509d74980756b9b9ff8fe",
        })
        .nonce("1")
        .sign("SENDER_PASSPHRASE");
```

## STEP 3. Accepting A Trade

We can accept a trade by specifying the sub-transactions related to closing a specific trade. These transactions are:

* auctionId - id of a NFTAuction Transaction \(Step 1\)
* bidId - id of a NFTBid Transaction \(Step 2\)

Both IDs correspond with the seller request and bidder offerings. The seller is responsible for which bid he is willing to accept. 

{% hint style="info" %}
When a trade is accepted all other bids are cancelled, and locked balances are returned to the bidders.
{% endhint %}

### How to Accept A Trade

{% embed url="https://github.com/protokol/nft-plugins/blob/develop/packages/examples/src/exchange/nft-accept-trade.ts" caption="NFTAcceptTrade Runnable Example" %}

```typescript
new Builders.NftAcceptTradeBuilder()
        .NFTAcceptTradeAsset({
            auctionId: "d8177d5c2a3eee46aea48fa5a8ce7c58c43c71909ac6cf9568e11065dc1f544a",
            bidId: "032383b3f5c541c117c3409fdb1545e7b34deb0f6922ef7a42c40867d24402d8",
        })
        .nonce("1")
        .sign("SENDER_PASSPHRASE");
```

