---
cover: .gitbook/assets/covers/how-dust-works-v3.png
coverY: 0
---

# How Dust works

The easiest way to understand Dust is to follow one swap all the way through.

## One swap, start to finish

Say you have round-ups turned on and you buy a token for $137.42 worth of USDG (the dollar stablecoin on Robinhood Chain).

1. You make the swap. It can happen right inside Dust, or, with Capture Everywhere turned on, anywhere else on Robinhood Chain: a Uniswap trade, a transfer, a payment.
2. Dust figures the round-up. Your $137.42 rounds up to $140.00, so your change is $2.58.
3. That $2.58 lands in your vault as accrued round-ups, waiting to be invested. Your money, still fully yours, sitting in a contract balance you can withdraw from at any time.
4. On its next pass, Dust's keeper sweeps the accrued change: it buys each Stock Token in your basket from its Uniswap v3 pool against USDG, at your weights, and the Stock Tokens land in your vault position next to every round-up that came before.

You wanted the token; you got the token. You also, almost invisibly, bought $2.58 of the stock market. Do that across a normal month of trading and the vault line starts to look like something.

## What actually enforces the rules

Dust on Robinhood Chain is four small contracts, and what each one is allowed to do is fixed in its code, not in our promises.

**The router (in-app swaps).** DustRouter does your swap and takes the round-up in the same transaction. It holds nothing between transactions and has no admin functions at all. The round-up is exactly your change times your multiplier, and it goes straight to your vault position.

**The vault (your ledger).** DustVault holds your accrued USDG and the Stock Tokens bought with it, as a balance in your name. It has no pause and no owner power over balances. Only the router can add accrued change, only the sweeper can spend it, and only you can withdraw. Withdrawals of accrued USDG always work, in every state the protocol can be in.

**The sweeper (investing).** DustSweeper buys your own basket, from a menu of Stock Tokens Dust has listed onchain, at the weights you set. The keeper is the off-chain worker that triggers it, but it holds no discretion. Before each sweep it quotes every leg from the live pool and passes the contract a minimum it must receive. If a pool returns less, the leg fails. If a Stock Token has been paused by its issuer or its pool is thin, that leg is skipped and its USDG goes back to your accrued balance, untouched. Same accrued amount, same basket, same buys, every time. The quote is the price guard, and the chain is the enforcer.

**Capture (outside activity).** DustCapture is the only contract with a standing permission, and only if you turn Capture Everywhere on. You set a weekly cap. The keeper can pull round-ups under that cap, and it can send them to exactly one place: your own vault position. The contract has no owner and no pause, so nobody, including us, can change its rules after deployment.

## What "rounding up" means when there's no cash register

A card purchase has an obvious round-up: $4.60 coffee, 40 cents of change. An onchain swap doesn't, so Dust defines it. A round-up is always measured in dollars: we take the dollar value of your swap and round it up to the next whole dollar. You choose the granularity, nearest 1 or nearest 5, or a multiplier if you want the background investing to run hotter.

Swaps inside Dust are paid in USDG, so the round-up comes straight out of USDG in the transaction you sign. Outside activity can be in USDG or in ETH. When you spend ETH, Dust values it in dollars at the pool price at that moment, rounds up, and captures the change. A round-up is worth what it was worth when you made it; once it lands in your vault as USDG it stops moving with the price of ETH.

On Solana the shape is the same with different parts: USDC is the dollar, swaps route through Jupiter into xStocks, and the program refuses to record a purchase unless your vault received what a fresh quote promised. You can fund round-ups there from USDC or SOL. [Also on Solana](solana.md) has the details.

## Where the automation comes from

Inside the Dust app, you sign your own round-ups and nothing else is needed. The more interesting case is everything you do everywhere else. Turn on Capture Everywhere, set a weekly cap, and Dust's keeper rounds up your outside trades and payments too, on its own schedule, without you lifting a finger. Exactly what that permission can and cannot do, and how to fund it from USDG, WETH, or a small ETH float, is covered in [Wallets and custody](wallets-and-custody.md).
