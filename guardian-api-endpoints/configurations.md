---
description: API Endpoints for Configurations
---

# Configurations

## List of Configurations Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [/configurations](configurations.md#get-configurationss) | Return configurations for crypto and transaction package | GET |

## GET - Configurations

Returns package configurations for guardian crypto and guardian transactions.

### Endpoint <a id="endpoint"></a>

```text
GET /configurations
```

### Example

```text
curl https://api.protokol.com/api/guardian/configurations
```

### Response

```javascript
{
  "data": {
    "package": {
      "name": "@protokol/guardian-api",
      "currentVersion": "1.0.0-beta.24",
      "latestVersion": "1.0.0-beta.23"
    },
    "crypto": {
      "defaults": {
        "guardianTypeGroup": 9002,
        "version": 2,
        "guardianGroupName": {
          "minLength": 1,
          "maxLength": 40
        },
        "guardianGroupPriority": {
          "min": 0,
          "max": 1000
        }
      }
    },
    "transactions": {
      "defaults": {
        "maxDefinedGroupsPerUser": 20,
        "transactionsAllowedByDefault": true,
        "feeType": 0
      }
    }
  }
}
```

