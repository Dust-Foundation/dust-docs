---
cover: .gitbook/assets/covers/wallets-and-custody-v3.png
coverY: 0
---

# Wallets and custody

This page exists because "non-custodial" is the most abused word in crypto. Here is what it means at Dust, mechanically, so you can verify it rather than trust it.

## Who holds what

Your assets sit in your own wallet, the MetaMask or other EVM account you connected. Dust the company has no account that holds user funds. There is no pooled deposit, no omnibus wallet, no "balance" that exists in our database instead of on the chain. Your accrued round-ups and your basket live in the vault contract as a balance in your name, withdrawable by you at any time, and the contract has no function that can send them anywhere but back to you. It has no pause. Its owner has no power over balances. If Dust the company disappeared tomorrow, your funds would still be on Robinhood Chain and withdrawable with standard tools, without our website.

The prior attempts at this product category all held customer money, and all ended with users unable to withdraw. We built Dust so that this failure is structurally impossible rather than merely promised against.

## The one permission Dust asks for

Automation needs authority, so we ask for the smallest one that works. Round-ups on swaps you make inside the app need no standing permission at all, you sign each one. The standing permission only comes in when you turn on Capture Everywhere for outside activity, and it is scoped hard:

| The permission can | The permission cannot |
|---|---|
| Pull your round-up change | Touch your other tokens |
| Send it only into your own vault position | Send funds to any other address |
| Spend up to the weekly cap you set | Exceed that cap, ever, for any reason |
| Act until you revoke it | Survive revocation |

These limits are not policies we follow. They are enforced by the Capture contract's code and by standard token allowances your wallet controls. If our keeper tried to exceed them, the transaction would fail on chain the same way a wrong password fails. This is worth sitting with, because it is the entire trust model. You are not trusting Dust's honesty. You are trusting a rule the chain enforces, which you can read and revoke.

## Three ways to fund Capture Everywhere

**From USDG, with a token allowance.** You grant the Capture contract a standard ERC-20 allowance on your USDG: a native permission to move up to an approved amount from your wallet. The keeper pulls your round-up from it straight into your vault, and the contract independently checks every pull against your weekly cap. Your allowance is a second cap you control from any wallet interface. Revoke it in one tap, from the app or your wallet. This path is live.

**From WETH, with a token allowance.** For people who mostly hold ETH. You grant the same kind of allowance on your wrapped ETH. When the keeper sees an outside transaction, the Capture contract swaps exactly the round-up's worth of WETH into USDG on one fixed Uniswap v3 pool and credits your vault. The contract refuses any price worse than the pool's 10-minute average plus 2 percent, so a misbehaving keeper cannot overpay with your ETH.

**From an ETH float.** If you would rather not hold wrapped ETH, park a small amount of plain ETH in the Capture contract. It is credited to you, only you, and you can withdraw it at any time, whether your cap is on or off. The keeper draws round-ups from it under the same price guard as the WETH path.

Whichever you use, the weekly cap counts every source together, and it can only ever add to your vault, never take from it. Set the cap to zero and Capture Everywhere is fully off.

On Solana, the same feature uses that chain's own primitives: a token delegate on your USDC, or a Squads smart account spending limit for SOL. [Also on Solana](solana.md) explains both.

## New to wallets

If you have never held a wallet, MetaMask is the common starting point: install it, and it creates an account only you control. Write down its recovery phrase and keep it somewhere safe, because whoever has that phrase has the account. Add Robinhood Chain as a network (the app does this for you), fund it with a little USDG to invest and a little ETH for fees, and you are ready. Dust never sees your recovery phrase and cannot recover it for you, which is the price of nobody else being able to touch your funds either.

For people who do not want to manage a wallet at all, we are building a path with embedded wallets and smart accounts, where the permission Dust holds is a scoped session key instead of a token allowance. That is planned, not shipped. Today, any EVM wallet works.

## Trying it before you trust it

You do not have to grant any standing permission to use Dust. Connect, build a basket, and round up your in-app swaps by signing each one. Nothing there trusts Dust with anything beyond the single transaction in front of you. It is a reasonable way to see the product work before you turn on Capture Everywhere, and we would suggest exactly that.
