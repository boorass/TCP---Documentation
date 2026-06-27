---
title: "Reward Funding"
sidebar_position: 5
description: "How the reward pool is funded, managed, and protected in TCPStakingV2"
sidebar_custom_props:
  icon: "credit-card"
---

The TCP staking reward system is powered by a fixed reward pool of 70,000,000 TCP tokens. This document explains how the reward pool is funded, managed, and protected against overflow.

## Reward Pool Overview

### Pool Specifications

| Parameter | Value | Notes |
|-----------|-------|-------|
| **Maximum Pool Size** | 70,000,000 TCP | Hard limit, enforced by contract |
| **Current Funding** | 70,000,000 TCP | Fully funded |
| **Funding Status** | Complete | Ready for distribution |
| **Protection** | Overflow prevention | Prevents exceeding maximum |

### Pool Purpose

The reward pool serves as:

- **Reward source**: Funds all user rewards
- **Sustainability guarantee**: Ensures long-term reward viability
- **Transparent allocation**: Fixed, verifiable amount
- **Protocol commitment**: Demonstrates protocol support for staking

## Funding Mechanism

### How Funding Works

The reward pool is funded through the `fundRewards()` function:

```solidity
function fundRewards(uint256 amount) external onlyOwner {
    // Validation: Check pool capacity
    require(
        rewardFunded + amount <= MAX_REWARD_POOL,
        "Exceeds reward pool maximum"
    );
    
    // Transfer tokens from owner to contract
    require(
        token.transferFrom(msg.sender, address(this), amount),
        "Transfer failed"
    );
    
    // Update internal accounting
    rewardFunded += amount;
    
    // Emit event for transparency
    emit RewardsFunded(amount);
}
```

### Funding Process

```
1. Authorization Check
   └─ Only owner (multisig) can fund

2. Capacity Validation
   ├─ Current funded: rewardFunded
   ├─ New amount: fundAmount
   ├─ Total: rewardFunded + fundAmount
   └─ Check: Total <= 70,000,000

3. Token Transfer
   ├─ Transfer from owner to contract
   ├─ Update contract balance
   └─ Verify transfer success

4. State Update
   ├─ Increase rewardFunded
   ├─ Update available rewards
   └─ Maintain invariants

5. Event Emission
   └─ RewardsFunded(amount) emitted
```

### Funding Example

```
Scenario: Fund 70,000,000 TCP

Step 1: Authorization
├─ Caller: Multisig address
├─ Permission: Owner ✓
└─ Status: Authorized

Step 2: Validation
├─ Current rewardFunded: 0
├─ Funding amount: 70,000,000
├─ Total: 70,000,000
├─ Maximum: 70,000,000
├─ Check: 70,000,000 <= 70,000,000 ✓
└─ Status: Validation passed

Step 3: Transfer
├─ From: Owner wallet
├─ To: Staking contract
├─ Amount: 70,000,000 TCP
└─ Status: Transfer successful

Step 4: State Update
├─ rewardFunded: 0 → 70,000,000
├─ Contract balance: 0 → 70,000,000
└─ Status: State updated

Step 5: Event
└─ RewardsFunded(70,000,000) emitted
```

## Overflow Protection

### The Mechanism

The contract prevents funding that would exceed the maximum pool:

```solidity
require(
    rewardFunded + fundAmount <= MAX_REWARD_POOL,
    "Exceeds reward pool maximum"
);
```

### Why Overflow Protection Matters

Overflow protection ensures:

1. **Predictable rewards**: Pool size is fixed and known
2. **Fair distribution**: All rewards come from the same pool
3. **Prevents accidents**: Protects against funding mistakes
4. **Maintains invariants**: Keeps accounting consistent
5. **User confidence**: Transparent, verifiable limits

### Overflow Prevention Example

```
Scenario 1: Attempt to exceed maximum

Current State:
├─ rewardFunded: 101 TCP
├─ Funding attempt: 69,999,900 TCP
└─ Total would be: 70,000,001 TCP

Validation:
├─ 70,000,001 > 70,000,000 ✗
└─ Status: Rejected

Result:
├─ Transaction reverted
├─ Error: "Exceeds reward pool maximum"
└─ State unchanged
```

```
Scenario 2: Correct funding

Current State:
├─ rewardFunded: 101 TCP
├─ Funding amount: 69,999,899 TCP
└─ Total: 70,000,000 TCP

Validation:
├─ 70,000,000 <= 70,000,000 ✓
└─ Status: Accepted

Result:
├─ Funding successful
├─ rewardFunded: 101 → 70,000,000
└─ State updated
```

## Pool State Tracking

### Core Variables

The contract tracks the pool state through three variables:

#### rewardFunded

**Definition**: Total TCP tokens registered as available for rewards

**Purpose**: Tracks total pool funding

**Updates**: Increases when funded, decreases when claimed

**Example**
```
Initial: 0 TCP
After funding: 70,000,000 TCP
After claims: 69,999,975 TCP (if 25 TCP claimed)
```

#### rewardReserved

**Definition**: Total TCP tokens reserved for pending claims

**Purpose**: Tracks rewards held for claims

**Updates**: Increases when rewards calculated, decreases when claimed

**Example**
```
Initial: 0 TCP
After stake: 0.8 TCP (reward reserved)
After claim: 0 TCP (reward claimed)
```

#### Available Rewards

**Definition**: Rewards available for new stakes

**Calculation**
```
Available = rewardFunded - rewardReserved
```

**Example**
```
rewardFunded: 70,000,000 TCP
rewardReserved: 100 TCP
Available: 69,999,900 TCP
```

### State Relationships

```
Reward Pool State:

rewardFunded (70,000,000 TCP)
    ├─ rewardReserved (100 TCP)
    │   └─ Held for pending claims
    └─ Available (69,999,900 TCP)
        └─ Available for new stakes
```

## Pool Capacity Management

### Capacity Calculation

The remaining capacity in the pool is calculated as:

```
Remaining Capacity = MAX_REWARD_POOL - rewardFunded
```

### Capacity Example

```
Scenario: Check remaining capacity

Current State:
├─ MAX_REWARD_POOL: 70,000,000 TCP
├─ rewardFunded: 101 TCP
└─ Remaining: 69,999,899 TCP

Interpretation:
├─ Pool is 0.14% full
├─ Can fund up to 69,999,899 more TCP
└─ Status: Plenty of capacity
```

### Capacity Monitoring

The contract provides functions to check capacity:

```solidity
function getRemainingCapacity() external view returns (uint256) {
    return MAX_REWARD_POOL - rewardFunded;
}

function getAvailableRewards() external view returns (uint256) {
    return rewardFunded - rewardReserved;
}

function getPoolStatus() external view returns (
    uint256 funded,
    uint256 reserved,
    uint256 available,
    uint256 remaining
) {
    return (
        rewardFunded,
        rewardReserved,
        rewardFunded - rewardReserved,
        MAX_REWARD_POOL - rewardFunded
    );
}
```

## Funding Authorization

### Owner-Only Funding

Only the contract owner (multisig) can fund the reward pool:

```solidity
function fundRewards(uint256 amount) external onlyOwner {
    // ...
}
```

### Multisig Governance

Funding operations require multisig approval:

```
Funding Workflow:

1. Proposal
   └─ Multisig member proposes funding

2. Review
   ├─ Other members review proposal
   ├─ Verify amount and purpose
   └─ Check pool capacity

3. Approval
   ├─ Required signers approve
   └─ Threshold reached

4. Execution
   ├─ Funding transaction executed
   ├─ Tokens transferred
   └─ State updated

5. Verification
   ├─ Check rewardFunded updated
   ├─ Verify contract balance
   └─ Confirm event emitted
```

### Authorization Benefits

Owner-only funding ensures:

- **Controlled additions**: Only authorized parties can fund
- **Governance alignment**: Multisig approval required
- **Accountability**: All funding is traceable
- **Security**: Prevents unauthorized funding
- **Transparency**: All funding is on-chain

## Pool Sustainability

### Funding Strategy

The reward pool is designed for sustainability:

```
Pool Funding:
├─ Initial funding: 70,000,000 TCP
├─ Fixed size: No automatic refills
├─ Depletion: Decreases with claims
└─ Governance: Multisig can refund if needed
```

### Reward Sustainability

The fixed pool ensures:

1. **Predictable rewards**: Pool size is known
2. **Fair distribution**: All rewards from same pool
3. **Long-term viability**: Sufficient for extended operation
4. **Transparent accounting**: All claims tracked
5. **Governance control**: Multisig can adjust if needed

### Pool Depletion Scenario

```
Scenario: Pool depletion over time

Year 1:
├─ Starting pool: 70,000,000 TCP
├─ Claims: 5,000,000 TCP
└─ Remaining: 65,000,000 TCP

Year 2:
├─ Starting pool: 65,000,000 TCP
├─ Claims: 5,000,000 TCP
└─ Remaining: 60,000,000 TCP

Year 3:
├─ Starting pool: 60,000,000 TCP
├─ Claims: 5,000,000 TCP
└─ Remaining: 55,000,000 TCP

Governance Options:
├─ Continue with remaining pool
├─ Refund pool if needed
└─ Adjust reward rates
```

## Pool Verification

### Balance Verification

The contract maintains an invariant:

```
Invariant: Contract Balance >= rewardFunded + totalStaked
```

This ensures:
- All funded rewards are in the contract
- All staked tokens are in the contract
- No tokens are lost or missing

### Verification Function

```solidity
function verifyPoolBalance() external view returns (bool) {
    uint256 expectedBalance = rewardFunded + totalStaked;
    uint256 actualBalance = token.balanceOf(address(this));
    return actualBalance == expectedBalance;
}
```

### Verification Example

```
Contract State:
├─ rewardFunded: 70,000,000 TCP
├─ totalStaked: 100,000 TCP
├─ Expected balance: 70,100,000 TCP
└─ Actual balance: 70,100,000 TCP

Verification:
├─ Expected == Actual ✓
└─ Status: Verified
```

## Events and Transparency

### RewardsFunded Event

```solidity
event RewardsFunded(uint256 amount);
```

Emitted when rewards are funded:

```
Event: RewardsFunded
├─ Amount: 70,000,000 TCP
├─ Block: 50,000,003
├─ Transaction: 0xabcd...
└─ Status: Recorded on-chain
```

### Event Tracking

All funding events are queryable:

```
Query: All RewardsFunded events

Event 1:
├─ Amount: 101 TCP
├─ Block: 50,000,003
└─ Timestamp: 2024-01-15 10:00:00

Event 2:
├─ Amount: 69,999,899 TCP
├─ Block: 50,000,006
└─ Timestamp: 2024-01-15 10:05:00

Total Funded: 70,000,000 TCP
```

## Key Takeaways

1. **Fixed pool**: 70,000,000 TCP maximum
2. **Overflow protection**: Prevents exceeding maximum
3. **Owner-only funding**: Multisig governance required
4. **Transparent tracking**: All funding on-chain
5. **Sustainable design**: Sufficient for long-term operation
6. **Verifiable state**: Balance invariants maintained

## Best Practices

### For Protocol Governance

✅ **Monitor pool status** regularly  
✅ **Plan refunding** if pool depletes  
✅ **Verify balance** periodically  
✅ **Track claims** over time  
✅ **Adjust rates** if needed  

### For Users

✅ **Check available rewards** before staking  
✅ **Monitor pool status** over time  
✅ **Claim rewards** periodically  
✅ **Understand sustainability** of rewards  
✅ **Stay informed** of governance updates  

## See also

- [How Staking Works](/docs/staking-rewards/how-staking-works)
- [Reward Distribution Logic](/docs/staking-rewards/reward-distribution-logic)
- [Technical Validation](/docs/staking-rewards/technical-validation)
- [TCPStakingV2 Contract](/docs/protocol-architecture/staking)
- [Governance Operations](/docs/category/governance-operations)
