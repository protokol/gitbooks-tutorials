---
description: List of NFT Base Confiugrations Endpoints.
---

# Base Configurations

## Configurations

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/configurations" path=" " %}
{% api-method-summary %}
/configurations
{% endapi-method-summary %}

{% api-method-description %}
Returns Base Plugins configuration settings
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
      "name": "@protokol/nft-base-api",
      "currentVersion": "1.0.1",
      "latestVersion": "1.0.1"
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
        },
        "nftCollectionJsonSchemaByteSize": 10000,
        "nftTokenAttributesByteSize": 10000
      }
    },
    "transactions": {
      "defaults": {
        "authorizedRegistrators": [],
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
curl https://explorer.protokol.sh/api/nft/configurations
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTBaseApi("configurations").index();

>>> Promise<ApiResponse<ConfigurationsResource>>
```
{% endtab %}
{% endtabs %}

