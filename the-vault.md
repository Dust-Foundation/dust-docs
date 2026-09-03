---
cover: .gitbook/assets/covers/the-vault-v3.png
coverY: 0
---

# The vault

The vault is where your round-ups accumulate. It is also, we suspect, the screen you'll open most, so here is exactly what it shows and how the mechanics work underneath.

## What you see

Your vault shows your basket balance, the breakdown by stock, your total contributed (every round-up ever, summed), and the difference between the two, which is your gain or loss. There's also the line the whole product was built for: "You've invested $83.40 without noticing since March 14."

Cost basis is tracked per investment, so you can see every individual round-up, what it bought, and at what price. Export it any time; your accountant will want it, and we'd rather give you a clean CSV than make you scrape a block explorer.

## How it works underneath

Your vault is your balance in the DustVault contract on Robinhood Chain, keyed to your wallet address. It holds two things: your accrued round-ups (USDG waiting to be invested) and your basket position, tracked per Stock Token with its cost basis. The Stock Tokens themselves sit in the vault contract and are credited to you by name, so your slice is always exactly yours and always onchain. Nothing about your balance lives only in our database. Any block explorer can read your position.

The contract holds nothing of its own between the moment change is accrued and the moment it's invested. There is no pooled pot, no shared balance, no accounting that could drift from what the chain says. Only the router can add accrued change, only the sweeper can spend it, and only you can withdraw.

On Solana your vault is an account in Dust's onchain program with the same shape: USDC waiting to be invested, and your xStocks position with cost basis.

## Withdrawing

No lockups, no notice periods, no withdrawal windows. Two options:

- **In kind.** The Stock Tokens themselves move to your wallet. You keep your market exposure and simply stop using the vault's accounting.
- **To USDG.** Your accrued round-ups come back as USDG directly. For basket positions, you move the Stock Tokens out and can sell them on the open market whenever you choose.

Withdrawals are yours to make even if round-ups are off, even if new sweeps are paused, and even if the Dust website is down (by calling the contract directly). The vault has no pause and no function that lets anyone gate a withdrawal of your USDG. We treat "can the user always leave" as a hard invariant, and it's one of the specific properties the security review checks.

One honest exception, and it is not ours: a Stock Token that its issuer has paused cannot be transferred by anyone until the pause lifts, so an in-kind withdrawal of that one token waits. Your USDG and your other Stock Tokens are unaffected.

## One thing the vault will not do

It will not nudge you. No streaks, no "your friends invested more than you," no notifications engineered to make you check daily. The entire thesis of Dust is that good investing happens when you're not paying attention. A vault that begs for attention would be arguing against itself.
