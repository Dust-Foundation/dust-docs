# How to use Dust

This is the long version of [Getting started](getting-started.md): every screen, every transaction you will be asked to sign, what each one does onchain, and what to expect afterwards. It describes Dust on Robinhood Chain, which is where Dust lives. If you are on Solana, the flow is close but the details differ, and [Also on Solana](solana.md) covers them. On Arc the flow is this one exactly, with two differences: the basket holds cirBTC rather than Stock Tokens for now, and round-ups are paid from USDC only. [Also on Arc](arc.md) has the specifics.

Nothing here requires trusting us with your money. Every step is a transaction from your own wallet, and every permission you grant is capped and revocable. If a step ever asks you to send funds to an address to "activate" something, close the tab. That is not Dust.

## Before you start

You need three things.

**A wallet that speaks EVM.** MetaMask, Rabby, Coinbase Wallet, or any wallet that can add a custom network. Dust never sees your seed phrase and never asks for it.

**Robinhood Chain added to that wallet.** The app offers to add it for you when you connect. If you prefer to add it by hand, these are the network details:

| Field | Value |
|---|---|
| Network name | Robinhood Chain |
| Chain id | 4663 |
| Currency | ETH |
| RPC | https://rpc.mainnet.chain.robinhood.com |
| Explorer | https://robinhoodchain.blockscout.com |

**Something in the wallet.** A little ETH for network fees (transactions on Robinhood Chain cost a fraction of a cent, so a few dollars of ETH lasts a long time), and the money you want your round-ups to come from. Dust works with USDG, the dollar stablecoin on Robinhood Chain, and with ETH, either as plain ETH or wrapped as WETH. You do not need all three. Most people bridge or buy a small amount of USDG, or simply use the ETH they already hold.

Dust is not yet open to the public. The steps below describe the app as built, and they are the same steps testers use today.

## Step 1: connect

Open the app at https://app.roundupdust.com. That is the only official address; bookmark it rather than following links from posts or messages. The network pill at the top right says Robinhood; that is the default, so you should not have to touch it. Tap **Connect wallet** and pick your wallet. On a phone without a wallet extension, pick **WalletConnect** and scan the code with your wallet app, or open the page from inside the wallet app's browser.

If your wallet is on another network, the app shows a **Switch to Robinhood Chain** button. Tap it and approve the switch. Until you do, the app cannot read your balances, so nothing else appears.

Nothing has been signed onchain yet. Connecting only tells the app which address to read.

## Step 2: what your change buys

A new wallet gets two setup screens. The first asks what your spare change should buy. This is yours to decide. Nobody at Dust picks stocks for you, and the contract that does the buying is written so that nobody at Dust can change your choice later.

Pick a mix or build your own:

- **The market**: half SPY, half QQQ.
- **Big tech**: NVDA, AAPL, MSFT, GOOGL, AMZN and META, evenly.
- **A bit of everything**: every Stock Token on the menu, evenly. Twenty today: TSLA, NVDA, AAPL, AMZN, SPY, MSFT, GOOGL, META, NFLX, AMD, PLTR, QQQ, GLD, SPCX, MSTR, MU, COST, LLY, CRCL and HIMS.
- **Build my own**: add the stocks you want with **Add a stock** and drag each slider. The others adjust so the total is always 100 percent. You never have to do the arithmetic.

The menu today is Stock Tokens only. When other kinds of assets are listed they appear in their own sections of **Add a stock**: real-world assets, where the token represents exposure to something like an apartment and the app says so plainly, and microcaps, which you pick yourself and which the app caps at 10 percent of a basket. Round-ups are never routed into either automatically.

Tap **Save and continue**. Your wallet asks you to sign one transaction. It records your basket in the DustSweeper contract under your address, and it is the only way a basket is ever set. It costs a fraction of a cent in ETH.

You can change the basket any time from the **Basket** tab. A change applies to future buys only. Stock Tokens you already hold in your vault stay exactly as they are.

## Step 3: let Dust collect your change

The second setup screen turns on round-ups. Instead of rounding up only what you buy inside the app, the keeper watches your wallet's activity on Robinhood Chain and rounds up what you spend anywhere else: a swap on a DEX, a purchase, an ETH transfer. You stay in control through two limits that live onchain, in a contract with no owner and no pause switch.

**Weekly limit.** Pick $5, $10 or $25 a week, or type your own, and tap **Set**. One transaction. This is the most Dust can ever collect in any seven-day window, across every source combined. A limit of zero means off.

**Paid from.** The app looks at what your wallet holds and leads with the simplest option:

- If you hold USDG, it asks you to **Allow** Dust to use up to your weekly limit of USDG for round-ups. A standard token permission, visible and removable in your wallet like any other.
- If you hold ETH and no USDG, it asks you to **Set aside** a little ETH. The ETH sits in the DustCapture contract credited to your address, and round-ups are drawn from it under a price guard: the contract refuses any price worse than the pool's ten-minute average plus 2 percent. **Take back** returns it to your wallet in one transaction, in every state.

**Other ways to pay** folds out the rest: allowing WETH, or adding a second source as a fallback. Round-ups come out of USDG first, then WETH, then the ETH you set aside. The weekly limit covers all of them together.

You can **Skip for now** and turn round-ups on later from the **Round-ups** tab. Until you do, nothing is collected and Home says so.

**What counts as a spend.** The keeper reads your transactions and asks what you gave up: USDG that left your wallet, or ETH that left your wallet (plain ETH and WETH are counted as one asset, so wrapping or unwrapping is never a spend). Within one transaction, each asset is netted against itself, so a swap that routes through several pools counts once, and a refund cancels out. Selling something for USDG is not a spend. Transactions with Dust's own contracts never count. ETH spends are valued in dollars at the pool price at the time.

**How the round-up is computed.** Each spend is rounded up to the next whole dollar. Spend $18.40 and the round-up is $0.60. Spend 0.02 ETH worth $50.15 and the round-up is $0.85. The keeper adds these up and collects them, usually within a minute of the transaction, bounded by your limit and by what your sources can cover.

**When it cannot collect.** If your weekly limit is used up, or no source has enough, the round-up is skipped. Dust does not keep a tab. There is never a balance owed, and nothing catches up later without your say.

**Turning it off.** The switch at the top of the **Round-ups** tab, or **Turn round-ups off** at the bottom, sets your limit to zero in one transaction. Whatever you allowed or set aside stays put until you remove it, each as its own transaction, so you can leave nothing granted. You can also remove the permissions from your wallet's own approvals screen without opening Dust.

### Adding money on a schedule

Round-ups only add what your trading produces. If you want a steady amount going in as well, the **Basket** tab has **Add on a schedule** under your basket: pick an amount ($10, $25, $50 or your own), how often (daily, weekly, every two weeks, monthly) and the first date. Saving it is a signature, not a transaction.

On each due date the keeper takes that amount of USDG from your wallet into your vault, through exactly the same contract path and under exactly the same weekly limit as round-ups. If the deposit plus your round-ups would not fit under the limit, the app asks you to raise the limit first, one transaction, before it lets you save the schedule. Dust never gains a second permission for this. The weekly limit and your USDG allowance are the whole of it, and both are yours to change or remove.

A deposit that cannot be covered is skipped, not retried: not enough USDG in the wallet, an allowance below the limit, or no room left under the limit that week. The card shows each skip with its reason. There are no partial deposits and nothing is caught up later. The money buys your basket at whatever weights it has at the time.

**Pause**, **Skip next**, **Edit** and **Cancel deposits** are each one tap plus a signature. Home shows the schedule next to your spare change with the next date and what it adds up to over a year.

## Step 4: Home

After setup, the app has four tabs: **Home**, **Basket**, **Round-ups** and **More**. On a phone they sit along the bottom of the screen.

Home shows the one number that matters, what your spare change is worth today, with how much change went in and the difference. Under it, status lines tell you whether round-ups are on and how much of this week's limit is left, what your basket buys, and your scheduled deposit if you have one. Tap any line to change it.

**Buy a stock** opens a small panel for buying a Stock Token with USDG inside the app, with a round-up attached. Choose the stock and how much to pay. The panel shows what you receive, quoted from the live pool, the change that goes into your basket, and the total from your wallet. **Options** folds out the details most people never touch: round up to the nearest $1 or $5, invest extra (1x, 2x or 10x the change), and price protection, which cancels the buy if the price moves more than the chosen percentage before it lands. If it is your first purchase, your wallet first asks you to approve USDG spending for the DustRouter contract; that approval is for the total shown, not unlimited.

**Invest now** appears when change is waiting in your vault. It does what the keeper does on its own schedule, described in step 5, signed by you instead.

**What you hold** lists each Stock Token in your vault with your share count. **Recent** is your last few round-ups and buys, in plain sentences, each with a link to the transaction.

## Step 5: investing the change

Change collects in your vault as USDG. On a schedule, the keeper invests it: it takes your waiting USDG and buys your basket with it, in your weights, from the Uniswap pools on Robinhood Chain. Very small amounts may wait until they add up.

Three things to know:

- **The fee is taken here and only here.** Dust charges 1 percent of the amount invested. Nothing on purchases, nothing on withdrawals, nothing on balances. The fee is capped at 5 percent in the contract code, so it can never quietly become something else. [Fees](fees.md) has the detail.
- **It is deterministic.** The same amount and the same basket give the same buys every time. The keeper supplies a minimum acceptable price per stock derived from the pool's recent average, and the contract rejects any fill below it.
- **A bad leg never breaks it.** If a Stock Token is paused by its issuer, or its pool is too thin, that stock is skipped and its share of the USDG stays in your vault. The others still buy.

Afterwards, Home shows the Stock Tokens you now hold, valued at today's prices, against the spare change that went in. That is the number to watch over months, not days.

## Step 6: More

Everything occasionally needed lives under **More**.

**Withdraw** moves a Stock Token from the vault to your wallet, in kind, or returns change that has not been invested yet as USDG. Both work at any time. There is no lockup, no pause on withdrawals, and no one who can freeze your balance. The one thing outside our control is a Stock Token the issuer has paused; an in-kind withdrawal of that token waits until they unpause it, and your other holdings are unaffected. [Risks and disclosures](risks-and-disclosures.md) covers this. ETH you set aside is taken back from the **Round-ups** tab.

**Stop investing my change** clears your basket onchain. Nothing is invested until you save a new one. What is in your vault stays yours, and round-ups keep being collected unless you turn them off too.

More also holds your share card, your full activity list, the network picker, the Race to Roundup card while the race runs, and links to these docs.

## What it costs

- Network fees on Robinhood Chain: a fraction of a cent per transaction, paid in ETH from your wallet. The keeper's own transactions (pulls and sweeps) are paid by Dust, not you.
- Pool fees on each swap, set by the pool, typically 0.01 to 0.3 percent.
- Dust's fee: 1 percent of each amount swept. Nothing else.

## If something looks wrong

**The app shows nothing after connecting.** Your wallet is on another network. Use **Switch to Robinhood Chain**.

**A round-up did not appear after an outside transaction.** Give it two minutes. Then check, in order: are round-ups on, is anything allowed or set aside, is there room left this week, and was the transaction actually a spend (selling for USDG, or wrapping ETH, is not). If the price of ETH moved more than 2 percent against the ten-minute average in that moment, a WETH or float pull is postponed until the average catches up.

**Change is sitting there without being invested.** Small amounts wait until they add up, or tap **Invest now** on Home. If a Stock Token in your basket was paused by its issuer, that stock is skipped and its share stays as waiting change. That is by design.

**You want everything out.** Turn round-ups off, remove what you allowed, take back any ETH you set aside, then withdraw each Stock Token and your waiting change under More. Five minutes, all from your own wallet, no request to us needed.

**You want to check what you granted.** Open your wallet's token approvals view for Robinhood Chain. Dust appears as approvals to the DustRouter (purchases) and DustCapture (round-ups) contracts, each capped at the amount you set. The addresses are listed in [Security](security.md).

## What Dust can never do

Move funds anywhere except into your own vault position. Collect more than your weekly limit. Change your basket. Charge more than the fee cap in the code. Freeze or redirect a withdrawal. Take custody of your keys. These are not policies. They are what the contracts allow and do not allow, and you can read them onchain.
