---
title: LP Protection Overview
sidebar_position: 1
description: Understanding TCP's liquidity protection framework
---

# LP Protection Overview

Protocol (TCP) implements an **advanced liquidity protection system** that goes beyond simple locks to provide comprehensive safeguards for LP.

## Why LP Protection Matters

Liquidity is critical because:
- **Trading depends on it** — Users need liquidity to trade
- **Price stability depends on it** — Adequate liquidity supports stable prices
- **Investor confidence depends on it** — Protected LP builds trust
- **Long-term viability depends on it** — Permanent LP ensures sustainability

## TCP's Approach

TCP protects LP through:

1. **Permanent Portion** — 85% locked for 365+ days
2. **Flexible Portion** — 15% with daily limits
3. **Proposal System** — Formal process for withdrawals
4. **Timelocks** — Waiting periods before execution
5. **Daily Limits** — Caps on flexible withdrawals

## Protection Structure

```
Total LP (100%)
├── Permanent (85%)
│   ├── 365+ day lock
│   ├── Cannot be withdrawn early
│   └── Timelock on withdrawal after expiration
└── Flexible (15%)
    ├── Daily withdrawal limits
    ├── Proposal-based withdrawals
    └── Timelock enforcement
```

## Key Metrics

| Metric | Value |
|--------|-------|
| **Permanent Portion** | 85% of total LP |
| **Flexible Portion** | 15% of total LP |
| **Permanent Lock Duration** | 365+ days |
| **Daily Withdrawal Limit** | Configurable (e.g., 1% of flexible) |
| **Timelock Delay** | Configurable (e.g., 7 days) |

## Protection Benefits

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

## Comparison to Standard Locks

| Aspect | Standard Lock | TCP Protection |
|--------|---------------|-----------------|
| **Permanent Portion** | Simple lock | 85% with 365+ day lock |
| **Flexible Portion** | None | 15% with daily limits |
| **Withdrawal Process** | Instant | Proposal + Timelock |
| **Daily Limits** | None | Yes |
| **Community Oversight** | Limited | Complete |
| **Transparency** | Limited | Complete |

## Key Takeaways

1. **Dual protection** — Permanent lock + flexible limits
2. **Long-term security** — 85% locked for 365+ days
3. **Flexible access** — 15% available with daily limits
4. **Timelock enforcement** — All withdrawals require delays
5. **Complete transparency** — All operations logged on-chain

---

**Next:** Learn about [Permanent Liquidity Rules](./permanent-liquidity-rules.md).
