---
title: "Staking Resources"
sidebar_position: 9
description: "Links to staking documentation, contracts, and community resources"
sidebar_custom_props:
  icon: "link-simple"
---

This page provides links to important staking resources, including documentation, contract information, and community channels.

## Documentation

### Core Guides

- [Introduction to TCP Staking](/docs/staking-rewards/introduction) - Overview and key characteristics
- [How Staking Works](/docs/staking-rewards/how-staking-works) - Step-by-step user guide
- [Reward Distribution Logic](/docs/staking-rewards/reward-distribution-logic) - Technical mechanics
- [Reward Funding](/docs/staking-rewards/reward-funding) - Pool management and protection
- [User Flows](/docs/staking-rewards/user-flows) - Complete workflows for all operations
- [Technical Validation](/docs/staking-rewards/technical-validation) - Testing and validation details

### Reference

- [TCPStakingV2 Contract](/docs/protocol-architecture/staking) - Technical contract details
- [Staking FAQ](/docs/staking-rewards/staking-faq) - Common questions and answers
- [Changelog](/docs/staking-rewards/changelog) - Version history and updates

## Contract Information

### TCPStakingV2

**Status**: Production-ready and fully operational  
**Network**: Polygon Mainnet  
**Validation**: Comprehensive testing completed  
**Audits**: Internal audits passed  

### Contract Functions

**Staking Operations**
- `stake(uint256 amount)` - Stake TCP tokens
- `unstake(uint256 amount)` - Unstake tokens
- `claimRewards()` - Claim earned rewards

**Query Functions**
- `getStakeBalance(address user)` - Check staked amount
- `getRewardBalance(address user)` - Check earned rewards
- `getAvailableRewards()` - Check pool availability
- `getTotalStaked()` - Check total staking

**Admin Functions**
- `fundRewards(uint256 amount)` - Fund reward pool (owner-only)
- `verifyBalance()` - Verify accounting consistency

### Events

- `Staked(address indexed user, uint256 amount)` - Emitted when tokens are staked
- `Unstaked(address indexed user, uint256 amount)` - Emitted when tokens are unstaked
- `RewardsClaimed(address indexed user, uint256 amount)` - Emitted when rewards are claimed
- `RewardsFunded(uint256 amount)` - Emitted when rewards are funded

## Verification

### On-Chain Verification

You can verify the staking contract on PolygonScan:

1. Go to [PolygonScan](https://polygonscan.com)
2. Search for the TCPStakingV2 contract address
3. View the contract code
4. Verify the source code matches the deployed contract

### Balance Verification

You can check your staking position:

1. Visit the staking interface
2. Connect your wallet
3. View your stake balance
4. View your earned rewards
5. Verify on PolygonScan

### Pool Status

You can check the reward pool status:

1. Query the contract on PolygonScan
2. Call `getAvailableRewards()` to check available rewards
3. Call `rewardFunded` to check total funded
4. Call `rewardReserved` to check reserved rewards

## Community Resources

### Official Links

- [Protocol Website](https://tcp-protocol.com) - Official website
- [GitHub Repository](https://github.com/tcp-protocol) - Source code
- [Documentation](https://docs.tcp-protocol.com) - Full documentation

### Community Channels

- [Discord](https://discord.gg/tcp-protocol) - Community chat
- [Twitter](https://twitter.com/tcp_protocol) - Official Twitter
- [Telegram](https://t.me/tcp_protocol) - Telegram group
- [Forum](https://forum.tcp-protocol.com) - Community forum

### Support

- [Contact Support](/docs/resources/contact-support) - Support options
- [FAQ](/docs/category/faq) - Common questions
- [Troubleshooting](/docs/staking-rewards/staking-faq#troubleshooting) - Troubleshooting guide

## Tools and Calculators

### Staking Calculator

Calculate your potential earnings:

1. Enter your stake amount
2. Enter the reward rate
3. Enter the duration
4. View estimated earnings

### Gas Calculator

Estimate transaction costs:

1. Check current gas prices on PolygonScan
2. Estimate gas for staking operations
3. Calculate transaction costs in MATIC and USD

### Portfolio Tracker

Track your staking position:

1. Connect your wallet
2. View your stake balance
3. View your earned rewards
4. Track transaction history

## External Resources

### Polygon Network

- [Polygon Website](https://polygon.technology) - Polygon network information
- [PolygonScan](https://polygonscan.com) - Block explorer
- [Polygon Docs](https://docs.polygon.technology) - Technical documentation

### Wallet Integration

- [MetaMask](https://metamask.io) - Popular Ethereum wallet
- [Ledger](https://www.ledger.com) - Hardware wallet
- [Trezor](https://trezor.io) - Hardware wallet
- [WalletConnect](https://walletconnect.com) - Wallet connection protocol

### DeFi Resources

- [DeFi Pulse](https://defipulse.com) - DeFi analytics
- [CoinGecko](https://coingecko.com) - Token information
- [CoinMarketCap](https://coinmarketcap.com) - Market data

## Learning Resources

### Blockchain Basics

- [Ethereum Documentation](https://ethereum.org/en/developers/docs/) - Ethereum technical docs
- [Smart Contract Security](https://consensys.github.io/smart-contract-best-practices/) - Security best practices
- [Solidity Documentation](https://docs.soliditylang.org) - Solidity language docs

### DeFi Concepts

- [DeFi Primer](https://blog.coinbase.com/a-beginners-guide-to-decentralized-finance-defi-574c68ff43c0) - DeFi introduction
- [Staking Guide](https://ethereum.org/en/staking/) - Ethereum staking guide
- [Token Economics](https://blog.coinbase.com/token-economics-101-what-is-tokenomics-1-of-4-faecf7176f86) - Tokenomics basics

## Reporting Issues

### Bug Reports

If you discover a bug:

1. Do not exploit it
2. Document the issue
3. Report to the protocol team
4. Follow responsible disclosure

### Feature Requests

To suggest features:

1. Visit the community forum
2. Check if the feature is already requested
3. Submit a detailed feature request
4. Engage with the community

### Security Issues

For security issues:

1. Do not disclose publicly
2. Contact the security team
3. Provide detailed information
4. Allow time for response

## FAQ

### Where can I find the contract address?

The TCPStakingV2 contract address is available on:
- PolygonScan
- Protocol documentation
- GitHub repository

### How do I verify the contract?

You can verify the contract on PolygonScan by:
1. Searching for the contract address
2. Viewing the contract code
3. Comparing with the source code
4. Checking the deployment transaction

### How do I check my rewards?

You can check your rewards through:
- Staking interface
- PolygonScan contract interaction
- Wallet integration
- Direct contract query

### How do I report a bug?

If you discover a bug:
1. Do not exploit it
2. Document the issue
3. Report to the protocol team
4. Follow responsible disclosure

## See also

- [Introduction to TCP Staking](/docs/staking-rewards/introduction)
- [How Staking Works](/docs/staking-rewards/how-staking-works)
- [Staking FAQ](/docs/staking-rewards/staking-faq)
- [Contact Support](/docs/resources/contact-support)
- [Community Links](/docs/resources/community-links)
