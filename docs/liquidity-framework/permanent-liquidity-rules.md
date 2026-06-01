---
title: Permanent Liquidity Rules
sidebar_position: 2
description: Rules and mechanics for TCP's permanent liquidity protection
---

# Permanent Liquidity Rules

The **Permanent Liquidity** portion (85% of total LP) is protected with a long-term lock and strict withdrawal rules.

## Permanent Portion Characteristics

| Property | Value |
|----------|-------|
| **Portion of Total LP** | 85% |
| **Lock Duration** | 365+ days |
| **Early Withdrawal** | Not allowed |
| **Lock Extension** | Allowed |
| **Withdrawal After Expiration** | Proposal + Timelock required |

## Lock Mechanism

### Initial Lock

When LP is locked:
1. 85% of LP designated as permanent
2. Lock duration set (365+ days)
3. Unlock date calculated
4. Lock recorded on-chain
5. Event emitted

### Lock Enforcement

The lock is enforced by smart contract:
- Cannot be bypassed
- Cannot be shortened
- Cannot be circumvented
- Immutable on-chain

### Lock Verification

You can verify lock status:
1. **PolygonScan** — Check lock events
2. **Contract Functions** — Call getLockStatus()
3. **Community Tools** — Use LP dashboards
4. **Countdown** — See time remaining

## Lock Extension

### Why Extend?

Lock can be extended to:
- Provide additional security
- Demonstrate long-term commitment
- Build investor confidence
- Support price stability

### How to Extend

```
1. Lock expires in 30 days
2. Owner calls extendLock()
3. Additional duration specified (e.g., 365 days)
4. New unlock date calculated
5. Extension recorded on-chain
6. Event emitted
```

### Extension Benefits

✅ **Additional security** — Extends protection period  
✅ **Demonstrates commitment** — Shows long-term thinking  
✅ **Builds confidence** — Investors see extended protection  
✅ **Supports stability** — Longer lock supports price stability  

## Withdrawal After Expiration

### When Lock Expires

After 365+ days:
1. Lock expires
2. Withdrawal becomes possible
3. Owner can propose withdrawal
4. Timelock begins
5. After timelock, withdrawal can execute

### Withdrawal Process

```
1. Lock Expires
   - 365+ day lock period complete
   - Withdrawal becomes possible

2. Propose Withdrawal
   - Owner proposes withdrawal
   - Amount specified
   - Proposal recorded on-chain

3. Timelock Period
   - 7 days (example)
   - Community monitors
   - Proposal can be cancelled

4. Execute Withdrawal
   - After timelock expires
   - Owner executes withdrawal
   - LP transferred

5. Completion
   - LP balance updated
   - Event logged on-chain
   - Transparency maintained
```

### Withdrawal Limits

Withdrawals are limited by:
- **Maximum amount** — Cannot exceed available LP
- **Timelock delay** — Must wait for timelock
- **Proposal requirement** — Must follow proposal process
- **Community oversight** — Community can monitor

## Permanent LP Examples

### Example 1: 365-Day Lock

```
Day 0:
- Lock 1000 LP
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

### Example 2: Lock Extension

```
Day 0:
- Lock 1000 LP
- Lock duration: 365 days
- Unlock date: Day 365

Day 350:
- Lock expires in 15 days
- Owner calls extendLock()
- Additional duration: 365 days
- New unlock date: Day 715
- Extension recorded on-chain

Day 715:
- Extended lock expires
- Withdrawal becomes possible
- Owner can propose withdrawal
- Timelock begins

Completion:
- LP protected for 715 days total
- Extended protection provided
- Investor confidence increased
```

## Permanent LP Transparency

### Public Information

All permanent LP information is public:

✅ **LP Balance** — Current LP holdings  
✅ **Lock Status** — Lock expiration date  
✅ **Lock Duration** — How long locked  
✅ **Unlock Date** — When lock expires  
✅ **Withdrawal History** — Past withdrawals  

### Verification Methods

You can verify permanent LP information:

1. **PolygonScan**
   - Check lock events
   - View lock status
   - Monitor lock expiration
   - Track withdrawals

2. **Contract Functions**
   - Call getLockStatus()
   - Check unlock date
   - Verify lock duration
   - View lock history

3. **Community Tools**
   - Use LP dashboards
   - Monitor lock status
   - Track lock expiration
   - Analyze patterns

## Permanent LP Benefits

### For Investors

✅ **Long-term protection** — 365+ day lock  
✅ **Confidence** — Demonstrates commitment  
✅ **Stability** — Supports price stability  
✅ **Transparency** — All information public  

### For the Protocol

✅ **Sustainability** — Long-term LP guaranteed  
✅ **Credibility** — Professional approach  
✅ **Institutional appeal** — Attracts serious investors  
✅ **Market stability** — Supports stable prices  

## Key Takeaways

1. **Long-term lock** — 365+ day lock enforced
2. **Cannot be shortened** — Lock cannot be reduced
3. **Can be extended** — Lock can be extended
4. **Proposal-based withdrawal** — Formal process required
5. **Complete transparency** — All operations logged on-chain

---

**Next:** Learn about [Flexible Liquidity Rules](./flexible-liquidity-rules.md).
