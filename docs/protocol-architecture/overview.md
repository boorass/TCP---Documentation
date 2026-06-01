---
title: Architecture Overview
sidebar_position: 1
description: Understanding TCP's modular smart contract architecture
---

# Architecture Overview

Protocol (TCP) is built on a **modular architecture** where different functions are handled by specialized smart contracts, each with clear responsibilities and security safeguards.

## The Modular Approach

Instead of concentrating all functionality in a single contract, TCP distributes responsibilities across multiple contracts:

```
TCP Ecosystem
├── Token Contract (ERC-20)
├── Protocol Router (Orchestration)
├── Treasury Contract (Reserves)
├── Liquidity Manager (LP Protection)
├── Staking Contract (Rewards)
├── Burn Engine (Supply Control)
├── Ecosystem Vault (Allocations)
└── Vesting Contract (Time-Locked Distribution)
```

## Benefits of Modularity

### 1. Clarity

**What It Means**
- Each contract has a single, clear purpose
- Functionality is easy to understand
- Responsibilities are explicit
- Code is easier to read and follow

**Why It Matters**
- Users understand what each contract does
- Developers can integrate more easily
- Auditors can review more thoroughly
- Community can verify operations

### 2. Security

**What It Means**
- Problems in one contract don't cascade to others
- Risks are compartmentalized
- Each contract can be secured independently
- Attack surface is reduced

**Why It Matters**
- Vulnerability in one area doesn't compromise entire system
- Easier to identify and fix issues
- Reduced risk of systemic failure
- Better overall security posture

### 3. Auditability

**What It Means**
- Each contract can be reviewed independently
- Scope is limited and manageable
- Interactions are explicit
- Testing is more thorough

**Why It Matters**
- Audits are more efficient
- Reviewers can focus on specific areas
- Issues are easier to identify
- Confidence in security is higher

### 4. Maintainability

**What It Means**
- Changes to one contract don't affect others
- Upgrades can be done independently
- Bugs can be fixed in isolation
- New features can be added without disruption

**Why It Matters**
- Protocol can evolve without major disruptions
- Fixes can be deployed quickly
- New features can be added safely
- Long-term sustainability is improved

### 5. Scalability

**What It Means**
- New functionality can be added as new contracts
- Existing contracts don't need to change
- System can grow without becoming monolithic
- New features can be integrated cleanly

**Why It Matters**
- Protocol can grow and evolve
- New features don't require rewriting existing code
- System remains manageable as it grows
- Future expansion is possible

## Architecture Principles

### 1. Single Responsibility

Each contract has one primary responsibility:

| Contract | Responsibility |
|----------|-----------------|
| **Token** | Manage token transfers and balances |
| **Treasury** | Manage strategic reserves |
| **Liquidity Manager** | Protect and manage LP |
| **Staking** | Distribute rewards |
| **Burn Engine** | Manage supply reduction |
| **Ecosystem Vault** | Allocate ecosystem resources |
| **Vesting** | Handle time-locked distributions |
| **Router** | Coordinate between contracts |

### 2. Clear Interfaces

Contracts interact through:
- **Well-defined functions** — Clear entry points
- **Explicit parameters** — Clear inputs and outputs
- **Event logging** — Transparent operations
- **Standard patterns** — Familiar to developers

### 3. Separation of Concerns

Different concerns are handled by different contracts:
- **Token mechanics** — Token contract
- **Asset management** — Treasury and Liquidity Manager
- **Reward distribution** — Staking contract
- **Supply management** — Burn Engine
- **Coordination** — Router contract

### 4. Explicit Dependencies

Contract dependencies are:
- **Minimal** — Contracts don't depend on each other unnecessarily
- **Explicit** — Dependencies are clear and documented
- **Manageable** — Easy to understand interactions
- **Testable** — Dependencies can be tested independently

## Contract Interactions

### Token Contract

The Token Contract is the foundation:
- Manages TCP token balances
- Processes transfers
- Handles approvals
- Emits transfer events

### Treasury Contract

The Treasury Contract manages reserves:
- Holds strategic tokens
- Processes withdrawal proposals
- Enforces timelocks
- Logs all operations

### Liquidity Manager

The Liquidity Manager protects LP:
- Manages permanent and flexible portions
- Enforces locks and limits
- Processes withdrawal proposals
- Logs all operations

### Staking Contract

The Staking Contract distributes rewards:
- Accepts user stakes
- Calculates rewards
- Distributes rewards
- Tracks participation

### Burn Engine

The Burn Engine manages supply:
- Executes burn operations
- Tracks supply changes
- Logs burn events
- Maintains transparency

### Ecosystem Vault

The Ecosystem Vault allocates resources:
- Holds ecosystem allocations
- Distributes to ecosystem projects
- Tracks allocation usage
- Maintains transparency

### Vesting Contract

The Vesting Contract handles time-locked distributions:
- Manages vesting schedules
- Releases tokens over time
- Tracks vesting progress
- Logs releases

### Protocol Router

The Protocol Router coordinates operations:
- Orchestrates multi-contract operations
- Ensures consistency
- Reduces operational errors
- Simplifies integration

## Data Flow

### Example: Staking Rewards Distribution

```
1. Staking Contract
   - Calculates rewards for stakers
   - Determines reward amounts

2. Token Contract
   - Transfers reward tokens
   - Updates balances

3. Event Logging
   - Logs reward distribution
   - Records on-chain

4. User Verification
   - User checks balance
   - Verifies rewards received
```

### Example: Treasury Withdrawal

```
1. Treasury Contract
   - Receives withdrawal proposal
   - Records proposal parameters
   - Starts timelock

2. Timelock Period
   - Waiting period enforced
   - Community can monitor
   - Proposal can be cancelled

3. Token Contract
   - Transfers tokens
   - Updates balances

4. Event Logging
   - Logs withdrawal
   - Records on-chain

5. User Verification
   - User checks balance
   - Verifies withdrawal received
```

## Security Architecture

### Layered Security

Security is implemented at multiple layers:

```
Application Layer
    ↓
Contract Layer (Access Controls)
    ↓
Timelock Layer (Delays)
    ↓
Blockchain Layer (Immutability)
```

### Access Control

Different operations require different approval levels:

| Operation | Approval Level |
|-----------|-----------------|
| **Routine Operations** | Owner |
| **Critical Operations** | Multisig |
| **Major Changes** | Community (if applicable) |

### Timelock Enforcement

Critical operations require waiting periods:
- Treasury withdrawals
- Liquidity changes
- Parameter adjustments
- Major upgrades

### Event Logging

All operations are logged:
- Transfer events
- Proposal events
- Execution events
- Parameter change events

## Deployment Architecture

### Contract Deployment

Contracts are deployed in order:

```
1. Token Contract
   - Deploy TCP token
   - Set initial parameters

2. Treasury Contract
   - Deploy treasury
   - Set token reference

3. Liquidity Manager
   - Deploy liquidity manager
   - Set token reference

4. Staking Contract
   - Deploy staking
   - Set token and reward references

5. Other Contracts
   - Deploy burn engine
   - Deploy ecosystem vault
   - Deploy vesting contracts

6. Router Contract
   - Deploy router
   - Set contract references
```

### Contract Initialization

After deployment:
- Set contract references
- Configure parameters
- Initialize balances
- Enable operations

## Upgrade Strategy

### Upgrade Approach

TCP uses a careful upgrade strategy:

1. **Minimal Changes** — Only change what's necessary
2. **Backward Compatibility** — Maintain compatibility when possible
3. **Gradual Rollout** — Test thoroughly before deployment
4. **Community Communication** — Inform community of changes
5. **Transparent Process** — All changes logged and verifiable

### Upgrade Process

Upgrades follow this process:

```
1. Development
   - Develop upgrade
   - Test thoroughly
   - Review code

2. Proposal
   - Propose upgrade
   - Explain changes
   - Gather feedback

3. Approval
   - Get necessary approvals
   - Community input if needed
   - Formal approval

4. Deployment
   - Deploy upgrade
   - Verify deployment
   - Monitor operations

5. Verification
   - Community verifies upgrade
   - Monitor for issues
   - Provide support
```

## Key Takeaways

1. **Modular design** — Each contract has single responsibility
2. **Clear separation** — Concerns are separated across contracts
3. **Explicit interactions** — Contract interactions are clear
4. **Layered security** — Security implemented at multiple levels
5. **Scalable architecture** — System can grow and evolve

---

**Next:** See the [Contract Map](./contract-map.md) for a detailed overview of all TCP contracts.
