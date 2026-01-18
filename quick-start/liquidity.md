---
description: >-
  Learn how to provide liquidity on Alphix, choose a strategy, and manage your positions.
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

### User Guide

This guide walks through creating a liquidity position on Alphix. To get started, navigate to [alphix.fi/liquidity/add](https://alphix.fi/liquidity/add).

{% stepper %}
{% step %}
**Select Pool**

![](../.gitbook/assets/Select.jpg)

Choose which pool to provide liquidity for. Each pool displays its current APR, combining swap fees and lending yield.
{% endstep %}

{% step %}
**Choose Strategy**

![](../.gitbook/assets/Select.jpg)

We propose users select **Unified Yield** to LP into Unified Pools.

> Your liquidity earns swap fees while idle capital is deployed to lending markets. Stable pools use concentrated positions. Standard pools use full range.

{% hint style="info" %}
**Custom Range** is for advanced users who want manual price ranges.
{% endhint %}
{% endstep %}

{% step %}
**Enter Deposit Amounts**

![](../.gitbook/assets/Select.jpg)

Input how much of each token to deposit. The interface shows your wallet balance and auto-fills the corresponding token amount.

{% hint style="success" %}
Single-token deposits are coming soon.
{% endhint %}
{% endstep %}

{% step %}
**Review and Create**

![](../.gitbook/assets/Select.jpg)

Review your position details, approve the tokens, and create your position. Once confirmed, you'll start earning immediately.
{% endstep %}
{% endstepper %}

***

### Managing Positions

Once created, manage positions from the Pool page or your Portfolio. Claim fees anytime, add more capital, or withdraw — accrued fees are claimed automatically.

***

### Liquidity Provisioning Risks

{% hint style="warning" %}
Providing liquidity carries risks that users should understand before committing capital.
{% endhint %}

<details>

<summary><mark style="color:$info;">Impermanent Loss (IL)</mark></summary>

When providing liquidity, your assets are exposed to price changes between the two tokens. If prices diverge significantly, your position value may be lower than simply holding the tokens.

* IL is minimized when tokens are correlated (stablecoins)
* Narrow ranges increase fee income but also IL exposure
* If price moves outside your range, the position stops earning and holds only the devaluing token

Read more about [Impermanent Loss](https://blog.ston.fi/impermanent-loss-explained-a-guide-for-defi-liquidity-providers/).

</details>

<details>

<summary><mark style="color:$info;">Smart Contract Risk</mark></summary>

Smart contracts carry inherent risk. We strongly encourage LPs to do their own research. Alphix is built on top of well-established protocols like Uniswap V4 and follows official standards. Core contracts have been audited by reputable third-party firms.

</details>
