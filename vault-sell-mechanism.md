# Vault-Sell Mechanism (Volume-Triggered)

This mechanism is designed to:
- allow creator-aligned revenue capture
- avoid per-trade user taxes
- operate safely under high volume
- remain bounded by price impact rules

## Components
- **Core program (on-chain):** enforces the rules and safety bounds
- **Vault (protocol-controlled inventory):** source of controlled actions
- **Keeper (off-chain):** monitors conditions and triggers actions

## Why off-chain keeper + on-chain enforcement
On-chain rolling volume windows are expensive and complex.

Instead:
- keeper computes volume off-chain (cheap)
- on-chain program verifies strict bounds (safe)
- protocol remains predictable, auditable, and scalable

## Trigger Conditions (examples)
Vault action may only be allowed if all conditions hold:

1) Minimum volume since last action:
`V_window >= V_min`

2) Cooldown elapsed:
`now - last_action_ts >= cooldown_secs`

3) Max price impact bound:
`impact(action_size) <= impact_max`

4) Optional market cap ranges:
`MC_min <= market_cap <= MC_max`

## Action Sizing (examples)
A simple conservative policy:

`action_size_usd = min( max_action_usd, alpha * V_window )`

Where:
- `alpha` = capture proportion for that window (ex: 0.01 to 0.30)
- `max_action_usd` = hard cap
- `V_window` = observed volume since last action

## Price Impact Safety
Define:
- `impact_max` = max allowed price impact (ex: 1%)

The on-chain program enforces that any action that would exceed `impact_max` is rejected.

## Anti-Spam / No “queued sells”
To prevent “50 triggers leading to 50 actions”:
- the program uses a **cooldown**
- and a **single state variable** `last_action_ts`
- keeper is allowed to call frequently, but the program only accepts when conditions are satisfied

Result:
- no action backlog
- no burst dumping
- stable behavior under high TPS
