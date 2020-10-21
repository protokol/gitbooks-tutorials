---
description: API Endpoints For Viewing Base Plugins Configurations
---

# Configurations

## List of **Configuration** Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [/configurations](https://docs.protokol.com/nft/nft-base-api/configurations#get-configurations) | return all configurations | GET |

## GET - Configurations

### **Endpoint**

```text
GET /configurations
```

### **Example**

```bash
curl https://api.protokol.com/api/nft/configurations
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

