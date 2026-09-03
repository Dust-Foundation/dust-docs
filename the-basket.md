---
cover: .gitbook/assets/covers/the-basket-v3.png
coverY: 0
---

# The basket

Your round-ups buy a basket of blue-chip Stock Tokens that you choose. This page covers what those tokens actually are, how you pick them, and the honest caveats you should know before you hold one.

## What you're actually buying

On Robinhood Chain the basket holds Stock Tokens, the tokens issued on that chain to track real US stocks and ETFs. Each one is designed to follow the price of its underlying stock, under terms the issuer publishes. They trade around the clock against USDG, settle onchain in a fraction of a second, and sit in a vault position that belongs to you.

Now the honest part, and please read it: **a Stock Token is not a share.** It is an instrument that gives you price exposure to the stock. You do not get voting rights, you are not a shareholder of record, and your claim is against the issuer, not against Nvidia or Apple. When we say "you own a piece of the market," we mean your vault's value moves with the market, which for a background investing product is the part that matters. We will never blur the legal difference, and you should be suspicious of anyone in this space who does.

## You pick the basket

Dust does not hand you a fixed list. You compose your own basket from the Stock Tokens Dust has listed onchain, and you set the weights: an even split across five names, or sixty percent in one and forty in another, whatever you want. The launch menu is TSLA, NVDA, AAPL, AMZN, and SPY, chosen for being the largest and most liquid names available. You can change your basket any time, and the change applies to future round-ups.

The listed menu lives onchain, in the sweeper contract, and the app reads it from there. That matters for one specific reason: it means what you can buy is a verifiable list, not a claim in an interface. Lookalike tokens with famous names exist on every chain. Your basket can only ever hold token contracts Dust has actually listed, which are the issuer's genuine Stock Token contracts, checked for real liquidity before listing.

## The caveats worth knowing

Stock Tokens are issued by a third party under their own rules, and two of those rules are worth naming plainly:

- The issuer can **pause a Stock Token**, which stops every transfer of it until the pause lifts.
- The issuer can **block an address**, which stops that address from sending or receiving the token.

Dust cannot override either. What Dust does instead is refuse to let them strand your dollars. Each leg of a sweep runs in isolation: if a Stock Token in your basket is paused when the keeper sweeps, that leg is skipped and its USDG goes back to your accrued balance, still yours and still withdrawable. If a token you already hold is paused, withdrawing that token waits until the issuer lifts the pause; your USDG and your other Stock Tokens are unaffected. The [Risks and disclosures](risks-and-disclosures.md) page covers it in full.

If Stock Tokens are unavailable where you live (they are not offered in the United States and several other countries), Dust cannot make them available to you. Eligibility follows the issuer's rules, not ours.

On Solana the basket holds xStocks instead, issued by Backed on the Token-2022 standard. The issuer there holds a permanent delegate, which is the power to freeze or claw back balances, and a transfer hook that is dormant today but could be switched on later. Same category of risk, different mechanics. [Also on Solana](solana.md) spells it out.

## Pricing and execution

Round-ups buy your basket from canonical Uniswap v3 pools, each Stock Token paired with USDG. Before each sweep the keeper quotes every leg from the live pool and hands the contract a minimum it must receive; a thin market rejects your purchase rather than filling it badly. You always see, per investment, exactly what was bought at what price: the app shows it and the chain records it. There is no Dust-quoted price to distrust, because the fill is whatever the open pool gave, verified onchain before it counts.
