---
title: "User Flows"
sidebar_position: 6
description: "Complete user workflows for staking, claiming rewards, and unstaking TCP tokens"
sidebar_custom_props:
  icon: "flow-arrow"
---

This guide walks through complete user workflows for interacting with the TCP staking system. Each workflow includes step-by-step instructions, on-chain operations, and expected outcomes.

## Workflow 1: Basic Staking

### Objective
Stake TCP tokens and begin earning rewards.

### Prerequisites
- TCP tokens in wallet
- Connected to Polygon Mainnet
- Sufficient MATIC for gas fees

### Step-by-Step Process

#### Step 1: Approve Staking Contract

**Action**: Grant the staking contract permission to spend your TCP tokens

**Instructions**
1. Open staking interface
2. Click "Approve"
3. Confirm amount (or use max)
4. Sign transaction in wallet
5. Wait for confirmation

**On-Chain**
```
Transaction: approve()
├─ From: User wallet
├─ To: TCP token contract
├─ Function: approve(stakingContract, amount)
├─ Gas: ~50,000 GWEI
└─ Status: Confirmed
```

**Result**
```
✓ Allowance set
✓ Staking contract can spend tokens
✓ Ready to stake
```

#### Step 2: Stake Tokens

**Action**: Transfer tokens to staking contract and create stake

**Instructions**
1. Enter amount to stake
2. Review details
3. Click "Stake"
4. Sign transaction
5. Wait for confirmation

**On-Chain**
```
Transaction: stake()
├─ From: User wallet
├─ To: Staking contract
├─ Function: stake(amount)
├─ Gas: ~80,000 GWEI
└─ Status: Confirmed
```

**State Changes**
```
Before:
├─ User balance: 1,000 TCP
├─ User stake: 0 TCP
├─ Contract balance: 0 TCP
└─ Total staked: 0 TCP

After:
├─ User balance: 0 TCP
├─ User stake: 1,000 TCP
├─ Contract balance: 1,000 TCP
└─ Total staked: 1,000 TCP
```

**Result**
```
✓ Stake recorded
✓ Rewards begin accruing
✓ Position active
```

#### Step 3: Monitor Rewards

**Action**: Track accruing rewards over time

**Instructions**
1. Open staking interface
2. View "Your Rewards"
3. Check accrual rate
4. Monitor over time

**Reward Accrual**
```
Day 1:   Accrued ≈ 0.027 TCP
Day 7:   Accrued ≈ 0.19 TCP
Day 30:  Accrued ≈ 0.82 TCP
Day 90:  Accrued ≈ 2.47 TCP
Day 365: Accrued ≈ 10 TCP
```

**Result**
```
✓ Rewards accruing
✓ Visible in interface
✓ Claimable anytime
```

### Workflow Summary

```
Approve → Stake → Monitor → Ready to Claim
```

---

## Workflow 2: Claiming Rewards

### Objective
Claim earned rewards without unstaking.

### Prerequisites
- Active staking position
- Accrued rewards > 0
- Sufficient MATIC for gas

### Step-by-Step Process

#### Step 1: Check Rewards

**Action**: View earned rewards

**Instructions**
1. Open staking interface
2. View "Your Rewards"
3. Note the amount
4. Decide to claim

**Reward Display**
```
Your Rewards: 25.50 TCP
├─ Accrued: 25.50 TCP
├─ Reserved: 25.50 TCP
├─ Available: Yes
└─ Claimable: Yes
```

#### Step 2: Claim Rewards

**Action**: Transfer rewards to wallet

**Instructions**
1. Click "Claim Rewards"
2. Review amount
3. Sign transaction
4. Wait for confirmation

**On-Chain**
```
Transaction: claimRewards()
├─ From: User wallet
├─ To: Staking contract
├─ Function: claimRewards()
├─ Gas: ~70,000 GWEI
└─ Status: Confirmed
```

**State Changes**
```
Before:
├─ User rewards: 25.50 TCP
├─ User balance: 0 TCP
├─ Reward pool: 69,999,974.50 TCP
└─ Reserved: 25.50 TCP

After:
├─ User rewards: 0 TCP
├─ User balance: 25.50 TCP
├─ Reward pool: 69,999,949 TCP
└─ Reserved: 0 TCP
```

**Result**
```
✓ Rewards transferred
✓ Balance updated
✓ Rewards reset to zero
✓ New accrual begins
```

#### Step 3: Verify Claim

**Action**: Confirm rewards received

**Instructions**
1. Check wallet balance
2. Verify transaction on PolygonScan
3. Confirm amount received

**Verification**
```
✓ Wallet balance increased
✓ Transaction confirmed
✓ Event emitted: RewardsClaimed
✓ Claim successful
```

### Workflow Summary

```
Check Rewards → Claim → Verify → New Accrual Begins
```

---

## Workflow 3: Partial Unstaking

### Objective
Unstake some tokens while keeping others staking.

### Prerequisites
- Active staking position
- Staked amount > unstake amount
- Sufficient MATIC for gas

### Step-by-Step Process

#### Step 1: Decide Unstake Amount

**Action**: Determine how much to unstake

**Instructions**
1. View current stake
2. Decide amount to unstake
3. Keep remaining stake
4. Plan for rewards

**Example**
```
Current stake: 1,000 TCP
Unstake amount: 500 TCP
Remaining stake: 500 TCP
```

#### Step 2: Unstake Tokens

**Action**: Transfer tokens back to wallet

**Instructions**
1. Enter unstake amount
2. Review details
3. Click "Unstake"
4. Sign transaction
5. Wait for confirmation

**On-Chain**
```
Transaction: unstake()
├─ From: User wallet
├─ To: Staking contract
├─ Function: unstake(amount)
├─ Gas: ~80,000 GWEI
└─ Status: Confirmed
```

**State Changes**
```
Before:
├─ User stake: 1,000 TCP
├─ User balance: 0 TCP
├─ Contract balance: 1,000 TCP
└─ Total staked: 1,000 TCP

After:
├─ User stake: 500 TCP
├─ User balance: 500 TCP
├─ Contract balance: 500 TCP
└─ Total staked: 500 TCP
```

**Result**
```
✓ Tokens unstaked
✓ Tokens returned to wallet
✓ Remaining stake active
✓ Rewards continue accruing
```

#### Step 3: Manage Remaining Position

**Action**: Continue staking with reduced amount

**Instructions**
1. Monitor remaining stake
2. Track rewards
3. Claim when desired
4. Unstake more later if needed

**Result**
```
✓ Partial position maintained
✓ Rewards continue accruing
✓ Flexible management
```

### Workflow Summary

```
Check Stake → Unstake Partial → Verify → Continue Staking
```

---

## Workflow 4: Complete Exit

### Objective
Unstake all tokens and claim all rewards.

### Prerequisites
- Active staking position
- Accrued rewards (optional)
- Sufficient MATIC for gas

### Step-by-Step Process

#### Step 1: Claim Final Rewards

**Action**: Claim all accrued rewards before unstaking

**Instructions**
1. View accrued rewards
2. Click "Claim Rewards"
3. Sign transaction
4. Wait for confirmation

**On-Chain**
```
Transaction: claimRewards()
├─ Amount: All accrued rewards
├─ Gas: ~70,000 GWEI
└─ Status: Confirmed
```

**Result**
```
✓ Rewards transferred
✓ Rewards reset to zero
✓ Ready to unstake
```

#### Step 2: Unstake All Tokens

**Action**: Transfer all staked tokens back to wallet

**Instructions**
1. Enter full stake amount
2. Review details
3. Click "Unstake"
4. Sign transaction
5. Wait for confirmation

**On-Chain**
```
Transaction: unstake()
├─ Amount: Full stake
├─ Gas: ~80,000 GWEI
└─ Status: Confirmed
```

**State Changes**
```
Before:
├─ User stake: 1,000 TCP
├─ User balance: 25.50 TCP (claimed rewards)
├─ Contract balance: 1,000 TCP
└─ Total staked: 1,000 TCP

After:
├─ User stake: 0 TCP
├─ User balance: 1,025.50 TCP
├─ Contract balance: 0 TCP
└─ Total staked: 0 TCP
```

**Result**
```
✓ All tokens unstaked
✓ All tokens returned
✓ Position closed
✓ Exit complete
```

#### Step 3: Verify Exit

**Action**: Confirm all tokens received

**Instructions**
1. Check wallet balance
2. Verify stake is zero
3. Confirm no pending rewards
4. Check PolygonScan

**Verification**
```
✓ Wallet balance: 1,025.50 TCP
✓ Stake balance: 0 TCP
✓ Pending rewards: 0 TCP
✓ Exit verified
```

### Workflow Summary

```
Claim Rewards → Unstake All → Verify → Exit Complete
```

---

## Workflow 5: Reward Compounding

### Objective
Claim rewards and restake them for compound growth.

### Prerequisites
- Active staking position
- Accrued rewards > 0
- Sufficient MATIC for gas

### Step-by-Step Process

#### Step 1: Claim Rewards

**Action**: Claim accrued rewards

**Instructions**
1. View accrued rewards
2. Click "Claim Rewards"
3. Sign transaction
4. Wait for confirmation

**Result**
```
✓ Rewards transferred to wallet
✓ Rewards reset to zero
✓ Ready to restake
```

#### Step 2: Approve Additional Staking

**Action**: Grant permission for claimed rewards

**Instructions**
1. Click "Approve"
2. Confirm amount (claimed rewards)
3. Sign transaction
4. Wait for confirmation

**Result**
```
✓ Allowance set for claimed rewards
✓ Ready to restake
```

#### Step 3: Restake Rewards

**Action**: Stake claimed rewards for compound growth

**Instructions**
1. Enter claimed reward amount
2. Click "Stake"
3. Sign transaction
4. Wait for confirmation

**State Changes**
```
Before:
├─ Stake: 1,000 TCP
├─ Balance: 25.50 TCP (claimed)
└─ Total position: 1,000 TCP

After:
├─ Stake: 1,025.50 TCP
├─ Balance: 0 TCP
└─ Total position: 1,025.50 TCP
```

**Result**
```
✓ Rewards restaked
✓ Larger stake earning rewards
✓ Compound growth begins
```

#### Step 4: Monitor Compound Growth

**Action**: Track increasing rewards from larger stake

**Instructions**
1. Monitor new stake amount
2. Track increased reward accrual
3. Repeat claiming and restaking
4. Watch compound growth

**Compound Example**
```
Year 1:
├─ Initial stake: 1,000 TCP
├─ Earned: 100 TCP
└─ Total: 1,100 TCP

Year 2:
├─ Stake: 1,100 TCP
├─ Earned: 110 TCP
└─ Total: 1,210 TCP

Year 3:
├─ Stake: 1,210 TCP
├─ Earned: 121 TCP
└─ Total: 1,331 TCP
```

### Workflow Summary

```
Claim → Approve → Restake → Monitor Growth → Repeat
```

---

## Workflow 6: Emergency Unstaking

### Objective
Quickly unstake all tokens in case of emergency.

### Prerequisites
- Active staking position
- Urgent need for liquidity
- Sufficient MATIC for gas

### Step-by-Step Process

#### Step 1: Assess Situation

**Action**: Determine if emergency unstaking is necessary

**Considerations**
```
✓ Need immediate liquidity
✓ Willing to forgo pending rewards
✓ Understand no lock-up period
✓ Ready to execute
```

#### Step 2: Unstake Immediately

**Action**: Unstake all tokens without claiming rewards

**Instructions**
1. Enter full stake amount
2. Click "Unstake"
3. Sign transaction
4. Wait for confirmation

**Result**
```
✓ Tokens unstaked immediately
✓ Tokens returned to wallet
✓ No lock-up period
✓ Liquidity available
```

#### Step 3: Claim Rewards Later

**Action**: Claim pending rewards after emergency resolves

**Instructions**
1. Wait for emergency to resolve
2. Return to staking interface
3. View pending rewards
4. Claim when ready

**Result**
```
✓ Rewards still available
✓ Can claim anytime
✓ No loss of rewards
```

### Workflow Summary

```
Emergency → Unstake Immediately → Resolve → Claim Rewards
```

---

## Common Workflow Patterns

### Pattern 1: Regular Claiming

```
Stake → Wait 30 days → Claim → Wait 30 days → Claim → Repeat
```

### Pattern 2: Compound Growth

```
Stake → Claim → Restake → Larger stake → Claim → Restake → Repeat
```

### Pattern 3: Gradual Exit

```
Stake → Claim → Unstake 25% → Claim → Unstake 25% → Repeat
```

### Pattern 4: Long-term Holding

```
Stake → Claim annually → Restake → Hold → Repeat
```

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

## Troubleshooting

### Issue: Approval Fails

**Cause**: Insufficient balance or allowance issues

**Solution**
1. Check wallet balance
2. Verify token contract address
3. Try approving exact amount
4. Retry transaction

### Issue: Stake Fails

**Cause**: Insufficient balance or reward pool issues

**Solution**
1. Check wallet balance
2. Verify approval amount
3. Check reward pool availability
4. Retry transaction

### Issue: Claim Fails

**Cause**: No rewards or pool issues

**Solution**
1. Verify you have accrued rewards
2. Check reward pool balance
3. Verify contract balance
4. Retry transaction

### Issue: Unstake Fails

**Cause**: Insufficient stake or contract issues

**Solution**
1. Check your stake balance
2. Verify unstake amount
3. Ensure contract has balance
4. Retry transaction

---

## See also

- [How Staking Works](/docs/staking-rewards/how-staking-works)
- [Reward Distribution Logic](/docs/staking-rewards/reward-distribution-logic)
- [Reward Funding](/docs/staking-rewards/reward-funding)
- [Technical Validation](/docs/staking-rewards/technical-validation)
- [FAQ](/docs/category/faq)
