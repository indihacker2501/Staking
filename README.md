Staking and Reward System

Overview

This project implements a staking system where users can stake XFI tokens in exchange for stXFI tokens (representing their stake) and earn rwXFI rewards over time. Users can later unstake their tokens and claim their accumulated rewards.

The project consists of three Solidity smart contracts:

RewardXFI.sol – The reward token contract (rwXFI).

StakeXFI.sol – The staking token contract (stXFI).

Staking.sol – The core staking contract, handling deposits, rewards, and withdrawals.

A frontend is also available to interact with the staking system.

Smart Contracts

1. RewardXFI (rwXFI - Reward Token)

This is an ERC-20 token used as the staking reward.

Constructor: Mints an initial supply to the contract deployer.

Transfer Functionality: Standard ERC-20 token transfers.

2. StakeXFI (stXFI - Staking Token)

This token represents the user's stake in the system.

Minting: When a user stakes XFI, they receive 100 stXFI per 1 XFI staked.

Burning: When unstaking, the equivalent stXFI is burned before returning XFI to the user.

Transfers: Supports ERC-20 transfers.

3. Staking (Core Staking Contract)

This contract allows users to stake XFI tokens, earn rewards, and withdraw their staked assets.

Staking: Users send XFI to receive stXFI tokens.

Rewards Calculation: Users earn rwXFI over time, based on the stake amount.

Claim Rewards: Users can claim their accumulated rwXFI.

Unstake: Users can withdraw their XFI, burning stXFI in the process.

Reward Percentage: Configurable by the contract owner.

Key Events:

Staked(address user, uint256 amount, bool isXFI) – Triggered when a user stakes.

RewardsCalculated(address user, uint256 reward) – Logs calculated rewards.

RewardsClaimed(address user, uint256 reward) – Logs reward claims.

Unstaked(address user, uint256 amount, bool isXFI) – Logs unstaking actions.

RewardPercentageUpdated(uint256 newPercentage) – Logs reward rate changes.

Frontend

The frontend allows users to interact with the staking system via Metamask and Web3.js/Ethers.js.

Features:

✅ Stake XFI – Convert XFI into stXFI.
✅ Claim Rewards – Withdraw accumulated rwXFI.
✅ Unstake Tokens – Convert stXFI back into XFI.
✅ View Balances – Display user balances for stXFI, rwXFI, and XFI.
✅ Responsive UI – User-friendly interface with real-time updates.

Tech Stack:

Frontend: React.js (Next.js/Vue.js can also be used)

Blockchain Integration: Ethers.js / Web3.js

Wallet Connection: MetaMask / WalletConnect

UI Components: TailwindCSS / Bootstrap

Installation & Deployment

1. Clone Repository

git clone https://github.com/your-repo/staking-system.git
cd staking-system

2. Install Dependencies

npm install

3. Deploy Contracts

Modify hardhat.config.js or truffle-config.js with your network settings.

Compile Contracts:

npx hardhat compile

Deploy Contracts:

npx hardhat run scripts/deploy.js --network goerli

Save the deployed contract addresses for frontend integration.

4. Start Frontend

npm run dev

Usage Guide

Connect Wallet using Metamask.

Stake XFI to receive stXFI tokens.

Wait for rewards to accumulate.

Claim rwXFI rewards anytime.

Unstake when needed to retrieve XFI.

Security Considerations

Contract is Ownable, allowing only the owner to modify reward rates.

Uses OpenZeppelin ERC-20 standards for security.

Requires sufficient XFI balance in contract to facilitate unstaking.

Future Improvements

🚀 Auto-compounding rewards
🚀 Flexible staking periods
🚀 Governance mechanism for community decisions
