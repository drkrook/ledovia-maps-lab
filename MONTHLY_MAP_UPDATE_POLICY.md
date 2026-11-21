# Ledovia Mandatory Monthly Map Updates — Policy v1.0

Decision: APPROVED by project owner on 2026-11-21. Applies to every published state street-map package, beginning with South Carolina and expanding nationally.

## Mandatory cadence
- Run an automated source-data pull and rebuild attempt **at least once per calendar month** for each published state.
- Record the upstream data snapshot date, build timestamp, package version, size, SHA-256, coverage, license/attribution, and validation result.
- Run validation before any release: archive integrity, MapLibre rendering, offline assets, representative geographic coverage, and installation/rollback checks.
- **Human approval is mandatory before publishing** a replacement to users. A scheduled build is not an automatic deployment.
- If the monthly build or validation fails, keep the prior working package available and flag the update as delayed; never claim it was updated.
- Users should be able to see their installed version/data date and whether an update is available. Do not force-download a large update over cellular or block access to the existing offline map when disconnected.
- Download replacement to separate storage; verify checksum and functional readiness before switching. Preserve rollback capability.
- Emergency resource records use a separate update track, with urgent corrections when verified; aerial imagery and elevation datasets update on source publication rather than an artificial monthly full redownload.
- Monthly full-package replacement is the initial implementation; differential downloads are future work, only after independent validation.

## Scope and status
This is a binding **product requirement**, not evidence that an automated scheduler, map updater, device notification, or monthly publication process is already running. Implementation requires separate scoped authorization and verification.

Protected: Ledovia Beta v0.8.590 and Stable are unchanged. Maps Lab source change is documentation only.
