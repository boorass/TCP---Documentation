---
title: Why Polygon
sidebar_position: 3
description: Understanding TCP's deployment on Polygon and the benefits it provides
---

# Why Polygon

Protocol (TCP) is deployed on **Polygon**, a leading Ethereum scaling solution. This choice enables TCP to operate efficiently while maintaining full EVM compatibility and security.

## What is Polygon?

Polygon is a Layer 2 scaling solution for Ethereum that provides:

- **EVM Compatibility** — Full compatibility with Ethereum smart contracts and tools
- **High Speed** — Fast block times and transaction finality
- **Low Costs** — Significantly reduced transaction fees compared to Ethereum mainnet
- **Security** — Backed by Ethereum's security through periodic checkpoints
- **Maturity** — Established infrastructure with billions in TVL

## Why TCP Chose Polygon

### 1. Cost Efficiency

Polygon's low transaction fees enable:
- **Accessible Staking** — Users can stake with minimal gas costs
- **Frequent Interactions** — Treasury operations, liquidity management, and reward distribution don't incur prohibitive fees
- **Community Participation** — Lower barriers for token holders to engage with the protocol

### 2. Speed & User Experience

Polygon's fast finality provides:
- **Quick Confirmations** — Transactions settle in seconds, not minutes
- **Responsive Operations** — Treasury proposals and liquidity withdrawals execute quickly
- **Better UX** — Users experience smooth, responsive interactions

### 3. EVM Compatibility

Full Ethereum compatibility means:
- **Standard Tools** — MetaMask, Etherscan (PolygonScan), Hardhat, Truffle all work seamlessly
- **Developer Familiarity** — Solidity developers can work with TCP contracts immediately
- **Ecosystem Integration** — Easy integration with DeFi protocols, exchanges, and wallets
- **Audit Tools** — Standard security analysis tools work without modification

### 4. Established Ecosystem

Polygon's mature ecosystem provides:
- **Exchange Support** — Major exchanges support Polygon deposits/withdrawals
- **Wallet Integration** — All major wallets support Polygon
- **DeFi Liquidity** — Established DEXs and liquidity pools
- **Infrastructure** — Reliable RPC providers, indexers, and monitoring tools

### 5. Institutional Readiness

Polygon is recognized by:
- **Institutional Investors** — Established as a legitimate scaling solution
- **Regulatory Clarity** — Clearer regulatory treatment than experimental chains
- **Enterprise Adoption** — Used by major brands and protocols
- **Audit Firms** — Security firms have extensive Polygon experience

## TCP Operations on Polygon

### Treasury Management
- Proposal creation and execution with timelocks
- Asset management with low transaction costs
- On-chain verification via PolygonScan

### Liquidity Management
- LP protection with permanent and flexible portions
- Withdrawal proposals with timelock enforcement
- Real-time balance verification

### Staking & Rewards
- User-friendly staking with minimal gas costs
- Reward distribution to thousands of participants
- Claim operations affordable for all users

### Token Transfers
- Fast, low-cost transfers between users
- Integration with DEXs for trading
- Seamless wallet interactions

### Community Participation
- Governance interactions accessible to all
- Event monitoring and verification
- Community-run tools and dashboards

## Polygon Network Details

| Property | Value |
|----------|-------|
| **Chain ID** | 137 |
| **Currency** | MATIC |
| **Block Time** | ~2 seconds |
| **Finality** | ~128 blocks (~3 minutes) |
| **Explorer** | PolygonScan |
| **RPC Endpoint** | https://polygon-rpc.com/ |

## Accessing Polygon

### For Users
1. **Add Polygon to MetaMask** — Use the Polygon RPC endpoint
2. **Bridge Assets** — Use official bridges to move assets from Ethereum or other chains
3. **Trade on DEXs** — Use Uniswap, QuickSwap, or other Polygon DEXs
4. **Interact with TCP** — Connect wallet and interact with TCP contracts

### For Developers
1. **Network Configuration** — Add Polygon to your development environment
2. **Contract Deployment** — Deploy using Hardhat, Truffle, or Foundry
3. **Testing** — Use Polygon testnet (Mumbai) for development
4. **Verification** — Verify contracts on PolygonScan

## Security Considerations

### Polygon's Security Model
- **Validator Network** — Secured by a distributed set of validators
- **Ethereum Checkpoints** — Regular checkpoints to Ethereum mainnet
- **Slashing** — Validators are slashed for misbehavior
- **Decentralization** — Over 100 validators securing the network

### TCP's Additional Safeguards
- **Smart Contract Security** — Timelocks and access controls
- **Operational Discipline** — Proposal-based critical operations
- **Audit Trail** — All actions logged on-chain
- **Recovery Functions** — Accident recovery mechanisms

## Comparison: Why Not Other Chains?

| Factor | Polygon | Ethereum | Arbitrum | Optimism |
|--------|---------|----------|----------|----------|
| **Cost** | Very Low | High | Low | Low |
| **Speed** | Fast | Slow | Fast | Fast |
| **EVM Compatible** | Yes | Native | Yes | Yes |
| **Maturity** | Established | Established | Growing | Growing |
| **Institutional Support** | Strong | Strongest | Growing | Growing |
| **TCP Choice** | ✅ | ❌ | Possible | Possible |

Polygon provides the optimal balance of cost, speed, maturity, and ecosystem support for TCP's operations.

## Future Considerations

As Polygon evolves:
- **Dencun Upgrade** — Further cost reductions through Ethereum improvements
- **Polygon 2.0** — Enhanced security and interoperability
- **Cross-Chain Bridges** — Potential future expansion to other chains

TCP's modular architecture makes it possible to expand to other networks in the future if needed, but Polygon remains the primary deployment.

---

**Next:** See [Quick Facts](./quick-facts.md) for a summary of TCP's key information.
