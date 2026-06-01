---
title: Key Functions Reference
sidebar_position: 4
description: TCP smart contract functions and usage
---

# Key Functions Reference

This page documents key functions across TCP smart contracts.

## Token Contract Functions

### transfer(address to, uint256 amount)

Transfers tokens to recipient.

**Parameters**
- `to` — Recipient address
- `amount` — Amount to transfer

**Returns**
- `bool` — Success status

### approve(address spender, uint256 amount)

Approves spender to spend tokens.

**Parameters**
- `spender` — Spender address
- `amount` — Approved amount

**Returns**
- `bool` — Success status

### balanceOf(address account)

Returns token balance.

**Parameters**
- `account` — Account address

**Returns**
- `uint256` — Token balance

## Treasury Contract Functions

### proposeWithdrawal(address recipient, uint256 amount)

Proposes treasury withdrawal.

**Parameters**
- `recipient` — Recipient address
- `amount` — Withdrawal amount

**Returns**
- `uint256` — Proposal ID

### executeWithdrawal(uint256 proposalId)

Executes pending withdrawal.

**Parameters**
- `proposalId` — Proposal ID

**Returns**
- `bool` — Success status

### cancelProposal(uint256 proposalId)

Cancels pending proposal.

**Parameters**
- `proposalId` — Proposal ID

**Returns**
- `bool` — Success status

## Liquidity Manager Functions

### proposeWithdrawal(uint256 amount)

Proposes LP withdrawal.

**Parameters**
- `amount` — Withdrawal amount

**Returns**
- `uint256` — Proposal ID

### executeWithdrawal(uint256 proposalId)

Executes pending withdrawal.

**Parameters**
- `proposalId` — Proposal ID

**Returns**
- `bool` — Success status

### getLPBalance()

Returns LP balance.

**Returns**
- `uint256` — LP balance

## Staking Contract Functions

### stake(uint256 amount)

Stakes tokens.

**Parameters**
- `amount` — Stake amount

**Returns**
- `bool` — Success status

### unstake(uint256 amount)

Unstakes tokens.

**Parameters**
- `amount` — Unstake amount

**Returns**
- `bool` — Success status

### claimRewards()

Claims earned rewards.

**Returns**
- `uint256` — Reward amount

### getRewardBalance(address user)

Returns earned rewards.

**Parameters**
- `user` — User address

**Returns**
- `uint256` — Reward amount

## Burn Engine Functions

### burn(uint256 amount)

Burns tokens.

**Parameters**
- `amount` — Burn amount

**Returns**
- `bool` — Success status

### getTotalBurned()

Returns total burned.

**Returns**
- `uint256` — Total burned amount

---

**Next:** See [Integration Notes](./integration-notes.md) for integration guidance.
