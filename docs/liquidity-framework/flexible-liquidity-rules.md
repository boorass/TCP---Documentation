---
title: Flexible Liquidity Rules
sidebar_position: 3
description: Rules and mechanics for TCP's flexible liquidity portion
---

# Flexible Liquidity Rules

The **Flexible Liquidity** portion (15% of total LP) is protected with daily withdrawal limits and timelock enforcement.

## Flexible Portion Characteristics

| Property | Value |
|----------|-------|
| **Portion of Total LP** | 15% of total LP |
| **Daily Withdrawal Limit** | Configurable (e.g., 1% of flexible) |
| **Withdrawal Process** | Proposal + Timelock |
| **Lock-Up Period** | None |
| **Consumption Tracking** | Daily |

## Daily Limit Mechanism

### How Daily Limits Work

```
Total Flexible LP: 1000 LP
Daily Limit: 1% = 10 LP per day

Day 1:
- Available: 10 LP
- Withdraw: 5 LP
- Consumed: 5 LP
- Remaining: 5 LP

Day 2:
- Available: 10 LP (resets)
- Withdraw: 8 LP
- Consumed: 8 LP
- Remaining: 2 LP

Day 3:
- Available: 10 LP (resets)
- Withdraw: 10 LP
- Consumed: 10 LP
- Remaining: 0 LP
```

### Limit Enforcement

Daily limits are enforced by smart contract:
- Consumption tracked per day
- Resets daily
- Cannot exceed limit
- Prevents large sudden withdrawals

### Limit Verification

You can verify daily limit status:
1. **PolygonScan** — Check limit events
2. **Contract Functions** — Call getDailyLimitStatus()
3. **Community Tools** — Use LP dashboards
4. **Real-time** — See current consumption

## Withdrawal Process

### Step-by-Step

```
1. Check Daily Limit
   - Daily limit: 10 LP
   - Current consumption: 3 LP
   - Available: 7 LP

2. Propose Withdrawal
   - Owner proposes withdrawal
   - Amount: 5 LP (within limit)
   - Proposal recorded on-chain

3. Timelock Period
   - 7 days (example)
   - Community monitors
   - Proposal can be cancelled

4. Execute Withdrawal
   - After timelock expires
   - Owner executes withdrawal
   - 5 LP transferred

5. Completion
   - LP balance updated
   - Daily consumption updated
   - Event logged on-chain
   - Transparency maintained
```

### Withdrawal Limits

Withdrawals are limited by:
- **Daily limit** — Cannot exceed daily cap
- **Timelock delay** — Must wait for timelock
- **Proposal requirement** — Must follow proposal process
- **Community oversight** — Community can monitor

## Flexible LP Examples

### Example 1: Daily Limit Consumption

```
Flexible LP: 1000 LP
Daily Limit: 1% = 10 LP per day

Day 1:
- Propose withdrawal: 8 LP
- Within limit: Yes
- Proposal recorded

Day 2:
- Timelock expires
- Execute withdrawal: 8 LP
- Daily consumption: 8 LP
- Remaining: 2 LP

Day 2 (later):
- Propose withdrawal: 5 LP
- Within limit: No (only 2 LP remaining)
- Proposal rejected

Day 3:
- Daily limit resets
- Available: 10 LP
- Propose withdrawal: 5 LP
- Within limit: Yes
- Proposal recorded

Day 4:
- Timelock expires
- Execute withdrawal: 5 LP
- Daily consumption: 5 LP
- Remaining: 5 LP
```

### Example 2: Multiple Withdrawals

```
Flexible LP: 1000 LP
Daily Limit: 1% = 10 LP per day

Day 1:
- Propose withdrawal: 3 LP
- Proposal recorded

Day 2:
- Timelock expires
- Execute withdrawal: 3 LP
- Daily consumption: 3 LP
- Remaining: 7 LP

Day 2 (later):
- Propose withdrawal: 7 LP
- Within limit: Yes
- Proposal recorded

Day 3:
- Timelock expires
- Execute withdrawal: 7 LP
- Daily consumption: 10 LP
- Remaining: 0 LP

Day 4:
- Daily limit resets
- Available: 10 LP
- Can propose new withdrawal
```

## Flexible LP Transparency

### Public Information

All flexible LP information is public:

✅ **LP Balance** — Current LP holdings  
✅ **Daily Limit** — Daily withdrawal limit  
✅ **Daily Consumption** — Current day consumption  
✅ **Remaining Available** — Available for withdrawal  
✅ **Withdrawal History** — Past withdrawals  

### Verification Methods

You can verify flexible LP information:

1. **PolygonScan**
   - Check withdrawal events
   - View daily consumption
   - Monitor limit status
   - Track withdrawals

2. **Contract Functions**
   - Call getFlexibleLPBalance()
   - Call getDailyLimitStatus()
   - Check remaining available
   - View withdrawal history

3. **Community Tools**
   - Use LP dashboards
   - Monitor daily consumption
   - Track limit status
   - Analyze patterns

## Flexible LP Benefits

### For Operations

✅ **Operational flexibility** — Some LP available for operations  
✅ **Daily limits** — Prevents large sudden withdrawals  
✅ **Timelock protection** — Waiting period enables oversight  
✅ **Community oversight** — Community can monitor  

### For Investors

✅ **Confidence** — Daily limits prevent abuse  
✅ **Stability** — Limits support price stability  
✅ **Transparency** — All operations visible  
✅ **Oversight** — Community can monitor  

## Key Takeaways

1. **Daily limits** — Caps on daily withdrawals
2. **Consumption tracking** — Daily consumption tracked
3. **Resets daily** — Limit resets each day
4. **Timelock enforcement** — All withdrawals require delays
5. **Complete transparency** — All operations logged on-chain

---

**Next:** Learn about [Timelock Workflow](./timelock-workflow.md) for withdrawal processes.
