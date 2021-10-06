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
| ​/assets​ | ReturnS all assets | GET |
| ​/assets/:id​ | Returns asset by id | GET |
| ​/assets/:id/wallets​ | Returns the wallet owning an asset | GET |
| ​/assets/wallet/:id​ | Returns the assets that wallet owns | GET |
| ​/assets/search​ | Search assets | POST |
| /assets/claim | Claims an asset | POST |

### List of Burn Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| ​/burns​ | Returns all burns | GET |
| ​/burns/:id​ | Returns burn by id | GET |

### List of Collection Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| ​/collections​ | Returns all collections | GET |
| ​/collections/:id​ | Returns collection by id | GET |
| ​/collections/:id/schema​ | Returns the schema of a collection | GET |
| ​/collections/:id/wallets​ | Returns the wallet owning a collection | GET |
| ​/collections/search​ | Search collections | POST |
| ​/collections/:id/assets​ | Returns the assets of a collection | GET |

### List of **Configuration** Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| ​/configurations​ | Returns all configurations | GET |

### List of Transfer Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| ​/transfers​ | Returns all transfers | GET |
| ​/transfers/:id​ | Returns transfer by id | GET |

## NFT Exchange API Endpoints

{% hint style="info" %}
Default prefix for NFT Exchange is `/api/nft/exchange`
{% endhint %}

### List of Auction Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| ​/auctions​ | Returns all active auctions | GET |
| ​/auctions/:id​ | Returns auction by id | GET |
| ​/auctions/:id/wallets​ | Returns the wallet owning an auction | GET |
| ​/auctions/search​ | Search auctions | POST |
| ​/auctions/canceled​ | Returns all canceled auctions | GET |
| ​/auctions/canceled/:id​ | Returns canceled auction by :id | GET |

### List of Bid Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| ​/bids​ | Returns all bids | GET |
| ​/bids/:id​ | Returns bid by id | GET |
| ​/bids/:id/wallets​ | Returns the wallet owning a bid | GET |
| ​/bids/search​ | Search bids | POST |
| ​/bids/canceled​ | Returns all canceled bids | GET |
| ​/bids/canceled/:id​ | Returns canceled bids by id | GET |

### List of **Configuration** Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| ​/configurations​ | Returns all configurations | GET |

### List of Trade Endpoints

| Endpoint | Description | Type |
| :--- | :--- | :--- |
| ​/trades​ | Returns all trades | GET |
| ​/trades/:id​ | Returns trade by id | GET |
| ​/trades/search​ | Search trades | POST |

