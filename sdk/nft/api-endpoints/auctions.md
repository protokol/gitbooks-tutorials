---
description: List of NFT Exchange Auction Endpoints.
---

# Auctions

## All Auctions

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/exchange/auctions" path=" " %}
{% api-method-summary %}
/auctions
{% endapi-method-summary %}

{% api-method-description %}
Returns all active auctions that have not been canceled or closed with succesfull NFTAcceptTrade transaction.
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

{% api-method-parameter name="expired" type="boolean" required=false %}
If true include expired \(not canceled or accapted\) auctions
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
    "totalCountIsEstimate": false,
    "count": 1,
    "pageCount": 1,
    "totalCount": 1,
    "next": null,
    "previous": null,
    "self": "/nft/exchange/auctions?transform=true&expired=false&page=1&limit=100",
    "first": "/nft/exchange/auctions?transform=true&expired=false&page=1&limit=100",
    "last": "/nft/exchange/auctions?transform=true&expired=false&page=1&limit=100"
  },
  "data": [
    {
      "id": "08466d59b86622152c643558c03e4037454dcaf4d8188af876812c79d433ae20",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "nftAuction": {
        "nftIds": [
          "4f1f337873d530838dba06c9ec256cfd8a2acf7a94e87fbb0cb4c7304d3e6788"
        ],
        "startAmount": "100000000000",
        "expiration": {
          "blockHeight": 20000
        },
        "status": "IN_PROGRESS"
      },
      "timestamp": {
        "epoch": 143238008,
        "unix": 1633339208,
        "human": "2021-10-04T09:20:08.000Z"
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
curl https://explorer.protokol.sh/api/nft/exchange/auctions
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTExchangeApi("auctions").getAllAuctions();

>>> Promise<ApiResponseWithPagination<AuctionsResource[]>>
```
{% endtab %}
{% endtabs %}

## Auction By Id

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/exchange/auctions/:id" path=" " %}
{% api-method-summary %}
/auctions/:id
{% endapi-method-summary %}

{% api-method-description %}
Returns auction by id
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The identifier of the auction to be retrieved
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
    "id": "08466d59b86622152c643558c03e4037454dcaf4d8188af876812c79d433ae20",
    "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "nftAuction": {
      "nftIds": [
        "4f1f337873d530838dba06c9ec256cfd8a2acf7a94e87fbb0cb4c7304d3e6788"
      ],
      "startAmount": "100000000000",
      "expiration": {
        "blockHeight": 20000
      }
    },
    "timestamp": {
      "epoch": 143238008,
      "unix": 1633339208,
      "human": "2021-10-04T09:20:08.000Z"
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
  "message": "Auction not found"
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
curl https://explorer.protokol.sh/api/nft/exchange/auctions/1d1757bc7e598fd73f0ec670e1f2c517d7d9a2a94d447bd5daa0a9384ebd4e7e
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTExchangeApi("auctions").getAuctionById("VALID_ID");

>>>  Promise<ApiResponse<AuctionsResource>>
```
{% endtab %}
{% endtabs %}

## Auctions Wallet

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/exchange/auctions/:id/wallets " path=" " %}
{% api-method-summary %}
/auctions/:id/wallets
{% endapi-method-summary %}

{% api-method-description %}
Returns wallet owning the auction
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
        {
          "collectionId": "8643026a0997dc9fe74ce4aa11f522ecff651fa72ecf0127a0665fd52535bc1b",
          "currentSupply": 3,
          "nftCollectionAsset": {
            "name": "AREX Defense Handguns",
            "description": "AREX weapons sales",
            "maximumSupply": 999,
            "jsonSchema": {
              "type": "object",
              "additionalProperties": false,
              "required": [
                "name",
                "description",
                "serialNumber",
                "caliber",
                "length",
                "height",
                "width",
                "barrelLength"
              ],
              "properties": {
                "name": {
                  "type": "string",
                  "maxLength": 120,
                  "minLength": 1
                },
                "description": {
                  "type": "string",
                  "maxLength": 3000,
                  "minLength": 1
                },
                "serialNumber": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "caliber": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "length": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "height": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "width": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "barrelLength": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "weight": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "weightWithMag": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "frameColors": {
                  "type": "string",
                  "maxLength": 255,
                  "minLength": 1
                },
                "slide": {
                  "type": "string",
                  "maxLength": 255,
                  "minLength": 1
                },
                "slights": {
                  "type": "string",
                  "maxLength": 255,
                  "minLength": 1
                },
                "frame": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "firingPinSafety": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "triggerSafety": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "ambidextrousManualSafety": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "ipfsImageHash": {
                  "type": "string",
                  "maxLength": 255,
                  "minLength": 1
                }
              }
            }
          }
        },
       ...
      ],
      "auctions": [
        {
          "auctionId": "08466d59b86622152c643558c03e4037454dcaf4d8188af876812c79d433ae20",
          "nftIds": [
            "4f1f337873d530838dba06c9ec256cfd8a2acf7a94e87fbb0cb4c7304d3e6788"
          ],
          "bids": []
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
  "message": "Auction not found or it was already completed/canceled"
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
curl https://explorer.protokol.sh/api/nft/exchange/auctions/1d1757bc7e598fd73f0ec670e1f2c517d7d9a2a94d447bd5daa0a9384ebd4e7e/wallets
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTExchangeApi("auctions").getAuctionsWallets("VALID_ID");

>>> Promise<ApiResponse<AuctionsWallet>>
```
{% endtab %}
{% endtabs %}

## Search Auctions

{% api-method method="post" host="https://explorer.protokol.sh/api/nft/exchange/auctions/search" path=" " %}
{% api-method-summary %}
/auctions/search
{% endapi-method-summary %}

{% api-method-description %}
Search auctions
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

{% api-method-parameter name="onlyActive" type="boolean" required=false %}
Only returns not canceled or not closed auctions
{% endapi-method-parameter %}

{% api-method-parameter name="expired" type="boolean" required=false %}
Extends onlyActive, if true include expired auctions
{% endapi-method-parameter %}

{% api-method-parameter name="includeBids" type="boolean" required=false %}
If true includes auction bids
{% endapi-method-parameter %}

{% api-method-parameter name="canceledBids" type="boolean" required=false %}
Extends includeBids, if true include canceled bids
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="senderPublicKey" type="string" required=false %}
Public key of a sender
{% endapi-method-parameter %}

{% api-method-parameter name="nftIds" type="array" required=false %}
Ids of nfts
{% endapi-method-parameter %}

{% api-method-parameter name="startAmount" type="string" required=false %}
Start amount of auctions
{% endapi-method-parameter %}

{% api-method-parameter name="expiration: { blockHeight}" type="object" required=false %}
Block height expiration
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
    "totalCountIsEstimate": false,
    "count": 2,
    "pageCount": 1,
    "totalCount": 2,
    "next": null,
    "previous": null,
    "self": "/nft/exchange/auctions/search?transform=true&onlyActive=false&expired=false&includeBids=false&canceledBids=false&page=1&limit=100",
    "first": "/nft/exchange/auctions/search?transform=true&onlyActive=false&expired=false&includeBids=false&canceledBids=false&page=1&limit=100",
    "last": "/nft/exchange/auctions/search?transform=true&onlyActive=false&expired=false&includeBids=false&canceledBids=false&page=1&limit=100"
  },
  "data": [
    {
      "id": "877db0e352e38c27aede0b999f11afb0185fa41ffc2d1058ec288bc374d943a0",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "nftAuction": {
        "nftIds": [
          "4f1f337873d530838dba06c9ec256cfd8a2acf7a94e87fbb0cb4c7304d3e6788"
        ],
        "startAmount": "10000000000",
        "expiration": {
          "blockHeight": 20000
        },
        "status": "CANCELED"
      },
      "timestamp": {
        "epoch": 143237784,
        "unix": 1633338984,
        "human": "2021-10-04T09:16:24.000Z"
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
  --url https://explorer.protokol.sh/api/nft/exchange/auctions/search \
  --header 'content-type: application/json' \
  --data '{
      "nftIds": ["238d98bd751025decc853a46da8fb995c68a9684a4156bcfa414e7596b6e73b1"]
  }'
```
{% endtab %}

{% tab title="Typescript" %}
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
{% endtab %}
{% endtabs %}

## Canceled Auctions

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/exchange/auctions/canceled " path=" " %}
{% api-method-summary %}
/auctions/canceled
{% endapi-method-summary %}

{% api-method-description %}
Returns canceled auctions transactions
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
    "self": "/nft/exchange/auctions/canceled?transform=true&page=1&limit=100",
    "first": "/nft/exchange/auctions/canceled?transform=true&page=1&limit=100",
    "last": "/nft/exchange/auctions/canceled?transform=true&page=1&limit=100"
  },
  "data": [
    {
      "id": "6d60ff9503ae3aea29f2f48df586410c809af6aeea698967469f3b81b880c426",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "nftAuctionCancel": {
        "auctionId": "877db0e352e38c27aede0b999f11afb0185fa41ffc2d1058ec288bc374d943a0"
      },
      "timestamp": {
        "epoch": 143237848,
        "unix": 1633339048,
        "human": "2021-10-04T09:17:28.000Z"
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
curl https://explorer.protokol.sh/api/nft/exchange/auctions/canceled
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTExchangeApi("auctions").getAllCanceledAuctions();

>>> Promise<ApiResponseWithPagination<AuctionCanceled[]>>
```
{% endtab %}
{% endtabs %}

## Canceled Auctions By Id

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/exchange/auctions/canceled/:id" path=" " %}
{% api-method-summary %}
/auctions/canceled/:id
{% endapi-method-summary %}

{% api-method-description %}
Returns canceled auction transaction by id
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The identifer of canceled auction to be retrieved
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

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Examples

{% tabs %}
{% tab title="Curl" %}
```text
curl https://explorer.protokol.sh/api/nft/exchange/auctions/canceled/3c26dee62a937aaf49c25e64d2776117362e9dc30dd6f27c839081d1e44608bc
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTExchangeApi("auctions").getCanceledAuctionById("VALID_ID");

>>> Promise<ApiResponse<AuctionCanceled>>
```
{% endtab %}
{% endtabs %}

