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
curl http://nft.protokol.com:4003/api/nft/assets
```

### Response

```javascript
{
  "meta": {
    "totalCountIsEstimate": true,
    "count": 2,
    "pageCount": 1,
    "totalCount": 2,
    "next": null,
    "previous": null,
    "self": "/nft/assets?page=1&limit=100&transform=true",
    "first": "/nft/assets?page=1&limit=100&transform=true",
    "last": "/nft/assets?page=1&limit=100&transform=true"
  },
  "data": [
    {
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
      }
    },
    {
      "id": "194a9b4768faf5e85441c2c900eb0be6ac8e8a80074e6ee78f7ef9295b1f50a5",
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

### Example

```bash
curl http://nft.protokol.com:4003/api/nft/assets/efbd8b013d408584b2b5d170df4cc685b0495b8fecad0f6551ddc13105043b59
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
curl http://nft.protokol.com:4003/api/nft/assets/efbd8b013d408584b2b5d170df4cc685b0495b8fecad0f6551ddc13105043b59/wallets
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
  --url http://nft.protokol.com:4003/api/nft/assets/search \
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
    "count": 2,
    "pageCount": 1,
    "totalCount": 2,
    "next": null,
    "previous": null,
    "self": "/nft/assets/search?page=1&limit=100&transform=true",
    "first": "/nft/assets/search?page=1&limit=100&transform=true",
    "last": "/nft/assets/search?page=1&limit=100&transform=true"
  },
  "data": [
    {
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
      }
    },
    {
      "id": "194a9b4768faf5e85441c2c900eb0be6ac8e8a80074e6ee78f7ef9295b1f50a5",
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
      }
    }
  ]
}
```

