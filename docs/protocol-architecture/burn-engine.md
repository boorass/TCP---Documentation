---
title: Burn Engine Contract
sidebar_position: 9
description: Technical details of the Burn Engine contract
---

# Burn Engine Contract

The **Burn Engine Contract** manages token supply reduction through burning mechanisms.

## Contract Purpose

The Burn Engine:
- Executes burn operations
- Tracks supply changes
- Logs burn events
- Maintains transparency
- Supports economic discipline

## Core Functions

### Burn Operations

#### `burn(uint256 amount)`

Burns tokens, removing them from circulation.

**Parameters**
- `amount` — Number of tokens to burn

**Returns**
- `bool` — True if successful

**Events**
- `TokensBurned(amount, newTotalSupply)`

**Requirements**
- Caller must be owner or authorized
- Amount must not exceed available balance
- Amount must be greater than zero

**Example**
```
// Burn 10,000 TCP
burn(10000e18)
```

#### `scheduleBurn(uint256 amount, uint256 timestamp)`

Schedules a burn for a future time.

**Parameters**
- `amount` — Number of tokens to burn
- `timestamp` — When to execute burn

**Returns**
- `uint256` — Burn ID

**Events**
- `BurnScheduled(burnId, amount, timestamp)`

**Example**
```
// Schedule burn for 30 days from now
scheduleBurn(10000e18, now + 30 days)
```

### Query Functions

#### `getTotalBurned()`

Returns total tokens burned.

**Returns**
- `uint256` — Total burned amount

#### `getBurnHistory(uint256 burnId)`

Returns details of a specific burn.

**Parameters**
- `burnId` — ID of burn

**Returns**
- `uint256` — Burn amount
- `uint256` — Burn timestamp
- `bool` — Is executed

## Events

### TokensBurned Event

```solidity
event TokensBurned(
    uint256 amount,
    uint256 newTotalSupply
)
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

Emitted when a burn is scheduled.

## Burn Parameters

### Key Parameters

| Parameter | Description |
|-----------|-------------|
| **Burn Amount** | Number of tokens to burn |
| **Burn Schedule** | When burns occur |
| **Burn Triggers** | Events that trigger burns |

## Integration Guide

### For Developers

**To Check Total Burned**
```solidity
uint256 totalBurned = burnEngine.getTotalBurned();
```

**To Execute Burn**
```solidity
burnEngine.burn(amount);
```

**To Schedule Burn**
```solidity
burnEngine.scheduleBurn(amount, timestamp);
```

## Key Takeaways

1. **Transparent burns** — All burns logged on-chain
2. **Economic discipline** — Supply reduction enforced
3. **Auditable** — Complete burn history available
4. **Scheduled burns** — Can be planned in advance

---

**Next:** Explore the [Security Model](../security-model/overview.md) to understand TCP's comprehensive security framework.
