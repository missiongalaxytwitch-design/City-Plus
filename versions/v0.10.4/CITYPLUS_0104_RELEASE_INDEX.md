# CityPlus v0.10.4 — Semantic Structure + Circulation-First Fit-Out

Immutable archive entry for the 0.10.4 runtime candidate.

Key changes:
- circulation-first floor-plan generation replacing the 0.10.3 perimeter-band bias;
- explicit residential, hotel and office room/space programs;
- structural-only mode remains supported;
- persistent semantic schema v5: BuildingSpaceRecord, BuildingElementRecord, BuildingRelationRecord;
- BuildingSemanticIndex queries semantic spaces/elements/relationships after generation;
- BuildingSemanticValidator aborts before voxel commit if semantic identity/references are invalid;
- generated columns have stable IDs and MOVEABLE/REGENERATABLE capabilities;
- typed SUPPORTS relationships connect columns to slabs;
- facade-contact BEDROOM/LIVING/LIVING_SLEEPING/HOTEL_ROOM spaces can be balcony targets while stair/core/service spaces are explicitly forbidden;
- AUTO/CENTRAL_SPINE/CORE_LOOP/MEDIAL_SKELETON circulation strategies;
- user-controlled material palette and standards controls preserved;
- Ontario standards metadata current to O. Reg. 242/26 / July 17, 2026 amendments;
- existing road/bridge/parking locked runtime classes were not changed.

Runtime candidate: `axiom-cityplus-0.10.4-alpha.10.4-semantic-structure+mc1.20.1.jar`
SHA-256: `38af47ac29d17307edb317b9ac7fd79446b4b91c49c305bb8666e9db1b125015`

Verification before runtime test:
- Java 17 class version pass
- RESOLVE_OK 231/231 BAD 0
- no packaged Minecraft/Fabric/Axiom test stubs
- 80/80 locked road/bridge/parking runtime classes byte-identical to v0.10.3
- historical BlockStateCodec byte-identical to known-good v0.10.0
- 0.10.1 drawing, 0.10.2 shell, 0.10.3 balcony/occupancy and 0.10.4 semantic tests pass

Real-modpack acceptance remains pending the in-game torture test.
