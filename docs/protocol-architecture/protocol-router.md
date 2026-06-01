---
title: Protocol Router
sidebar_position: 4
description: Understanding the Protocol Router contract that orchestrates TCP operations
---

# Protocol Router

The **Protocol Router** is a coordination contract that orchestrates interactions between different TCP contracts, ensuring consistency and reducing operational errors.

## Router Purpose

The Protocol Router:
- Coordinates between contracts
- Manages complex multi-contract operations
- Ensures state consistency
- Reduces operational errors
- Simplifies integration

## Why a Router?

Without a router, complex operations would require:
- Multiple separate transactions
- Manual coordination
- Higher risk of partial execution
- Increased operational complexity

With a router:
- Single transaction for complex operations
- Automatic coordination
- Atomic execution (all-or-nothing)
- Reduced complexity

## Core Functions

### Operation Execution

#### `executeOperation(bytes calldata operationData)`

Executes a coordinated operation across multiple contracts.

**Parameters**
- `operationData` — Encoded operation data

**Returns**
- `bool` — True if successful

**Events**
- `OperationExecuted(operationId, status)`

**Example Operations**
- Multi-contract transfers
- Coordinated withdrawals
- Complex reward distributions

### Operation Validation

#### `validateOperation(bytes calldata operationData)`

Validates an operation before execution.

**Parameters**
- `operationData` — Encoded operation data

**Returns**
- `bool` — True if valid

**Checks**
- All parameters valid
- All contracts accessible
- All permissions granted
- All balances sufficient

### Operation Logging

#### `logOperation(uint256 operationId, bytes calldata operationData)`

Logs an operation for transparency.

**Parameters**
- `operationId` — Unique operation ID
- `operationData` — Encoded operation data

**Events**
- `OperationLogged(operationId, timestamp)`

## Supported Operations

### 1. Staking Reward Distribution

**Operation**
- Calculate rewards
- Transfer reward tokens
- Update staker records
- Log distribution

**Contracts Involved**
- Staking Contract
- Token Contract

**Execution**
```
1. Router receives operation
2. Validates operation
3. Calls Staking Contract to calculate rewards
4. Calls Token Contract to transfer tokens
5. Updates staker records
6. Logs operation
7. Emits event
```

### 2. Treasury Withdrawal

**Operation**
- Verify proposal
- Check timelock
- Transfer tokens
- Update treasury

**Contracts Involved**
- Treasury Contract
- Token Contract

**Execution**
```
1. Router receives operation
2. Validates proposal
3. Checks timelock expiration
4. Calls Token Contract to transfer
5. Updates treasury balance
6. Logs operation
7. Emits event
```

### 3. Liquidity Withdrawal

**Operation**
- Verify proposal
- Check limits
- Transfer LP
- Update balance

**Contracts Involved**
- Liquidity Manager
- Token Contract

**Execution**
```
1. Router receives operation
2. Validates proposal
3. Checks daily limits
4. Calls Token Contract to transfer
5. Updates LP balance
6. Updates daily consumption
7. Logs operation
8. Emits event
```

## Events

### OperationExecuted Event

```solidity
event OperationExecuted(
    uint256 indexed operationId,
    string operationType,
    bool success,
    uint256 timestamp
)
```

Emitted when an operation is executed.

**Parameters**
- `operationId` — Unique operation ID
- `operationType` — Type of operation
- `success` — Whether operation succeeded
- `timestamp` — Execution timestamp

### OperationFailed Event

```solidity
event OperationFailed(
    uint256 indexed operationId,
    string reason,
    uint256 timestamp
)
```

Emitted when an operation fails.

**Parameters**
- `operationId` — Unique operation ID
- `reason` — Failure reason
- `timestamp` — Failure timestamp

### OperationLogged Event

```solidity
event OperationLogged(
    uint256 indexed operationId,
    bytes operationData,
    uint256 timestamp
)
```

Emitted when an operation is logged.

**Parameters**
- `operationId` — Unique operation ID
- `operationData` — Encoded operation data
- `timestamp` — Logging timestamp

## Router Architecture

### Contract References

The router maintains references to:
- Token Contract
- Treasury Contract
- Liquidity Manager
- Staking Contract
- Burn Engine
- Ecosystem Vault
- Vesting Contract

### Operation Flow

```
User/Contract
    ↓
Protocol Router
    ├── Validate Operation
    ├── Execute Operation
    │   ├── Call Contract 1
    │   ├── Call Contract 2
    │   └── Call Contract N
    ├── Log Operation
    └── Emit Event
```

## Benefits of Router

### 1. Atomicity

Operations either complete fully or not at all:
- No partial execution
- Consistent state
- Reduced error risk

### 2. Simplicity

Complex operations simplified:
- Single transaction
- Automatic coordination
- Reduced complexity

### 3. Transparency

All operations logged:
- Complete audit trail
- Verifiable execution
- Community oversight

### 4. Reliability

Reduced operational errors:
- Automatic validation
- Consistent execution
- Error handling

## Router Security

### Access Control

Only authorized addresses can:
- Execute operations
- Validate operations
- Log operations

### Operation Validation

All operations are validated:
- Parameter validation
- Permission checks
- Balance verification
- State consistency

### Error Handling

Errors are handled gracefully:
- Failed operations logged
- Partial execution prevented
- State consistency maintained
- Error messages provided

## Integration with Router

### For Developers

**To Execute Operation**
```solidity
// Encode operation
bytes memory operationData = abi.encode(
    operationType,
    param1,
    param2,
    ...
);

// Execute operation
router.executeOperation(operationData);
```

**To Validate Operation**
```solidity
// Validate before execution
bool isValid = router.validateOperation(operationData);
require(isValid, "Invalid operation");
```

### For Users

Users interact with router indirectly:
- Call contract functions
- Router handles coordination
- Operations execute automatically
- Results are transparent

## Router Monitoring

### On PolygonScan

You can monitor router operations:
1. Visit PolygonScan
2. Search for router address
3. View operation events
4. Track execution history

### Community Tools

Community tools can:
- Monitor operations
- Track execution
- Analyze patterns
- Provide dashboards

## Key Takeaways

1. **Coordinates operations** — Manages multi-contract interactions
2. **Ensures consistency** — Maintains state consistency
3. **Reduces errors** — Prevents partial execution
4. **Improves reliability** — Automatic validation and error handling
5. **Transparent** — All operations logged and verifiable

---

**Next:** Learn about the [Treasury Contract](./treasury.md) that manages strategic reserves.
