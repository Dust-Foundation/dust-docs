# How to use Dust

This is the long version of [Getting started](getting-started.md): every screen, every transaction you will be asked to sign, what each one does onchain, and what to expect afterwards. It describes Dust on Robinhood Chain, which is where Dust lives. If you are on Solana, the flow is close but the details differ, and [Also on Solana](solana.md) covers them.

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

Open the app. The chain switcher at the top right shows Robinhood first; that is the default, so you should not have to touch it. Click **Connect wallet** and approve the connection in your wallet.

If your wallet is on another network, the app shows a **Switch to Robinhood Chain** button. Click it and approve the switch. Until you do, the app cannot read your balances, so nothing else appears.

Nothing has been signed onchain yet. Connecting only tells the app which address to read.

## Step 2: build your basket

The first thing Dust asks is what your spare change should buy. This is yours to decide. Nobody at Dust picks stocks for you, and the contract that does the buying is written so that nobody at Dust can change your choice later.

You see the menu of Stock Tokens available on Robinhood Chain. At launch it is five: TSLA, NVDA, AAPL, AMZN, and SPY. Each row has a percentage. Set them any way you like as long as they add up to 100 percent. **Split evenly** does 20 percent each. You can leave a token at zero if you do not want it.

Click **Save basket**. Your wallet asks you to sign one transaction. It records your basket in the DustSweeper contract under your address, and it is the only way a basket is ever set. It costs a fraction of a cent in ETH.

You can come back and change the basket any time. A change applies to future sweeps only. Stock Tokens you already hold in your vault stay exactly as they are.

## Step 3: round up a purchase inside Dust

With a basket saved, the main screen appears: your vault at the top, then **Buy Stock Tokens**, then **Withdraw**, then **Capture everywhere**.

The **Buy Stock Tokens** panel is a swap with a round-up attached. You choose which Stock Token to buy under **I want to buy**, and how much USDG to spend under **Paying**. Then two choices that only affect the change:

- **Round up to nearest**: $1 or $5. Spending $61.30 rounded to the nearest dollar leaves $0.70 of change; rounded to the nearest $5, $3.70.
- **Invest extra**: 1x, 2x, or 10x. The multiplier applies to the change, not the purchase. At 10x, that $0.70 becomes $7.00.

The panel shows **You receive about** (the Stock Tokens you get, quoted from the live Uniswap pool), the change it will invest for you, and **Total from your wallet**, which is the purchase plus the change. A **Max slippage** setting protects the purchase leg. If the amount already ends on a whole dollar, the panel says so and there is no change this time.

Click the buy button and sign. If it is your first purchase, your wallet first asks you to approve USDG spending for the DustRouter contract; that approval is for the total shown, not unlimited. Then one transaction does two things: it swaps your USDG for the Stock Token, which lands directly in your wallet, and it moves the change into your vault as accrued USDG, credited to your address.

The purchase is yours immediately. The change waits in the vault for the sweep, covered in step 5.

## Step 4: turn on Capture everywhere

This is the part that makes Dust work in the background. Instead of rounding up only what you buy inside the app, the keeper watches your wallet's activity on Robinhood Chain and rounds up what you spend anywhere else: a swap on a DEX, a purchase, an ETH transfer. You stay in control through two limits that live onchain, in a contract with no owner and no pause switch.

**Set your weekly cap.** Under **Capture everywhere**, enter a dollar amount and click **Set weekly cap**. One transaction. This is the most the keeper can ever pull in any seven-day window, across every funding source combined. Start small, $5 or $10, and raise it later with **Update cap** if you want. A cap of zero means off.

**Fund your round-ups.** A cap alone does nothing; the status reads "Cap set, nothing funded yet." Pick at least one source. You can use more than one, and the keeper tries them in this order:

1. **USDG allowance.** Approve the DustCapture contract to spend USDG from your wallet, up to an amount you choose. Standard token approval, visible and revocable in your wallet like any other. Round-ups are pulled from your USDG balance.
2. **WETH allowance.** For people who hold ETH rather than dollars. Click **Approve WETH**; the app suggests an amount worth about 1.25 times your weekly cap at the current price, and you can change it. When a round-up is due, the contract takes exactly the round-up's worth of WETH from your wallet and swaps it into USDG on the WETH/USDG pool, straight into your vault. The contract refuses any price worse than the pool's ten-minute average plus 2 percent, so nobody, including us, can run that swap at a bad price.
3. **ETH float.** For people who hold plain ETH and do not want to wrap it. Enter an amount and click **Deposit ETH**. The ETH sits in the DustCapture contract credited to your address, and the keeper draws round-ups from it under the same price guard. It is yours the whole time: **Withdraw all** returns it to your wallet in one transaction, in every state, cap or no cap. The app leaves a little ETH in your wallet for gas when you deposit.

The panel shows your **Weekly cap**, **Left this week**, your **ETH float** balance, and each allowance.

**What counts as a spend.** The keeper reads your transactions and asks what you gave up: USDG that left your wallet, or ETH that left your wallet (plain ETH and WETH are counted as one asset, so wrapping or unwrapping is never a spend). Within one transaction, each asset is netted against itself, so a swap that routes through several pools counts once, and a refund cancels out. Selling something for USDG is not a spend. Transactions with Dust's own contracts never count. ETH spends are valued in dollars at the pool price at the time.

**How the round-up is computed.** Each spend is rounded up to the next whole dollar. Spend $18.40 and the round-up is $0.60. Spend 0.02 ETH worth $50.15 and the round-up is $0.85. The keeper adds these up and pulls them, usually within a minute of the transaction, bounded by your cap and by what your funding sources can cover.

**When it cannot pull.** If your weekly cap is used up, or no funding source has enough, the round-up is skipped. Dust does not keep a tab. There is never a balance owed, and nothing catches up later without your say.

**Turning it off.** **Turn off capture everywhere** sets your cap to zero in one transaction. The app then offers to revoke each allowance and withdraw your float, each as its own transaction, so you can leave nothing granted. You can also revoke the allowances from your wallet's own approvals screen without opening Dust.

## Step 5: the sweep

Change collects in your vault as accrued USDG. On a schedule, the keeper sweeps it: it takes your accrued USDG and buys your basket with it, in your weights, from the Uniswap pools on Robinhood Chain. Very small amounts may wait until they add up to a sweep-sized sum.

Three things to know about a sweep:

- **The fee is taken here and only here.** Dust charges 1 percent of the amount swept. Nothing on purchases, nothing on withdrawals, nothing on balances. The fee is capped at 5 percent in the contract code, so it can never quietly become something else. [Fees](fees.md) has the detail.
- **It is deterministic.** The same accrued amount and the same basket give the same buys every time. The keeper supplies a minimum acceptable price per leg derived from the pool's recent average, and the contract rejects any fill below it.
- **A bad leg never breaks the sweep.** If a Stock Token is paused by its issuer, or its pool is too thin, that leg is skipped and its share of the USDG goes back to your accrued balance. The other legs still buy.

After a sweep, your vault shows the Stock Tokens you now hold, with your cost basis, which is the spare change that went in. That is the number to watch over months, not days.

## Step 6: your vault

**Your vault** at the top of the screen lists each Stock Token you hold and the USDG waiting to be swept. Everything in it is credited to your address in the DustVault contract, a per-user ledger with no pooled shares and no owner power over balances.

**Withdraw** gives you two kinds of buttons. Withdraw a Stock Token, and the tokens move from the vault to your wallet, in kind. You then hold them like any other token on Robinhood Chain and can sell them wherever they trade. Withdraw your accrued USDG, and the unswept change comes back to your wallet as USDG. Both work at any time. There is no lockup, no pause on withdrawals, and no one who can freeze your balance. The one thing outside our control is a Stock Token the issuer has paused; an in-kind withdrawal of that token waits until they unpause it, and your other holdings are unaffected. [Risks and disclosures](risks-and-disclosures.md) covers this.

Your ETH float, if you deposited one, is withdrawn from the **Capture everywhere** panel, not here.

## What it costs

- Network fees on Robinhood Chain: a fraction of a cent per transaction, paid in ETH from your wallet. The keeper's own transactions (pulls and sweeps) are paid by Dust, not you.
- Pool fees on each swap, set by the pool, typically 0.01 to 0.3 percent.
- Dust's fee: 1 percent of each amount swept. Nothing else.

## If something looks wrong

**The app shows nothing after connecting.** Your wallet is on another network. Use **Switch to Robinhood Chain**.

**A round-up did not appear after an outside transaction.** Give it two minutes. Then check, in order: is your weekly cap set above zero, is anything funded, is there room left this week, and was the transaction actually a spend (selling for USDG, or wrapping ETH, is not). If the price of ETH moved more than 2 percent against the ten-minute average in that moment, a WETH or float pull is postponed until the average catches up.

**Accrued USDG is sitting there without a sweep.** Small amounts wait until they add up. If a Stock Token in your basket was paused by its issuer, its leg is skipped and that share returns to accrued, so you may see USDG reappear after a sweep. That is by design.

**You want everything out.** Turn off capture (cap to zero), revoke allowances, **Withdraw all** on the float, then withdraw each Stock Token and your accrued USDG. Five minutes, all from your own wallet, no request to us needed.

**You want to check what you granted.** Open your wallet's token approvals view for Robinhood Chain. Dust appears as approvals to the DustRouter (purchases) and DustCapture (round-ups) contracts, each capped at the amount you set. The addresses are listed in [Security](security.md).

## What Dust can never do

Move funds anywhere except into your own vault position. Pull more than your weekly cap. Change your basket. Charge more than the fee cap in the code. Freeze or redirect a withdrawal. Take custody of your keys. These are not policies. They are what the contracts allow and do not allow, and you can read them onchain.
