---
description: API Endpoints for Groups
---

# Groups

## List all Groups Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [/groups](groups.md#get-return-all-groups) | Retrun all groups | GET |
| [/groups/:id](groups.md#get-return-group-by-name) | Retrun group by name | GET |
| [/groups/:id/users](groups.md#get-return-all-users-of-group) | Return all users of group with wanted name | GET |



## GET - Return All Groups

### Endpoint <a id="endpoint"></a>

```text
GET /groups
```

### **Query Parameters** <a id="query-parameters"></a>

| **Name** | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| page | int | The number of the page that will be returned. | No |
| limit | int | The number of resources per page. | No |
| orderBy | string | Type by which should order resources. | No |

### Example

```text
curl http://nft.protokol.com:4003/api/guardian/groups
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
    "self": "/guardian/groups?page=1&limit=100",
    "first": "/guardian/groups?page=1&limit=100",
    "last": "/guardian/groups?page=1&limit=100"
  },
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

## GET - Return Group by Name

### Endpoint <a id="endpoint"></a>

```text
GET /groups/{id}
```

### Path Parameters <a id="path-parameters"></a>

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The name of the group | Yes |

### Example

```text
curl http://nft.protokol.com:4003/api/guardian/groups/group%20name
```

### Response

```javascript
{
  "data": {
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
}
```

## GET - Return All Users Of Group

### Endpoint <a id="endpoint"></a>

```text
GET /groups/{id}/users
```

### Path Parameters <a id="path-parameters"></a>

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| id | string | The name of the group | Yes |

### Example

```text
curl http://nft.protokol.com:4003/api/guardian/groups/group%20name/users
```

### Response

```javascript
{
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
