# CityPlus 0.10.3 — CAD/BIM reuse decisions

This is an additive design record for the Building Studio implementation. Older docs remain untouched.

## Floor-plan/circulation
The first shell occupancy solver deliberately reuses mature CAD/BIM ideas instead of treating floor planning as random wall generation:
- discrete inward offset / distance transform to establish circulation depth;
- obstacle-aware A* to reconnect circulation and route it to cores;
- graph validation for hard reachability;
- vertical cores reserved before apartment/room subdivision.

Autodesk Revit Path of Travel was a particularly useful precedent: it performs plan-level obstacle analysis on a fixed grid and uses a custom A* route calculation. CityPlus uses the same family of approach directly on Minecraft's voxel grid, while adding its own multi-storey vertical-core graph because Revit Path of Travel is level-local.

## Reusable geometry libraries evaluated
**JTS Topology Suite** is a strong future dependency/adapter candidate for continuous polygon buffering, offset curves and polygonization. It is pure Java and dual-licensed EPL 2.0 / Eclipse Distribution License 1.0. 0.10.3 does not bundle it yet because the authoritative shell detector currently produces discrete Minecraft cells; converting cell masks to continuous polygons and back would add another rasterization boundary during a regression-sensitive release.

**Google OR-Tools / CP-SAT** was also evaluated. Its Java API is suitable for large integer/Boolean constraint problems, but its native/runtime packaging is heavier than justified for the first shell solver. CityPlus keeps the v1 solver deterministic and in-core while leaving room for a future solver adapter for mixed-use/program optimization.

## Shared civil alignment
The new neutral path-system record follows the same high-level decomposition used by buildingSMART IFC Alignment: horizontal alignment, vertical profile, and optional cant/crossfall. Domain policy then sits above that common geometry. This prepares one foundation for road, rail, canal, seawall, retaining wall, levee, path, utility corridor, and runway/taxiway systems without refactoring the working road stack in this release.

## Standards
The standards layer is deliberately advisory and user-overridable. The first IBC 2024 model profile covers a small verified set of egress concepts. The Ontario profile records the current NBC 2020 + Ontario-amendment basis but leaves clause-level numeric values user-controlled until a verified Ontario rule table is imported. Generated Minecraft layouts are never represented as code-certified professional designs.