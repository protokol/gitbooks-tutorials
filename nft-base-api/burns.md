---
description: API Endpoints for managing NFT Burn Transactions
---

# Burns

## List of Burn Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [/burns](https://docs.protokol.com/nft/nft-base-api/burns#get-return-all-burns) | return all burns | GET |
| [/burns/:id](https://docs.protokol.com/nft/nft-base-api/burns#get-return-burn-by-id) | return burn by :id | GET |

## GET - Return All Burns

Return all NFTBurn transactions

### Endpoint

```text
GET /burns
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
curl http://nft.protokol.com:4003/api/nft/burns
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
    "self": "/nft/burns?page=1&limit=100&transform=true",
    "first": "/nft/burns?page=1&limit=100&transform=true",
    "last": "/nft/burns?page=1&limit=100&transform=true"
  },
  "data": [
    {
      "id": "23a7f2a6a3dfeeacac170bcbbaac2002a030192b3ab8b00a5fef0b7264bc7f02",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "nftBurn": {
        "nftId": "95aa99984e1fbc5af94742a59ab5e5d3bda877aee98b098bbee8cd33afc9f26c"
      }
    }
  ]
}
```

## GET - Return Burn By ID

Return a NFTBurn transaction by specified id.

### Endpoint

```bash
GET /burns/{id}
```

### Path Parameters

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The identifier of the burn to be retrieved. | Yes |

### Example

```bash
curl http://nft.protokol.com:4003/api/nft/burns/23a7f2a6a3dfeeacac170bcbbaac2002a030192b3ab8b00a5fef0b7264bc7f02
```

### Response

```javascript
{
  "data": {
    "id": "23a7f2a6a3dfeeacac170bcbbaac2002a030192b3ab8b00a5fef0b7264bc7f02",
    "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "nftBurn": {
      "nftId": "95aa99984e1fbc5af94742a59ab5e5d3bda877aee98b098bbee8cd33afc9f26c"
    }
  }
}
```



