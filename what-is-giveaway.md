# What is a Giveaway

A giveaway on Xenona is a fully automated, blockchain-based event where participants can compete for prizes under predefined rules. Each giveaway is represented by a dedicated smart contract, which ensures security, transparency, and fairness for all participants.

Giveaways operate autonomously from start to finish: the prize is locked in the contract, entries are validated on-chain, and the winner is selected using verifiable randomness. This eliminates any need for manual intervention and prevents tampering or manipulation.

## Key Features

- **Automated Execution:** All aspects of the giveaway — from entry validation to prize distribution — are handled by the smart contract.  
- **Verifiable Randomness:** Winners are selected through Chainlink VRF, ensuring trustless and provably fair outcomes.  
- **Secure Prize Handling:** Prizes are locked in the smart contract and automatically transferred to the winner after a small 1% platform fee is deducted.  

In essence, a Xenona giveaway is a trustless, fair, and fully transparent mechanism for distributing prizes, giving both creators and participants confidence in the integrity of every event.

---

## Lifecycle

### 1. Giveaway Creation

The lifecycle begins when a creator sets up a new giveaway through the **Create Giveaway** flow. At this stage:

- The prize is deposited into the giveaway smart contract  
- Entry rules, duration, and participant limits are defined  
- Optional metadata like title and description is added  

Once deployed, the giveaway contract becomes autonomous: all entries, validations, and state changes are managed on-chain.

---

## 2. Giveaway Activation

Immediately after deployment, the giveaway becomes active. Participants can now view it and, if they meet the requirements, enter. The smart contract ensures:

- The prize remains securely locked  
- Participant data is recorded transparently on-chain

This prevents tampering or unfair manipulation by the creator or any third party.

---

### 3. Participation Period

During the active period:

- Users join the giveaway by submitting their entries on-chain  
- All rules and restrictions are checked automatically (password, wallet balance, address age, transaction history, etc.) on server

The participation window ends either when the **maximum number of participants** is reached or when the **duration expires**, whichever comes first.

---

### 4. Ending the Giveaway

Once the participation period is over:

- Giveaway end transaction is submitted on-chain by application backend on behalf of the factory
- Ending the giveaway initiates the winner selection process and giveawan becomes pending

---

### 5. Winner Selection

The giveaway contract requests a **verifiable random number** from [Chainlink VRF](https://docs.chain.link/vrf):

- This randomness is used to pick the winner in a fully deterministic and verifiable way  
- No one — not even the creator — can influence the outcome  

This ensures **fairness** and **trustless selection** for all participants.

---

### 6. Prize Distribution

After a winner is selected:

- A **fixed 1% fee** is deducted from the prize and sent to the Factory  
- The remaining prize is automatically transferred to the winning participant’s wallet  
- The giveaway contract’s state is updated to mark it as completed  

The lifecycle is now complete — the giveaway has run autonomously from start to finish.

---

### 7. Post-Giveaway

Even after completion:

- All entries, rules, and winner data remain publicly visible and verifiable on-chain  
- Users and creators can reference the history for transparency or reporting purposes  
- There is no possibility of retroactive changes to the outcome or prize  
- You can view the history of your giveaways creations, entries and winning from profile page

This on-chain lifecycle guarantees **trust, fairness, and complete transparency** for every Xenona giveaway.

