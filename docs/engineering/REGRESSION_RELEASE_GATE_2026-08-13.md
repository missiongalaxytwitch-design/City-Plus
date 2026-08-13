# CityPlus Regression Release Gate

Recorded: 2026-08-13

New features must not silently change established behavior from the v0.10.0 baseline.

Every candidate should re-check the existing road generator, node and snapping behavior, elevation and bridges, parking and streetscape assets, spline editing, Build Mode push/pull and vertical stretch, floor/ceiling tools, room detection, persistence, and the newer drawing tools.

Ordinary room detection must remain unchanged when Planning Shell Mode is disabled.

Deterministic fixtures should compare generated block output and semantic records against known-good expected results. Unexpected changes fail the candidate. Intentional changes must be recorded as intentional before the expected fixture is replaced.

Class-resolution and remapped Minecraft linkage checks remain required for every installable JAR.

Automated checks do not replace the real modpack test. In-game screenshots, diagnostics, and observed behavior remain the final acceptance evidence.
