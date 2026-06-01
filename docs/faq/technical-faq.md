---
title: Technical FAQ
sidebar_position: 2
description: Technical questions about Protocol (TCP)
---

# Technical FAQ

## Why does TCP use multiple contracts?

Multiple contracts provide:
- Clear separation of concerns
- Reduced risk concentration
- Easier auditing
- Better maintainability
- Improved security

## What is a timelock?

A timelock is a smart contract mechanism that:
- Records a proposed operation
- Enforces a waiting period
- Allows execution only after period expires
- Enables cancellation before execution

## Why are timelocks important?

Timelocks:
- Prevent instant-action risks
- Enable community oversight
- Allow error correction
- Build confidence

## How does the liquidity manager work?

The liquidity manager:
- Separates LP into permanent (85%) and flexible (15%)
- Enforces 365+ day lock on permanent portion
- Applies daily limits to flexible portion
- Requires proposal and timelock for withdrawals

## What is the daily withdrawal limit?

The daily limit caps how much flexible LP can be withdrawn per day. The exact limit is configurable.

## Can I bypass the timelock?

No, timelocks are enforced by smart contracts and cannot be bypassed.

## How are rewards calculated?

Rewards are calculated as:
```
User Reward = (User Stake / Total Stake) × Total Rewards
```

## Can I lose my staked tokens?

Staking involves smart contract risk. While designed safely, vulnerabilities are possible. Only stake what you can afford to lose.

## How do I verify contract addresses?

1. Visit PolygonScan
2. Search for contract address
3. Verify source code
4. Check official sources

## Are contracts verified on PolygonScan?

Yes, all contracts are verified on PolygonScan.

## How do I integrate with TCP?

See [Integration Notes](../smart-contracts/integration-notes.md) for integration guidance.

## What is the token standard?

TCP is ERC-20 compatible.

## How many decimals does TCP have?

TCP has 18 decimals.

## Can I use TCP on other chains?

TCP is deployed on Polygon. Cross-chain bridges may be available.

## How do I monitor TCP operations?

You can monitor using:
- PolygonScan
- Contract functions
- Community tools
- Event logs

---

**Next:** See [Security FAQ](./security-faq.md) for security questions.
