---
description: List of NFT Exchange Bid Endpoints.
---

# Bids

## All Bids

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/exchange/bids" path=" " %}
{% api-method-summary %}
/bids
{% endapi-method-summary %}

{% api-method-description %}
Return all bids
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="page" type="integer" required=false %}
The number of page that will be returned
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="integer" required=false %}
The number of resources per page
{% endapi-method-parameter %}

{% api-method-parameter name="orderBy" type="string" required=false %}
Order by specific parameter \(asc or desc\)  
Example: orderBy=id:asc
{% endapi-method-parameter %}

{% api-method-parameter name="transform" type="boolean" required=false %}
Returns modified or raw data
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "meta": {
    "totalCountIsEstimate": true,
    "count": 2,
    "pageCount": 1,
    "totalCount": 2,
    "next": null,
    "previous": null,
    "self": "/nft/exchange/bids?transform=true&page=1&limit=100",
    "first": "/nft/exchange/bids?transform=true&page=1&limit=100",
    "last": "/nft/exchange/bids?transform=true&page=1&limit=100"
  },
  "data": [
    {
      "id": "73f15a9d387035ac8f860e9f6bce63919735f8cf4eee05048ac31b935d3d69a1",
      "senderPublicKey": "02def27da9336e7fbf63131b8d7e5c9f45b296235db035f1f4242c507398f0f21d",
      "nftBid": {
        "auctionId": "08466d59b86622152c643558c03e4037454dcaf4d8188af876812c79d433ae20",
        "bidAmount": "150000000000"
      },
      "timestamp": {
        "epoch": 143238112,
        "unix": 1633339312,
        "human": "2021-10-04T09:21:52.000Z"
      }
    },
    {
      "id": "ce81232de97526c7be16dc66f7efba4f8f92a686e8b8d1250f48a87dacd45945",
      "senderPublicKey": "02def27da9336e7fbf63131b8d7e5c9f45b296235db035f1f4242c507398f0f21d",
      "nftBid": {
        "auctionId": "91221ffc0838fde5983e5ffe32c427b5720dc5703df6b89f1126fa7f62ebd964",
        "bidAmount": "150000000000"
      },
      "timestamp": {
        "epoch": 143238328,
        "unix": 1633339528,
        "human": "2021-10-04T09:25:28.000Z"
      }
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Examples

{% tabs %}
{% tab title="Curl" %}
```text
curl https://explorer.protokol.sh/api/nft/exchange/bids
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTExchangeApi("bids").getAllBids();

>>> Promise<ApiResponse<BidsResource>>
```
{% endtab %}
{% endtabs %}

## Bids By Id

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/exchange/bids/:id" path=" " %}
{% api-method-summary %}
/bids/:id
{% endapi-method-summary %}

{% api-method-description %}
Returns bid by id
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The identifier of the bid to be retrieved
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="transform" type="boolean" required=false %}
Returns modified or raw data
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "data": {
    "id": "73f15a9d387035ac8f860e9f6bce63919735f8cf4eee05048ac31b935d3d69a1",
    "senderPublicKey": "02def27da9336e7fbf63131b8d7e5c9f45b296235db035f1f4242c507398f0f21d",
    "nftBid": {
      "auctionId": "08466d59b86622152c643558c03e4037454dcaf4d8188af876812c79d433ae20",
      "bidAmount": "150000000000"
    },
    "timestamp": {
      "epoch": 143238112,
      "unix": 1633339312,
      "human": "2021-10-04T09:21:52.000Z"
    }
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 404,
  "error": "Not Found",
  "message": "Bid not found"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 422,
  "error": "Unprocessable Entity",
  "message": "\"id\" length must be 64 characters long"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Examples

{% tabs %}
{% tab title="Curl" %}
```text
curl https://explorer.protokol.sh/api/nft/exchange/bid/1d1757bc7e598fd73f0ec670e1f2c517d7d9a2a94d447bd5daa0a9384ebd4e7e
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTExchangeApi("bids").getBidById("VALID_ID");

>>> Promise<ApiResponse<BidsResource>>
```
{% endtab %}
{% endtabs %}

## Bids Wallet

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/exchange/bids/:id/wallets " path=" " %}
{% api-method-summary %}
/bids/:id/wallets
{% endapi-method-summary %}

{% api-method-description %}
Returns wallet owning the bid
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The identifier of the auction
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "data": {
    "address": "ANBkoGqWeTSiaEVgVzSKZd3jS7UWzv9PSo",
    "publicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "nft": {
      "collections": [
        ...
      ],
      "auctions": [
        {
          "auctionId": "08466d59b86622152c643558c03e4037454dcaf4d8188af876812c79d433ae20",
          "nftIds": [
            "4f1f337873d530838dba06c9ec256cfd8a2acf7a94e87fbb0cb4c7304d3e6788"
          ],
          "bids": [
            "6cb1e1b85a6a87108ae37b2e1ca94732bc609caa8ab6d992395b143e3d157cf9"
          ]
        }
      ],
      "lockedBalance": "0"
    }
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 404,
  "error": "Not Found",
  "message": "Bid not found or it was already accepted/canceled"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 422,
  "error": "Unprocessable Entity",
  "message": "\"id\" length must be 64 characters long"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Examples

{% tabs %}
{% tab title="Curl" %}
```text
curl https://explorer.protokol.sh/api/nft/exchange/bids/1d1757bc7e598fd73f0ec670e1f2c517d7d9a2a94d447bd5daa0a9384ebd4e7e/wallets
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTExchangeApi("auctions").getAuctionsWallets("VALID_ID");

>>> Promise<ApiResponse<AuctionsWallet>>
```
{% endtab %}
{% endtabs %}

## Search Bids

{% api-method method="post" host="https://explorer.protokol.sh/api/nft/exchange/bids/search" path=" " %}
{% api-method-summary %}
/bids/search
{% endapi-method-summary %}

{% api-method-description %}
Seach auctions
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="page" type="integer" required=false %}
The number of the page that will be returned
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="integer" required=false %}
The number of resources per page
{% endapi-method-parameter %}

{% api-method-parameter name="orderBy" type="string" required=false %}
Order by specific parameter \(asc or desc\)  
Example: orderBy=id:asc
{% endapi-method-parameter %}

{% api-method-parameter name="transform" type="boolean" required=false %}
Returns modified or raw data
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="senderPublicKey" type="string" required=false %}
Public key of a sender
{% endapi-method-parameter %}

{% api-method-parameter name="auctionId" type="array" required=false %}
Id of an auction
{% endapi-method-parameter %}

{% api-method-parameter name="bidAmount" type="string" required=false %}
Amount of a bid
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "meta": {
    "totalCountIsEstimate": true,
    "count": 3,
    "pageCount": 1,
    "totalCount": 3,
    "next": null,
    "previous": null,
    "self": "/nft/exchange/bids/search?transform=true&page=1&limit=100",
    "first": "/nft/exchange/bids/search?transform=true&page=1&limit=100",
    "last": "/nft/exchange/bids/search?transform=true&page=1&limit=100"
  },
  "data": [
    {
      "id": "73f15a9d387035ac8f860e9f6bce63919735f8cf4eee05048ac31b935d3d69a1",
      "senderPublicKey": "02def27da9336e7fbf63131b8d7e5c9f45b296235db035f1f4242c507398f0f21d",
      "nftBid": {
        "auctionId": "08466d59b86622152c643558c03e4037454dcaf4d8188af876812c79d433ae20",
        "bidAmount": "150000000000"
      },
      "timestamp": {
        "epoch": 143238112,
        "unix": 1633339312,
        "human": "2021-10-04T09:21:52.000Z"
      }
    },
    ...
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Examples

{% tabs %}
{% tab title="Curl" %}
```bash
curl --request POST \
  --url https://explorer.protokol.sh/api/nft/exchange/bids/search \
  --header 'content-type: application/json' \
  --data '{
      "bidAmount": "150000000000"
}'
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTExchangeApi("bids").searchByBid({
        auctionId: "VALID_AUCTION_ID",
        senderPublicKey: "VALID_SENDER_PUBLIC_KEY",
        bidAmount: "BID_AMOUNT",
});

>>> Promise<ApiResponse<BidCanceled>>
```
{% endtab %}
{% endtabs %}

## Canceled Bids

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/exchange/bids/canceled " path=" " %}
{% api-method-summary %}
/bids/canceled
{% endapi-method-summary %}

{% api-method-description %}
Returns canceled bids transactions
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="page" type="integer" required=false %}
The number of the page that will be returned
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="integer" required=false %}
The number of resources per page
{% endapi-method-parameter %}

{% api-method-parameter name="orderBy" type="string" required=false %}
Order by specific parameter \(asc or desc\)  
Example: orderBy=id:asc
{% endapi-method-parameter %}

{% api-method-parameter name="transform" type="boolean" required=false %}
Returns modified or raw data
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "meta": {
    "totalCountIsEstimate": true,
    "count": 1,
    "pageCount": 1,
    "totalCount": 1,
    "next": null,
    "previous": null,
    "self": "/nft/exchange/bids/canceled?transform=true&page=1&limit=100",
    "first": "/nft/exchange/bids/canceled?transform=true&page=1&limit=100",
    "last": "/nft/exchange/bids/canceled?transform=true&page=1&limit=100"
  },
  "data": [
    {
      "id": "59da5fbc385ff7952eeda4829f4f0f8c57ab39930c1a91ac5cecea2ea5f0a9a0",
      "senderPublicKey": "02def27da9336e7fbf63131b8d7e5c9f45b296235db035f1f4242c507398f0f21d",
      "nftBidCancel": {
        "bidId": "73f15a9d387035ac8f860e9f6bce63919735f8cf4eee05048ac31b935d3d69a1"
      },
      "timestamp": {
        "epoch": 143238184,
        "unix": 1633339384,
        "human": "2021-10-04T09:23:04.000Z"
      }
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Examples

{% tabs %}
{% tab title="Curl" %}
```text
curl https://explorer.protokol.sh/api/nft/exchange/bids/canceled
```
{% endtab %}
{% endtabs %}

## Canceled Bids By Id

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/exchange/bids/canceled/:id" path=" " %}
{% api-method-summary %}
/bids/canceled/:id
{% endapi-method-summary %}

{% api-method-description %}
Returns canceled bid transaction by id
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The identifer of canceled bid to be retrieved
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="transform" type="boolean" required=false %}
Returns modified or raw data
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "data": {
    "id": "59da5fbc385ff7952eeda4829f4f0f8c57ab39930c1a91ac5cecea2ea5f0a9a0",
    "senderPublicKey": "02def27da9336e7fbf63131b8d7e5c9f45b296235db035f1f4242c507398f0f21d",
    "nftBidCancel": {
      "bidId": "73f15a9d387035ac8f860e9f6bce63919735f8cf4eee05048ac31b935d3d69a1"
    },
    "timestamp": {
      "epoch": 143238184,
      "unix": 1633339384,
      "human": "2021-10-04T09:23:04.000Z"
    }
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 404,
  "error": "Not Found",
  "message": "Bid not found"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 422,
  "error": "Unprocessable Entity",
  "message": "\"id\" length must be 64 characters long"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Examples

{% tabs %}
{% tab title="Curl" %}
```text
curl https://explorer.protokol.sh/api/nft/exchange/bids/canceled/3c26dee62a937aaf49c25e64d2776117362e9dc30dd6f27c839081d1e44608bc
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTExchangeApi("bids").getCanceledBidById("VALID_ID");

>>> Promise<ApiResponse<BidCanceled>>
```
{% endtab %}
{% endtabs %}

