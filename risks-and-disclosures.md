---
cover: .gitbook/assets/covers/risks-and-disclosures-v3.png
coverY: 0
---

# Risks and disclosures

Every investment product carries risk, and products this new carry kinds that older ones don't. This page lists the real ones, in plain language, ordered roughly by how much they should matter to you. Nothing here is hypothetical hand-wringing; each is a risk we actively engineer against, and none can be engineered to zero.

**Market risk.** The basket tracks stocks. Stocks go down, sometimes a lot, sometimes for years. Dust automates buying; it does not make the market kind. A vault that's down 20% is functioning correctly, however it feels.

**Issuer risk.** Tokenized stocks are claims on their issuer, not shares of the underlying companies. If the issuer failed or halted the product, token holders would depend on the issuer's redemption and backing arrangements. This is meaningfully different from holding shares at a broker, and it is the single most important structural fact about what you own. We chose the largest, most institutionally backed issuer available, which reduces this risk and does not remove it.

On Solana specifically, the xStocks token standard (Token-2022) gives the issuer a permanent delegate over the tokens, which is the power to freeze or claw back balances, and a transfer hook that is dormant today but could be activated later. These are properties of the asset itself and would apply in any wallet, not just Dust. They are the sharpest form of issuer risk on that chain, and you should hold these tokens understanding the issuer retains that control.

**Program risk.** Dust's onchain program, and the programs it composes with (Jupiter for swaps, the token program, Squads for SOL capture), can contain bugs. The Dust program is new Rust, which is exactly why an external audit is the gate before public launch. Audits, invariant testing, and a bug bounty reduce the odds; nothing makes them zero. Our scoped-permission design limits how much a single failure can reach, which is described honestly in [Security](security.md).

**Liquidity risk.** Tokenized stock markets are young and sometimes thin. Thin markets mean wider spreads and, in stress, prices that drift from the stock's real price. Dust's slippage bounds reject bad fills rather than accept them, which protects your price at the cost of occasionally delaying a sweep or a large withdrawal.

**Chain risk.** Dust runs on Solana. Solana is fast and cheap, but it has halted and degraded before, and under heavy congestion transactions can fail or be delayed. A halt or a congested period would delay investing and capture until it cleared. Your funds stay yours throughout, but the automation depends on the chain being up. Dust's second home, Robinhood Chain, is a young Layer 2 with its own version of this risk (a single sequencer whose downtime delays transactions). Young infrastructure also changes: fees, tooling, and rules can shift under us, and by extension under you.

**Availability.** Tokenized stocks like xStocks are not offered in the United States and several other jurisdictions, and eligibility follows the issuer's rules and your local law. Dust does not and cannot extend availability beyond what the issuer permits. It is your responsibility to confirm the product is available where you live, and the app will not pretend otherwise.

**Regulatory risk.** The rules around tokenized securities are actively evolving in most jurisdictions. Future rulings could restrict how products like Dust operate, where, or for whom. Our non-custodial, non-discretionary design was chosen partly because it is the most defensible shape for this product, and that is a judgment, not a guarantee.

## The disclosures, plainly

Dust is software, not a broker, adviser, or fund. It executes the deterministic rule you configured; it does not choose investments for you, and nothing in the app or these docs is investment advice. Past performance of any basket, real or backtested, does not predict future results. Only invest what you can afford to lose, which for a spare-change product should be unusually easy advice to follow.

If, after reading this page, the product still makes sense to you, you understand it as well as we can make it understandable. That was the goal.
