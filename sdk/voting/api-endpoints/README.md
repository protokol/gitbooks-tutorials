---
description: List of Voting API Endpoints.
---

# API Endpoints

{% hint style="info" %}
Default Voting API prefix is `/api/voting`
{% endhint %}

## List Of Configurations Endpoints

| Endpoints | Description | Type |
| :--- | :--- | :--- |
| [/configurations](configurations.md#configurations-1) | Returns configurations for voting plugins | GET |

## List Of Create Proposal Endpoints

| Endpoints | Description | Type |
| :--- | :--- | :--- |
| /create/proposal/transactions | Returns all create proposal transactions | GET |
| /create/proposal/transactions/:id | Returns create proposal transaction by id | GET |
| /create/proposal/:id/wallet | Returns wallet by create proposal id | GET |

## List Of Cast Vote Endpoints

| Endpoints | Description | Type |
| :--- | :--- | :--- |
| /cast/vote/transactions | Returns all cast vote transactions | GET |
| /cast/vote/transactions/:id | Returns cast vote transaction by id | GET |
| /cast/vote/:id/wallet | Returns wallet by cast vote id | GET |

## List Of Statistics Endpoints

| Endpoints | Description | Type |
| :--- | :--- | :--- |
| /statistics/:id | Returns statistics for proposal by id | GET |

