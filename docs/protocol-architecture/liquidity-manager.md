---
title: Liquidity Manager Contract
sidebar_position: 6
description: Technical details of the Liquidity Manager contract and LP protection
---

# Liquidity Manager Contract

The **Liquidity Manager Contract** protects and manages LP with advanced safeguards, separating permanent and flexible portions with distinct protection mechanisms.

## Contract Purpose

The Liquidity Manager:
- Manages LP holdings
- Protects permanent portion (85%)
- Manages flexible portion (15%)
- Enforces locks and limits
- Logs all operations

## Core Concepts

### LP Structure

```
Total LP
├── Permanent Portion (85%)
│   └── Long-term lock (365+ days)
└── Flexible Portion (15%)
    └── Daily limits + timelock
```

### Protection Levels

| Portion | Lock Duration | Daily Limit | Timelock |
|---------|---------------|-------------|----------|
| **Permanent** | 365+ days | None | Yes |
| **Flexible** | None | Yes | Yes |

## Core Functions

### Permanent Liquidity Management

#### `lockLiquidity(uint256 amount, uint256 duration)`

Locks LP for a specified duration.

**Parameters**
- `amount` — LP amount to lock
- `duration` — Lock duration in seconds

**Returns**
- `uint256` — Lock ID

**Events**
- `LiquidityLocked(lockId, amount, unlockTime)`

**Requirements**
- Caller must be owner or authorized
- Amount must not exceed available LP
- Duration must be at least 365 days

**Example**
```
// Lock 1000 LP for 365 days
lockLiquidity(1000e18, 365 days)
```

#### `extendLock(uint256 lockId, uint256 additionalDuration)`

Extends an existing lock.

**Parameters**
- `lockId` — ID of lock to extend
- `additionalDuration` — Additional duration in seconds

**Returns**
- `bool` — True if successful

**Events**
- `LockExtended(lockId, newUnlockTime)`

**Example**
```
// Extend lock by 180 days
extendLock(1, 180 days)
```

#### `proposePermanentWithdrawal(uint256 lockId)`

Proposes withdrawal of permanent LP after lock expires.

**Parameters**
- `lockId` — ID of lock to withdraw

**Returns**
- `uint256` — Proposal ID

**Events**
- `WithdrawalProposed(proposalId, lockId, amount, executionTime)`

**Requirements**
- Lock must have expired
- No active proposal for this lock
- Caller must be owner or authorized

**Example**
```
// Propose withdrawal of permanent LP
proposePermanentWithdrawal(1)
```

### Flexible Liquidity Management

#### `proposeFlexibleWithdrawal(uint256 amount)`

Proposes withdrawal from flexible portion.

**Parameters**
- `amount` — LP amount to withdraw

**Returns**
- `uint256` — Proposal ID

**Events**
- `WithdrawalProposed(proposalId, amount, executionTime)`

**Requirements**
- Amount must not exceed daily limit
- Amount must not exceed available flexible LP
- No active proposal exists

**Example**
```
// Propose withdrawal of 500 LP
proposeFlexibleWithdrawal(500e18)
```

#### `executeWithdrawal(uint256 proposalId)`

Executes a withdrawal after timelock expires.

**Parameters**
- `proposalId` — ID of proposal to execute

**Returns**
- `bool` — True if successful

**Events**
- `WithdrawalExecuted(proposalId, amount)`

**Requirements**
- Timelock period must have expired
- Proposal must not be cancelled
- Amount must be available

**Example**
```
// Execute withdrawal
executeWithdrawal(1)
```

#### `cancelProposal(uint256 proposalId)`

Cancels a pending withdrawal proposal.

**Parameters**
- `proposalId` — ID of proposal to cancel

**Returns**
- `bool` — True if successful

**Events**
- `ProposalCancelled(proposalId)`

**Example**
```
// Cancel proposal
cancelProposal(1)
```

### Query Functions

#### `getLPBalance()`

Returns total LP balance.

**Returns**
- `uint256` — Total LP balance

#### `getPermanentLPBalance()`

Returns permanent LP balance.

**Returns**
- `uint256` — Permanent LP balance

#### `getFlexibleLPBalance()`

Returns flexible LP balance.

**Returns**
- `uint256` — Flexible LP balance

#### `getLockStatus(uint256 lockId)`

Returns status of a specific lock.

**Parameters**
- `lockId` — ID of lock

**Returns**
- `uint256` — Amount locked
- `uint256` — Unlock time
- `bool` — Is expired

#### `getDailyLimitStatus()`

Returns daily limit consumption.

**Returns**
- `uint256` — Daily limit
- `uint256` — Current consumption
- `uint256` — Remaining available

#### `getTimeUntilExecution(uint256 proposalId)`

Returns time until proposal can execute.

**Parameters**
- `proposalId` — ID of proposal

**Returns**
- `uint256` — Seconds until execution

## Liquidity Parameters

### Key Parameters

| Parameter | Value |
|-----------|-------|
| **Permanent Portion** | 85% of total LP |
| **Flexible Portion** | 15% of total LP |
| **Permanent Lock Duration** | 365+ days |
| **Daily Withdrawal Limit** | Configurable (e.g., 1% of flexible) |
| **Timelock Delay** | Configurable (e.g., 7 days) |

### Parameter Management

Parameters are managed through:
- Owner control for routine adjustments
- Multisig approval for critical changes
- Transparent process with event logging

## Events

### LiquidityLocked Event

```solidity
event LiquidityLocked(
    uint256 indexed lockId,
    uint256 amount,
    uint256 unlockTime
)
```

Emitted when LP is locked.

### LockExtended Event

```solidity
event LockExtended(
    uint256 indexed lockId,
    uint256 newUnlockTime
)
```

Emitted when a lock is extended.

### WithdrawalProposed Event

```solidity
event WithdrawalProposed(
    uint256 indexed proposalId,
    uint256 amount,
    uint256 executionTime
)
```

Emitted when a withdrawal is proposed.

### WithdrawalExecuted Event

```solidity
event WithdrawalExecuted(
    uint256 indexed proposalId,
    uint256 amount
)
```

Emitted when a withdrawal is executed.

### ProposalCancelled Event

```solidity
event ProposalCancelled(
    uint256 indexed proposalId
)
```

Emitted when a proposal is cancelled.

## Withdrawal Workflows

### Permanent LP Withdrawal

```
1. Lock Expires
   - 365+ day lock period complete
   - Withdrawal becomes possible
   - Expiration date transparent

2. Propose Withdrawal
   - Owner calls proposePermanentWithdrawal()
   - Proposal recorded on-chain
   - Timelock period begins

3. Timelock Period
   - Waiting period enforced
   - Community can monitor
   - Proposal can be cancelled

4. Execute Withdrawal
   - After timelock expires
   - Owner calls executeWithdrawal()
   - LP transferred

5. Completion
   - LP balance updated
   - Event logged on-chain
   - Transparency maintained
```

### Flexible LP Withdrawal

```
1. Check Daily Limit
   - Current consumption checked
   - Remaining limit calculated
   - Limit enforced by contract

2. Propose Withdrawal
   - Owner calls proposeFlexibleWithdrawal()
   - Amount within daily limit
   - Proposal recorded on-chain
   - Timelock period begins

3. Timelock Period
   - Waiting period enforced
   - Community can monitor
   - Proposal can be cancelled

4. Execute Withdrawal
   - After timelock expires
   - Owner calls executeWithdrawal()
   - LP transferred

5. Completion
   - LP balance updated
   - Daily consumption updated
   - Event logged on-chain
   - Transparency maintained
```

## Security Features

### Permanent Lock Protection

- 365+ day lock enforced by smart contract
- Cannot be bypassed
- Lock can only be extended, not shortened
- Withdrawal requires additional timelock

### Daily Limit Protection

- Daily withdrawal limit enforced
- Consumption tracked per day
- Resets daily
- Prevents large sudden withdrawals

### Timelock Protection

- All withdrawals require waiting period
- Community has time to react
- Proposals can be cancelled
- Prevents instant unauthorized withdrawals

### Event Logging

- All locks logged
- All proposals logged
- All executions logged
- Complete audit trail

## Liquidity Transparency

### Public Information

All liquidity information is publicly available:

✅ **LP Balance** — Current LP holdings  
✅ **Permanent Portion** — 85% portion details  
✅ **Flexible Portion** — 15% portion details  
✅ **Lock Status** — Lock expiration dates  
✅ **Daily Limits** — Daily withdrawal limits  
✅ **Pending Proposals** — Proposed withdrawals  
✅ **Withdrawal History** — Past withdrawals  

### Verification Methods

You can verify liquidity information:

1. **PolygonScan**
   - Check LP balance
   - View lock events
   - Monitor proposals
   - Track withdrawals

2. **Contract Functions**
   - Call getLPBalance()
   - Call getPermanentLPBalance()
   - Call getFlexibleLPBalance()
   - Call getLockStatus()
   - Call getDailyLimitStatus()

3. **Community Tools**
   - Use liquidity dashboards
   - Monitor LP metrics
   - Track lock status
   - Analyze patterns

## Integration Guide

### For Developers

**To Check LP Balance**
```solidity
uint256 balance = liquidityManager.getLPBalance();
```

**To Propose Withdrawal**
```solidity
liquidityManager.proposeFlexibleWithdrawal(amount);
```

**To Execute Withdrawal**
```solidity
liquidityManager.executeWithdrawal(proposalId);
```

**To Check Lock Status**
```solidity
(amount, unlockTime, isExpired) = liquidityManager.getLockStatus(lockId);
```

## Key Takeaways

1. **Dual protection** — Permanent lock + flexible limits
2. **Long-term security** — 85% locked for 365+ days
3. **Flexible access** — 15% available with daily limits
4. **Timelock enforcement** — All withdrawals require delays
5. **Complete transparency** — All operations logged on-chain

---

**Next:** Explore the [Security Model](../security-model/overview.md) to understand TCP's comprehensive security framework.
