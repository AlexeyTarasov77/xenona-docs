# Giveaway.sol

The `Giveaway.sol` contract represents a single giveaway on the Xenona platform. Each giveaway is deployed as an independent smart contract, ensuring transparency, fairness, and autonomous execution. The contract handles participant registration, enforces entry rules, manages prize distribution, and integrates with Chainlink VRF for verifiable random winner selection.

---

## Overview

`Giveaway.sol` is designed to operate independently once deployed. It supports:

- Native token or ERC-20 prizes  
- Configurable participant limits and duration  
- Signature-based entry authorization  
- Automatic winner selection via Chainlink VRF  
- 1% platform fee for Xenona  
- Emergency cancellation and refunds  

This design guarantees trustless execution and ensures the prize is securely managed throughout the giveaway lifecycle.

---

## Participation Logic

- **Entering the Giveaway:** Participants must provide a signature from the factory owner. Once verified, the participant is added to the contract and an event is emitted.
This approach prevents unauthorized entering attempts

---

## Ending and Completing Giveaways

The contract manages three main end scenarios:

1. **Cancellation:** If minimum participants are not met, the giveaway is automatically canceled and prizes refunded.  
2. **Single Participant:** If only one participant joins, the contract completes immediately and awards the prize.  
3. **Multiple Participants:** Requests randomness from Chainlink VRF to select a winner fairly.

After a winner is determined:

- 1% of the prize is sent to the Factory as a platform fee  
- 99% is sent to the winner  
- Any remaining LINK tokens are refunded to the Factory  
- Status is updated to `COMPLETED` and an event is emitted

---

## Cancellation

- The factory can cancel a giveaway at any time before completion  
- Refunds the prize to the creator and any remaining LINK to the factory  
- Updates the giveaway status to `CANCELED`  

This ensures that problematic or stalled giveaways can be resolved safely.

---

## Security and Fairness

- Participant entries are verified via signature from the factory owner  
- All state changes are managed on-chain, preventing manipulation  
- Winner selection is provably fair through Chainlink VRF  
- Prize distribution and platform fees are automatically enforced  

---

`Giveaway.sol` ensures that each giveaway runs autonomously, fairly, and securely from start to finish, providing trustless participation and verifiable outcomes for all users.

