---
description: API Endpoints For Bids
---

# Bids

## List of Bid Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [/bids](https://docs.protokol.com/nft/nft-exchange-api/bids#get-return-all-bids) | return all bids | GET |
| [/bids/:id](https://docs.protokol.com/nft/nft-exchange-api/bids#get-return-bid-by-id) | return bid by :id | GET |
| [/bids/:id/wallets](https://docs.protokol.com/nft/nft-exchange-api/bids#get-return-bids-wallet) | return the wallet owning a bid | GET |
| [/bids/search](https://docs.protokol.com/nft/nft-exchange-api/bids#post-search-bids) | search bids | POST |
| [/bids/canceled](https://docs.protokol.com/nft/nft-exchange-api/bids#get-return-all-canceled-bids) | return all canceled bids | GET |
| [/bids/canceled/:id](https://docs.protokol.com/nft/nft-exchange-api/bids#get-return-canceled-bid-by-id) | return canceled bid by :id | GET |

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
      "id": "d86c6dc4cb3534549088fe96b06ccd90bde6e6953e14ddd2b9de1d291540bd1a",
      "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
      "nftBid": {
        "auctionId": "4acf50de691a6173a07ccb769381003685ebbdb2dbc9d7601baa882cc9bbfd56",
        "bidAmount": "1223"
      },
      "timestamp": {
        "epoch": 105742784,
        "unix": 1595843984,
        "human": "2020-07-27T09:59:44.000Z"
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
	  "bidAmount": "1223"
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
    "self": "/nft/exchange/bids/search?page=1&limit=100&transform=true",
    "first": "/nft/exchange/bids/search?page=1&limit=100&transform=true",
    "last": "/nft/exchange/bids/search?page=1&limit=100&transform=true"
  },
  "data": [
    {
      "id": "d86c6dc4cb3534549088fe96b06ccd90bde6e6953e14ddd2b9de1d291540bd1a",
      "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
      "nftBid": {
        "auctionId": "4acf50de691a6173a07ccb769381003685ebbdb2dbc9d7601baa882cc9bbfd56",
        "bidAmount": "1223"
      },
      "timestamp": {
        "epoch": 105742784,
        "unix": 1595843984,
        "human": "2020-07-27T09:59:44.000Z"
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
    "self": "/nft/exchange/bids/canceled?page=1&limit=100&transform=true",
    "first": "/nft/exchange/bids/canceled?page=1&limit=100&transform=true",
    "last": "/nft/exchange/bids/canceled?page=1&limit=100&transform=true"
  },
  "data": [
    {
      "id": "af0b1ee7d47c5342724a9e8567ff0fe4342a9bff522b2ca243c32d779e00b722",
      "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
      "nftBidCancel": {
        "bidId": "d86c6dc4cb3534549088fe96b06ccd90bde6e6953e14ddd2b9de1d291540bd1a"
      },
      "timestamp": {
        "epoch": 105742936,
        "unix": 1595844136,
        "human": "2020-07-27T10:02:16.000Z"
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

