---
description: Api endpoints for collections.
---

# Collections

## GET - Return all collections

### Endpoint

```text
GET /collections
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
curl http://nft.protokol.com:4003/api/nft/collections
```

### Response

```javascript
{
  "meta": {
    "totalCountIsEstimate": false,
    "count": 1,
    "pageCount": 1,
    "totalCount": 1,
    "next": null,
    "previous": null,
    "self": "/nft/collections?page=1&limit=100&transform=true",
    "first": "/nft/collections?page=1&limit=100&transform=true",
    "last": "/nft/collections?page=1&limit=100&transform=true"
  },
  "data": [
    {
      "id": "a0b5af0fb67f45d8ab090537f5bb80650bb73de6c36934e334b07683ba305db6",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "name": "protokol card",
      "description": "A card from proto game",
      "maximumSupply": 100,
      "jsonSchema": {
        "properties": {
          "sales": {
            "type": "number"
          },
          "connections": {
            "type": "number"
          },
          "survival": {
            "type": "number"
          },
          "skin": {
            "type": "number"
          },
          "damage": {
            "type": "number"
          }
        }
      }
    }
  ]
}
```

## GET - Specific collection by id

### Endpoint

```bash
GET /collections/{id}
```

### Path parameters

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The identifier of the collection to be retrieved. | Yes |

### Example

```bash
curl http://nft.protokol.com:4003/api/nft/collections/a0b5af0fb67f45d8ab090537f5bb80650bb73de6c36934e334b07683ba305db6
```

### Response

```javascript
{
  "data": {
    "id": "a0b5af0fb67f45d8ab090537f5bb80650bb73de6c36934e334b07683ba305db6",
    "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "name": "protokol card",
    "description": "A card from proto game",
    "maximumSupply": 100,
    "jsonSchema": {
      "properties": {
        "sales": {
          "type": "number"
        },
        "connections": {
          "type": "number"
        },
        "survival": {
          "type": "number"
        },
        "skin": {
          "type": "number"
        },
        "damage": {
          "type": "number"
        }
      }
    }
  }
}
```

## GET -  Schema of specific collection

### Endpoint

```bash
GET /collections/{id}/schema
```

### Path parameters

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The identifier of the collection to be retrieved. | Yes |

### Example

```bash
curl http://nft.protokol.com:4003/api/nft/collections/a0b5af0fb67f45d8ab090537f5bb80650bb73de6c36934e334b07683ba305db6/schema
```

### Response

```javascript
{
  "data": {
    "id": "a0b5af0fb67f45d8ab090537f5bb80650bb73de6c36934e334b07683ba305db6",
    "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "properties": {
      "sales": {
        "type": "number"
      },
      "connections": {
        "type": "number"
      },
      "survival": {
        "type": "number"
      },
      "skin": {
        "type": "number"
      },
      "damage": {
        "type": "number"
      }
    }
  }
}
```

## GET - Collections wallet

### Endpoint

```bash
GET /collections/wallets/{id}
```

### Path parameters

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The identifier of the collections wallet to be retrieved. | Yes |

### Example

```bash
curl http://nft.protokol.com:4003/api/nft/collections/18f7ba659b5c87737f5db131e15ad682e2e37fdf8259ec227b5bc9e5e9d9c28b/wallets
```

### Response

```javascript
{
  "data": {
    "address": "AV6GP5qhhsZG6MHb4gShy22doUnVjEKHcN",
    "publicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
    "nft": {
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
      "assetsIds": []
    }
  }
}
```

