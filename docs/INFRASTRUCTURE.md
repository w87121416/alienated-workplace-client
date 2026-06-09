# Alienated Workplace Client Infrastructure

This repository is an isolated client repository for Alienated Workplace. It must not share PlayFab Title IDs, Steam App IDs, secrets, save schemas, or deployment environments with any other project.

## Required Environments

- GitHub repository: `w87121416/alienated-workplace-client`
- PlayFab Title: dedicated title, pending console creation
- Steamworks App ID: dedicated app, pending developer console configuration
- Web deployment: GitHub Pages workflow in `.github/workflows/pages.yml`

## Login Rules

- Steam client: Steamworks Session Ticket -> PlayFab `LoginWithSteam`
- Web client: PlayFab `LoginWithCustomID` for temporary identity or `LoginWithPlayFab` for account/password identity
- Account linking: Steam identity and web identity must link to the same PlayFab primary player ID

## Data Rules

- Cloud authority: PlayFab is authoritative for inventory, wallet, unlocks, progress, and cloud saves
- Local cache: display/cache only, never authoritative
- Conflict policy: cloud revision wins; stale local data cannot overwrite cloud data
- Secrets: never commit PlayFab secret keys, Steam Web API keys, session tickets, or player tokens

## Cost Policy

Default to GitHub free hosting and PlayFab Free Tier. If concurrency, anti-cheat, audit log retention, or regional connectivity requires paid upgrades, prepare a budget request before enabling paid services.
