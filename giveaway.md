# Giveaway.sol

The [`Giveaway.sol`](https://github.com/webwise-tech/giveaway-platform-blockchain/blob/main/src/Giveaway.sol) contract represents a single giveaway on Xenona. Each giveaway runs independently, handling participant entries, enforcing rules, managing prizes, and using Chainlink VRF for verifiable random winner selection.

---

## Overview

[`Giveaway.sol`](https://github.com/webwise-tech/giveaway-platform-blockchain/blob/main/src/Giveaway.sol) supports:

- Native or ERC-20 prizes  
- Configurable participant limits and duration  
- Signature-based entry verification  
- Automatic winner selection via Chainlink VRF  
- 1% platform fee for Xenona  
- Emergency cancellation and refunds  

This ensures trustless, transparent, and secure execution throughout the giveaway lifecycle.

---

## Participation & Completion

Participants enter via factory-authorized signatures. The contract handles:

- **Cancellation:** if minimum participants are not met  
- **Single participant:** completes immediately  
- **Multiple participants:** requests randomness for winner selection  

Upon completion:

- 1% fee goes to the Factory, 99% to the winner  
- Remaining LINK is refunded to the Factory  
- Status updates and events are emitted  

---

## Security & Fairness

- Signature-verified entries  
- Fully on-chain state management  
- Provably fair winner selection  
- Automatic prize and fee distribution  

---

## Contract Source Code

(SOURCE CODE HERE)

`Giveaway.sol` guarantees each giveaway runs autonomously, fairly, and securely, providing verifiable outcomes and trustless participation for all users.

