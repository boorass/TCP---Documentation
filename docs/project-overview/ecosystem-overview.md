---
title: Ecosystem Overview
sidebar_position: 3
description: Understanding TCP's layered ecosystem structure
---

# Ecosystem Overview

Protocol (TCP) is organized as a **layered ecosystem**, where different functional areas are handled by specialized components. This structure enables clarity, security, and scalability.

## The Layered Architecture

TCP's ecosystem is built in distinct layers, each serving a specific purpose:

```
┌─────────────────────────────────────────┐
│         Governance & Operations         │
├─────────────────────────────────────────┤
│  Token  │ Treasury │ Liquidity │ Staking │
├─────────────────────────────────────────┤
│  Burn   │ Ecosystem │ Vesting │ Router  │
├─────────────────────────────────────────┤
│      Polygon Blockchain (Layer 1)       │
└─────────────────────────────────────────┘
```

## Layer 1: Token Layer

### Purpose
The Token Layer is the foundation of the entire ecosystem. It manages the TCP token itself.

### Key Components
- **TCP Token Contract** — ERC-20 compatible token
- **Token Supply** — Total circulating and maximum supply
- **Token Transfers** — User-to-user transfers
- **Token Approvals** — Spending allowances for other contracts

### Responsibilities
- Maintain accurate token balances
- Process transfers between addresses
- Manage approvals for contract interactions
- Emit transfer events for transparency

### Key Features
- Standard ERC-20 interface
- Compatible with all wallets and exchanges
- Transparent balance tracking
- Immutable transaction history

## Layer 2: Treasury Layer

### Purpose
The Treasury Layer manages strategic reserves and ensures disciplined access to treasury assets.

### Key Components
- **Treasury Contract** — Holds and manages reserves
- **Withdrawal Proposals** — Formal process for accessing funds
- **Timelock Mechanism** — Delays before execution
- **Cancellation System** — Ability to stop pending withdrawals

### Responsibilities
- Safeguard strategic reserves
- Process withdrawal proposals
- Enforce timelock delays
- Log all treasury operations

### Key Features
- Non-instantaneous withdrawals
- Proposal-based access control
- Timelock protection
- Complete on-chain audit trail

### Typical Operations
1. **Proposal Creation** — Owner proposes withdrawal
2. **Parameter Recording** — Amount and recipient recorded
3. **Timelock Period** — Waiting period begins
4. **Execution Window** — After delay, withdrawal can execute
5. **Completion** — Funds transferred to recipient

## Layer 3: Liquidity Layer

### Purpose
The Liquidity Layer protects LP and ensures long-term liquidity availability.

### Key Components
- **Liquidity Manager Contract** — Manages LP holdings
- **Permanent Liquidity** — 85% portion with long-term lock
- **Flexible Liquidity** — 15% portion with daily limits
- **Withdrawal Proposals** — Formal process for LP access

### Responsibilities
- Protect LP from sudden withdrawal
- Manage permanent and flexible portions
- Enforce withdrawal limits
- Maintain liquidity transparency

### Key Features
- Permanent lock (365+ days)
- Flexible portion with daily caps
- Proposal-based withdrawals
- Timelock enforcement

### Protection Mechanisms
- **Permanent Portion** — Cannot be withdrawn for extended period
- **Flexible Portion** — Daily limits prevent large withdrawals
- **Proposal System** — Formal process for any withdrawal
- **Timelock** — Additional delay before execution

## Layer 4: Reward Layer

### Purpose
The Reward Layer enables staking and distributes rewards to participants.

### Key Components
- **Staking Contract** — Manages user stakes
- **Reward Distribution** — Calculates and distributes rewards
- **Reward Pool** — Holds rewards for distribution
- **User Tracking** — Tracks stakes and rewards per user

### Responsibilities
- Accept user stakes
- Calculate reward amounts
- Distribute rewards fairly
- Track user participation

### Key Features
- User-friendly staking
- Transparent reward calculation
- Flexible unstaking
- Real-time reward tracking

### Typical User Flow
1. **Stake** — User deposits TCP tokens
2. **Earn** — Rewards accrue over time
3. **Claim** — User claims earned rewards
4. **Unstake** — User can withdraw staked tokens

## Layer 5: Burn Layer

### Purpose
The Burn Layer manages token supply reduction according to protocol rules.

### Key Components
- **Burn Engine Contract** — Executes burn operations
- **Burn Logic** — Defines when and how tokens are burned
- **Supply Tracking** — Monitors total supply changes
- **Burn Events** — Logs all burn operations

### Responsibilities
- Execute burn operations
- Maintain burn logic consistency
- Track supply changes
- Ensure transparency

### Key Features
- Transparent burn logic
- Traceable supply reduction
- Economic discipline
- Long-term sustainability

## Layer 6: Allocation Layer

### Purpose
The Allocation Layer manages ecosystem resources and supports growth initiatives.

### Key Components
- **Ecosystem Vault** — Holds allocation reserves
- **Distribution Logic** — Manages allocation release
- **Vesting Contracts** — Time-locked distributions
- **Allocation Tracking** — Monitors allocation usage

### Responsibilities
- Manage ecosystem allocations
- Support ecosystem development
- Handle vesting schedules
- Track allocation usage

### Key Features
- Structured allocation process
- Time-locked releases
- Transparent distribution
- Growth support

### Typical Allocations
- **Ecosystem Development** — Support for projects building on TCP
- **Partnerships** — Resources for strategic partnerships
- **Community Initiatives** — Support for community-led projects
- **Strategic Reserves** — Long-term growth reserves

## Layer 7: Orchestration Layer

### Purpose
The Orchestration Layer coordinates between different components and manages complex operations.

### Key Components
- **Protocol Router** — Coordinates contract interactions
- **Operation Sequencing** — Manages multi-step operations
- **State Consistency** — Ensures consistent protocol state
- **Error Handling** — Manages error conditions

### Responsibilities
- Coordinate between contracts
- Manage complex operations
- Maintain state consistency
- Handle edge cases

### Key Features
- Reduced operational errors
- Consistent behavior
- Simplified integration
- Improved reliability

## How Layers Interact

### Example: Staking Rewards Distribution

```
1. Reward Pool (Allocation Layer)
   ↓
2. Staking Contract (Reward Layer)
   ↓
3. Token Contract (Token Layer)
   ↓
4. User Wallets
```

### Example: Treasury Withdrawal

```
1. Treasury Contract (Treasury Layer)
   ↓
2. Timelock Enforcement
   ↓
3. Token Contract (Token Layer)
   ↓
4. Recipient Wallet
```

### Example: LP Protection

```
1. Liquidity Manager (Liquidity Layer)
   ↓
2. Proposal System
   ↓
3. Timelock Enforcement
   ↓
4. LP Holder Wallet
```

## Data Flow

All layers work together to create a complete ecosystem:

```
User Interaction
    ↓
Contract Layer (Token, Treasury, Liquidity, Staking, etc.)
    ↓
Event Logging
    ↓
On-Chain Verification (PolygonScan)
    ↓
Community Monitoring
```

## Security Across Layers

Each layer has its own security mechanisms:

| Layer | Security Mechanism |
|-------|-------------------|
| **Token** | Standard ERC-20 security |
| **Treasury** | Timelocks + Proposals |
| **Liquidity** | Permanent lock + Daily limits |
| **Rewards** | Transparent calculation |
| **Burn** | Explicit burn logic |
| **Allocation** | Vesting schedules |
| **Orchestration** | State consistency checks |

## Ecosystem Resilience

The layered architecture provides resilience:

- **Compartmentalization** — Issues in one layer don't cascade
- **Independent Verification** — Each layer can be verified independently
- **Graceful Degradation** — Protocol can function even if some features are limited
- **Recovery Options** — Multiple paths to recover from issues

## Scalability

The layered design enables future scalability:

- **New Layers** — Additional functionality can be added
- **Layer Upgrades** — Individual layers can be improved
- **Cross-Chain** — Layers could potentially be deployed across chains
- **Integration** — External protocols can integrate with specific layers

## Key Takeaways

1. **Layered Design** — Each layer has a specific purpose
2. **Clear Separation** — Layers interact through defined interfaces
3. **Security** — Each layer has appropriate safeguards
4. **Transparency** — All operations logged and verifiable
5. **Scalability** — Architecture supports future growth

---

**Next:** Learn about TCP's [Value Proposition](./value-proposition.md) and why it matters.
