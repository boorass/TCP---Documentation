---
title: Liquidity Protection
sidebar_position: 4
description: TCP's advanced liquidity protection mechanisms
---

# Liquidity Protection

Protocol (TCP) implements **advanced liquidity protection** that goes beyond simple locks to provide comprehensive LP safeguards.

## Why Liquidity Protection Matters

Liquidity is critical because:
- **Trading depends on it** — Users need liquidity to trade
- **Price stability depends on it** — Adequate liquidity supports stable prices
- **Investor confidence depends on it** — Protected LP builds trust
- **Long-term viability depends on it** — Permanent LP ensures sustainability

## TCP's Liquidity Protection Approach

TCP protects LP through:

1. **Permanent Portion** — 85% locked long-term
2. **Flexible Portion** — 15% with daily limits
3. **Proposal System** — Formal process for withdrawals
4. **Timelocks** — Waiting periods before execution
5. **Daily Limits** — Caps on flexible withdrawals

## Permanent Liquidity Protection

### 85% Permanent Portion

**Characteristics**
- 85% of total LP locked
- 365+ day lock period
- Cannot be withdrawn before expiration
- Lock can be extended, not shortened

**Benefits**
- Long-term LP guaranteed
- Investor confidence
- Price stability
- Sustainable trading

**Protection Mechanism**
```
Total LP
└── Permanent (85%)
    ├── 365+ day lock
    ├── Cannot be withdrawn early
    ├── Lock can be extended
    └── Timelock on withdrawal after expiration
```

### Lock Enforcement

The lock is enforced by smart contract:
- Cannot be bypassed
- Cannot be shortened
- Cannot be circumvented
- Immutable on-chain

## Flexible Liquidity Protection

### 15% Flexible Portion

**Characteristics**
- 15% of total LP available
- Daily withdrawal limits
- Proposal-based withdrawals
- Timelock enforcement

**Benefits**
- Some flexibility for operations
- Daily limits prevent abuse
- Proposal system enables oversight
- Timelocks enable community reaction

**Protection Mechanism**
```
Total LP
└── Flexible (15%)
    ├── Daily limit (e.g., 1% per day)
    ├── Proposal required
    ├── Timelock enforcement
    └── Consumption tracking
```

### Daily Limit Enforcement

Daily limits are enforced by smart contract:
- Consumption tracked per day
- Resets daily
- Cannot exceed limit
- Prevents large sudden withdrawals

## Withdrawal Process

### For Permanent LP (after lock expires)

```
1. Lock expires
   - 365+ days passed
   - Withdrawal becomes possible
   - Expiration date transparent

2. Propose withdrawal
   - Owner proposes withdrawal
   - Amount specified
   - Proposal recorded on-chain

3. Timelock period
   - 7 days (example)
   - Community monitors
   - Proposal can be cancelled

4. Execute withdrawal
   - After timelock expires
   - Owner executes withdrawal
   - LP transferred

5. Completion
   - LP balance updated
   - Event logged on-chain
   - Transparency maintained
```

### For Flexible LP

```
1. Check daily limit
   - Daily limit: 1% of flexible portion
   - Current consumption: 0.3%
   - Available: 0.7%

2. Propose withdrawal
   - Owner proposes withdrawal
   - Amount: 0.5% (within limit)
   - Proposal recorded on-chain

3. Timelock period
   - 7 days (example)
   - Community monitors
   - Proposal can be cancelled

4. Execute withdrawal
   - After timelock expires
   - Owner executes withdrawal
   - LP transferred

5. Completion
   - LP balance updated
   - Daily consumption updated
   - Event logged on-chain
   - Transparency maintained
```

## Liquidity Transparency

### Public Information

All liquidity information is public:

✅ **LP Balance** — Current LP holdings  
✅ **Permanent Portion** — 85% portion details  
✅ **Flexible Portion** — 15% portion details  
✅ **Lock Status** — Lock expiration date  
✅ **Daily Limits** — Daily withdrawal limits  
✅ **Pending Proposals** — Proposed withdrawals  
✅ **Withdrawal History** — Past withdrawals  

### Verification Methods

You can verify liquidity information:

1. **PolygonScan**
   - Check LP balance
   - View lock events
   - Monitor proposals
   - Track withdrawals

2. **Contract Functions**
   - Call getLPBalance()
   - Call getPermanentLPBalance()
   - Call getFlexibleLPBalance()
   - Call getLockStatus()
   - Call getDailyLimitStatus()

3. **Community Tools**
   - Use liquidity dashboards
   - Monitor LP metrics
   - Track lock status
   - Analyze patterns

## Liquidity Protection Benefits

### For Investors

✅ **Confidence** — Protected LP builds investor confidence  
✅ **Stability** — Permanent LP ensures long-term stability  
✅ **Transparency** — All LP information public and verifiable  
✅ **Oversight** — Community can monitor LP  

### For Traders

✅ **Liquidity** — Adequate LP ensures efficient trading  
✅ **Slippage** — Protected LP reduces slippage  
✅ **Stability** — Stable LP supports stable prices  
✅ **Reliability** — Long-term LP ensures reliability  

### For the Protocol

✅ **Sustainability** — Permanent LP ensures long-term viability  
✅ **Credibility** — Advanced protection builds credibility  
✅ **Institutional Appeal** — Professional approach attracts institutions  
✅ **Market Stability** — Protected LP supports market stability  

## Liquidity Protection Examples

### Example 1: Permanent LP Lock

```
Scenario: Protect 1000 LP tokens for 365 days

Day 0:
- 1000 LP locked
- Lock duration: 365 days
- Unlock date: Day 365
- Event logged on PolygonScan

Days 1-364:
- LP locked and protected
- Cannot be withdrawn
- Community can verify lock
- Lock status visible on-chain

Day 365:
- Lock expires
- Withdrawal becomes possible
- Owner can propose withdrawal
- Timelock begins

Day 372:
- Timelock expires
- Owner executes withdrawal
- LP transferred
- Event logged on PolygonScan

Completion:
- LP protected for 365 days
- Transparency maintained
- Investor confidence maintained
```

### Example 2: Flexible LP Withdrawal

```
Scenario: Withdraw from flexible portion

Daily Limit: 1% of flexible portion (10 LP)
Current Consumption: 3 LP
Available: 7 LP

Day 0:
- Owner proposes withdrawal
- Amount: 5 LP (within limit)
- Proposal recorded on-chain

Days 1-6:
- Timelock period
- Community monitors
- Proposal can be cancelled

Day 7:
- Timelock expires
- Owner executes withdrawal
- 5 LP transferred
- Daily consumption: 8 LP

Day 8:
- Daily consumption resets
- New daily limit available
- Process can repeat

Completion:
- Flexible LP accessed with safeguards
- Daily limits enforced
- Transparency maintained
```

## Key Takeaways

1. **Dual protection** — Permanent lock + flexible limits
2. **Long-term security** — 85% locked for 365+ days
3. **Flexible access** — 15% available with daily limits
4. **Timelock enforcement** — All withdrawals require delays
5. **Complete transparency** — All operations logged on-chain

---

**Next:** Learn about [Treasury Protection](./treasury-protection.md) and treasury safeguards.
