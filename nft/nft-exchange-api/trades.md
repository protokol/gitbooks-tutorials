---
description: API Endpoints For Trades
---

# Trades

## GET - Return All Trades

### Endpoint

```text
GET /trades
```

### **Query Parameters** <a id="query-parameters"></a>

| **Name** | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| page | int | The number of the page that will be returned. | No |
| limit | int | The number of resources per page. | No |
| orderBy | string | Type by which should order resources. | No |
| transform | boolean | If returns modified or raw data. | No |

### Example

```text
curl http://nft.protokol.com:4003/api/nft/exchange/trades
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
    "self": "/nft/exchange/trades?page=1&limit=100&transform=true",
    "first": "/nft/exchange/trades?page=1&limit=100&transform=true",
    "last": "/nft/exchange/trades?page=1&limit=100&transform=true"
  },
  "data": [
    {
      "id": "993faf758740972af07b67892e1ff2a66f1467c9203020bdb65f8a0a533942e7",
      "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
      "completedTrade": {
        "auctionId": "4166ebfa58824bf774dbd1f70c04a22adf3f77f30ce2f32ae69f98b302b5752f",
        "bidId": "249010d96a54a8fbd14b1d2b5d3d12abc56edf0843f11a9c84d0fd8a2385625a"
      }
    }
  ]
}
```

## GET - Return Trade By Id

### Endpoint

```bash
GET /trades/{id}
```

### Path Parameters <a id="path-parameters"></a>

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The identifier of the trade to be retrieved. | Yes |

### Example

```text
curl http://nft.protokol.com:4003/api/nft/exchange/trades/993faf758740972af07b67892e1ff2a66f1467c9203020bdb65f8a0a533942e7
```

### Response

```javascript
{
  "data": {
    "id": "993faf758740972af07b67892e1ff2a66f1467c9203020bdb65f8a0a533942e7",
    "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
    "completedTrade": {
      "auction": {
        "id": "4166ebfa58824bf774dbd1f70c04a22adf3f77f30ce2f32ae69f98b302b5752f",
        "nftId": "a6273964d15a1de37792497bf15e12e67898c7217a680cbf2e152cccc33e5182",
        "startAmount": "999",
        "expiration": {
          "blockHeight": 1000000
        }
      },
      "bid": {
        "id": "249010d96a54a8fbd14b1d2b5d3d12abc56edf0843f11a9c84d0fd8a2385625a",
        "auctionId": "4166ebfa58824bf774dbd1f70c04a22adf3f77f30ce2f32ae69f98b302b5752f",
        "bidAmount": "12223"
      }
    }
  }
}
```

## POST - Search Trades

### Endpoint

```bash
POST /trades/search
```

### **Query Parameters** <a id="query-parameters"></a>

| **Name** | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| page | int | The number of the page that will be returned. | No |
| limit | int | The number of resources per page. | No |
| orderBy | string | Type by which should order resources. | No |

### Body Parameters <a id="body-parameters"></a>

| **Name** | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| senderPublicKey | string | Public key of a sender. | No |
| auctionId | string | Id of a auction. | No |
| bidId | string | Id of a bid. | No |

### Example

```bash
curl --request POST \
  --url http://nft.protokol.com:4003/api/nft/exchange/trades/search \
  --header 'content-type: application/json' \
  --data '{
	  	"senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0"
}'
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
    "self": "/nft/exchange/trades/search?page=1&limit=100",
    "first": "/nft/exchange/trades/search?page=1&limit=100",
    "last": "/nft/exchange/trades/search?page=1&limit=100"
  },
  "data": [
    {
      "id": "993faf758740972af07b67892e1ff2a66f1467c9203020bdb65f8a0a533942e7",
      "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
      "completedTrade": {
        "auctionId": "4166ebfa58824bf774dbd1f70c04a22adf3f77f30ce2f32ae69f98b302b5752f",
        "bidId": "249010d96a54a8fbd14b1d2b5d3d12abc56edf0843f11a9c84d0fd8a2385625a"
      }
    }
  ]
}
```

