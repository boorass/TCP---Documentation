---
title: Contract Summary
sidebar_position: 2
description: Overview of all TCP smart contracts and their roles
---

# Contract Summary

This page provides a summary of all TCP smart contracts and their primary functions.

## Contract Overview

| Contract | Role | Key Functions |
|----------|------|----------------|
| **TCP Token** | Token management | transfer, approve, balanceOf |
| **Protocol Router** | Orchestration | executeOperation, validateOperation |
| **Treasury** | Reserve management | proposeWithdrawal, executeWithdrawal |
| **Liquidity Manager** | LP protection | proposeWithdrawal, executeWithdrawal |
| **Staking** | Reward distribution | stake, unstake, claimRewards |
| **Burn Engine** | Supply reduction | burn, scheduleBurn |
| **Ecosystem Vault** | Allocations | allocateTokens, distributeTokens |
| **Vesting** | Time-locked distribution | createVesting, releaseTokens |

## Contract Interactions

```
User
  ↓
Token Contract ← → Staking Contract
  ↓                    ↓
Treasury Contract      Burn Engine
  ↓
Liquidity Manager
  ↓
Protocol Router
```

## Key Functions by Category

### Token Operations
- `transfer()` — Transfer tokens
- `approve()` — Approve spending
- `balanceOf()` — Check balance

### Treasury Operations
- `proposeWithdrawal()` — Propose withdrawal
- `executeWithdrawal()` — Execute withdrawal
- `cancelProposal()` — Cancel proposal

### Liquidity Operations
- `proposeWithdrawal()` — Propose withdrawal
- `executeWithdrawal()` — Execute withdrawal
- `getLPBalance()` — Check LP balance

### Staking Operations
- `stake()` — Stake tokens
- `unstake()` — Unstake tokens
- `claimRewards()` — Claim rewards

### Burn Operations
- `burn()` — Burn tokens
- `scheduleBurn()` — Schedule burn

---

**Next:** See [Events Reference](./events-reference.md) for event documentation.
