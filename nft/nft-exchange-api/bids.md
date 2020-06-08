---
description: Api endpoints for Bids.
---

# Bids

## GET - Return All Bids

### Endpoint

```text
GET /bids
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
curl http://nft.protokol.com:4003/api/nft/exchange/bids
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
    "self": "/nft/exchange/bids?page=1&limit=100&transform=true",
    "first": "/nft/exchange/bids?page=1&limit=100&transform=true",
    "last": "/nft/exchange/bids?page=1&limit=100&transform=true"
  },
  "data": [
    {
      "id": "b7cb70737ea5ae78fd348fb58c02e799dfd296e2ae7d54ac83f95f3e8bf8594b",
      "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
      "nftBid": {
        "auctionId": "4166ebfa58824bf774dbd1f70c04a22adf3f77f30ce2f32ae69f98b302b5752f",
        "bidAmount": "12223"
      }
    }
  ]
}
```

## GET - Return Bid By Id

### Endpoint

```bash
GET /bids/{id}
```

### Path Parameters <a id="path-parameters"></a>

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The identifier of the bid to be retrieved. | Yes |

### Example

```text
curl http://nft.protokol.com:4003/api/nft/exchange/bids/b7cb70737ea5ae78fd348fb58c02e799dfd296e2ae7d54ac83f95f3e8bf8594b
```

### Response

```javascript
{
  "data": {
    "id": "b7cb70737ea5ae78fd348fb58c02e799dfd296e2ae7d54ac83f95f3e8bf8594b",
    "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
    "nftBid": {
      "auctionId": "4166ebfa58824bf774dbd1f70c04a22adf3f77f30ce2f32ae69f98b302b5752f",
      "bidAmount": "12223"
    }
  }
}
```

## GET - Return Bids Wallet

### Endpoint

```bash
GET /bids/{id}/wallets
```

### Path Parameters <a id="path-parameters-1"></a>

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The identifier of the bid. | Yes |

### Example

```text
curl http://nft.protokol.com:4003/api/nft/exchange/bids/b7cb70737ea5ae78fd348fb58c02e799dfd296e2ae7d54ac83f95f3e8bf8594b/wallets
```

### Response

```javascript
{
  "data": {
    "address": "AV6GP5qhhsZG6MHb4gShy22doUnVjEKHcN",
    "publicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
    "nft": {
      "base": {
        "collections": {
          "18f7ba659b5c87737f5db131e15ad682e2e37fdf8259ec227b5bc9e5e9d9c28b": {
            "currentSupply": 1,
            "nftCollectionAsset": {
              "name": "FIFA-20-PLAYERS",
              "description": "FIFA 2020 Players",
              "maximumSupply": 100200,
              "jsonSchema": {
                "properties": {
                  "name": {
                    "type": "string"
                  },
                  "pac": {
                    "type": "number"
                  },
                  "sho": {
                    "type": "number"
                  },
                  "pas": {
                    "type": "number"
                  },
                  "dri": {
                    "type": "number"
                  },
                  "def": {
                    "type": "number"
                  },
                  "phy": {
                    "type": "number"
                  }
                }
              }
            }
          }
        },
        "tokenIds": {
          "a6273964d15a1de37792497bf15e12e67898c7217a680cbf2e152cccc33e5182": {}
        }
      },
      "exchange": {
        "auctions": {
          "4166ebfa58824bf774dbd1f70c04a22adf3f77f30ce2f32ae69f98b302b5752f": {
            "nftId": "a6273964d15a1de37792497bf15e12e67898c7217a680cbf2e152cccc33e5182",
            "bids": [
              "b7cb70737ea5ae78fd348fb58c02e799dfd296e2ae7d54ac83f95f3e8bf8594b"
            ]
          }
        }
      }
    }
  }
}
```

## POST - Search Bids

### Endpoint

```bash
POST /bids/search
```

### **Query Parameters** <a id="query-parameters-1"></a>

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
| bidAmount | string | Amount of a bid. | No |

### Example

```bash
curl --request POST \
  --url http://nft.protokol.com:4003/api/nft/exchange/bids/search \
  --header 'content-type: application/json' \
  --data '{
	  "bidAmount": "12223"
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
    "self": "/nft/exchange/bids/search?page=1&limit=100",
    "first": "/nft/exchange/bids/search?page=1&limit=100",
    "last": "/nft/exchange/bids/search?page=1&limit=100"
  },
  "data": [
    {
      "id": "b7cb70737ea5ae78fd348fb58c02e799dfd296e2ae7d54ac83f95f3e8bf8594b",
      "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
      "nftBid": {
        "auctionId": "4166ebfa58824bf774dbd1f70c04a22adf3f77f30ce2f32ae69f98b302b5752f",
        "bidAmount": "12223"
      }
    }
  ]
}
```

## GET - Return All Canceled Bids

### Endpoint

```bash
GET /bids/canceled
```

### **Query Parameters** <a id="query-parameters"></a>

| **Name** | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| page | int | The number of the page that will be returned. | No |
| limit | int | The number of resources per page. | No |
| orderBy | string | Type by which should order resources. | No |

### Example

```bash
curl http://nft.protokol.com:4003/api/nft/exchange/bids/canceled
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
    "self": "/nft/exchange/bids/canceled?page=1&limit=100",
    "first": "/nft/exchange/bids/canceled?page=1&limit=100",
    "last": "/nft/exchange/bids/canceled?page=1&limit=100"
  },
  "data": [
    {
      "id": "88bda3c46f75d0ca2372825b2cded17987355ea8dc64f2c11e3855b869bb7935",
      "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
      "nftBidCancel": {
        "bidId": "b7cb70737ea5ae78fd348fb58c02e799dfd296e2ae7d54ac83f95f3e8bf8594b"
      }
    }
  ]
}
```

## GET - Return Canceled Bid By Id

### Endpoint

```bash
GET /bids/canceled/{id}
```

### Path Parameters <a id="path-parameters"></a>

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The identifier of the bid to be retrieved. | Yes |

### Example

```bash
curl http://nft.protokol.com:4003/api/nft/exchange/bids/canceled/88bda3c46f75d0ca2372825b2cded17987355ea8dc64f2c11e3855b869bb7935
```

### Response

```javascript
{
  "data": {
    "id": "88bda3c46f75d0ca2372825b2cded17987355ea8dc64f2c11e3855b869bb7935",
    "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
    "nftBidCancel": {
      "bidId": "b7cb70737ea5ae78fd348fb58c02e799dfd296e2ae7d54ac83f95f3e8bf8594b"
    }
  }
}
```

