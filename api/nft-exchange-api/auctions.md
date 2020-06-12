---
description: API Endpoints For Auctions
---

# Auctions

## GET - Return All Auctions

### Endpoint <a id="endpoint"></a>

```text
GET /auctions
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
curl http://nft.protokol.com:4003/api/nft/exchange/auctions
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
    "self": "/nft/exchange/auctions?page=1&limit=100&transform=true",
    "first": "/nft/exchange/auctions?page=1&limit=100&transform=true",
    "last": "/nft/exchange/auctions?page=1&limit=100&transform=true"
  },
  "data": [
    {
      "id": "ab1303eb497ab290318c860bda259d5fafaf45fe0624712d088bcf99ee411e3e",
      "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
      "nftAuction": {
        "nftId": "a6273964d15a1de37792497bf15e12e67898c7217a680cbf2e152cccc33e5182",
        "startAmount": "999",
        "expiration": {
          "blockHeight": 1000000
        }
      }
    }
  ]
}
```

## GET - Return An Auction By Id

### Endpoint

```bash
GET /auctions/{id}
```

### Path Parameters <a id="path-parameters"></a>

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The identifier of the auction to be retrieved. | Yes |

### Example

```bash
curl http://nft.protokol.com:4003/api/nft/exchange/auctions/ab1303eb497ab290318c860bda259d5fafaf45fe0624712d088bcf99ee411e3e
```

### Response

```javascript
{
  "data": {
    "id": "ab1303eb497ab290318c860bda259d5fafaf45fe0624712d088bcf99ee411e3e",
    "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
    "nftAuction": {
      "nftId": "a6273964d15a1de37792497bf15e12e67898c7217a680cbf2e152cccc33e5182",
      "startAmount": "999",
      "expiration": {
        "blockHeight": 1000000
      }
    }
  }
}
```

## GET - Return Auctions Wallet

### Endpoint

```bash
GET /auctions/{id}/wallets
```

### Path Parameters <a id="path-parameters-1"></a>

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The identifier of the auction. | Yes |

### Example

```bash
curl http://nft.protokol.com:4003/api/nft/exchange/auctions/ab1303eb497ab290318c860bda259d5fafaf45fe0624712d088bcf99ee411e3e/wallets
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
          "ab1303eb497ab290318c860bda259d5fafaf45fe0624712d088bcf99ee411e3e": {
            "nftId": "a6273964d15a1de37792497bf15e12e67898c7217a680cbf2e152cccc33e5182",
            "bids": []
          }
        }
      }
    }
  }
}
```

## POST - Search Auctions

### Endpoint

```bash
POST /auctions/search
```

### **Query parameters** <a id="query-parameters-1"></a>

| **Name** | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| page | int | The number of the page that will be returned. | No |
| limit | int | The number of resources per page. | No |
| orderBy | string | Type by which should order resources. | No |

### Body Parameters <a id="body-parameters"></a>

| **Name** | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| senderPublicKey | string | Public key of a sender. | No |
| nftId | string | Id of nft. | No |
| startAmount | string | Start amount of auctions. | No |
| expiration: {blockHeight} | number | BlockHeight expiration | No |

### Example

```bash
curl --request POST \
  --url http://nft.protokol.com:4003/api/nft/exchange/auctions/search \
  --header 'content-type: application/json' \
  --data '{
	  "nftId": "a6273964d15a1de37792497bf15e12e67898c7217a680cbf2e152cccc33e5182"
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
    "self": "/nft/exchange/auctions/search?page=1&limit=100",
    "first": "/nft/exchange/auctions/search?page=1&limit=100",
    "last": "/nft/exchange/auctions/search?page=1&limit=100"
  },
  "data": [
    {
      "id": "ab1303eb497ab290318c860bda259d5fafaf45fe0624712d088bcf99ee411e3e",
      "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
      "nftAuction": {
        "nftId": "a6273964d15a1de37792497bf15e12e67898c7217a680cbf2e152cccc33e5182",
        "startAmount": "999",
        "expiration": {
          "blockHeight": 1000000
        }
      }
    }
  ]
}
```

## GET - Return All Canceled Auctions

### Endpoint

```bash
GET /auctions/canceled
```

### **Query parameters** <a id="query-parameters-1"></a>

| **Name** | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| page | int | The number of the page that will be returned. | No |
| limit | int | The number of resources per page. | No |
| orderBy | string | Type by which should order resources. | No |

### Example

```bash
curl http://nft.protokol.com:4003/api/nft/exchange/auctions/cancled
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
    "self": "/nft/exchange/auctions/canceled?page=1&limit=100",
    "first": "/nft/exchange/auctions/canceled?page=1&limit=100",
    "last": "/nft/exchange/auctions/canceled?page=1&limit=100"
  },
  "data": [
    {
      "id": "b772364d3bdb94333cdd6390c3c33910eb9444989eabfd5393f4fb75f30eb697",
      "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
      "nftAuctionCancel": {
        "auctionId": "ab1303eb497ab290318c860bda259d5fafaf45fe0624712d088bcf99ee411e3e"
      }
    }
  ]
}
```

## GET - Return Canceled Auction By Id

### Endpoint

```bash
GET /auctions/canceled/{id}
```

### Path Parameters <a id="path-parameters"></a>

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The identifier of the canceled auction to be retrieved. | Yes |

### Example

```bash
curl http://nft.protokol.com:4003/api/nft/exchange/auctions/canceled/b772364d3bdb94333cdd6390c3c33910eb9444989eabfd5393f4fb75f30eb697
```

### Response

```javascript
{
  "data": {
    "id": "b772364d3bdb94333cdd6390c3c33910eb9444989eabfd5393f4fb75f30eb697",
    "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
    "nftAuctionCancel": {
      "auctionId": "ab1303eb497ab290318c860bda259d5fafaf45fe0624712d088bcf99ee411e3e"
    }
  }
}
```



