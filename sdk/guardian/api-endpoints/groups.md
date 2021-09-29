---
description: Guardian Groups Endpoints.
---

# Groups

## Groups

{% api-method method="get" host="https://explorer.protokol.sh/api/guardian/groups  " path=" " %}
{% api-method-summary %}
/groups
{% endapi-method-summary %}

{% api-method-description %}
Returns all Groups
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="page" type="integer" required=false %}
The number of a page that will be returned
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="integer" required=false %}
The number of resources per page
{% endapi-method-parameter %}

{% api-method-parameter name="orderBy" type="string" required=false %}
Type by which it should order resources.  
Example: orderBy=name:asc
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=false %}
Value by which it should search for resources \(allows wildcard %\)
{% endapi-method-parameter %}

{% api-method-parameter name="priority" type="integer" required=false %}
Value by which should search for resources
{% endapi-method-parameter %}

{% api-method-parameter name="active" type="boolean" required=false %}
Value by which should search for resources
{% endapi-method-parameter %}

{% api-method-parameter name="default" type="boolean" required=false %}
Value by which should search for resources
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
    "totalCountIsEstimate": false,
    "count": 2,
    "pageCount": 1,
    "totalCount": 2,
    "next": null,
    "previous": null,
    "self": "/guardian/groups?page=1&limit=100",
    "first": "/guardian/groups?page=1&limit=100",
    "last": "/guardian/groups?page=1&limit=100"
  },
  "data": [
    {
      "name": "Test Guardian Permission Group",
      "priority": 1,
      "active": true,
      "default": false,
      "allow": [
        {
          "transactionType": 1,
          "transactionTypeGroup": 1
        }
      ],
      "deny": [
        {
          "transactionType": 2,
          "transactionTypeGroup": 1
        }
      ]
    },
    {
      "name": "Test Guardian Permission Group2",
      "priority": 1,
      "active": true,
      "default": false,
      "allow": [
        {
          "transactionType": 1,
          "transactionTypeGroup": 1
        }
      ],
      "deny": [
        {
          "transactionType": 2,
          "transactionTypeGroup": 1
        }
      ]
    }
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
curl https://explorer.protokol.sh/api/guardian/groups
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = await connection.guardianApi("groups").index();

>>> Promise<ApiResponseWithPagination<Group>>
```
{% endtab %}
{% endtabs %}

## Group By Name

{% api-method method="get" host="https://explorer.protokol.sh/api/guardian/groups/:name  " path=" " %}
{% api-method-summary %}
/groups/:name
{% endapi-method-summary %}

{% api-method-description %}
Returns Group by name
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="name" type="string" required=false %}
The name of the group
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
    "name": "Test Guardian Permission Group",
    "priority": 1,
    "active": true,
    "default": false,
    "allow": [
      {
        "transactionType": 1,
        "transactionTypeGroup": 1
      }
    ],
    "deny": [
      {
        "transactionType": 2,
        "transactionTypeGroup": 1
      }
    ]
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
  "message": "Group not found"
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
curl https://explorer.protokol.sh/api/guardian/groups/Test%20Guardian%20Permission%20Group
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = await connection.guardianApi("groups").get("VALID_GROUP_NAME");

>>> Promise<ApiResponse<Group>>
```
{% endtab %}
{% endtabs %}

## Users By Group Name

{% api-method method="get" host="https://explorer.protokol.sh/api/guardian/groups/:name/users  " path=" " %}
{% api-method-summary %}
/groups/:name/users
{% endapi-method-summary %}

{% api-method-description %}
Returns users of specific group by name
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="name" type="string" required=false %}
The name of the group
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
  "data": [
    {
      "publicKey": "03c11f2a1fc02c88cd9b8db5272cba390bdb9ce3e1d58355de1b7a24c673e06ebc",
      "groups": [
        "Test Guardian Permission Group"
      ],
      "allow": [
        {
          "transactionType": 2,
          "transactionTypeGroup": 1
        }
      ],
      "deny": []
    }
  ]
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
  "message": "Group not found"
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
curl https://explorer.protokol.sh/api/guardian/groups/Test%20group%201/users
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = await connection.guardianApi("groups").users("VALID_GROUP_NAME");

>>> Promise<ApiResponse<User>>
```
{% endtab %}
{% endtabs %}

