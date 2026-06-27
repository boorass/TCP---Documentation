---
title: "How Staking Works"
sidebar_position: 2
description: "Complete guide to TCP staking mechanics, user workflows, and reward accrual"
sidebar_custom_props:
  icon: "book-open"
---

TCP Protocol's staking system enables token holders to earn rewards by locking their TCP tokens in the TCPStakingV2 contract. This guide explains the complete staking process, from approval to reward claiming.

## Staking Overview

The staking process consists of five main steps:

```
1. Approve → 2. Stake → 3. Accrue Rewards → 4. Claim → 5. Unstake
```

Each step is a separate transaction that interacts with the staking contract and the TCP token contract.

## Step 1: Approve the Staking Contract

Before you can stake TCP tokens, you must grant the staking contract permission to spend your tokens.

### Why Approval is Required

The ERC-20 token standard requires a two-step process:
1. **Approve**: Grant the contract an allowance
2. **Transfer**: The contract uses that allowance to transfer tokens

This design protects users by requiring explicit permission before any token movement.

### How to Approve

**Via Web Interface**
1. Connect your wallet
2. Navigate to the staking interface
3. Click "Approve"
4. Confirm the transaction in your wallet
5. Wait for confirmation on Polygon Mainnet

**Via Smart Contract**
```solidity
// Approve the staking contract to spend your TCP tokens
tcp.approve(stakingContractAddress, amountToApprove);
```

**On-Chain Result**
- Allowance recorded in TCP token contract
- Staking contract can now transfer up to the approved amount
- Event emitted: `Approval(user, stakingContract, amount)`

### Approval Amount

You can approve any amount:
- **Exact amount**: Approve only what you plan to stake
- **Larger amount**: Approve more to avoid repeated approvals
- **Unlimited**: Approve maximum uint256 (not recommended)

:::tip
Approve slightly more than you plan to stake initially. This avoids needing to re-approve for future stakes.
:::

## Step 2: Stake Tokens

Once approved, you can stake your TCP tokens.

### How to Stake

**Via Web Interface**
1. Enter the amount to stake
2. Review the transaction details
3. Click "Stake"
4. Confirm in your wallet
5. Wait for confirmation

**Via Smart Contract**
```solidity
// Stake 1000 TCP tokens
staking.stake(1000e18);
```

### What Happens On-Chain

When you stake tokens:

```
1. Validation
   ├─ Check: User has approved sufficient amount
   ├─ Check: User has sufficient balance
   └─ Check: Reward pool has capacity

2. Token Transfer
   └─ Transfer tokens from user to staking contract

3. Position Creation
   ├─ Record stake amount
   ├─ Record stake timestamp
   └─ Initialize reward tracking

4. Event Emission
   └─ Emit Staked(user, amount)
```

### Staking Example

```
User: 0x1234...
Amount: 1,000 TCP
Timestamp: Block 50,000,000

On-Chain State:
├─ User Balance: 1,000 TCP → 0 TCP
├─ Contract Balance: 0 TCP → 1,000 TCP
├─ User Stake: 0 TCP → 1,000 TCP
└─ Total Staked: 0 TCP → 1,000 TCP
```

## Step 3: Rewards Accrue Continuously

Once staked, your rewards begin accruing immediately.

### Reward Calculation

Rewards are calculated based on your share of the total stake:

```
Your Reward = (Your Stake / Total Stake) × Reward Rate
```

### Continuous Accrual

Rewards accrue continuously, updated on each block:

```
Block 50,000,000: Reward = 0.000001 TCP
Block 50,000,001: Reward = 0.000002 TCP
Block 50,000,002: Reward = 0.000003 TCP
...
```

### Reward Tracking

The staking contract maintains:
- **Accrued rewards**: Calculated continuously
- **Reserved rewards**: Held for claim operations
- **Available rewards**: Remaining in the reward pool

### Example Reward Accrual

```
Scenario: 1,000 TCP staked at 10% APY

Day 1:   Accrued ≈ 0.027 TCP
Day 7:   Accrued ≈ 0.19 TCP
Day 30:  Accrued ≈ 0.82 TCP
Day 365: Accrued ≈ 100 TCP
```

:::note
Actual reward rates depend on the current reward pool funding and total staked amount. Check the staking interface for current rates.
:::

## Step 4: Claim Rewards

You can claim your earned rewards at any time.

### How to Claim

**Via Web Interface**
1. View your earned rewards
2. Click "Claim Rewards"
3. Confirm in your wallet
4. Wait for confirmation

**Via Smart Contract**
```solidity
// Claim all earned rewards
uint256 rewardAmount = staking.claimRewards();
```

### What Happens On-Chain

When you claim rewards:

```
1. Calculation
   └─ Calculate total accrued rewards

2. Validation
   ├─ Check: Rewards are available
   ├─ Check: Reward pool has sufficient balance
   └─ Check: No double-payment risk

3. Reward Transfer
   └─ Transfer rewards to user wallet

4. State Update
   ├─ Reset user's accrued rewards to zero
   ├─ Update reward pool balance
   └─ Record claim in contract state

5. Event Emission
   └─ Emit RewardsClaimed(user, amount)
```

### Claiming Example

```
User: 0x1234...
Accrued Rewards: 25 TCP
Claim Timestamp: Block 50,100,000

On-Chain State:
├─ User Reward Balance: 25 TCP → 0 TCP
├─ User Wallet: 0 TCP → 25 TCP
├─ Reward Pool: 70,000,000 TCP → 69,999,975 TCP
└─ Reserved Rewards: 25 TCP → 0 TCP
```

### Claim Frequency

You can claim:
- **Anytime**: No restrictions on claim frequency
- **Partially**: Claim some rewards, leave others accruing
- **Fully**: Claim all accrued rewards at once

:::tip
Claim rewards periodically to compound your earnings. Claimed rewards can be restaked for additional returns.
:::

## Step 5: Unstake Tokens

You can unstake your tokens at any time without lock-up periods.

### How to Unstake

**Via Web Interface**
1. Enter the amount to unstake
2. Review the transaction details
3. Click "Unstake"
4. Confirm in your wallet
5. Wait for confirmation

**Via Smart Contract**
```solidity
// Unstake 500 TCP tokens
staking.unstake(500e18);
```

### What Happens On-Chain

When you unstake tokens:

```
1. Validation
   ├─ Check: User has staked tokens
   ├─ Check: Amount does not exceed stake
   └─ Check: Contract has sufficient balance

2. Token Transfer
   └─ Transfer tokens from contract to user

3. Position Update
   ├─ Reduce stake amount
   ├─ Maintain reward tracking
   └─ Update total staked

4. Event Emission
   └─ Emit Unstaked(user, amount)
```

### Unstaking Example

```
User: 0x1234...
Unstake Amount: 500 TCP
Timestamp: Block 50,200,000

On-Chain State:
├─ User Stake: 1,000 TCP → 500 TCP
├─ User Wallet: 0 TCP → 500 TCP
├─ Contract Balance: 1,000 TCP → 500 TCP
└─ Total Staked: 1,000 TCP → 500 TCP
```

### Partial vs Full Unstaking

**Partial Unstaking**
- Unstake some tokens, keep others staking
- Remaining stake continues earning rewards
- Useful for accessing liquidity while maintaining position

**Full Unstaking**
- Unstake all tokens
- Claim remaining rewards
- Exit the staking position

:::warning
Unstaking does not automatically claim rewards. Claim your rewards before unstaking if you want to receive them.
:::

## Complete Staking Workflow

### Scenario: 1-Year Staking Position

```
Day 0: Approval
├─ Approve staking contract for 1,000 TCP
└─ Status: Ready to stake

Day 0: Staking
├─ Stake 1,000 TCP
├─ Rewards begin accruing
└─ Status: Position active

Day 90: Claim
├─ Accrue ~25 TCP in rewards
├─ Claim 25 TCP
├─ Rewards reset to zero
└─ Status: Position active, rewards claimed

Day 180: Partial Unstaking
├─ Unstake 500 TCP
├─ Remaining stake: 500 TCP
├─ Remaining rewards continue accruing
└─ Status: Position reduced

Day 365: Final Claim & Unstaking
├─ Accrue ~50 TCP in additional rewards
├─ Claim 50 TCP
├─ Unstake remaining 500 TCP
└─ Status: Position closed

Final Result:
├─ Staked: 1,000 TCP
├─ Earned: 75 TCP
├─ Returned: 1,000 TCP
└─ Total Received: 1,075 TCP
```

## Staking Parameters

### Current Configuration

| Parameter | Value | Notes |
|-----------|-------|-------|
| **Reward Pool Maximum** | 70,000,000 TCP | Hard limit, enforced by contract |
| **Minimum Stake** | 1 TCP | Effectively no minimum |
| **Maximum Stake** | Unlimited | Per user, no cap |
| **Lock-up Period** | None | Unstake anytime |
| **Claim Frequency** | Unlimited | Claim anytime |
| **Reward Rate** | Variable | Based on pool funding |

### Pool Overflow Protection

The staking contract includes automatic protection against reward pool overflow:

```solidity
require(
    rewardFunded + newAmount <= MAX_REWARD_POOL,
    "Exceeds reward pool maximum"
);
```

This ensures the reward pool never exceeds 70,000,000 TCP.

## Key Takeaways

1. **Two-step process**: Approve, then stake
2. **Continuous rewards**: Accrue automatically on each block
3. **Flexible claiming**: Claim anytime without restrictions
4. **No lock-up**: Unstake immediately when needed
5. **On-chain transparency**: All operations recorded and verifiable

## Best Practices

### For Stakers

✅ **Understand the mechanism** before staking  
✅ **Start with small amounts** to test the process  
✅ **Monitor your rewards** regularly  
✅ **Claim periodically** to compound earnings  
✅ **Keep records** of all transactions  

### For Security

✅ **Verify contract address** before approving  
✅ **Use hardware wallets** for large stakes  
✅ **Check gas prices** before transactions  
✅ **Confirm transactions** carefully  
✅ **Never share private keys** or seed phrases  

## Common Questions

**Q: Do I need to approve every time I stake?**  
A: No. Once approved, you can stake multiple times up to the approved amount.

**Q: Can I claim rewards without unstaking?**  
A: Yes. Claiming rewards does not affect your stake.

**Q: Are there penalties for unstaking?**  
A: No. You can unstake anytime without penalties.

**Q: How often should I claim rewards?**  
A: Whenever you want. Claiming is optional and can be done anytime.

**Q: What happens if the reward pool runs out?**  
A: The contract prevents staking if rewards are unavailable. The pool is managed to prevent this.

## See also

- [Reward Distribution Logic](/docs/staking-rewards/reward-distribution-logic)
- [Reward Funding](/docs/staking-rewards/reward-funding)
- [User Flows](/docs/staking-rewards/user-flows)
- [TCPStakingV2 Contract](/docs/protocol-architecture/staking)
- [Technical Validation](/docs/staking-rewards/technical-validation)
