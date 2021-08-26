---
description: Nameservice Configurations Endpoints.
---

# Configurations

## GET - configurations <a id="configs"></a>

### Endpoint

```text
/configurations
```

### Example

```text
curl https://explorer.protokol.sh/api/nameservice/configurations
```

### Response

```javascript
{
  "data": {
    "api": {
      "packageName": "@protokol/nameservice-api",
      "currentVersion": "1.0.0-beta.2",
      "latestVersion": "1.0.0-beta.0",
      "defaults": {}
    },
    "transactions": {
      "packageName": "@protokol/nameservice-transactions",
      "currentVersion": "1.0.0-beta.2",
      "latestVersion": "1.0.0-beta.0",
      "defaults": {
        "defaults": {
          "feeType": 0
        }
      }
    },
    "crypto": {
      "packageName": "@protokol/nameservice-crypto",
      "currentVersion": "1.0.0-beta.2",
      "latestVersion": "1.0.0-beta.0",
      "defaults": {
        "defaults": {
          "nameserviceTypeGroup": 9004,
          "version": 2,
          "nameserviceStaticFee": 5000000000
        }
      }
    }
  }
}
```

