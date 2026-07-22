# The vault

The vault is where your round-ups accumulate. It is also, we suspect, the screen you'll open most, so here is exactly what it shows and how the mechanics work underneath.

## What you see

Your vault shows your basket balance in dollars, the breakdown by stock, your total contributed (every round-up ever, summed), and the difference between the two, which is your gain or loss. There's also the line the whole product was built for: "You've invested $83.40 without noticing since March 14."

Cost basis is tracked per sweep, so you can see every individual round-up, what it bought, and at what price. Export it any time; your accountant will want it, and we'd rather give you a clean CSV than make you scrape a block explorer.

## How it works underneath

The vault is an ERC-4626-style contract. When your round-ups buy the basket, the stock tokens are deposited and you're credited shares proportional to your contribution. Shares are just accounting: they track your slice of the assets, and the assets themselves stay in the vault contract on chain, attributable to you, at all times. Your position is visible to any block explorer. Nothing about your balance lives only in our database.

## Withdrawing

No lockups, no notice periods, no withdrawal windows. Two options:

- **In kind.** The stock tokens themselves move to your wallet. You keep your market exposure and simply stop using the vault's accounting.
- **To USDG.** The vault sells your share of the basket at market on the same pools it bought from, and you receive stablecoins. Standard slippage bounds apply, and on a thin market a very large withdrawal may execute in parts.

Withdrawals are yours to make even if round-ups are paused, even if the sweeper is paused, and even if the Dust website is down (via the contracts directly). We treat "can the user always leave" as a hard invariant, and it's one of the specific properties our security review checks.

## One thing the vault will not do

It will not nudge you. No streaks, no "your friends invested more than you," no notifications engineered to make you check daily. The entire thesis of Dust is that good investing happens when you're not paying attention. A vault that begs for attention would be arguing against itself.
