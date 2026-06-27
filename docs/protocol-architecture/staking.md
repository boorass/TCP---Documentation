---
title: "Staking Contract"
sidebar_position: 8
description: "Technical details of TCPStakingV2 contract and reward distribution"
sidebar_custom_props:
  icon: "code"
---

TCPStakingV2 is the official, production-ready staking contract for TCP Protocol. It enables users to stake TCP tokens and earn rewards through a transparent, on-chain mechanism.

## Contract Overview

### Purpose

The Staking Contract:
- Accepts user stakes of TCP tokens
- Calculates and distributes rewards
- Maintains transparent accounting
- Protects against overflow and double-payment
- Integrates with the protocol router

### Status

- **Contract**: TCPStakingV2
- **Network**: Polygon Mainnet
- **Status**: Production-ready and fully operational
- **Validation**: Comprehensive testing completed
- **Audits**: Internal audits passed

## Core Architecture

### Contract Structure

```
TCPStakingV2
├─ Staking Operations
│  ├─ stake()
│  ├─ unstake()
│  └─ claimRewards()
├─ Query Functions
│  ├─ getStakeBalance()
│  ├─ getRewardBalance()
│  ├─ getAvailableRewards()
│  └─ getTotalStaked()
├─ Admin Functions
│  ├─ fundRewards()
│  └─ verifyBalance()
└─ State Management
   ├─ rewardFunded
   ├─ rewardReserved
   ├─ totalStaked
   └─ userPositions
```

### State Variables

#### Reward Pool State

```solidity
uint256 public rewardFunded;      // Total rewards funded
uint256 public rewardReserved;    // Total rewards reserved for claims
uint256 constant MAX_REWARD_POOL = 70_000_000e18;  // 70M TCP maximum
```

#### Staking State

```solidity
uint256 public totalStaked;       // Total tokens staked by all users
mapping(address => uint256) public userStake;      // User stake amounts
mapping(address => uint256) public userRewards;    // User accrued rewards
```

#### Token Reference

```solidity
IERC20 public token;              // TCP token contract reference
```

## Core Functions

### Staking Operations

#### stake(uint256 amount)

Stakes TCP tokens and begins earning rewards.

**Parameters**
- `amount`: Number of tokens to stake (in wei, 18 decimals)

**Returns**
- `bool`: True if successful

**Events**
- `Staked(address indexed user, uint256 amount)`

**Requirements**
- User must approve tokens first
- Amount must be greater than zero
- User must have sufficient balance
- Reward pool must have capacity

**Logic**
```solidity
function stake(uint256 amount) external {
    require(amount > 0, "Amount must be greater than zero");
    
    // Calculate reward for this stake
    uint256 reward = calculateReward(amount);
    
    // Validate reward availability
    require(
        getAvailableRewards() >= reward,
        "Insufficient available rewards"
    );
    
    // Transfer tokens from user to contract
    require(
        token.transferFrom(msg.sender, address(this), amount),
        "Transfer failed"
    );
    
    // Update state
    userStake[msg.sender] += amount;
    totalStaked += amount;
    rewardReserved += reward;
    
    // Emit event
    emit Staked(msg.sender, amount);
}
```

**Example**
```solidity
// Stake 1000 TCP tokens
staking.stake(1000e18);
```

#### unstake(uint256 amount)

Unstakes TCP tokens and returns them to the user.

**Parameters**
- `amount`: Number of tokens to unstake (in wei, 18 decimals)

**Returns**
- `bool`: True if successful

**Events**
- `Unstaked(address indexed user, uint256 amount)`

**Requirements**
- User must have staked tokens
- Amount must not exceed staked balance
- No lock-up period

**Logic**
```solidity
function unstake(uint256 amount) external {
    require(amount > 0, "Amount must be greater than zero");
    require(
        userStake[msg.sender] >= amount,
        "Insufficient staked balance"
    );
    
    // Transfer tokens from contract to user
    require(
        token.transfer(msg.sender, amount),
        "Transfer failed"
    );
    
    // Update state
    userStake[msg.sender] -= amount;
    totalStaked -= amount;
    
    // Emit event
    emit Unstaked(msg.sender, amount);
}
```

**Example**
```solidity
// Unstake 500 TCP tokens
staking.unstake(500e18);
```

#### claimRewards()

Claims earned rewards and transfers them to the user.

**Returns**
- `uint256`: Reward amount claimed

**Events**
- `RewardsClaimed(address indexed user, uint256 amount)`

**Requirements**
- User must have accrued rewards
- Reward pool must have sufficient balance
- No double-payment risk

**Logic**
```solidity
function claimRewards() external returns (uint256) {
    uint256 rewards = userRewards[msg.sender];
    
    require(rewards > 0, "No rewards to claim");
    require(
        rewardFunded >= rewards,
        "Insufficient reward pool"
    );
    
    // Transfer rewards to user
    require(
        token.transfer(msg.sender, rewards),
        "Transfer failed"
    );
    
    // Update state
    userRewards[msg.sender] = 0;
    rewardFunded -= rewards;
    rewardReserved -= rewards;
    
    // Emit event
    emit RewardsClaimed(msg.sender, rewards);
    
    return rewards;
}
```

**Example**
```solidity
// Claim all earned rewards
uint256 claimed = staking.claimRewards();
```

### Query Functions

#### getStakeBalance(address user)

Returns the user's staked balance.

**Parameters**
- `user`: User address

**Returns**
- `uint256`: Staked amount (in wei)

**Example**
```solidity
uint256 stake = staking.getStakeBalance(msg.sender);
```

#### getRewardBalance(address user)

Returns the user's accrued rewards.

**Parameters**
- `user`: User address

**Returns**
- `uint256`: Reward amount (in wei)

**Example**
```solidity
uint256 rewards = staking.getRewardBalance(msg.sender);
```

#### getAvailableRewards()

Returns rewards available for new stakes.

**Returns**
- `uint256`: Available reward amount (in wei)

**Calculation**
```solidity
function getAvailableRewards() public view returns (uint256) {
    return rewardFunded - rewardReserved;
}
```

**Example**
```solidity
uint256 available = staking.getAvailableRewards();
```

#### getTotalStaked()

Returns total tokens staked by all users.

**Returns**
- `uint256`: Total staked amount (in wei)

**Example**
```solidity
uint256 total = staking.getTotalStaked();
```

### Admin Functions

#### fundRewards(uint256 amount)

Funds the reward pool (owner-only).

**Parameters**
- `amount`: Number of tokens to fund (in wei)

**Requirements**
- Caller must be owner (multisig)
- Total funded cannot exceed 70,000,000 TCP
- Tokens must be transferred successfully

**Logic**
```solidity
function fundRewards(uint256 amount) external onlyOwner {
    require(
        rewardFunded + amount <= MAX_REWARD_POOL,
        "Exceeds reward pool maximum"
    );
    
    require(
        token.transferFrom(msg.sender, address(this), amount),
        "Transfer failed"
    );
    
    rewardFunded += amount;
    
    emit RewardsFunded(amount);
}
```

**Example**
```solidity
// Fund 70,000,000 TCP
staking.fundRewards(70_000_000e18);
```

#### verifyBalance()

Verifies that contract balance matches accounting state.

**Returns**
- `bool`: True if balance matches expected state

**Logic**
```solidity
function verifyBalance() external view returns (bool) {
    uint256 expectedBalance = totalStaked + rewardFunded;
    uint256 actualBalance = token.balanceOf(address(this));
    return actualBalance == expectedBalance;
}
```

## Events

### Staked Event

```solidity
event Staked(address indexed user, uint256 amount);
```

Emitted when tokens are staked.

**Parameters**
- `user`: User address
- `amount`: Staked amount

### Unstaked Event

```solidity
event Unstaked(address indexed user, uint256 amount);
```

Emitted when tokens are unstaked.

**Parameters**
- `user`: User address
- `amount`: Unstaked amount

### RewardsClaimed Event

```solidity
event RewardsClaimed(address indexed user, uint256 amount);
```

Emitted when rewards are claimed.

**Parameters**
- `user`: User address
- `amount`: Claimed reward amount

### RewardsFunded Event

```solidity
event RewardsFunded(uint256 amount);
```

Emitted when rewards are funded.

**Parameters**
- `amount`: Funded amount

## Reward Calculation

### Proportional Distribution

Rewards are calculated proportionally based on stake share:

```
User Reward = (User Stake / Total Stake) × Total Reward Rate
```

### Continuous Accrual

Rewards accrue continuously per block:

```
Block Reward = Total Reward Rate / Blocks Per Year
User Block Reward = (User Stake / Total Stake) × Block Reward
```

### Reward Reservation

When a user stakes, their calculated reward is immediately reserved:

```solidity
uint256 reward = calculateReward(amount);
rewardReserved += reward;
```

This prevents double-payment and ensures accurate accounting.

## Reward Pool Management

### Pool Specifications

| Parameter | Value |
|-----------|-------|
| **Maximum Pool** | 70,000,000 TCP |
| **Current Funding** | 70,000,000 TCP |
| **Overflow Protection** | Enabled |
| **Refunding** | Via governance |

### Overflow Prevention

The contract prevents funding beyond the maximum:

```solidity
require(
    rewardFunded + amount <= MAX_REWARD_POOL,
    "Exceeds reward pool maximum"
);
```

### Pool State Tracking

```
rewardFunded (70,000,000 TCP)
├─ rewardReserved (reserved for claims)
└─ Available (rewardFunded - rewardReserved)
```

## Security Features

### Double-Payment Prevention

The contract prevents double-payment through:

1. **Reward Reservation**: Rewards reserved when calculated
2. **State Reset**: User reward balance reset after claim
3. **Pool Tracking**: rewardReserved decreases with claims

### Overflow Protection

The contract prevents reward pool overflow:

```solidity
require(
    rewardFunded + amount <= MAX_REWARD_POOL,
    "Exceeds reward pool maximum"
);
```

### Owner Validation

Only the owner (multisig) can fund rewards:

```solidity
function fundRewards(uint256 amount) external onlyOwner {
    // ...
}
```

### Balance Verification

The contract maintains invariants:

```
Invariant 1: rewardFunded <= MAX_REWARD_POOL
Invariant 2: rewardReserved <= rewardFunded
Invariant 3: Contract Balance = totalStaked + rewardFunded
```

## Integration Guide

### For Users

**To Stake**
1. Approve staking contract
2. Call `stake(amount)`
3. Rewards begin accruing

**To Claim Rewards**
1. Call `claimRewards()`
2. Rewards transferred to wallet

**To Unstake**
1. Call `unstake(amount)`
2. Tokens returned to wallet

### For Developers

**Check Stake**
```solidity
uint256 stake = staking.getStakeBalance(user);
```

**Check Rewards**
```solidity
uint256 rewards = staking.getRewardBalance(user);
```

**Stake Tokens**
```solidity
staking.stake(amount);
```

**Claim Rewards**
```solidity
staking.claimRewards();
```

**Unstake Tokens**
```solidity
staking.unstake(amount);
```

## Testing and Validation

### Validation Completed

✅ **Configuration testing**: Router and token setup verified  
✅ **Functional testing**: All operations validated  
✅ **Reward pool testing**: Overflow protection confirmed  
✅ **Safe simulations**: Multisig governance validated  
✅ **Mainnet validation**: Production network testing complete  

### Test Results

All tests passed:
- Staking operations: ✓
- Reward calculation: ✓
- Claiming mechanism: ✓
- Unstaking process: ✓
- Overflow prevention: ✓
- State consistency: ✓

## Key Takeaways

1. **Official contract**: TCPStakingV2 is the production-ready implementation
2. **Fully tested**: Comprehensive validation on Polygon Mainnet
3. **Secure design**: Multiple layers of protection
4. **Transparent**: All operations on-chain and verifiable
5. **Flexible**: Stake and unstake anytime without lock-up

## See also

- [Introduction to TCP Staking](/docs/staking-rewards/introduction)
- [How Staking Works](/docs/staking-rewards/how-staking-works)
- [Reward Distribution Logic](/docs/staking-rewards/reward-distribution-logic)
- [Reward Funding](/docs/staking-rewards/reward-funding)
- [User Flows](/docs/staking-rewards/user-flows)
- [Technical Validation](/docs/staking-rewards/technical-validation)
