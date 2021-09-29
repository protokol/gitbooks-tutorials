---
description: Guardian Configurations Endpoints.
---

# Configurations

## Configurations

{% api-method method="get" host="https://explorer.protokol.sh/api/guardian/configurations" path=" " %}
{% api-method-summary %}
/configurations
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "data": {
    "package": {
      "name": "@protokol/guardian-api",
      "currentVersion": "1.0.0",
      "latestVersion": "1.0.0"
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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Examples

{% tabs %}
{% tab title="Curl" %}
```text
curl https://explorer.protokol.sh/api/guardian/configurations
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = await connection.guardianApi("configurations").index();

>>> Promise<ApiResponse<GuardianConfigurations>>
```
{% endtab %}
{% endtabs %}

