---
title: Timelock Workflow
sidebar_position: 4
description: Understanding timelock enforcement in liquidity withdrawals
---

# Timelock Workflow

Protocol (TCP) enforces **timelocks on all liquidity withdrawals** to enable community oversight and prevent instant-action risks.

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

## Withdrawal Workflow

### Phase 1: Proposal Creation

**What Happens**
- Owner proposes withdrawal
- Parameters recorded
- Timelock begins
- Event emitted

**On-Chain**
- Proposal recorded
- Timelock started
- Event logged
- Community notified

**Timeline**
- Immediate

**Example**
```
Owner proposes withdrawal:
- Amount: 500 LP
- Recipient: Operations wallet
- Timelock: 7 days
- Proposal recorded on-chain
```

### Phase 2: Timelock Period

**What Happens**
- Waiting period begins
- Community monitors
- Proposal can be cancelled
- Countdown visible

**On-Chain**
- Timelock enforced
- Countdown visible
- Cancellation available
- Transparency maintained

**Timeline**
- 7 days (example)

**Example**
```
Days 1-6:
- Timelock period active
- Community monitors proposal
- Proposal visible on PolygonScan
- Proposal can be cancelled if needed
```

### Phase 3: Execution Window

**What Happens**
- Timelock expires
- Execution becomes available
- Proposal can be executed
- Execution window opens

**On-Chain**
- Timelock expires
- Execution function available
- Proposal ready to execute
- Community notified

**Timeline**
- After timelock expires

**Example**
```
Day 7:
- Timelock expires
- Execution available
- Owner can execute
- Execution window opens
```

### Phase 4: Execution or Cancellation

**Execution Path**
```
1. Owner executes withdrawal
2. LP transferred
3. Event logged
4. Completion
```

**Cancellation Path**
```
1. Owner cancels proposal
2. Proposal marked cancelled
3. Event logged
4. No LP transferred
```

## Timelock Examples

### Example 1: Successful Withdrawal

```
Day 0 (Monday):
- Owner proposes withdrawal
- Amount: 500 LP
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
- 500 LP transferred
- Event logged on PolygonScan

Completion:
- LP transferred
- Balance updated
- Transparency maintained
```

### Example 2: Cancelled Withdrawal

```
Day 0 (Monday):
- Owner proposes withdrawal
- Amount: 500 LP
- Timelock: 7 days
- Event logged on PolygonScan

Day 3 (Thursday):
- Community raises concerns
- Owner cancels proposal
- Proposal marked cancelled
- Event logged on PolygonScan

Completion:
- Proposal cancelled
- No LP transferred
- Community satisfied
- Transparency maintained
```

### Example 3: Multiple Proposals

```
Day 0:
- Proposal 1 created
- Timelock begins

Day 3:
- Proposal 2 created
- Timelock begins

Day 7:
- Proposal 1 timelock expires
- Proposal 1 executed
- 500 LP transferred

Day 10:
- Proposal 2 timelock expires
- Proposal 2 executed
- 300 LP transferred

Completion:
- Both proposals executed
- 800 LP total transferred
- Transparency maintained
```

## Timelock Transparency

### Public Information

All timelock information is public:

✅ **Proposal Details** — What withdrawal is proposed  
✅ **Timelock Duration** — How long to wait  
✅ **Execution Time** — When proposal can execute  
✅ **Cancellation Status** — Whether proposal is cancelled  
✅ **Execution Status** — Whether proposal executed  

### Verification Methods

You can verify timelock information:

1. **PolygonScan**
   - View proposal events
   - Check execution times
   - Monitor cancellations
   - Track executions

2. **Contract Functions**
   - Call getTimeUntilExecution()
   - Check proposal status
   - Verify cancellation status
   - View execution history

3. **Community Tools**
   - Use timelock dashboards
   - Monitor proposals
   - Track execution times
   - Analyze patterns

## Timelock Best Practices

### For Administrators

✅ **Communicate proposals** — Inform community of proposals  
✅ **Explain reasoning** — Explain purpose of withdrawals  
✅ **Allow review time** — Give community time to assess  
✅ **Respond to feedback** — Address community concerns  
✅ **Be transparent** — Maintain complete transparency  

### For Community

✅ **Monitor proposals** — Watch for new proposals  
✅ **Assess impact** — Evaluate withdrawal impact  
✅ **Provide feedback** — Share concerns and suggestions  
✅ **Request cancellation** — Ask for cancellation if needed  
✅ **Stay vigilant** — Maintain security awareness  

## Key Takeaways

1. **Waiting period** — Timelocks enforce waiting periods
2. **Community oversight** — Community has time to monitor
3. **Cancellation available** — Ability to stop proposals
4. **Transparent** — All timelocks visible on-chain
5. **Enforced** — Timelocks enforced by smart contracts

---

**Next:** Learn about [Monitoring & Transparency](./monitoring-transparency.md).
