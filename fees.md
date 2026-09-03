---
cover: .gitbook/assets/covers/fees-v3.png
coverY: 0
---

# Fees

One fee, stated up front: Dust charges a percentage of each round-up at the moment it's invested. The rate is 1% at launch, and it is shown in the app before you enable round-ups and on every investment receipt afterward. If the rate ever changes, it changes onchain, in the open, never quietly, and the sweeper contract caps it in code at 5% so it can never exceed that ceiling no matter who holds the admin key.

On a $2.58 round-up at a 1% fee, Dust earns about 3 cents and $2.55 goes into your basket. That's the entire relationship. The fee is only taken when something is actually invested, so change that has accrued but not yet been swept costs you nothing.

What we deliberately do not charge:

- No deposit or withdrawal fees. Leaving is free, always. A product that charges you to leave doesn't believe you'd stay.
- No management fee on your vault balance. Your assets sitting there cost you nothing.
- No spread. Your basket purchases execute at the open-market price in canonical Uniswap v3 pools on Robinhood Chain, and the transaction record proves it. We do not quote you one price and fill at another.

That last one gets its own paragraph because of history. The clearest fraud finding against Coinseed, the failed round-up app, was not its unregistered status. It was hidden markups: advertising low fees while quietly padding the quoted price of every trade. Onchain execution makes that behavior checkable. Every Dust investment is a public transaction, and the contract will not complete a leg unless your vault received at least the minimum quoted before the sweep. You can compare what you paid against the pool in the same block. We chose rails where "trust us on pricing" is replaced by "check."

## Network fees

Transactions on Robinhood Chain cost a small fee in ETH, usually a fraction of a cent. For swaps you make yourself, you pay it as normal. For automated sweeps and capture, Dust's keeper pays the network fees out of its own ETH, not yours, and the app shows what each pass did.

On Solana the same applies with SOL: you pay fees on your own transactions, the keeper pays for the ones it sends.

## Why this model

We considered a monthly subscription (the Acorns model) and rejected it, because a flat fee punishes exactly the small, sporadic users the product exists for. A percentage of round-ups scales with the value you actually get: invest little, pay pennies. It also aligns us properly. Dust makes money only when your change is actually getting invested, not when your balance sits still and not when you churn trades.
