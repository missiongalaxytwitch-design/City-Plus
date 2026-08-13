# CityPlus 0.10.4 focused torture card

Install only `axiom-cityplus-0.10.4-alpha.10.4-semantic-structure+mc1.20.1.jar`.

1. Regression smoke test: confirm old roads/bridges/parking/Build tools register; preview/place a known road and parking lot.
2. Re-test the skyscraper that exposed the perimeter-band bug. Start with 10–20 storeys, AUTO circulation, and preview low/middle/high floors. Units should be organized around connected circulation rather than just forming a perimeter onion ring.
3. Explicit residential program: try 1 Living, 3 Bedrooms, 1 Kitchen, 2 Bathrooms, 1 Storage. If a unit cannot fit the requested program, CityPlus should warn instead of silently claiming success.
4. Structural-only mode: Units per floor = 0, Structural supports = ON. Expect floors, continuous cores, circulation, columns and service zones, but no units/rooms.
5. Round/curved tower: AUTO should not crash on a non-rectangular shell and should choose a shape-aware circulation strategy.
6. After commit, inspect/export the world semantic JSON. Look for schema v5 buildingSpaces, buildingElements and buildingRelations. Bedrooms/living spaces at the facade may be balcony.eligible; stair/core/service spaces must be balcony.forbidden. Columns should have stable IDs and MOVEABLE capability; SUPPORTS relations should connect columns to slabs.
7. Test independent material assignments for slab, corridor, partitions, core, stairs, service and columns.

Failure capture: screenshot before/preview/after, latest.log, `config/architect/diagnostics/architect-latest.jsonl`, and the affected `config/architect/worlds/*.json` when identity/relationships look wrong.
