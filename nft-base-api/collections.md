---
description: Api endpoints for collections.
---

# Collections

## Return all collections

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

## Get specific collection by id

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

## Get schema of specific collection

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

## Get collections wallet --TODO 

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

```

