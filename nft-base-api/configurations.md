---
description: Api endpoints for configurations.
---

# Configurations

### GET - Configurations

**Endpoint:**

```text
GET /configurations
```

**Example:**

```bash
curl http://nft.protokol.com:4003/api/nft/configurations
```

**Result**

```javascript
{
  "data": {
    "package": {
      "name": "@protokol/nft-base-api",
      "version": "0.1.0"
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
        "nftCollectionAllowedSchemaIssuers": {
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

