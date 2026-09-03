---
cover: .gitbook/assets/covers/faq-v3.png
coverY: 0
---

# FAQ

**Is my money held by Dust?**
No. Assets stay in your own wallet and your vault position. Dust holds one narrow permission, and only if you turn on Capture Everywhere: pulling your round-up change under a weekly cap, into your own vault position. You revoke it in one tap. If Dust vanished, you could withdraw everything without us.

**Which chain does Dust run on?**
Robinhood Chain is home, and these docs describe that version first. Dust is also deployed on Solana; [Also on Solana](solana.md) explains what differs there. You switch chains in the app.

**How big are round-ups, really?**
As big as your trading. Someone who makes 40 swaps a month at nearest-dollar rounding invests roughly $20 a month on average; a 2x multiplier doubles that. It's meant to be small enough that you never feel it and steady enough that it adds up. The app shows your monthly run rate after a couple of weeks.

**Can I turn it off?**
Any time, instantly, from the app or from your wallet directly. Your vault keeps working when round-ups are off, and withdrawals are never gated on anything.

**Do I actually own Nvidia shares?**
You own Stock Tokens that track the price. Not shares, no voting rights, and your claim is on the issuer, which can also pause the token or block an address. The [basket page](the-basket.md) explains all of that without marketing gloss, because it matters. On Solana the equivalent is an xStock, issued by Backed.

**Can I round up if I only hold ETH, not USDG?**
Swaps inside the app are USDG swaps, so those round-ups come from USDG. For capturing outside activity, Capture Everywhere can be funded from USDG, from WETH, or from a small ETH float you park in the Capture contract. All three are live. The [custody page](wallets-and-custody.md) has the details. On Solana, round-ups can be funded from SOL as well as USDC.

**What happens if an investment fails?**
Nothing bad. Each leg either completes or doesn't happen. A failed leg (thin pool, a stale quote, a Stock Token its issuer has paused) is skipped and its USDG goes back to your accrued balance, to be retried on a later pass. Your round-up sits in your own vault in the meantime, not in limbo, and you can withdraw it whenever.

**What does Dust cost?**
A percentage of each round-up, 1% at launch, taken only when it's actually invested, shown before you enable the feature and on every receipt. Capped in code at 5%. No deposit, withdrawal, or management fees, and no hidden spread. The [fees page](fees.md) has the arithmetic.

**I live in the US. Can I use Dust?**
Stock Tokens are not offered in the US, and neither are xStocks, so no, not today. This follows from the issuers' rules, not ours. If that changes, these docs will change.

**Is it safe? Has it been audited?**
The contracts are deployed on Robinhood Chain mainnet and the full loop has been verified against live mainnet state, but they have not yet had their external audit, which is the gate before public launch. The same is true of the Solana program. We won't invite other people's money before that's done and published. The [security page](security.md) and [roadmap](roadmap.md) are straight about where things stand.

**Why would a trader want this? I can already buy stocks.**
You can. Do you? The product isn't for the disciplined version of you that logs into a brokerage every month. It's for the actual you, mid-trade at 2 a.m. The honest pitch is that Dust converts behavior you already exhibit into investing you already know you should do.

**What's the minimum to start?**
There isn't one. The first round-up can be 30 cents. That's rather the point.
