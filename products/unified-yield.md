---
cover: ../.gitbook/assets/UY.jpg
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

Unified Yield solves this by routing idle liquidity into yield-generating vaults, allowing LPs to earn lending yield continuously while remaining fully available for swaps through Just-In-Time (JIT) accounting.

The result is a dual-yield position. LPs earn swap fees from trading activity AND lending yield from the underlying vaults, simultaneously, from the same capital.

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

When you provide liquidity, your tokens are deposited into the Hook contract. The Hook immediately routes these tokens to underlying yield vaults based on the asset's yield strategy, where they begin earning lending yield.

You receive ERC-4626 shares representing your position. These shares automatically appreciate as yield accrues.
{% endstep %}

{% step %}
#### During Swaps (JIT)

When a swap occurs, the Hook uses flash accounting to make your liquidity virtually present in the pool:

1. **beforeSwap**: Liquidity is flash-added to the pool
2. **Swap executes**: Against full available liquidity
3. **afterSwap**: Net amounts settle. Tokens received go to the vault, tokens sent come from the vault

Your capital earns the swap fee while never actually leaving the yield-generating position.
{% endstep %}

{% step %}
#### Withdraw

When you withdraw, the Hook burns your shares, retrieves the underlying tokens from the vault (including all accrued yield), and sends them to your wallet.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
The liquidity is only "in the pool" at the exact moment of the swap. No capital sits idle.
{% endhint %}

### Position Characteristics

Unified Yield positions differ from standard concentrated liquidity positions in several ways:

<table data-view="cards"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Simplified Ranges</strong></td><td>Standard pools use full range. Stable pools use concentrated positions. No manual range management required.</td></tr><tr><td><strong>Vault Shares</strong></td><td>You receive ERC-4626 shares instead of an NFT. Shares are fungible and automatically accrue yield.</td></tr><tr><td><strong>Dual Yield</strong></td><td>Earn from two sources: swap fees from trading activity and lending yield from the underlying vaults.</td></tr></tbody></table>

<details>

<summary><mark style="color:$info;">APR Breakdown</mark></summary>

Unified Yield positions display a combined APR from multiple sources:

| Component | Source |
| --------- | ------ |
| Swap APR | Trading fees from swaps |
| Unified Yield APR | Average lending rate across both tokens' vaults |

The total APR shown is the sum of all components. Actual returns vary based on pool volume, vault rates, and market conditions.

</details>

<details>

<summary><mark style="color:$info;">Supported Assets</mark></summary>

Unified Yield works with assets that have compatible yield vaults. Each asset is routed to a vault based on its yield strategy.

<table data-view="cards"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>ETH</strong></td><td>Wrapped ETH lending vault</td></tr><tr><td><strong>USDC</strong></td><td>USDC lending vault</td></tr><tr><td><strong>USDS</strong></td><td>USDS lending vault</td></tr></tbody></table>

</details>

### Why it Matters

**Liquidity Providers**

**Traditional LPs face idle capital.** Funds deposited into a pool only earn when swaps occur. Between trades, capital generates zero return. This inefficiency compounds over time, especially in lower-volume pools.

**Alphix it.** Unified Yield ensures your capital is always working. When not used for swaps, it earns lending yield in underlying vaults. When swaps occur, JIT accounting captures the fees. <mark style="color:$info;">No idle capital. Dual yield streams.</mark>

{% hint style="success" %}
Earn swap fees AND lending yield. Capital never sits idle.
{% endhint %}

**Traders**

**Traders need deep liquidity.** Shallow pools mean higher slippage. LPs constantly moving capital between protocols fragments available depth.

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
