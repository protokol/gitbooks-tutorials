---
description: Api endpoints for configurations.
---

# Configurations

### Configurations <a id="configurations"></a>

**Endpoint:**

```bash
GET /configurations
```

#### Example:

```bash
curl http://nft.protokol.com:4003/api/nft/exchange/configurations
```

#### Response

```javascript
{
  "data": {
    "package": {
      "name": "@protokol/nft-exchange-api",
      "version": "1.0.0-beta.2"
    },
    "crypto": {
      "defaults": {
        "nftExchangeTypeGroup": 9001
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

