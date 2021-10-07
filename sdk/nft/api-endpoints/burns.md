---
description: List of NFT Base Burns API Endpoints.
---

# Burns

## All Burns

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/burns" path=" " %}
{% api-method-summary %}
/burns
{% endapi-method-summary %}

{% api-method-description %}
Return all burn transactions
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="page" type="integer" required=false %}
The number of page to be returned
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
    "self": "/nft/burns?transform=true&page=1&limit=100",
    "first": "/nft/burns?transform=true&page=1&limit=100",
    "last": "/nft/burns?transform=true&page=1&limit=100"
  },
  "data": [
    {
      "id": "a6664c2d2e26e4c7a7548850f0f820d755c0cad1287a21be2582ab039f6d5c2f",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "nftBurn": {
        "nftId": "f811518958861d4c1e72943f646b1bd848f606e6cc9bd6300480e6a0b501cf47"
      },
      "timestamp": {
        "epoch": 143493208,
        "unix": 1633594408,
        "human": "2021-10-07T08:13:28.000Z"
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
curl https://explorer.protokol.sh/api/nft/burns
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTBaseApi("burns").all();

>>> Promise<ApiResponseWithPagination<BurnsResource[]>>
```
{% endtab %}
{% endtabs %}

## Burn By Id

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/burns/:id" path=" " %}
{% api-method-summary %}
/burns/:id
{% endapi-method-summary %}

{% api-method-description %}
Returns burn transaction by id
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=false %}
The identifier to be retrieved
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
    "id": "a6664c2d2e26e4c7a7548850f0f820d755c0cad1287a21be2582ab039f6d5c2f",
    "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "nftBurn": {
      "nftId": "f811518958861d4c1e72943f646b1bd848f606e6cc9bd6300480e6a0b501cf47"
    },
    "timestamp": {
      "epoch": 143493208,
      "unix": 1633594408,
      "human": "2021-10-07T08:13:28.000Z"
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
  "message": "Burn Transaction not found"
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
curl https://explorer.protokol.sh/api/nft/burns/f2c47694e32cdb7cae7e3ca8726836fac323a3175559277469faf541ae49c5b4
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTBaseApi("burns").get("VALID_ID");

>>> Promise<ApiResponse<BurnsResource>>
```
{% endtab %}
{% endtabs %}

