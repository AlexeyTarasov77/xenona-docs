# What is a Smart Contract?

A smart contract is a single digital agreement stored on a blockchain that automatically executes when its predefined terms and conditions are met. It operates without intermediaries, ensuring participants can trust the outcome immediately.

Smart contracts are used to automate specific workflows, triggering the next action once the conditions encoded in the contract are satisfied. This can include transferring funds, granting access, or updating records, all executed securely on-chain.

## How a Smart Contract Works

A smart contract functions like an “if/when…then…” program written into blockchain code. When the predetermined conditions are met and verified by the network, the contract executes the defined actions automatically.

The blockchain records all transactions, making them immutable and transparent. Only authorized parties can view relevant data, and the contract enforces the rules exactly as written, eliminating ambiguity or manual intervention.

A single smart contract can contain all necessary stipulations to ensure the task is completed correctly. Participants define how data and actions are represented on-chain, agree on rules for execution, consider exceptions, and outline dispute resolution mechanisms. Developers then encode these rules into the contract, often using templates or web tools to simplify deployment and usage.

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
