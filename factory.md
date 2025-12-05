# Factory.sol

The [`Factory.sol`](https://github.com/webwise-tech/giveaway-platform-blockchain/blob/main/src/Factory.sol) contract is the central management contract of Xenona. It **deploys and oversees individual giveaways**, manages LINK tokens for randomness requests, handles platform fees, and provides emergency controls.

---

## Overview

[`Factory.sol`](https://github.com/webwise-tech/giveaway-platform-blockchain/blob/main/src/Factory.sol) coordinates all Xenona giveaways. While each giveaway is a separate [`Giveaway.sol`](./giveaway.md) contract, the factory ensures:

- Authorized giveaway creation via owner signatures  
- Support for native tokens and ERC-20 prizes  
- Automated LINK allocation for Chainlink VRF  
- Lifecycle management including ending, canceling, and refunds  
- Owner-controlled token and fee management  

This guarantees secure, compliant, and fair operations across all giveaways.

---

## Main Responsibilities

- **Creating Giveaways:** Ensures unique IDs, verifies owner signatures, securely funds the prize, and emits a `NewGiveaway` event.  
- **Ending Giveaways:** Verifies readiness, allocates LINK for VRF, triggers winner selection, restricted to factory owner.  
- **Canceling Giveaways:** Refunds prizes if a giveaway cannot proceed, providing an emergency mechanism.  
- **Managing Tokens and Fees:** Transfers native or ERC-20 tokens for fees, refunds, or recovery, controlled by the factory owner.

---

## Key Components

- **Owner (_owner):** manages sensitive functions  
- **LINK Token (_linkToken):** funds Chainlink VRF requests  
- **VRF Wrapper (_vrfWrapper):** interface for randomness  
- **Giveaway Map (_giveawaysMap):** tracks all deployed giveaways  

---

## Security

- Only factory owner can create, end, or cancel giveaways  
- SafeERC20 ensures secure token transfers  
- Prizes are immediately sent to giveaway contracts  
- LINK allocation is strictly controlled for VRF requests

---

## Contract Source Code

(SOURCE CODE HERE)

[`Factory.sol`](https://github.com/webwise-tech/giveaway-platform-blockchain/blob/main/src/Factory.sol) serves as the backbone of Xenona, ensuring secure, automated, and fair deployment and management of all giveaways while maintaining centralized oversight.

