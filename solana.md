# Also on Solana

Dust lives on Robinhood Chain. We added a Solana deployment because a lot of the people this product is for already trade there, and enough of the same pieces exist on Solana that the product works the same way. So Dust runs on both. Robinhood Chain is the home and the place new features land first; Solana is a full deployment, kept in step where the mechanics allow.

The same four things a round-up product needs are all present on Solana: real blue-chip stock tokens worth accumulating, a deep market to buy them on, a dollar to denominate round-ups in, and permissionless deployment.

The specifics, for those who want them:

| | |
|---|---|
| What it is | A high-throughput Layer 1, roughly 400ms slots, low fees |
| The assets | xStocks: tokenized blue-chip stocks issued by Backed, self-custodied, trading 24/7 |
| The token standard | Token-2022, eight decimals |
| The market | Jupiter, which routes across every major Solana DEX for the best fill |
| The dollar | Native USDC, six decimals |
| Wallets | Phantom, Solflare, and most other Solana wallets |
| Deployment | Permissionless. Anyone can deploy programs, including us |

## What is the same

Everything that matters. You pick a basket and set weights. Your round-ups accrue in a vault account that is yours, and your basket is bought with them by a keeper that holds no discretion. Withdrawals cannot be gated by anyone. The fee is the same percentage of each round-up, taken only when it is invested. And nobody but you can move your funds.

## What differs

**One program instead of four contracts.** On Solana, Dust is a single onchain program that plays the role of the router, vault, sweeper, and capture contracts together. It enforces every rule described in these docs.

**USDC and xStocks.** The dollar is USDC, and the basket holds xStocks, issued by Backed on the Token-2022 standard. An xStock is backed one-to-one by shares the issuer holds with a regulated custodian, and it is not a share: no voting rights, and your claim is on the issuer.

**Funding from SOL.** A round-up is always measured in dollars, but on Solana you can fund it from either USDC or SOL. If you pay from SOL, the app swaps exactly the round-up's worth of SOL into USDC inside the same transaction you sign, then banks it. The change stops moving with the price of SOL the moment it lands.

**Capture Everywhere with Solana's own primitives.** From USDC, you grant a standard SPL delegate on your USDC account, capped by the weekly limit you set, revocable at any time. From SOL, your SOL lives in a Squads smart account you alone own, and you grant the keeper an onchain spending limit: so much SOL per week, to one destination, revocable whenever. Squads is an audited protocol that a large share of Solana treasuries already rely on, and Dust adds no custody on top of it. The keeper can never pull more than your cap, your delegate allowance, and your balance allow, and the program checks all three on every pull.

## How a sweep stays honest

Buying your basket means swapping USDC for xStocks through Jupiter, and Jupiter's route is composed by an off-chain keeper. We do not trust it. Each leg of a sweep is wrapped by the program: it snapshots the vault before the swap, and refuses to finish the leg unless the vault actually received at least the amount a fresh Jupiter quote promised, minus a slippage tolerance. Because the whole leg is one atomic transaction, a keeper that tried to divert or underfill a swap would simply make the transaction revert. The quote is the price guard, and the chain is the enforcer.

## The caveats

xStocks are Token-2022 tokens, and that standard allows two extensions worth naming. The first is a transfer hook, which today is dormant on these mints but could be activated by the issuer later. The second is a permanent delegate, which the issuer holds and which lets them freeze or claw back tokens. This is the Solana form of issuer risk, and it is covered plainly in [Risks and disclosures](risks-and-disclosures.md). It is a property of the asset, not of Dust, and it would apply to these tokens in any wallet.

Solana has a particular hazard worth naming too: copycat tokens with names ending in "pump" or lookalike tickers. Your basket only ever holds the verified xStocks mints the program lists onchain.

Liquidity for stock tokens is still young here as well. Jupiter routing and our onchain slippage bounds protect your price by rejecting bad fills, at the cost of occasionally delaying a sweep when a market is thin.

## Where the Solana deployment stands

The program is deployed to mainnet, and the full loop has been run with real money: a round-up, a live swap through Jupiter into real xStocks, and a withdrawal back out. All three ways change gets captured work end to end. It sits behind the same gate as Robinhood Chain: an external audit and a capped, invite-only beta before the doors open. The [roadmap](roadmap.md) has the current status.

## Two chains, one product

The Dust you use is the same on either chain: pick a basket, let your spare change buy it, withdraw whenever you want, and nobody but you can move your funds. Switching chains is a toggle in the app. We would rather run each chain honestly than pretend the differences do not exist, so where the mechanics differ, these docs say so.
