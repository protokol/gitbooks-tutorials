---
description: Api endpoints for assets.
---

# Assets

## Return assets

### Endpoint

```text
GET /assets
```

### **Query parameters**

| **Name** | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| page | int | The number of the page that will be returned. | No |
| limit | int  | The number of resources per page. | No |
| orderBy | string | Type by which should order resources. | No |
| transaform | boolean | If returns modified or raw data. | No |

### Example

```text
curl http://127.0.0.1:4003/api/nft/assets
```

### Response

```javascript
{
  "meta": {
    "totalCountIsEstimate": false,
    "count": 3,
    "pageCount": 1,
    "totalCount": 3,
    "next": null,
    "previous": null,
    "self": "/nft/assets?page=1&limit=100&transform=true",
    "first": "/nft/assets?page=1&limit=100&transform=true",
    "last": "/nft/assets?page=1&limit=100&transform=true"
  },
  "data": [
    {
      "id": "95aa99984e1fbc5af94742a59ab5e5d3bda877aee98b098bbee8cd33afc9f26c",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "collectionId": "a0b5af0fb67f45d8ab090537f5bb80650bb73de6c36934e334b07683ba305db6",
      "attributes": {
        "sales": 1300,
        "connection": 1300,
        "survival": 1300,
        "skin": 80,
        "damage": 5
      }
    },
    {
      "id": "099f664716ed062a494a7ca41bda699783f3d16bae9e61b1658ea981ccaa1a6c",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "collectionId": "a0b5af0fb67f45d8ab090537f5bb80650bb73de6c36934e334b07683ba305db6",
      "attributes": {
        "sales": 1300,
        "connection": 1300,
        "survival": 1300,
        "skin": 80,
        "damage": 5
      }
    },
    {
      "id": "37ad059074ae6cec2bff69800b8dd55723848c6a73299369f1cf5d33222899cd",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "collectionId": "a0b5af0fb67f45d8ab090537f5bb80650bb73de6c36934e334b07683ba305db6",
      "attributes": {
        "sales": 1300,
        "connection": 1300,
        "survival": 1300,
        "skin": 80,
        "damage": 5
      }
    }
  ]
}
```



## Return asset by id

### Endpoint

```bash
GET /assets/{id}
```

### Path parameters

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The identifier of the asset to be retrieved. | Yes |

### Example

```bash
curl http://127.0.0.1:4003/api/nft/assets/95aa99984e1fbc5af94742a59ab5e5d3bda877aee98b098bbee8cd33afc9f26c
```

### Response

```javascript
{
  "data": {
    "id": "95aa99984e1fbc5af94742a59ab5e5d3bda877aee98b098bbee8cd33afc9f26c",
    "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "collectionId": "a0b5af0fb67f45d8ab090537f5bb80650bb73de6c36934e334b07683ba305db6",
    "attributes": {
      "sales": 1300,
      "connection": 1300,
      "survival": 1300,
      "skin": 80,
      "damage": 5
    }
  }
}
```

## Return assets wallet

### Endpoint

```bash
GET /assets/{id}/wallets
```

### Path parameters

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The identifier of the asset. | Yes |

### Example

```bash
curl http://127.0.0.1:4003/api/nft/assets/95aa99984e1fbc5af94742a59ab5e5d3bda877aee98b098bbee8cd33afc9f26c/wallets
```

### Response

```javascript
{
  "data": {
    "address": "ANBkoGqWeTSiaEVgVzSKZd3jS7UWzv9PSo",
    "publicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "nft": {
      "base": {
        "nftCollections": [
          {
            "collectionId": "a0b5af0fb67f45d8ab090537f5bb80650bb73de6c36934e334b07683ba305db6",
            "currentSupply": 3,
            "nftCollectionAsset": {
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
        ],
        "nftIds": [
          "95aa99984e1fbc5af94742a59ab5e5d3bda877aee98b098bbee8cd33afc9f26c",
          "099f664716ed062a494a7ca41bda699783f3d16bae9e61b1658ea981ccaa1a6c",
          "37ad059074ae6cec2bff69800b8dd55723848c6a73299369f1cf5d33222899cd"
        ]
      }
    }
  }
}
```

## Search assets

### Endpoint

```bash
POST /assets/search
```

### **Query parameters**

| **Name** | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| page | int | The number of the page that will be returned. | No |
| limit | int  | The number of resources per page. | No |
| orderBy | string | Type by which should order resources. | No |
| transaform | boolean | If returns modified or raw data. | No |

### Example

```bash
curl --request POST \
  --url http://127.0.0.1:4003/api/nft/assets/search \
  --header 'content-type: application/json' \
  --data '{
	"sales": 1300
}'

```

### Response

```javascript
{
  "meta": {
    "totalCountIsEstimate": false,
    "count": 3,
    "pageCount": 1,
    "totalCount": 3,
    "next": null,
    "previous": null,
    "self": "/nft/assets/search?page=1&limit=100&transform=true",
    "first": "/nft/assets/search?page=1&limit=100&transform=true",
    "last": "/nft/assets/search?page=1&limit=100&transform=true"
  },
  "data": [
    {
      "id": "95aa99984e1fbc5af94742a59ab5e5d3bda877aee98b098bbee8cd33afc9f26c",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "collectionId": "a0b5af0fb67f45d8ab090537f5bb80650bb73de6c36934e334b07683ba305db6",
      "attributes": {
        "sales": 1300,
        "connection": 1300,
        "survival": 1300,
        "skin": 80,
        "damage": 5
      }
    },
    {
      "id": "099f664716ed062a494a7ca41bda699783f3d16bae9e61b1658ea981ccaa1a6c",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "collectionId": "a0b5af0fb67f45d8ab090537f5bb80650bb73de6c36934e334b07683ba305db6",
      "attributes": {
        "sales": 1300,
        "connection": 1300,
        "survival": 1300,
        "skin": 80,
        "damage": 5
      }
    },
    {
      "id": "37ad059074ae6cec2bff69800b8dd55723848c6a73299369f1cf5d33222899cd",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "collectionId": "a0b5af0fb67f45d8ab090537f5bb80650bb73de6c36934e334b07683ba305db6",
      "attributes": {
        "sales": 1300,
        "connection": 1300,
        "survival": 1300,
        "skin": 80,
        "damage": 5
      }
    }
  ]
}
```

