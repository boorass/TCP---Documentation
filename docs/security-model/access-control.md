---
title: Access Control
sidebar_position: 2
description: Understanding TCP's role-based access control system
---

# Access Control

Protocol (TCP) uses a **role-based access control system** to manage permissions and prevent unauthorized operations.

## Access Control Principles

### 1. Least Privilege

Each role has minimum required permissions:
- Owner can't bypass timelocks
- Multisig required for critical changes
- No single role controls everything
- Explicit permission checks

### 2. Role Separation

Different operations require different approval levels:
- Routine operations → Owner
- Critical operations → Multisig
- Major changes → Community (if applicable)

### 3. Explicit Permissions

All permissions are explicit:
- No implicit permissions
- Clear role definitions
- Transparent assignments
- Auditable access

### 4. Transparent Management

Role management is transparent:
- All role changes logged
- Role assignments public
- Permission changes visible
- Community can verify

## Role Definitions

### Owner Role

**Responsibilities**
- Routine administrative tasks
- Parameter adjustments within limits
- Proposal creation
- Emergency pause functions (if applicable)

**Limitations**
- Cannot bypass timelocks
- Cannot exceed withdrawal limits
- Cannot change critical parameters
- Cannot revoke multisig permissions

**Typical Operations**
- Propose treasury withdrawals
- Propose liquidity withdrawals
- Adjust non-critical parameters
- Create proposals

### Multisig Role

**Responsibilities**
- Critical decision approval
- Major parameter changes
- Treasury withdrawals above threshold
- Protocol upgrades
- Emergency procedures

**Limitations**
- Requires multiple signatures
- Cannot act unilaterally
- Subject to timelocks
- Transparent operations

**Typical Operations**
- Approve critical withdrawals
- Approve major parameter changes
- Approve protocol upgrades
- Approve emergency procedures

### Community Role (if applicable)

**Responsibilities**
- Governance decisions
- Major protocol changes
- Parameter adjustments
- Resource allocation

**Limitations**
- Requires community consensus
- Subject to voting rules
- Transparent process
- Auditable decisions

**Typical Operations**
- Vote on major changes
- Approve governance proposals
- Allocate community resources
- Provide feedback

## Access Control Implementation

### Smart Contract Permissions

Permissions are enforced by smart contracts:

```solidity
// Only owner can call
require(msg.sender == owner, "Only owner");

// Only multisig can call
require(isMultisigMember(msg.sender), "Only multisig");

// Only authorized can call
require(hasRole(msg.sender, AUTHORIZED_ROLE), "Not authorized");
```

### Permission Checking

Before each operation:
1. Check caller's role
2. Verify permissions
3. Enforce limits
4. Log operation

### Permission Transparency

All permissions are transparent:
- Role assignments public
- Permission checks visible
- Access logs available
- Audit trail complete

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

### Role Verification

You can verify roles:

1. **PolygonScan** — View role assignments
2. **Contract Functions** — Call hasRole() function
3. **Community Tools** — Use community dashboards
4. **Event Logs** — Check role change events

## Access Control Examples

### Example 1: Treasury Withdrawal

```
Operation: Withdraw 100,000 TCP from treasury

1. Owner proposes withdrawal
   - Requires: Owner role
   - Check: Owner permission verified
   - Action: Proposal created

2. Timelock period begins
   - Duration: 7 days
   - Community can monitor
   - Proposal can be cancelled

3. After timelock expires
   - Owner executes withdrawal
   - Requires: Owner role
   - Check: Owner permission verified
   - Action: Tokens transferred

4. Completion
   - Event logged on-chain
   - Treasury balance updated
   - Transparency maintained
```

### Example 2: Critical Parameter Change

```
Operation: Change reward rate

1. Multisig proposes change
   - Requires: Multisig role
   - Check: Multisig permission verified
   - Action: Proposal created

2. Multisig approval
   - Requires: Multiple signatures
   - Check: Signatures verified
   - Action: Proposal approved

3. Timelock period begins
   - Duration: 7 days
   - Community can monitor
   - Proposal can be cancelled

4. After timelock expires
   - Multisig executes change
   - Requires: Multisig role
   - Check: Multisig permission verified
   - Action: Parameter updated

5. Completion
   - Event logged on-chain
   - Parameter updated
   - Transparency maintained
```

## Security Features

### Permission Verification

All operations verify permissions:
- Check caller's role
- Verify role permissions
- Enforce role limits
- Log verification

### Unauthorized Access Prevention

Unauthorized access is prevented:
- Only authorized roles can act
- Permissions enforced by code
- No backdoors or workarounds
- Transparent enforcement

### Role Audit Trail

Complete audit trail of roles:
- All assignments logged
- All revocations logged
- All changes timestamped
- Complete history available

## Access Control Best Practices

### For Administrators

✅ **Assign roles carefully** — Only assign necessary roles  
✅ **Revoke unused roles** — Remove roles when no longer needed  
✅ **Monitor access** — Watch for unusual access patterns  
✅ **Document decisions** — Keep records of role assignments  
✅ **Communicate changes** — Inform community of role changes  

### For Community

✅ **Monitor roles** — Watch for role changes  
✅ **Verify permissions** — Check role permissions  
✅ **Assess changes** — Evaluate role assignments  
✅ **Provide feedback** — Share concerns about access control  
✅ **Stay vigilant** — Maintain security awareness  

## Key Takeaways

1. **Role-based** — Permissions based on roles
2. **Least privilege** — Minimum required permissions
3. **Transparent** — All permissions visible and auditable
4. **Enforced** — Permissions enforced by smart contracts
5. **Auditable** — Complete audit trail of all access

---

**Next:** Learn about [Timelocks](./timelocks.md) that protect critical operations.
