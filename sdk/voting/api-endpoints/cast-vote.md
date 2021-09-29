---
description: Voting Cast Vote API Endpoints.
---

# Cast Vote

### /cast/vote/transactions

{% api-method method="get" host="http://localhost:4003/api/cast/vote/transactions" path=" " %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}
Returns all Cast Vote Transactions
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
Orders by specific parameter \(asc or desc\)  
Example: orderBy=id:asc
{% endapi-method-parameter %}

{% api-method-parameter name="transform" type="boolean" required=false %}
Transforms to raw response
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
    "count": 4,
    "pageCount": 1,
    "totalCount": 4,
    "next": null,
    "previous": null,
    "self": "/voting/cast/vote/transactions?transform=true&page=1&limit=100",
    "first": "/voting/cast/vote/transactions?transform=true&page=1&limit=100",
    "last": "/voting/cast/vote/transactions?transform=true&page=1&limit=100"
  },
  "data": [
    {
      "id": "4ce88923c7d961fc29dd6a5111979cb2767df947bf9f3b0f791a841a21d675de",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "proposalId": "c8f3fff0df73f1125d15a467b4f9401a7967e2915c93612737b7761cde7ada29",
      "decision": "yes",
      "timestamp": {
        "epoch": 136819968,
        "unix": 1626921168,
        "human": "2021-07-22T02:32:48.000Z"
      }
    },
    {
      "id": "4498ecbc765e38f289761f1d04a9dfb2e062d87239d8e5af55c77e4c6e842b53",
      "senderPublicKey": "02def27da9336e7fbf63131b8d7e5c9f45b296235db035f1f4242c507398f0f21d",
      "proposalId": "fe8419bda6525ef0074e733dbd3e8b671267c6c8d51b025fd7ae0812947cec30",
      "decision": "no",
      "timestamp": {
        "epoch": 142719936,
        "unix": 1632821136,
        "human": "2021-09-28T09:25:36.000Z"
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

#### Curl Example

```bash
curl http://localhost:4003/api/cast/vote/transactions
```

### 

### /cast/vote/transactions/:id

{% api-method method="get" host="http://localhost:4003/api/cast/vote/transactions/:id" path=" " %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}
Returns Cast Vote Transaction by id.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
Transaction Id 
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="transform" type="boolean" required=false %}
Transforms to raw response
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
    "id": "4ce88923c7d961fc29dd6a5111979cb2767df947bf9f3b0f791a841a21d675de",
    "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "proposalId": "c8f3fff0df73f1125d15a467b4f9401a7967e2915c93612737b7761cde7ada29",
    "decision": "yes",
    "timestamp": {
      "epoch": 136819968,
      "unix": 1626921168,
      "human": "2021-07-22T02:32:48.000Z"
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
  "message": "Transaction not found!"
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

#### Curl Example

```bash
curl http://localhost:4003/api/cast/vote/transactions/4ce88923c7d961fc29dd6a5111979cb2767df947bf9f3b0f791a841a21d675de
```



### /cast/vote/:id/wallet

{% api-method method="get" host="http://localhost:4003/api/cast/vote/:id/wallet " path=" " %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}
Returns wallet by Cast Vote transaction id
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
Cast Vote transaction id
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
    "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "nonce": "37",
    "balance": "244813000000000",
    "proposals": {
      "8ba1411eb769c3ba7d04b7e353d5c78240705597ee254100164ee77b9999234b": {
        "proposal": {
          "duration": {
            "blockHeight": 123456
          },
          "content": "qwertz"
        },
        "agree": [],
        "disagree": []
      },
      "c8f3fff0df73f1125d15a467b4f9401a7967e2915c93612737b7761cde7ada29": {
        "proposal": {
          "duration": {
            "blockHeight": 123456
          },
          "content": "qwertz"
        },
        "agree": [
          "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37"
        ],
        "disagree": []
      },
      "9268a2dba346f7a9673877755061b5ba0bd14f72beeced37b877022aca2aed92": {
        "proposal": {
          "duration": {
            "blockHeight": 123456
          },
          "content": "QmPfdpTRbhGVZZWKZDzNT5T4NB6C7fFo5wM9Xe8qmLCXWt"
        },
        "agree": [],
        "disagree": []
      },
      "fe8419bda6525ef0074e733dbd3e8b671267c6c8d51b025fd7ae0812947cec30": {
        "proposal": {
          "duration": {
            "blockHeight": 123456
          },
          "content": "QmPfdpTRbhGVZZWKZDzNT5T4NB6C7fFo5wM9Xe8qmLCXWt"
        },
        "agree": [
          "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
          "038082dad560a22ea003022015e3136b21ef1ffd9f2fd50049026cbe8e2258ca17"
        ],
        "disagree": [
          "02def27da9336e7fbf63131b8d7e5c9f45b296235db035f1f4242c507398f0f21d"
        ]
      }
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
  "message": "Wallet not found!"
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

#### Curl Example

```bash
curl http://localhost:4003/api/cast/vote/4ce88923c7d961fc29dd6a5111979cb2767df947bf9f3b0f791a841a21d675de/wallet
```

