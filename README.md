# FHE-Compliant-Voting

A confidential voting system for enterprise governance and compliance, built with Zama (FHE) and Web3 technologies. This platform enables critical organizational decisions to be made with the highest degree of privacy and verifiability.

## Project Background

Traditional corporate governance and compliance mechanisms often struggle with ensuring authentic, uncoerced feedback and voting. Key challenges include:

* **Fear of Coercion:** Stakeholders may alter their votes or feedback if they believe their individual choices will be exposed, especially in sensitive matters.
* **Centralized Trust:** System administrators in traditional systems have the potential to view, alter, or suppress sensitive data, creating a single point of failure and trust.
* **Lack of Verifiability:** It is difficult for participants to independently verify that their vote was counted correctly without revealing the vote itself.
* **Inadequate Privacy:** Standard blockchain solutions, while transparent, expose voting patterns, which can be undesirable in a corporate context.

FHE-Compliant-Voting addresses these issues by leveraging Fully Homomorphic Encryption (FHE) to create a trustless system where votes are processed without ever being decrypted.

## Features

### Core Functionality

* **Encrypted Vote Submission:** Users cast votes that are encrypted on the client-side before being submitted to the smart contract.
* **Homomorphic Tallying:** The smart contract aggregates vote counts directly on the encrypted data. Only the final, aggregated result is ever decrypted and made public.
* **Verifiable Anonymity:** The system can verify a voter's eligibility without linking their identity to their specific vote.
* **Threshold-Based Alerts:** Configure alerts that trigger when vote counts for a certain category exceed a predefined (and potentially encrypted) threshold.
* **Zero-Knowledge Audits:** Administrators can generate zero-knowledge proofs to confirm that all processing was done correctly, without revealing any underlying private data.

### Privacy & Security

* **End-to-End Encryption:** Votes are protected from the user's device to the final tally, with no plaintext exposure in between.
* **Immutable Records:** All encrypted votes are stored immutably on the blockchain, preventing tampering or deletion.
* **Admin-Blind Access:** Management and administrators can only view aggregated statistics, not the plaintext content of individual votes.

## Architecture

### Smart Contracts

**ConfidentialVote.sol** (deployed on an FHE-enabled EVM)

* Manages encrypted vote submissions.
* Maintains immutable, encrypted records on-chain.
* Aggregates vote statistics homomorphically.
* Provides transparent public access to final, tallied results.

### Frontend Application

* **React + TypeScript:** For a modern and interactive user interface.
* **Ethers.js:** For all blockchain interactions and smart contract calls.
* **Zama Web Wallet/SDK:** To handle client-side FHE key management and encryption.
* **Real-time Dashboard:** Displays the latest proposals and final, aggregated voting results.

## Technology Stack

### Blockchain

* **Solidity ^0.8.24:** For smart contract development.
* **Zama fhEVM:** Enables homomorphic operations on encrypted data within the EVM.
* **Hardhat:** Development, testing, and deployment framework.
* **Ethereum (or L2s):** Target network for deployment.

### Frontend

* **React 18 + TypeScript:** Modern frontend framework.
* **Ethers.js:** Ethereum blockchain interaction library.
* **WASM:** For running FHE encryption libraries efficiently in the browser.
* **CSS / Styled-Components:** For styling and responsive layout.

## Installation

### Prerequisites

* Node.js 18+
* npm / yarn / pnpm package manager
* An Ethereum wallet like MetaMask

### Setup

```bash
# Clone the repository
git clone <repository-url>
cd FHE-Compliant-Voting

# Install dependencies for the backend/contracts
npm install

# Compile contracts
npx hardhat compile

# Deploy to a network (configure hardhat.config.js first)
npx hardhat run deploy/deploy.ts --network <your-network>

# Navigate to the frontend directory
cd frontend

# Install frontend dependencies
npm install

# Run the development server
npm run dev