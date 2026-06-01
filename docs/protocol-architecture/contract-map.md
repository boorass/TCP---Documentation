---
title: Contract Map
sidebar_position: 2
description: Complete overview of all TCP smart contracts and their roles
---

# Contract Map

This page provides a comprehensive map of all smart contracts in the Protocol (TCP) ecosystem.

## Contract Overview

TCP consists of the following smart contracts:

```
TCP Ecosystem Contracts
├── Core Contracts
│   ├── TCP Token
│   ├── Protocol Router
│   └── Access Control
├── Asset Management
│   ├── Treasury
│   ├── Liquidity Manager
│   └── Ecosystem Vault
├── Reward & Distribution
│   ├── Staking
│   ├── Burn Engine
│   └── Vesting
└── Supporting Contracts
    └── (Additional as needed)
```

## Core Contracts

### 1. TCP Token Contract

**Purpose**
- Manage the TCP token
- Handle transfers and balances
- Manage approvals
- Emit transfer events

**Key Functions**
- `transfer()` — Transfer tokens
- `approve()` — Approve spending
- `transferFrom()` — Transfer on behalf
- `balanceOf()` — Check balance
- `totalSupply()` — Check total supply

**Key Events**
- `Transfer` — Token transfer
- `Approval` — Approval granted

**Characteristics**
- ERC-20 compatible
- Standard interface
- Transparent operations
- Immutable history

### 2. Protocol Router Contract

**Purpose**
- Coordinate between contracts
- Manage complex operations
- Ensure consistency
- Reduce operational errors

**Key Functions**
- `executeOperation()` — Execute multi-contract operation
- `validateOperation()` — Validate operation
- `logOperation()` — Log operation

**Key Events**
- `OperationExecuted` — Operation completed
- `OperationFailed` — Operation failed

**Characteristics**
- Orchestrates interactions
- Ensures consistency
- Simplifies integration
- Improves reliability

### 3. Access Control Contract

**Purpose**
- Manage roles and permissions
- Control access to functions
- Enforce authorization
- Log access changes

**Key Functions**
- `grantRole()` — Grant role
- `revokeRole()` — Revoke role
- `hasRole()` — Check role
- `renounceRole()` — Renounce role

**Key Events**
- `RoleGranted` — Role granted
- `RoleRevoked` — Role revoked

**Characteristics**
- Role-based access control
- Explicit permissions
- Transparent changes
- Auditable access

## Asset Management Contracts

### 4. Treasury Contract

**Purpose**
- Manage strategic reserves
- Process withdrawal proposals
- Enforce timelocks
- Log all operations

**Key Functions**
- `proposeWithdrawal()` — Propose withdrawal
- `executeWithdrawal()` — Execute withdrawal
- `cancelProposal()` — Cancel proposal
- `getTreasuryBalance()` — Check balance
- `getPendingProposal()` — Check pending proposal

**Key Events**
- `WithdrawalProposed` — Proposal created
- `WithdrawalExecuted` — Withdrawal executed
- `ProposalCancelled` — Proposal cancelled

**Characteristics**
- Proposal-based access
- Timelock enforcement
- Cancellation mechanism
- Complete transparency

**Parameters**
- Timelock delay (e.g., 7 days)
- Maximum withdrawal amount
- Recipient address
- Proposal status

### 5. Liquidity Manager Contract

**Purpose**
- Protect and manage LP
- Enforce locks and limits
- Process withdrawal proposals
- Log all operations

**Key Functions**
- `lockLiquidity()` — Lock LP
- `proposeWithdrawal()` — Propose withdrawal
- `executeWithdrawal()` — Execute withdrawal
- `getLPBalance()` — Check LP balance
- `getPermanentLockStatus()` — Check lock status
- `getFlexibleLimitStatus()` — Check daily limit

**Key Events**
- `LiquidityLocked` — LP locked
- `WithdrawalProposed` — Proposal created
- `WithdrawalExecuted` — Withdrawal executed
- `LockExtended` — Lock extended

**Characteristics**
- Permanent and flexible portions
- Lock enforcement
- Daily limits
- Complete transparency

**Parameters**
- Permanent portion: 85%
- Flexible portion: 15%
- Permanent lock duration: 365+ days
- Daily withdrawal limit
- Timelock delay

### 6. Ecosystem Vault Contract

**Purpose**
- Allocate ecosystem resources
- Distribute to ecosystem projects
- Track allocation usage
- Maintain transparency

**Key Functions**
- `allocateTokens()` — Allocate tokens
- `distributeTokens()` — Distribute tokens
- `getBalance()` — Check balance
- `getAllocationStatus()` — Check allocation

**Key Events**
- `TokensAllocated` — Allocation created
- `TokensDistributed` — Distribution executed

**Characteristics**
- Structured allocation
- Transparent distribution
- Usage tracking
- Auditable operations

## Reward & Distribution Contracts

### 7. Staking Contract

**Purpose**
- Accept user stakes
- Calculate rewards
- Distribute rewards
- Track participation

**Key Functions**
- `stake()` — Deposit tokens
- `unstake()` — Withdraw tokens
- `claimRewards()` — Claim rewards
- `getStakeBalance()` — Check stake
- `getRewardBalance()` — Check rewards
- `getRewardRate()` — Check reward rate

**Key Events**
- `Staked` — Tokens staked
- `Unstaked` — Tokens unstaked
- `RewardsClaimed` — Rewards claimed

**Characteristics**
- User-friendly interface
- Transparent calculations
- Flexible unstaking
- Real-time tracking

**Parameters**
- Reward rate (e.g., 10% APY)
- Minimum stake (if applicable)
- Maximum stake (if applicable)
- Reward period

### 8. Burn Engine Contract

**Purpose**
- Execute burn operations
- Track supply changes
- Log burn events
- Maintain transparency

**Key Functions**
- `burn()` — Burn tokens
- `scheduleBurn()` — Schedule burn
- `getBurnHistory()` — Check burn history
- `getTotalBurned()` — Check total burned

**Key Events**
- `TokensBurned` — Burn executed
- `BurnScheduled` — Burn scheduled

**Characteristics**
- Transparent burn logic
- Traceable supply reduction
- Economic discipline
- Auditable operations

**Parameters**
- Burn amount
- Burn schedule
- Burn triggers

### 9. Vesting Contract

**Purpose**
- Manage vesting schedules
- Release tokens over time
- Track vesting progress
- Log releases

**Key Functions**
- `createVesting()` — Create vesting schedule
- `releaseTokens()` — Release vested tokens
- `getVestingBalance()` — Check vesting balance
- `getVestingSchedule()` — Check schedule

**Key Events**
- `VestingCreated` — Schedule created
- `TokensReleased` — Tokens released

**Characteristics**
- Structured vesting
- Automatic release
- Transparent schedules
- Auditable operations

**Parameters**
- Vesting duration
- Release schedule
- Cliff period (if applicable)
- Recipient address

## Contract Relationships

### Contract Dependencies

```
Token Contract
    ↑
    ├── Treasury (holds tokens)
    ├── Staking (transfers rewards)
    ├── Burn Engine (burns tokens)
    ├── Vesting (releases tokens)
    └── Liquidity Manager (holds LP)

Protocol Router
    ↓
    ├── Treasury
    ├── Liquidity Manager
    ├── Staking
    └── Other contracts
```

### Data Flow

```
User Interaction
    ↓
Contract Function Call
    ↓
Token Transfer (if applicable)
    ↓
Event Emission
    ↓
On-Chain Logging
    ↓
Community Verification
```

## Contract Addresses

For deployed contract addresses, see [Deployed Addresses](./deployed-addresses.md).

## Contract Verification

All contracts are:
- **Deployed on Polygon** — Chain ID 137
- **Verified on PolygonScan** — Source code visible
- **Auditable** — Can be reviewed by third parties
- **Transparent** — All operations logged

## Contract Interaction Examples

### Example 1: Staking Rewards

```
1. User calls stake() on Staking Contract
2. Staking Contract calls transferFrom() on Token Contract
3. User's tokens transferred to Staking Contract
4. Stake recorded in Staking Contract
5. Rewards begin accruing
6. User calls claimRewards() on Staking Contract
7. Staking Contract calls transfer() on Token Contract
8. Reward tokens transferred to user
9. Events logged on-chain
```

### Example 2: Treasury Withdrawal

```
1. Owner calls proposeWithdrawal() on Treasury Contract
2. Proposal recorded with timelock
3. Timelock period begins
4. Community monitors proposal
5. After timelock expires, owner calls executeWithdrawal()
6. Treasury Contract calls transfer() on Token Contract
7. Tokens transferred to recipient
8. Treasury balance updated
9. Events logged on-chain
```

### Example 3: Liquidity Withdrawal

```
1. Owner calls proposeWithdrawal() on Liquidity Manager
2. Proposal recorded with timelock
3. Timelock period begins
4. Community monitors proposal
5. After timelock expires, owner calls executeWithdrawal()
6. Liquidity Manager transfers LP tokens
7. LP balance updated
8. Daily limit consumption updated
9. Events logged on-chain
```

## Key Takeaways

1. **Modular design** — Each contract has single responsibility
2. **Clear roles** — Each contract's purpose is explicit
3. **Explicit interactions** — Contract interactions are clear
4. **Transparent operations** — All operations logged on-chain
5. **Auditable system** — Complete audit trail available

---

**Next:** Learn about the [TCP Token](./tcp-token.md) contract in detail.
