---
description: A Light Typescript Client Supporting NFT and Public ARK REST API
---

# Guardian Client

## Prerequisites <a id="prerequisites"></a>

Before we get started we need to make sure that all of the required dependencies are installed.

### [yarn](https://classic.yarnpkg.com/lang/en/)

```text
yarn add @protokol/client
```

## Initialization

```typescript
import { GuardianConnection } from "./guardian-connection";

const connection = new GuardianConnection("http://nft.protokol.com:4003/api");
```

## Guardian Endpoints

## Configurations

### List Configurations

```typescript
const response = await connection.guardianApi("configurations").index();

>>> Promise<ApiResponse<GuardianConfigurations>>
```

## Groups

### List All Groups

```typescript
const response = await connection.guardianApi("groups").index();

>>> Promise<ApiResponseWithPagination<Group>>
```

### Get Group By Name

```typescript
const response = await connection.guardianApi("groups").get("VALID_GROUP_NAME");

>>> Promise<ApiResponse<Group>>
```

### Get Users By Group Name

```typescript
const response = await connection.guardianApi("groups").users("VALID_GROUP_NAME");

>>> Promise<ApiResponse<User>>
```

## Users

### List All Users

```typescript
const response = await connection.guardianApi("users").index();

>>> Promise<ApiResponseWithPagination<User>>
```

### Get User By Public Key

```typescript
const response = await connection.guardianApi("users").get("PUBLIC_KEY");

>>> Promise<ApiResponse<User>>
```

### Get User Groups 

```typescript
const response = await connection.guardianApi("users").userGroups("PUBLIC_KEY");

>>> Promise<ApiResponse<UserGroups>>
```







