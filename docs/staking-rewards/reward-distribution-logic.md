---
title: "Reward Distribution Logic"
sidebar_position: 3
description: "Technical explanation of how rewards are calculated, reserved, and distributed in TCPStakingV2"
sidebar_custom_props:
  icon: "chart-line"
---

TCPStakingV2 implements a sophisticated reward distribution system that ensures fair allocation, prevents double-payment, and maintains transparent accounting. This document explains the technical mechanics of reward calculation and distribution.

## Reward System Architecture

The reward system operates through three core components:

```
Reward Pool (70M TCP)
        ↓
Reward Accounting
├─ rewardFunded: Total rewards registered
├─ rewardReserved: Rewards held for claims
└─ Available: rewardFunded - rewardReserved
        ↓
Reward Distribution
├─ Continuous accrual per block
├─ Proportional to stake share
└─ Claimable on demand
```

## Core Accounting Variables

### rewardFunded

**Definition**: Total TCP tokens registered as available for rewards.

**Purpose**: Tracks the total reward pool that has been funded into the contract.

**Updates**: Increases when rewards are funded, decreases when claimed.

**Example**
```
Initial: rewardFunded = 0
After funding 70M TCP: rewardFunded = 70,000,000
After claims: rewardFunded = 69,999,975 (if 25 TCP claimed)
```

### rewardReserved

**Definition**: Total TCP tokens reserved for pending claims.

**Purpose**: Tracks rewards that have been calculated but not yet claimed.

**Updates**: Increases when rewards are calculated, decreases when claimed.

**Example**
```
User stakes 1,000 TCP
Reward calculated: 25 TCP
rewardReserved increases: 0 → 25

User claims rewards
rewardReserved decreases: 25 → 0
```

### Available Rewards

**Definition**: Rewards available for new stakes.

**Calculation**
```
Available = rewardFunded - rewardReserved
```

**Purpose**: Ensures new stakes don't exceed available rewards.

**Example**
```
rewardFunded = 70,000,000 TCP
rewardReserved = 100 TCP
Available = 69,999,900 TCP
```

## Reward Calculation

### Proportional Reward Formula

Rewards are calculated proportionally based on each user's share of total staked tokens:

```
User Reward = (User Stake / Total Stake) × Total Reward Rate
```

### Per-Block Accrual

Rewards accrue continuously, calculated per block:

```
Block Reward = Total Reward Rate / Blocks Per Year
User Block Reward = (User Stake / Total Stake) × Block Reward
```

### Continuous Accrual Example

```
Scenario:
├─ User Stake: 1,000 TCP
├─ Total Stake: 100,000 TCP
├─ Annual Reward Rate: 10%
└─ Blocks Per Year: ~7,884,000 (Polygon)

Calculation:
├─ User Share: 1,000 / 100,000 = 1%
├─ Annual Reward: 100,000 × 10% = 10,000 TCP
├─ User Annual Reward: 10,000 × 1% = 100 TCP
├─ Per-Block Reward: 100 / 7,884,000 ≈ 0.0000127 TCP
└─ Per-Day Reward: 100 / 365 ≈ 0.274 TCP
```

## Reward Reservation Process

### When Rewards Are Reserved

Rewards are reserved (added to `rewardReserved`) when:

1. **User stakes tokens**
   - Reward calculated for the stake
   - Reward reserved immediately
   - Prevents double-allocation

2. **Rewards are claimed**
   - Accrued rewards transferred to user
   - Reserved amount decreases
   - Available rewards updated

### Reservation Example

```
Step 1: User stakes 1,000 TCP
├─ Reward calculated: 25 TCP
├─ rewardReserved: 0 → 25
└─ Available: 69,999,975 → 69,999,950

Step 2: User claims rewards
├─ 25 TCP transferred to user
├─ rewardReserved: 25 → 0
└─ Available: 69,999,950 → 69,999,975
```

## Reward Pool Management

### Pool Capacity

The reward pool has a maximum capacity:

```
Maximum Reward Pool = 70,000,000 TCP
```

### Overflow Protection

The contract prevents funding that would exceed the maximum:

```solidity
require(
    rewardFunded + fundAmount <= MAX_REWARD_POOL,
    "Exceeds reward pool maximum"
);
```

### Pool State Tracking

The contract maintains:

| Variable | Purpose | Example |
|----------|---------|---------|
| **rewardFunded** | Total funded | 70,000,000 TCP |
| **rewardReserved** | Reserved for claims | 100 TCP |
| **Available** | Available for new stakes | 69,999,900 TCP |
| **Contract Balance** | Actual TCP in contract | 140,000,100 TCP |

### Pool Invariants

The system maintains critical invariants:

```
Invariant 1: rewardFunded <= MAX_REWARD_POOL
Invariant 2: rewardReserved <= rewardFunded
Invariant 3: Available = rewardFunded - rewardReserved
Invariant 4: Contract Balance >= rewardFunded + totalStaked
```

## Claim Processing

### Claim Workflow

```
1. User initiates claim
        ↓
2. Contract calculates accrued rewards
        ↓
3. Contract validates availability
   ├─ Check: Rewards available
   ├─ Check: Pool has balance
   └─ Check: No double-payment
        ↓
4. Contract transfers rewards
        ↓
5. Contract updates state
   ├─ Decrease rewardReserved
   ├─ Decrease rewardFunded
   └─ Update user reward balance
        ↓
6. Contract emits event
```

### Claim Validation

Before processing a claim, the contract validates:

```solidity
// Validation 1: User has accrued rewards
require(userRewards > 0, "No rewards to claim");

// Validation 2: Reward pool has sufficient balance
require(
    rewardFunded >= userRewards,
    "Insufficient reward pool"
);

// Validation 3: Contract has sufficient balance
require(
    token.balanceOf(address(this)) >= userRewards,
    "Insufficient contract balance"
);

// Validation 4: No double-payment
require(
    rewardReserved >= userRewards,
    "Invalid reward state"
);
```

### Claim State Update

After successful claim:

```
rewardFunded -= claimedAmount
rewardReserved -= claimedAmount
userRewards = 0
contractBalance -= claimedAmount
```

## Double-Payment Prevention

### The Risk

Without proper accounting, a user could claim the same rewards multiple times:

```
Scenario (PREVENTED):
├─ User accrues 25 TCP
├─ User claims 25 TCP (first claim)
├─ User claims 25 TCP again (second claim) ← PREVENTED
└─ User receives 50 TCP instead of 25
```

### Prevention Mechanism

TCPStakingV2 prevents double-payment through:

1. **Reward Reservation**
   - Rewards reserved when calculated
   - Only reserved amount can be claimed
   - Prevents claiming more than reserved

2. **State Reset**
   - User reward balance reset to zero after claim
   - Prevents re-claiming same rewards
   - Requires new accrual before next claim

3. **Pool Tracking**
   - rewardReserved decreases with each claim
   - Prevents claiming from empty pool
   - Maintains invariant: rewardReserved <= rewardFunded

### Prevention Example

```
Step 1: Stake 1,000 TCP
├─ Reward calculated: 25 TCP
├─ rewardReserved: 0 → 25
└─ userRewards: 0 → 25

Step 2: Claim 25 TCP
├─ Transfer 25 TCP to user
├─ rewardReserved: 25 → 0
├─ userRewards: 25 → 0
└─ Status: Claim successful

Step 3: Attempt second claim
├─ userRewards: 0 (reset in step 2)
├─ Validation fails: "No rewards to claim"
└─ Status: Claim rejected
```

## Reward Pool Funding

### Funding Process

The reward pool is funded through:

```
1. Initial funding
   └─ 70,000,000 TCP transferred to contract

2. Funding validation
   ├─ Check: Amount does not exceed maximum
   ├─ Check: Caller is authorized
   └─ Check: Tokens are transferred

3. State update
   ├─ rewardFunded += fundAmount
   └─ Contract balance updated

4. Event emission
   └─ RewardsFunded(amount) emitted
```

### Funding Validation

```solidity
function fundRewards(uint256 amount) external onlyOwner {
    // Validation 1: Amount does not exceed maximum
    require(
        rewardFunded + amount <= MAX_REWARD_POOL,
        "Exceeds reward pool maximum"
    );
    
    // Validation 2: Transfer tokens
    require(
        token.transferFrom(msg.sender, address(this), amount),
        "Transfer failed"
    );
    
    // Validation 3: Update state
    rewardFunded += amount;
    
    // Validation 4: Emit event
    emit RewardsFunded(amount);
}
```

### Funding Example

```
Scenario: Fund 70,000,000 TCP

Step 1: Validation
├─ Current rewardFunded: 0
├─ New amount: 70,000,000
├─ Total: 70,000,000 <= 70,000,000 ✓
└─ Status: Validation passed

Step 2: Transfer
├─ Transfer 70,000,000 TCP from owner to contract
├─ Owner balance: 100,000,000 → 30,000,000
└─ Contract balance: 0 → 70,000,000

Step 3: State Update
├─ rewardFunded: 0 → 70,000,000
├─ rewardReserved: 0
└─ Available: 70,000,000

Step 4: Event
└─ RewardsFunded(70,000,000) emitted
```

## Reward Pool Overflow Prevention

### The Mechanism

The contract prevents funding that would exceed the maximum pool:

```solidity
require(
    rewardFunded + fundAmount <= MAX_REWARD_POOL,
    "Exceeds reward pool maximum"
);
```

### Overflow Prevention Example

```
Scenario: Attempt to fund 69,999,900 TCP when 101 TCP already funded

Step 1: Check current state
├─ rewardFunded: 101 TCP
├─ Funding amount: 69,999,900 TCP
└─ Total: 70,000,001 TCP

Step 2: Validation
├─ 70,000,001 > 70,000,000 ✗
└─ Status: Validation fails

Step 3: Transaction reverted
├─ Error: "Exceeds reward pool maximum"
└─ Status: Funding rejected

Step 4: Corrected attempt
├─ Funding amount: 69,999,899 TCP
├─ Total: 70,000,000 TCP ✓
└─ Status: Funding accepted
```

## Contract Balance Verification

### Balance Composition

The contract balance consists of two parts:

```
Contract Balance = Staked Tokens + Reward Pool

Example:
├─ Staked Tokens: 100,000 TCP
├─ Reward Pool: 70,000,000 TCP
└─ Total Balance: 70,100,000 TCP
```

### Balance Verification Function

```solidity
function verifyBalance() external view returns (bool) {
    uint256 expectedBalance = totalStaked + rewardFunded;
    uint256 actualBalance = token.balanceOf(address(this));
    return actualBalance == expectedBalance;
}
```

### Balance Invariant

The contract maintains:

```
Invariant: Contract Balance = Total Staked + Reward Funded
```

This ensures:
- No tokens are lost
- All tokens are accounted for
- Staking and rewards are properly segregated

## Event Emission

### Key Events

The contract emits events for transparency:

```solidity
event Staked(address indexed user, uint256 amount);
event Unstaked(address indexed user, uint256 amount);
event RewardsClaimed(address indexed user, uint256 amount);
event RewardsFunded(uint256 amount);
```

### Event Tracking

All events are recorded on-chain and queryable:

```
Event: Staked
├─ User: 0x1234...
├─ Amount: 1,000 TCP
└─ Block: 50,000,000

Event: RewardsClaimed
├─ User: 0x1234...
├─ Amount: 25 TCP
└─ Block: 50,100,000
```

## Key Takeaways

1. **Proportional rewards**: Based on stake share
2. **Continuous accrual**: Updated per block
3. **Automatic reservation**: Prevents double-payment
4. **Pool overflow protection**: Enforced by contract
5. **Transparent accounting**: All state verifiable on-chain
6. **Flexible claiming**: Claim anytime without restrictions

## See also

- [How Staking Works](/docs/staking-rewards/how-staking-works)
- [Reward Funding](/docs/staking-rewards/reward-funding)
- [User Flows](/docs/staking-rewards/user-flows)
- [Technical Validation](/docs/staking-rewards/technical-validation)
- [TCPStakingV2 Contract](/docs/protocol-architecture/staking)
