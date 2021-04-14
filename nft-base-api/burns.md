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
curl https://explorer.protokol.sh/api/nft/burns
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
    "self": "/nft/burns?page=1&limit=100&transform=true",
    "first": "/nft/burns?page=1&limit=100&transform=true",
    "last": "/nft/burns?page=1&limit=100&transform=true"
  },
  "data": [
    {
      "id": "bae71bfb5790dea7c7278f9329baf3b04745dd3378eb8801d7a94e542cd89908",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "nftBurn": {
        "nftId": "1eeef6bac21a47cc33f897ee1f4e3eb2357108e859c614acd1a99e0a1cc5a117"
      },
      "timestamp": {
        "epoch": 105741112,
        "unix": 1595842312,
        "human": "2020-07-27T09:31:52.000Z"
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
| transform | boolean | If returns modified or raw data. | No |

### Example

```bash
curl https://explorer.protokol.sh/api/nft/burns/f2c47694e32cdb7cae7e3ca8726836fac323a3175559277469faf541ae49c5b4
```

### Response

```javascript
{
  "data": {
    "id": "23a7f2a6a3dfeeacac170bcbbaac2002a030192b3ab8b00a5fef0b7264bc7f02",
    "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "nftBurn": {
      "nftId": "95aa99984e1fbc5af94742a59ab5e5d3bda877aee98b098bbee8cd33afc9f26c"
    },
    "timestamp": {
      "epoch": 105746776,
      "unix": 1595847976,
      "human": "2020-07-27T11:06:16.000Z"
    }
  }
}
```



