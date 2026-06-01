---
title: Recovery Functions
sidebar_position: 6
description: TCP's accident recovery mechanisms
---

# Recovery Functions

Protocol (TCP) includes **recovery functions** to handle accidental token transfers and fund deposits, preventing permanent loss of assets.

## Recovery Function Purpose

Recovery functions exist to:
- **Prevent loss** — Recover accidentally sent tokens
- **Maintain safety** — Recover native funds sent by mistake
- **Protect assets** — Prevent permanent loss
- **Enable operations** — Handle edge cases

## What Can Be Recovered

### Tokens Sent by Mistake

**Scenario**
- User accidentally sends tokens to contract
- Tokens are not TCP (different token)
- Tokens would be permanently lost
- Recovery prevents loss

**Recovery Process**
1. Identify accidentally sent tokens
2. Call recovery function
3. Tokens transferred to safe address
4. Loss prevented

### Native Funds Sent by Mistake

**Scenario**
- User accidentally sends MATIC to contract
- MATIC would be permanently lost
- Recovery prevents loss
- Funds returned to user

**Recovery Process**
1. Identify accidentally sent MATIC
2. Call recovery function
3. MATIC transferred to safe address
4. Loss prevented

## What Cannot Be Recovered

### TCP Token

**Protection**
- TCP token cannot be recovered via recovery function
- Prevents abuse of recovery mechanism
- Protects treasury and allocations
- Enforces discipline

**Reason**
- TCP is the primary asset
- Recovery would compromise security
- Must use formal withdrawal process
- Maintains operational discipline

### Core Assets

**Protection**
- Core protocol assets cannot be recovered
- Prevents circumventing safeguards
- Protects treasury
- Maintains security

**Reason**
- Recovery would bypass timelocks
- Would compromise security
- Must use formal processes
- Maintains discipline

## Recovery Function Implementation

### Token Recovery

**Function**
```solidity
function recoverToken(address token, uint256 amount)
```

**Parameters**
- `token` — Token address to recover
- `amount` — Amount to recover

**Requirements**
- Token must not be TCP
- Amount must be available
- Caller must be authorized

**Process**
1. Verify token is not TCP
2. Transfer tokens to safe address
3. Log recovery event
4. Maintain transparency

### Native Fund Recovery

**Function**
```solidity
function recoverNativeFunds(uint256 amount)
```

**Parameters**
- `amount` — Amount of MATIC to recover

**Requirements**
- Amount must be available
- Caller must be authorized

**Process**
1. Verify amount available
2. Transfer MATIC to safe address
3. Log recovery event
4. Maintain transparency

## Recovery Events

### TokenRecovered Event

```solidity
event TokenRecovered(
    address indexed token,
    uint256 amount,
    address indexed recipient
)
```

Emitted when tokens are recovered.

### NativeFundsRecovered Event

```solidity
event NativeFundsRecovered(
    uint256 amount,
    address indexed recipient
)
```

Emitted when native funds are recovered.

## Recovery Transparency

### Public Information

All recovery information is public:

✅ **Recovery Events** — All recoveries logged  
✅ **Token Addresses** — Which tokens recovered  
✅ **Amounts** — How much recovered  
✅ **Recipients** — Where funds sent  
✅ **Timestamps** — When recovery occurred  

### Verification Methods

You can verify recovery information:

1. **PolygonScan**
   - View recovery events
   - Check recovered amounts
   - Monitor recipients
   - Track history

2. **Contract Functions**
   - Call recovery functions
   - Check recovery logs
   - Verify amounts
   - View history

3. **Community Tools**
   - Use recovery dashboards
   - Monitor recoveries
   - Analyze patterns
   - Track history

## Recovery Examples

### Example 1: Accidental Token Transfer

```
Scenario: User accidentally sends USDC to contract

1. User sends 1000 USDC
   - Intended recipient: Different address
   - Actual recipient: TCP contract
   - USDC now locked in contract

2. Recovery initiated
   - Owner identifies accidental transfer
   - Calls recoverToken(USDC, 1000)
   - Recovery function executes

3. Recovery execution
   - Contract verifies USDC is not TCP
   - Transfers 1000 USDC to safe address
   - Event logged on PolygonScan

4. Completion
   - USDC recovered
   - Loss prevented
   - User can retrieve from safe address
   - Transparency maintained
```

### Example 2: Accidental MATIC Transfer

```
Scenario: User accidentally sends MATIC to contract

1. User sends 10 MATIC
   - Intended recipient: Different address
   - Actual recipient: TCP contract
   - MATIC now locked in contract

2. Recovery initiated
   - Owner identifies accidental transfer
   - Calls recoverNativeFunds(10)
   - Recovery function executes

3. Recovery execution
   - Contract verifies MATIC available
   - Transfers 10 MATIC to safe address
   - Event logged on PolygonScan

4. Completion
   - MATIC recovered
   - Loss prevented
   - User can retrieve from safe address
   - Transparency maintained
```

## Recovery Security

### Protection Mechanisms

Recovery functions are protected by:
- **Authorization checks** — Only authorized addresses can call
- **Token verification** — Cannot recover TCP
- **Amount verification** — Cannot exceed available amount
- **Event logging** — All recoveries logged
- **Transparency** — All recoveries visible on-chain

### Limitations

Recovery functions:
- Cannot bypass timelocks
- Cannot access core assets
- Cannot recover TCP
- Cannot be used for unauthorized transfers

## Recovery Best Practices

### For Users

✅ **Verify addresses** — Always check recipient address  
✅ **Use official sources** — Only use official contract addresses  
✅ **Test transfers** — Test with small amount first  
✅ **Double-check** — Verify before confirming transaction  
✅ **Contact support** — If accident occurs, contact support  

### For Administrators

✅ **Monitor transfers** — Watch for accidental transfers  
✅ **Respond quickly** — Recover accidentally sent funds promptly  
✅ **Communicate** — Inform users of recovery  
✅ **Document** — Keep records of recoveries  
✅ **Maintain transparency** — Log all recoveries  

## Key Takeaways

1. **Accident recovery** — Recover accidentally sent tokens
2. **Loss prevention** — Prevent permanent loss of funds
3. **Limited scope** — Cannot recover TCP or core assets
4. **Transparent** — All recoveries logged and verifiable
5. **Safety mechanism** — Handles edge cases safely

---

**Next:** Learn about [Operational Risk Controls](./operational-risk-controls.md) and incident response.
