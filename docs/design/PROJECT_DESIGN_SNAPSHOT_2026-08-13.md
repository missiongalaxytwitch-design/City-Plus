# CityPlus Project Design Snapshot — 2026-08-13

This file is an immutable design snapshot assembled alongside the v0.10.0 baseline archive. It records the current product direction and engineering commitments without replacing the larger research/design documents.

## Product direction

CityPlus is a semantic city-design layer inside Axiom, not merely a road generator and not a replacement for Axiom. The intended experience combines Cities: Skylines-style infrastructure, Move It/TM:PE-style post-placement editing, Sims-style building workflows, civil-style alignment/grading, reusable asset libraries, and ordinary block editing at the lowest level.

Core doctrine: **blocks are output; meaning is the model.** Roads, rooms, walls, buildings, rails, runways, utilities, vehicles, ships, factories, and assets retain semantic identities independent of their block materials. CityPlus should re-solve design intent and constraints, then voxelize the result.

## Shared capability kernel

Prefer reusable primitives over isolated mini-tools:

- continuous plan geometry: line, arc, spline, stationing, projection, tangent/normal/curvature
- vertical profiles and elevation
- cross-sections and offsets
- rasterization/voxel policies
- semantic anchors and attachment ports
- repetition/distribution rules
- transform constraints
- material substitution groups
- asset families, variants, tags, bounds, and placement rules
- optional adapter capabilities

Roads, rail, airports, canals, walls, facade systems, utilities, ships, and other assemblies should consume the same neutral skills where appropriate.

## Existing road/infrastructure doctrine

The current road stack is proven infrastructure and should not be casually rewritten while unrelated features are added. Roads are continuous semantic corridors, not stamped slices. Existing behavior includes cross-sections, continuous curves, stationing, elevation/bank/profile, snapping, nodes, lane rails and movement semantics, bridges/elevated structures, earthworks, parking, streetscape/utilities, saved road packages, custom roadside assets, and post-placement road spline editing.

Normal motor lanes retain a 3-block minimum; bike/cycle/path families may use 2. Semantic lane classes currently include GENERAL, BIKE, BUS, TAXI, HOV, and TOLL. Existing node intent includes continuation, fork, merge/diverge, T, and X/crossing behavior.

## Building/editor direction

Building work should become semantic rather than giant voxel scaling. Rooms, boundaries, openings, floors, facades, storeys, atria/voids, stairs/elevators/cores, roofs, and attached systems should eventually be explicit relationships.

High-rise editing should use masses, storey types, facade systems, repeated bays/modules, protected voids, podium/crown conditions, and per-floor exceptions. Increasing tower width should add/reallocate facade bays rather than stretch windows and columns into nonsense.

The editor should remain viewport-first. Sims 3-style camera behavior remains the preferred CityPlus editor direction. Axiom remains the host editor and block-level detail tool.

## Two distinct building workflows

**Shell Occupancy** is generative and applies only to an empty or mostly empty protected building envelope. Its future pipeline is shell/void protection → floor plates → vertical cores → circulation/egress → service space → room subdivision → doors/openings → furnishing/decor → validation. It must not modify the protected exterior to force a solution.

**Existing Plan Recognition** is interpretive. If a floor plan already exists, CityPlus should understand it: rooms, corridors, atria, shafts, stairs/elevators, repeated floor patterns, facade-opening relationships, voids, and vertical relationships. Recognition must not silently redesign the authored plan.

Both workflows can reuse room/topology/storey/void models, but they do not have the same authority.

## Room detection

Room detection must improve beyond finished boxes. Planning-shell recognition should tolerate open tops and plausible terrain/grass floors, infer likely wall/storey height from wall-top agreement, classify floor evidence, and expose confidence/threshold controls. Ordinary Detect Rooms must retain its existing behavior when Planning Shell Mode is off.

## Drawing/build foundation

Near-term building primitives include true parametric Circle/Arc geometry, point-click Wall/Room generation, Level Wall, safer room/build transforms, and connectivity-aware placement. CityPlus-owned generated rooms should be recorded semantically directly rather than unnecessarily rediscovered by the room detector.

## Minecraft placement reconciliation

Fast Axiom bulk placement is a major performance advantage and should remain the default. Connection-sensitive block states require a targeted refinement layer rather than turning every operation into sequential placement.

Preferred long-term model:

- STATIC_BULK: ordinary solids and states derived directly
- NEIGHBOR_RECONCILE: panes, fences, walls, bars and similar adjacency-shaped states
- SEQUENTIAL_REQUIRED: content whose valid result genuinely depends on placement ordering
- BLOCK_ENTITY_PRESERVE: payload-bearing content that must be preserved or cause a safe abort
- ADAPTER_CONTROLLED: functional/mod-specific placement delegated to an optional integration

For pure neighbor-shaped states, prefer a pre-commit virtual-neighborhood solve against the complete target edit, followed by the normal single bulk commit. Use post-commit/adapters only when real world-side effects are necessary.

## Asset library, variants, tags, and packs

Every reusable object should be savable as an asset family with unlimited user-created variants. Variants may change materials, blocks, geometry, tags, or function. Generic material groups should support repaint/substitution without vehicle-specific special cases.

Tags are operational discovery metadata. An SUV tagged as a vehicle should automatically become eligible for parking/road population; an office desk should become eligible for office fit-out; a streetlight should be discoverable by streetscape systems.

The catalogue should eventually use small cached rendered/blueprint thumbnails with Sims-like family/variant browsing.

Community import/export is a first-class feature. Proposed `.citypluspack` containers should preserve stable IDs, families, variants, tags, previews, placement rules, presets, standards profiles, dependencies, cross-references, and optional adapter metadata.

Community policy direction: packs built for the CityPlus ecosystem should remain freely accessible, while attribution, documentation, author links, and support/donation links remain welcome. Final legal terms require proper legal drafting before publication as enforceable terms.

## Scaling and assembly constraints

Never assume every selected block can scale uniformly. Useful transform categories include PARAMETRIC, REPEATABLE, RIGID, RIGID_WITH_PORTS, PROTECTED_VOLUME, EXTENSIBLE_CONNECTION, and USER_LOCKED.

Functional Create/multiblock/redstone machinery should normally remain rigid/protected. Connections such as belts, pipes, cables, hull sections, facade bays, or repeated modules may extend/repeat according to explicit rules.

## Vehicle / ship / aircraft / machine builder

A future generic Assembly Builder should use a Spore-like broad interaction model: choose components, snap them through semantic ports, scale/repeat allowed regions, mirror/rotate safe components, and refine the result in Axiom.

Everything should know what it is and what it can connect to. Domain presets can specialize the generic builder for ships, aircraft, road vehicles, rail vehicles, and industrial machines. Functional mod adapters may expose safe ports without becoming hard dependencies.

## Civil, rail, airports, canals

A neutral civil kernel should provide alignment, vertical profile, stationing, cross-section, target surfaces, grade control, cut/fill and terrain transitions. Civil Smooth means solving an engineered target surface, not applying a generic blur.

Rail and airport systems should consume the same civil/alignment foundations. CityPlus owns corridor/civil semantics; optional Create/Steam 'n' Rails adapters translate compatible solved geometry into functional mod content. Canals can later reuse the same alignment and terrain skills.

## Optional mod integration

Fabric/Axiom remains the development priority. Forge/NeoForge is intentionally later.

Adapters must be optional, isolated and fail-safe. Installed compatible mods may provide contextual suggestions or semantic parts, but missing integrations must never make ordinary CityPlus geometry unusable. Create-family rail, energy/stress, logistics, NPC/population, elevators, power systems and similar capabilities should be mapped through adapters only when a stable semantic object already exists in the core.

## Performance strategy

Preserve the current semantic-solve → voxelize → bulk-commit architecture. Store semantic records broadly, but compute expensive systems only in the active context/region: **store broadly, compute narrowly.** Avoid whole-world background solvers unless a feature genuinely requires them.

Future performance diagnostics should record semantic object count, affected bounds/chunks, solve time, voxelization time, affected block count, reconciliation count, adapter time and commit time.

## Regression/release doctrine

Every new release must prove it did not silently break established road, node, bridge, parking, streetscape, asset, persistence, room or Build Mode behavior. Use deterministic golden fixtures where practical. Unexpected output changes fail the candidate; intentional changes require an explicit recorded reason.

Release verification scopes remain distinct:

1. source compile/self-tests
2. Mojmap → Fabric intermediary remap
3. runtime class-resolution/linkage audit
4. real modpack test

The final authority remains the real in-game result. A screenshot showing a broken system overrides a green unit test.

## Current roadmap direction

Near term: drawing/building foundation, planning-shell recognition, connectivity reconciliation, semantic-transform safety, and regression hardening.

Then: asset families/variants/tags/material groups/thumbnails/pack format; explicit Building/Storey/Boundary semantics; civil profile/grading kernel; deeper roads/bridges and regional standards; procedural shell occupancy and furnishing; rail; airports; utilities/functional adapters; and the generic assembly/vehicle/ship/aircraft builder.

The goal is not to replace building. The goal is to automate repetitive physical labor while leaving design decisions and final block-level refinement in the user's hands.
