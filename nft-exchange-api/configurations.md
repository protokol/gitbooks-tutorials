---
description: API Endpoints For Viewing Exchange Plugins Configurations
---

# Configurations

## List of **Configuration** Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [/configurations](https://docs.protokol.com/nft/nft-exchange-api/configurations#configurations) | return all configurations | GET |

## GET - Configurations

### **Endpoint**

```bash
GET /configurations
```

### Example

```bash
curl https://explorer.protokol.sh/api/nft/exchange/configurations
```

### Response

```javascript
{
  "data": {
    "package": {
      "name": "@protokol/nft-exchange-api",
      "currentVersion": "1.0.0-beta.2",
      "latestVersion": "1.0.0-beta.0"
    },
    "crypto": {
      "defaults": {
        "nftExchangeTypeGroup": 9001,
        "nftAuction": {
          "minItems": 1,
          "maxItems": 10
        }
      }
    },
    "transactions": {
      "defaults": {
        "safetyDistance": 51
      }
    }
  }
}
```

