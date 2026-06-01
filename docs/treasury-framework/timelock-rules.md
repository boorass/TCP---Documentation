---
title: Timelock Rules
sidebar_position: 3
description: Understanding treasury timelock enforcement
---

# Timelock Rules

Protocol (TCP) enforces **timelocks on all treasury withdrawals** to enable community oversight and prevent instant-action risks.

## Timelock Purpose

Timelocks serve to:
- **Prevent instant withdrawals** — Waiting period required
- **Enable oversight** — Community has time to monitor
- **Allow cancellation** — Ability to stop withdrawals
- **Build confidence** — Visible safeguards build trust

## Timelock Parameters

| Parameter | Value |
|-----------|-------|
| **Timelock Duration** | 7 days (example) |
| **Proposal Creation** | Immediate |
| **Execution Window** | After timelock expires |
| **Cancellation** | Anytime before execution |

## Timelock Enforcement

### How Timelocks Work

```
1. Proposal Created
   - Timelock begins
   - Countdown starts
   - Community notified

2. Waiting Period
   - 7 days (example)
   - Community monitors
   - Proposal can be cancelled

3. Execution Available
   - After 7 days
   - Withdrawal can execute
   - Execution window opens

4. Execution or Cancellation
   - Owner executes or cancels
   - Operation completes
   - Event logged
```

### Timelock Verification

You can verify timelock status:
1. **PolygonScan** — Check timelock events
2. **Contract Functions** — Call getTimeUntilExecution()
3. **Community Tools** — Use timelock dashboards
4. **Real-time** — See countdown

## Timelock Examples

### Example 1: Successful Withdrawal

```
Day 0 (Monday):
- Owner proposes withdrawal
- Amount: 50,000 TCP
- Timelock: 7 days
- Event logged on PolygonScan

Days 1-6 (Tuesday-Sunday):
- Timelock period active
- Community monitors proposal
- Proposal visible on PolygonScan
- Community assesses withdrawal

Day 7 (Monday):
- Timelock expires
- Owner executes withdrawal
- 50,000 TCP transferred
- Event logged on PolygonScan

Completion:
- Withdrawal executed
- Treasury balance reduced
- Transparency maintained
```

### Example 2: Cancelled Withdrawal

```
Day 0 (Monday):
- Owner proposes withdrawal
- Amount: 50,000 TCP
- Timelock: 7 days
- Event logged on PolygonScan

Day 3 (Thursday):
- Community raises concerns
- Owner cancels proposal
- Proposal cancelled on-chain
- Event logged on PolygonScan

Completion:
- Proposal cancelled
- No withdrawal executed
- Community satisfied
- Transparency maintained
```

## Timelock Benefits

### For the Protocol

✅ **Prevents instant withdrawals** — Waiting period required  
✅ **Enables oversight** — Community has time to monitor  
✅ **Allows cancellation** — Ability to stop withdrawals  
✅ **Builds confidence** — Visible safeguards build trust  

### For Investors

✅ **Confidence** — Visible safeguards build confidence  
✅ **Oversight** — Community can monitor  
✅ **Transparency** — All operations visible  
✅ **Accountability** — Clear responsibility  

## Key Takeaways

1. **Waiting period** — Timelocks enforce waiting periods
2. **Community oversight** — Community has time to monitor
3. **Cancellation available** — Ability to stop proposals
4. **Transparent** — All timelocks visible on-chain
5. **Enforced** — Timelocks enforced by smart contracts

---

**Next:** Learn about [Cancellation Rules](./cancellation-rules.md).
