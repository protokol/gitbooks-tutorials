---
description: API Endpoints For Auctions
---

# Auctions

## List of Auction Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [/auctions](https://docs.protokol.com/nft/nft-exchange-api/auctions#get-return-all-auctions) | return all active auctions | GET |
| [/auctions/:id](https://docs.protokol.com/nft/nft-exchange-api/auctions#get-return-an-auction-by-id) | return auction by :id | GET |
| [/auctions/:id/wallets](https://docs.protokol.com/nft/nft-exchange-api/auctions#get-return-auctions-wallet) | return the wallet owning an auction | GET |
| [/auctions/search](https://docs.protokol.com/nft/nft-exchange-api/auctions#post-search-auctions) | search auctions | POST |
| [/auctions/canceled](https://docs.protokol.com/nft/nft-exchange-api/auctions#get-return-all-canceled-auctions) | return all canceled auctions | GET |
| [/auctions/canceled/:id](https://docs.protokol.com/nft/nft-exchange-api/auctions#get-return-canceled-auction-by-id) | return canceled auction by :id | GET |

## GET - Return All Active Auctions

Active auctions are auctions that have NOT been canceled or closed with a succesfull NFTAcceptTrade Transaction.

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
curl https://api.protokol.com/api/nft/exchange/auctions
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
    "self": "/nft/exchange/auctions?transform=true&page=1&limit=100",
    "first": "/nft/exchange/auctions?transform=true&page=1&limit=100",
    "last": "/nft/exchange/auctions?transform=true&page=1&limit=100"
  },
  "data": [
    {
      "id": "7584c9e10b5beb9e41eb1d328030b91352bb7a2198f658f6962233b9de86db99",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "nftAuction": {
        "nftIds": [
          "5ad837bcec77fc2b5e9f8bfe89337f0dc02b95ec2ecac4842a95e4d4a1313f7b"
        ],
        "startAmount": "999",
        "expiration": {
          "blockHeight": 1000000
        }
      },
      "timestamp": {
        "epoch": 105741720,
        "unix": 1595842920,
        "human": "2020-07-27T09:42:00.000Z"
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
| transform | boolean | If returns modified or raw data. | No |

### Example

```bash
curl https://api.protokol.com/api/nft/exchange/auctions/1d1757bc7e598fd73f0ec670e1f2c517d7d9a2a94d447bd5daa0a9384ebd4e7e
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
    },
    "timestamp": {
      "epoch": 105746776,
      "unix": 1595847976,
      "human": "2020-07-27T11:06:16.000Z"
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
curl https://api.protokol.com/api/nft/exchange/auctions/1d1757bc7e598fd73f0ec670e1f2c517d7d9a2a94d447bd5daa0a9384ebd4e7e/wallets
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
  --url https://api.protokol.com/api/nft/exchange/auctions/search \
  --header 'content-type: application/json' \
  --data '{
	  "nftIds": ["238d98bd751025decc853a46da8fb995c68a9684a4156bcfa414e7596b6e73b1"]
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
    "self": "/nft/exchange/auctions/search?page=1&limit=100&transform=true",
    "first": "/nft/exchange/auctions/search?page=1&limit=100&transform=true",
    "last": "/nft/exchange/auctions/search?page=1&limit=100&transform=true"
  },
  "data": [
    {
      "id": "7584c9e10b5beb9e41eb1d328030b91352bb7a2198f658f6962233b9de86db99",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "nftAuction": {
        "nftIds": [
          "5ad837bcec77fc2b5e9f8bfe89337f0dc02b95ec2ecac4842a95e4d4a1313f7b"
        ],
        "startAmount": "999",
        "expiration": {
          "blockHeight": 1000000
        }
      },
      "timestamp": {
        "epoch": 105741720,
        "unix": 1595842920,
        "human": "2020-07-27T09:42:00.000Z"
      }
    }
  ]
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
curl https://api.protokol.com/api/nft/exchange/auctions/cancled
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
    "self": "/nft/exchange/auctions/canceled?page=1&limit=100&transform=true",
    "first": "/nft/exchange/auctions/canceled?page=1&limit=100&transform=true",
    "last": "/nft/exchange/auctions/canceled?page=1&limit=100&transform=true"
  },
  "data": [
    {
      "id": "e90f3db3c4c144f78da7b0d7d19d1c859f61c24933b1ec97e2ebfe7abbc0a4d8",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "nftAuctionCancel": {
        "auctionId": "7584c9e10b5beb9e41eb1d328030b91352bb7a2198f658f6962233b9de86db99"
      },
      "timestamp": {
        "epoch": 105742000,
        "unix": 1595843200,
        "human": "2020-07-27T09:46:40.000Z"
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
| transform | boolean | If returns modified or raw data. | No |

### Example

```bash
curl https://api.protokol.com/api/nft/exchange/auctions/canceled/3c26dee62a937aaf49c25e64d2776117362e9dc30dd6f27c839081d1e44608bc
```

### Response

```javascript
{
  "data": {
    "id": "b772364d3bdb94333cdd6390c3c33910eb9444989eabfd5393f4fb75f30eb697",
    "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
    "nftAuctionCancel": {
      "auctionId": "ab1303eb497ab290318c860bda259d5fafaf45fe0624712d088bcf99ee411e3e"
    },
    "timestamp": {
      "epoch": 105746776,
      "unix": 1595847976,
      "human": "2020-07-27T11:06:16.000Z"
    }
  }
}
```



