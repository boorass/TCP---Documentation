---
title: Ecosystem Vault Contract
sidebar_position: 7
description: Technical details of the Ecosystem Vault contract
---

# Ecosystem Vault Contract

The **Ecosystem Vault Contract** manages allocations for ecosystem development, partnerships, and community initiatives.

## Contract Purpose

The Ecosystem Vault:
- Holds ecosystem allocations
- Distributes to ecosystem projects
- Tracks allocation usage
- Maintains transparency
- Supports ecosystem growth

## Core Functions

### Allocation Management

#### `allocateTokens(address recipient, uint256 amount, string memory purpose)`

Allocates tokens for a specific purpose.

**Parameters**
- `recipient` — Address to receive allocation
- `amount` — Allocation amount
- `purpose` — Purpose of allocation

**Returns**
- `uint256` — Allocation ID

**Events**
- `TokensAllocated(allocationId, recipient, amount, purpose)`

**Requirements**
- Caller must be owner or authorized
- Amount must not exceed available balance
- Purpose must be specified

#### `distributeTokens(uint256 allocationId)`

Distributes allocated tokens.

**Parameters**
- `allocationId` — ID of allocation to distribute

**Returns**
- `bool` — True if successful

**Events**
- `TokensDistributed(allocationId, recipient, amount)`

**Requirements**
- Allocation must exist
- Allocation must not be distributed
- Recipient must be valid

#### `getBalance()`

Returns vault balance.

**Returns**
- `uint256` — Current balance

#### `getAllocationStatus(uint256 allocationId)`

Returns status of an allocation.

**Parameters**
- `allocationId` — ID of allocation

**Returns**
- `address` — Recipient address
- `uint256` — Allocation amount
- `bool` — Is distributed
- `string` — Purpose

## Events

### TokensAllocated Event

```solidity
event TokensAllocated(
    uint256 indexed allocationId,
    address indexed recipient,
    uint256 amount,
    string purpose
)
```

Emitted when tokens are allocated.

### TokensDistributed Event

```solidity
event TokensDistributed(
    uint256 indexed allocationId,
    address indexed recipient,
    uint256 amount
)
```

Emitted when tokens are distributed.

## Key Takeaways

1. **Structured allocation** — Clear purpose for each allocation
2. **Transparent distribution** — All allocations logged on-chain
3. **Ecosystem support** — Resources for ecosystem development
4. **Auditable** — Complete history available for review

---

**Next:** Learn about the [Staking Contract](./staking.md) that distributes rewards.
