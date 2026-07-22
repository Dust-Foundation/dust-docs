# Security

Security claims in crypto are cheap, so this page sticks to things that are checkable: what is enforced by code, what is verified by third parties, and what our own powers are limited to.

## The design limits the damage first

The most important security property of Dust is the one described in [Wallets and custody](wallets-and-custody.md): the protocol never has broad access to user funds. The sweeper's permission is scoped to round-up amounts in one token with a per-period cap. A total compromise of Dust's backend (assume the worst: an attacker controls our servers and our session keys) could at most sweep users' capped round-up amounts into their own vault positions, from which the users can withdraw. That is a bad day, not a wipeout. We consider "what does the attacker get if they fully own us" the honest starting point for security design, and we built so the answer is small.

## Audits and review

The contract suite goes through professional third-party audit before any mainnet deployment that touches real funds, and the reports are published in full, findings included, not summarized into a badge. Between audit rounds, the suite runs a continuous fuzzing and invariant-testing campaign; the invariants include "vault shares always redeem for the underlying assets" and "no path exists for sweeper funds to reach a non-vault address."

A public bug bounty runs from mainnet day one, with payouts scaled to severity and to the value the protocol holds. Details and scope live on the bounty page linked in the app.

## Admin powers, enumerated

Here is everything the Dust team can do to the live protocol, in total:

- Change basket composition and weights: through a multisig, behind a public timelock, visible before it takes effect.
- Change the fee rate: same multisig, same timelock, same visibility.
- Pause the sweeper: immediate, because pausing is protective. A pause stops new round-ups from being collected. It cannot stop withdrawals.

And everything we cannot do: we cannot withdraw or transfer user assets, cannot exceed any user's cap, cannot freeze a user's vault, cannot block withdrawals, and cannot upgrade contracts out from under you silently. Admin keys are held by a multisig; no single person, including the founder, can execute an admin action alone.

The pause deserves one more sentence, because "pausable" scares people who have been rugged before. Our pause policy is written and published: what triggers a pause (an active exploit, a critical oracle failure, an issuer halt on Stock Tokens), who decides, and the guarantee that withdrawal paths stay open while paused. If we ever pause, you can leave during the pause. That property is tested, not aspirational.

## What we monitor

Sweep failures, price-feed staleness, vault invariant checks on every block, and sequencer status on the underlying chain. Incidents get a public status page and a written postmortem. We won't pretend incidents will never happen; we'll commit to you finding out from us, quickly, rather than from a thread of screenshots.
