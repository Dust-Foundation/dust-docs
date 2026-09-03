---
cover: .gitbook/assets/covers/roadmap-v3.png
coverY: 0
---

# Roadmap and status

This page is the honest ledger of what's built, what's in progress, and what's planned. It gets updated as things ship, and we keep the history rather than rewriting it. It's sequenced by phase rather than by promised dates: in a market this young, a roadmap with confident quarter labels is a fiction, and we'd rather tell you the order things happen in and what gates each step.

## Done: deployed on Robinhood Chain mainnet

The four Dust contracts are deployed on Robinhood Chain mainnet, the keeper runs on production infrastructure, and the full loop has been verified against live mainnet state: a round-up on a USDG swap, a sweep into Stock Tokens at the quoted price from the live Uniswap v3 pools, and a withdrawal back out. The launch menu is TSLA, NVDA, AAPL, AMZN, and SPY. Capture Everywhere is live for round-ups funded from USDG. WETH and ETH float funding are live too, and the first ETH-funded round-up has been captured and swept into Stock Tokens on mainnet. This is the proof that the mechanism works, not an invitation for the public yet. The gates below are what stand between here and open doors.

## Done: deployed on Solana mainnet

The Solana program is live on mainnet, and the full loop has been run with real money: a real round-up, invested through Jupiter into real xStocks, then withdrawn back out. All three ways change gets captured work end to end there: round-ups on in-app swaps (funded from USDC or SOL), Capture Everywhere from a USDC balance, and Capture Everywhere from SOL through a Squads smart account. [Also on Solana](solana.md) explains the deployment.

## Now: audit and hardening

The contracts are new Solidity and the program is new Rust, so the next gate is an external professional audit of both, with findings resolved and the report published. Alongside it: moving ownership of the sweeper and the treasury address onto a multisig on Robinhood Chain, and moving the admin role and upgrade authority onto a multisig (or burning the upgrade authority) on Solana. None of this is optional before other people's money is involved.

## Next: capped beta

A deliberately small launch: invite-only, with per-user caps and a cap on total protocol size. The founder's own funds have already gone through the live system; beta widens that to a small group, with the caps and the reasoning stated. Caps rise gradually as the system proves itself. If you want in early, the waitlist is in the app.

## Then: open launch

Public signup and caps lifted in stages, with the app and keeper hosted for reliability and a public bug bounty live from day one.

## Planned, in rough order

- Embedded wallets and smart accounts with scoped session keys, so opting in does not require managing a wallet or granting a token allowance. Planned, not shipped; any EVM wallet works today.
- A boost option: add a fixed amount on top of each round-up, for people who want the background investing to run hotter.
- Round-ups on more of your activity, priced from onchain quotes.
- Themed baskets, composed from the Stock Tokens already on the chain.
- Deeper pool routing as Robinhood Chain's markets grow.
- On Solana: native SOL captured straight into your basket, without the small conversion step the current SOL path uses, and the rest of the list above kept in step where Solana's primitives allow.

## What we won't build

No leverage on round-ups. No yield products that depend on a centralized counterparty; that's the exact failure that took down Donut, and "your boring stock basket quietly became someone's loan book" is not a sentence we ever want to write in a postmortem.
