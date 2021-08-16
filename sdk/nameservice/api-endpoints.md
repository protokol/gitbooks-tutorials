---
description: List of nameservice api endpoints.
---

# Api Endpoints

{% hint style="info" %}
Defualt nameservice prefix is `/api/nameservice`
{% endhint %}

## List of configurations endpoints

| Endpoints | Description | Type |
| :--- | :--- | :--- |
| /configurations | Returns configurations for nameserivce plugins | GET |

## List of nameservice endpoints

| Endpoints | Description | Type |
| :--- | :--- | :--- |
| / | Returns all nameservice transactions | GET |
| /:id | Returns specific nameservice transaction by id | GET |
| /:id/wallet | Returns wallet by its nameservice name | GET |



## GET - configurations

### Endpoint

```text
/configurations
```

### Example

```text
curl https://explorer.protokol.sh/api/nameservice/configurations
```

### Response

```javascript
{
  "data": {
    "api": {
      "packageName": "@protokol/nameservice-api",
      "currentVersion": "1.0.0-beta.2",
      "latestVersion": "1.0.0-beta.0",
      "defaults": {}
    },
    "transactions": {
      "packageName": "@protokol/nameservice-transactions",
      "currentVersion": "1.0.0-beta.2",
      "latestVersion": "1.0.0-beta.0",
      "defaults": {
        "defaults": {
          "feeType": 0
        }
      }
    },
    "crypto": {
      "packageName": "@protokol/nameservice-crypto",
      "currentVersion": "1.0.0-beta.2",
      "latestVersion": "1.0.0-beta.0",
      "defaults": {
        "defaults": {
          "nameserviceTypeGroup": 9004,
          "version": 2,
          "nameserviceStaticFee": 5000000000
        }
      }
    }
  }
}
```

## GET - /

### Endpoint

```text
/
```

### Example

```text
curl https://explorer.protokol.sh/api/nameservice
```

### **Query Parameters**

| **Name** | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| page | int | The number of the page that will be returned. | No |
| limit | int | The number of resources per page. | No |
| orderBy | string | Type by which should order resources. | No |
| transform | boolean | If returns modified or raw data. | No |

### Response

```javascript
{
  "meta": {
    "totalCountIsEstimate": true,
    "count": 1,
    "pageCount": 1,
    "totalCount": 1,
    "next": null,
    "previous": null,
    "self": "/nameservice?transform=true&page=1&limit=100",
    "first": "/nameservice?transform=true&page=1&limit=100",
    "last": "/nameservice?transform=true&page=1&limit=100"
  },
  "data": [
    {
      "id": "b20e1aebb3652c247c1d1bdc88074a819d175af20f00232d4a85bb9b5a07b637",
      "sender": "ANBkoGqWeTSiaEVgVzSKZd3jS7UWzv9PSo",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "nameservice": "zan",
      "timestamp": {
        "epoch": 138928576,
        "unix": 1629029776,
        "human": "2021-08-15T12:16:16.000Z"
      }
    }
  ]
}
```

## GET - /:Id

### **Endpoint**

```text
/:id
```

### Example

```text
curl https://explorer.protokol.sh/api/nameservice/aedafa0fa07e79ada72c8d676efaa9429ff04f47271bce742c6079b56872285c
```

### Response

```javascript
{
  "data": {
    "id": "b20e1aebb3652c247c1d1bdc88074a819d175af20f00232d4a85bb9b5a07b637",
    "sender": "ANBkoGqWeTSiaEVgVzSKZd3jS7UWzv9PSo",
    "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "nameservice": "zan",
    "timestamp": {
      "epoch": 138928576,
      "unix": 1629029776,
      "human": "2021-08-15T12:16:16.000Z"
    }
  }
}
```

## GET - /:id/wallet

### Endpoint

```text
/:id/wallet
```

### Example

```text
curl https://explorer.protokol.sh/api/nameservice/zan/wallet
```

### Response

```javascript
{
  "data": {
    "address": "ANBkoGqWeTSiaEVgVzSKZd3jS7UWzv9PSo",
    "publicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "balance": "244995000000000",
    "nonce": "6",
    "name": "zan"
  }
}
```

