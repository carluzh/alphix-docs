---
description: >-
  An overview of the core products that make Unified Pools powerful.
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

# Key Features

### Dynamic Fees

Dynamic Fees are a direct improvement on the fee-tier system seen across leading DEXs. They improve the experience for LPs who no longer need to choose and rebalance between fee tiers to optimize yield and allow for more context-rich trade execution.

Several protocols have already begun experimenting with dynamic fee models. However, leading implementations base their approach on external volatility data. While this compensates for Impermanent Loss and improves the risk-reward profile for LPs, it does so at the cost of pool competitiveness. Additionally, they rely on oracles, which introduce attack vectors such as data manipulation or latency exploits.

Alphix takes a fundamentally different approach. By leveraging pool internal data and an in-house designed and tested algorithm, we achieve fair fee pricing that follows the market demand while positioning the pool as a competitive option across all market environments.

{% content-ref url="../products/dynamic-fee.md" %}
[dynamic-fee.md](../products/dynamic-fee.md)
{% endcontent-ref %}

### Unified Yield

Unified Yield deploys idle liquidity into lending markets, generating additional returns beyond trading fees. The result is a dual income stream for LPs without fragmenting the Unified Pool structure. Slippage is not negatively influenced as liquidity is recalled instantly via JIT (Just-In-Time) accounting when swaps occur. <mark style="color:$info;">More yield. Same Execution.</mark>

This creates a yield floor for liquidity providers. Even during periods of low trading activity, positions continue earning lending yield. LPs no longer face the opportunity cost of idle capital as liquidity in Unified Pools is always productive.

{% content-ref url="../products/unified-yield.md" %}
[unified-yield.md](../products/unified-yield.md)
{% endcontent-ref %}

***

### Additional Features

Alphix’s modular hook framework enables a set of potential innovations.

<table data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-cover data-type="image">Cover image</th></tr></thead><tbody><tr><td><strong>Liquidity Rebalancing</strong></td><td>Automated adjustments to maintain optimal pool ratios</td><td><a href="../.gitbook/assets/Rebalance.png">Rebalance.png</a></td></tr><tr><td><strong>Internalizing MEV</strong></td><td>Frontrunning Protection using privatized order flow</td><td><a href="../.gitbook/assets/Sandwich.png">Sandwich.png</a></td></tr><tr><td><strong>Artificial Intelligence</strong></td><td>For advanced liquidity management and yield optimization</td><td><a href="../.gitbook/assets/AI.png">AI.png</a></td></tr></tbody></table>

By focusing on market-relevant, battle-tested features, Alphix ensures that every innovation enhances the LP and trader experience while maintaining deep liquidity and composability. The Alphix Hook will evolve with market trends and protocol needs.



