---
description: Guardian Users Endpoints
---

# Users

## Users

{% api-method method="get" host="https://explorer.protokol.sh/api/guardian/users  " path=" " %}
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

{% api-method-parameter name="publickey" type="string" required=false %}
Value by which it searches for resources \(allows wildcard %\)
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
curl https://explorer.protokol.sh/api/guardian/users
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = await connection.guardianApi("users").index();

>>> Promise<ApiResponseWithPagination<User>>
```
{% endtab %}
{% endtabs %}

## User By Publickey

{% api-method method="get" host="https://explorer.protokol.sh/api/guardian/users/:id " path=" " %}
{% api-method-summary %}
/users/:id
{% endapi-method-summary %}

{% api-method-description %}
Returns User by publickey
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
  "message": "User not found"
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
  "message": "\"id\" length must be 66 characters long"
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
curl https://explorer.protokol.sh/api/guardian/users/03c11f2a1fc02c88cd9b8db5272cba390bdb9ce3e1d58355de1b7a24c673e06ebc
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = await connection.guardianApi("users").get("PUBLIC_KEY");

>>> Promise<ApiResponse<User>>
```
{% endtab %}
{% endtabs %}

## User Groups

{% api-method method="get" host="https://explorer.protokol.sh/api/guardian/users/:id/groups  " path=" " %}
{% api-method-summary %}
/users/:id/groups
{% endapi-method-summary %}

{% api-method-description %}
Returns groups of specific user by publickey
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
  "message": "User not found"
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
  "message": "\"id\" length must be 66 characters long"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="Curl" %}
```text
curl https://explorer.protokol.sh/api/guardian/users/03c11f2a1fc02c88cd9b8db5272cba390bdb9ce3e1d58355de1b7a24c673e06ebc/groups
```
{% endtab %}

{% tab title="Typescript" %}
```typescript
const response = await connection.guardianApi("users").userGroups("PUBLIC_KEY");

>>> Promise<ApiResponse<UserGroups>>
```
{% endtab %}
{% endtabs %}

