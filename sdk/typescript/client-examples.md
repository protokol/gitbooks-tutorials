# Client Examples

## Initialization

```typescript
import { NFTConnection } from "./nft-connection";

const connection = new NFTConnection("http://nft.protokol.com:4003/api");
```

## NFT Base Endpoints

## Collections

### List All Collections

```typescript
const response = connection.NFTBaseApi("collections").all();

>>> Promise<ApiResponseWithPagination<CollectionsResource[]>>
```

### Get Collection By Id

```typescript
const response = connection.NFTBaseApi("collections").get("VALID_ID");

>>> Promise<ApiResponse<CollectionsResource>>
```

### Get Schema By Id 

```typescript
const response = connection.NFTBaseApi("collections").getSchema("VALID_ID");

>>> Promise<ApiResponse<Schema>>
```

### Get Collections Wallet 

```typescript
const response = connection.NFTBaseApi("collections").wallet("VALID_ID");

>>> Promise<ApiResponse<CollectionsWallet>>
```

### Search Collections

```typescript
const response = connection.NFTBaseApi("collections").searchByCollections({
     jsonSchema: {
      "VALID_JSON_OBJECT"
      },
});
    
    >>> Promise<ApiResponseWithPagination<CollectionsResource[]>>
```

### Search Asset By Collection Id 

```typescript
const response = connection.NFTBaseApi("collections").assetByCollectionId("VALID_ID");

>>> Promise<ApiResponseWithPagination<CollectionsAsset[]>>
```

## Assets

### Return All Assets

```typescript
const response = connection.NFTBaseApi("assets").all();

>>> Promise<ApiResponseWithPagination<AssetsResource[]>>
```

### Return Asset By Id

```typescript
const response = connection.NFTBaseApi("assets").get("VALID_ID");

>>> Promise<ApiResponse<AssetsResource>> 
```

### Return Assets Wallet

```typescript
const response = connection.NFTBaseApi("assets").wallet("VALID_ID");

>>> Promise<ApiResponse<AssetsWallet>>
```

### Search By Asset

```typescript
const response = connection.NFTBaseApi("assets").searchByAsset({
    "VALID_JSON_OBJECT"
});

>>> Promise<ApiResponseWithPagination<AssetsResource[]>>
```

## Transfers

### Return All Transfers

```typescript
const response = connection.NFTBaseApi("transfers").all();

>>> Promise<ApiResponseWithPagination<TransfersResource[]>>
```

### Return Transfer By Id

```typescript
const response = connection.NFTBaseApi("transfers").get("VALID_ID");

>>> Promise<ApiResponse<TransfersResource>>
```

## Burns

### Return All Burns

```typescript
const response = connection.NFTBaseApi("burns").all();

>>> Promise<ApiResponseWithPagination<BurnsResource[]>>
```

### Return Burn By Id

```typescript
const response = connection.NFTBaseApi("burns").get("VALID_ID");

>>> Promise<ApiResponse<BurnsResource>> 
```

## Configurations

### Return Base Configurations

```typescript
const response = connection.NFTBaseApi("configurations").index();

>>> Promise<ApiResponse<ConfigurationsResource>>
```



