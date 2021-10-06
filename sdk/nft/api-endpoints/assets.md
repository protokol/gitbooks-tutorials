---
description: List of NFT Base Assets API Endpoints.
---

# Assets

## All Assets

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/assets" path=" " %}
{% api-method-summary %}
/assets
{% endapi-method-summary %}

{% api-method-description %}
Returns all Assets
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="page" type="integer" required=false %}
The number of page to be returned
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="integer" required=false %}
The number of transaction per page
{% endapi-method-parameter %}

{% api-method-parameter name="orderBy" type="string" required=false %}
Order by specific parameter \(asc or desc\)  
Example: orderBy=id:asc
{% endapi-method-parameter %}

{% api-method-parameter name="transform" type="boolean" required=false %}
Transform to raw response
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
    "count": 3,
    "pageCount": 1,
    "totalCount": 3,
    "next": null,
    "previous": null,
    "self": "/nft/assets?transform=true&page=1&limit=100",
    "first": "/nft/assets?transform=true&page=1&limit=100",
    "last": "/nft/assets?transform=true&page=1&limit=100"
  },
  "data": [
    {
      "id": "f811518958861d4c1e72943f646b1bd848f606e6cc9bd6300480e6a0b501cf47",
      "ownerPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "collectionId": "8643026a0997dc9fe74ce4aa11f522ecff651fa72ecf0127a0665fd52535bc1b",
      "attributes": {
        "name": "AREX ALPHA",
        "description": "THE AREX ALPHA IS THE NEXT EVOLUTIONARY STEP IN THE AREX HANDGUN FAMILY. IT IS A DIRECT DESCENDANT OF THE AREX ZERO 1 AND HAS INHERITED ITS TOUGHNESS AND RELIABILITY. LISTENING TO THE PRACTICAL SHOOTERS, AREX DESIGNED AND DEVELOPED A PISTOL THAT EXCELS IN COMPETITIVE PRACTICAL SHOOTING AS WELL AS IN TACTICAL SCENARIOS. WITH THE ELUSIVE AND ALL IMPORTANT SHOOTABILITY BEING AREXS PRIMARY GOAL, A STEEL FRAME WAS USED IN PLACE OF AN ALUMINUM ONE. A REENGINEERED GRIP RESULTS IN SHORTER TRIGGER REACH AND NOTABLY HIGHER HAND POSITION. AN UNDERCUT TRIGGER GUARD AND EXTENDED BEAVERTAIL COMPLETE THE ERGONOMIC TRANSFORMATION. THE LONG SLIDE HOUSES A FIVE INCH BARREL, PROVIDING A LONGER LINE OF SIGHT FOR FASTER AND MORE ACCURATE SHOTS. THE SLIDE HAS BEEN LIGHTENED SIGNIFICANTLY UTILIZING LIGHTENING CUTS TO ACCOMPLISH FASTER CYCLING.",
        "serialNumber": "6789897676898976",
        "caliber": "9 x 19 mm",
        "length": "226 mm // 8.9 inches",
        "height": "155 mm // 6.1 inches",
        "width": "42 mm // 1.65 inches",
        "barrelLength": "127 mm // 5.0 inches",
        "weight": "1202 g // 42.3 oz",
        "frameColors": "Nitrocarburized steel // Graphite black color // Blue // Red",
        "slide": "Nitrocarburized steel // Graphite black color",
        "slights": "Fiber optic front and fully adjustable black rear sight",
        "ipfsImageHash": "QmPbvs8G1jVaH6iHBUC2W1YnwY9AhzD98ydVqnhG9KMej1"
      },
      "timestamp": {
        "epoch": 143237168,
        "unix": 1633338368,
        "human": "2021-10-04T09:06:08.000Z"
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
```text
curl https://explorer.protokol.sh/api/nft/assets
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTBaseApi("assets").all();

>>> Promise<ApiResponseWithPagination<AssetsResource[]>>
```
{% endtab %}
{% endtabs %}

## Asset by id

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/assets/:id   " path=" " %}
{% api-method-summary %}
/assets/:id
{% endapi-method-summary %}

{% api-method-description %}
Returns asset by id
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The identifier of the asset to be retrieved
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="transform" type="boolean" required=false %}
Transform to raw response
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
    "id": "f811518958861d4c1e72943f646b1bd848f606e6cc9bd6300480e6a0b501cf47",
    "ownerPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "collectionId": "8643026a0997dc9fe74ce4aa11f522ecff651fa72ecf0127a0665fd52535bc1b",
    "attributes": {
      "name": "AREX ALPHA",
      "description": "THE AREX ALPHA IS THE NEXT EVOLUTIONARY STEP IN THE AREX HANDGUN FAMILY. IT IS A DIRECT DESCENDANT OF THE AREX ZERO 1 AND HAS INHERITED ITS TOUGHNESS AND RELIABILITY. LISTENING TO THE PRACTICAL SHOOTERS, AREX DESIGNED AND DEVELOPED A PISTOL THAT EXCELS IN COMPETITIVE PRACTICAL SHOOTING AS WELL AS IN TACTICAL SCENARIOS. WITH THE ELUSIVE AND ALL IMPORTANT SHOOTABILITY BEING AREXS PRIMARY GOAL, A STEEL FRAME WAS USED IN PLACE OF AN ALUMINUM ONE. A REENGINEERED GRIP RESULTS IN SHORTER TRIGGER REACH AND NOTABLY HIGHER HAND POSITION. AN UNDERCUT TRIGGER GUARD AND EXTENDED BEAVERTAIL COMPLETE THE ERGONOMIC TRANSFORMATION. THE LONG SLIDE HOUSES A FIVE INCH BARREL, PROVIDING A LONGER LINE OF SIGHT FOR FASTER AND MORE ACCURATE SHOTS. THE SLIDE HAS BEEN LIGHTENED SIGNIFICANTLY UTILIZING LIGHTENING CUTS TO ACCOMPLISH FASTER CYCLING.",
      "serialNumber": "6789897676898976",
      "caliber": "9 x 19 mm",
      "length": "226 mm // 8.9 inches",
      "height": "155 mm // 6.1 inches",
      "width": "42 mm // 1.65 inches",
      "barrelLength": "127 mm // 5.0 inches",
      "weight": "1202 g // 42.3 oz",
      "frameColors": "Nitrocarburized steel // Graphite black color // Blue // Red",
      "slide": "Nitrocarburized steel // Graphite black color",
      "slights": "Fiber optic front and fully adjustable black rear sight",
      "ipfsImageHash": "QmPbvs8G1jVaH6iHBUC2W1YnwY9AhzD98ydVqnhG9KMej1"
    },
    "timestamp": {
      "epoch": 143237168,
      "unix": 1633338368,
      "human": "2021-10-04T09:06:08.000Z"
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
  "message": "Asset not found"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
tr
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Examples

{% tabs %}
{% tab title="Curl" %}
```text
curl https://explorer.protokol.sh/api/nft/assets/f811518958861d4c1e72943f646b1bd848f606e6cc9bd6300480e6a0b501cf47
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTBaseApi("assets").get("VALID_ID");

>>> Promise<ApiResponse<AssetsResource>>
```
{% endtab %}
{% endtabs %}

## Wallet Owning Asset

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/assets/:id/wallets  " path=" " %}
{% api-method-summary %}
/assets/:id/wallets
{% endapi-method-summary %}

{% api-method-description %}
Returns assets owner wallet
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=false %}
The identifier of the asset
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
    "address": "AbfQq8iRSf9TFQRzQWo33dHYU7HFMS17Zd",
    "publicKey": "02def27da9336e7fbf63131b8d7e5c9f45b296235db035f1f4242c507398f0f21d",
    "nft": {
      "collections": [],
      "assetsIds": [
        "aa4a880e053644fee1475616a874e6689c2dfdbca0fb0a3db5a3f091c6e07d80"
      ]
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
  "message": "Asset not found or it was burned"
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
curl https://explorer.protokol.sh/api/nft/assets/baab82791f89a7f0af9e806dd2c634c9064903e514d1053179ff03f6d3d40866/wallets
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTBaseApi("assets").wallet("VALID_ID");

>>> Promise<ApiResponse<AssetsWallet>>
```
{% endtab %}
{% endtabs %}

## Wallet Assets

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/assets/wallet/:id" path=" " %}
{% api-method-summary %}
/assets/wallet/:id
{% endapi-method-summary %}

{% api-method-description %}
Returns all assets a wallet owns.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
Public key of a wallet
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

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
It returns modified or raw data
{% endapi-method-parameter %}

{% api-method-parameter name="inAuction" type="boolean" required=false %}
Returns only assets in active auctions \(not canceled or accepted trade auctions\)
{% endapi-method-parameter %}

{% api-method-parameter name="inExpiredAuction" type="boolean" required=false %}
Extends inAuction parameter, if true include assets included in expired auction, false by default
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
    "self": "/nft/assets/wallet/02def27da9336e7fbf63131b8d7e5c9f45b296235db035f1f4242c507398f0f21d?transform=true&inAuction=false&inExpiredAuction=false&page=1&limit=100",
    "first": "/nft/assets/wallet/02def27da9336e7fbf63131b8d7e5c9f45b296235db035f1f4242c507398f0f21d?transform=true&inAuction=false&inExpiredAuction=false&page=1&limit=100",
    "last": "/nft/assets/wallet/02def27da9336e7fbf63131b8d7e5c9f45b296235db035f1f4242c507398f0f21d?transform=true&inAuction=false&inExpiredAuction=false&page=1&limit=100"
  },
  "data": [
    {
      "id": "aa4a880e053644fee1475616a874e6689c2dfdbca0fb0a3db5a3f091c6e07d80",
      "ownerPublicKey": "02def27da9336e7fbf63131b8d7e5c9f45b296235db035f1f4242c507398f0f21d",
      "senderPublicKey": "02def27da9336e7fbf63131b8d7e5c9f45b296235db035f1f4242c507398f0f21d",
      "collectionId": "8643026a0997dc9fe74ce4aa11f522ecff651fa72ecf0127a0665fd52535bc1b",
      "attributes": {
        "name": "AREX ALPHA",
        "description": "THE AREX ALPHA IS THE NEXT EVOLUTIONARY STEP IN THE AREX HANDGUN FAMILY. IT IS A DIRECT DESCENDANT OF THE AREX ZERO 1 AND HAS INHERITED ITS TOUGHNESS AND RELIABILITY. LISTENING TO THE PRACTICAL SHOOTERS, AREX DESIGNED AND DEVELOPED A PISTOL THAT EXCELS IN COMPETITIVE PRACTICAL SHOOTING AS WELL AS IN TACTICAL SCENARIOS. WITH THE ELUSIVE AND ALL IMPORTANT SHOOTABILITY BEING AREXS PRIMARY GOAL, A STEEL FRAME WAS USED IN PLACE OF AN ALUMINUM ONE. A REENGINEERED GRIP RESULTS IN SHORTER TRIGGER REACH AND NOTABLY HIGHER HAND POSITION. AN UNDERCUT TRIGGER GUARD AND EXTENDED BEAVERTAIL COMPLETE THE ERGONOMIC TRANSFORMATION. THE LONG SLIDE HOUSES A FIVE INCH BARREL, PROVIDING A LONGER LINE OF SIGHT FOR FASTER AND MORE ACCURATE SHOTS. THE SLIDE HAS BEEN LIGHTENED SIGNIFICANTLY UTILIZING LIGHTENING CUTS TO ACCOMPLISH FASTER CYCLING.",
        "serialNumber": "6789897676898976",
        "caliber": "9 x 19 mm",
        "length": "226 mm // 8.9 inches",
        "height": "155 mm // 6.1 inches",
        "width": "42 mm // 1.65 inches",
        "barrelLength": "127 mm // 5.0 inches",
        "weight": "1202 g // 42.3 oz",
        "frameColors": "Nitrocarburized steel // Graphite black color // Blue // Red",
        "slide": "Nitrocarburized steel // Graphite black color",
        "slights": "Fiber optic front and fully adjustable black rear sight",
        "ipfsImageHash": "QmPbvs8G1jVaH6iHBUC2W1YnwY9AhzD98ydVqnhG9KMej1"
      },
      "timestamp": {
        "epoch": 143238280,
        "unix": 1633339480,
        "human": "2021-10-04T09:24:40.000Z"
      }
    }
  ]
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
  "message": "Wallet not found"
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
  "message": "\"id\" length must be 66 characters long"
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
curl https://explorer.protokol.sh/api/nft/assets/wallet/03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTBaseApi("assets").walletAssets("PUBLIC_KEY");

>>> Promise<ApiResponseWithPagination<AssetsResource[]>>
```
{% endtab %}
{% endtabs %}

## Search By Asset

{% api-method method="post" host="https://explorer.protokol.sh/api/nft/assets/search" path=" " %}
{% api-method-summary %}
/assets/search
{% endapi-method-summary %}

{% api-method-description %}
Search assets by their JSON attributes.
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
It returns modified or raw data.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="attributeName" type="object" required=true %}
Attribute to search by.
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
    "self": "/nft/assets/search?transform=true&page=1&limit=100",
    "first": "/nft/assets/search?transform=true&page=1&limit=100",
    "last": "/nft/assets/search?transform=true&page=1&limit=100"
  },
  "data": [
    {
      "id": "f811518958861d4c1e72943f646b1bd848f606e6cc9bd6300480e6a0b501cf47",
      "ownerPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "collectionId": "8643026a0997dc9fe74ce4aa11f522ecff651fa72ecf0127a0665fd52535bc1b",
      "attributes": {
        "name": "AREX ALPHA",
        "description": "THE AREX ALPHA IS THE NEXT EVOLUTIONARY STEP IN THE AREX HANDGUN FAMILY. IT IS A DIRECT DESCENDANT OF THE AREX ZERO 1 AND HAS INHERITED ITS TOUGHNESS AND RELIABILITY. LISTENING TO THE PRACTICAL SHOOTERS, AREX DESIGNED AND DEVELOPED A PISTOL THAT EXCELS IN COMPETITIVE PRACTICAL SHOOTING AS WELL AS IN TACTICAL SCENARIOS. WITH THE ELUSIVE AND ALL IMPORTANT SHOOTABILITY BEING AREXS PRIMARY GOAL, A STEEL FRAME WAS USED IN PLACE OF AN ALUMINUM ONE. A REENGINEERED GRIP RESULTS IN SHORTER TRIGGER REACH AND NOTABLY HIGHER HAND POSITION. AN UNDERCUT TRIGGER GUARD AND EXTENDED BEAVERTAIL COMPLETE THE ERGONOMIC TRANSFORMATION. THE LONG SLIDE HOUSES A FIVE INCH BARREL, PROVIDING A LONGER LINE OF SIGHT FOR FASTER AND MORE ACCURATE SHOTS. THE SLIDE HAS BEEN LIGHTENED SIGNIFICANTLY UTILIZING LIGHTENING CUTS TO ACCOMPLISH FASTER CYCLING.",
        "serialNumber": "6789897676898976",
        "caliber": "9 x 19 mm",
        "length": "226 mm // 8.9 inches",
        "height": "155 mm // 6.1 inches",
        "width": "42 mm // 1.65 inches",
        "barrelLength": "127 mm // 5.0 inches",
        "weight": "1202 g // 42.3 oz",
        "frameColors": "Nitrocarburized steel // Graphite black color // Blue // Red",
        "slide": "Nitrocarburized steel // Graphite black color",
        "slights": "Fiber optic front and fully adjustable black rear sight",
        "ipfsImageHash": "QmPbvs8G1jVaH6iHBUC2W1YnwY9AhzD98ydVqnhG9KMej1"
      },
      "timestamp": {
        "epoch": 143237168,
        "unix": 1633338368,
        "human": "2021-10-04T09:06:08.000Z"
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
  --url https://explorer.protokol.sh/api/nft/assets/search \
  --header 'content-type: application/json' \
  --data '{
      "name": "AREX ALPHA"
}'
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTBaseApi("assets").searchByAsset({
    "VALID_JSON_OBJECT"
});

>>> Promise<ApiResponseWithPagination<AssetsResource[]>>
```
{% endtab %}
{% endtabs %}

