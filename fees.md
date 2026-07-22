# Fees

One fee, stated up front: Dust charges a percentage of each round-up at the moment it's swept. The current rate is shown in the app before you enable round-ups and on every sweep receipt afterward. If the rate ever changes, it changes through the same timelocked, publicly announced process as the basket, never quietly.

On a 2.58 round-up at a 2.5% fee, Dust earns about 6 cents and 2.52 goes into your basket. That's the entire relationship.

What we deliberately do not charge:

- No deposit or withdrawal fees. Leaving is free, always. A product that charges you to leave doesn't believe you'd stay.
- No management fee on your vault balance. Your assets sitting there cost you nothing.
- No spread. Your basket purchases execute at the public market price on public pools, and the transaction record proves it. We do not quote you one price and fill at another.

That last one gets its own paragraph because of history. The clearest fraud finding against Coinseed, the failed 2018-era round-up app, was not its unregistered status. It was hidden markups: advertising low fees while quietly padding the quoted price of every trade. Onchain execution makes that behavior checkable. Every Dust sweep is a public transaction; anyone can compare what you paid against the pool price in the same block. We chose rails where "trust us on pricing" is replaced by "check".

## Gas

Transactions on Robinhood Chain cost gas like on any chain, though far less than Ethereum mainnet. For swaps you make yourself, you pay gas as normal. For automated sweeps, Dust batches round-ups so gas stays a small fraction of the amount swept, and the app shows gas per sweep. Where sponsored gas is available for embedded-wallet users, we say so explicitly in the app rather than folding costs somewhere less visible.

## Why this model

We considered a monthly subscription (the Acorns model) and rejected it, because a flat fee punishes exactly the small, sporadic users the product exists for. A percentage of round-ups scales with the value you actually get: invest little, pay pennies. It also aligns us properly. Dust makes money only when your change is actually getting invested, not when your balance sits still and not when you churn trades.
