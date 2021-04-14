---
description: API Endpoints for Users
---

# Users

## List all Users Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [/users](users.md#list-all-users-endpoints) | Return all users | GET |
| [/users/:id](users.md#get-return-user-by-public-key) | Return user by a public key | GET |
| [/users/:id/groups](users.md#get-return-groups-of-user-by-public-key) | Return all groups of a user | GET |

## GET - Return All Users

### Endpoint <a id="endpoint"></a>

```text
GET /users
```

### **Query Parameters** <a id="query-parameters"></a>

| **Name** | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| page | int | The number of the page that will be returned. | No |
| limit | int | The number of resources per page. | No |
| publicKey | string | String by which should search for resources \(allows wildcard %\) | No |

### Example

```text
curl https://explorer.protokol.sh/api/guardian/users
```

### Response

```javascript
{
  "meta": {
    "totalCountIsEstimate": false,
    "count": 1,
    "pageCount": 1,
    "totalCount": 1,
    "next": null,
    "previous": null,
    "self": "/guardian/users?publicKey=032%25&page=1&limit=100",
    "first": "/guardian/users?publicKey=032%25&page=1&limit=100",
    "last": "/guardian/users?publicKey=032%25&page=1&limit=100"
  },
  "data": [
    {
      "publicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "groups": [
        "group name"
      ],
      "allow": [
        {
          "transactionType": 0,
          "transactionTypeGroup": 9002
        }
      ],
      "deny": []
    }
  ]
}
```

## GET - Return User By Public Key

### Endpoint <a id="endpoint"></a>

```text
GET /users/{id}
```

### Path Parameters <a id="path-parameters"></a>

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | Public Key of the user | Yes |

### Example

```text
curl https://explorer.protokol.sh/api/guardian/users/03c11f2a1fc02c88cd9b8db5272cba390bdb9ce3e1d58355de1b7a24c673e06ebc
```

### Response

```javascript
{
  "data": {
    "publicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
    "groups": [
      "group name"
    ],
    "permissions": [
      {
        "kind": 1,
        "types": [
          {
            "transactionType": 1,
            "transactionTypeGroup": 9002
          }
        ]
      }
    ]
  }
}
```

## GET - Return Groups of User By Public Key

### Endpoint <a id="endpoint"></a>

```text
GET /users/{id}/groups
```

### Path Parameters <a id="path-parameters"></a>

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | Public Key of the user | Yes |

### Example

```text
curl https://explorer.protokol.sh/api/guardian/users/03c11f2a1fc02c88cd9b8db5272cba390bdb9ce3e1d58355de1b7a24c673e06ebc/groups
```

### Response

```javascript
{
  "data": [
    {
      "name": "group name",
      "priority": 1,
      "active": true,
      "default": true,
      "allow": [
        {
          "transactionType": 1,
          "transactionTypeGroup": 9002
        }
      ],
      "deny": []
    }
  ]
}
```

