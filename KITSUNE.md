# Kitsune Viewer — Aurora migration

This is a fork of Aurora Viewer, based initially on upstream commit
6a39d37d602d6e38a3a682574e4c39d67f621cf5. Aurora's Rust/wgpu renderer,
licenses and attribution remain intact. The previous Firestorm-based Kitsune
repository is preserved separately.

This first migration commit separates default settings, caches, logs, Blender
LiveMesh discovery and updater maintenance from Aurora. It changes the window
title and Windows product metadata to Kitsune and points release discovery and
its download allowlist at this fork. Existing signature checks remain enabled;
no Kitsune signed release infrastructure has been configured yet.

This is a development foundation, not a completed port or a tested release.
Internal crate/executable names, application icon, login and installer branding,
network identity and some integration identifiers still come from Aurora.
Do not install this over Aurora or reuse Aurora's custom cache/profile paths.

## Feature migration

| Kitsune goal | Aurora baseline / remaining work |
| --- | --- |
| Explorer inventory with folder history and multiple windows | Native responsive Explorer and single-folder windows already exist; compare behavior before adding duplicates. |
| Selected-face texture/material inspection and image export | Reuse Aurora's build, texture and material inspectors; add Kitsune access workflow and shortcut after tracing native selection and asset APIs. |
| Cache browser | Still to implement; the previous Kitsune inspector was not a complete cache browser. |
| Configurable Shift+Alt+left-click inspection | Still to port and validate against Aurora input handling. |
| Posing and pose export | Aurora has native poser and animation tools; compare local avatar targeting and export formats before extending them. |
| Smooth inventory updates | Profile the native Rust implementation; Firestorm's C++ time-budget patch does not transfer directly. |
| Fox icon and Kitsune landing screen | Recover existing artwork and adapt to Aurora's native startup UI. |
| Windows AVX2 package | Still to configure and build. No Windows artifact is produced by this commit. |

Havok support and unrestricted asset export are not implemented by this migration.
Features must be validated offline first, then by the user in Second Life.
