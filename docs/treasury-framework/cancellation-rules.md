---
title: Cancellation Rules
sidebar_position: 4
description: Understanding treasury proposal cancellation
---

# Cancellation Rules

Protocol (TCP) enables **proposal cancellation** to stop pending withdrawals if concerns arise.

## Cancellation Purpose

Cancellation serves to:
- **Stop mistakes** — Prevent accidental withdrawals
- **Prevent abuse** — Stop unauthorized withdrawals
- **Respond to concerns** — Address community concerns
- **Maintain safety** — Protect treasury

## Who Can Cancel

Cancellation can be performed by:
- **Owner** — For owner-proposed withdrawals
- **Multisig** — For multisig-proposed withdrawals
- **Community** — If governance enabled

## Cancellation Process

### How to Cancel

```
1. Identify Proposal
   - Find proposal to cancel
   - Verify proposal details
   - Assess reason for cancellation

2. Initiate Cancellation
   - Call cancelProposal()
   - Specify proposal ID
   - Confirm cancellation

3. Cancellation Recorded
   - Cancellation event emitted
   - Proposal marked cancelled
   - Event logged on-chain

4. Completion
   - Proposal cancelled
   - No withdrawal executed
   - Transparency maintained
```

### Cancellation Timing

Cancellation can occur:
- **Before timelock expires** — Anytime before execution
- **After timelock expires** — Before execution
- **Not after execution** — Cannot cancel executed withdrawals

## Cancellation Examples

### Example 1: Cancellation Before Execution

```
Day 0:
- Owner proposes withdrawal
- Amount: 50,000 TCP
- Timelock: 7 days
- Event logged on PolygonScan

Day 3:
- Community raises concerns
- Owner assesses concerns
- Owner decides to cancel
- Owner calls cancelProposal()
- Cancellation recorded on-chain
- Event logged on PolygonScan

Completion:
- Proposal cancelled
- No withdrawal executed
- Community satisfied
- Transparency maintained
```

### Example 2: Cancellation Due to Error

```
Day 0:
- Owner proposes withdrawal
- Amount: 50,000 TCP (intended: 5,000 TCP)
- Error discovered
- Owner calls cancelProposal()
- Cancellation recorded on-chain

Day 1:
- Owner proposes correct withdrawal
- Amount: 5,000 TCP
- Timelock: 7 days
- Event logged on PolygonScan

Completion:
- Incorrect proposal cancelled
- Correct proposal created
- Error corrected
- Transparency maintained
```

## Cancellation Transparency

### Public Information

All cancellation information is public:

✅ **Cancellation Events** — All cancellations logged  
✅ **Cancellation Reasons** — Why proposals cancelled  
✅ **Cancellation Timing** — When cancelled  
✅ **Cancellation History** — Past cancellations  

### Verification Methods

You can verify cancellation information:

1. **PolygonScan**
   - View cancellation events
   - Check cancellation reasons
   - Monitor cancellation history
   - Track patterns

2. **Contract Functions**
   - Call getProposalStatus()
   - Check cancellation status
   - Verify cancellation reason
   - View cancellation history

3. **Community Tools**
   - Use cancellation dashboards
   - Monitor cancellations
   - Track cancellation patterns
   - Analyze trends

## Cancellation Best Practices

### For Administrators

✅ **Cancel promptly** — Cancel problematic proposals quickly  
✅ **Communicate clearly** — Explain reason for cancellation  
✅ **Provide updates** — Keep community informed  
✅ **Maintain transparency** — Keep operations visible  

### For Community

✅ **Request cancellation** — Ask for cancellation if needed  
✅ **Provide feedback** — Share concerns and suggestions  
✅ **Stay vigilant** — Monitor for problematic proposals  
✅ **Support process** — Support cancellation when appropriate  

## Key Takeaways

1. **Cancellation available** — Ability to stop proposals
2. **Anytime before execution** — Can cancel before timelock expires
3. **Transparent** — All cancellations logged on-chain
4. **Community-friendly** — Enables community to stop problematic proposals
5. **Safety mechanism** — Protects treasury from mistakes

---

**Next:** Learn about [Asset Recovery Rules](./asset-recovery-rules.md).
