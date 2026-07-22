# FAQ

**Is my money held by Dust?**
No. Assets stay in your own wallet and vault position. Dust holds one narrow permission: moving your round-up change (only USDG, only into your basket, under your cap), and you can revoke it in one tap. If Dust vanished, you could withdraw everything without us.

**How big are round-ups, really?**
As big as your trading. Someone who makes 40 swaps a month at nearest-dollar rounding sweeps roughly $20 a month on average; a 2x multiplier doubles that. It is meant to be small enough that you never feel it and steady enough that it adds up. The app shows your monthly run rate after a couple of weeks.

**Can I turn it off?**
Any time, instantly, from the app or (for external wallets) from your wallet directly. Your vault keeps working when round-ups are off, and withdrawals are never gated on anything.

**Do I actually own Nvidia shares?**
You own Stock Tokens that track the price. Not shares, no voting rights, and your claim is on the token's issuer. The [basket page](the-basket.md) explains the difference without marketing gloss, because the difference matters.

**What happens if a sweep fails?**
Nothing bad. Sweeps are atomic: they either complete or don't happen. A failed sweep (thin market, stale price feed, chain congestion) is retried later. Your round-up sits in your own account in the meantime, not in limbo.

**Why USDG-only round-ups at launch?**
Rounding up a stablecoin amount is exact. Rounding up a volatile-token swap requires trusting a price oracle at the moment of the swap, which we'd rather ship carefully than quickly. It's on the roadmap.

**What does Dust cost?**
A percentage of each round-up, shown before you enable the feature and on every sweep. No deposit, withdrawal, or management fees, and no hidden spread. The [fees page](fees.md) has the arithmetic.

**I live in the US. Can I use Dust?**
Stock Tokens are not offered in the US, so no, not today. This follows from the issuer's rules, not ours. If that changes, these docs will change.

**Why would a trader want this? I can already buy stocks.**
You can. Do you? The product isn't for the disciplined version of you that logs into a brokerage every month. It's for the actual you, mid-trade at 2 a.m. The honest pitch is that Dust converts behavior you already exhibit into investing you already know you should do.

**What's the minimum to start?**
There isn't one. The first round-up can be 30 cents. That's rather the point.
