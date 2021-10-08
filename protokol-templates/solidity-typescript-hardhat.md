---
description: >-
  A BoilerPlate Template Project To Start Solidity Development With Hardhat and
  Typescript
---

# Solidity Typescript Hardhat

It can be found on the following link

{% embed url="https://github.com/protokol/solidity-typescript-hardhat-template" %}

## Hardhat Configuration

* typescript support enabled
* typechain plugin installed \(typescript type bindings are generated from smart contracts\)/check Typechain docs
* hardhat-deploy plugin enabled \(use deployments from `deploy` folder, order and tag them; multi-network\)
* hardhat console enabled - to allow console.log usage within solidity code
* testing environment configured and operational

Check the Hardhat documentation for more information.

{% embed url="https://hardhat.org/getting-started/" %}

We recommend installing `hh autocomplete` so you can use `hh` shorthand globally.

`npm i -g hardhat-shorthand`

{% embed url="https://hardhat.org/guides/shorthand.html" %}

## Usage

Run `npm install` and then:

* `hh compile` - to compile smart contract and generate typechain ts bindings
* `hh test` - to run tests
* `hh deploy` - to deploy to local network \(see options for more\)
* `hh TABTAB` - to use autocomplete
* `hh node` - to run a localhost node

Check `package.json` scripts for more options. Use `.env.example` file and adapt it to you values and settings.

