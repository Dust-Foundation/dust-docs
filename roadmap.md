# Roadmap and status

This page is the honest ledger of what's built, what's in progress, and what's planned. It gets updated as things ship, and we keep the history rather than rewriting it. Sequenced by phase rather than by promised dates: in a market this young, a roadmap with confident quarter labels is a fiction, and we'd rather tell you the order things happen in and what gates each step.

## Now: testnet

Dust is being built and proven on Robinhood Chain's testnet. The core contracts (router, sweeper, vault) and the app are developed against test Stock Tokens. The gate to everything after: the full flow working end to end, plus a completed third-party audit of the contract suite.

## Next: capped beta on mainnet

A deliberately small launch: invite-only, with per-user vault caps and a global cap on total protocol size. The founder's own funds go through the system for weeks before anyone else's. Caps rise gradually as the system proves itself with real money, and beta users will know the caps and the reasoning. If you want in early, the waitlist is in the app.

## Then: open launch

Public signup, caps lifted in stages, and the second wallet tier for MetaMask users (automatic sweeps via granted permissions) if wallet support on the chain has matured by then; otherwise it follows as its own release.

## Planned, in rough order

- Round-ups on swaps that don't touch USDG, priced via onchain oracles.
- A boost option: add a fixed amount on top of each round-up, for people who want the background investing to run hotter.
- Address upgrading (EIP-7702) so external wallets get the full automated experience without changing address.
- Borrowing against your vault through the chain's lending markets, so long-term holders can access liquidity without selling.
- Themed baskets, starting with an index-style option when a sufficiently liquid tokenized index product exists on our chain. Today none does, which is why the launch basket is individual blue chips.
- Additional chains and issuers, once the first deployment has earned the right to be copied.

## What we won't build

No leverage on round-ups. No token (see [the page on that](no-token.md)). No yield products that depend on a centralized counterparty; that's the exact failure that took down Donut, and "your boring stock basket quietly became someone's loan book" is not a sentence we ever want to write in a postmortem.
