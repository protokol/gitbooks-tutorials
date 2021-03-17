---
description: API Endpoints For Managing Assets
---

# Assets

## List of Asset Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [/assets](https://docs.protokol.com/nft/nft-base-api/assets#get-return-all-assets) | return all assets | GET |
| [/assets/:id](https://docs.protokol.com/nft/nft-base-api/assets#get-return-asset-by-id) | return asset by :id | GET |
| [/assets/:id/wallets](https://docs.protokol.com/nft/nft-base-api/assets#get-return-assets-wallet) | return the wallet owning an asset | GET |
| /assets/wallets/:id | return the assets that wallet owns | GET |
| [/assets/search](https://docs.protokol.com/nft/nft-base-api/assets#post-search-assets-by-attributes) | search assets | POST |

## GET - Return All Assets

Returns assets in a paginated manner.

### Endpoint

```text
GET /assets
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
curl https://api.protokol.com/api/nft/assets
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
    "self": "/nft/assets?page=1&limit=100&transform=true",
    "first": "/nft/assets?page=1&limit=100&transform=true",
    "last": "/nft/assets?page=1&limit=100&transform=true"
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



## GET - Return Asset By ID

Returns a specific asset and its properties, based on the specified asset id.

### Endpoint

```bash
GET /assets/{id}
```

### Path parameters

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The identifier of the asset to be retrieved. | Yes |
| transform | boolean | If returns modified or raw data. | No |

### Example

```bash
curl https://api.protokol.com/api/nft/assets/baab82791f89a7f0af9e806dd2c634c9064903e514d1053179ff03f6d3d40866
```

### Response

```javascript
{
  "data": {
    "id": "efbd8b013d408584b2b5d170df4cc685b0495b8fecad0f6551ddc13105043b59",
    "ownerPublicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
    "collectionId": "e38324971ab923b6d74693448cad180207b4aa99ca4f5c20625dc290cd8b7e55",
    "attributes": {
      "name": "Antonio Caracciolo",
      "pac": 78,
      "sho": 65,
      "pas": 23,
      "dri": 32,
      "def": 21,
      "phy": 12
    },
    "timestamp": {
      "epoch": 105746776,
      "unix": 1595847976,
      "human": "2020-07-27T11:06:16.000Z"
    }
  }
}
```

## GET - Return Assets Wallet

Returns a specific asset's owner wallet information.

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
curl https://api.protokol.com/api/nft/assets/baab82791f89a7f0af9e806dd2c634c9064903e514d1053179ff03f6d3d40866/wallets
```

### Response

```javascript
{
  "data": {
    "address": "AV6GP5qhhsZG6MHb4gShy22doUnVjEKHcN",
    "publicKey": "022f2978d57f95c021b9d4bf082b482738ce392bcf6bc213710e7a21504cfeb5a0",
    "nft": {
      "collections": {
        "e38324971ab923b6d74693448cad180207b4aa99ca4f5c20625dc290cd8b7e55": {
          "currentSupply": 2,
          "nftCollectionAsset": {
            "name": "FIFA-20-PLAYERS",
            "description": "FIFA 2020 Players",
            "maximumSupply": 100,
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
      "assetsIds": [
        "efbd8b013d408584b2b5d170df4cc685b0495b8fecad0f6551ddc13105043b59",
        "194a9b4768faf5e85441c2c900eb0be6ac8e8a80074e6ee78f7ef9295b1f50a5"
      ]
    }
  }
}
```

## GET - Return Wallet's Assets

Returns the assets that a wallet owns.

### Endpoint

```bash
GET /assets/wallet/{id}
```

### Path parameters

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The public key of a wallet | Yes |

### **Query Parameters**

| **Name** | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| page | int | The number of the page that will be returned. | No |
| limit | int  | The number of resources per page. | No |
| orderBy | string | Type by which should order resources. | No |
| transform | boolean | If returns modified or raw data. | No |

### Example

```bash
curl https://api.protokol.com/api/nft/assets/wallet/03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37
```

### Response

```javascript
{
   "meta":{
      "totalCountIsEstimate":true,
      "count":1,
      "pageCount":1,
      "totalCount":1,
      "next":null,
      "previous":null,
      "self":"/nft/assets/wallet/03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37?limit=1&transform=true&page=1",
      "first":"/nft/assets/wallet/03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37?limit=1&transform=true&page=1",
      "last":"/nft/assets/wallet/03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37?limit=1&transform=true&page=1"
   },
   "data":[
      {
         "id":"85ae652027c44696bb7b5188f951b287ed507312e827c0f0e71a363188928e84",
         "ownerPublicKey":"03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
         "senderPublicKey":"03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
         "collectionId":"76b406ad81e2731b64325d6024a67b38a0ef7c67905e6e7eb03a746cf977042a",
         "attributes":{
            "number":100,
            "string":"Card"
         },
         "timestamp":{
            "epoch":124666048,
            "unix":1614767248,
            "human":"2021-03-03T10:27:28.000Z"
         }
      }
   ]
}
```

## POST - Search Assets By Attributes

Search assets by their JSON attributes. All attributes can be searched.

### Endpoint

```bash
POST /assets/search
```

### **Query Parameters**

| **Name** | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| page | int | The number of the page that will be returned. | No |
| limit | int  | The number of resources per page. | No |
| orderBy | string | Type by which should order resources. | No |
| transform | boolean | If returns modified or raw data. | No |

### Body Parameters

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| attributeName | object | Attribute to search by. | Yes |

### Example

```bash
curl --request POST \
  --url https://api.protokol.com/api/nft/assets/search \
  --header 'content-type: application/json' \
  --data '{
	  "name": "Antonio Caracciolo"
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
    "self": "/nft/assets/search?page=1&limit=100&transform=true",
    "first": "/nft/assets/search?page=1&limit=100&transform=true",
    "last": "/nft/assets/search?page=1&limit=100&transform=true"
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

