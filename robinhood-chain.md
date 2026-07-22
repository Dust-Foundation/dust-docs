---
cover: .gitbook/assets/covers/robinhood-chain.png
coverY: 0
---

# Why Robinhood Chain

Dust could not have been built a year ago, and even today it can only be built in one place. This page explains the choice.

A round-up product needs four things on the same chain: real blue-chip assets worth accumulating, a liquid market to buy them on, a stable dollar to denominate round-ups in, and the freedom for a third-party team to deploy contracts without anyone's permission. Plenty of chains have three of the four. Robinhood Chain, which went live on public mainnet on July 1, 2026, is the first with all of them.

The specifics, for those who want them:

| | |
|---|---|
| What it is | An Ethereum Layer 2 built on Arbitrum's chain stack, settling to Ethereum |
| Chain ID | 4663 (testnet 46630) |
| Gas | ETH, with roughly 100ms block times |
| The assets | Robinhood Stock Tokens: tokenized blue-chip stocks, self-custodied, trading 24/7 |
| The market | A dedicated Uniswap deployment, with Stock Token pairs against USDG |
| The dollar | USDG, a Paxos-issued stablecoin |
| Deployment | Permissionless. Anyone can deploy contracts, including us |

The chain also ships with native account abstraction (ERC-4337), which is the wallet technology Dust's permission model runs on. That's not a nice-to-have; it's the load-bearing primitive. On chains where smart accounts are an afterthought, the "one narrow revocable permission" design gets much harder to do well.

## The caveats

Transactions are ordered by a single sequencer operated by Robinhood, which is normal for young L2s but worth naming: censorship resistance today depends on the chain's escape-hatch mechanisms to Ethereum, not on decentralized ordering. Every token transfer on the chain is screened by Chainalysis, so the environment is compliant by construction, which cuts both ways depending on your politics. And the chain is weeks old: liquidity is early, tooling is early, and adoption numbers are not yet public. We think being early to the first chain with native stocks is the right bet for this product, and we'd rather say "it's early" plainly than discover you assumed otherwise.

## If Robinhood Chain isn't where you are

Stock Token availability follows the issuer's country list (120+ countries, excluding the US and a few others). Longer term, the same Dust design works anywhere tokenized equities and programmable wallets coexist, and several other issuers run on other chains. Multi-chain is a roadmap item, not a promise with a date. We would rather get one chain right first.
