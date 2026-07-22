---
cover: .gitbook/assets/covers/the-basket-v2.png
coverY: 0
---

# The basket

Your round-ups buy a fixed basket of tokenized blue-chip stocks. This page covers what those tokens actually are, what's in the basket, and who can change it (almost nobody, slowly, in public).

## What you're actually buying

The basket holds Stock Tokens issued on Robinhood Chain. Each one tracks the price of a real US stock and is backed by the issuer, Robinhood's dedicated issuance entity. They trade around the clock, settle onchain in seconds, and sit in your own wallet.

Now the honest part, and please read it: **a Stock Token is not a share.** It is a tokenized instrument that gives you price exposure to the stock. You do not get voting rights, you are not a shareholder of record, and your claim is against the token's issuer, not against Nvidia or Apple. When we say "you own a piece of the market," we mean your vault's value moves with the market, which for a background investing product is the part that matters. But we will never blur the legal difference, and you should be suspicious of anyone in this space who does.

If Stock Tokens are unavailable where you live (they are not offered in the United States and several other countries), Dust cannot make them available to you. Eligibility follows the issuer's rules, not ours. See [Risks and disclosures](risks-and-disclosures.md).

## What's in it

The launch basket is deliberately unexciting: a handful of the largest, most liquid US names available as Stock Tokens, at fixed published weights. The exact list and weights live in the app and onchain, where they are verifiable. The selection principle is boring on purpose. This is the "default index" for people who don't want to choose, not a managed fund chasing performance. If you have strong opinions about allocation, Dust is probably not where you express them; the basket is for the version of you that would otherwise invest nothing.

Themed baskets (an index-style option, a dividend tilt) are on the roadmap, but we would rather launch one good default than five mediocre choices.

## Who can change the basket, and how

Nobody at Dust can quietly change what your change buys. Basket composition is controlled by a multisig behind a timelock: any change is published onchain and takes effect only after a public delay, giving you time to see it, disagree with it, and turn off round-ups or withdraw before it applies. Day to day, the sweeper executes the same deterministic rule every time. There is no trader at Dust, no discretion, no rebalancing desk. This is a design choice with a history behind it: the last company that exercised discretion over swept user funds, Coinseed, converted customer balances into dogecoin without consent and was shut down by a court. Deterministic rules are the reason a product like this can deserve trust at all.

## Pricing and execution

Round-ups buy the basket at market on the chain's public Uniswap pools, with slippage bounds set so a thin market rejects your purchase rather than filling it badly. Small purchases are batched where that saves meaningful gas. You always see, per sweep, exactly what was bought at what price; the app shows it and the chain records it.
