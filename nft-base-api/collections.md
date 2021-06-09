<style>
  ad { color: red }
</style>
---
description: API Endpoints For Token Collections
---

# Collections

## List of Collection Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [/collections](https://docs.protokol.com/nft/nft-base-api/collections#get-return-all-collections) | return all collections | GET |
| [/collections/:id](https://docs.protokol.com/nft/nft-base-api/collections#get-specific-collection-by-id) | return collection by :id | GET |
| [/collections/:id/schema](https://docs.protokol.com/nft/nft-base-api/collections#get-collection-schema) | return the schema of a collection | GET |
| [/collections/:id/wallets](https://docs.protokol.com/nft/nft-base-api/collections#get-collections-wallet) | return the wallet owning a collection | GET |
| [/collections/search](https://docs.protokol.com/nft/nft-base-api/collections#post-collections-search) | search collections | POST |
| [/collections/:id/assets](https://docs.protokol.com/nft/nft-base-api/collections#get-return-all-collection-assets) | return the assets of a collection | GET |

## GET - Return All Collections

Return all registered asset collection types. 

### Endpoint

```text
GET /collections
```

### **Query Parameters**

| **Name** | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| page | int | The number of the page that will be returned. | No |
| limit | int  | The number of resources per page. | No |
| orderBy | string | Type by which should order resources. | No |
| transform | boolean | If returns modified or raw data. | No |

### Example

```text
curl https://explorer.protokol.sh/api/nft/collections
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
    "self": "/nft/collections?page=1&limit=100&transform=true",
    "first": "/nft/collections?page=1&limit=100&transform=true",
    "last": "/nft/collections?page=1&limit=100&transform=true"
  },
  "data": [
    {
      "id": "bc045f0a977d368735030c7eadaa45de5581c1ffb2b0e9e93752c82579c516fe",
      "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
      "name": "FIFA-20-PLAYERS",
      "description": "FIFA 2020 Players",
      "maximumSupply": 10,
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
      },
      "timestamp": {
        "epoch": 105746776,
        "unix": 1595847976,
        "human": "2020-07-27T11:06:16.000Z"
      }
    }
  ]
}
```

## GET - Specific Collection By ID

### Endpoint

```bash
GET /collections/{id}
```

### Path Parameters

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The identifier of the collection to be retrieved. | Yes |
| transform | boolean | If returns modified or raw data. | No |

### Example

```bash
curl https://explorer.protokol.sh/api/nft/collections/a6ebed9672c970f4eeb4387321806e5eb478d9609b5d67401ecbb32fde759425
```

### Response

```javascript
{
  "data": {
    "id": "8eeaf8899d5230b22e6979805e9a8865eb7093ccae028b46a972f80fd60c790b",
    "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
    "name": "FIFA-20-PLAYERS",
    "description": "FIFA 2020 Players",
    "maximumSupply": 1,
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
    },
    "timestamp": {
      "epoch": 105746776,
      "unix": 1595847976,
      "human": "2020-07-27T11:06:16.000Z"
    }
  }
}
```

## GET -  Collection Schema

Returns JSON schema registered by a collection.

### Endpoint

```bash
GET /collections/{id}/schema
```

### Path Parameters

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The identifier of the collection to be retrieved. | Yes |
| transform | boolean | If returns modified or raw data. | No |

### Example

```bash
curl https://explorer.protokol.sh/api/nft/collections/a6ebed9672c970f4eeb4387321806e5eb478d9609b5d67401ecbb32fde759425/schema
```

### Response

```javascript
{
  "data": {
    "id": "8eeaf8899d5230b22e6979805e9a8865eb7093ccae028b46a972f80fd60c790b",
    "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
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
    },
    "timestamp": {
      "epoch": 105746776,
      "unix": 1595847976,
      "human": "2020-07-27T11:06:16.000Z"
    }
  }
}
```

## GET - Collections Wallet

Returns owning wallet for the specified collection.

### Endpoint

```bash
GET /collections/{id}/wallets
```

### Path Parameters

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The identifier of the collections wallet to be retrieved. | Yes |

### Example

```bash
curl https://explorer.protokol.sh/api/nft/collections/a6ebed9672c970f4eeb4387321806e5eb478d9609b5d67401ecbb32fde759425/wallets
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

## POST - Collections Search

Search collections by attributes.

### Endpoint

```bash
POST /collections/search
```

### **Query Parameters**

| **Name** | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| page | int | The number of the page that will be returned. | No |
| limit | int  | The number of resources per page. | No |
| orderBy | string | Type by which should order resources. | No |
| transform | boolean | If returns modified or raw data. | N |

### Body Parameters

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| attributeName | object | Attribute to search by. | Yes |

### Example

```javascript
curl --request POST \
  --url https://explorer.protokol.sh/api/nft/collections/search \
  --header 'content-type: application/json' \
  --data '{"jsonSchema": {"properties": {"name": {"type":"string"}}}}'
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
    "self": "/nft/collections/search?page=1&limit=100&transform=true",
    "first": "/nft/collections/search?page=1&limit=100&transform=true",
    "last": "/nft/collections/search?page=1&limit=100&transform=true"
  },
  "data": [
    {
      "id": "6c456c5687b1ca1b9a89457bc26dc8a7223694084a8f89cf295fc688f5a3342b",
      "senderPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
      "name": "FIFA-20-PLAYERS",
      "description": "FIFA 2020 Players",
      "maximumSupply": 1,
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
      },
      "timestamp": {
        "epoch": 105740120,
        "unix": 1595841320,
        "human": "2020-07-27T09:15:20.000Z"
      }
    }
  ]
}
```

## GET - Return All Collection Assets

Return all created assets belonging to a specific collection.

### Endpoints

```bash
GET /collections/{id}/assets
```

### **Query Parameters**

| **Name** | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| page | int | The number of the page that will be returned. | No |
| limit | int  | The number of resources per page. | No |
| orderBy | string | Type by which should order resources. | No |
| transform | boolean | If returns modified or raw data. | No |

### Path Parameters

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The identifier of the collections id to return assets. | Yes |

### Example

```bash
curl https://explorer.protokol.sh/api/nft/collections/a6ebed9672c970f4eeb4387321806e5eb478d9609b5d67401ecbb32fde759425/assets
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
    "self": "/nft/collections/6c456c5687b1ca1b9a89457bc26dc8a7223694084a8f89cf295fc688f5a3342b/assets?page=1&limit=100&transform=true",
    "first": "/nft/collections/6c456c5687b1ca1b9a89457bc26dc8a7223694084a8f89cf295fc688f5a3342b/assets?page=1&limit=100&transform=true",
    "last": "/nft/collections/6c456c5687b1ca1b9a89457bc26dc8a7223694084a8f89cf295fc688f5a3342b/assets?page=1&limit=100&transform=true"
  },
  "data": [
    {
      "id": "1eeef6bac21a47cc33f897ee1f4e3eb2357108e859c614acd1a99e0a1cc5a117",
      "ownerPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "collectionId": "6c456c5687b1ca1b9a89457bc26dc8a7223694084a8f89cf295fc688f5a3342b",
      "attributes": {
        "name": "Antonio Caracciolo",
        "pac": 90,
        "sho": 65,
        "pas": 23,
        "dri": 32,
        "def": 21,
        "phy": 12
      },
      "timestamp": {
        "epoch": 105740128,
        "unix": 1595841328,
        "human": "2020-07-27T09:15:28.000Z"
      }
    }
  ]
}
```

