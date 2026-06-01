---
title: Timelocks
sidebar_position: 3
description: Understanding TCP's timelock protection mechanisms
---

# Timelocks

**Timelocks** are a critical security mechanism in Protocol (TCP) that prevent instant-action risks by requiring waiting periods before critical operations can execute.

## What are Timelocks?

A timelock is a smart contract mechanism that:
1. Records a proposed operation
2. Enforces a waiting period
3. Allows execution only after the period expires
4. Enables cancellation before execution

## Timelock Objectives

### 1. Prevent Instant-Action Risks

**Problem**
- Instant withdrawals can cause sudden loss of funds
- No time for community to react
- Increased risk of abuse

**Solution**
- Require waiting period before execution
- Community has time to monitor
- Ability to cancel if needed
- Reduced instant-action risk

### 2. Enable Community Oversight

**Problem**
- Hidden operations reduce transparency
- Community can't monitor or react
- Difficult to detect abuse

**Solution**
- Proposals visible on-chain
- Community can monitor
- Time to assess and react
- Transparent operations

### 3. Improve Operational Discipline

**Problem**
- Instant operations can be mistakes
- No time for review
- Difficult to prevent errors

**Solution**
- Waiting period allows review
- Mistakes can be caught
- Proposals can be cancelled
- Improved discipline

### 4. Build Community Trust

**Problem**
- Instant operations reduce trust
- Community worried about abuse
- Difficult to verify safety

**Solution**
- Visible waiting periods
- Community can verify
- Cancellation mechanism
- Increased trust

## Timelock Implementation

### Timelock Process

```
1. Proposal Creation
   - Operation proposed
   - Parameters recorded
   - Timelock begins
   - Event emitted

2. Waiting Period
   - Specified duration passes
   - Community monitors
   - Proposal can be cancelled
   - Countdown visible

3. Execution Window
   - After timelock expires
   - Operation can execute
   - Caller initiates execution
   - Operation completes

4. Completion
   - Operation executed
   - Event emitted
   - Transparency maintained
   - Audit trail recorded
```

### Timelock Parameters

| Parameter | Value |
|-----------|-------|
| **Treasury Withdrawal Timelock** | 7 days (example) |
| **Liquidity Withdrawal Timelock** | 7 days (example) |
| **Parameter Change Timelock** | 7 days (example) |
| **Upgrade Timelock** | 14 days (example) |

## Timelock Operations

### Treasury Withdrawal Timelock

**Operation**
- Withdraw tokens from treasury

**Timelock**
- 7 days (example)

**Process**
```
Day 0: Proposal created
Days 1-6: Waiting period
Day 7: Execution available
Day 8+: Execution window
```

### Liquidity Withdrawal Timelock

**Operation**
- Withdraw LP from liquidity manager

**Timelock**
- 7 days (example)

**Process**
```
Day 0: Proposal created
Days 1-6: Waiting period
Day 7: Execution available
Day 8+: Execution window
```

### Parameter Change Timelock

**Operation**
- Change critical parameters

**Timelock**
- 7 days (example)

**Process**
```
Day 0: Change proposed
Days 1-6: Waiting period
Day 7: Change available
Day 8+: Execution window
```

## Cancellation Mechanism

### Why Cancellation Matters

Cancellation allows:
- Stopping mistakes
- Preventing abuse
- Responding to concerns
- Maintaining safety

### How Cancellation Works

```
1. Proposal created
   - Timelock begins
   - Cancellation available

2. Community reviews
   - Proposal assessed
   - Concerns raised
   - Feedback provided

3. Cancellation decision
   - If concerns valid
   - Proposal cancelled
   - Operation prevented

4. Completion
   - Cancellation logged
   - Transparency maintained
   - Community satisfied
```

### Who Can Cancel

Cancellation can be performed by:
- Owner (for owner-proposed operations)
- Multisig (for multisig-proposed operations)
- Community (if governance enabled)

## Timelock Transparency

### Public Information

All timelock information is public:

✅ **Proposal Details** — What operation is proposed  
✅ **Timelock Duration** — How long to wait  
✅ **Execution Time** — When operation can execute  
✅ **Cancellation Status** — Whether proposal is cancelled  
✅ **Execution Status** — Whether operation executed  

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

## Timelock Examples

### Example 1: Treasury Withdrawal

```
Scenario: Withdraw 50,000 TCP for operations

Day 0 (Monday):
- Owner proposes withdrawal
- Amount: 50,000 TCP
- Recipient: Operations wallet
- Timelock: 7 days
- Event logged on PolygonScan

Days 1-6 (Tuesday-Sunday):
- Community monitors proposal
- Proposal visible on PolygonScan
- Community assesses withdrawal
- Proposal can be cancelled if needed

Day 7 (Monday):
- Timelock expires
- Withdrawal can execute
- Owner calls executeWithdrawal()
- Tokens transferred
- Event logged on PolygonScan

Completion:
- Operations funded
- Transparency maintained
- Community satisfied
```

### Example 2: Parameter Change

```
Scenario: Change reward rate from 10% to 12%

Day 0 (Monday):
- Multisig proposes change
- New rate: 12% APY
- Timelock: 7 days
- Event logged on PolygonScan

Days 1-6 (Tuesday-Sunday):
- Community monitors proposal
- Proposal visible on PolygonScan
- Community assesses impact
- Proposal can be cancelled if needed

Day 7 (Monday):
- Timelock expires
- Change can execute
- Multisig calls executeChange()
- Parameter updated
- Event logged on PolygonScan

Completion:
- Reward rate updated
- Transparency maintained
- Community satisfied
```

## Timelock Security

### Benefits

✅ **Prevents instant abuse** — Waiting period prevents sudden actions  
✅ **Enables oversight** — Community has time to monitor  
✅ **Allows cancellation** — Mistakes can be stopped  
✅ **Builds trust** — Visible safeguards build confidence  
✅ **Maintains discipline** — Enforces operational discipline  

### Limitations

⚠️ **Delays operations** — Waiting period delays execution  
⚠️ **Requires monitoring** — Community must monitor proposals  
⚠️ **Not foolproof** — Doesn't prevent all risks  
⚠️ **Requires discipline** — Must be consistently applied  

## Best Practices

### For Administrators

✅ **Use timelocks** — Always use timelocks for critical operations  
✅ **Communicate proposals** — Inform community of proposals  
✅ **Allow review time** — Give community time to assess  
✅ **Be transparent** — Explain reasoning for proposals  
✅ **Respect feedback** — Consider community feedback  

### For Community

✅ **Monitor proposals** — Watch for new proposals  
✅ **Assess impact** — Evaluate proposal impact  
✅ **Provide feedback** — Share concerns and suggestions  
✅ **Request cancellation** — Ask for cancellation if needed  
✅ **Stay vigilant** — Maintain security awareness  

## Key Takeaways

1. **Prevent instant actions** — Waiting periods prevent sudden operations
2. **Enable oversight** — Community has time to monitor
3. **Allow cancellation** — Mistakes can be stopped
4. **Build trust** — Visible safeguards build confidence
5. **Maintain discipline** — Enforces operational discipline

---

**Next:** Learn about [Liquidity Protection](./liquidity-protection.md) and advanced LP safeguards.
