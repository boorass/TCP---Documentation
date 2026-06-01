---
title: Treasury Contract
sidebar_position: 5
description: Technical details of the Treasury contract and withdrawal mechanisms
---

# Treasury Contract

The **Treasury Contract** manages Protocol (TCP)'s strategic reserves with disciplined, timelock-protected access.

## Contract Purpose

The Treasury Contract:
- Holds strategic token reserves
- Manages withdrawal proposals
- Enforces timelock delays
- Enables proposal cancellation
- Logs all operations

## Core Functions

### Withdrawal Management

#### `proposeWithdrawal(address recipient, uint256 amount)`

Proposes a withdrawal from the treasury.

**Parameters**
- `recipient` — Address to receive tokens
- `amount` — Number of tokens to withdraw

**Returns**
- `uint256` — Proposal ID

**Events**
- `WithdrawalProposed(proposalId, recipient, amount, executionTime)`

**Requirements**
- Caller must be owner or authorized
- Amount must not exceed treasury balance
- No active proposal exists

**Example**
```
// Propose withdrawal of 100,000 TCP
proposeWithdrawal(0x123..., 100000e18)
```

#### `executeWithdrawal(uint256 proposalId)`

Executes a withdrawal after timelock expires.

**Parameters**
- `proposalId` — ID of proposal to execute

**Returns**
- `bool` — True if successful

**Events**
- `WithdrawalExecuted(proposalId, recipient, amount)`

**Requirements**
- Timelock period must have expired
- Proposal must not be cancelled
- Recipient must be valid
- Amount must be available

**Example**
```
// Execute withdrawal
executeWithdrawal(1)
```

#### `cancelProposal(uint256 proposalId)`

Cancels a pending withdrawal proposal.

**Parameters**
- `proposalId` — ID of proposal to cancel

**Returns**
- `bool` — True if successful

**Events**
- `ProposalCancelled(proposalId, reason)`

**Requirements**
- Caller must be owner or authorized
- Proposal must be pending
- Proposal must not have executed

**Example**
```
// Cancel proposal
cancelProposal(1)
```

### Query Functions

#### `getTreasuryBalance()`

Returns the current treasury balance.

**Returns**
- `uint256` — Current balance

**Example**
```
// Check treasury balance
uint256 balance = getTreasuryBalance()
```

#### `getPendingProposal()`

Returns information about the pending proposal.

**Returns**
- `uint256` — Proposal ID
- `address` — Recipient address
- `uint256` — Withdrawal amount
- `uint256` — Execution time
- `bool` — Is cancelled

**Example**
```
// Check pending proposal
(id, recipient, amount, execTime, cancelled) = getPendingProposal()
```

#### `getProposalStatus(uint256 proposalId)`

Returns the status of a specific proposal.

**Parameters**
- `proposalId` — ID of proposal

**Returns**
- `string` — Status (pending, executed, cancelled)

#### `getTimeUntilExecution(uint256 proposalId)`

Returns time remaining until proposal can execute.

**Parameters**
- `proposalId` — ID of proposal

**Returns**
- `uint256` — Seconds until execution (0 if ready)

## Treasury Parameters

### Key Parameters

| Parameter | Description |
|-----------|-------------|
| **Timelock Delay** | Waiting period before execution (e.g., 7 days) |
| **Max Withdrawal** | Maximum withdrawal amount per proposal |
| **Token Address** | Address of TCP token contract |
| **Owner Address** | Address authorized to propose withdrawals |

### Parameter Management

Parameters are managed through:
- Owner control for routine adjustments
- Multisig approval for critical changes
- Transparent process with event logging

## Events

### WithdrawalProposed Event

```solidity
event WithdrawalProposed(
    uint256 indexed proposalId,
    address indexed recipient,
    uint256 amount,
    uint256 executionTime
)
```

Emitted when a withdrawal is proposed.

**Parameters**
- `proposalId` — Unique proposal ID
- `recipient` — Recipient address
- `amount` — Withdrawal amount
- `executionTime` — When proposal can execute

### WithdrawalExecuted Event

```solidity
event WithdrawalExecuted(
    uint256 indexed proposalId,
    address indexed recipient,
    uint256 amount
)
```

Emitted when a withdrawal is executed.

**Parameters**
- `proposalId` — Proposal ID
- `recipient` — Recipient address
- `amount` — Withdrawn amount

### ProposalCancelled Event

```solidity
event ProposalCancelled(
    uint256 indexed proposalId,
    string reason
)
```

Emitted when a proposal is cancelled.

**Parameters**
- `proposalId` — Proposal ID
- `reason` — Cancellation reason

## Withdrawal Workflow

### Step-by-Step Process

```
1. Proposal Creation
   - Owner calls proposeWithdrawal()
   - Parameters recorded on-chain
   - Timelock period begins
   - Event emitted

2. Timelock Period
   - Waiting period enforced
   - Community can monitor
   - Proposal can be cancelled
   - Time remaining visible

3. Execution Window
   - After timelock expires
   - Proposal can be executed
   - Owner calls executeWithdrawal()
   - Tokens transferred

4. Completion
   - Treasury balance updated
   - Event emitted
   - Operation logged on-chain
   - Transparency maintained
```

## Security Features

### Timelock Protection

- Withdrawal cannot execute immediately
- Community has time to react
- Proposal can be cancelled if needed
- Prevents sudden unauthorized withdrawals

### Access Control

- Only authorized addresses can propose
- Only authorized addresses can execute
- Only authorized addresses can cancel
- Clear role definitions

### Balance Verification

- Withdrawal amount verified
- Cannot exceed treasury balance
- Prevents overdrafts
- Maintains solvency

### Event Logging

- All proposals logged
- All executions logged
- All cancellations logged
- Complete audit trail

## Treasury Transparency

### Public Information

All treasury information is publicly available:

✅ **Treasury Balance** — Current holdings  
✅ **Pending Proposals** — Proposed withdrawals  
✅ **Proposal Status** — Status of each proposal  
✅ **Execution Time** — When proposals can execute  
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

## Treasury Examples

### Example 1: Operational Funding

```
Scenario: Treasury needs to fund operations

1. Owner proposes withdrawal
   - Amount: 50,000 TCP
   - Recipient: Operations wallet
   - Timelock: 7 days

2. Community monitors
   - Proposal visible on PolygonScan
   - Community can assess
   - Proposal can be cancelled if needed

3. After 7 days
   - Owner executes withdrawal
   - 50,000 TCP transferred
   - Event logged on-chain

4. Completion
   - Operations funded
   - Treasury balance reduced
   - Transparency maintained
```

### Example 2: Strategic Initiative

```
Scenario: Treasury supports strategic initiative

1. Owner proposes withdrawal
   - Amount: 100,000 TCP
   - Recipient: Initiative wallet
   - Timelock: 7 days

2. Community reviews
   - Proposal details visible
   - Community can provide feedback
   - Proposal can be cancelled if needed

3. After 7 days
   - Owner executes withdrawal
   - 100,000 TCP transferred
   - Initiative funded

4. Completion
   - Initiative supported
   - Treasury balance reduced
   - Transparency maintained
```

## Integration Guide

### For Developers

**To Check Treasury Balance**
```solidity
uint256 balance = treasury.getTreasuryBalance();
```

**To Propose Withdrawal**
```solidity
treasury.proposeWithdrawal(recipient, amount);
```

**To Execute Withdrawal**
```solidity
treasury.executeWithdrawal(proposalId);
```

**To Cancel Proposal**
```solidity
treasury.cancelProposal(proposalId);
```

### For Community

**To Monitor Treasury**
1. Visit PolygonScan
2. Search for treasury address
3. View proposal events
4. Monitor execution events

**To Assess Proposals**
1. Check proposal details
2. Verify recipient address
3. Assess withdrawal amount
4. Consider impact

## Key Takeaways

1. **Disciplined access** — Withdrawals require proposal and timelock
2. **Community oversight** — Proposals visible and monitorable
3. **Cancellation mechanism** — Ability to stop proposals
4. **Complete transparency** — All operations logged on-chain
5. **Auditable** — Full history available for review

---

**Next:** Learn about the [Liquidity Manager](./liquidity-manager.md) that protects LP.
