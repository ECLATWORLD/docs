---
description: >-
  Eclat native bridge is used to relay the Eclat native token between Eclat and
  Ethereum networks
---

# Eclat: Ethereum ↔ Eclat

Eclat native bridge between Ethereum and Eclat is used to relay the Eclat native token from Eclat to Ethereum network

## Architecture Overview

The Eclat bridged is based on POA's bridge implementation, it is used to transfer Eclat tokens between the Eclat chain and the Ethereum network.

Tokens sent to the respective bridge contract on one network \(whether it's Eclat or Ethereum\) are "locked" in the bridge, "unlocked" on the other network bridge and transferred to the sender. The bridge contracts are deployed on both networks, and bridge oracle processes run on each validators machine as part of the validator deployment stack.

Besides the transfer of Eclat tokens between the two networks, the bridge is also responsible for network core functionality events of relaying the block rewards to the Ethereum network:

**Mint block reward distributed on the Eclat chain on Ethereum**

Each cycle the total block reward distributed on Eclat chain is minted on Ethereum and locked on the bridge contract.

This works by listening to the \`RewardedOnCycle\` event emitted by the BlockReward contract on Eclat chain, waiting for all bridge validators on Eclat chain to sign it, and eventually sending a transaction to mint on Ethereum \(by the last signing validator\).

## Contracts

Home side of the bridge on the Eclat network: [0xd617774b9708F79187Dc7F03D3Bdce0a623F6988](https://eclatscan.com/address/0xd617774b9708F79187Dc7F03D3Bdce0a623F6988/transactions)

Foreign side of the bridge on the Ethereum network: [0xcFEECa15E01323Efb82143C1Fa11B9925EfbF506](https://eclatscan.com/address/0xcFEECa15E01323Efb82143C1Fa11B9925EfbF506/transactions)

Eclat token on the Ethereum network: [0x970B9bB2C0444F5E81e9d0eFb84C8ccdcdcAf84d](https://etherscan.io/token/0x970b9bb2c0444f5e81e9d0efb84c8ccdcdcaf84d)

## Source Code

{% embed url="https://github.com/fuseio/fuse-bridge/tree/master/native-to-erc20/contracts" %}

## How to use

On Eclat you send native Eclat token to the home bridge contract. Then you receive an equal amount of the Eclat token on the Ethereum network, sent from the foreign bridge contract

On Ethereum network you transfer the Eclat token to the foreign bridge contract. After a couple of confirmations, you will receive equal amount of the Eclat native token, sent from the home bridge contract.

#### 

