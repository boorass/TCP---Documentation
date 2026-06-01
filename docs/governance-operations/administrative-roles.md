---
title: Administrative Roles
sidebar_position: 1
description: TCP's administrative roles and responsibilities
---

# Administrative Roles

Protocol (TCP) uses a **role-based governance structure** where different roles have distinct responsibilities and authority levels.

## Role Hierarchy

```
Community (if applicable)
    ↓
Multisig (Critical Decisions)
    ↓
Owner (Routine Operations)
    ↓
Smart Contracts (Enforcement)
```

## Owner Role

### Responsibilities

The Owner is responsible for:

**Routine Operations**
- Propose treasury withdrawals
- Propose liquidity withdrawals
- Adjust non-critical parameters
- Create proposals

**Administrative Tasks**
- Manage routine operations
- Monitor protocol health
- Respond to community feedback
- Maintain transparency

### Authority

The Owner can:
- ✅ Propose withdrawals
- ✅ Create proposals
- ✅ Adjust parameters (within limits)
- ❌ Bypass timelocks
- ❌ Exceed withdrawal limits
- ❌ Change critical parameters

### Limitations

The Owner cannot:
- Bypass timelock delays
- Exceed maximum withdrawal amounts
- Change critical parameters unilaterally
- Revoke multisig permissions
- Circumvent security safeguards

## Multisig Role

### Responsibilities

The Multisig is responsible for:

**Critical Decisions**
- Approve major withdrawals
- Approve parameter changes
- Approve protocol upgrades
- Approve emergency procedures

**Oversight**
- Review owner proposals
- Assess impact of changes
- Provide additional security
- Maintain protocol integrity

### Authority

The Multisig can:
- ✅ Approve critical withdrawals
- ✅ Approve major changes
- ✅ Approve upgrades
- ✅ Approve emergency procedures
- ❌ Act unilaterally (requires multiple signatures)
- ❌ Bypass timelocks

### Limitations

The Multisig:
- Requires multiple signatures
- Cannot act unilaterally
- Subject to timelocks
- Must follow formal procedures

## Community Role (if applicable)

### Responsibilities

The Community is responsible for:

**Governance**
- Vote on major decisions
- Approve major changes
- Provide feedback
- Participate in governance

### Authority

The Community can:
- ✅ Vote on proposals
- ✅ Approve major changes
- ✅ Provide feedback
- ✅ Participate in governance

## Role Management

### Assigning Roles

Roles are assigned through:

1. **Owner Assignment** — Owner assigns roles
2. **Multisig Approval** — Critical roles require multisig approval
3. **Transparent Process** — All assignments logged on-chain
4. **Community Input** — Major assignments may require community input

### Revoking Roles

Roles are revoked through:

1. **Owner Revocation** — Owner can revoke roles
2. **Multisig Approval** — Critical revocations require multisig approval
3. **Transparent Process** — All revocations logged on-chain
4. **Effective Immediately** — Revocation takes effect immediately

## Responsibility Matrix

| Operation | Owner | Multisig | Community |
|-----------|-------|----------|-----------|
| **Propose Withdrawal** | ✅ | ✅ | ❌ |
| **Approve Withdrawal** | ❌ | ✅ | ❌ |
| **Execute Withdrawal** | ✅ | ✅ | ❌ |
| **Propose Parameter Change** | ✅ | ✅ | ❌ |
| **Approve Parameter Change** | ❌ | ✅ | ✅ |
| **Execute Parameter Change** | ✅ | ✅ | ❌ |
| **Propose Upgrade** | ✅ | ✅ | ❌ |
| **Approve Upgrade** | ❌ | ✅ | ✅ |
| **Execute Upgrade** | ✅ | ✅ | ❌ |

## Key Takeaways

1. **Clear roles** — Each role has defined responsibilities
2. **Distributed authority** — No single role controls everything
3. **Checks and balances** — Multiple roles required for critical decisions
4. **Transparent** — All role assignments logged on-chain
5. **Accountable** — Clear responsibility for each operation

---

**Next:** Learn about [Multisig Responsibilities](./multisig-responsibilities.md).
