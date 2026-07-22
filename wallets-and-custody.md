---
cover: .gitbook/assets/covers/wallets-and-custody.png
coverY: 0
---

# Wallets and custody

This page exists because "non-custodial" is the most abused word in crypto. Here is what it means at Dust, mechanically, so you can verify it rather than trust it.

## Who holds what

Your assets sit in your own wallet: either an embedded wallet created at signup that only you control, or the external wallet you connected. Dust the company has no account that holds user funds. There is no pooled deposit contract, no omnibus wallet, no "balance" that exists in our database instead of on the chain. If Dust the company disappeared tomorrow, your tokens would still be in your wallet and withdrawable with standard tools, without our website.

The three prior attempts at this product category all held customer money, and all three ended with users unable to withdraw. We built Dust so that this failure is structurally impossible rather than merely promised against.

## The one permission Dust asks for

Automation needs authority, so we ask for the smallest one that works. When you enable automatic round-ups, your wallet grants the DustSweeper contract a scoped session permission:

| The permission can | The permission cannot |
|---|---|
| Move USDG from your account | Touch any other token you hold |
| Send it only into basket purchases credited to your vault | Send funds to any other address |
| Spend up to the per-period cap you set | Exceed the cap, ever, for any reason |
| Act until you revoke it | Survive revocation |

These limits are not policies we follow. They are constraints enforced by your own account's code: if our backend tried to exceed them, the transaction would fail on chain the same way a wrong password fails. This is worth sitting with for a second, because it is the entire trust model. You are not trusting Dust's honesty; you are trusting a rule your own wallet enforces, which you can read and revoke.

Revocation is one tap in the app, and for external wallets it also works from the wallet's own interface, so you never depend on our site being up to turn us off.

## Embedded wallets

If you signed up with email, your wallet is an ERC-4337 smart account, with the signing key secured by our wallet infrastructure provider and controlled through your login. You can export your key at any time and take the account to another interface. Recovery works through your email login rather than a seed phrase. There is a real trade-off here: it's dramatically easier, and it means your account security is only as good as your email security. Turn on two-factor authentication for the email you use.

## External wallets

MetaMask and similar wallets work in three tiers, and you choose how deep to go:

1. Connect and swap. Works today, no standing permission at all. Round-ups happen only on swaps made through Dust, captured inside the transaction you sign.
2. Grant a periodic permission (ERC-7715, in recent MetaMask releases). One signature, and Dust can sweep your accrued round-ups on a schedule, within the cap. Managed and revocable from MetaMask itself.
3. Upgrade your address to a smart account (EIP-7702). Same address, same keys, full automation, batched approvals. For power users; entirely optional.

Nothing about tier 1 requires trusting Dust with anything beyond the single transaction in front of you, which makes it a reasonable way to try the product before granting any standing permission. We'd suggest exactly that.
