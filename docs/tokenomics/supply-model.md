---
title: Supply Model
sidebar_position: 2
description: TCP's token supply model - principles, structure, and sustainability
---

# Supply Model

Protocol (TCP) operates with a **clear, defensible supply model** designed for long-term sustainability and transparency.

## Supply Model Principles

The TCP supply model is built on four core principles:

### 1. Clarity
- **Easy to understand** — Supply mechanics are straightforward
- **Transparent** — All supply information publicly available
- **Verifiable** — Anyone can check supply on-chain
- **Documented** — Complete documentation of supply logic

### 2. Defensibility
- **Justified** — Supply model can be explained and defended
- **Reasonable** — Allocations make sense for project needs
- **Sustainable** — Designed for long-term viability
- **Auditable** — Can be reviewed by third parties

### 3. Consistency
- **Aligned with Architecture** — Supply model matches contract design
- **Aligned with Tokenomics** — Consistent with economic model
- **Aligned with Governance** — Consistent with governance rules
- **Aligned with Operations** — Consistent with operational practices

### 4. Sustainability
- **Long-Term Viability** — Designed to support long-term growth
- **Economic Discipline** — Mechanisms to maintain value
- **Balanced Incentives** — Rewards aligned with participation
- **Scalable** — Supports ecosystem growth

## Supply Structure

### Total Supply

The TCP token has:

- **Maximum Supply** — Hard cap on total tokens (if applicable)
- **Current Supply** — Tokens currently in existence
- **Circulating Supply** — Tokens in active circulation
- **Locked Supply** — Tokens in vesting or locked contracts

### Supply Composition

The total supply is composed of:

```
Total Supply
├── Circulating Supply
│   ├── Holder Wallets
│   ├── Exchange Reserves
│   └── Liquidity Pools
├── Locked Supply
│   ├── Vesting Contracts
│   ├── Treasury Reserves
│   └── Ecosystem Allocations
└── Staking Rewards
    └── Available for Distribution
```

## Supply Management

### Mechanisms for Supply Control

TCP uses several mechanisms to manage supply:

#### 1. Burn Mechanism
- **Purpose** — Reduce supply over time
- **Trigger** — Specific protocol events or operations
- **Effect** — Permanent removal from circulation
- **Transparency** — All burns logged on-chain

#### 2. Vesting Schedules
- **Purpose** — Gradual release of allocated tokens
- **Duration** — Tokens released over defined periods
- **Transparency** — Vesting schedules publicly available
- **Automation** — Vesting executed automatically

#### 3. Treasury Management
- **Purpose** — Hold strategic reserves
- **Access** — Controlled via proposal and timelock
- **Transparency** — Treasury balance publicly visible
- **Discipline** — Formal process for withdrawals

#### 4. Staking Rewards
- **Purpose** — Incentivize participation
- **Source** — Allocated reward pool
- **Distribution** — Earned through staking
- **Sustainability** — Designed to be sustainable

### Supply Dynamics

The supply changes over time according to:

```
Current Supply
    ↓
+ New Rewards (from staking)
- Burned Tokens (from burn mechanism)
= New Supply
```

## Allocation Framework

### Strategic Allocations

Tokens are allocated across several strategic categories:

| Category | Purpose | Characteristics |
|----------|---------|-----------------|
| **Ecosystem** | Support ecosystem development | Vested, allocated for growth |
| **Operations** | Fund project operations | Vested, allocated for team |
| **Partnerships** | Support strategic partnerships | Vested, allocated for partners |
| **Community** | Reward community participation | Vested, allocated for community |
| **Staking** | Reward staking participants | Earned through participation |
| **Treasury** | Strategic reserves | Held for future use |
| **Liquidity** | Provide trading liquidity | Locked in LP contracts |

### Allocation Distribution

Allocations are distributed according to:

1. **Initial Distribution** — Tokens allocated at launch
2. **Vesting Release** — Tokens released over time
3. **Earned Rewards** — Tokens earned through participation
4. **Burn Reduction** — Tokens removed from circulation

## Supply Transparency

### Public Information

All supply information is publicly available:

✅ **Total Supply** — Current total supply on-chain  
✅ **Circulating Supply** — Tokens in active circulation  
✅ **Locked Supply** — Tokens in vesting or locked contracts  
✅ **Treasury Balance** — Treasury holdings publicly visible  
✅ **Burn History** — All burns logged on-chain  
✅ **Vesting Schedules** — Vesting information publicly available  

### Verification Methods

You can verify supply information:

1. **PolygonScan**
   - Check total supply
   - View token transfers
   - Monitor burn events
   - Track treasury balance

2. **Contract Functions**
   - Call `totalSupply()` for total supply
   - Call `balanceOf()` for specific balances
   - Check vesting contract state
   - Verify burn events

3. **Community Tools**
   - Use community dashboards
   - Monitor supply metrics
   - Track allocation releases
   - Analyze supply trends

## Supply Sustainability

### Long-Term Viability

The supply model is designed for long-term sustainability through:

#### Balanced Incentives
- Rewards encourage participation
- Burn maintains scarcity
- Allocations support growth
- Treasury provides reserves

#### Economic Discipline
- Burn mechanism reduces supply
- Vesting prevents sudden dumps
- Treasury limits prevent abuse
- Staking rewards incentivize holding

#### Scalable Structure
- Supply model supports growth
- Allocations enable expansion
- Rewards scale with participation
- Treasury supports operations

### Supply Projections

The supply evolves according to:

1. **Year 1** — Initial distribution and vesting begins
2. **Year 2-3** — Vesting continues, burn mechanism active
3. **Year 4+** — Mature supply model, sustainable rewards

## Supply vs. Demand

### Supply-Side Factors

Supply is influenced by:
- **Vesting releases** — Gradual token release
- **Burn mechanism** — Supply reduction
- **Staking rewards** — New token creation
- **Treasury operations** — Reserve management

### Demand-Side Factors

Demand is influenced by:
- **Ecosystem growth** — More users, more demand
- **Staking rewards** — Incentivizes holding
- **Partnerships** — Increases utility
- **Market conditions** — General crypto market

### Balance

The supply model is designed to:
- **Maintain balance** between supply and demand
- **Prevent oversupply** through burn mechanism
- **Encourage holding** through staking rewards
- **Support growth** through allocations

## Supply Model Governance

### Parameter Management

Supply model parameters are managed through:

1. **Owner Control** — Routine parameter adjustments
2. **Multisig Approval** — Critical parameter changes
3. **Community Input** — Major changes may require community input
4. **Transparent Process** — All changes logged on-chain

### Parameter Flexibility

The supply model allows for:
- **Burn rate adjustment** — Modify burn mechanism
- **Reward adjustment** — Adjust staking rewards
- **Allocation adjustment** — Modify allocation amounts
- **Vesting adjustment** — Adjust vesting schedules

## Important Notes

### Supply Model Accuracy

- **Official Source** — Always refer to deployed contracts for authoritative supply information
- **On-Chain Verification** — Verify supply on PolygonScan
- **Documentation** — Check official documentation for details
- **Updates** — Supply model may be updated, check for latest information

### Supply Considerations

When evaluating supply:

✅ **Understand the model** — Know how supply is managed  
✅ **Verify on-chain** — Check actual supply on PolygonScan  
✅ **Monitor changes** — Track supply changes over time  
✅ **Consider context** — Understand supply in context of ecosystem  

## Key Takeaways

1. **Clear supply model** — Easy to understand and verify
2. **Transparent management** — All supply information public
3. **Sustainable design** — Designed for long-term viability
4. **Multiple mechanisms** — Burn, vesting, rewards, treasury
5. **Community trust** — Transparent, auditable supply management

---

**Next:** Learn about the [Allocation Framework](./allocation-framework.md) and how tokens are distributed.
