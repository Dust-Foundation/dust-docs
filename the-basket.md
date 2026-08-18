---
cover: .gitbook/assets/covers/the-basket-v3.png
coverY: 0
---

# The basket

Your round-ups buy a basket of tokenized blue-chip stocks that you choose. This page covers what those tokens actually are, how you pick them, and the honest caveats you should know before you hold one.

## What you're actually buying

On Solana the basket holds xStocks, tokenized stocks issued by Backed. Each one tracks the price of a real US stock and is backed one-to-one by shares the issuer holds with a regulated custodian. They trade around the clock, settle onchain in seconds, and sit in your own wallet.

Now the honest part, and please read it: **an xStock is not a share.** It is a tokenized instrument that gives you price exposure to the stock. You do not get voting rights, you are not a shareholder of record, and your claim is against the issuer, not against Nvidia or Apple. When we say "you own a piece of the market," we mean your vault's value moves with the market, which for a background investing product is the part that matters. We will never blur the legal difference, and you should be suspicious of anyone in this space who does.

## You pick the basket

Dust does not hand you a fixed list. You compose your own basket from the stocks Dust has listed onchain, and you set the weights: an even split across five names, or sixty percent in one and forty in another, whatever you want. The launch menu is a handful of the largest, most liquid US names available as xStocks. You can change your basket any time, and the change applies to future round-ups.

The listed menu lives onchain, in the program, and the app reads it from there. That matters for one specific reason: it means what you can buy is a verifiable list, not a claim in an interface. Solana has a real problem with copycat tokens using famous names and lookalike tickers. Your basket can only ever hold mints Dust has actually listed, which are the genuine Backed issuances, checked for real liquidity before listing.

## The caveats worth knowing

xStocks are built on Token-2022, a newer token standard with optional features, and two of them are worth naming plainly:

- The issuer holds a **permanent delegate** over the tokens, which is the power to freeze or claw back balances. This is the sharpest form of issuer risk on Solana, it is a property of the asset itself, and it would apply in any wallet, not just Dust.
- The tokens carry a **transfer hook** that is dormant today but could be switched on by the issuer later.

Neither of these is something Dust can prevent, and we would rather you hold these tokens knowing the issuer retains that control. The [Risks and disclosures](risks-and-disclosures.md) page covers it in full.

If xStocks are unavailable where you live (they are not offered in the United States and several other countries), Dust cannot make them available to you. Eligibility follows the issuer's rules, not ours.

## Pricing and execution

Round-ups buy your basket through Jupiter, which routes across Solana's DEXs to find the best price, with slippage bounds set so a thin market rejects your purchase rather than filling it badly. You always see, per investment, exactly what was bought at what price: the app shows it and the chain records it. There is no Dust-quoted price to distrust, because the fill is whatever the open market gave, verified onchain before it counts.
