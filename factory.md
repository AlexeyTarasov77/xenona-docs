# Factory.sol

The [`Factory.sol`](https://github.com/webwise-tech/giveaway-platform-blockchain/blob/main/src/Factory.sol) contract is the core administrative smart contract of the Xenona platform. Its primary role is to **deploy and manage individual giveaway contracts**, while handling platform-level operations such as LINK token allocation for randomness requests, fee collection, and emergency management.

---

## Overview

[`Factory.sol`](https://github.com/webwise-tech/giveaway-platform-blockchain/blob/main/src/Factory.sol) acts as the central manager for all giveaways on Xenona. Each giveaway created through the platform is a separate [`Giveaway.sol`](./giveaway.md) contract, but the factory coordinates deployment, prize funding, and lifecycle operations. Key features include:

- Signature-authorized giveaway creation to prevent unauthorized deployments  
- Support for both native tokens and ERC-20 prizes  
- Automated calculation and distribution of LINK tokens for Chainlink VRF randomness  
- Centralized management of giveaway lifecycle operations (ending, cancelling, refunds)  
- Owner-controlled mechanisms for token recovery or platform fee withdrawal

The contract maintains ownership privileges, meaning only the factory owner can perform sensitive operations like ending or canceling giveaways.

---

## Main Responsibilities

### 1. Creating Giveaways

The [`createGiveaway`](https://github.com/webwise-tech/giveaway-platform-blockchain/blob/6432f36af2e4bde4342ca19b27aeb1a2f185824b/src/Factory.sol#L107) function is used to deploy a new giveaway contract:

- Ensures **uniqueness** of the giveaway using a unique `giveawayId`  
- Requires a **signature from the factory owner** to authorize the deployment  
- Supports both **native token** prizes (ETH, BNB, MATIC, etc.) and **ERC-20 tokens**  
- Transfers the prize securely to the newly deployed giveaway contract  
- Emits a `NewGiveaway` event for off-chain tracking and frontend updates

This function guarantees that each giveaway is properly funded and fully compliant with platform rules before becoming active.

---

### 2. Ending Giveaways

The factory provides an [`endGiveaway`](https://github.com/webwise-tech/giveaway-platform-blockchain/blob/6432f36af2e4bde4342ca19b27aeb1a2f185824b/src/Factory.sol#L190) function to finalize giveaways:

- Verifies that the giveaway is **ready to end** (duration expired or participant limit reached)  
- Calculates required **LINK tokens** for Chainlink VRF randomness requests  
- Transfers LINK to the giveaway contract and triggers the winner selection  
- Restricted to the **factory owner** to ensure controlled execution of VRF operations

This automation ensures winners are chosen fairly and payouts occur correctly.

---

### 3. Canceling Giveaways

The [`cancelGiveaway`](https://github.com/webwise-tech/giveaway-platform-blockchain/blob/6432f36af2e4bde4342ca19b27aeb1a2f185824b/src/Factory.sol#L219) function allows the factory owner to cancel problematic or stalled giveaways:

- Refunds the prize to the original creator  
- Only available before the giveaway has ended  
- Serves as an **emergency mechanism** to protect both participants and creators

---

### 4. Managing Tokens and Fees

The factory can transfer tokens via the [`transfer`](https://github.com/webwise-tech/giveaway-platform-blockchain/blob/6432f36af2e4bde4342ca19b27aeb1a2f185824b/src/Factory.sol#L236) function:

- Supports **native tokens** and **ERC-20 tokens**  
- Can withdraw platform fees, recover excess LINK, or handle mistakenly sent tokens  
- Restricted to **factory owner**, ensuring security and proper governance

---

## Key Components

- **Owner (_owner):** administrative address controlling sensitive functions  
- **LINK Token (_linkToken):** used to pay Chainlink VRF for verifiable randomness  
- **VRF Wrapper (_vrfWrapper):** interface for randomness requests to Chainlink VRF  
- **Giveaway Map (_giveawaysMap):** tracks all created giveaways to prevent duplicate IDs

---

## Events

- [`NewGiveaway(uint64 giveawayId, address giveawayAddress, uint256 endTime)`](https://github.com/webwise-tech/giveaway-platform-blockchain/blob/6432f36af2e4bde4342ca19b27aeb1a2f185824b/src/Factory.sol#L47): emitted when a giveaway is successfully deployed

---

## Security Considerations

- Only the factory owner can create, end, or cancel giveaways  
- ERC-20 transfers use SafeERC20 to prevent transfer failures  
- Prize assets are transferred directly to each giveaway contract, never held long-term in the factory  
- LINK token allocation is strictly managed to ensure VRF requests are always funded

---

[`Factory.sol`](https://github.com/webwise-tech/giveaway-platform-blockchain/blob/main/src/Factory.sol) acts as the backbone of Xenona, automating the deployment, lifecycle management, and security of every giveaway while maintaining centralized oversight through owner privileges.

