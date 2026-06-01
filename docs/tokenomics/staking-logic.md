---
title: Staking Logic
sidebar_position: 5
description: Understanding TCP's staking mechanism and reward distribution
---

# Staking Logic

Protocol (TCP) features a **staking mechanism** that enables token holders to earn rewards while supporting the protocol.

## What is Staking?

**Staking** is the process of locking tokens in a smart contract to earn rewards. When you stake:

1. **You deposit TCP tokens** — Lock tokens in staking contract
2. **Rewards accrue over time** — Earn rewards based on stake
3. **You can claim rewards** — Withdraw earned rewards
4. **You can unstake anytime** — Withdraw staked tokens

## Staking Objectives

### 1. Incentivize Participation

**Purpose**
- Reward token holders
- Encourage long-term holding
- Support community engagement
- Build ecosystem participation

**How It Works**
- Stakers earn rewards
- Rewards increase over time
- Rewards incentivize holding
- Participation is rewarded

### 2. Align Incentives

**Purpose**
- Align holder interests with protocol
- Encourage protocol support
- Build community commitment
- Support long-term growth

**How It Works**
- Stakers benefit from protocol success
- Rewards increase with participation
- Incentives aligned with growth
- Community invested in success

### 3. Distribute Rewards

**Purpose**
- Distribute tokens to participants
- Support ecosystem growth
- Reward community contributions
- Enable sustainable distribution

**How It Works**
- Rewards distributed to stakers
- Distribution is transparent
- Rewards are earned, not given
- Distribution is sustainable

### 4. Support Protocol Security

**Purpose**
- Encourage participation
- Build community commitment
- Support long-term stability
- Strengthen ecosystem

**How It Works**
- Stakers are invested in protocol
- Stakers benefit from success
- Stakers support stability
- Community commitment strengthens protocol

## Staking Mechanism

### How Staking Works

```
1. User Deposits TCP
   ↓
2. Tokens Locked in Staking Contract
   ↓
3. Rewards Accrue Over Time
   ↓
4. User Claims Rewards
   ↓
5. User Can Unstake Anytime
```

### Staking Process

**Step 1: Deposit**
- User approves staking contract to spend tokens
- User deposits TCP tokens
- Tokens locked in staking contract
- Stake recorded on-chain

**Step 2: Earn**
- Rewards accrue over time
- Reward rate determined by parameters
- Rewards calculated transparently
- Rewards tracked on-chain

**Step 3: Claim**
- User claims earned rewards
- Rewards transferred to user wallet
- Claim recorded on-chain
- User can claim anytime

**Step 4: Unstake**
- User can unstake anytime
- Staked tokens returned to user
- Unstake recorded on-chain
- No lock-up period required

## Reward Mechanism

### Reward Calculation

Rewards are calculated based on:

1. **Stake Amount** — How many tokens staked
2. **Stake Duration** — How long tokens are staked
3. **Reward Rate** — Percentage return per period
4. **Total Pool** — Total tokens in staking pool

### Reward Formula

```
User Reward = (User Stake / Total Stake) × Total Rewards
```

### Reward Distribution

Rewards are distributed:
- **Continuously** — Rewards accrue over time
- **On-Demand** — User claims when ready
- **Transparently** — Calculation visible on-chain
- **Automatically** — Smart contract handles distribution

## Reward Funding

### Reward Sources

Rewards come from:

1. **Allocation Pool** — Tokens allocated for rewards
2. **Protocol Revenue** — Revenue from protocol operations
3. **Ecosystem Allocations** — Allocations for rewards
4. **Treasury** — Treasury can fund rewards if needed

### Reward Sustainability

Rewards are designed to be sustainable through:

1. **Adequate Funding** — Sufficient tokens allocated
2. **Sustainable Rate** — Rate designed to last long-term
3. **Flexible Adjustment** — Rate can be adjusted if needed
4. **Transparent Tracking** — Reward pool tracked on-chain

### Reward Rate

The reward rate is:
- **Transparent** — Publicly available
- **Adjustable** — Can be modified if needed
- **Sustainable** — Designed for long-term viability
- **Fair** — Applied equally to all stakers

## Staking Parameters

### Key Parameters

| Parameter | Description |
|-----------|-------------|
| **Minimum Stake** | Minimum tokens required to stake |
| **Reward Rate** | Percentage return per period |
| **Reward Period** | Time period for reward calculation |
| **Lock-Up Period** | Time tokens are locked (if applicable) |
| **Maximum Stake** | Maximum tokens per user (if applicable) |

### Parameter Management

Parameters are managed through:

1. **Owner Control** — Routine adjustments
2. **Multisig Approval** — Critical changes
3. **Community Input** — Major changes may require input
4. **Transparent Process** — All changes logged on-chain

## Staking Transparency

### Staking Information

All staking information is publicly available:

✅ **Reward Rate** — Current reward rate  
✅ **Total Staked** — Total tokens in staking pool  
✅ **Your Stake** — Your staked amount  
✅ **Your Rewards** — Your earned rewards  
✅ **Reward History** — Past reward distributions  

### Verification Methods

You can verify staking information:

1. **Staking Contract**
   - Check reward rate
   - View total staked
   - Check your stake
   - View your rewards

2. **PolygonScan**
   - View staking events
   - Monitor stake changes
   - Track reward distributions
   - Verify transactions

3. **Community Tools**
   - Use staking dashboards
   - Monitor reward rates
   - Track staking metrics
   - Analyze staking trends

## Staking Economics

### Reward Economics

Staking rewards are designed to:

1. **Incentivize Participation** — Rewards encourage staking
2. **Support Value** — Rewards support token value
3. **Sustainable** — Rewards designed for long-term viability
4. **Fair** — Rewards distributed fairly to all stakers

### Staking Yield

Your staking yield depends on:

1. **Reward Rate** — Percentage return
2. **Stake Duration** — How long you stake
3. **Total Pool** — Total tokens staked
4. **Your Stake** — Your staked amount

### Yield Calculation

```
Annual Yield = (Reward Rate × Your Stake) / 100
```

## Staking User Flow

### Example: Staking 1,000 TCP

```
1. Approve Staking Contract
   - Approve 1,000 TCP for spending

2. Deposit Tokens
   - Deposit 1,000 TCP
   - Tokens locked in contract
   - Stake recorded on-chain

3. Earn Rewards
   - Rewards accrue daily
   - After 1 year: 100 TCP earned (10% APY)
   - Rewards tracked on-chain

4. Claim Rewards
   - Claim 100 TCP rewards
   - Rewards transferred to wallet
   - Claim recorded on-chain

5. Unstake (Optional)
   - Unstake 1,000 TCP
   - Tokens returned to wallet
   - Unstake recorded on-chain
```

## Staking Risks

### Considerations

When staking, consider:

⚠️ **Smart Contract Risk** — Staking contract may have vulnerabilities  
⚠️ **Market Risk** — Token value may decrease  
⚠️ **Reward Risk** — Reward rate may change  
⚠️ **Liquidity Risk** — Tokens locked while staking  
⚠️ **Operational Risk** — Protocol operations may be disrupted  

### Risk Mitigation

Risks are mitigated through:

✅ **Audited Contracts** — Staking contract audited for security  
✅ **Transparent Operations** — All operations logged on-chain  
✅ **Flexible Unstaking** — Can unstake anytime  
✅ **Reward Sustainability** — Rewards designed to be sustainable  
✅ **Community Oversight** — Community monitors staking operations  

## Staking Governance

### Staking Parameters

Staking parameters are governed through:

1. **Owner Control** — Routine adjustments
2. **Multisig Approval** — Critical changes
3. **Community Input** — Major changes may require input
4. **Transparent Process** — All changes logged on-chain

### Staking Flexibility

The staking mechanism allows for:
- **Reward Rate Adjustment** — Modify reward rate
- **Parameter Adjustment** — Modify staking parameters
- **Pool Management** — Manage reward pool
- **Emergency Pause** — Pause staking if needed

## Important Notes

### Staking Accuracy

- **Official Source** — Always refer to official documentation for staking information
- **On-Chain Verification** — Verify staking on-chain
- **Updates** — Staking mechanism may be updated, check for latest information
- **Context** — Understand staking in context of overall tokenomics

### Staking Considerations

When evaluating staking:

✅ **Understand the mechanism** — Know how staking works  
✅ **Verify the rewards** — Check reward rate on-chain  
✅ **Monitor your stake** — Track your staked amount  
✅ **Assess the risks** — Evaluate staking risks  

## Key Takeaways

1. **Simple mechanism** — Easy to understand and use
2. **Transparent rewards** — All rewards calculated and verified on-chain
3. **Flexible participation** — Stake and unstake anytime
4. **Sustainable design** — Rewards designed for long-term viability
5. **Community trust** — Transparent, auditable staking operations

---

**Next:** Learn about [Treasury & Liquidity Logic](./treasury-liquidity-logic.md) and how these critical assets are protected.
