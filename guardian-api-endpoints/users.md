---
description: API Endpoints for Users
---

# Users

## List all Users Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [/users](users.md#list-all-users-endpoints) | Retrun all users | GET |
| [/users/:id](users.md#get-return-user-by-public-key) | Retrun user by public key | GET |
| [/users/:id/groups](users.md#get-return-groups-of-user-by-public-key) | Return all groups of user | GET |

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

### Example

```text
curl http://nft.protokol.com:4003/api/guardian/users
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
    "self": "/guardian/users?page=1&limit=100",
    "first": "/guardian/users?page=1&limit=100",
    "last": "/guardian/users?page=1&limit=100"
  },
  "data": [
    {
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
curl http://nft.protokol.com:4003/api/guardian/users/03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37
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
curl http://nft.protokol.com:4003/api/guardian/users/03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37/groups
```

### Response

```javascript
{
  "data": [
    {
      "name": "group name",
      "priority": 1,
      "active": false,
      "default": false,
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
  ]
}
```

