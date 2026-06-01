---
title: Multisig Responsibilities
sidebar_position: 2
description: Understanding the Multisig role and approval processes
---

# Multisig Responsibilities

The **Multisig** (Multi-Signature) role provides additional security by requiring multiple signatures for critical decisions.

## What is Multisig?

A multisig is a smart contract that:
- Requires multiple signatures to approve actions
- Prevents single-person control
- Distributes authority
- Improves security

## Multisig Requirements

### Signature Requirements

Critical operations require:
- **Minimum signatures** — e.g., 3 of 5 signatures
- **Authorized signers** — Only designated signers
- **Explicit approval** — Each signer must approve
- **Transparent process** — All approvals logged

### Approval Process

```
1. Proposal Created
   - Operation proposed
   - Details recorded
   - Signers notified

2. Signer Review
   - Signers review proposal
   - Assess impact
   - Provide feedback

3. Signature Collection
   - Signers approve
   - Signatures collected
   - Threshold reached

4. Execution
   - Operation executes
   - Event logged
   - Transparency maintained
```

## Multisig Operations

### Critical Withdrawals

**Requirement**
- Multisig approval required for large withdrawals
- Threshold: e.g., above 100,000 TCP

**Process**
1. Owner proposes withdrawal
2. Multisig reviews proposal
3. Signers approve
4. Withdrawal executes

### Parameter Changes

**Requirement**
- Multisig approval required for critical parameter changes
- Examples: reward rate, lock duration, withdrawal limits

**Process**
1. Owner proposes change
2. Multisig reviews impact
3. Signers approve
4. Change executes

### Protocol Upgrades

**Requirement**
- Multisig approval required for upgrades
- Ensures careful review
- Prevents unauthorized changes

**Process**
1. Developer proposes upgrade
2. Multisig reviews code
3. Signers approve
4. Upgrade executes

### Emergency Procedures

**Requirement**
- Multisig approval required for emergency actions
- Examples: pause operations, freeze assets

**Process**
1. Issue identified
2. Emergency action proposed
3. Multisig approves
4. Action executes

## Multisig Security

### Benefits

✅ **Prevents single-person control** — Requires consensus  
✅ **Improves security** — Multiple reviews reduce errors  
✅ **Distributes authority** — No single point of failure  
✅ **Builds trust** — Community confidence in decisions  

### Limitations

⚠️ **Slower decisions** — Requires multiple signatures  
⚠️ **Coordination needed** — Signers must coordinate  
⚠️ **Signer availability** — All signers must be available  
⚠️ **Complexity** — More complex than single-sig  

## Multisig Transparency

### Public Information

All multisig information is public:

✅ **Signers** — Who can sign  
✅ **Threshold** — How many signatures needed  
✅ **Proposals** — All proposals visible  
✅ **Approvals** — All approvals logged  
✅ **Execution** — All executions logged  

### Verification Methods

You can verify multisig information:

1. **PolygonScan**
   - View multisig contract
   - Check signers
   - View proposals
   - Monitor approvals

2. **Contract Functions**
   - Call getSigners()
   - Call getThreshold()
   - Check proposal status
   - View approval status

3. **Community Tools**
   - Use multisig dashboards
   - Monitor proposals
   - Track approvals
   - Analyze patterns

## Multisig Best Practices

### For Signers

✅ **Review carefully** — Thoroughly review proposals  
✅ **Assess impact** — Evaluate impact of decisions  
✅ **Communicate** — Discuss with other signers  
✅ **Provide feedback** — Share concerns and suggestions  
✅ **Maintain security** — Protect signing keys  

### For Community

✅ **Monitor proposals** — Watch for new proposals  
✅ **Assess impact** — Evaluate proposal impact  
✅ **Provide feedback** — Share concerns and suggestions  
✅ **Request review** — Ask for careful review  
✅ **Stay vigilant** — Maintain security awareness  

## Key Takeaways

1. **Multiple signatures** — Requires consensus
2. **Prevents single control** — Distributes authority
3. **Improves security** — Multiple reviews reduce errors
4. **Transparent** — All approvals logged on-chain
5. **Community trust** — Builds confidence in decisions

---

**Next:** Learn about [Proposal Flow](./proposal-flow.md) and how proposals are processed.
