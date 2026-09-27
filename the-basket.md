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

Dust does not hand you a fixed list. You compose your own basket from the Stock Tokens Dust has listed onchain, and you set the weights: an even split, or sixty percent in one and forty in another, whatever you want. The menu is twenty names today: TSLA, NVDA, AAPL, AMZN, SPY, MSFT, GOOGL, META, NFLX, AMD, PLTR, QQQ, GLD, SPCX, MSTR, MU, COST, LLY, CRCL and HIMS, each chosen for having a deep, verified USDG pool. You can change your basket any time, and the change applies to future round-ups.

<details>

<summary>Presets, or build your own</summary>

The Basket tab opens with three ready-made mixes and a custom option.

* **The market**: half SPY, half QQQ.
* **Big tech**: NVDA, AAPL, MSFT, GOOGL, AMZN and META, evenly.
* **A bit of everything**: every Stock Token on the menu, evenly.
* **Build my own**: add the names you want and drag a slider for each. The other sliders adjust so the total is always 100 percent.

Saving any of them is one transaction that records your weights in the sweeper contract under your address. Presets are only a starting point; the contract stores weights, not a preset name, so you can tweak one and save it as your own.

</details>

<details>

<summary>Other kinds of assets: real-world assets and microcaps</summary>

Today the menu is Stock Tokens only. The app is built for two more kinds, which appear in their own sections of **Add a stock** once a qualifying token is listed:

* **Real-world assets.** A token that represents exposure to something like an apartment, issued by a third party. The app says plainly that you hold the token, not the deed, and the issuer's rules apply the same way a Stock Token issuer's do. We diligence the tokenization provider before listing anything, because you inherit their risk.
* **Microcaps.** Small, thinly traded tokens. Only ones you add yourself, and the app caps them at 10 percent of a basket. Round-ups are never routed into microcaps automatically, and Dust does not curate a "degen" list. The point of Dust is spare change into stable assets; a small slice you choose is the most this will ever be.

Neither is available on Robinhood Chain yet. Nothing here is listed until it has a deep, canonical pool, the same bar every Stock Token clears.

</details>

<details>

<summary>Coming next: a blue-chip crypto basket</summary>

The next thing we build is a second kind of basket: the five largest crypto assets, held the same way your stocks are. Pick it on its own or alongside your Stock Tokens, set the weights, and round-ups buy it under exactly the same rules: canonical pools only, a minimum price the contract enforces on every leg, and everything sitting in a vault position that belongs to you.

It is not built yet, and we are not putting a date on it. The list of five, the pools they trade in on Robinhood Chain, and the disclosures will be published here before anything is listed. Like everything else on this page, it will be something you choose, never something round-ups go into on their own.

</details>

<details>

<summary>Adding money on a schedule</summary>

Round-ups only add what your trading produces. If you want a steady amount going in as well, the **Basket** tab has **Add on a schedule** under your basket: an amount, how often (daily, weekly, every two weeks, monthly) and a first date. Each deposit buys your basket at whatever weights it has on the day.

The schedule is a signed instruction, not a new permission. Every deposit goes through the same contract path as a round-up and counts against the same weekly limit you set on-chain, so Dust can never take more than that limit whatever the schedule says. A deposit the wallet cannot cover is skipped with a reason, never retried and never partially filled. Pause, skip the next one, edit or cancel with a signature. [How to use Dust](how-to-use.md) has the step by step.

</details>

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
