---
title: "Liquidity Manager Evolution"
sidebar_position: 7
description: "TCP Liquidity Manager V1 and V3 deployment history, operational improvements, and security continuity"
sidebar_custom_props:
  icon: clock-clockwise
---

# Liquidity Manager Evolution

TCP's liquidity management has evolved through two deployed contract versions, each maintaining the same core security model and liquidity philosophy while improving operational capabilities.

## TCP Liquidity Manager V1

TCP Liquidity Manager V1 was the initial liquidity management contract that established the protocol's liquidity protection framework.

### V1 Features

V1 introduced and enforced:

- **85% Permanent Liquidity Allocation** - Long-term locked portion
- **15% Flexible Liquidity Allocation** - Operationally accessible portion
- **365-day Permanent Liquidity Lock** - Enforced by smart contract
- **72-hour Timelocked Withdrawals** - All withdrawals require waiting period
- **Multisig-Controlled Liquidity Operations** - Governance-protected actions
- **Daily and Per-Transaction Withdrawal Limits** - Rate limiting on flexible portion

### V1 Design

V1 was designed around a single initial LP deposit model. The contract successfully enforced the protocol's liquidity protection philosophy, establishing the foundational security controls that remain in place today.

The permanent lock mechanism and daily limits proved effective at protecting LP while allowing necessary operational flexibility.

## TCP Liquidity Manager V3

TCP Liquidity Manager V3 was introduced as an operational enhancement to improve liquidity management capabilities while preserving all core security controls.

### V3 Improvements

V3 added operational enhancements:

- **Support for Progressive Liquidity Additions** - Ability to add liquidity over time rather than single deposit
- **Improved Liquidity Management Flexibility** - Enhanced operational workflows
- **Simplified Withdrawal Proposal Architecture** - Streamlined proposal mechanics
- **Preservation of All Core Security Controls** - No reduction in protection

### V3 Security Continuity

V3 maintains all critical security features from V1:

- **85% Permanent Liquidity Allocation** - Same protection ratio
- **15% Flexible Liquidity Allocation** - Same operational allocation
- **365-day Permanent Lock** - Same lock duration
- **72-hour Withdrawal Timelocks** - Same timelock period
- **Multisig Governance Controls** - Same approval requirements
- **Withdrawal Rate Limits** - Same daily consumption limits

The security model, access controls, and protection mechanisms are unchanged between versions.

## Tokenomics Continuity

The migration from V1 to V3 does not modify TCP tokenomics.

The following remain unchanged:

- **Liquidity Allocation Model** - 85/15 split preserved
- **Security Framework** - All protections maintained
- **Governance Controls** - Multisig requirements unchanged
- **Liquidity Protection Mechanisms** - Lock and timelock rules unchanged

Only operational liquidity management capabilities were improved. No token supply, distribution, or economic model changes occurred.

## Current Status

### V1 Deployment

TCP Liquidity Manager V1 remains deployed as part of the protocol's operational history. The contract continues to function and can be monitored on-chain.

### V3 Deployment

TCP Liquidity Manager V3 is the active liquidity management contract currently used for protocol operations and future liquidity management activities.

Both versions maintain the same liquidity philosophy and security standards.

## Migration Philosophy

The upgrade from V1 to V3 reflects TCP's commitment to:

1. **Operational Excellence** - Improving workflows without compromising security
2. **Security Preservation** - Maintaining all protection mechanisms
3. **Transparency** - Clear documentation of changes and continuity
4. **Community Trust** - No hidden changes to tokenomics or protection levels

## Verification

You can verify both contract versions on-chain:

- **V1 Contract** - Available on PolygonScan with full transaction history
- **V3 Contract** - Active contract with current liquidity operations
- **Lock Status** - Query functions show all locks and their expiration dates
- **Withdrawal History** - All proposals and executions logged on-chain

See [Deployed Addresses](/docs/smart-contracts/deployed-addresses) for contract locations.

## See also

- [Liquidity Manager Contract](/docs/protocol-architecture/liquidity-manager) - Technical reference
- [Liquidity Protection](/docs/security-model/liquidity-protection) - Security model details
- [Permanent Liquidity Rules](/docs/liquidity-framework/permanent-liquidity-rules) - Lock mechanics
- [Flexible Liquidity Rules](/docs/liquidity-framework/flexible-liquidity-rules) - Flexible portion rules
