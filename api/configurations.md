---
description: Api endpoints for configurations
---

# Configurations

## List of **Configuration** Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [/configurations](https://docs.protokol.com/nft/api/nft-base-api/configurations#get-configurations) | return all configurations | GET |

## GET - Configurations

### **Endpoint**

```text
GET /configurations
```

### **Example**

```bash
curl http://nft.protokol.com:4003/api/nft/configurations
```

### **Result**

```javascript
{
  "data": {
    "package": {
      "name": "@protokol/nft-base-api",
      "currentVersion": "1.0.0-beta.2",
      "latestVersion": "1.0.0-beta.0"
    },
    "crypto": {
      "defaults": {
        "nftBaseTypeGroup": 9000,
        "nftCollectionName": {
          "minLength": 5,
          "maxLength": 40
        },
        "nftCollectionDescription": {
          "minLength": 5,
          "maxLength": 80
        },
        "nftCollectionAllowedIssuers": {
          "minItems": 1,
          "maxItems": 10
        },
        "nftTransfer": {
          "minItems": 1,
          "maxItems": 10
        }
      }
    },
    "transactions": {
      "defaults": {}
    }
  }
}
```

\*\*\*\*

