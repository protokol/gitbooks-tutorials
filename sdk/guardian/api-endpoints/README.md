---
description: List of Guardian API Endpoints
---

# API Endpoints

{% hint style="info" %}
Default nameservice prefix is `/api/guardian`
{% endhint %}

## List Of Configurations Endpoints

| Endpoints | Description | Type |
| :--- | :--- | :--- |
| [/configurations](../../nameservice/api-endpoints/configurations.md) | Returns configurations for Guardian plugins | GET |

## List Of Groups Endpoints

| Endpoints | Description | Type |
| :--- | :--- | :--- |
| [/groups](groups.md#groups-1) | Returns all Groups | GET |
| [/groups/:name](groups.md#groups-name) | Returns Group by its name | GET |
| [/groups/:name/users](groups.md#users-by-group-name) | Returns Users of a Group by name | GET |

## List Of Users Endpoints

| Endpoints | Description | Type |
| :--- | :--- | :--- |
| [/users](users.md#users-1) | Returns all Users | GET |
| [/users/:id](users.md#users-id) | Returns User by Publickey | GET |
| [/users/:id/groups](users.md#users-id-groups) | Returns All Groups of User by Publickey | GET |



## Guardian Client

{% hint style="info" %}
A Light Typescript Client Supporting Guardian REST API
{% endhint %}

### Installation

#### [yarn](https://classic.yarnpkg.com/lang/en/)

```text
yarn add @protokol/client
```

#### [pnpm](https://pnpm.js.org/)

```text
pnpm add @protokol/client
```

#### [npm](https://www.npmjs.com/)

```text
npm install @protokol/client
```



### Initialization

```typescript
import { ProtokolConnection } from "@protokol/client";

const connection = new ProtokolConnection("https://explorer.protokol.sh/api");
```

## 





