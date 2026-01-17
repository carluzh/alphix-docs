---
hidden: true
cover: ../.gitbook/assets/Basi.png
coverY: 0
layout:
  width: default
  cover:
    visible: true
    size: hero
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
---

# Alphix Philosophy

## Hook-First Architecture

Alphix is built as a **Uniswap V4 Hook contract** rather than a standalone Automated Market Maker (AMM). This approach creates a flexible layer where new features and market mechanisms can be added without deploying new pools or fragmenting liquidity.

## Permissionless & Composable

Alphix is fully compatible with existing Uniswap V4 SDKs, Subgraphs, and tooling. Developers can integrate Alphix Hooks, pools and fee data into decentralized applications (dApps) or analytics dashboards with minimal effort. \
\
In addition, all Alphix smart contracts are decentralized, transparent and permissionless, making them easy to combine with other DeFi protocols, strategies, or aggregators.

## Unified Liquidity

On Alphix, each token pair exists in a **single pool**. The Alphix Hook is designed to be flexible and customizable. This makes it simple to introduce new functionality while preserving the same core liquidity.

Because every feature runs within a single hook framework, liquidity stays deep and consolidated. Traders benefit from deeper liquidity and better pricing, while LPs no longer need to split their funds across multiple fee tiers.

## **Security-Focused**

Alphix builds on top of **well-established, lindy** protocols like Uniswap V4 and follows **battle-tested** standards (e.g. OpenZeppelin). It integrates proven features and adds built-in safety checks. A clear audit roadmap further ensures that Alphix operates in a secure environment for LPs, traders, and integrators.
