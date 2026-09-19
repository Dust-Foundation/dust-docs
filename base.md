# Also on Base

Dust lives on Robinhood Chain. Base is the third chain we run on, and it is there for one reason: Coinbase's tokenized stocks trade on Base, and the market for them is Aerodrome. Dust on Base rounds up your swaps and payments and buys those stocks through Aerodrome's Slipstream pools, where their liquidity actually lives.

The specifics, for those who want them:

| | |
|---|---|
| What it is | Coinbase's Layer 2, two-second blocks, ETH for gas |
| The dollar | USDC, six decimals |
| The assets | Coinbase tokenized stocks: NVDAc, AAPLc, METAc and GOOGLc at launch, one-to-one claims on shares held with a regulated custodian, plus AERO, Aerodrome's own token, as a partner asset |
| The market | Aerodrome Slipstream, concentrated-liquidity pools. Each launch stock's pool held between one and one and a half million dollars of USDC when we listed it, twenty to three hundred times what any other venue on Base holds for the same stock |
| Wallets | MetaMask, Rabby, Coinbase Wallet, and anything that supports Base |
| Chain id | 8453 |
| Explorer | https://basescan.org |

## What is the same

Everything. The four contracts on Base are the audited code from Robinhood Chain, byte for byte. Same vault only you can withdraw from, same keeper with no discretion, same 1% fee taken only when change is invested, same weekly cap you set and can zero from your own wallet. Round-ups can be funded from USDC, from WETH, or from a small ETH float, exactly as on Robinhood Chain.

## What differs

**Aerodrome instead of Uniswap.** Dust's contracts were written for Uniswap v3 pools. Aerodrome's Slipstream pools are close cousins: the same swap call, the same callback, the same price history our 10-minute average uses. What differs is how a pool is looked up, by tick spacing rather than fee tier, and that Aerodrome's fees move with market conditions. A small adapter contract, about forty lines with no owner and no settings, presents Aerodrome to the Dust contracts in the shape they expect. Only pools created by Aerodrome's own factories can ever come back from it. The four core contracts stayed untouched; the adapter is the one new piece, and it is small enough to read in a minute.

**Coinbase tokenized stocks are part of the chain.** On Base the stock tokens are not ordinary contracts. They are built into the Base node itself, a standard Coinbase calls B20. To a wallet or to Dust they behave like any ERC-20, and a vault or a pool can hold them like any other token. The issuer keeps the powers you would expect: it can block an address, pause transfers, and burn a blocked balance. Dust checks nothing the issuer does not, and skips a leg the issuer has frozen rather than fail the sweep. That is the Base form of issuer risk, and it is a property of the asset, not of Dust.

**A share multiplier.** Like Robinhood's Stock Tokens, a Coinbase stock token can carry a multiplier that changes on corporate actions such as dividends. The raw balance in your vault does not change; the number of shares it represents does. The app shows the share count.

**AERO is on the menu.** Aerodrome is the venue every Base round-up flows through, so its token is listed as a partner asset. Your basket can hold it alongside the stocks, or not; it is your choice, like every other weight.

## How a sweep stays honest

As on Robinhood Chain, because it is the same code: each buy is floored at the pool's own 10-minute average price less 3%, computed inside the contract, and the keeper's inputs are pinned into the transaction so a stale quote reverts instead of filling badly. Every launch pool carries hours of price history, checked before it was listed.

## The caveats

Coinbase tokenized stocks are offered outside the United States only, and eligibility follows Coinbase's rules and your local law. Dust cannot extend that.

Aerodrome's fees are dynamic. That is good for execution most of the time and it is why the contracts read the fee live rather than remembering it.

Like every chain, Base has lookalike tokens. Your basket only ever holds the assets the sweeper lists onchain, and the list is curated.

## Where the Base deployment stands

The contracts are deployed to Base mainnet, the keeper runs on production infrastructure, and the full loop was verified against live Base state before deploy: a USDC round-up captured, swept into four tokenized stocks and AERO through Aerodrome pools at the pinned price, and withdrawn. It sits behind the same capped, invite-only beta as everything else. Race to Roundup scores Robinhood Chain only. The [roadmap](roadmap.md) has the current status.

## Four chains, one product

Robinhood Chain for Robinhood's Stock Tokens, Base for Coinbase's tokenized stocks through Aerodrome, Solana for xStocks, Arc for dollar-native spending. Switching is a toggle in the app, and the rules are the same everywhere: pick a basket, let your spare change buy it, withdraw whenever you want, and nobody but you can move your funds.
