---
title: "Staking FAQ"
sidebar_position: 7
description: "Frequently asked questions about TCP staking, rewards, and TCPStakingV2"
sidebar_custom_props:
  icon: "question"
---

This FAQ addresses common questions about TCP staking, reward mechanics, and the TCPStakingV2 contract.

## General Questions

### What is TCP staking?

TCP staking is a decentralized mechanism that allows TCP token holders to lock their tokens in the TCPStakingV2 contract and earn rewards. Staking is voluntary, flexible, and requires no lock-up period.

### Why should I stake TCP?

Staking provides several benefits:

- **Passive income**: Earn rewards on your TCP holdings
- **Flexibility**: Stake and unstake anytime without penalties
- **Transparency**: All rewards calculated on-chain and verifiable
- **Community support**: Help secure and support the protocol
- **Compound growth**: Claim and restake for exponential returns

### Is staking mandatory?

No. Staking is completely voluntary. You can hold TCP without staking and participate in the protocol normally.

### What is TCPStakingV2?

TCPStakingV2 is the official, production-ready staking contract for TCP Protocol. It was thoroughly tested on Polygon Mainnet and validated as fully functional and secure. No migration to a V3 was necessary.

### Why is TCPStakingV2 the final version?

After extensive testing, including:
- Multiple internal audits
- Safe multisig simulations
- Comprehensive Polygon Mainnet validation

TCPStakingV2 was confirmed to be fully functional and secure. No improvements or migrations were needed.

---

## Staking Mechanics

### How do I start staking?

1. **Approve**: Grant the staking contract permission to spend your TCP tokens
2. **Stake**: Transfer your desired amount to the staking contract
3. **Earn**: Rewards begin accruing immediately
4. **Claim**: Claim rewards anytime without restrictions
5. **Unstake**: Unstake tokens anytime without lock-up

### Do I need to approve every time I stake?

No. Once you approve the staking contract for a certain amount, you can stake multiple times up to that approved amount without re-approving.

### Can I stake any amount?

Yes. There is no minimum or maximum stake limit. You can stake any amount from 1 TCP to your entire balance.

### Is there a lock-up period?

No. You can unstake your tokens immediately anytime without any lock-up period or penalties.

### Can I unstake partially?

Yes. You can unstake any amount up to your total stake. Your remaining stake continues earning rewards.

### What happens when I unstake?

When you unstake:
1. Your tokens are transferred back to your wallet
2. Your stake balance is reduced
3. Your remaining stake continues earning rewards
4. Any pending rewards remain claimable

### Do I lose rewards when I unstake?

No. Unstaking does not affect your pending rewards. You can claim rewards before or after unstaking.

---

## Reward Mechanics

### How are rewards calculated?

Rewards are calculated proportionally based on your share of total staked tokens:

```
Your Reward = (Your Stake / Total Stake) × Total Reward Rate
```

### How often are rewards calculated?

Rewards accrue continuously, updated on each block. You can claim them anytime.

### When do rewards start accruing?

Rewards begin accruing immediately when you stake. They are calculated continuously from that moment.

### Can I claim rewards anytime?

Yes. You can claim your earned rewards anytime without restrictions. There is no waiting period or frequency limit.

### What happens when I claim rewards?

When you claim:
1. Your accrued rewards are transferred to your wallet
2. Your reward balance is reset to zero
3. New rewards begin accruing immediately
4. Your stake remains unchanged

### Can I claim partial rewards?

The contract claims all accrued rewards at once. You cannot claim partial amounts.

### What if I don't claim rewards?

Your rewards continue accruing and remain claimable. You can claim them anytime in the future.

### Can I lose my rewards?

No. Your accrued rewards are reserved and protected. They cannot be lost or forfeited.

### Why are rewards reserved?

Reward reservation prevents double-payment and ensures accurate accounting. Reserved rewards are held for your claim and cannot be allocated to other users.

---

## Reward Pool

### What is the reward pool?

The reward pool is a fixed allocation of 70,000,000 TCP tokens dedicated to funding all staking rewards.

### Why is there a maximum pool size?

The maximum pool size ensures:
- **Predictable rewards**: Pool size is fixed and known
- **Fair distribution**: All rewards come from the same pool
- **Prevents accidents**: Protects against funding mistakes
- **Maintains invariants**: Keeps accounting consistent

### Can the reward pool be increased?

The maximum pool is 70,000,000 TCP. The contract prevents funding beyond this limit. If the pool depletes, the multisig can refund it through governance.

### What happens if the reward pool runs out?

The contract prevents staking if rewards are unavailable. The pool is managed to prevent depletion.

### How is the reward pool funded?

The reward pool is funded by the protocol owner (multisig) through the `fundRewards()` function. Funding requires multisig approval and cannot exceed the maximum pool size.

### Can I see the reward pool status?

Yes. You can query the contract to see:
- Total funded rewards
- Reserved rewards
- Available rewards
- Remaining capacity

### Is the reward pool sustainable?

Yes. The 70,000,000 TCP pool is designed for long-term sustainability and can support staking rewards for an extended period.

---

## Security and Safety

### Is staking safe?

TCPStakingV2 has been thoroughly tested and validated:
- Multiple internal audits completed
- Safe multisig simulations passed
- Comprehensive Mainnet validation completed
- All invariants verified

However, smart contracts carry inherent risks. Always do your own research.

### What are the risks of staking?

Potential risks include:
- **Smart contract risk**: Contracts may have vulnerabilities
- **Market risk**: Token value may decrease
- **Reward risk**: Reward rate may change
- **Operational risk**: Protocol operations may be disrupted

### How is my stake protected?

Your stake is protected through:
- Audited smart contracts
- Owner validation and multisig governance
- Automatic reward pool overflow protection
- Continuous reward accrual without double-payment risk

### Can I lose my staked tokens?

No. Your staked tokens are held in the contract and can only be withdrawn by you through the unstake function.

### What if the contract has a bug?

TCPStakingV2 has been thoroughly tested and validated. However, if a critical issue is discovered, the multisig can take emergency action to protect user funds.

### How do I verify the contract?

You can verify the contract on PolygonScan:
1. Go to PolygonScan
2. Search for the staking contract address
3. View the contract code
4. Verify the source code matches the deployed contract

---

## Rewards and Returns

### What is the current reward rate?

The reward rate depends on:
- Total reward pool funding
- Total staked amount
- Reward distribution mechanism

Check the staking interface for the current rate.

### Can the reward rate change?

Yes. The reward rate can be adjusted by the multisig through governance. Changes are announced in advance.

### How much can I earn?

Your earnings depend on:
- Amount staked
- Reward rate
- Duration of staking
- Whether you compound rewards

Use the staking calculator to estimate your earnings.

### Is there a maximum reward?

No. Your rewards are limited only by the reward pool size and your stake amount.

### Can I earn more by staking longer?

Yes. Longer staking periods result in more accrued rewards. Rewards accrue continuously over time.

### What is compound staking?

Compound staking is claiming your rewards and restaking them. This increases your stake amount, which earns more rewards, creating exponential growth.

### How do I compound my rewards?

1. Claim your accrued rewards
2. Approve the staking contract for the claimed amount
3. Stake the claimed rewards
4. Your larger stake earns more rewards

---

## Technical Questions

### What network is staking on?

Staking is on Polygon Mainnet. All transactions occur on Polygon.

### What is the contract address?

The TCPStakingV2 contract address is available on PolygonScan and in the protocol documentation.

### How do I interact with the contract?

You can interact through:
- Web interface (if available)
- Direct contract interaction on PolygonScan
- Wallet integration
- Smart contract integration

### What are the main contract functions?

Core functions:
- `approve()`: Grant permission to spend tokens
- `stake()`: Stake tokens
- `unstake()`: Unstake tokens
- `claimRewards()`: Claim earned rewards
- `getStakeBalance()`: Check your stake
- `getRewardBalance()`: Check your rewards

### How do I check my stake balance?

You can check your balance through:
- Staking interface
- PolygonScan contract interaction
- Wallet integration
- Direct contract query

### How do I check my reward balance?

You can check your rewards through:
- Staking interface
- PolygonScan contract interaction
- Wallet integration
- Direct contract query

### What events does the contract emit?

Key events:
- `Staked(user, amount)`: Emitted when tokens are staked
- `Unstaked(user, amount)`: Emitted when tokens are unstaked
- `RewardsClaimed(user, amount)`: Emitted when rewards are claimed
- `RewardsFunded(amount)`: Emitted when rewards are funded

---

## Troubleshooting

### Why does my approval fail?

Possible causes:
- Insufficient TCP balance
- Token contract issue
- Network connectivity problem
- Gas price too low

**Solution**: Check balance, verify contract address, retry with higher gas.

### Why does my stake fail?

Possible causes:
- Insufficient approved amount
- Insufficient balance
- Reward pool unavailable
- Contract issue

**Solution**: Check approval, verify balance, check pool status, retry.

### Why can't I claim rewards?

Possible causes:
- No accrued rewards
- Reward pool depleted
- Contract issue
- Network problem

**Solution**: Check reward balance, verify pool status, retry.

### Why does my unstake fail?

Possible causes:
- Insufficient stake balance
- Unstake amount too high
- Contract issue
- Network problem

**Solution**: Check stake balance, verify amount, retry.

### Why are my rewards not accruing?

Possible causes:
- Stake not confirmed
- Network issue
- Contract issue
- Rewards paused

**Solution**: Verify stake is recorded, check network, retry.

### How do I report a bug?

If you discover a bug:
1. Do not exploit it
2. Document the issue
3. Report to the protocol team
4. Follow responsible disclosure

---

## Best Practices

### Before Staking

✅ **Understand the mechanism** completely  
✅ **Verify contract address** on PolygonScan  
✅ **Start with small amount** to test  
✅ **Check gas prices** before transactions  
✅ **Have sufficient MATIC** for gas fees  

### During Staking

✅ **Monitor rewards** regularly  
✅ **Claim periodically** to compound  
✅ **Track transactions** for records  
✅ **Stay informed** of protocol updates  
✅ **Verify balances** on PolygonScan  

### When Claiming

✅ **Check available rewards** before claiming  
✅ **Verify gas prices** are reasonable  
✅ **Confirm transaction** details  
✅ **Wait for confirmation** before assuming success  
✅ **Verify receipt** on PolygonScan  

### When Unstaking

✅ **Claim rewards first** if you want them  
✅ **Verify unstake amount** before confirming  
✅ **Understand no lock-up** means immediate return  
✅ **Check remaining stake** after partial unstaking  
✅ **Confirm tokens received** in wallet  

---

## Getting Help

### Where can I find more information?

- [How Staking Works](/docs/staking-rewards/how-staking-works)
- [Reward Distribution Logic](/docs/staking-rewards/reward-distribution-logic)
- [Reward Funding](/docs/staking-rewards/reward-funding)
- [User Flows](/docs/staking-rewards/user-flows)
- [Technical Validation](/docs/staking-rewards/technical-validation)

### How do I contact support?

Visit the [Contact Support](/docs/resources/contact-support) page for support options.

### Where can I find the contract?

The TCPStakingV2 contract is available on:
- PolygonScan
- Protocol documentation
- GitHub repository

### How do I verify the contract?

You can verify the contract on PolygonScan by:
1. Searching for the contract address
2. Viewing the contract code
3. Comparing with the source code
4. Checking the deployment transaction

---

## See also

- [Introduction to TCP Staking](/docs/staking-rewards/introduction)
- [How Staking Works](/docs/staking-rewards/how-staking-works)
- [Reward Distribution Logic](/docs/staking-rewards/reward-distribution-logic)
- [User Flows](/docs/staking-rewards/user-flows)
- [Technical Validation](/docs/staking-rewards/technical-validation)
