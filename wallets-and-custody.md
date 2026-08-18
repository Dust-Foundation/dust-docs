---
cover: .gitbook/assets/covers/wallets-and-custody-v2.png
coverY: 0
---

# Wallets and custody

This page exists because "non-custodial" is the most abused word in crypto. Here is what it means at Dust, mechanically, so you can verify it rather than trust it.

## Who holds what

Your assets sit in your own wallet, the Phantom or Solflare account you connected. Dust the company has no account that holds user funds. There is no pooled deposit, no omnibus wallet, no "balance" that exists in our database instead of on the chain. Your banked round-ups and your basket live in a program vault that is attributable to you and withdrawable by you at any time, and the program has no power to send them anywhere but back to you. If Dust the company disappeared tomorrow, your funds would still be on Solana and withdrawable with standard tools, without our website.

The prior attempts at this product category all held customer money, and all ended with users unable to withdraw. We built Dust so that this failure is structurally impossible rather than merely promised against.

## The one permission Dust asks for

Automation needs authority, so we ask for the smallest one that works. Round-ups on swaps you make inside the app need no standing permission at all, you sign each one. The standing permission only comes in when you turn on capture-everywhere for outside swaps, and it is scoped hard:

| The permission can | The permission cannot |
|---|---|
| Pull your round-up change | Touch your other tokens |
| Send it only into your own vault | Send funds to any other address |
| Spend up to the weekly cap you set | Exceed that cap, ever, for any reason |
| Act until you revoke it | Survive revocation |

These limits are not policies we follow. They are enforced by Solana itself and, in the SOL case, by Squads' audited program. If our keeper tried to exceed them, the transaction would fail on chain the same way a wrong password fails. This is worth sitting with, because it is the entire trust model. You are not trusting Dust's honesty. You are trusting a rule the chain enforces, which you can read and revoke.

## Two ways to fund capture-everywhere

**From USDC, with an SPL delegate.** You grant Dust's keeper a delegate on your USDC account: a native Solana permission to move up to an approved amount from that one account. The keeper pulls your round-up from it, and the program independently checks the pull against your weekly cap on every single one. Revoke it in one tap, from the app or your wallet.

**From SOL, with a Squads spending limit.** Native SOL cannot be delegated the way a token can, so for SOL the seamless path uses a smart account. Your SOL lives in a Squads smart account you alone own, and you grant the keeper a spending limit: up to so much SOL per week, to one destination, revocable any time. The limit is enforced onchain by Squads, an audited protocol that a large share of Solana treasuries already rely on. Dust adds no custody of its own on top of it. When the keeper sees an outside swap, it pulls the round-up in SOL within that limit, converts it to USDC, and credits your vault. It can only ever add to your vault, never take from it.

## New to wallets

If you have never held a Solana wallet, Phantom is the common starting point: install it, and it creates an account only you control. Write down its recovery phrase and keep it somewhere safe, because whoever has that phrase has the account. Fund it with a little USDC to invest and a little SOL for fees, and you are ready. Dust never sees your recovery phrase and cannot recover it for you, which is the price of nobody else being able to touch your funds either.

## Trying it before you trust it

You do not have to grant any standing permission to use Dust. Connect, build a basket, and round up your in-app swaps by signing each one. Nothing there trusts Dust with anything beyond the single transaction in front of you. It is a reasonable way to see the product work before you turn on capture-everywhere, and we would suggest exactly that.
