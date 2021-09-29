---
description: Voting Create Proposal API Endpoints.
---

# Create Proposal

### /create/proposal/transactions

{% api-method method="get" host="http://localhost:4003/api/create/proposal/transactions" path=" " %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}
Returns all Create Proposal Transactions
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
    "self": "/voting/create/proposal/transactions?transform=true&page=1&limit=100",
    "first": "/voting/create/proposal/transactions?transform=true&page=1&limit=100",
    "last": "/voting/create/proposal/transactions?transform=true&page=1&limit=100"
  },
  "data": [
    {
      "id": "8ba1411eb769c3ba7d04b7e353d5c78240705597ee254100164ee77b9999234b",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "duration": {
        "blockHeight": 123456
      },
      "content": "qwertz",
      "timestamp": {
        "epoch": 136819696,
        "unix": 1626920896,
        "human": "2021-07-22T02:28:16.000Z"
      }
    },
    {
      "id": "c8f3fff0df73f1125d15a467b4f9401a7967e2915c93612737b7761cde7ada29",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "duration": {
        "blockHeight": 123456
      },
      "content": "qwertz",
      "timestamp": {
        "epoch": 136819704,
        "unix": 1626920904,
        "human": "2021-07-22T02:28:24.000Z"
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
curl http://localhost:4003/api/create/proposal/transactions
```

### 

### /create/proposal/transactions/:id

{% api-method method="get" host="http://localhost:4003/api/create/proposal/transactions/:id" path=" " %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}
Returns Create Proposal Transaction by id.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=false %}
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
    "id": "fe8419bda6525ef0074e733dbd3e8b671267c6c8d51b025fd7ae0812947cec30",
    "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "duration": {
      "blockHeight": 123456
    },
    "content": "QmPfdpTRbhGVZZWKZDzNT5T4NB6C7fFo5wM9Xe8qmLCXWt",
    "timestamp": {
      "epoch": 142719560,
      "unix": 1632820760,
      "human": "2021-09-28T09:19:20.000Z"
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
curl http://localhost:4003/api/create/proposal/transactions/fe8419bda6525ef0074e733dbd3e8b671267c6c8d51b025fd7ae0812947cec30
```



### /create/proposal/:id/wallet

{% api-method method="get" host="http://localhost:4003/api/create/proposal/:id/wallet " path=" " %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}
Returns wallet by create proposal transaction id
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=false %}
Create Proposal transaction id
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
    "nonce": "36",
    "balance": "244863000000000",
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
        "agree": [],
        "disagree": []
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

