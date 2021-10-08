---
description: List of NFT Exchange Trade Endpoints
---

# Trades

## All Trades

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/exchange/trades" path=" " %}
{% api-method-summary %}
/auctions
{% endapi-method-summary %}

{% api-method-description %}
Returns all trade transactions
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
    "self": "/nft/exchange/trades?transform=true&page=1&limit=100",
    "first": "/nft/exchange/trades?transform=true&page=1&limit=100",
    "last": "/nft/exchange/trades?transform=true&page=1&limit=100"
  },
  "data": [
    {
      "id": "56d68daa8eaa9182fa0dc4d7b484247bc2f4c2e5ead6911d8ccc0f79d4c2876c",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "completedTrade": {
        "auctionId": "91221ffc0838fde5983e5ffe32c427b5720dc5703df6b89f1126fa7f62ebd964",
        "bidId": "ce81232de97526c7be16dc66f7efba4f8f92a686e8b8d1250f48a87dacd45945"
      },
      "timestamp": {
        "epoch": 143238352,
        "unix": 1633339552,
        "human": "2021-10-04T09:25:52.000Z"
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
curl https://explorer.protokol.sh/api/nft/exchange/trades
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTExchangeApi("trades").all();

>>> Promise<ApiResponse<TradesResource>>
```
{% endtab %}
{% endtabs %}

## Trade By Id

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/exchange/trades/:id" path=" " %}
{% api-method-summary %}
/trades/:id
{% endapi-method-summary %}

{% api-method-description %}
Returns trade by id
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The identifier of the trade to be retrieved
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
    "id": "56d68daa8eaa9182fa0dc4d7b484247bc2f4c2e5ead6911d8ccc0f79d4c2876c",
    "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "completedTrade": {
      "auction": {
        "id": "91221ffc0838fde5983e5ffe32c427b5720dc5703df6b89f1126fa7f62ebd964",
        "nftIds": [
          "aa4a880e053644fee1475616a874e6689c2dfdbca0fb0a3db5a3f091c6e07d80"
        ],
        "startAmount": "100000000000",
        "expiration": {
          "blockHeight": 20000
        }
      },
      "bid": {
        "id": "ce81232de97526c7be16dc66f7efba4f8f92a686e8b8d1250f48a87dacd45945",
        "auctionId": "91221ffc0838fde5983e5ffe32c427b5720dc5703df6b89f1126fa7f62ebd964",
        "bidAmount": "150000000000"
      }
    },
    "timestamp": {
      "epoch": 143238352,
      "unix": 1633339552,
      "human": "2021-10-04T09:25:52.000Z"
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
  "message": "Trade was not found!"
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
curl https://explorer.protokol.sh/api/nft/exchange/trade/1d1757bc7e598fd73f0ec670e1f2c517d7d9a2a94d447bd5daa0a9384ebd4e7e
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTExchangeApi("trades").get("VALID_ID");

>>> Promise<ApiResponse<TradeById>>
```
{% endtab %}
{% endtabs %}

## Search Trades

{% api-method method="post" host="https://explorer.protokol.sh/api/nft/exchange/trades/search" path=" " %}
{% api-method-summary %}
/auctions/search
{% endapi-method-summary %}

{% api-method-description %}
Search trades
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

{% api-method-parameter name="auctionId" type="string" required=false %}
Id of an auction
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
    "count": 3,
    "pageCount": 1,
    "totalCount": 3,
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
  --url https://explorer.protokol.sh/api/nft/exchange/trades/search \
  --header 'content-type: application/json' \
  --data '{
          "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37"
}'
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTExchangeApi("trades").search({
        auctionId: "VALID_AUCTION_ID",
        bidId: "VALID_BID_ID",
        senderPublicKey: "VALID_SENDER_PUBLIC_KEY",
});

>>> Promise<ApiResponseWithPagination<TradesResource[]>>
```
{% endtab %}
{% endtabs %}

