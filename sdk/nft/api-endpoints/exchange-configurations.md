---
description: List of NFT Exchange Configurations Endpoints
---

# Exchange Configurations

## Configurations

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/exchange/configurations" path=" " %}
{% api-method-summary %}
/configurations
{% endapi-method-summary %}

{% api-method-description %}
Returns Exchange Plugins configuration settings
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
      "name": "@protokol/nft-exchange-api",
      "currentVersion": "1.0.1",
      "latestVersion": "1.0.1"
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
curl https://explorer.protokol.sh/api/nft/exchange/configurations
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTExchangeApi("configurations").index();

>>> Promise<ApiResponse<ConfigurationsResource>>
```
{% endtab %}
{% endtabs %}

