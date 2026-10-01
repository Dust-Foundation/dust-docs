---
cover: .gitbook/assets/covers/roadmap-v3.png
coverY: 0
---

# Roadmap and status

This page is the honest ledger of what's built, what's in progress, and what's planned. It gets updated as things ship, and we keep the history rather than rewriting it. It's sequenced by phase rather than by promised dates: in a market this young, a roadmap with confident quarter labels is a fiction, and we'd rather tell you the order things happen in and what gates each step.

## Done: deployed on Robinhood Chain mainnet

The four Dust contracts are deployed on Robinhood Chain mainnet, the keeper runs on production infrastructure, and the full loop has been verified against live mainnet state: a round-up on a USDG swap, a sweep into Stock Tokens at the quoted price from the live Uniswap v3 pools, and a withdrawal back out. The menu is twenty Stock Tokens: the launch five (TSLA, NVDA, AAPL, AMZN, SPY) plus MSFT, GOOGL, META, NFLX, AMD, PLTR, QQQ, GLD, SPCX and MSTR, added Sept 9, and MU, COST, LLY, CRCL and HIMS, added Sept 21, plus Bitcoin (Coinbase Wrapped BTC) and Ether, added Sept 30 as the first crypto on the menu. Capture Everywhere is live for round-ups funded from USDG. WETH and ETH float funding are live too, and the first ETH-funded round-up has been captured and swept into Stock Tokens on mainnet. This is the proof that the mechanism works, not an invitation for the public yet. The gates below are what stand between here and open doors.

## Done: deployed on Solana mainnet

The Solana program is live on mainnet, and the full loop has been run with real money: a real round-up, invested through Jupiter into real xStocks, then withdrawn back out. All three ways change gets captured work end to end there: round-ups on in-app swaps (funded from USDC or SOL), Capture Everywhere from a USDC balance, and Capture Everywhere from SOL through a Squads smart account. [Also on Solana](solana.md) explains the deployment.

## Done: deployed on Arc mainnet

September 18, 2026, two days after Circle opened Arc. The same four audited contracts, byte for byte, with a keeper running on production infrastructure. The loop was verified against live Arc state before deploy: a USDC round-up captured, swept into cirBTC at the pinned price, withdrawn. cirBTC is the only asset listed because it is the only one on Arc with real liquidity today; more get listed as they arrive. [Also on Arc](arc.md) explains the deployment.

## Done: deployed on Base mainnet

Coinbase's tokenized stocks (NVDAc, AAPLc, METAc, GOOGLc) and AERO, plus cbBTC and Ether since Sept 30, bought through Aerodrome Slipstream pools, where their liquidity lives. The four audited contracts unchanged, behind a forty-line adapter that presents Aerodrome to them in the Uniswap shape they expect. The loop was verified against live Base state before deploy. [Also on Base](base.md) explains the deployment.

## Done: the app, version 1

September 23, 2026: the app was rebuilt around four tabs, Home, Basket, Round-ups and More, with a two-step setup for a new wallet and plain words everywhere. September 27: scheduled deposits, a fixed amount added weekly or monthly on top of round-ups, running under the same weekly limit. [How to use Dust](how-to-use.md) describes the current app.

## Now: October 2026

A big month. This is what we are shipping, in order. Weeks are the order things happen in, not promises of a date; dates may shift, and we would rather ship it right than ship it on a Tuesday. An AMA every Friday and a recap post every week.

**Week 1**

* This roadmap.
* Recurring deposits: live since September 27. Set a weekly or monthly amount on top of your round-ups.
* First look at the mobile app.
* RWA basket teaser: your spare change into real-world assets.
* Friday AMA: full roadmap walkthrough.

**Week 2**

* First new integration of the month goes live.
* Mobile app beta opens. $DUST holders get first access.
* Buyback and burn dashboard: revenue in, tokens bought back, tokens burned, each with a transaction link.
* Friday AMA with the integration partner.

**Week 3**

* Second integration of the month goes live.
* Holder multipliers: the more $DUST you hold, the more you round up.
* Auto-rebalancing: your weights stay where you set them.
* More on how the RWA basket works.
* Friday AMA: open floor. Bring the hard questions.

**Week 4**

* Mobile app launches publicly.
* First public burn, announced with the transaction hash.
* Final look at the RWA basket before launch.
* Friday AMA: live walkthrough of the app.

**Week 5**

* RWA basket goes live.
* Monthly revenue post: real numbers, buybacks and burns to date.
* Public metrics dashboard: round-ups, volume and active vaults, updating live.
* Friday AMA: month recap and what is coming in November.

Alongside all of this we are building the marketing around every release, videos, walkthroughs and teasers, so by the time something goes live you already know exactly what it does and why it matters.

## Now: audit and hardening

The Robinhood Chain contracts were audited by [CredShields](https://credshields.com), with the report delivered on September 11, 2026: twelve findings, none critical, one high. Every finding was addressed in a new version of the four contracts, deployed the same day, with a test for each that replays the auditor's scenario, and CredShields re-reviewed and marked every finding fixed. The full report is public: [Audit_Report_Dust.pdf](https://github.com/Credshields/audit-reports/blob/master/Audit_Report_Dust.pdf). The Arc and Base deployments reuse that exact bytecode, so they are covered; the Base adapter is new code and goes to the auditors as a small follow-up. The Solana program still needs its own external audit. Alongside it: moving ownership of the sweeper and the treasury address onto a multisig on Robinhood Chain and on Arc, and moving the admin role and upgrade authority onto a multisig (or burning the upgrade authority) on Solana. None of this is optional before other people's money is involved.

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
