---
cover: .gitbook/assets/covers/glossary.png
coverY: 0
---

# Glossary

Crypto documentation has a habit of defining jargon with more jargon. These are the terms used in these docs, in plain language, with what each one means for you specifically.

**Round-up.** The gap between what you spent on a swap and that amount rounded up to your chosen granularity. Spend 137.42 with nearest-5 rounding and the round-up is 2.58. It's the raw material of the entire product.

**Sweep.** The act of collecting your round-up and buying the basket with it. In-app swaps sweep instantly inside your own transaction; automated sweeps run on a schedule and are batched to save gas.

**USDG.** The dollar stablecoin on Robinhood Chain, issued by Paxos. One USDG targets one dollar. Round-ups are denominated and collected in it.

**Stock Token.** A token on Robinhood Chain that tracks the price of a real US stock, issued by Robinhood's issuance entity. Price exposure, settled onchain, held in your own wallet. Not a share: no voting rights, and your claim is on the issuer. The [basket page](the-basket.md) covers the difference properly.

**Basket.** The fixed, published set of Stock Tokens (with fixed weights) that your round-ups buy. Changes only through a public, delayed process.

**Vault.** The contract that holds your basket purchases and tracks your position, cost basis, and history. Your assets, no lockups, withdrawable any time.

**Shares (vault shares).** The accounting units that track your slice of the vault's assets. When we say your vault "holds $83.40," it means your shares currently redeem for that much of the basket.

**Self-custody.** Your assets are controlled by your keys, not held by a company on your behalf. Dust never holds user funds; the [custody page](wallets-and-custody.md) explains the mechanics rather than just asserting the word.

**Smart account.** A wallet that is a program rather than just a keypair, which is what lets it enforce rules like spending caps and scoped permissions. Email signups get one automatically; MetaMask users can upgrade to one without changing address.

**Session key / permission.** The single standing authorization you grant Dust's sweeper: move USDG only, into your basket only, under your cap, until you revoke it. Enforced by your own account's code, not by our good behavior.

**Revoke.** Cancel that permission. One tap in the app, or from your wallet directly. Takes effect immediately and needs nothing from us.

**Slippage.** The difference between the price you expected and the price a trade actually fills at, which grows when markets are thin. Dust sets bounds so a bad fill is rejected instead of accepted.

**Gas.** The fee the blockchain charges to process a transaction, paid in ETH on Robinhood Chain. Small on an L2, but never zero; sweeps are batched to keep it a small fraction of the amount invested.

**L2 (Layer 2).** A blockchain that runs on top of Ethereum, inheriting its security while being faster and cheaper. Robinhood Chain is one.

**Multisig.** A wallet requiring multiple people to approve any action. Dust's admin powers live behind one, so no single person can act alone.

**Timelock.** A mandatory public delay between announcing a protocol change (basket weights, fees) and it taking effect. Its job is to make "quietly" impossible.

**Sequencer.** The machine that orders transactions on an L2. Robinhood Chain's is run by Robinhood; the [chain page](robinhood-chain.md) discusses what that means.

**DEX / AMM.** A decentralized exchange, and the pool-based mechanism (automated market maker) most of them use for pricing. Dust buys the basket on the chain's public Uniswap pools, at prices anyone can verify.
