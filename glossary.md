---
cover: .gitbook/assets/covers/glossary-v3.png
coverY: 0
---

# Glossary

Crypto documentation has a habit of defining jargon with more jargon. These are the terms used in these docs, in plain language, with what each one means for you specifically. Robinhood Chain terms come first; the Solana terms are at the end.

**Round-up.** The gap between what you spent on a swap and that amount rounded up to your chosen granularity. Spend $137.42 with nearest-1 rounding and the round-up is $0.58; with nearest-5 rounding it is $2.58. It's the raw material of the entire product.

**Sweep (investing).** Collecting your accrued round-ups and buying your basket with them. In-app round-ups accrue when you sign; sweeps run on the keeper's schedule.

**Capture Everywhere.** Rounding up swaps and payments you make outside the Dust app, not just inside it. You set a weekly cap, and the keeper can pull round-ups under it into your own vault position, funded from USDG, WETH, or an ETH float.

**Weekly cap.** The most Capture Everywhere may pull from you in any seven-day window, in dollars, set by you and changeable at any time. It counts every funding source together. Setting it to zero turns the feature off.

**Robinhood Chain.** The Ethereum Layer 2 where Dust lives. Built on Arbitrum's Orbit stack, chain ID 4663, gas paid in ETH, blocks roughly every 100 milliseconds. It is where Stock Tokens are issued and traded.

**Stock Token.** A token on Robinhood Chain that tracks the price of a real US stock or ETF, issued by a third party under its own terms. Price exposure, settled onchain, held in your vault position. Not a share: no voting rights, and your claim is on the issuer, which can pause the token or block an address. The [basket page](the-basket.md) covers the difference properly.

**USDG.** Global Dollar, the stablecoin Dust uses on Robinhood Chain, issued by Paxos. One USDG targets one dollar. Round-ups are denominated in it, and it's what your basket is bought with.

**ETH.** Ether, the token that pays network fees on Robinhood Chain. Fees are usually a fraction of a cent. Outside spending in ETH can be rounded up too, valued in dollars at the pool price.

**WETH.** Wrapped ETH, the token form of ETH that contracts can move with an allowance. Granting an allowance on your WETH is one way to fund Capture Everywhere.

**ETH float.** A small amount of plain ETH you park in the Capture contract for round-ups. Credited to you alone, withdrawable at any time, in every state.

**Allowance.** A standard permission on an ERC-20 token that lets one contract move up to an approved amount from your wallet. Dust uses it for Capture Everywhere on USDG and WETH. You set it, you can lower it or revoke it from any wallet interface, and it is a cap the contract cannot exceed.

**Uniswap v3 pool.** The onchain market where a Stock Token trades against USDG. Dust buys your basket directly from these pools, and the fill is checked against a quoted minimum before it counts.

**Basket.** The set of Stock Tokens, with weights, that you choose for your round-ups to buy. You compose it yourself from the menu Dust lists onchain, and can change it any time.

**Menu.** The onchain list of Stock Tokens you can put in a basket. Dust curates it; you choose from it. Curating the menu is the only basket-related power Dust has.

**Vault.** Your balance in Dust's vault contract. It holds your accrued round-ups and your basket position, with cost basis and history. Your assets, no lockups, withdrawable any time.

**The keeper.** The off-chain worker that triggers sweeps and collects Capture Everywhere round-ups. It holds no discretion: it can only send money into your own vault position, and the contracts reject any leg that returns less than the quoted minimum, so a misbehaving keeper can only make a transaction fail, never divert funds.

**Leg.** One Stock Token's share of a sweep. Each leg runs on its own, so a paused or thin token is skipped, its USDG returned to you, and the rest of the basket still buys.

**Self-custody.** Your assets are controlled by your keys, not held by a company on your behalf. Dust never holds user funds; the [custody page](wallets-and-custody.md) explains the mechanics rather than just asserting the word.

**Revoke.** Cancel a permission: lower an allowance to zero, set your weekly cap to zero, or both. Takes effect immediately and needs nothing from us.

**Slippage.** The difference between the price you expected and the price a trade actually fills at, which grows when markets are thin. Dust sets a minimum output per leg so a bad fill is rejected instead of accepted.

**Smart contract.** Code deployed on the chain that enforces rules nobody can bend after deployment. Dust on Robinhood Chain is four of them: the router, the vault, the sweeper, and the Capture contract.

**Multisig.** An account requiring multiple approvers for any action. Dust's admin powers move behind one before public launch, so no single person can act alone.

**Session key.** A scoped, revocable key a smart account can hand to an app for a narrow set of actions. The planned path for a smoother Dust opt-in; not shipped yet.

## Solana terms

**Program.** On Solana, an onchain program is what other chains call a smart contract. Dust on Solana is a single program that enforces every rule described in these docs.

**USDC.** The dollar stablecoin Dust uses on Solana. One USDC targets one dollar.

**xStock.** A token on Solana that tracks the price of a real US stock, issued by Backed and held one-to-one against real shares. Not a share, and the issuer holds a freeze and clawback power over the token.

**SOL.** Solana's native token, used to pay network fees. You can also fund round-ups from SOL, converted to USDC as they're banked.

**Jupiter.** Solana's main swap aggregator. It routes a trade across every major DEX to find the best price. Dust buys the Solana basket through it, and the fill is verified onchain before it counts.

**SPL delegate.** A native Solana permission to let someone move up to an approved amount from one of your token accounts. Dust uses it for USDC capture on Solana, capped, revocable in one tap.

**Squads smart account.** A programmable account (from Squads, an audited Solana protocol) that can hold your SOL and enforce rules like spending limits. Dust uses it for SOL capture on Solana.

**Spending limit.** The onchain rule on a Squads account that lets the keeper pull up to so much SOL per week, to one destination. Enforced by Squads, not by Dust's good behavior.
