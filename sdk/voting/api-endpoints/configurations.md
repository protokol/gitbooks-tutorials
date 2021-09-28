---
description: Voting Configurations Endpoints.
---

# Configurations

### Configurations

{% api-method method="get" host="http://localhost:4003/api/voting/configurations" path="" %}
{% api-method-summary %}
/configurations
{% endapi-method-summary %}

{% api-method-description %}
Returns configurations for voting core plugins.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
  "data": {
    "api": {
      "packageName": "@protokol/voting-api",
      "currentVersion": "1.0.0",
      "latestVersion": "1.0.0"
    },
    "transactions": {
      "packageName": "@protokol/voting-transactions",
      "currentVersion": "1.0.0",
      "latestVersion": "1.0.0"
    },
    "crypto": {
      "packageName": "@protokol/voting-crypto",
      "currentVersion": "1.0.0",
      "latestVersion": "1.0.0"
    }
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

```text
curl http://localhost:4003/api/voting/configurations
```

