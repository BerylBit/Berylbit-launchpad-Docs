# Bot & MEV Defense

Bots are not “bad” by default — but uncontrolled extraction harms users and kills charts.

Berylbit is designed to reduce value leakage via:

## 1) Bounded execution rules
- max impact per action
- cooldowns
- min volume thresholds
- reject extreme patterns when needed

## 2) Reduce “free arbitrage”
Large discontinuities and thin liquidity create easy arb.
Berylbit aims to reduce discontinuity and improve launch legibility.

## 3) Keep value inside the chart
In most markets, value leaks to:
- MEV backrunning
- sandwiching
- toxic flow that extracts from normal traders

Berylbit aims to make launch mechanics and transitions less exploitable.

> Exact defense methods are implementation-dependent and are enforced on-chain.
