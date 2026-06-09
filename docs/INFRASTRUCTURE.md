# Alienated Workplace Client Infrastructure

This repository is an isolated client repository for Alienated Workplace. It must not share PlayFab Title IDs, Steam App IDs, secrets, save schemas, or deployment environments with any other project.

## Required Environments

- GitHub repository: `w87121416/alienated-workplace-client`
- PlayFab Title: dedicated title `Dog gun kill`, Title ID `185174`
- Steamworks App ID: pending developer console configuration; current Steamworks account has no organization/app access
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

## Current External Console Status

- PlayFab Game Manager is reachable and the dev title has been created.
- PlayFab Steam Add-on is open and waiting for Steam Application ID and Steam Web API Key.
- Steamworks account `zhanglance3` currently shows no affiliated organization and no app dashboard. Steamworks registration / Steam Direct must be approved and handled by the owner because it can involve agreements and payment.
