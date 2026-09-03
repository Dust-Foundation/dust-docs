---
cover: .gitbook/assets/covers/security-v3.png
coverY: 0
---

# Security

Security claims in crypto are cheap, so this page sticks to things that are checkable: what is enforced by code, what is verified by third parties, and what our own powers are limited to.

## The design limits the damage first

The most important security property of Dust is the one described in [Wallets and custody](wallets-and-custody.md): the contracts never have broad access to user funds. Capture permissions are scoped to round-up amounts under a per-user weekly cap, and the keeper holds no key that can move anything beyond that. Assume the worst: an attacker fully controls our servers and our keeper's key. The most they could do is sweep users' accrued change into those users' own baskets, and pull users' capped round-ups into those users' own vault positions, from which the users withdraw. They cannot redirect a pull, because the Capture contract sends to exactly one destination, the vault, credited to the same user the money came from. They cannot overpay with a user's ETH, because the contract bounds every WETH swap to the pool's 10-minute average plus 2 percent. They cannot reach anything the vault holds, because the vault has no function that moves funds anywhere but back to their owner. That is a bad day, not a wipeout. We consider "what does the attacker get if they fully own us" the honest starting point, and we built so the answer is small.

## Audits and review

The Robinhood Chain contracts are new Solidity, and they go through professional third-party audit before any public launch that invites other people's money. The report is published in full, findings included, not summarized into a badge. We say this plainly because it is the current gate: the contracts are deployed to mainnet and the full loop has been verified against live mainnet state, and until that audit is done and its findings resolved, Dust stays pre-public. The Capture Everywhere funding paths for WETH and ETH are new code, so the audit scope covers them too. The Solana program is separate new code in Rust, and it sits behind the same gate.

A public bug bounty runs from public launch, with payouts scaled to severity and to the value the protocol holds. Details and scope live on the bounty page linked in the app.

## Admin powers, enumerated

Here is everything the Dust team can do to the live protocol on Robinhood Chain, in total. All of it lives in the sweeper contract:

- Curate the Stock Token menu: list or delist which Stock Tokens users can choose from. This never touches an existing user's holdings. A delisted token is simply skipped in future sweeps, and anything you already hold in it stays withdrawable.
- Change the fee rate: within the 5% ceiling fixed in the contract's code, visible onchain.
- Set the keeper and treasury addresses, and a minimum sweep size.
- Pause new sweeps: immediate, because pausing is protective. It stops new investing. It cannot touch the vault or withdrawals.

The other three contracts have less. The router has no admin functions at all. The Capture contract has no owner and no pause; its rules cannot be changed by anyone after deployment. The vault has no pause, and its owner has no power over any balance.

And everything we cannot do: we cannot withdraw or transfer user assets, cannot exceed any user's cap, cannot freeze a user's vault, cannot block withdrawals, and cannot change the rules retroactively. Before public launch, ownership of the sweeper and the treasury address move to a multisig, so no single person, including the founder, can act alone. On Solana, the admin role and the program's upgrade authority move to a multisig the same way, or the upgrade authority is burned to make the program immutable. Where we are in that process is on the [roadmap](roadmap.md).

The pause deserves one more sentence, because "pausable" scares people who have been rugged before. A pause stops new sweeps; it never touches your ability to leave. If we ever pause, you can withdraw during the pause. That property is enforced by the vault, which simply has no function to gate a withdrawal of your USDG, and it is one of the specific things the audit checks.

## What we monitor

Failed sweeps, stale quotes, keeper health and balance, issuer pauses on listed Stock Tokens, and the contracts' own state. Incidents get a public status page and a written postmortem. We won't pretend incidents will never happen. We commit to you finding out from us, quickly, rather than from a thread of screenshots.
