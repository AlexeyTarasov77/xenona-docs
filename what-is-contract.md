# What are smart contracts?

Smart contracts are digital contracts stored on a blockchain that are automatically executed when predetermined terms and conditions are met.

Smart contracts are typically used to automate the execution of an agreement so that all participants can be immediately certain of the outcome, without any intermediary’s involvement or time loss. They can also automate a workflow, triggering the next action when predetermined conditions are met.

## How smart contracts work

Smart contracts work by the following simple “if/when…then…” statements that are written into code on a blockchain. A network of computers executes the actions when predetermined conditions are met and verified.

These actions might include releasing funds to the appropriate parties, registering a vehicle, sending notifications or issuing a ticket. The blockchain is then updated when the transaction is completed. That means the transaction cannot be changed, and only parties who have been granted permission can see the results.

Within a smart contract, there can be as many stipulations as needed to satisfy the participants that the task is completed satisfactorily. To establish the terms, participants must determine how transactions and their data are represented on the blockchain, agree on the “if/when...then…” rules that govern those transactions, explore all possible exceptions and define a framework for resolving disputes.

Then, a developer programs the smart contract. However, organizations that use blockchain for business increasingly provide templates, web interfaces and other online tools to simplify structuring smart contracts.

## How Xenona Uses Smart Contracts

- Every giveaway created on Xenona is deployed as its own smart contract, ensuring it operates independently and transparently.  
- Prizes are securely locked in the contract until the giveaway concludes.  
- Entry rules and eligibility checks are enforced automatically, removing the need for manual verification.  
- When the giveaway ends, the contract requests a verifiable random number (via Chainlink VRF) to select winners fairly.  
- Finally, the contract distributes the prize according to the rules and records the outcome on-chain for full transparency.

[Xenona uses **two primary smart contracts:**](https://github.com/webwise-tech/giveaway-platform-blockchain)

- [**Giveaway.sol**](./giveaway.md) — manages each individual giveaway, including prize locking, entry tracking, and winner selection.  
- [**Factory.sol**](./factory.md) — responsible for deploying new giveaways, managing fees, and coordinating necessary resources such as LINK tokens for randomness.

Together, these contracts automate the entire giveaway lifecycle, from creation to prize distribution, while guaranteeing fairness, security, and trustless operation.
