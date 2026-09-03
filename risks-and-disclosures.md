---
cover: .gitbook/assets/covers/risks-and-disclosures-v3.png
coverY: 0
---

# Risks and disclosures

Every investment product carries risk, and products this new carry kinds that older ones don't. This page lists the real ones, in plain language, ordered roughly by how much they should matter to you. Nothing here is hypothetical hand-wringing; each is a risk we actively engineer against, and none can be engineered to zero.

**Market risk.** The basket tracks stocks. Stocks go down, sometimes a lot, sometimes for years. Dust automates buying; it does not make the market kind. A vault that's down 20% is functioning correctly, however it feels.

**Issuer risk.** Stock Tokens are claims on their issuer, not shares of the underlying companies. If the issuer failed or halted the product, token holders would depend on the issuer's redemption and backing arrangements. This is meaningfully different from holding shares at a broker, and it is the single most important structural fact about what you own.

On Robinhood Chain specifically, the issuer can pause a Stock Token or block an address, and Dust cannot override either. Dust skips a paused token during a sweep and returns that leg's USDG to your accrued balance, so your dollars are never stranded. But a Stock Token you already hold cannot be moved by anyone while its issuer has it paused, and a blocked address cannot send or receive it. These are properties of the asset itself and would apply in any wallet, not just Dust.

On Solana, the xStocks token standard (Token-2022) gives the issuer a permanent delegate over the tokens, which is the power to freeze or claw back balances, and a transfer hook that is dormant today but could be activated later. Same category, sharper form, and again a property of the asset rather than of Dust.

**Smart contract risk.** Dust's contracts, and the contracts they compose with (the Uniswap v3 pools, USDG, and the Stock Token contracts), can contain bugs. On Solana the same applies to Dust's program, Jupiter, the token program, and Squads. The Dust code is new, which is exactly why an external audit is the gate before public launch. Audits, invariant testing, and a bug bounty reduce the odds; nothing makes them zero. Our scoped-permission design limits how much a single failure can reach, which is described honestly in [Security](security.md).

**Liquidity risk.** Stock Token markets are young and sometimes thin. Thin markets mean wider spreads and, in stress, prices that drift from the stock's real price. Dust's minimum-output checks reject bad fills rather than accept them, which protects your price at the cost of occasionally delaying a sweep or a large withdrawal.

**Chain risk.** Dust runs on Robinhood Chain, a young Layer 2 with a single sequencer operated by Robinhood. If the sequencer is down or degraded, transactions are delayed until it recovers, and investing and capture wait with them. Your funds stay yours throughout, but the automation depends on the chain being up. Solana, where Dust is also deployed, has halted and degraded before, and under heavy congestion transactions can fail or be delayed. Young infrastructure also changes: fees, tooling, and rules can shift under us, and by extension under you.

**Availability.** Stock Tokens are not offered in the United States and several other jurisdictions, and eligibility follows the issuer's rules and your local law. The same is true of xStocks on Solana. Dust does not and cannot extend availability beyond what the issuer permits. It is your responsibility to confirm the product is available where you live, and the app will not pretend otherwise.

**Regulatory risk.** The rules around stock tokens and similar instruments are actively evolving in most jurisdictions. Future rulings could restrict how products like Dust operate, where, or for whom. Our non-custodial, non-discretionary design was chosen partly because it is the most defensible shape for this product, and that is a judgment, not a guarantee.

## The disclosures, plainly

Dust is software, not a broker, adviser, or fund. It executes the deterministic rule you configured; it does not choose investments for you, and nothing in the app or these docs is investment advice. Past performance of any basket, real or backtested, does not predict future results. Only invest what you can afford to lose, which for a spare-change product should be unusually easy advice to follow.

If, after reading this page, the product still makes sense to you, you understand it as well as we can make it understandable. That was the goal.
