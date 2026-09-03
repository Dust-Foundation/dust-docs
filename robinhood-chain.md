---
cover: .gitbook/assets/covers/robinhood-chain-v3.png
coverY: 0
---

# Why Robinhood Chain

Dust could not have been built a year ago, and it was built here first for a reason. This page explains the choice.

A round-up product needs four things on the same chain: real blue-chip assets worth accumulating, a liquid market to buy them on, a stable dollar to denominate round-ups in, and the freedom for a third-party team to deploy contracts without anyone's permission. Plenty of chains have three of the four. Robinhood Chain, which went live on public mainnet on July 1, 2026, was the first with all of them, and it is where Dust lives.

The specifics, for those who want them:

| | |
|---|---|
| What it is | An Ethereum Layer 2 built on Arbitrum's Orbit stack, settling to Ethereum |
| Chain ID | 4663 (testnet 46630) |
| Gas | ETH, with roughly 100ms block times and fees of a fraction of a cent |
| The assets | Stock Tokens: blue-chip US stocks and ETFs as tokens, self-custodied, trading 24/7 |
| The market | Canonical Uniswap v3 pools, each Stock Token paired with USDG |
| The dollar | USDG (Global Dollar), issued by Paxos, six decimals |
| Wallets | MetaMask or any EVM wallet |
| Deployment | Permissionless. Anyone can deploy contracts, including us |

## Why it fits

**The assets are native here.** Stock Tokens are issued on this chain, not bridged onto it. The tokens Dust buys are the issuer's own contracts, and the pools they trade in are the deepest ones that exist for them.

**The dollar is a real dollar.** USDG is a regulated stablecoin, and every Stock Token has a USDG pool. That means round-ups can be denominated, accrued, and invested in the same dollar without a conversion hop, and what you see in your vault is what the chain holds.

**Transactions are cheap and fast.** A round-up is a tiny transaction, and a product made of tiny transactions dies on a chain where each one costs a dollar. Here a sweep of a five-stock basket costs a fraction of a cent in ETH and confirms in well under a second, which is what lets Dust invest change instead of eating it.

**Trading and investing live in one place.** The people this product is for already trade here. The change from a swap on Robinhood Chain can become a Stock Token on Robinhood Chain in the same ecosystem, with no bridge and no second wallet.

The chain also supports account abstraction, which is the path we plan to use for embedded wallets and scoped session keys later. Today Dust works with plain wallets and standard token allowances, so nothing about the product depends on it yet.

## The caveats

Transactions are ordered by a single sequencer operated by Robinhood, which is normal for young L2s but worth naming: censorship resistance today depends on the chain's escape-hatch mechanisms to Ethereum, not on decentralized ordering. Token transfers on the chain are screened for compliance, so the environment is compliant by construction, which cuts both ways depending on your politics. Stock Tokens can be paused and addresses blocked by their issuer, and Dust cannot override that; the [basket page](the-basket.md) covers what Dust does about it. And the chain is young: liquidity is early, tooling is early, and adoption numbers are not yet public. We think being early to the first chain with native stocks is the right bet for this product, and we'd rather say "it's early" plainly than discover you assumed otherwise.

## If Robinhood Chain isn't where you are

Stock Token availability follows the issuer's country list (120+ countries, excluding the US and a few others). Dust is also deployed on Solana, where the assets are xStocks and the dollar is USDC. [Also on Solana](solana.md) explains what is the same and what differs.
