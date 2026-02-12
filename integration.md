# Integration Guide

## Who integrates with Berylbit?
- frontends (launch UX)
- analytics dashboards
- bots/keepers for monitoring and triggering actions
- partner launchpads that want to integrate Berylbit mechanics via licensing

## How to integrate (high level)
1) Install the SDK
2) Configure RPC + Program ID
3) Read protocol state (markets, configs)
4) Build UI or automation

SDK: https://github.com/BerylBit/Launchpad-sdk

## Typical integration paths
- UI: market list, launch facts, buy/sell, graduation status
- Keeper: monitor volume and call bounded vault action
- Analytics: market health, migration conditions, volume windows
