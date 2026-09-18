# Also on Arc

Dust lives on Robinhood Chain. On September 18, 2026, two days after Circle opened Arc's mainnet, we deployed Dust there too. Arc is the chain Circle built around USDC: the dollar is native, gas is paid in USDC, and payments settle in about half a second. A round-up product that turns everyday spending into an investment belongs on a chain built for everyday spending, so Dust runs on Arc as well. Robinhood Chain stays the home and the place new features land first.

The specifics, for those who want them:

| | |
|---|---|
| What it is | Circle's Layer 1, live on public mainnet since September 16, 2026. Blocks every half second, deterministic finality |
| The dollar | USDC, native to the chain. It is both the money you spend and the gas you pay with, so there is no second token to hold |
| The assets | cirBTC, Circle's Bitcoin, for now. See below for why that is the whole list today |
| The market | A Uniswap v3 style factory; the cirBTC/USDC pool held over six million dollars at launch |
| Wallets | MetaMask, Rabby, Phantom, Ledger. The app offers to add Arc to your wallet |
| Chain id | 5042 |
| Explorer | https://explorer.arc.io |
| Deployment | Permissionless. Anyone can deploy contracts, including us |

## What is the same

Everything that matters, and more literally than on Solana: the four contracts on Arc are the exact same audited code as on Robinhood Chain, byte for byte. Same vault that only you can withdraw from, same keeper with no discretion, same price floor on every buy, same 1% fee taken only when change is invested, same weekly cap you set and can zero out from your own wallet. The CredShields audit covers this code, and nothing was changed to ship it here. The contract addresses are in the [security page](security.md).

## What differs

**Bitcoin, not stocks, for now.** Arc is days old, and no tokenized stocks trade there yet. The only asset on Arc with deep enough liquidity to buy safely is cirBTC, Circle's Bitcoin, so that is the only thing a basket on Arc can hold today. That is where Arc is, not a limit of Dust. When an issuer brings stocks to Arc, or when EURC's market gets deep enough, adding an asset is one listing on the sweeper, no redeploy. The app says this plainly above the basket so nobody is surprised.

**USDC funds everything.** On Robinhood Chain, Capture Everywhere can draw round-ups from USDG, from WETH, or from a small ETH float. On Arc there is no ETH to speak of, and native value is USDC, so round-ups come from one place: a USDC allowance capped by your weekly limit. Simpler, and it means the two funding paths that do not apply are never offered in the app.

**Payments count, not just swaps.** Because USDC is the native currency on Arc, a plain payment, sending USDC to someone, shows up onchain the same way a swap does. The keeper rounds those up too. On Arc, "every swap" becomes "every payment and swap".

**Gas in dollars.** You never need ETH. A round-up capture costs the keeper well under a cent, and the whole set of four contracts cost about fifteen cents to deploy.

## How a sweep stays honest

Exactly as on Robinhood Chain, because it is the same code: each buy is floored at the pool's own 10-minute average price less 3%, computed inside the contract, and the keeper's inputs are pinned into the transaction so a stale quote reverts instead of filling badly. The cirBTC pool carries the full price history the floor needs; that was checked before the pool was listed.

## The caveats

cirBTC is issued by Circle and backed by Bitcoin Circle holds. It is a claim on Circle, not Bitcoin in your own custody, in the same way a Stock Token is a claim on its issuer. Circle can pause or restrict it under its terms, which is the Arc form of issuer risk, and it is a property of the asset, not of Dust.

Arc itself enforces a protocol-level blocklist on native USDC transfers. A blocked address cannot move USDC on Arc at all, in any wallet, and Dust cannot override that.

Arc is very new. Its validators are a fixed set of named institutions today, with a move to open staking announced for 2027. Fees have a floor of 20 gwei that the chain enforces; the keeper prices every transaction above it. And like any chain that is days old, its tooling, wallets and explorers are still catching up.

Lookalikes exist here already: within a day of launch there was a token on Arc calling itself NVIDIA. It is a memecoin. Your basket on Arc only ever holds the assets the sweeper lists onchain, and the list is curated, not open.

## Where the Arc deployment stands

The contracts are deployed to Arc mainnet, the keeper runs on production infrastructure, and the full loop was verified against live Arc state before deploy: a USDC round-up captured, swept into cirBTC at the pinned price, and withdrawn. It is the same audited bytecode as Robinhood Chain, so the audit gate is already passed. It sits behind the same capped, invite-only beta as everything else. Race to Roundup scores Robinhood Chain only. The [roadmap](roadmap.md) has the current status.

## Three chains, one product

Robinhood Chain for tokenized stocks, Solana for xStocks, Arc for dollar-native spending that rounds up into Bitcoin today and more as Arc grows. Switching is a toggle in the app, and the rules are the same everywhere: pick a basket, let your spare change buy it, withdraw whenever you want, and nobody but you can move your funds.
