# Ledovia Maps Lab — South Carolina Offline Basemap Gate (Phase 1, revision LAB-SC-001)

Status: SPECIFIED / NOT YET PASSED. This is a test gate, not a downloadable map package.

## Goal
Prove that an actual South Carolina vector basemap renders in MapLibre GL JS after a cold launch in airplane mode, without fetching map tiles, fonts, sprites, styles, or JavaScript from the network. Do not confuse browser cache with installed offline coverage.

## Current findings (source inspection)
- Lab index.html loads MapLibre 4.7.1, PMTiles 3.2.1, and Protomaps basemap styling from external CDNs.
- Its vector source is an externally hosted PMTiles archive.
- Glyph and sprite assets are external.
- USGS topo, shaded relief, satellite, and SC 2023 HD imagery are online services.
- No local SC vector PMTiles package or offline-ready style assets are present.

## Reusable national package contract (proposed, not implemented)
A state release must declare: schema_version, state_fips, state_name, build_version, generated_at, source_name, source_url, source_date, source_license, attribution, file_name, byte_size, sha256, tile_format, min_zoom, max_zoom, bounds, offline_assets, coverage_notes, and verified_status.
Publish no state as ready until all bytes, checksums, licensing, offline rendering, and coverage checks pass. Separate street maps, aerial imagery, and resource records internally. Never silently substitute an online layer while offline.

## Source and packaging gate
1. Select an OpenStreetMap-derived source with documented redistribution/attribution terms and reproducible extract date.
2. Build a state-clipped vector PMTiles archive with a documented tile schema compatible with the selected MapLibre style; do not assume arbitrary OSM PBF files can be rendered as PMTiles.
3. Record actual archive size and SHA-256, zoom range, boundaries, coastline handling, and feature coverage.
4. Host or sideload the archive in the isolated lab; verify HTTP Range requests if hosted and persistent device storage if installed.
5. Bundle MapLibre JavaScript/CSS, PMTiles runtime, style JSON, glyph PBF ranges, and sprite PNG/JSON locally, with any required licenses.
6. Run airplane-mode cold-start tests on Florence, Columbia, Charleston, Greenville, rural Pee Dee, and coastal/island edges; record screenshots and missing-tile/error counts.
7. Confirm no remote requests are required and that blank/missing areas are disclosed. Verify stored bytes and persistence after browser restart.

## Blockers identified
- This environment has no direct access to download the external OSM extract and no installed tile compiler. Therefore no SC archive was generated in this revision.
- Device storage quota, archive size, OSM licensing details for the chosen compiled tileset, and Android offline operation remain unverified.

## Release gate
PASS only when a real SC archive plus local assets has been installed, independently integrity-checked, and cold-start-tested offline. Otherwise FAIL/NOT TESTED.

Protected: Beta v0.8.590 and Stable remain unchanged. This file is documentation in the isolated Maps Lab only.
