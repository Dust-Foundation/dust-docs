---
cover: .gitbook/assets/covers/the-vault-v2.png
coverY: 0
---

# The vault

The vault is where your round-ups accumulate. It is also, we suspect, the screen you'll open most, so here is exactly what it shows and how the mechanics work underneath.

## What you see

Your vault shows your basket balance, the breakdown by stock, your total contributed (every round-up ever, summed), and the difference between the two, which is your gain or loss. There's also the line the whole product was built for: "You've invested $83.40 without noticing since March 14."

Cost basis is tracked per investment, so you can see every individual round-up, what it bought, and at what price. Export it any time; your accountant will want it, and we'd rather give you a clean CSV than make you scrape a block explorer.

## How it works underneath

Your vault is an account in Dust's onchain program, keyed to your wallet. It holds two things: your banked round-ups (USDC waiting to be invested) and your basket position, tracked per stock with its cost basis. The stock tokens themselves are held in a program vault and attributed to you in your account, so your slice is always exactly yours and always onchain. Nothing about your balance lives only in our database. Any block explorer can read your position.

The program holds nothing of its own between the moment change is banked and the moment it's invested. There is no pooled pot, no shared balance, no accounting that could drift from what the chain says.

## Withdrawing

No lockups, no notice periods, no withdrawal windows. Two options:

- **In kind.** The stock tokens themselves move to your wallet. You keep your market exposure and simply stop using the vault's accounting.
- **To USDC.** Your banked round-ups come back as USDC directly. For basket positions, you move the stock tokens out and can sell them on the open market whenever you choose.

Withdrawals are yours to make even if round-ups are paused, even if new investing is paused, and even if the Dust website is down (by calling the program directly). The program has no instruction that lets anyone gate a withdrawal. We treat "can the user always leave" as a hard invariant, and it's one of the specific properties the security review checks.

## One thing the vault will not do

It will not nudge you. No streaks, no "your friends invested more than you," no notifications engineered to make you check daily. The entire thesis of Dust is that good investing happens when you're not paying attention. A vault that begs for attention would be arguing against itself.
