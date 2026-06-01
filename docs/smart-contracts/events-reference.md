---
title: Events Reference
sidebar_position: 3
description: TCP smart contract events and logging
---

# Events Reference

This page documents all important events emitted by TCP smart contracts.

## Token Events

### Transfer Event

```solidity
event Transfer(address indexed from, address indexed to, uint256 value)
```

Emitted when tokens are transferred.

### Approval Event

```solidity
event Approval(address indexed owner, address indexed spender, uint256 value)
```

Emitted when approval is granted.

## Treasury Events

### WithdrawalProposed Event

```solidity
event WithdrawalProposed(
    uint256 indexed proposalId,
    address indexed recipient,
    uint256 amount,
    uint256 executionTime
)
```

Emitted when withdrawal is proposed.

### WithdrawalExecuted Event

```solidity
event WithdrawalExecuted(
    uint256 indexed proposalId,
    address indexed recipient,
    uint256 amount
)
```

Emitted when withdrawal is executed.

### ProposalCancelled Event

```solidity
event ProposalCancelled(
    uint256 indexed proposalId,
    string reason
)
```

Emitted when proposal is cancelled.

## Liquidity Events

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

Emitted when lock is extended.

## Staking Events

### Staked Event

```solidity
event Staked(address indexed user, uint256 amount)
```

Emitted when tokens are staked.

### Unstaked Event

```solidity
event Unstaked(address indexed user, uint256 amount)
```

Emitted when tokens are unstaked.

### RewardsClaimed Event

```solidity
event RewardsClaimed(address indexed user, uint256 amount)
```

Emitted when rewards are claimed.

## Burn Events

### TokensBurned Event

```solidity
event TokensBurned(uint256 amount, uint256 newTotalSupply)
```

Emitted when tokens are burned.

### BurnScheduled Event

```solidity
event BurnScheduled(
    uint256 indexed burnId,
    uint256 amount,
    uint256 timestamp
)
```

Emitted when burn is scheduled.

## Monitoring Events

You can monitor events on PolygonScan:

1. **Visit PolygonScan** — https://polygonscan.com/
2. **Search for contract** — Enter contract address
3. **View events** — See all contract events
4. **Filter events** — Filter by event type
5. **Export data** — Export event data

---

**Next:** See [Key Functions Reference](./key-functions-reference.md) for function documentation.
