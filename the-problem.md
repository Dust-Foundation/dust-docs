# The problem

Almost nobody in crypto invests. That sounds wrong, so let us be precise: people in crypto trade constantly, but very few accumulate anything that compounds. The average active wallet makes dozens of swaps a month and ends the year holding whatever its last trade left behind.

Meanwhile the boring answer, buying a little of the market on a schedule and not touching it, is the single most reliable wealth-building behavior we know of. Everyone agrees on this. Almost no one does it, because it requires the one resource traders don't spend on the future: attention.

## Round-ups solved this once already

Acorns proved the model in traditional finance. Link a card, round up your purchases, sweep the change into an index portfolio. Millions of people who never managed to "start investing" ended up with real portfolios, because the product removed the decision entirely. The money moved when they weren't looking, in amounts too small to miss.

Nobody has built this onchain. That is not for lack of trying:

- Coinseed rounded up card purchases into crypto. It held customer funds, marked up prices without disclosure, and was sued by the SEC and the New York Attorney General on the same day in 2021. A court shut it down permanently and entered a $3 million judgment.
- Bundil pitched itself as "Acorns for crypto" on Shark Tank. Users reported broken withdrawals. It shut down in early 2023.
- Donut offered simple savings with DeFi yield. The yield came from a centralized lender, Genesis, and when Genesis failed in late 2022, Donut froze withdrawals.

Read those three stories again and notice what they share. Every one of them was custodial. The company held the money, and the company became the point of failure: legally, operationally, or both. The round-up idea never failed. The custody did.

## Why it's buildable now

Two things changed. First, real assets arrived onchain: tokenized blue-chip stocks now trade 24/7 against stablecoins on public blockchains, with self-custody. Second, wallets became programmable. A modern smart account can grant an app a narrow, standing permission ("you may move my round-up change, only into my basket, up to this cap, and I can revoke you anytime") without ever handing over keys or funds. In 2021 that primitive did not exist in any usable form. In 2026 it is production infrastructure.

Put those together and the Acorns model finally works without the fatal ingredient. No company holds your money. The rules are enforced by your own wallet and by contracts anyone can read. Dust is that product.

Onchain trading generates more "spare change" per user than card spending ever did. A person who swaps a few times a week produces round-ups constantly, from activity they were going to do anyway. Dust just refuses to let that change evaporate.
