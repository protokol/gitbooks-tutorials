---
description: API Endpoints for Groups
---

# Groups

## List all Groups Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [/groups](groups.md#get-return-all-groups) | Return all groups | GET |
| [/groups/:id](groups.md#get-return-group-by-name) | Return group by name | GET |
| [/groups/:id/users](groups.md#get-return-all-users-of-group) | Return all users of a group with wanted name | GET |



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
| name | string | String by which should search for resources \(allows wildcard %\) | No |
| priority | int | The number by which should search for resources | No |
| active | boolean | Value by which should search for resources | No |
| default | boolean | Value by which should search for resources | No |

### Example

```text
curl https://api.protokol.com/api/guardian/groups
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
    "self": "/guardian/groups?orderBy=name%3Adesc&name=def%25&page=1&limit=100",
    "first": "/guardian/groups?orderBy=name%3Adesc&name=def%25&page=1&limit=100",
    "last": "/guardian/groups?orderBy=name%3Adesc&name=def%25&page=1&limit=100"
  },
  "data": [
    {
      "name": "Default Transfer Group",
      "priority": 1,
      "active": true,
      "default": true,
      "allow": [
        {
          "transactionType": 1,
          "transactionTypeGroup": 1
        }
      ],
      "deny": []
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
curl https://api.protokol.com/api/guardian/groups/Test%20Guardian%20Permission%20Group
```

### Response

```javascript
{
  "data": {
    "name": "Test Guardian Permission Group",
    "priority": 1,
    "active": true,
    "default": true,
    "allow": [
      {
        "transactionType": 1,
        "transactionTypeGroup": 1
      }
    ],
    "deny": []
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
curl https://api.protokol.com/api/guardian/groups/Test%20group%201/users
```

### Response

```javascript
{
  "data": [
    {
      "publicKey": "03287bfebba4c7881a0509717e71b34b63f31e40021c321f89ae04f84be6d6ac37",
      "groups": [
        "Test group 1"
      ],
      "allow": [
        {
          "transactionType": 1,
          "transactionTypeGroup": 1
        }
      ],
      "deny": []
    }
  ]
}
```



