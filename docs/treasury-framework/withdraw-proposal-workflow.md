---
title: Withdraw Proposal Workflow
sidebar_position: 2
description: Understanding the treasury withdrawal proposal process
---

# Withdraw Proposal Workflow

Protocol (TCP) uses a **formal proposal workflow** for all treasury withdrawals, ensuring transparency and enabling community oversight.

## Proposal Workflow

### Step 1: Proposal Creation

**What Happens**
- Owner proposes withdrawal
- Amount specified
- Recipient specified
- Proposal recorded on-chain

**On-Chain**
- Proposal event emitted
- Parameters stored
- Timelock begins
- Community notified

**Example**
```
Owner proposes withdrawal:
- Amount: 50,000 TCP
- Recipient: Operations wallet
- Proposal recorded on-chain
```

### Step 2: Timelock Period

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

**Example**
```
Timelock Period: 7 days
Day 0: Proposal created
Days 1-6: Waiting period
Day 7: Execution available
```

### Step 3: Execution or Cancellation

**Execution Path**
```
1. Owner executes proposal
2. Tokens transferred
3. Event logged
4. Completion
```

**Cancellation Path**
```
1. Owner cancels proposal
2. Proposal marked cancelled
3. Event logged
4. No tokens transferred
```

## Proposal Examples

### Example 1: Operational Funding

```
Day 0:
- Owner proposes withdrawal
- Amount: 100,000 TCP
- Recipient: Operations wallet
- Purpose: Q1 operations
- Proposal recorded on-chain

Days 1-6:
- Timelock period
- Community assesses proposal
- Proposal visible on PolygonScan
- Proposal can be cancelled if needed

Day 7:
- Timelock expires
- Owner executes withdrawal
- 100,000 TCP transferred
- Event logged on PolygonScan

Completion:
- Operations funded
- Treasury balance reduced
- Transparency maintained
- Audit trail recorded
```

### Example 2: Strategic Initiative

```
Day 0:
- Owner proposes withdrawal
- Amount: 50,000 TCP
- Recipient: Partnership wallet
- Purpose: Strategic partnership
- Proposal recorded on-chain

Days 1-6:
- Timelock period
- Community assesses partnership
- Proposal visible on PolygonScan
- Community provides feedback

Day 5:
- Community raises concerns
- Owner cancels proposal
- Proposal cancelled on-chain
- Event logged on PolygonScan

Completion:
- Proposal cancelled
- Treasury protected
- Community satisfied
- Transparency maintained
```

## Proposal Transparency

### Public Information

All proposal information is public:

✅ **Proposal Details** — Amount, recipient, timing  
✅ **Timelock Status** — How long until execution  
✅ **Execution Status** — Whether executed  
✅ **Cancellation Status** — Whether cancelled  
✅ **Withdrawal History** — Past withdrawals  

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

## Proposal Best Practices

### For Administrators

✅ **Communicate proposals** — Inform community of proposals  
✅ **Explain reasoning** — Explain purpose of withdrawals  
✅ **Allow review time** — Give community time to assess  
✅ **Respond to feedback** — Address community concerns  
✅ **Be transparent** — Maintain complete transparency  

### For Community

✅ **Monitor proposals** — Watch for new proposals  
✅ **Assess impact** — Evaluate withdrawal purposes  
✅ **Provide feedback** — Share concerns and suggestions  
✅ **Request cancellation** — Ask for cancellation if needed  
✅ **Stay vigilant** — Maintain security awareness  

## Key Takeaways

1. **Formal process** — All withdrawals follow formal process
2. **Transparent** — All proposals visible on-chain
3. **Timelock-protected** — Waiting period enables oversight
4. **Cancellable** — Ability to stop proposals
5. **Auditable** — Complete audit trail available

---

**Next:** Learn about [Timelock Rules](./timelock-rules.md).
