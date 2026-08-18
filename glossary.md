---
cover: .gitbook/assets/covers/glossary-v2.png
coverY: 0
---

# Glossary

Crypto documentation has a habit of defining jargon with more jargon. These are the terms used in these docs, in plain language, with what each one means for you specifically.

**Round-up.** The gap between what you spent on a swap and that amount rounded up to your chosen granularity. Spend $137.42 with nearest-5 rounding and the round-up is $2.58. It's the raw material of the entire product.

**Investing (the sweep).** Collecting your banked round-ups and buying your basket with them, through Jupiter. In-app round-ups get banked when you sign; automated investing runs on the keeper's schedule.

**Capture-everywhere.** Rounding up swaps and payments you make outside the Dust app, not just inside it. It uses a capped, revocable permission you grant, funded from either USDC or SOL.

**USDC.** The dollar stablecoin Dust uses on Solana. One USDC targets one dollar. Round-ups are denominated in it, and it's what your basket is bought with.

**xStock.** A token on Solana that tracks the price of a real US stock, issued by Backed and held one-to-one against real shares. Price exposure, settled onchain, in your own wallet. Not a share: no voting rights, and your claim is on the issuer. The [basket page](the-basket.md) covers the difference, and the issuer's freeze/clawback power, properly.

**Basket.** The set of xStocks, with weights, that you choose for your round-ups to buy. You compose it yourself from the menu Dust lists onchain, and can change it any time.

**Vault.** Your account in Dust's onchain program. It holds your banked round-ups and your basket position, with cost basis and history. Your assets, no lockups, withdrawable any time.

**The keeper.** The off-chain worker that does the swaps and collects capture round-ups. It holds no discretion: the program rejects any investment where your vault didn't receive what a live quote promised, so a misbehaving keeper can only make a transaction fail, never divert funds.

**Self-custody.** Your assets are controlled by your keys, not held by a company on your behalf. Dust never holds user funds; the [custody page](wallets-and-custody.md) explains the mechanics rather than just asserting the word.

**SPL delegate.** A native Solana permission to let someone move up to an approved amount from one of your token accounts. Dust uses it for USDC capture: the keeper can pull your round-ups from your USDC, capped, and you revoke it in one tap.

**Squads smart account.** A programmable account (from Squads, an audited Solana protocol) that can hold your SOL and enforce rules like spending limits. Dust uses it for SOL capture: you grant the keeper a weekly SOL limit, enforced onchain, revocable any time.

**Spending limit.** The onchain rule on a Squads account that lets the keeper pull up to so much SOL per week, to one destination. Enforced by Squads, not by Dust's good behavior.

**Revoke.** Cancel a permission, whether an SPL delegate or a Squads limit. Takes effect immediately and needs nothing from us.

**Jupiter.** Solana's main swap aggregator. It routes a trade across every major DEX to find the best price. Dust buys your basket through it, and the fill is verified onchain before it counts.

**Slippage.** The difference between the price you expected and the price a trade actually fills at, which grows when markets are thin. Dust sets bounds so a bad fill is rejected instead of accepted.

**SOL.** Solana's native token, used to pay network fees. Fees are usually a fraction of a cent. You can also fund round-ups from SOL, converted to USDC as they're banked.

**Program.** On Solana, an onchain program is what other chains call a smart contract. Dust is a single program that enforces every rule described in these docs.

**Multisig.** An account requiring multiple approvers for any action. Dust's admin powers and the program's upgrade authority move behind one before public launch, so no single person can act alone.

**Timelock.** A mandatory public delay between announcing a protocol change and it taking effect. Its job is to make "quietly" impossible.
