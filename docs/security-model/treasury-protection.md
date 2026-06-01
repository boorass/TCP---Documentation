---
title: Treasury Protection
sidebar_position: 5
description: TCP's treasury safeguards and withdrawal discipline
---

# Treasury Protection

Protocol (TCP) protects its treasury through **disciplined, timelock-protected withdrawal mechanisms** that prevent instant access to strategic reserves.

## Treasury Protection Principles

### 1. Non-Instantaneous Withdrawals

**Principle**
- Withdrawals cannot execute immediately
- Waiting period required
- Community has time to react
- Prevents sudden loss of funds

**Implementation**
- Proposal-based system
- Timelock enforcement
- Cancellation mechanism
- On-chain transparency

### 2. Formal Proposal Process

**Principle**
- All withdrawals require formal proposal
- Parameters explicitly specified
- Proposal recorded on-chain
- Community can assess

**Implementation**
- Proposal creation function
- Parameter recording
- Event emission
- Audit trail

### 3. Timelock Delays

**Principle**
- Waiting period before execution
- Community monitoring time
- Ability to cancel
- Operational discipline

**Implementation**
- Configurable timelock (e.g., 7 days)
- Countdown visible on-chain
- Cancellation available
- Enforcement by smart contract

### 4. Cancellation Mechanism

**Principle**
- Ability to stop pending withdrawals
- Prevents mistakes
- Responds to concerns
- Maintains safety

**Implementation**
- Cancellation function
- Owner/multisig authorization
- Event logging
- Immediate effect

## Treasury Withdrawal Process

### Step-by-Step

```
1. Proposal Creation (Day 0)
   - Owner proposes withdrawal
   - Amount: 50,000 TCP
   - Recipient: Operations wallet
   - Proposal recorded on-chain
   - Event emitted

2. Timelock Period (Days 1-6)
   - 7-day waiting period
   - Community monitors proposal
   - Proposal details visible on PolygonScan
   - Proposal can be cancelled if needed

3. Execution Window (Day 7+)
   - Timelock expires
   - Withdrawal can execute
   - Owner calls executeWithdrawal()
   - Tokens transferred to recipient

4. Completion
   - Treasury balance updated
   - Event emitted
   - Transparency maintained
   - Audit trail recorded
```

## Treasury Protection Features

### Access Control

Treasury access is controlled through:
- Owner authorization required
- Multisig approval for large withdrawals
- Explicit permission checks
- Role-based access

### Amount Limits

Treasury withdrawals are limited by:
- Maximum withdrawal amount
- Cannot exceed treasury balance
- Enforced by smart contract
- Prevents overdrafts

### Timelock Enforcement

Timelocks are enforced by:
- Smart contract code
- Cannot be bypassed
- Countdown visible on-chain
- Immutable enforcement

### Event Logging

All treasury operations are logged:
- Proposal creation logged
- Execution logged
- Cancellation logged
- Complete audit trail

## Treasury Transparency

### Public Information

All treasury information is public:

✅ **Treasury Balance** — Current holdings  
✅ **Pending Proposals** — Proposed withdrawals  
✅ **Proposal Details** — Amount, recipient, timing  
✅ **Execution Status** — Whether proposal executed  
✅ **Withdrawal History** — Past withdrawals  

### Verification Methods

You can verify treasury information:

1. **PolygonScan**
   - Check treasury balance
   - View proposal events
   - Monitor execution events
   - Track withdrawal history

2. **Contract Functions**
   - Call getTreasuryBalance()
   - Call getPendingProposal()
   - Call getProposalStatus()
   - Call getTimeUntilExecution()

3. **Community Tools**
   - Use treasury dashboards
   - Monitor proposals
   - Track withdrawals
   - Analyze patterns

## Treasury Protection Benefits

### For the Protocol

✅ **Safeguards reserves** — Protects strategic assets  
✅ **Prevents abuse** — Timelocks prevent misuse  
✅ **Maintains discipline** — Enforces operational discipline  
✅ **Builds credibility** — Professional approach builds trust  

### For Investors

✅ **Confidence** — Protected treasury builds confidence  
✅ **Transparency** — All operations visible and verifiable  
✅ **Oversight** — Community can monitor treasury  
✅ **Accountability** — Clear responsibility for treasury  

### For the Community

✅ **Visibility** — All treasury operations visible  
✅ **Oversight** — Community can monitor and react  
✅ **Cancellation** — Ability to stop problematic proposals  
✅ **Participation** — Community can assess proposals  

## Treasury Protection Examples

### Example 1: Operational Funding

```
Scenario: Fund operations for Q1

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
Scenario: Fund strategic partnership

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

## Treasury Protection Best Practices

### For Administrators

✅ **Use formal proposals** — Always use proposal system  
✅ **Communicate clearly** — Explain purpose of withdrawals  
✅ **Allow review time** — Give community time to assess  
✅ **Respect feedback** — Consider community concerns  
✅ **Maintain transparency** — Keep operations visible  

### For Community

✅ **Monitor treasury** — Watch for new proposals  
✅ **Assess proposals** — Evaluate withdrawal purposes  
✅ **Provide feedback** — Share concerns and suggestions  
✅ **Request cancellation** — Ask for cancellation if needed  
✅ **Stay vigilant** — Maintain security awareness  

## Key Takeaways

1. **Non-instantaneous** — Withdrawals require waiting period
2. **Proposal-based** — Formal process for all withdrawals
3. **Timelock-protected** — Delays enable community oversight
4. **Cancellable** — Ability to stop pending withdrawals
5. **Transparent** — All operations logged and verifiable

---

**Next:** Learn about [Recovery Functions](./recovery-functions.md) and accident recovery mechanisms.
