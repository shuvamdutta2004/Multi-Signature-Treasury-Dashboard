Multi-Signature Treasury Dashboard
A polished Next.js frontend for a Soroban smart contract that lets signers collectively manage a shared treasury: propose transfers, vote on proposals, execute approved transfers, and track all activity in real time.

Next.js 15 Tailwind CSS v3 Stellar Soroban Testnet Freighter wallet

Contract Explorer

Stellar Expert: https://stellar.expert/explorer/testnet/contract/CANWI4UO2NHX3PJD6VDSHTXJHNPRBATL5VRBDCNQATUQW2LUWF4YM4JP

Contract ID: CANWI4UO2NHX3PJD6VDSHTXJHNPRBATL5VRBDCNQATUQW2LUWF4YM4JP

Freighter wallet Address: GBUX3IHQTAIRN3BXVBWZMKFW2CF6FE4QKQWYEDHYGQXL6OQ3YFMN5R3N

Overview
This project combines:

* A Soroban smart contract for multi-signature treasury logic (initialize, deposit, create proposal, vote, execute proposal)
* A Next.js dashboard for interacting with the contract
* Freighter wallet integration for authenticated write actions (create proposal, vote, execute proposal, deposit)
* Read-only contract calls for treasury balance lookup, signer registration checks, proposal listing, threshold checks, and proposal voting counts

The current frontend is designed as a clean operator console with live status output, wallet visibility, voting progress indicators, real-time events feed, and responsive layout for desktop and mobile.

What You Can Do
* Initialize a new treasury with custom signers list and approval threshold
* Deposit XLM into the treasury contract
* Create a Spend Proposal (specifying recipient, amount, and description)
* Vote on active proposals (approve / reject)
* Execute an approved proposal that has met or exceeded the threshold
* List all treasury proposals
* Track real-time activity and contract events
* View local transaction history with execution statuses

Smart Contract Behavior
The Soroban contract stores treasury state with:
* signers (Vector of signer Addresses)
* threshold (approval count needed)
* proposal registry (Spend Proposals)
* voter maps (signer votes cast per proposal)
* balances (treasury XLM balance)

Exposed contract methods:
* `initialize`
* `deposit`
* `create_proposal`
* `vote`
* `execute_proposal`
* `get_proposal`
* `get_proposals`
* `get_signers`
* `get_balance`
* `get_threshold`

Frontend Highlights
* StellarWalletsKit integration with support for Freighter and other wallets
* Live contract response tracking and toast notifications
* Voting progress indicator with threshold status badges
* Auto-polling of contract events feed every 5 seconds using getEvents RPC
* Responsive dashboard layout with separate treasury stats, active proposals, event feed, and transaction history panels

Tech Stack
* Next.js 15
* Tailwind CSS v3
* @stellar/stellar-sdk
* @creit.tech/stellar-wallets-kit
* Soroban smart contract in Rust

Project Structure
.
├── app/
│   ├── page.tsx
│   ├── dashboard/
│   ├── treasury/
│   ├── activity/
│   ├── transactions/
│   ├── layout.tsx
│   └── providers.tsx
├── components/
│   ├── layout/
│   │   ├── Navbar.tsx
│   │   └── Sidebar.tsx
│   ├── wallet/
│   │   ├── WalletConnectButton.tsx
│   │   └── AddressDisplay.tsx
│   ├── treasury/
│   │   ├── ProposalCard.tsx
│   │   ├── CreateProposalForm.tsx
│   │   ├── VotingProgress.tsx
│   │   └── TreasuryStats.tsx
│   ├── activity/
│   │   ├── EventFeed.tsx
│   │   └── EventItem.tsx
│   └── transactions/
│       └── TransactionStatus.tsx
├── contracts/
│   └── treasury/
│       ├── Cargo.toml
│       └── src/
│           ├── lib.rs
│           └── types.rs
├── hooks/
│   ├── useWallet.ts
│   ├── useTreasury.ts
│   ├── useProposals.ts
│   ├── useVote.ts
│   ├── useCreateProposal.ts
│   ├── useContractEvents.ts
│   └── useExecuteProposal.ts
├── lib/
│   ├── stellar/
│   │   ├── client.ts
│   │   ├── contract.ts
│   │   ├── wallet.ts
│   │   └── events.ts
│   └── utils.ts
├── store/
│   ├── walletStore.ts
│   ├── transactionStore.ts
│   └── eventStore.ts
├── types/
│   ├── contract.ts
│   ├── wallet.ts
│   └── events.ts
└── README.md

Local Setup
Prerequisites
* Node.js installed
* npm installed
* Freighter wallet extension
* Access to Stellar Soroban testnet

Install
```bash
npm install
```

Run The App
```bash
npm run dev
```

Production Build
```bash
npm run build
```

Lint
```bash
npm run lint
```

User Flow
1. Connect Freighter Wallet (address: `GBUX3IHQTAIRN3BXVBWZMKFW2CF6FE4QKQWYEDHYGQXL6OQ3YFMN5R3N`).
2. Select dashboard to check signer status and balance.
3. Propose a new spend transfer (recipient, amount, description).
4. Have signers vote on the proposal (approve/reject).
5. Once the threshold is met, execute the proposal to transfer the funds.
6. Track events in real-time in the activity feed.

