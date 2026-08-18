---
cover: .gitbook/assets/covers/security-v2.png
coverY: 0
---

# Security

Security claims in crypto are cheap, so this page sticks to things that are checkable: what is enforced by code, what is verified by third parties, and what our own powers are limited to.

## The design limits the damage first

The most important security property of Dust is the one described in [Wallets and custody](wallets-and-custody.md): the program never has broad access to user funds. Capture permissions are scoped to round-up amounts under a per-user weekly cap, and the keeper holds no key that can move anything beyond that. Assume the worst: an attacker fully controls our servers and our keeper's key. The most they could do is invest users' capped round-up amounts into those users' own vaults, from which the users withdraw. They cannot redirect a swap, because the program refuses any investment where the vault didn't receive what a live quote promised. They cannot reach a stablecoin buffer users hold, because a stolen SPL delegate is still capped on every pull, and a Squads spending limit is enforced by Squads, not by us. That is a bad day, not a wipeout. We consider "what does the attacker get if they fully own us" the honest starting point, and we built so the answer is small.

## Audits and review

The Solana program is a new codebase in Rust, and it goes through professional third-party audit before any public launch that invites other people's money. The report is published in full, findings included, not summarized into a badge. We say this plainly because it is the current gate: the program is deployed to mainnet and proven with our own money, and until that audit is done and its findings resolved, Dust stays pre-public. New code deserves fresh eyes, and adding the SOL-capture path meant new code, so the audit scope covers it too.

A public bug bounty runs from public launch, with payouts scaled to severity and to the value the protocol holds. Details and scope live on the bounty page linked in the app.

## Admin powers, enumerated

Here is everything the Dust team can do to the live protocol, in total:

- Curate the stock menu: add or remove which xStocks users can choose from. This never touches an existing user's holdings.
- Change the fee rate: within a hard ceiling fixed in the program's code, through the admin process, visible onchain.
- Set the keeper and treasury addresses.
- Pause new investing and capture: immediate, because pausing is protective. It stops new round-ups from being collected. It cannot stop withdrawals.

And everything we cannot do: we cannot withdraw or transfer user assets, cannot exceed any user's cap, cannot freeze a user's vault, cannot block withdrawals, and cannot change the rules retroactively. Before public launch, the admin role and the program's upgrade authority both move to a multisig (or the upgrade authority is burned to make the program immutable), so no single person, including the founder, can act alone. Where we are in that process is on the [roadmap](roadmap.md).

The pause deserves one more sentence, because "pausable" scares people who have been rugged before. A pause stops new collection; it never touches your ability to leave. If we ever pause, you can withdraw during the pause. That property is enforced by the program, which simply has no instruction to gate a withdrawal, and it is one of the specific things the audit checks.

## What we monitor

Failed investments, price-quote staleness, keeper health and balance, and the program's own state. Incidents get a public status page and a written postmortem. We won't pretend incidents will never happen. We commit to you finding out from us, quickly, rather than from a thread of screenshots.
