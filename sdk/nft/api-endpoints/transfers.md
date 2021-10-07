---
description: List of NFT Base Transfer Endpoints.
---

# Transfers

## All Transfers

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/transfers" path=" " %}
{% api-method-summary %}
/transfers
{% endapi-method-summary %}

{% api-method-description %}

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
    "self": "/nft/transfers?transform=true&page=1&limit=100",
    "first": "/nft/transfers?transform=true&page=1&limit=100",
    "last": "/nft/transfers?transform=true&page=1&limit=100"
  },
  "data": [
    {
      "id": "606aceccbb930f4a1e694ba876d0574a4dbf39cb8437d7c5f2dc1b7c9fa3ba23",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "nftTransfer": {
        "nftIds": [
          "b612cdce4e127bbf2393261100bfb4b1866684de2df1dd0d0bbcdb2eaa7b55b8"
        ],
        "recipientId": "AMfyf9iRjXiKNcLQVTUE9oCESUPzmQ6iUT"
      },
      "timestamp": {
        "epoch": 143495632,
        "unix": 1633596832,
        "human": "2021-10-07T08:53:52.000Z"
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
curl https://explorer.protokol.sh/api/nft/transfers
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTBaseApi("transfers").all();

>>> Promise<ApiResponseWithPagination<TransfersResource[]>>
```
{% endtab %}
{% endtabs %}

## Transfer By Id

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/transfers/:id" path=" " %}
{% api-method-summary %}
/transfers/:id
{% endapi-method-summary %}

{% api-method-description %}
Returns Transfer transaction by id
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The identifer to be retrieved
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
    "id": "606aceccbb930f4a1e694ba876d0574a4dbf39cb8437d7c5f2dc1b7c9fa3ba23",
    "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "nftTransfer": {
      "nftIds": [
        "b612cdce4e127bbf2393261100bfb4b1866684de2df1dd0d0bbcdb2eaa7b55b8"
      ],
      "recipientId": "AMfyf9iRjXiKNcLQVTUE9oCESUPzmQ6iUT"
    },
    "timestamp": {
      "epoch": 143495632,
      "unix": 1633596832,
      "human": "2021-10-07T08:53:52.000Z"
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
  "message": "NTF Transfer Transaction not found"
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
curl https://explorer.protokol.sh/api/nft/transfers/5a5fe2fb9c5b1102b2d6266d41b6184676bd42c2b648c82e13264a562252072b
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTBaseApi("transfers").get("VALID_ID");

>>> Promise<ApiResponse<TransfersResource>>
```
{% endtab %}
{% endtabs %}

