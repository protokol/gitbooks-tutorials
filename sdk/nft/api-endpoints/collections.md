---
description: List of NFT Base Collections API Endpoints.
---

# Collections

## All Collections

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/collections" path=" " %}
{% api-method-summary %}
/collections
{% endapi-method-summary %}

{% api-method-description %}
Returns all Collections Registered
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="page" type="integer" required=false %}
The number of page that will be returned
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="integer" required=false %}
The number of resources per page
{% endapi-method-parameter %}

{% api-method-parameter name="orderBy" type="string" required=false %}
Order by specific parameter \(asc or desc\)  
Example: orderBy=id:asc
{% endapi-method-parameter %}

{% api-method-parameter name="transform" type="boolean" required=false %}
It returns modified or raw data
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "meta": {
    "totalCountIsEstimate": true,
    "count": 2,
    "pageCount": 1,
    "totalCount": 2,
    "next": null,
    "previous": null,
    "self": "/nft/collections?transform=true&page=1&limit=100",
    "first": "/nft/collections?transform=true&page=1&limit=100",
    "last": "/nft/collections?transform=true&page=1&limit=100"
  },
  "data": [
    {
      "id": "8643026a0997dc9fe74ce4aa11f522ecff651fa72ecf0127a0665fd52535bc1b",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "name": "AREX Defense Handguns",
      "description": "AREX weapons sales",
      "maximumSupply": 1000,
      "jsonSchema": {
        "type": "object",
        "additionalProperties": false,
        "required": [
          "name",
          "description",
          "serialNumber",
          "caliber",
          "length",
          "height",
          "width",
          "barrelLength"
        ],
        "properties": {
          "name": {
            "type": "string",
            "maxLength": 120,
            "minLength": 1
          },
          "description": {
            "type": "string",
            "maxLength": 3000,
            "minLength": 1
          },
          "serialNumber": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "caliber": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "length": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "height": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "width": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "barrelLength": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "weight": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "weightWithMag": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "frameColors": {
            "type": "string",
            "maxLength": 255,
            "minLength": 1
          },
          "slide": {
            "type": "string",
            "maxLength": 255,
            "minLength": 1
          },
          "slights": {
            "type": "string",
            "maxLength": 255,
            "minLength": 1
          },
          "frame": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "firingPinSafety": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "triggerSafety": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "ambidextrousManualSafety": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "ipfsImageHash": {
            "type": "string",
            "maxLength": 255,
            "minLength": 1
          }
        }
      },
      "timestamp": {
        "epoch": 143237072,
        "unix": 1633338272,
        "human": "2021-10-04T09:04:32.000Z"
      }
    },
    ...
  ]
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
curl https://explorer.protokol.sh/api/nft/collections
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTBaseApi("collections").all();

>>> Promise<ApiResponseWithPagination<CollectionsResource[]>>
```
{% endtab %}
{% endtabs %}

## Collection By id

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/collections/:id" path=" " %}
{% api-method-summary %}
/collections/:id
{% endapi-method-summary %}

{% api-method-description %}
Return collection by its id
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The identifier of the collection
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="transform" type="boolean" required=false %}
It returns modified or raw data
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "data": {
    "id": "8643026a0997dc9fe74ce4aa11f522ecff651fa72ecf0127a0665fd52535bc1b",
    "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "name": "AREX Defense Handguns",
    "description": "AREX weapons sales",
    "maximumSupply": 1000,
    "jsonSchema": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "name",
        "description",
        "serialNumber",
        "caliber",
        "length",
        "height",
        "width",
        "barrelLength"
      ],
      "properties": {
        "name": {
          "type": "string",
          "maxLength": 120,
          "minLength": 1
        },
        "description": {
          "type": "string",
          "maxLength": 3000,
          "minLength": 1
        },
        "serialNumber": {
          "type": "string",
          "maxLength": 40,
          "minLength": 1
        },
        "caliber": {
          "type": "string",
          "maxLength": 40,
          "minLength": 1
        },
        "length": {
          "type": "string",
          "maxLength": 40,
          "minLength": 1
        },
        "height": {
          "type": "string",
          "maxLength": 40,
          "minLength": 1
        },
        "width": {
          "type": "string",
          "maxLength": 40,
          "minLength": 1
        },
        "barrelLength": {
          "type": "string",
          "maxLength": 40,
          "minLength": 1
        },
        "weight": {
          "type": "string",
          "maxLength": 40,
          "minLength": 1
        },
        "weightWithMag": {
          "type": "string",
          "maxLength": 40,
          "minLength": 1
        },
        "frameColors": {
          "type": "string",
          "maxLength": 255,
          "minLength": 1
        },
        "slide": {
          "type": "string",
          "maxLength": 255,
          "minLength": 1
        },
        "slights": {
          "type": "string",
          "maxLength": 255,
          "minLength": 1
        },
        "frame": {
          "type": "string",
          "maxLength": 40,
          "minLength": 1
        },
        "firingPinSafety": {
          "type": "string",
          "maxLength": 40,
          "minLength": 1
        },
        "triggerSafety": {
          "type": "string",
          "maxLength": 40,
          "minLength": 1
        },
        "ambidextrousManualSafety": {
          "type": "string",
          "maxLength": 40,
          "minLength": 1
        },
        "ipfsImageHash": {
          "type": "string",
          "maxLength": 255,
          "minLength": 1
        }
      }
    },
    "timestamp": {
      "epoch": 143237072,
      "unix": 1633338272,
      "human": "2021-10-04T09:04:32.000Z"
    }
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 404,
  "error": "Not Found",
  "message": "Collection not found"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 422,
  "error": "Unprocessable Entity",
  "message": "\"id\" length must be 64 characters long"
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
curl https://explorer.protokol.sh/api/nft/collections/a6ebed9672c970f4eeb4387321806e5eb478d9609b5d67401ecbb32fde759425
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTBaseApi("collections").get("VALID_ID");

>>> Promise<ApiResponse<CollectionsResource>>
```
{% endtab %}
{% endtabs %}

## Collection Schema

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/collections/:id/schema" path=" " %}
{% api-method-summary %}
/collections/:id/schema
{% endapi-method-summary %}

{% api-method-description %}
Returns JSON schema registered by the collection
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The identifier of the collection
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="transform" type="boolean" required=false %}
It returns modified or raw data
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "data": {
    "id": "8643026a0997dc9fe74ce4aa11f522ecff651fa72ecf0127a0665fd52535bc1b",
    "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "type": "object",
    "additionalProperties": false,
    "required": [
      "name",
      "description",
      "serialNumber",
      "caliber",
      "length",
      "height",
      "width",
      "barrelLength"
    ],
    "properties": {
      "name": {
        "type": "string",
        "maxLength": 120,
        "minLength": 1
      },
      "description": {
        "type": "string",
        "maxLength": 3000,
        "minLength": 1
      },
      "serialNumber": {
        "type": "string",
        "maxLength": 40,
        "minLength": 1
      },
      "caliber": {
        "type": "string",
        "maxLength": 40,
        "minLength": 1
      },
      "length": {
        "type": "string",
        "maxLength": 40,
        "minLength": 1
      },
      "height": {
        "type": "string",
        "maxLength": 40,
        "minLength": 1
      },
      "width": {
        "type": "string",
        "maxLength": 40,
        "minLength": 1
      },
      "barrelLength": {
        "type": "string",
        "maxLength": 40,
        "minLength": 1
      },
      "weight": {
        "type": "string",
        "maxLength": 40,
        "minLength": 1
      },
      "weightWithMag": {
        "type": "string",
        "maxLength": 40,
        "minLength": 1
      },
      "frameColors": {
        "type": "string",
        "maxLength": 255,
        "minLength": 1
      },
      "slide": {
        "type": "string",
        "maxLength": 255,
        "minLength": 1
      },
      "slights": {
        "type": "string",
        "maxLength": 255,
        "minLength": 1
      },
      "frame": {
        "type": "string",
        "maxLength": 40,
        "minLength": 1
      },
      "firingPinSafety": {
        "type": "string",
        "maxLength": 40,
        "minLength": 1
      },
      "triggerSafety": {
        "type": "string",
        "maxLength": 40,
        "minLength": 1
      },
      "ambidextrousManualSafety": {
        "type": "string",
        "maxLength": 40,
        "minLength": 1
      },
      "ipfsImageHash": {
        "type": "string",
        "maxLength": 255,
        "minLength": 1
      }
    },
    "timestamp": {
      "epoch": 143237072,
      "unix": 1633338272,
      "human": "2021-10-04T09:04:32.000Z"
    }
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 404,
  "error": "Not Found",
  "message": "Collection not found"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 422,
  "error": "Unprocessable Entity",
  "message": "\"id\" length must be 64 characters long"
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
curl https://explorer.protokol.sh/api/nft/collections/a6ebed9672c970f4eeb4387321806e5eb478d9609b5d67401ecbb32fde759425/schema
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTBaseApi("collections").getSchema("VALID_ID");

>>> Promise<ApiResponse<Schema>>
```
{% endtab %}
{% endtabs %}

## Collections Wallet

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/collections/:id/wallets " path=" " %}
{% api-method-summary %}
/collections/:id/wallets
{% endapi-method-summary %}

{% api-method-description %}
Returns wallet of owned collection
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The identifier of the collection
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
    "nft": {
      "collections": [
        {
          "collectionId": "8643026a0997dc9fe74ce4aa11f522ecff651fa72ecf0127a0665fd52535bc1b",
          "currentSupply": 3,
          "nftCollectionAsset": {
            "name": "AREX Defense Handguns",
            "description": "AREX weapons sales",
            "maximumSupply": 1000,
            "jsonSchema": {
              "type": "object",
              "additionalProperties": false,
              "required": [
                "name",
                "description",
                "serialNumber",
                "caliber",
                "length",
                "height",
                "width",
                "barrelLength"
              ],
              "properties": {
                "name": {
                  "type": "string",
                  "maxLength": 120,
                  "minLength": 1
                },
                "description": {
                  "type": "string",
                  "maxLength": 3000,
                  "minLength": 1
                },
                "serialNumber": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "caliber": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "length": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "height": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "width": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "barrelLength": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "weight": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "weightWithMag": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "frameColors": {
                  "type": "string",
                  "maxLength": 255,
                  "minLength": 1
                },
                "slide": {
                  "type": "string",
                  "maxLength": 255,
                  "minLength": 1
                },
                "slights": {
                  "type": "string",
                  "maxLength": 255,
                  "minLength": 1
                },
                "frame": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "firingPinSafety": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "triggerSafety": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "ambidextrousManualSafety": {
                  "type": "string",
                  "maxLength": 40,
                  "minLength": 1
                },
                "ipfsImageHash": {
                  "type": "string",
                  "maxLength": 255,
                  "minLength": 1
                }
              }
            }
          }
        },
       ...
      ],
      "assetsIds": [
        "f811518958861d4c1e72943f646b1bd848f606e6cc9bd6300480e6a0b501cf47",
        "4f1f337873d530838dba06c9ec256cfd8a2acf7a94e87fbb0cb4c7304d3e6788"
      ]
    }
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 404,
  "error": "Not Found",
  "message": "Collection not found"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=422 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "statusCode": 422,
  "error": "Unprocessable Entity",
  "message": "\"id\" length must be 64 characters long"
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
curl https://explorer.protokol.sh/api/nft/collections/a6ebed9672c970f4eeb4387321806e5eb478d9609b5d67401ecbb32fde759425/wallets
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTBaseApi("collections").wallet("VALID_ID");

>>> Promise<ApiResponse<CollectionsWallet>>
```
{% endtab %}
{% endtabs %}

## Search Collection

{% api-method method="post" host="https://explorer.protokol.sh/api/nft/collections/search" path=" " %}
{% api-method-summary %}
/collections/search
{% endapi-method-summary %}

{% api-method-description %}
Search collection by attributes
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="page" type="integer" required=false %}
The number of page that will be returned
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="integer" required=false %}
The number of resources per page
{% endapi-method-parameter %}

{% api-method-parameter name="orderBy" type="string" required=false %}
Order by specific parameter \(asc or desc\)  
Example: orderBy=id:asc
{% endapi-method-parameter %}

{% api-method-parameter name="transform" type="boolean" required=false %}
It returns modified or raw data
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="attributeName" type="object" required=false %}
Attribute to search by
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "meta": {
    "totalCountIsEstimate": true,
    "count": 2,
    "pageCount": 1,
    "totalCount": 2,
    "next": null,
    "previous": null,
    "self": "/nft/collections/search?transform=true&page=1&limit=100",
    "first": "/nft/collections/search?transform=true&page=1&limit=100",
    "last": "/nft/collections/search?transform=true&page=1&limit=100"
  },
  "data": [
    {
      "id": "8643026a0997dc9fe74ce4aa11f522ecff651fa72ecf0127a0665fd52535bc1b",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "name": "AREX Defense Handguns",
      "description": "AREX weapons sales",
      "maximumSupply": 1000,
      "jsonSchema": {
        "type": "object",
        "additionalProperties": false,
        "required": [
          "name",
          "description",
          "serialNumber",
          "caliber",
          "length",
          "height",
          "width",
          "barrelLength"
        ],
        "properties": {
          "name": {
            "type": "string",
            "maxLength": 120,
            "minLength": 1
          },
          "description": {
            "type": "string",
            "maxLength": 3000,
            "minLength": 1
          },
          "serialNumber": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "caliber": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "length": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "height": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "width": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "barrelLength": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "weight": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "weightWithMag": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "frameColors": {
            "type": "string",
            "maxLength": 255,
            "minLength": 1
          },
          "slide": {
            "type": "string",
            "maxLength": 255,
            "minLength": 1
          },
          "slights": {
            "type": "string",
            "maxLength": 255,
            "minLength": 1
          },
          "frame": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "firingPinSafety": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "triggerSafety": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "ambidextrousManualSafety": {
            "type": "string",
            "maxLength": 40,
            "minLength": 1
          },
          "ipfsImageHash": {
            "type": "string",
            "maxLength": 255,
            "minLength": 1
          }
        }
      },
      "timestamp": {
        "epoch": 143237072,
        "unix": 1633338272,
        "human": "2021-10-04T09:04:32.000Z"
      }
    },
    ...
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Examples

{% tabs %}
{% tab title="Curl" %}
```bash
curl --request POST \
  --url https://explorer.protokol.sh/api/nft/collections/search \
  --header 'content-type: application/json' \
  --data '{"jsonSchema": {"name": "AREX Defense Handguns"}'
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = connection.NFTBaseApi("collections").searchByCollections({
     jsonSchema: {
      "VALID_JSON_OBJECT"
      },
});

    >>> Promise<ApiResponseWithPagination<CollectionsResource[]>>
```
{% endtab %}
{% endtabs %}

## Collection Assets

{% api-method method="get" host="https://explorer.protokol.sh/api/nft/collections/:id/assets" path=" " %}
{% api-method-summary %}
/collections/:id/assets
{% endapi-method-summary %}

{% api-method-description %}
Returns assets belonging to specific collection
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The identifier of the collection
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="page" type="integer" required=false %}
The number of the page that will be returned
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="integer" required=false %}
The number of resources per page
{% endapi-method-parameter %}

{% api-method-parameter name="orderBy" type="string" required=false %}
Order by specific parameter \(asc or desc\)  
Example: orderBy=id:asc
{% endapi-method-parameter %}

{% api-method-parameter name="transform" type="boolean" required=false %}
It returns modified or raw data
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "meta": {
    "totalCountIsEstimate": true,
    "count": 3,
    "pageCount": 1,
    "totalCount": 3,
    "next": null,
    "previous": null,
    "self": "/nft/collections/8643026a0997dc9fe74ce4aa11f522ecff651fa72ecf0127a0665fd52535bc1b/assets?transform=true&page=1&limit=100",
    "first": "/nft/collections/8643026a0997dc9fe74ce4aa11f522ecff651fa72ecf0127a0665fd52535bc1b/assets?transform=true&page=1&limit=100",
    "last": "/nft/collections/8643026a0997dc9fe74ce4aa11f522ecff651fa72ecf0127a0665fd52535bc1b/assets?transform=true&page=1&limit=100"
  },
  "data": [
    {
      "id": "f811518958861d4c1e72943f646b1bd848f606e6cc9bd6300480e6a0b501cf47",
      "ownerPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "senderPublicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "collectionId": "8643026a0997dc9fe74ce4aa11f522ecff651fa72ecf0127a0665fd52535bc1b",
      "attributes": {
        "name": "AREX ALPHA",
        "description": "THE AREX ALPHA IS THE NEXT EVOLUTIONARY STEP IN THE AREX HANDGUN FAMILY. IT IS A DIRECT DESCENDANT OF THE AREX ZERO 1 AND HAS INHERITED ITS TOUGHNESS AND RELIABILITY. LISTENING TO THE PRACTICAL SHOOTERS, AREX DESIGNED AND DEVELOPED A PISTOL THAT EXCELS IN COMPETITIVE PRACTICAL SHOOTING AS WELL AS IN TACTICAL SCENARIOS. WITH THE ELUSIVE AND ALL IMPORTANT SHOOTABILITY BEING AREXS PRIMARY GOAL, A STEEL FRAME WAS USED IN PLACE OF AN ALUMINUM ONE. A REENGINEERED GRIP RESULTS IN SHORTER TRIGGER REACH AND NOTABLY HIGHER HAND POSITION. AN UNDERCUT TRIGGER GUARD AND EXTENDED BEAVERTAIL COMPLETE THE ERGONOMIC TRANSFORMATION. THE LONG SLIDE HOUSES A FIVE INCH BARREL, PROVIDING A LONGER LINE OF SIGHT FOR FASTER AND MORE ACCURATE SHOTS. THE SLIDE HAS BEEN LIGHTENED SIGNIFICANTLY UTILIZING LIGHTENING CUTS TO ACCOMPLISH FASTER CYCLING.",
        "serialNumber": "6789897676898976",
        "caliber": "9 x 19 mm",
        "length": "226 mm // 8.9 inches",
        "height": "155 mm // 6.1 inches",
        "width": "42 mm // 1.65 inches",
        "barrelLength": "127 mm // 5.0 inches",
        "weight": "1202 g // 42.3 oz",
        "frameColors": "Nitrocarburized steel // Graphite black color // Blue // Red",
        "slide": "Nitrocarburized steel // Graphite black color",
        "slights": "Fiber optic front and fully adjustable black rear sight",
        "ipfsImageHash": "QmPbvs8G1jVaH6iHBUC2W1YnwY9AhzD98ydVqnhG9KMej1"
      },
      "timestamp": {
        "epoch": 143237168,
        "unix": 1633338368,
        "human": "2021-10-04T09:06:08.000Z"
      }
    },
    ...
  ]
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
curl https://explorer.protokol.sh/api/nft/collections/a6ebed9672c970f4eeb4387321806e5eb478d9609b5d67401ecbb32fde759425/assets
```
{% endtab %}

{% tab title="Second Tab" %}
```typescript
const response = connection.NFTBaseApi("collections").assetByCollectionId("VALID_ID");

>>> Promise<ApiResponseWithPagination<CollectionsAsset[]>>
```
{% endtab %}
{% endtabs %}

