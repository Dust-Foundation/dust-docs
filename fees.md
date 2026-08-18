---
cover: .gitbook/assets/covers/fees-v2.png
coverY: 0
---

# Fees

One fee, stated up front: Dust charges a percentage of each round-up at the moment it's invested. The current rate is shown in the app before you enable round-ups and on every investment receipt afterward. If the rate ever changes, it changes through the same public, timelocked process as anything else, never quietly, and it is capped in the program's own code so it can never exceed a hard ceiling.

On a $2.58 round-up at a 1% fee, Dust earns about 3 cents and $2.55 goes into your basket. That's the entire relationship. The fee is only taken when something is actually invested, so change that gets banked but not yet swept costs you nothing.

What we deliberately do not charge:

- No deposit or withdrawal fees. Leaving is free, always. A product that charges you to leave doesn't believe you'd stay.
- No management fee on your vault balance. Your assets sitting there cost you nothing.
- No spread. Your basket purchases execute at the open-market price Jupiter finds across Solana's DEXs, and the transaction record proves it. We do not quote you one price and fill at another.

That last one gets its own paragraph because of history. The clearest fraud finding against Coinseed, the failed round-up app, was not its unregistered status. It was hidden markups: advertising low fees while quietly padding the quoted price of every trade. Onchain execution makes that behavior checkable. Every Dust investment is a public transaction, and the program will not even record it unless your vault received at least what a live quote promised. You can compare what you paid against the market in the same block. We chose rails where "trust us on pricing" is replaced by "check."

## Network fees

Transactions on Solana cost a small fee in SOL, usually a fraction of a cent, plus a priority fee when the network is busy. For swaps you make yourself, you pay it as normal. For automated investing and capture, Dust's keeper pays the network fees out of its own SOL, not yours, and the app shows what each pass did.

## Why this model

We considered a monthly subscription (the Acorns model) and rejected it, because a flat fee punishes exactly the small, sporadic users the product exists for. A percentage of round-ups scales with the value you actually get: invest little, pay pennies. It also aligns us properly. Dust makes money only when your change is actually getting invested, not when your balance sits still and not when you churn trades.
