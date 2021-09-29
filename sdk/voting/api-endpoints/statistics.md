---
description: Voting Statistics API Endpoints.
---

# Statistics

### /statistics/:id

{% api-method method="get" host="http://localhost:4003/api/statistics/:id " path=" " %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}
Returns statistical information of selected proposal.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
Create Proposal Id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "data": {
    "address": "ANBkoGqWeTSiaEVgVzSKZd3jS7UWzv9PSo",
    "publicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "status": "VOTING_IN_PROGRESS",
    "allVoters": "734909200000000",
    "agreed": {
      "amount": "489861200000000",
      "percentage": 66.656
    },
    "disagreed": {
      "amount": "245048000000000",
      "percentage": 33.343999999999994
    }
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Curl Example

```bash
curl http://localhost:4003/api/statistics/fe8419bda6525ef0074e733dbd3e8b671267c6c8d51b025fd7ae0812947cec30
```

