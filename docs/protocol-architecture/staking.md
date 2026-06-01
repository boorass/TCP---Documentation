---
title: Staking Contract
sidebar_position: 8
description: Technical details of the Staking contract and reward distribution
---

# Staking Contract

The **Staking Contract** enables users to stake TCP tokens and earn rewards.

## Contract Purpose

The Staking Contract:
- Accepts user stakes
- Calculates rewards
- Distributes rewards
- Tracks participation
- Maintains transparency

## Core Functions

### Staking Operations

#### `stake(uint256 amount)`

Stakes TCP tokens.

**Parameters**
- `amount` — Number of tokens to stake

**Returns**
- `bool` — True if successful

**Events**
- `Staked(user, amount)`

**Requirements**
- User must approve tokens first
- Amount must be greater than zero
- User must have sufficient balance

**Example**
```
// Stake 1000 TCP
stake(1000e18)
```

#### `unstake(uint256 amount)`

Unstakes TCP tokens.

**Parameters**
- `amount` — Number of tokens to unstake

**Returns**
- `bool` — True if successful

**Events**
- `Unstaked(user, amount)`

**Requirements**
- User must have staked tokens
- Amount must not exceed staked balance
- No lock-up period

**Example**
```
// Unstake 500 TCP
unstake(500e18)
```

#### `claimRewards()`

Claims earned rewards.

**Returns**
- `uint256` — Reward amount

**Events**
- `RewardsClaimed(user, amount)`

**Requirements**
- User must have earned rewards
- Rewards must be available

**Example**
```
// Claim rewards
claimRewards()
```

### Query Functions

#### `getStakeBalance(address user)`

Returns user's staked balance.

**Parameters**
- `user` — User address

**Returns**
- `uint256` — Staked amount

#### `getRewardBalance(address user)`

Returns user's earned rewards.

**Parameters**
- `user` — User address

**Returns**
- `uint256` — Reward amount

#### `getRewardRate()`

Returns current reward rate.

**Returns**
- `uint256` — Reward rate (e.g., 10 for 10% APY)

#### `getTotalStaked()`

Returns total tokens staked.

**Returns**
- `uint256` — Total staked amount

## Events

### Staked Event

```solidity
event Staked(
    address indexed user,
    uint256 amount
)
```

Emitted when tokens are staked.

### Unstaked Event

```solidity
event Unstaked(
    address indexed user,
    uint256 amount
)
```

Emitted when tokens are unstaked.

### RewardsClaimed Event

```solidity
event RewardsClaimed(
    address indexed user,
    uint256 amount
)
```

Emitted when rewards are claimed.

## Reward Calculation

### Reward Formula

```
User Reward = (User Stake / Total Stake) × Total Rewards
```

### Reward Accrual

Rewards accrue continuously:
- Calculated per block
- Updated on each interaction
- Claimable at any time

## Staking Parameters

### Key Parameters

| Parameter | Description |
|-----------|-------------|
| **Reward Rate** | Percentage return per period |
| **Minimum Stake** | Minimum tokens required (if applicable) |
| **Maximum Stake** | Maximum tokens per user (if applicable) |
| **Reward Pool** | Total tokens available for rewards |

## Integration Guide

### For Users

**To Stake**
1. Approve staking contract
2. Call stake() function
3. Tokens locked in contract
4. Rewards begin accruing

**To Claim Rewards**
1. Call claimRewards() function
2. Rewards transferred to wallet
3. Rewards reset to zero

**To Unstake**
1. Call unstake() function
2. Staked tokens returned
3. Remaining rewards can be claimed

### For Developers

**To Check Stake**
```solidity
uint256 stake = staking.getStakeBalance(user);
```

**To Check Rewards**
```solidity
uint256 rewards = staking.getRewardBalance(user);
```

**To Stake**
```solidity
staking.stake(amount);
```

## Key Takeaways

1. **Simple mechanism** — Easy to understand and use
2. **Flexible participation** — Stake and unstake anytime
3. **Transparent rewards** — Rewards calculated on-chain
4. **Auditable** — Complete history available for review

---

**Next:** Learn about the [Burn Engine](./burn-engine.md) that manages supply reduction.
