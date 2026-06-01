---
title: Burn Logic
sidebar_position: 4
description: Understanding TCP's token burn mechanism and supply control
---

# Burn Logic

Protocol (TCP) integrates a **burn mechanism** to maintain economic discipline and support long-term value preservation.

## What is Burning?

**Burning** is the permanent removal of tokens from circulation. When tokens are burned:

1. **Tokens are sent to a burn address** — An address that cannot spend tokens
2. **Tokens are removed from circulation** — No longer available for trading or use
3. **Total supply decreases** — Fewer tokens in existence
4. **Scarcity increases** — Remaining tokens become relatively scarcer

## Burn Mechanism Objectives

### 1. Economic Discipline

**Purpose**
- Maintain economic discipline
- Support long-term value
- Prevent oversupply
- Encourage scarcity

**How It Works**
- Regular burn schedule
- Burn triggered by protocol events
- Transparent burn logic
- Predictable supply reduction

### 2. Supply Control

**Purpose**
- Manage token supply
- Prevent inflation
- Maintain scarcity
- Support sustainability

**How It Works**
- Burn reduces total supply
- Supply reduction is predictable
- Burn events are logged
- Supply changes are transparent

### 3. Value Preservation

**Purpose**
- Support token value
- Reduce dilution
- Encourage holding
- Long-term sustainability

**How It Works**
- Fewer tokens in circulation
- Relative scarcity increases
- Holding becomes more valuable
- Long-term value supported

### 4. Protocol Incentives

**Purpose**
- Align incentives
- Reward participation
- Support ecosystem
- Encourage engagement

**How It Works**
- Burn rewards participation
- Burn supports ecosystem
- Burn aligns incentives
- Burn encourages engagement

## Burn Mechanisms

### 1. Scheduled Burns

**How It Works**
- Tokens burned on a regular schedule
- Burn amount predetermined
- Burn timing transparent
- Burn events logged

**Example**
- Burn 1% of supply annually
- Burn occurs on specific dates
- Burn amount announced in advance
- Burn events logged on-chain

### 2. Event-Triggered Burns

**How It Works**
- Tokens burned when specific events occur
- Burn amount based on event
- Burn logic transparent
- Burn events logged

**Example Events**
- Tokens burned from failed transactions
- Tokens burned from penalty mechanisms
- Tokens burned from protocol fees
- Tokens burned from ecosystem activities

### 3. Proposal-Based Burns

**How It Works**
- Burn proposed by governance
- Burn approved by community
- Burn executed after approval
- Burn events logged

**Example**
- Community votes to burn tokens
- Burn amount specified in proposal
- Burn executed after approval
- Burn events logged on-chain

## Burn Transparency

### Burn Information

All burn information is publicly available:

✅ **Burn Schedule** — When burns occur  
✅ **Burn Amount** — How many tokens are burned  
✅ **Burn History** — All past burns logged  
✅ **Burn Logic** — How burn amount is calculated  
✅ **Burn Address** — Where burned tokens go  

### Burn Verification

You can verify burn information:

1. **PolygonScan**
   - Search for burn events
   - View burn transactions
   - Monitor burn address
   - Track supply changes

2. **Contract Functions**
   - Call burn function (if applicable)
   - Check burn events
   - Verify burn logic
   - Monitor supply changes

3. **Community Tools**
   - Use community dashboards
   - Monitor burn metrics
   - Track burn history
   - Analyze supply trends

## Burn Economics

### Supply Reduction

Burning reduces supply according to:

```
Current Supply
    ↓
- Burned Tokens
    ↓
= New Supply
```

### Impact on Value

Burning can impact token value through:

1. **Scarcity** — Fewer tokens increases relative scarcity
2. **Perception** — Burn signals economic discipline
3. **Demand** — Burn may increase demand
4. **Price** — Scarcity and demand may support price

### Long-Term Effects

Over time, burning:
- **Reduces supply** — Fewer tokens in circulation
- **Increases scarcity** — Remaining tokens become scarcer
- **Supports value** — Scarcity can support value
- **Demonstrates discipline** — Shows commitment to economics

## Burn Governance

### Burn Parameters

Burn parameters are managed through:

1. **Owner Control** — Routine burn adjustments
2. **Multisig Approval** — Critical burn changes
3. **Community Input** — Major changes may require input
4. **Transparent Process** — All changes logged on-chain

### Burn Flexibility

The burn mechanism allows for:
- **Burn rate adjustment** — Modify burn amount
- **Burn schedule adjustment** — Modify burn timing
- **Burn trigger adjustment** — Modify burn conditions
- **Burn pause** — Temporarily pause burns if needed

## Burn Examples

### Example 1: Annual Scheduled Burn

```
Burn Schedule: Annually
Burn Amount: 1% of total supply
Burn Timing: January 1st each year
Burn Logic: Fixed percentage
Transparency: Announced in advance
Verification: Logged on PolygonScan
```

### Example 2: Event-Triggered Burn

```
Burn Trigger: Failed transactions
Burn Amount: Transaction fee
Burn Logic: Automatic on failure
Transparency: Logged as event
Verification: Visible on PolygonScan
```

### Example 3: Proposal-Based Burn

```
Burn Proposal: Community votes
Burn Amount: Specified in proposal
Burn Timing: After approval
Burn Logic: As specified in proposal
Transparency: Logged on-chain
Verification: Visible on PolygonScan
```

## Burn Considerations

### Benefits of Burning

✅ **Economic discipline** — Demonstrates commitment to economics  
✅ **Supply control** — Manages token supply  
✅ **Value support** — Scarcity can support value  
✅ **Investor confidence** — Shows long-term thinking  
✅ **Transparency** — All burns logged and verifiable  

### Burn Limitations

⚠️ **No guarantee of value** — Burning doesn't guarantee price appreciation  
⚠️ **Market dependent** — Value depends on demand and market conditions  
⚠️ **Not a substitute for fundamentals** — Burn alone doesn't create value  
⚠️ **Requires discipline** — Burn logic must be consistently followed  

## Important Notes

### Burn Accuracy

- **Official Source** — Always refer to official documentation for burn information
- **On-Chain Verification** — Verify burns on PolygonScan
- **Updates** — Burn mechanism may be updated, check for latest information
- **Context** — Understand burns in context of overall tokenomics

### Burn Monitoring

When monitoring burns:

✅ **Track burn schedule** — Know when burns occur  
✅ **Verify burn amounts** — Check amounts on-chain  
✅ **Monitor supply changes** — Track total supply over time  
✅ **Assess impact** — Evaluate burn's impact on economics  

## Key Takeaways

1. **Transparent burn logic** — All burns logged and verifiable
2. **Economic discipline** — Burn demonstrates commitment to economics
3. **Supply control** — Burn manages token supply
4. **Multiple mechanisms** — Scheduled, event-triggered, and proposal-based burns
5. **Community trust** — Transparent, auditable burn management

---

**Next:** Learn about [Staking Logic](./staking-logic.md) and how rewards are distributed.
