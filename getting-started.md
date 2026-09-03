---
cover: .gitbook/assets/covers/getting-started-v3.png
coverY: 0
---

# Getting started

Dust runs on Robinhood Chain. Connecting takes about a minute, and there are two paths in depending on how far you want automation to go.

## Connect and start

1. Open the app and connect an EVM wallet. MetaMask works, and so does any wallet that can add a custom network. The app offers to add Robinhood Chain for you.
2. Build your basket: pick which Stock Tokens your spare change buys, and their weights. The launch menu is TSLA, NVDA, AAPL, AMZN, and SPY. You can change your basket any time.
3. Fund with USDG (and keep a little ETH for network fees). Trade the way you already do.

From your first round-up onward, you'll see the vault balance move. Most people check it obsessively for two days and then forget about it, which is exactly the point.

Round-ups on swaps you make inside Dust need nothing more than that: you sign each one, and the change lands in your vault. If you'd rather have it happen everywhere, read on.

## Capture Everywhere

This is the part that makes Dust feel like Acorns: round up your swaps and payments made anywhere on Robinhood Chain, not just in the app. You set a weekly cap, the keeper collects the change under it, and nothing above that cap can ever be pulled. Three ways to fund it:

- **From USDG.** You keep a little USDG and grant the Capture contract a standard token allowance on it. When the keeper spots an outside transaction, it pulls the round-up from your USDG, up to your cap, straight into your vault. Simplest path, live today.
- **From WETH.** For people who mostly hold ETH. You grant an allowance on your wrapped ETH, and the Capture contract swaps exactly the round-up's worth into USDG on one fixed pool, refusing any price worse than the pool's recent average plus a small margin. Built and deploying (status: deploying).
- **From an ETH float.** You park a small amount of plain ETH in the Capture contract. It stays credited to you and you can take it back out at any time, in every state. The keeper draws round-ups from it under the same price guard. Built and deploying (status: deploying).

The weekly cap applies across all three together. All are opt-in, all are capped onchain, and all are revocable from your wallet as well as from our app. Setting your cap to zero is a full opt-out.

On Solana the same feature is funded from USDC through a token delegate, or from SOL through a Squads smart account. [Also on Solana](solana.md) covers it.

## Your first five minutes, honestly

A realistic first session: you connect MetaMask, build a five-stock basket, fund with $200 of USDG, and make a swap for $61.30. Your vault now holds about $0.70 of the basket, which at today's prices is a sliver of a share of a few large companies. It will look like a rounding error, because it is one. The product only makes sense over months. If you want the vault to grow faster, raise the multiplier.

## What Dust does not ask you for

No bank account. No card. No personal trading history. We do not take deposits to hold. Your funds stay in your own wallet, and the contracts only ever move the round-up amounts you authorized. If any product claiming to be Dust asks you to send funds to an address to "activate" round-ups, it is a scam. The only official links are listed in these docs. Lookalike tokens exist on every chain, and Robinhood Chain is no exception: a token with the right name and the wrong address is not a Stock Token. Your basket only ever holds the Stock Token contracts Dust has listed onchain, covered on the [basket page](the-basket.md).
