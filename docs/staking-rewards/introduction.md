---
title: "Introduction to TCP Staking"
sidebar_position: 1
description: "Overview of TCP Protocol's on-chain staking system and reward mechanisms"
sidebar_custom_props:
  icon: "rocket"
---

TCP Protocol features a fully on-chain staking system that enables TCP token holders to lock their tokens and earn rewards. This documentation provides a comprehensive guide to understanding, using, and integrating with the staking infrastructure.

## What is TCP Staking?

TCP Staking is a decentralized, smart-contract-based mechanism that allows token holders to:

- **Deposit TCP tokens** into the staking contract
- **Earn rewards** proportional to their stake
- **Claim rewards** at any time without restrictions
- **Unstake tokens** immediately without lock-up periods

The staking system is powered by **TCPStakingV2**, the official production contract deployed on Polygon Mainnet after comprehensive validation and testing.

## Key Characteristics

| Feature | Details |
|---------|---------|
| **Contract** | TCPStakingV2 (official version) |
| **Network** | Polygon Mainnet |
| **Lock-up Period** | None (flexible unstaking) |
| **Reward Pool** | 70,000,000 TCP (maximum) |
| **Calculation** | On-chain, continuous accrual |
| **Claim Frequency** | Anytime (no restrictions) |
| **Governance** | Multisig-protected |

## Architecture Overview

The staking system operates through a modular architecture:

```
TCP Token (ERC-20)
        ↓
TCPStakingV2 Contract
        ↓
    ├─ Stake Management
    ├─ Reward Calculation
    ├─ Reward Distribution
    └─ Claim Processing
        ↓
Reward Pool (70M TCP)
        ↓
Participants & Rewards
```

## Development History

TCPStakingV2 represents the final, production-ready implementation of the staking system:

- **Design Phase**: Initial architecture and specification
- **Development Phase**: Smart contract implementation
- **Internal Audits**: Multiple security reviews completed
- **Safe Simulations**: Comprehensive testing on Safe multisig
- **Polygon Mainnet Testing**: Full validation on production network
- **Official Deployment**: TCPStakingV2 confirmed as official version

No migration to a V3 was necessary. After extensive testing, TCPStakingV2 was validated as fully functional and secure, making it the definitive staking implementation for TCP Protocol.

## Quick Start

### For Users

1. **Approve** the staking contract to spend your TCP tokens
2. **Stake** your desired amount of TCP
3. **Monitor** your rewards as they accrue continuously
4. **Claim** rewards at any time
5. **Unstake** tokens whenever you choose

### For Developers

1. Review the [TCPStakingV2 contract details](/docs/protocol-architecture/staking)
2. Understand the [reward mechanics](/docs/staking-rewards/reward-distribution-logic)
3. Integrate with the [Router](/docs/protocol-architecture/protocol-router)
4. Implement [user flows](/docs/staking-rewards/user-flows)

## Documentation Structure

This staking documentation is organized into several sections:

- **How Staking Works**: Step-by-step user guide
- **Reward Distribution Logic**: Technical mechanics of reward calculation
- **Reward Funding**: How the reward pool is managed
- **User Flows**: Complete workflows for all staking operations
- **Technical Validation**: Details of testing and validation
- **Security**: Protection mechanisms and best practices
- **FAQ**: Common questions and answers

## Key Principles

### Transparency

All staking operations are recorded on-chain and verifiable through Polygon Mainnet. Users can audit their stakes, rewards, and claims at any time.

### Security

TCPStakingV2 includes multiple layers of protection:
- Owner validation and multisig governance
- Automatic reward pool overflow protection
- Continuous reward accrual without double-payment risk
- Timelock-protected treasury integration

### Simplicity

The staking mechanism is designed to be straightforward:
- No complex lock-up periods
- No tier-based restrictions
- No minimum or maximum stake limits
- Rewards calculated automatically on-chain

### Sustainability

The reward system is designed for long-term viability:
- Fixed reward pool of 70,000,000 TCP
- Automatic pool overflow prevention
- Transparent reward tracking
- Governance-controlled adjustments

## Official Contract

**TCPStakingV2** is the official, production-ready staking contract for TCP Protocol.

- **Status**: Active and fully operational
- **Network**: Polygon Mainnet
- **Validation**: Complete
- **Audits**: Internal audits passed
- **Testing**: Mainnet validation complete

## Next Steps

- Learn [how staking works](/docs/staking-rewards/how-staking-works) with detailed examples
- Understand [reward distribution logic](/docs/staking-rewards/reward-distribution-logic)
- Review [technical validation](/docs/staking-rewards/technical-validation)
- Check the [FAQ](/docs/faq/general-faq) for common questions

## See also

- [TCPStakingV2 Contract Details](/docs/protocol-architecture/staking)
- [Reward Funding](/docs/staking-rewards/reward-funding)
- [User Flows](/docs/staking-rewards/user-flows)
- [Security Model](/docs/category/security-model)
