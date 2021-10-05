---
description: Showing how to setup @protokol/nft development environment.
---

# Development

### Prerequisites

* **Node version 12.x or 14.x**
* **yarn package manager**
* **docker and docker-compose**

{% hint style="info" %}
For more information about setting up development environment go to   
[https://ark.dev/docs/core/getting-started/development-setup/introduction](https://ark.dev/docs/core/getting-started/development-setup/introduction)
{% endhint %}

### To run local development enviornment execute the following steps:

#### 1. Clone nft repository

```bash
git clone https://github.com/protokol/nft.git

cd nft

yarn && yarn build
```

#### 2. Run Postgres database

```bash
cd docker/development/testnet

docker-compose up postgres
```

#### 3. Run local blockchain

_**From repository root folder:**_

```bash
yarn full:testnet
```

### Version Bumping

#### Prerelease

```bash
yarn version:beta
```

#### Patch

```bash
yarn version:patch
```

### Changelog

```bash
yarn changelog
```

