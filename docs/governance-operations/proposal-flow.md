---
title: Proposal Flow
sidebar_position: 3
description: Understanding TCP's proposal creation and execution process
---

# Proposal Flow

Protocol (TCP) uses a **formal proposal flow** for all critical operations, ensuring transparency and enabling community oversight.

## Proposal Workflow

### Standard Proposal Flow

```
1. Proposal Creation
   ↓
2. Parameter Recording
   ↓
3. Timelock Begins
   ↓
4. Community Monitoring
   ↓
5. Execution Window Opens
   ↓
6. Execution (or Cancellation)
   ↓
7. Completion
```

## Step 1: Proposal Creation

**What Happens**
- Owner or multisig creates proposal
- Operation type specified
- Parameters recorded
- Proposal ID assigned

**On-Chain**
- Proposal event emitted
- Proposal recorded in contract
- Timelock begins
- Community notified

**Example**
```
Owner proposes treasury withdrawal
- Amount: 50,000 TCP
- Recipient: Operations wallet
- Proposal ID: 1
- Timelock: 7 days
```

## Step 2: Parameter Recording

**What Happens**
- All proposal parameters recorded
- Recipient address verified
- Amount verified
- Execution time calculated

**On-Chain**
- Parameters stored in contract
- Verification performed
- Event emitted with details
- Audit trail created

**Example**
```
Proposal 1 Parameters:
- Type: Treasury Withdrawal
- Amount: 50,000 TCP
- Recipient: 0x123...
- Execution Time: Day 7
- Status: Pending
```

## Step 3: Timelock Begins

**What Happens**
- Waiting period begins
- Countdown starts
- Community can monitor
- Proposal can be cancelled

**On-Chain**
- Timelock recorded
- Countdown visible
- Cancellation available
- Transparency maintained

**Example**
```
Timelock Period: 7 days
Day 0: Proposal created
Days 1-6: Waiting period
Day 7: Execution available
```

## Step 4: Community Monitoring

**What Happens**
- Community monitors proposal
- Assesses impact
- Provides feedback
- Requests cancellation if needed

**On-Chain**
- Proposal visible on PolygonScan
- Community can verify details
- Event logs available
- Audit trail visible

**Example**
```
Community Reviews:
- Assesses withdrawal purpose
- Evaluates recipient
- Checks treasury balance
- Provides feedback
```

## Step 5: Execution Window Opens

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

**Example**
```
Day 7: Timelock expires
- Execution available
- Execution window opens
- Owner can execute
```

## Step 6: Execution or Cancellation

### Execution Path

**What Happens**
- Owner executes proposal
- Operation completes
- Funds transferred
- Event logged

**On-Chain**
- Execution function called
- Operation executed
- Event emitted
- Audit trail recorded

**Example**
```
Owner executes withdrawal:
- 50,000 TCP transferred
- Recipient receives funds
- Event logged on PolygonScan
```

### Cancellation Path

**What Happens**
- Owner cancels proposal
- Operation prevented
- Proposal marked cancelled
- Event logged

**On-Chain**
- Cancellation function called
- Proposal marked cancelled
- Event emitted
- Audit trail recorded

**Example**
```
Owner cancels proposal:
- Proposal cancelled
- No funds transferred
- Event logged on PolygonScan
```

## Step 7: Completion

**What Happens**
- Operation completes
- Proposal closed
- Audit trail complete
- Transparency maintained

**On-Chain**
- Final event emitted
- Proposal status updated
- Audit trail recorded
- History available

**Example**
```
Proposal 1 Completed:
- Status: Executed
- Amount: 50,000 TCP
- Recipient: 0x123...
- Date: Day 7
- Audit Trail: Complete
```

## Proposal Types

### Treasury Withdrawal Proposal

**Flow**
1. Owner proposes withdrawal
2. Amount and recipient specified
3. Timelock begins (7 days)
4. Community monitors
5. Owner executes after timelock
6. Funds transferred

**Example**
```
Proposal: Treasury Withdrawal
Amount: 100,000 TCP
Recipient: Operations wallet
Timelock: 7 days
Status: Executed
```

### Liquidity Withdrawal Proposal

**Flow**
1. Owner proposes withdrawal
2. Amount specified
3. Daily limit checked
4. Timelock begins (7 days)
5. Community monitors
6. Owner executes after timelock
7. LP transferred

**Example**
```
Proposal: Liquidity Withdrawal
Amount: 500 LP
Daily Limit: 1000 LP
Timelock: 7 days
Status: Executed
```

### Parameter Change Proposal

**Flow**
1. Owner proposes change
2. New parameter specified
3. Timelock begins (7 days)
4. Community monitors
5. Multisig approves
6. Owner executes after timelock
7. Parameter updated

**Example**
```
Proposal: Parameter Change
Parameter: Reward Rate
Old Value: 10%
New Value: 12%
Timelock: 7 days
Status: Executed
```

## Proposal Transparency

### Public Information

All proposal information is public:

✅ **Proposal Details** — What operation is proposed  
✅ **Parameters** — Specific details of proposal  
✅ **Timelock Status** — How long until execution  
✅ **Execution Status** — Whether executed or cancelled  
✅ **Audit Trail** — Complete history  

### Verification Methods

You can verify proposal information:

1. **PolygonScan**
   - View proposal events
   - Check execution times
   - Monitor cancellations
   - Track executions

2. **Contract Functions**
   - Call getPendingProposal()
   - Check proposal status
   - Verify execution time
   - View execution history

3. **Community Tools**
   - Use proposal dashboards
   - Monitor proposals
   - Track execution times
   - Analyze patterns

## Best Practices

### For Administrators

✅ **Communicate proposals** — Inform community of proposals  
✅ **Explain reasoning** — Explain purpose of proposals  
✅ **Allow review time** — Give community time to assess  
✅ **Respond to feedback** — Address community concerns  
✅ **Be transparent** — Maintain complete transparency  

### For Community

✅ **Monitor proposals** — Watch for new proposals  
✅ **Assess impact** — Evaluate proposal impact  
✅ **Provide feedback** — Share concerns and suggestions  
✅ **Request cancellation** — Ask for cancellation if needed  
✅ **Stay vigilant** — Maintain security awareness  

## Key Takeaways

1. **Formal process** — All proposals follow formal flow
2. **Transparent** — All proposals visible on-chain
3. **Timelock-protected** — Waiting period enables oversight
4. **Cancellable** — Ability to stop proposals
5. **Auditable** — Complete audit trail available

---

**Next:** Learn about [Emergency Procedures](./emergency-procedures.md) and incident response.
