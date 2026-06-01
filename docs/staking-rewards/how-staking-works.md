---
title: How Staking Works
sidebar_position: 1
description: Understanding TCP staking mechanics and user participation
---

# How Staking Works

Protocol (TCP) features a **simple, user-friendly staking mechanism** that enables token holders to earn rewards.

## Staking Overview

Staking allows you to:
- **Deposit TCP tokens** — Lock tokens in staking contract
- **Earn rewards** — Receive rewards over time
- **Claim rewards** — Withdraw earned rewards anytime
- **Unstake anytime** — Withdraw staked tokens without lock-up

## Staking Process

### Step 1: Approve Staking Contract

Before staking, you must approve the staking contract to spend your tokens.

**How to Approve**
1. Open your wallet
2. Find TCP token
3. Select "Approve"
4. Enter staking contract address
5. Enter amount to approve
6. Confirm transaction

**On-Chain**
- Approval recorded
- Allowance set
- Event emitted
- Ready to stake

### Step 2: Stake Tokens

Once approved, you can stake your tokens.

**How to Stake**
1. Open staking interface
2. Enter amount to stake
3. Review details
4. Confirm transaction
5. Wait for confirmation

**On-Chain**
- Tokens transferred to staking contract
- Stake recorded
- Rewards begin accruing
- Event emitted

**Example**
```
Stake 1,000 TCP
- Tokens transferred
- Stake recorded
- Rewards begin accruing
```

### Step 3: Earn Rewards

Your rewards accrue automatically over time.

**How Rewards Work**
- Calculated continuously
- Based on your stake
- Based on reward rate
- Updated on each block

**Reward Calculation**
```
Your Reward = (Your Stake / Total Stake) × Total Rewards
```

**Example**
```
Your Stake: 1,000 TCP
Total Stake: 100,000 TCP
Reward Rate: 10% APY
Annual Reward: 100 TCP
```

### Step 4: Claim Rewards

You can claim your earned rewards anytime.

**How to Claim**
1. Open staking interface
2. View earned rewards
3. Click "Claim"
4. Confirm transaction
5. Wait for confirmation

**On-Chain**
- Rewards calculated
- Rewards transferred
- Claim recorded
- Event emitted

**Example**
```
Claim 25 TCP rewards
- Rewards transferred to wallet
- Claim recorded on-chain
- Rewards reset to zero
```

### Step 5: Unstake Tokens

You can unstake your tokens anytime without lock-up.

**How to Unstake**
1. Open staking interface
2. Enter amount to unstake
3. Review details
4. Confirm transaction
5. Wait for confirmation

**On-Chain**
- Tokens transferred back
- Stake reduced
- Unstake recorded
- Event emitted

**Example**
```
Unstake 500 TCP
- 500 TCP transferred back
- Stake reduced to 500 TCP
- Unstake recorded on-chain
```

## Staking Parameters

### Key Parameters

| Parameter | Value |
|-----------|-------|
| **Reward Rate** | e.g., 10% APY |
| **Minimum Stake** | e.g., 1 TCP (if applicable) |
| **Maximum Stake** | e.g., 1,000,000 TCP (if applicable) |
| **Reward Period** | Continuous |
| **Lock-Up Period** | None |

### Parameter Flexibility

Parameters can be adjusted:
- Reward rate can be modified
- Minimum stake can be changed
- Maximum stake can be adjusted
- Changes announced in advance

## Reward Mechanics

### Reward Accrual

Rewards accrue continuously:
- Calculated per block
- Updated on each interaction
- Claimable anytime
- No lock-up period

### Reward Distribution

Rewards are distributed from:
- **Reward Pool** — Allocated tokens
- **Protocol Revenue** — Protocol earnings
- **Treasury** — If needed
- **Ecosystem Allocations** — If applicable

### Reward Sustainability

Rewards are designed to be sustainable:
- Adequate funding
- Long-term viability
- Adjustable rate
- Transparent tracking

## Staking Examples

### Example 1: Simple Staking

```
Scenario: Stake 1,000 TCP for 1 year

Day 0:
- Approve staking contract
- Stake 1,000 TCP
- Rewards begin accruing

Day 365:
- Earned rewards: ~100 TCP (at 10% APY)
- Claim rewards
- 100 TCP transferred to wallet

Completion:
- Staked: 1,000 TCP
- Earned: 100 TCP
- Total: 1,100 TCP
```

### Example 2: Partial Unstaking

```
Scenario: Stake 1,000 TCP, then unstake 500

Day 0:
- Stake 1,000 TCP
- Rewards begin accruing

Day 180:
- Earned rewards: ~50 TCP (at 10% APY)
- Unstake 500 TCP
- 500 TCP transferred back
- Remaining stake: 500 TCP

Day 365:
- Earned additional rewards: ~25 TCP
- Claim all rewards
- 75 TCP transferred to wallet

Completion:
- Staked: 500 TCP
- Earned: 75 TCP
- Unstaked: 500 TCP
```

### Example 3: Continuous Staking

```
Scenario: Stake, claim, and restake

Day 0:
- Stake 1,000 TCP

Day 180:
- Earned: 50 TCP
- Claim rewards
- Stake additional 50 TCP
- New stake: 1,050 TCP

Day 365:
- Earned: ~52.50 TCP
- Claim rewards
- Total earned: 102.50 TCP

Completion:
- Staked: 1,050 TCP
- Earned: 102.50 TCP
```

## Staking Benefits

### For Users

✅ **Passive income** — Earn rewards on holdings  
✅ **Flexibility** — Stake and unstake anytime  
✅ **Transparency** — Rewards calculated on-chain  
✅ **Simplicity** — Easy to understand and use  
✅ **No lock-up** — Access tokens anytime  

### For Protocol

✅ **Incentivizes holding** — Rewards encourage long-term holding  
✅ **Builds community** — Rewards build community engagement  
✅ **Supports security** — Staking supports protocol security  
✅ **Aligns incentives** — Rewards align holder interests  

## Staking Risks

### Considerations

⚠️ **Smart contract risk** — Staking contract may have vulnerabilities  
⚠️ **Market risk** — Token value may decrease  
⚠️ **Reward risk** — Reward rate may change  
⚠️ **Liquidity risk** — Tokens locked while staking  
⚠️ **Operational risk** — Protocol operations may be disrupted  

### Risk Mitigation

Risks are mitigated through:
- Audited contracts
- Transparent operations
- Flexible unstaking
- Reward sustainability
- Community oversight

## Best Practices

### For Stakers

✅ **Understand the mechanism** — Know how staking works  
✅ **Verify the contract** — Check contract on PolygonScan  
✅ **Start small** — Test with small amount first  
✅ **Monitor rewards** — Track your rewards  
✅ **Claim regularly** — Claim rewards periodically  

### For Community

✅ **Monitor staking** — Watch staking metrics  
✅ **Assess rewards** — Evaluate reward sustainability  
✅ **Provide feedback** — Share suggestions  
✅ **Report issues** — Report any problems  
✅ **Stay informed** — Follow staking updates  

## Key Takeaways

1. **Simple mechanism** — Easy to understand and use
2. **Flexible participation** — Stake and unstake anytime
3. **Transparent rewards** — Rewards calculated on-chain
4. **No lock-up** — Access tokens anytime
5. **Community trust** — Transparent, auditable staking

---

**Next:** Learn about [Reward Funding](./reward-funding.md) and how rewards are sustained.
