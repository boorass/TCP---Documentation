---
title: "\\\"V2 to V3 Documentation Index\\\""
sidebar_position: 9
description: "\\\"Complete index of TCPStaking V2 to V3 migration documentation\\\""
sidebar_custom_props:
  icon: \"book-open\"
---

# V2 to V3 Documentation Index

Complete documentation for the TCPStaking V2 to V3 transition.

## Quick Start

**New to this migration?** Start here:

1. [Migration Summary](/docs/staking-rewards/migration-summary), 2-minute overview
2. [How Staking Works](/docs/staking-rewards/how-staking-works), User guide
3. [V2 to V3 Migration](/docs/staking-rewards/v2-to-v3-migration), Full technical details

## Documentation Structure

### For Users

**If you're a token holder or staker:**

- [Migration Summary](/docs/staking-rewards/migration-summary), What changed and what you need to know
- [How Staking Works](/docs/staking-rewards/how-staking-works), How to stake and earn rewards
- [Reward Funding](/docs/staking-rewards/reward-funding), How rewards are funded and sustained

### For Developers

**If you're integrating with the staking contract:**

- [V2 to V3 Migration](/docs/staking-rewards/v2-to-v3-migration), Technical architecture and improvements
- [Staking Contract](/docs/protocol-architecture/staking), Contract functions and interfaces
- [Integration Notes](/docs/smart-contracts/integration-notes), Integration guidelines

### For Governance

**If you're involved in protocol governance:**

- [Changelog: V2 to V3](/docs/staking-rewards/changelog-v2-v3), Official changelog entry
- [Upgrade & Migration Philosophy](/docs/governance-operations/upgrade-migration-philosophy), Protocol upgrade approach
- [Multisig Responsibilities](/docs/governance-operations/multisig-responsibilities), Governance roles

### For Auditors

**If you're auditing the protocol:**

- [V2 to V3 Migration](/docs/staking-rewards/v2-to-v3-migration), Root cause analysis and improvements
- [Staking Contract](/docs/protocol-architecture/staking), Contract technical details
- [Security Model](/docs/category/security-model), Protocol security overview

## Document Descriptions

### Migration Summary

**File:** `migration-summary.md`  
**Length:** ~2 minutes  
**Purpose:** Quick reference guide

**Contains:**
- What changed between V2 and V3
- What stayed the same
- User action required (none)
- Key facts and timeline
- FAQ

**Best for:** Users who want a quick overview

### V2 to V3 Migration (Full)

**File:** `v2-to-v3-migration.md`  
**Length:** ~10 minutes  
**Purpose:** Comprehensive technical documentation

**Contains:**
- Executive summary
- Timeline
- What happened in V2
- Root cause analysis
- Why V3 was created
- V3 design goals and improvements
- Protocol impact assessment
- Technical comparison
- Lessons learned
- Transparency and trust discussion

**Best for:** Developers, auditors, and those wanting full technical details

### Changelog: V2 to V3

**File:** `changelog-v2-v3.md`  
**Length:** ~8 minutes  
**Purpose:** Official changelog entry

**Contains:**
- Release information
- Issue description
- Root cause
- Resolution and improvements
- Migration details
- Technical details
- Deployment timeline
- Ecosystem compatibility
- Quality assurance results
- Community impact

**Best for:** Governance, auditors, and official record keeping

### How Staking Works

**File:** `how-staking-works.md`  
**Length:** ~8 minutes  
**Purpose:** User guide to staking

**Contains:**
- Staking overview
- Step-by-step staking process
- Reward mechanics
- Staking examples
- Benefits and risks
- Best practices

**Best for:** Token holders and stakers

### Reward Funding

**File:** `reward-funding.md`  
**Length:** ~6 minutes  
**Purpose:** How rewards are funded and sustained

**Contains:**
- Reward pool overview
- Funding mechanisms
- Reward sustainability
- Treasury integration
- Governance of rewards

**Best for:** Users wanting to understand reward sustainability

### Staking Contract (Technical)

**File:** `docs/protocol-architecture/staking.md`  
**Length:** ~6 minutes  
**Purpose:** Technical contract reference

**Contains:**
- Contract purpose
- Core functions
- Events
- Reward calculation
- Integration guide

**Best for:** Developers and integrators

## Navigation Guide

### By Role

**Token Holder**
1. [Migration Summary](/docs/staking-rewards/migration-summary)
2. [How Staking Works](/docs/staking-rewards/how-staking-works)
3. [Reward Funding](/docs/staking-rewards/reward-funding)

**Developer**
1. [V2 to V3 Migration](/docs/staking-rewards/v2-to-v3-migration)
2. [Staking Contract](/docs/protocol-architecture/staking)
3. [Integration Notes](/docs/smart-contracts/integration-notes)

**Auditor**
1. [V2 to V3 Migration](/docs/staking-rewards/v2-to-v3-migration)
2. [Changelog: V2 to V3](/docs/staking-rewards/changelog-v2-v3)
3. [Security Model](/docs/category/security-model)

**Governance**
1. [Changelog: V2 to V3](/docs/staking-rewards/changelog-v2-v3)
2. [Upgrade & Migration Philosophy](/docs/governance-operations/upgrade-migration-philosophy)
3. [Multisig Responsibilities](/docs/governance-operations/multisig-responsibilities)

### By Question

**\"What changed?\"**
- [Migration Summary](/docs/staking-rewards/migration-summary), Quick overview
- [V2 to V3 Migration](/docs/staking-rewards/v2-to-v3-migration), Full details

**\"Do I need to do anything?\"**
- [Migration Summary](/docs/staking-rewards/migration-summary), Answer: No

**\"How do I stake?\"**
- [How Staking Works](/docs/staking-rewards/how-staking-works), Step-by-step guide

**\"How are rewards funded?\"**
- [Reward Funding](/docs/staking-rewards/reward-funding), Detailed explanation

**\"What was the root cause?\"**
- [V2 to V3 Migration](/docs/staking-rewards/v2-to-v3-migration), Root cause analysis

**\"Is this a security issue?\"**
- [V2 to V3 Migration](/docs/staking-rewards/v2-to-v3-migration), Impact assessment

## Key Points

### The Issue

- Discovered during pre-mainnet validation
- Reward accounting diverged from actual balance
- No users affected
- No funds lost

### The Solution

- V3 provides unified accounting
- Includes balance verification
- Stronger invariant enforcement
- Production-grade reliability

### User Impact

- No action required
- Staking fully operational
- Rewards unchanged
- No migration needed

## Related Documentation

### Staking & Rewards

- [How Staking Works](/docs/staking-rewards/how-staking-works)
- [Reward Funding](/docs/staking-rewards/reward-funding)
- [Reward Distribution Logic](/docs/staking-rewards/reward-distribution-logic)
- [User Flows](/docs/staking-rewards/user-flows)
- [Risks & Notes](/docs/staking-rewards/risks-notes)

### Protocol Architecture

- [Staking Contract](/docs/protocol-architecture/staking)
- [Protocol Router](/docs/protocol-architecture/protocol-router)
- [Treasury](/docs/protocol-architecture/treasury)

### Governance & Operations

- [Upgrade & Migration Philosophy](/docs/governance-operations/upgrade-migration-philosophy)
- [Multisig Responsibilities](/docs/governance-operations/multisig-responsibilities)
- [Proposal Flow](/docs/governance-operations/proposal-flow)

### Security

- [Security Model Overview](/docs/security-model/overview)
- [Access Control](/docs/security-model/access-control)
- [Treasury Protection](/docs/security-model/treasury-protection)

## FAQ

**Q: Where should I start?**  
A: Start with [Migration Summary](/docs/staking-rewards/migration-summary) for a quick overview.

**Q: Do I need to migrate anything?**  
A: No. No user action is required.

**Q: Will my rewards change?**  
A: No. Reward mechanisms remain the same.

**Q: Is this a security issue?**  
A: The issue was discovered before public launch and resolved proactively.

**Q: Where's the full technical details?**  
A: See [V2 to V3 Migration](/docs/staking-rewards/v2-to-v3-migration).

**Q: What's the official changelog?**  
A: See [Changelog: V2 to V3](/docs/staking-rewards/changelog-v2-v3).

## Support

For questions about the migration:

1. Check the relevant documentation above
2. Review the FAQ section
3. Contact the protocol team through official channels

---

**Last Updated:** Mainnet Launch  
**Status:** Complete  
**User Impact:** None
