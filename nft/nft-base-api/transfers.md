---
description: Api endpoints for Transfers.
---

# Transfers

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
curl http://nft.protokol.com:4003/api/nft/transfers
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
      "id": "ca89d9614d79e0df97cee7dbb3d517f6872bb719e2c0a4727ea980ed18274411",
      "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
      "nftTransfer": {
        "nftIds": [
          "a6273964d15a1de37792497bf15e12e67898c7217a680cbf2e152cccc33e5182"
        ],
        "recipientId": "AW8n3yvSAqUJkyfcG5u3bgRxsNKzXYPamN"
      }
    }
  ]
}
```

## GET - Return transfer by id

### Endpoint

```bash
GET /transfers/{id}
```

### Path parameters

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The identifier of the transfer to be retrieved. | Yes |

### Example

```bash
curl http://nft.protokol.com:4003/api/nft/transfers/ca89d9614d79e0df97cee7dbb3d517f6872bb719e2c0a4727ea980ed18274411
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
    }
  }
}
```
