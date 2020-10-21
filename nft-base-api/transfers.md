---
description: API Endpoints For NFT Transfers
---

# Transfers

## List of Transfer Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [/transfers](https://docs.protokol.com/nft/nft-base-api/transfers#get-return-all-transfers) | return all transfers | GET |
| [/transfers/:id](https://docs.protokol.com/nft/nft-base-api/transfers#get-return-transfer-by-id) | return transfer by :id | GET |

## GET - Return all Transfers

### Endpoint

```text
GET /transfers
```

### **Query parameters**

| **Name** | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| page | int | The number of the page that will be returned. | No |
| limit | int  | The number of resources per page. | No |
| orderBy | string | Type by which should order resources. | No |
| transform | boolean | If returns modified or raw data. | No |

### Example

```text
curl https://api.protokol.com/api/nft/transfers
```

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
    "self": "/nft/transfers?page=1&limit=100&transform=true",
    "first": "/nft/transfers?page=1&limit=100&transform=true",
    "last": "/nft/transfers?page=1&limit=100&transform=true"
  },
  "data": [
    {
      "id": "68ef043ddfd009e378a62b813595ceb41c71a4c8d4a1d7fecf4cb15229acdede",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "nftTransfer": {
        "nftIds": [
          "f2429b0e9ceee60e95e1cd45f5f821016f3806063ea848ea94f0d2bfde06245b"
        ],
        "recipientId": "AW8n3yvSAqUJkyfcG5u3bgRxsNKzXYPamN"
      },
      "timestamp": {
        "epoch": 105741400,
        "unix": 1595842600,
        "human": "2020-07-27T09:36:40.000Z"
      }
    }
  ]
}
```

## GET - Return Transfer by id

### Endpoint

```bash
GET /transfers/{id}
```

### Path parameters

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The identifier of the transfer to be retrieved. | Yes |
| transform | boolean | If returns modified or raw data. | No |

### Example

```bash
curl https://api.protokol.com/api/nft/transfers/ca89d9614d79e0df97cee7dbb3d517f6872bb719e2c0a4727ea980ed18274411
```

### Response

```bash
{
  "data": {
    "id": "ca89d9614d79e0df97cee7dbb3d517f6872bb719e2c0a4727ea980ed18274411",
    "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
    "nftTransfer": {
      "nftIds": [
        "a6273964d15a1de37792497bf15e12e67898c7217a680cbf2e152cccc33e5182"
      ],
      "recipientId": "AW8n3yvSAqUJkyfcG5u3bgRxsNKzXYPamN"
    },
    "timestamp": {
      "epoch": 105746776,
      "unix": 1595847976,
      "human": "2020-07-27T11:06:16.000Z"
    }
  }
}
```

