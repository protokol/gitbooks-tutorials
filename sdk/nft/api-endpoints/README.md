---
description: List of NFT API Endpoints For NFT-Base and NFT-Exchange
---

# API Endpoints

## NFT Base API Endpoints

{% hint style="info" %}
Default prefix for NFT Base is `/api/nft`
{% endhint %}

### List of Assets Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [​/assets​](assets.md#all-assets) | Returns all assets | GET |
| [​/assets/:id​](assets.md#asset-by-id) | Returns asset by id | GET |
| [​/assets/:id/wallets​](assets.md#wallet-owning-asset) | Returns the wallet owning an asset | GET |
| [​/assets/wallet/:id​](assets.md#wallet-assets) | Returns the assets that wallet owns | GET |
| [​/assets/search​](assets.md#search-by-asset) | Search assets | POST |
| /assets/claim | Claims an asset | POST |

### List of Burn Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [​/burns​](burns.md#all-burns) | Returns all burns | GET |
| [​/burns/:id​](burns.md#burn-by-id) | Returns burn by id | GET |

### List of Collection Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [​/collections​](collections.md#all-collections) | Returns all collections | GET |
| [​/collections/:id​](collections.md#collection-by-id) | Returns collection by id | GET |
| [​/collections/:id/schema​](collections.md#collection-schema) | Returns the schema of a collection | GET |
| [​/collections/:id/wallets​](collections.md#collections-wallet) | Returns the wallet owning a collection | GET |
| [​/collections/search​](collections.md#search-collection) | Search collections | POST |
| [​/collections/:id/assets​](collections.md#collection-assets) | Returns the assets of a collection | GET |

### List of **Configuration** Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [​/configurations​](base-configurations.md#configurations) | Returns all configurations | GET |

### List of Transfer Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [​/transfers​](transfers.md#all-transfers) | Returns all transfers | GET |
| [​/transfers/:id​](transfers.md#transfer-by-id) | Returns transfer by id | GET |

## NFT Exchange API Endpoints

{% hint style="info" %}
Default prefix for NFT Exchange is `/api/nft/exchange`
{% endhint %}

### List of Auction Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [​/auctions​](auctions.md#all-auctions) | Returns all active auctions | GET |
| [​/auctions/:id​](auctions.md#auction-by-id) | Returns auction by id | GET |
| [​/auctions/:id/wallets​](auctions.md#auctions-wallet) | Returns the wallet owning an auction | GET |
| [​/auctions/search​](auctions.md#search-auctions) | Search auctions | POST |
| [​/auctions/canceled​](auctions.md#canceled-auctions) | Returns all canceled auctions | GET |
| [​/auctions/canceled/:id​](auctions.md#canceled-auctions-by-id) | Returns canceled auction by :id | GET |

### List of Bid Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [​/bids​](bids.md#all-bids) | Returns all bids | GET |
| [​/bids/:id​](bids.md#bids-by-id) | Returns bid by id | GET |
| [​/bids/:id/wallets​](bids.md#bids-wallet) | Returns the wallet owning a bid | GET |
| [​/bids/search​](bids.md#search-bids) | Search bids | POST |
| [​/bids/canceled​](bids.md#canceled-bids) | Returns all canceled bids | GET |
| [​/bids/canceled/:id​](bids.md#canceled-bids-by-id) | Returns canceled bids by id | GET |

### List of **Configuration** Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [​/configurations​](exchange-configurations.md#configurations) | Returns all configurations | GET |

### List of Trade Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| [​/trades​](trades.md#all-trades) | Returns all trades | GET |
| [​/trades/:id​](trades.md#trade-by-id) | Returns trade by id | GET |
| [​/trades/search​](trades.md#search-trades) | Search trades | POST |

## NFT Client

{% hint style="info" %}
A Light Typescript Client Supporting NFT REST API
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

