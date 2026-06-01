---
title: TCP Token Contract
sidebar_position: 3
description: Technical details of the TCP Token contract
---

# TCP Token Contract

The **TCP Token Contract** is the foundation of the Protocol (TCP) ecosystem. It manages the TCP token and enables all token-based interactions.

## Contract Purpose

The TCP Token Contract:
- Manages token balances
- Processes transfers
- Handles approvals
- Emits transfer events
- Maintains immutable history

## Token Specifications

| Property | Value |
|----------|-------|
| **Token Name** | Protocol Token |
| **Ticker** | TCP |
| **Standard** | ERC-20 |
| **Decimals** | 18 |
| **Network** | Polygon |

## Core Functions

### Transfer Functions

#### `transfer(address to, uint256 amount)`

Transfers tokens from sender to recipient.

**Parameters**
- `to` — Recipient address
- `amount` — Number of tokens to transfer

**Returns**
- `bool` — True if successful

**Events**
- `Transfer(from, to, amount)`

**Example**
```
// Transfer 100 TCP to recipient
transfer(0x123..., 100e18)
```

#### `transferFrom(address from, address to, uint256 amount)`

Transfers tokens on behalf of another address (requires approval).

**Parameters**
- `from` — Sender address
- `to` — Recipient address
- `amount` — Number of tokens to transfer

**Returns**
- `bool` — True if successful

**Events**
- `Transfer(from, to, amount)`

**Example**
```
// Transfer 100 TCP from sender to recipient
transferFrom(0x456..., 0x123..., 100e18)
```

### Approval Functions

#### `approve(address spender, uint256 amount)`

Approves a spender to spend tokens on behalf of the sender.

**Parameters**
- `spender` — Address allowed to spend
- `amount` — Maximum amount allowed

**Returns**
- `bool` — True if successful

**Events**
- `Approval(owner, spender, amount)`

**Example**
```
// Approve staking contract to spend 1000 TCP
approve(0xStaking..., 1000e18)
```

#### `increaseAllowance(address spender, uint256 addedValue)`

Increases the allowance for a spender.

**Parameters**
- `spender` — Address to increase allowance for
- `addedValue` — Amount to increase by

**Returns**
- `bool` — True if successful

**Events**
- `Approval(owner, spender, newAmount)`

#### `decreaseAllowance(address spender, uint256 subtractedValue)`

Decreases the allowance for a spender.

**Parameters**
- `spender` — Address to decrease allowance for
- `subtractedValue` — Amount to decrease by

**Returns**
- `bool` — True if successful

**Events**
- `Approval(owner, spender, newAmount)`

### Query Functions

#### `balanceOf(address account)`

Returns the token balance of an address.

**Parameters**
- `account` — Address to check

**Returns**
- `uint256` — Token balance

**Example**
```
// Check balance of address
uint256 balance = balanceOf(0x123...)
```

#### `allowance(address owner, address spender)`

Returns the approved allowance for a spender.

**Parameters**
- `owner` — Token owner
- `spender` — Approved spender

**Returns**
- `uint256` — Approved amount

**Example**
```
// Check allowance for staking contract
uint256 allowed = allowance(0x123..., 0xStaking...)
```

#### `totalSupply()`

Returns the total token supply.

**Returns**
- `uint256` — Total supply

**Example**
```
// Check total supply
uint256 total = totalSupply()
```

#### `decimals()`

Returns the number of decimals.

**Returns**
- `uint8` — Number of decimals (18)

#### `name()`

Returns the token name.

**Returns**
- `string` — Token name

#### `symbol()`

Returns the token symbol.

**Returns**
- `string` — Token symbol (TCP)

## Events

### Transfer Event

```solidity
event Transfer(address indexed from, address indexed to, uint256 value)
```

Emitted when tokens are transferred.

**Parameters**
- `from` — Sender address
- `to` — Recipient address
- `value` — Amount transferred

### Approval Event

```solidity
event Approval(address indexed owner, address indexed spender, uint256 value)
```

Emitted when approval is granted.

**Parameters**
- `owner` — Token owner
- `spender` — Approved spender
- `value` — Approved amount

## Token Mechanics

### Transfer Process

```
1. Sender initiates transfer
   ↓
2. Contract checks sender balance
   ↓
3. Contract deducts from sender
   ↓
4. Contract adds to recipient
   ↓
5. Transfer event emitted
   ↓
6. Transaction recorded on-chain
```

### Approval Process

```
1. Owner approves spender
   ↓
2. Contract records allowance
   ↓
3. Approval event emitted
   ↓
4. Spender can now transfer up to approved amount
   ↓
5. Spender calls transferFrom()
   ↓
6. Contract checks allowance
   ↓
7. Contract deducts from owner
   ↓
8. Contract adds to recipient
   ↓
9. Transfer event emitted
```

## Security Features

### Balance Verification

- Balances are verified before transfer
- Insufficient balance prevents transfer
- Prevents double-spending

### Approval Mechanism

- Spender must be approved before transfer
- Approval amount is enforced
- Prevents unauthorized transfers

### Event Logging

- All transfers logged as events
- All approvals logged as events
- Complete audit trail on-chain

### Immutable History

- All transactions recorded on-chain
- Cannot be altered or deleted
- Permanent record of all operations

## Integration Guide

### For Wallet Users

**To Send Tokens**
1. Open wallet
2. Select "Send"
3. Enter recipient address
4. Enter amount
5. Confirm transaction

**To Approve Spending**
1. Open wallet
2. Select "Approve"
3. Enter spender address
4. Enter amount
5. Confirm transaction

### For Smart Contracts

**To Transfer Tokens**
```solidity
// Transfer tokens
IERC20(tokenAddress).transfer(recipient, amount);
```

**To Transfer on Behalf**
```solidity
// Transfer on behalf (requires approval)
IERC20(tokenAddress).transferFrom(owner, recipient, amount);
```

**To Approve Spending**
```solidity
// Approve spending
IERC20(tokenAddress).approve(spender, amount);
```

### For Exchanges

**To Accept Deposits**
1. Monitor Transfer events
2. Check recipient address
3. Verify amount
4. Credit user account

**To Send Withdrawals**
1. Call transfer() function
2. Specify recipient and amount
3. Wait for confirmation
4. Update user balance

## Verification on PolygonScan

You can verify token information on PolygonScan:

1. **Visit PolygonScan** — https://polygonscan.com/
2. **Search for token address** — Enter TCP token address
3. **View token details** — See name, symbol, decimals
4. **Check transfers** — View all token transfers
5. **Verify contract** — See verified source code

## Key Takeaways

1. **Standard ERC-20** — Fully compatible with standard interface
2. **Simple mechanics** — Easy to understand and use
3. **Transparent operations** — All transfers logged on-chain
4. **Secure design** — Built-in safeguards prevent abuse
5. **Auditable** — Complete history available on-chain

---

**Next:** Learn about the [Protocol Router](./protocol-router.md) that orchestrates contract interactions.
