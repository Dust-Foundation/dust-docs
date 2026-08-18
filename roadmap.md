---
cover: .gitbook/assets/covers/roadmap-v3.png
coverY: 0
---

# Roadmap and status

This page is the honest ledger of what's built, what's in progress, and what's planned. It gets updated as things ship, and we keep the history rather than rewriting it. It's sequenced by phase rather than by promised dates: in a market this young, a roadmap with confident quarter labels is a fiction, and we'd rather tell you the order things happen in and what gates each step.

## Done: deployed and proven on Solana mainnet

The Solana program is live on mainnet, and the full loop has been run with real money. A real round-up, invested through Jupiter into real xStocks, then withdrawn back out. All three ways change gets captured work end to end: round-ups on in-app swaps (funded from USDC or SOL), capture-everywhere from a USDC balance, and capture-everywhere from SOL through a Squads smart account. This is the proof that the mechanism works, not an invitation for the public yet. The gates below are what stand between here and open doors.

## Now: audit and hardening

The program is new Rust, so the next gate is an external professional audit, with findings resolved and the report published. Alongside it: moving the admin role and the program's upgrade authority off the deployment key and onto a multisig (or burning the upgrade authority to make the program immutable), and pointing the keeper and treasury at their production addresses. None of this is optional before other people's money is involved.

## Next: capped beta

A deliberately small launch: invite-only, with per-user caps and a cap on total protocol size. The founder's own funds have already gone through the live system; beta widens that to a small group, with the caps and the reasoning stated. Caps rise gradually as the system proves itself. If you want in early, the waitlist is in the app.

## Then: open launch

Public signup and caps lifted in stages, with the app and keeper hosted for reliability and a public bug bounty live from day one.

## Planned, in rough order

- Native SOL captured straight into your basket, without the small conversion step the current SOL path uses.
- A boost option: add a fixed amount on top of each round-up, for people who want the background investing to run hotter.
- Round-ups on more of your activity, priced from onchain quotes.
- Themed baskets, starting with an index-style option when a sufficiently liquid tokenized index exists on Solana.
- Deeper Robinhood Chain support, kept in step with the Solana build for people already there.

## The other chain

Dust also runs on Robinhood Chain, its second home. That build stays supported and available; Solana is where the primary effort and the newest features land first. [Why Solana](solana.md) and [Why Robinhood Chain](robinhood-chain.md) explain each choice.

## What we won't build

No leverage on round-ups. No yield products that depend on a centralized counterparty; that's the exact failure that took down Donut, and "your boring stock basket quietly became someone's loan book" is not a sentence we ever want to write in a postmortem.
