---
cover: .gitbook/assets/covers/risks-and-disclosures.png
coverY: 0
---

# Risks and disclosures

Every investment product carries risk, and products this new carry kinds that older ones don't. This page lists the real ones, in plain language, ordered roughly by how much they should matter to you. Nothing here is hypothetical hand-wringing; each is a risk we actively engineer against, and none can be engineered to zero.

**Market risk.** The basket tracks stocks. Stocks go down, sometimes a lot, sometimes for years. Dust automates buying; it does not make the market kind. A vault that's down 20% is functioning correctly, however it feels.

**Issuer risk.** Stock Tokens are claims on their issuer, not shares of the underlying companies. If the issuer failed or halted the product, token holders would depend on the issuer's redemption and backing arrangements. This is meaningfully different from holding shares at a broker, and it is the single most important structural fact about what you own. We chose the largest, most institutionally backed issuer available, which reduces this risk and does not remove it.

**Smart contract risk.** Dust's contracts, and the contracts they compose with (the DEX, the vault standard, the wallet stack), can contain bugs. Audits, fuzzing, invariant testing, and a bug bounty reduce the odds; nothing makes them zero. Our scoped-permission design limits how much a single failure can reach, which is described honestly in [Security](security.md).

**Liquidity risk.** Tokenized stock markets are young and sometimes thin. Thin markets mean wider spreads and, in stress, prices that drift from the stock's real price. Dust's slippage bounds reject bad fills rather than accept them, which protects your price at the cost of occasionally delaying a sweep or a large withdrawal.

**Chain risk.** Robinhood Chain is weeks old, runs a single sequencer, and screens transfers for compliance. Sequencer downtime would delay transactions (including sweeps) until it recovered or until Ethereum escape hatches applied. Young chains also change: fees, tooling, and rules can shift under us, and by extension under you.

**Availability.** Stock Tokens are not offered in the United States and several other jurisdictions, and eligibility follows the issuer's rules and your local law. Dust does not and cannot extend availability beyond what the issuer permits. It is your responsibility to confirm the product is available where you live, and the app will not pretend otherwise.

**Regulatory risk.** The rules around tokenized securities are actively evolving in most jurisdictions. Future rulings could restrict how products like Dust operate, where, or for whom. Our non-custodial, non-discretionary design was chosen partly because it is the most defensible shape for this product, and that is a judgment, not a guarantee.

## The disclosures, plainly

Dust is software, not a broker, adviser, or fund. It executes the deterministic rule you configured; it does not choose investments for you, and nothing in the app or these docs is investment advice. Past performance of any basket, real or backtested, does not predict future results. Only invest what you can afford to lose, which for a spare-change product should be unusually easy advice to follow.

If, after reading this page, the product still makes sense to you, you understand it as well as we can make it understandable. That was the goal.
