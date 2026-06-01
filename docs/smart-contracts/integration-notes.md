---
title: Integration Notes
sidebar_position: 5
description: Guidelines for integrating with TCP smart contracts
---

# Integration Notes

This page provides guidance for developers integrating with TCP smart contracts.

## Integration Overview

To integrate with TCP:

1. **Get contract addresses** — From [Deployed Addresses](./deployed-addresses.md)
2. **Get contract ABI** — From PolygonScan
3. **Set up connection** — Connect to Polygon RPC
4. **Call functions** — Use standard interfaces
5. **Monitor events** — Listen for contract events

## Token Integration

### Adding TCP to Wallet

```
Token Address: 0x...
Token Name: Protocol Token
Ticker: TCP
Decimals: 18
Network: Polygon
```

### Token Transfer

```solidity
// Transfer tokens
IERC20(tokenAddress).transfer(recipient, amount);
```

### Token Approval

```solidity
// Approve spending
IERC20(tokenAddress).approve(spender, amount);
```

## Staking Integration

### Staking Tokens

```solidity
// Approve staking contract
IERC20(tokenAddress).approve(stakingAddress, amount);

// Stake tokens
IStaking(stakingAddress).stake(amount);
```

### Claiming Rewards

```solidity
// Claim rewards
IStaking(stakingAddress).claimRewards();
```

### Unstaking Tokens

```solidity
// Unstake tokens
IStaking(stakingAddress).unstake(amount);
```

## Event Monitoring

### Monitoring Transfers

```solidity
// Listen for Transfer events
event Transfer(address indexed from, address indexed to, uint256 value);
```

### Monitoring Staking

```solidity
// Listen for Staked events
event Staked(address indexed user, uint256 amount);

// Listen for RewardsClaimed events
event RewardsClaimed(address indexed user, uint256 amount);
```

## Best Practices

### For Exchanges

✅ **Verify contract address** — Always verify on PolygonScan  
✅ **Monitor deposits** — Listen for Transfer events  
✅ **Monitor withdrawals** — Track user withdrawals  
✅ **Update balances** — Keep user balances current  
✅ **Handle errors** — Handle transaction failures  

### For DeFi Protocols

✅ **Use standard interfaces** — Follow ERC-20 standard  
✅ **Handle approvals** — Properly handle token approvals  
✅ **Monitor events** — Listen for relevant events  
✅ **Test thoroughly** — Test all interactions  
✅ **Verify contracts** — Verify on PolygonScan  

### For Developers

✅ **Use official addresses** — Only use official contract addresses  
✅ **Verify on PolygonScan** — Always verify contracts  
✅ **Test on testnet** — Test on Polygon Mumbai first  
✅ **Handle errors** — Properly handle all error cases  
✅ **Monitor operations** — Monitor all operations  

## Common Integration Patterns

### Pattern 1: Token Transfer

```solidity
// 1. Approve contract to spend tokens
token.approve(contractAddress, amount);

// 2. Call contract function
contract.functionThatTransfersTokens(amount);

// 3. Monitor Transfer event
// Listen for Transfer event to confirm
```

### Pattern 2: Staking

```solidity
// 1. Approve staking contract
token.approve(stakingAddress, amount);

// 2. Stake tokens
staking.stake(amount);

// 3. Monitor Staked event
// Listen for Staked event to confirm

// 4. Claim rewards later
staking.claimRewards();

// 5. Monitor RewardsClaimed event
// Listen for RewardsClaimed event to confirm
```

## Troubleshooting

### Common Issues

**Issue: Transaction fails**
- Check gas price
- Verify parameters
- Check balance
- Check approvals

**Issue: Event not emitted**
- Check transaction status
- Verify contract address
- Check event filters
- Monitor logs

**Issue: Balance not updated**
- Wait for confirmation
- Check contract state
- Verify transaction
- Monitor events

## Support

For integration support:
- Check documentation
- Review examples
- Monitor events
- Contact support

---

**Next:** Explore [Governance & Operations](../governance-operations/overview.md) for operational details.
