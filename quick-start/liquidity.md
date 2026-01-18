---
cover: ../.gitbook/assets/QuickStart.png
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

# Add Liquidity

Learn how to provide liquidity on Alphix, choose a strategy, and manage your positions.

{% stepper %}
{% step %}
**Select Pool**

Choose which pool to provide liquidity for. Each pool displays its current APR, combining swap fees and lending yield.
{% endstep %}

{% step %}
**Choose Strategy**

We propose users select **Unified Yield** to LP into Unified Pools. Your liquidity earns swap fees while idle capital is automatically deployed to lending markets for additional yield. In stable pools, positions are inherently concentrated. In standard pools, positions use full range.

{% hint style="info" %}
**Custom Range** is available for sophisticated users who want concentrated positions with user-defined price ranges. This increases Impermanent Loss exposure and management overhead.
{% endhint %}
{% endstep %}

{% step %}
**Enter Deposit Amounts**

Input how much of each token to deposit. The interface shows your wallet balance and auto-fills the corresponding token amount.

{% hint style="info" %}
Single-token deposits are coming soon.
{% endhint %}
{% endstep %}

{% step %}
**Review and Create**

Review your position details, approve the tokens, and create your position. Once confirmed, you'll start earning immediately.
{% endstep %}
{% endstepper %}

***

### Managing Positions

Once created, manage your positions from the Pool page or your Portfolio.

**Claim Fees**

Accumulated fees can be claimed at any time without modifying your position.

**Increase Liquidity**

Add more capital to an existing position. Unclaimed fees are automatically compounded.

**Withdraw Liquidity**

Remove part or all of your position. Accrued fees are claimed automatically with the withdrawal.

***

### Liquidity Provisioning Risks

{% hint style="danger" %}
Providing liquidity carries risks that users should understand before committing capital.
{% endhint %}

**Impermanent Loss (IL)**

When providing liquidity, your assets are exposed to price changes between the two tokens. If prices diverge significantly, your position value may be lower than simply holding the tokens.

* IL is minimized when tokens are correlated (stablecoins)
* Narrow ranges increase fee income but also IL exposure
* If price moves outside your range, the position stops earning and holds only the devaluing token

Read more about [Impermanent Loss](https://blog.ston.fi/impermanent-loss-explained-a-guide-for-defi-liquidity-providers/).

**Smart Contract Risk**

Smart contracts carry inherent risk. We strongly encourage LPs to do their own research. Alphix is built on top of well-established protocols like Uniswap V4 and follows official standards. Core contracts have been audited by reputable third-party firms.
