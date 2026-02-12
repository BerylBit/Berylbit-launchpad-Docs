# Parameter Reference

These parameters are per-market configurable (subject to protocol bounds).

## Volume gating
- `V_min_low`: min volume to allow action at low cap/low liquidity
- `V_min_mid`: min volume at mid cap ranges
- `V_min_high`: min volume at higher cap ranges

Example:
- if cap between 2k–10k → trigger only if buys/volume exceed a small threshold
- if cap between 11k–20k → higher threshold
- scaling continues upward

## Cooldown
- `cooldown_secs`: minimum time between accepted actions
Example: 30–120 seconds

## Max impact
- `impact_max_bps`: hard cap for allowed action impact
Example: 100 bps (1%)

## Max size
- `max_action_usd`: hard cap on action size per interval

## Capture ratio
- `alpha`: proportion of observed volume used in sizing
Example: 1%–30% depending on conditions

## Emergency guards
- `pause_actions`: emergency stop
- `cap_only_mode`: restrict actions to conservative mode
