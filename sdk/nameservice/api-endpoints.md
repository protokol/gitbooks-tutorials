---
description: List of nameservice api endpoints.
---

# Api Endpoints

{% hint style="info" %}
Defualt nameservice prefix is `/api/nameservice`
{% endhint %}

## List of configurations endpoints

| Endpoints | Description | Type |
| :--- | :--- | :--- |
| /configurations | Returns configurations for nameserivce plugins | GET |

## List of nameservice endpoints

| Endpoints | Description | Type |
| :--- | :--- | :--- |
| / | Returns all nameservice transactions | GET |
| /:id | Returns specific nameservice transaction by id | GET |
| /:id/wallet | Returns wallet by its nameservice name | GET |



## GET - configurations

### Endpoint

```text
/configurations
```

### Example

```text
curl https://explorer.protokol.sh/api/nameservice/configurations
```

## GET - /

### Endpoint

```text
/
```

### Example

```text
curl https://explorer.protokol.sh/api/nameservice
```

### **Query Parameters**

| **Name** | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| page | int | The number of the page that will be returned. | No |
| limit | int | The number of resources per page. | No |
| orderBy | string | Type by which should order resources. | No |
| transform | boolean | If returns modified or raw data. | No |

## GET - /:Id

### **Endpoint**

```text
/:id
```

### Example

```text
curl https://explorer.protokol.sh/api/nameservice/aedafa0fa07e79ada72c8d676efaa9429ff04f47271bce742c6079b56872285c
```

## GET - /:id/wallet

### Endpoint

```text
/:id/wallet
```

### Example

```text
curl https://explorer.protokol.sh/api/nameservice/zan/wallet
```

