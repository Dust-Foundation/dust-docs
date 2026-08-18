# Why Solana

Dust started on Robinhood Chain because it was the first place all the pieces existed at once. Solana is where the most people already are, and where enough of those pieces have now arrived that the same product works. So Dust runs on both. Solana is the primary hub; Robinhood Chain stays a first-class home for the people already there.

The same four things a round-up product needs are all present on Solana today: real tokenized blue-chip stocks worth accumulating, a deep market to buy them on, a dollar to denominate round-ups in, and permissionless deployment.

The specifics, for those who want them:

| | |
|---|---|
| What it is | A high-throughput Layer 1, roughly 400ms slots, low fees |
| The assets | xStocks: tokenized blue-chip stocks issued by Backed, self-custodied, trading 24/7 |
| The token standard | Token-2022, eight decimals |
| The market | Jupiter, which routes across every major Solana DEX for the best fill |
| The dollar | Native USDC, six decimals |
| Deployment | Permissionless. Anyone can deploy programs, including us |

Instead of holding a fixed wallet permission the way the EVM version does, the Solana build uses the primitives Solana already has. Your round-ups are moved by transactions you sign, and the capture-everywhere option uses a standard SPL delegate you grant and can revoke at any time, capped by a weekly limit you set. The keeper can never pull more than that cap, the delegate allowance, and your balance allow, and the program checks all three on every pull.

A round-up is always measured in dollars, but you can fund it from either USDC or SOL. If you pay from SOL, the app swaps exactly the round-up's worth of SOL into USDC inside the same transaction you sign, then banks it. That also means the change you bank stops moving with the price of SOL the moment it lands, so a round-up is worth what it was worth when you made it.

## How a sweep stays honest

Buying your basket means swapping USDC for stocks through Jupiter, and Jupiter's route is composed by an off-chain keeper. We do not trust it. Each leg of a sweep is wrapped by the program: it snapshots the vault before the swap, and refuses to finish the leg unless the vault actually received at least the amount a fresh Jupiter quote promised, minus a slippage tolerance. Because the whole leg is one atomic transaction, a keeper that tried to divert or underfill a swap would simply make the transaction revert. The quote is the price guard, and the chain is the enforcer.

## The caveats

xStocks are Token-2022 tokens, and that standard allows two extensions worth naming. The first is a transfer hook, which today is dormant on these mints but could be activated by the issuer later. The second is a permanent delegate, which the issuer holds and which lets them freeze or claw back tokens. This is the Solana form of issuer risk, and it is covered plainly in [Risks and disclosures](risks-and-disclosures.md). It is a property of the asset, not of Dust, and it would apply to these tokens in any wallet.

Liquidity for tokenized stocks is still young here too. Jupiter routing and our on-chain slippage bounds protect your price by rejecting bad fills, at the cost of occasionally delaying a sweep when a market is thin.

## Two chains, one product

The Dust you use is the same on either chain: pick a basket, let your spare change buy it, withdraw whenever you want, and nobody but you can move your funds. Switching hubs is a toggle in the app. We would rather run each chain honestly than pretend the differences do not exist, so where the mechanics differ, these docs say so.
