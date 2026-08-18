---
cover: .gitbook/assets/covers/how-dust-works-v3.png
coverY: 0
---

# How Dust works

The easiest way to understand Dust is to follow one swap all the way through.

## One swap, start to finish

Say you have round-ups turned on and you buy a token for $137.42 worth of USDC (the dollar stablecoin Dust uses on Solana).

1. You make the swap. It can happen right inside Dust, or anywhere else on Solana: a Jupiter route, a swap in Phantom, any DEX.
2. Dust figures the round-up. Your $137.42 rounds up to $140.00, so your change is $2.58.
3. That $2.58 lands in your vault as banked round-ups, waiting to be invested. Your money, still fully yours, sitting in a vault account you can withdraw from at any time.
4. On its next pass, Dust's keeper invests the banked change: it swaps your USDC for your chosen stocks through Jupiter, and the stock tokens land in your vault position next to every round-up that came before.

You wanted the token; you got the token. You also, almost invisibly, bought $2.58 of the stock market. Do that across a normal month of trading and the vault line starts to look like something.

## What actually enforces the rules

Everything runs through a single onchain program on Solana. It is the only thing that can move your banked round-ups, and what it is allowed to do is fixed in its code, not in our promises.

**Banking the round-up.** When change is banked, your USDC moves into a vault account the program controls, credited to you. You sign it, or (for capture-everywhere) a capped permission you granted does. Either way the amount is exactly your round-up and nothing more.

**Investing it.** The keeper is the off-chain worker that does the swaps, but it holds no discretion. For each stock in your basket it asks Jupiter for a live quote, and the program refuses to record the purchase unless your vault actually received at least what that quote promised, minus a small slippage tolerance. The whole leg is one atomic transaction. A keeper that tried to hand you a bad fill, or route the money somewhere else, would simply make the transaction fail. The quote is the price guard, and the chain is the enforcer.

**Holding it.** Your basket lives in your vault position, tracked per stock, with your cost basis and history. The program holds nothing of its own between investments. You can withdraw the stock tokens themselves, or the banked USDC, at any time. Withdrawals cannot be paused, gated, or blocked by anyone, including us.

## What "rounding up" means when there's no cash register

A card purchase has an obvious round-up: $4.60 coffee, 40 cents of change. An onchain swap doesn't, so Dust defines it. A round-up is always measured in dollars: we take the dollar value of your swap and round it up to the next whole dollar. You choose the granularity, nearest 1 or nearest 5, or a multiplier if you want the background investing to run hotter.

You can fund the round-up from either USDC or SOL. Pay from USDC and it moves straight to your vault. Pay from SOL and the app swaps exactly the round-up's worth of SOL into USDC in the same transaction you sign, then banks it. A nice side effect of that: the change you bank stops moving with the price of SOL the moment it lands, so a round-up is worth what it was worth when you made it.

## Where the automation comes from

Inside the Dust app, you sign your own round-ups and nothing else is needed. The more interesting case is swaps you make everywhere else. Turn on capture-everywhere and grant one capped, revocable permission, and Dust's keeper rounds up your outside trades too, on its own schedule, without you lifting a finger. Exactly what that permission can and cannot do, and how to fund it from USDC or SOL, is covered in [Wallets and custody](wallets-and-custody.md).
