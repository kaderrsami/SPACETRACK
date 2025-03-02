# Homework 4: NFTs for Space

This repository contains the complete implementation of a blockchain-based supply chain solution for aerospace components. The project is built using Solidity and leverages OpenZeppelin’s audited libraries to implement an ERC‑20 token (SPACETRACK Token) for incentives and governance and an ERC‑721 token (CDTNFT) for digital twins representing aerospace components. The white paper detailing the theoretical framework, market research, tokenomics, and technical specifications is included in this repository.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Architecture and Design](#architecture-and-design)
- [Contracts](#contracts)
  - [SPACETRACK Token (ERC-20)](#spacetrack-token-erc-20)
  - [CDTNFT (ERC-721)](#cdtnft-erc-721)
- [Installation and Deployment](#installation-and-deployment)
- [Testing and Use-Case Walkthrough](#testing-and-use-case-walkthrough)
- [White Paper](#white-paper)
- [License](#license)

---

## Project Overview

This project demonstrates a blockchain solution for managing the aerospace supply chain. It provides a secure and transparent method to track the lifecycle of aerospace components using digital twins (NFTs) while incentivizing network participants with a utility token. The design is informed by real-world implementations in the aerospace and logistics industries, and it implements all functions described in the white paper.

---

## Features

- **Digital Twin Representation:** Each aerospace component is represented as an NFT (CDTNFT), capturing its manufacturing, testing, and transfer history.
- **Incentive and Governance Token:** The SPACETRACK token (ERC‑20) is used to reward participants and facilitate on-chain governance.
- **Role-Based Access Control:** Critical functions such as minting, metadata updates, and burning are restricted to authorized roles.
- **Pausable Contract Functionality:** Emergency stops can be activated to secure token transfers.
- **Event Logging:** All significant actions (minting, transferring, updating metadata, burning) are logged for on-chain traceability.
- **Deployment on Sepolia:** The contracts are designed for deployment on the Sepolia testnet using Forge.
- **Test Script:** A sample test script demonstrates minting, updating, transferring, and burning operations.

---

## Architecture and Design

The system is divided into two main modules:

1. **SPACETRACK Token (ERC‑20):**  
   This token serves as the economic and governance backbone of the system. It employs OpenZeppelin’s `ERC20PresetMinterPauser` for controlled minting, burning, and pausing functions. The token is used to incentivize and reward participants across the aerospace supply chain.

2. **CDTNFT (ERC‑721):**  
   This token represents a digital twin for each aerospace component. Using OpenZeppelin’s ERC‑721 extensions, the contract supports controlled minting, updating metadata, transferring ownership, and burning tokens. Metadata URIs link to off-chain JSON files (for example, hosted on IPFS) that contain detailed component information.

The design follows best practices from successful blockchain supply chain projects and includes role-based permissions, modular smart contract architecture, and thorough event logging.

---

## Contracts

### SPACETRACK Token (ERC‑20)

- **File:** `SPACETRACKToken.sol`
- **Description:** Implements an ERC‑20 token using OpenZeppelin’s preset, with minting, pausing, and burning functionality.
- **Key Functions:**  
  - `mint`: Controlled by the MINTER_ROLE.
  - `burn`: Available for token removal.
  - `pause`/`unpause`: Emergency functions for securing token transfers.

### CDTNFT (ERC‑721)

- **File:** `CDTNFT.sol`
- **Description:** Represents digital twins for aerospace components as NFTs. It includes functions to mint new tokens, update metadata, transfer ownership, and burn tokens.
- **Key Functions:**  
  - `mintNFT`: Mint a new NFT for a component.
  - `updateTokenURI`: Modify the NFT metadata (e.g., after quality testing).
  - `transferFrom`: Standard ERC‑721 transfer function.
  - `burn`: Remove a defective component from circulation.
  - `pause`/`unpause`: Control transfers during emergencies.

---

## Installation and Deployment

### Prerequisites

- **Foundry/Forge:** For compiling and deploying Solidity contracts.
- **Node.js & Hardhat:** For running test scripts and simulating transactions.
- **Sepolia RPC URL and Private Key:** For deployment on the Sepolia testnet.

### Steps

1. **Clone the Repository:**
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Install Dependencies:**
   Install OpenZeppelin contracts and Hardhat if required.
   ```bash
   npm install
   ```

3. **Configure Foundry:**
   Update your `foundry.toml` file with the Sepolia RPC URL and your private key.

4. **Compile Contracts:**
   ```bash
   forge build
   ```

5. **Deploy Contracts:**
   Deploy the SPACETRACK token and CDTNFT contracts on Sepolia:
   ```bash
   forge create --rpc-url <sepolia_rpc_url> --private-key <your_private_key> SPACETRACKToken.sol:SPACETRACKToken
   forge create --rpc-url <sepolia_rpc_url> --private-key <your_private_key> CDTNFT.sol:CDTNFT
   ```

---

## Testing and Use-Case Walkthrough

A sample testing script (written in JavaScript for Hardhat) is provided in the `test/TokenTests.js` file. The script simulates the following use cases:

1. **Minting a New Component NFT:**  
   A new aerospace component NFT is minted and assigned to the manufacturer.

2. **Updating NFT Metadata After Testing:**  
   The NFT’s metadata is updated with testing results.

3. **Transferring NFT Ownership:**  
   The NFT is transferred from the manufacturer to a fabrication lab, representing a supply chain event.

4. **Burning a Defective Component NFT:**  
   The NFT is burned when the component is deemed defective.

Capture screenshots of transaction details (using a block explorer such as Sepolia Etherscan) and annotate them to demonstrate each use case.

---

## White Paper

The white paper, which contains detailed market research, tokenomics, technical specifications, and architectural diagrams, is included in this repository. You can find it in the root directory as `Solidity_and_Smart_Contract_Development__Homework_4.pdf`.

---

## License

This project is licensed under the MIT License.

---

Feel free to adjust the project details or extend the contracts further as needed. The provided implementation and documentation are intended to serve as a robust foundation for applying blockchain technology to aerospace supply chain management.
