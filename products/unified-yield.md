---
cover: ../.gitbook/assets/Unified-Yield-Banner.png
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

# Unified Yield

Traditional liquidity provision has a fundamental inefficiency: LP funds sit idle in the pool waiting for swaps. In a typical 24-hour period, deposited capital might only be actively used for a fraction of the time. The rest of the time, it earns nothing.

Unified Yield solves this by deploying idle liquidity to Aave, allowing LPs to earn lending yield continuously while remaining fully available for swaps through Just-In-Time (JIT) accounting.

The result is a dual-yield position. LPs earn swap fees from trading activity AND lending yield from Aave — simultaneously, from the same capital.

{% hint style="info" %}
Unified Yield positions use ERC-4626 vault shares, a tokenized representation of your deposit that automatically accrues yield.
{% endhint %}

***

### How It Works

At the core of Unified Yield sits the JIT (Just-In-Time) liquidity mechanism. Here's what happens:

{% hint style="warning" %}
The explanation below is simplified to convey the underlying logic. The production implementation includes additional safeguards.
{% endhint %}

{% stepper %}
{% step %}
#### Deposit

When you provide liquidity, your tokens are deposited into the Hook contract. The Hook immediately routes these tokens to underlying Aave vaults, where they begin earning lending yield.

You receive ERC-4626 shares representing your position. These shares automatically appreciate as yield accrues.
{% endstep %}

{% step %}
#### During Swaps (JIT)

When a swap occurs, the Hook uses flash accounting to make your liquidity virtually present in the pool:

1. **beforeSwap**: Liquidity is flash-added to the pool
2. **Swap executes**: Against full available liquidity
3. **afterSwap**: Net amounts settle — tokens received go to Aave, tokens sent come from Aave

Your capital earns the swap fee while never actually leaving the yield-generating position.
{% endstep %}

{% step %}
#### Withdraw

When you withdraw, the Hook burns your shares, retrieves the underlying tokens from Aave (including all accrued yield), and sends them to your wallet.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
The liquidity is only "in the pool" at the exact moment of the swap. No capital sits idle.
{% endhint %}

### Position Characteristics

Unified Yield positions differ from standard concentrated liquidity positions in several ways:

<table data-view="cards"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Full Range</strong></td><td>Positions cover all prices. No range management required — you're always in range.</td></tr><tr><td><strong>Vault Shares</strong></td><td>You receive ERC-4626 shares instead of an NFT. Shares are fungible and automatically accrue yield.</td></tr><tr><td><strong>Dual Yield</strong></td><td>Earn from two sources: swap fees from trading activity and lending yield from Aave.</td></tr></tbody></table>

<details>

<summary><mark style="color:$info;">APR Breakdown</mark></summary>

Unified Yield positions display a combined APR from multiple sources:

| Component | Source | Typical Range |
| --------- | ------ | ------------- |
| Swap APR | Trading fees from swaps | 5-15% |
| Unified Yield APR | Average Aave lending rate for both tokens | 3-8% |
| Points Bonus | 50% multiplier on Swap APR during Points campaign | Variable |

The total APR shown is the sum of all components. Actual returns vary based on pool volume, Aave rates, and market conditions.

{% hint style="info" %}
Unified Yield APR is calculated as the average of both tokens' Aave lending rates.
{% endhint %}

</details>

<details>

<summary><mark style="color:$info;">Supported Assets</mark></summary>

Unified Yield works with assets that have liquid Aave markets. Currently supported:

* **ETH** — Via Aave's aWETH
* **USDC** — Via Aave's aUSDC
* **USDS** — Via Aave's aUSDS

Each pool's Hook deposits into the corresponding Aave vaults for its token pair.

</details>

### Why it Matters

**Liquidity Providers**

**Traditional LPs face idle capital.** Funds deposited into a pool only earn when swaps occur. Between trades, capital generates zero return. This inefficiency compounds over time, especially in lower-volume pools.

**Alphix it.** Unified Yield ensures your capital is always working. When not used for swaps, it earns lending yield on Aave. When swaps occur, JIT accounting captures the fees. <mark style="color:$info;">No idle capital. Dual yield streams.</mark>

{% hint style="success" %}
Earn swap fees AND lending yield. Capital never sits idle.
{% endhint %}

**Traders**

**Traders need deep liquidity.** Shallow pools mean higher slippage. Traditional yield farming often pulls liquidity away from DEXs into lending protocols, fragmenting available depth.

**Alphix it.** Unified Yield keeps liquidity in the pool while earning external yield. LPs have no reason to withdraw for better rates elsewhere. This concentrates liquidity and improves execution for traders.

{% hint style="success" %}
Deeper liquidity. Better execution.
{% endhint %}

**Protocols**

**Protocols struggle with LP retention.** Liquidity providers constantly seek the highest yield, leading to mercenary capital that moves at any rate differential. Incentive programs become expensive arms races.

**Alphix it.** Unified Yield makes Alphix pools inherently more attractive by offering dual yield. Protocols building on Alphix benefit from stickier liquidity without additional incentive spend.

{% hint style="success" %}
Stickier liquidity. Lower incentive costs.
{% endhint %}
