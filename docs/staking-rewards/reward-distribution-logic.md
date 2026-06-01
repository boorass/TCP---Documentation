---
title: Reward Distribution Logic
sidebar_position: 3
description: Understanding how TCP staking rewards are calculated and distributed
---

# Reward Distribution Logic

Protocol (TCP) uses a **transparent, fair reward distribution system** where rewards are calculated based on stake and distributed automatically.

## Reward Calculation

### Basic Formula

```
User Reward = (User Stake / Total Stake) × Total Rewards
```

### Example Calculation

```
User Stake: 1,000 TCP
Total Stake: 100,000 TCP
Total Rewards (Annual): 10,000 TCP

User Reward = (1,000 / 100,000) × 10,000 = 100 TCP
```

## Distribution Mechanism

### Continuous Accrual

Rewards accrue continuously:
- Calculated per block
- Updated on each interaction
- Claimable anytime
- No lock-up period

### Automatic Distribution

Rewards are distributed automatically:
- User claims rewards
- Rewards transferred
- Claim recorded on-chain
- Event emitted

### Fair Distribution

Distribution is fair because:
- Same rate for all users
- Proportional to stake
- No favoritism
- Transparent calculation

## Reward Timing

### Accrual Timeline

```
Day 0: Stake 1,000 TCP
Day 1: Rewards accrue
Day 2: More rewards accrue
...
Day 365: Annual rewards accumulated
```

### Claim Timeline

```
Day 0: Stake tokens
Day 1: Can claim (if rewards accrued)
Day 2: Can claim
...
Anytime: Can claim accumulated rewards
```

### Unstake Timeline

```
Day 0: Stake tokens
Day 1: Can unstake anytime
Day 2: Can unstake anytime
...
Anytime: Can unstake without lock-up
```

## Reward Scenarios

### Scenario 1: Simple Staking

```
Stake: 1,000 TCP
Reward Rate: 10% APY
Duration: 1 year

Calculation:
Annual Reward = 1,000 × 10% = 100 TCP
Daily Reward = 100 / 365 = 0.274 TCP
Monthly Reward = 100 / 12 = 8.33 TCP

After 1 year:
Total Earned: 100 TCP
Total Balance: 1,100 TCP
```

### Scenario 2: Increasing Stake

```
Day 0: Stake 1,000 TCP
Day 180: Stake additional 500 TCP
Reward Rate: 10% APY

Calculation:
Days 0-180: Reward on 1,000 TCP = 50 TCP
Days 180-365: Reward on 1,500 TCP = 75 TCP
Total Annual: 125 TCP

After 1 year:
Total Earned: 125 TCP
Total Staked: 1,500 TCP
Total Balance: 1,625 TCP
```

### Scenario 3: Decreasing Stake

```
Day 0: Stake 1,000 TCP
Day 180: Unstake 500 TCP
Reward Rate: 10% APY

Calculation:
Days 0-180: Reward on 1,000 TCP = 50 TCP
Days 180-365: Reward on 500 TCP = 25 TCP
Total Annual: 75 TCP

After 1 year:
Total Earned: 75 TCP
Total Staked: 500 TCP
Unstaked: 500 TCP
Total Balance: 1,075 TCP
```

## Distribution Transparency

### Public Information

All distribution information is public:

✅ **Reward Rate** — Current reward rate  
✅ **Total Staked** — Total tokens staked  
✅ **Your Stake** — Your staked amount  
✅ **Your Rewards** — Your earned rewards  
✅ **Distribution History** — Past distributions  

### Verification Methods

You can verify distribution information:

1. **Staking Contract**
   - Check reward rate
   - View total staked
   - Check your stake
   - View your rewards

2. **PolygonScan**
   - View staking events
   - Monitor stake changes
   - Track reward distributions
   - Verify transactions

3. **Community Tools**
   - Use staking dashboards
   - Monitor reward rates
   - Track staking metrics
   - Analyze patterns

## Distribution Fairness

### Fair Principles

Distribution is fair because:

1. **Same Rate** — All users get same reward rate
2. **Proportional** — Rewards proportional to stake
3. **Transparent** — Calculation visible on-chain
4. **Automatic** — No manual intervention
5. **Verifiable** — Anyone can verify calculation

### Fairness Verification

You can verify fairness:

1. **Check Rate** — Verify all users get same rate
2. **Check Calculation** — Verify proportional calculation
3. **Check History** — Verify consistent application
4. **Check Events** — Verify all distributions logged
5. **Check Balances** — Verify correct amounts

## Distribution Best Practices

### For Stakers

✅ **Understand calculation** — Know how rewards calculated  
✅ **Monitor rewards** — Track your rewards  
✅ **Claim regularly** — Claim rewards periodically  
✅ **Verify calculation** — Verify your rewards  
✅ **Report discrepancies** — Report any issues  

### For Community

✅ **Monitor distribution** — Watch distribution patterns  
✅ **Verify fairness** — Verify fair distribution  
✅ **Assess sustainability** — Evaluate long-term viability  
✅ **Provide feedback** — Share suggestions  
✅ **Report issues** — Report any problems  

## Key Takeaways

1. **Fair calculation** — Proportional to stake
2. **Transparent** — Calculation visible on-chain
3. **Automatic** — No manual intervention
4. **Continuous** — Rewards accrue continuously
5. **Verifiable** — Anyone can verify calculation

---

**Next:** Learn about [User Flows](./user-flows.md) and typical staking workflows.
