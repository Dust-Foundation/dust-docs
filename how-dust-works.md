---
cover: .gitbook/assets/covers/how-dust-works.png
coverY: 0
---

# How Dust works

The easiest way to understand Dust is to follow one swap all the way through.

## One swap, start to finish

Say you have round-ups turned on and you buy a token with 137.42 USDG (the dollar stablecoin on Robinhood Chain).

1. You confirm the swap in Dust like on any exchange.
2. Dust routes it through the DustRouter contract, which executes your swap and, in the same transaction, rounds your spend up to 140.00. The 2.58 USDG difference is your round-up.
3. The round-up goes to the DustSweeper contract, which buys your basket: small slices of tokenized blue-chip stocks, purchased at their current market price on the chain's Uniswap markets.
4. The stock tokens land in your position in the DustVault, next to every round-up that came before.

You wanted the token; you got the token. You also, almost invisibly, bought $2.58 of the stock market. Do that across a normal month of trading and the vault line starts to look like something.

Because the swap and the round-up happen in one atomic transaction, there is no gap where the change sits somewhere waiting to be invested, and nothing extra for you to sign.

## The pieces, in plain terms

**DustRouter** is the front door. It takes your swap, executes it, and captures the round-up atomically. If any part fails, the whole transaction fails and nothing moves. There is no state where your swap succeeded but your change went missing.

**DustSweeper** is the only contract with permission to spend your round-ups, and the permission you grant it is narrow by construction: it can move USDG only, only into basket purchases for your own vault position, and only up to the per-period cap you chose. It cannot touch your other tokens. It cannot send funds anywhere else. You can revoke it in one tap.

**DustVault** is your ledger. It tracks your basket shares, your cost basis, and your history. The assets in it are yours; the vault has no lockups, and you can withdraw at any time, either as the stock tokens themselves or converted back to USDG.

**The basket** is a fixed, published list of tokenized blue-chip stocks with fixed weights. Nobody at Dust picks stocks for you day to day. The rules for changing the basket composition are deliberate and slow (announced in advance and delayed by a timelock), which is covered in [The basket](the-basket.md).

## What "rounding up" means when there's no cash register

A card purchase has an obvious round-up: $4.60 coffee, 40 cents of change. An onchain swap doesn't, so Dust defines it: we round the stablecoin side of your swap up to the next whole dollar and sweep the difference. Spend 137.42, invest 0.58? No: spend 137.42, and 2.58 gets swept because you set your round-up to the next 5. You choose the granularity: nearest 1, nearest 5, or a multiplier (2x or 10x your change) if you want the background investing to run hotter. Swaps that don't touch the stablecoin are skipped in v1; pricing them fairly via oracles is on the roadmap.

## Where the automation comes from

Inside the Dust app, the router handles everything and no automation is needed. The more interesting case is swaps you make elsewhere. If your account is a Dust smart account (or a wallet that supports modern permission standards, like recent MetaMask versions), you can grant the one-time permission described above, and Dust's sweeper will collect and invest your round-ups from activity across the chain, on a schedule, without you doing anything. How that permission works, exactly what it can and cannot do, and how to revoke it are covered in [Wallets and custody](wallets-and-custody.md).
