# NEVA Linux hotfix for CS2 1.41.9.7

Community hotfix, not an official CounterStrikeSharp release.

- Source: upstream PR #1490, commit `86e57d69ee33d0480a6ebd221b579860a26eeb78`.
- Fixed SDK: `81020d1a26b9d4321b9f030c96929ec18e8c0cff` (alliedmodders/s2sdk#124).
- Linux ClientPrint gamedata: upstream PR #1492, commit `0e88459b82da8b952b27c176d814b1fff7dce520`.
- Includes native Linux SteamRT3 binary and matching managed API; the with-runtime archive also includes ASP.NET Core runtime 10.0.3, matching upstream packaging.
- Upstream code and contributor attribution are retained. No NuGet package is published.

The SDK patch addresses the changed network-message handle layout and lookup slots.
The CSS patch preserves message names seen by managed plugins and adapts SDK call sites.

## Install through NEVA Egg

Use release `v1.0.379-neva.1` from `NaMol4anke/CounterStrikeSharp` and the
`counterstrikesharp-with-runtime-linux-1.0.379-neva.1.zip` asset.
Retain the upstream archive layout: extract into `game/csgo`.

Set `CSS_RELEASE_TAG=v1.0.379-neva.1` in the SMS provisioning environment;
managed SMS startup sets `RELEASE_FREEZE=1`. The Egg CSS updater repository must
be `NaMol4anke/CounterStrikeSharp`. A tag pin alone does not change the repository.
Keep `INSTALL_CSS=1` and preserve the currently installed NAP and its configuration.

## Validation and limits

Release publication requires a native build in the Steam Runtime SDK container,
managed API tests, matching API publication, corrected ClientPrint gamedata,
archive integrity checks and SHA256 checksums. BUILD-PROVENANCE.txt records the source SHA.
These checks do not replace a live CS2 test with NAP, player joins, reconnects,
map changes, warmup, knife/live rounds, demo recording and SMS readiness.

Back up existing addon files, version tracking and settings before installation.
Reverting to unpatched binaries does not solve the CS2 1.41.9.7 compatibility issue.

Upstream references:
- https://github.com/roflmuffin/CounterStrikeSharp/pull/1490
- https://github.com/roflmuffin/CounterStrikeSharp/pull/1492
- https://github.com/alliedmodders/s2sdk/pull/124