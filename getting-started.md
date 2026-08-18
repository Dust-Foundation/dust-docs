---
cover: .gitbook/assets/covers/getting-started-v2.png
coverY: 0
---

# Getting started

Dust runs on Solana. Connecting takes about a minute, and there are two paths in depending on how far you want automation to go.

## Connect and start

1. Open the app and connect a Solana wallet. Phantom and Solflare both work, and most other wallets show up automatically.
2. Build your basket: pick which stocks your spare change buys, and their weights. You can change it any time.
3. Fund with USDC (and keep a little SOL for network fees). Trade the way you already do.

From your first round-up onward, you'll see the vault balance move. Most people check it obsessively for two days and then forget about it, which is exactly the point.

Round-ups on swaps you make inside Dust need nothing more than that: you sign each one, and the change is banked. If you'd rather have it happen everywhere, read on.

## Capture everywhere

This is the part that makes Dust feel like Acorns: round up your swaps and payments made anywhere on Solana, not just in the app. You grant a capped, revocable allowance the keeper uses to collect the change, and nothing above the weekly cap you set can ever be pulled. Two ways to fund it:

- **From USDC.** You keep a little USDC, and you grant Dust a standard SPL delegate on that balance. When the keeper spots an outside swap, it pulls the round-up from your USDC, up to your cap. Simplest path, works today.
- **From SOL.** For people who mostly hold SOL. Your SOL lives in a Squads smart account you own, and you give the keeper an onchain spending limit: so much SOL per week, to one place, revocable whenever. The keeper pulls the round-up in SOL and converts it. The [custody page](wallets-and-custody.md) covers both in detail.

Both are opt-in, both are capped onchain, and both are revocable from your wallet as well as from our app.

## Your first five minutes, honestly

A realistic first session: you connect Phantom, build a five-stock basket, fund with $200 of USDC, and make a swap for $61.30. Your vault now holds about $0.70 of the basket, which at today's prices is a sliver of a share of a few large companies. It will look like a rounding error, because it is one. The product only makes sense over months. If you want the vault to grow faster, raise the multiplier.

## What Dust does not ask you for

No bank account. No card. No personal trading history. We do not take deposits to hold. Your funds stay in your own wallet, and the program only ever moves the round-up amounts you authorized. If any product claiming to be Dust asks you to send funds to an address to "activate" round-ups, it is a scam. The only official links are listed in these docs. Solana has a particular hazard worth naming: copycat tokens with names ending in "pump" or lookalike tickers. Your basket only ever holds the verified xStocks the app lists onchain, covered on the [basket page](the-basket.md).
