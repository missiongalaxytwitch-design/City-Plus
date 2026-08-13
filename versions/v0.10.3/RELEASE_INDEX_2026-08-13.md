# Axiom-CityPlus v0.10.3 Alpha 10.3 — Building Studio

Immutable release record for the 2026-08-13 Building Studio test candidate.

## Candidate artifacts
- Runtime: `axiom-cityplus-0.10.3-alpha.10.3-building-studio+mc1.20.1.jar`
- Runtime SHA-256: `668aaa468db155cd7ce61fc4938f3a57da665a79d885ca622a74119af488b64e`
- Matching source archive: `axiom-cityplus-0.10.3-alpha.10.3-building-studio-source.zip`
- Source SHA-256: `91fd558028ed53e468c584af222fc660272b158a291655858944eb9a0ead60ad`

## Main implementation slice
- Axiom-CityPlus: Building Studio with separate **Occupy Empty Shell** and **Recognize Existing Plan** workflows.
- Multi-storey shell occupancy generation with per-storey shell re-scan.
- Continuous exit-stair and elevator-shaft core reservation before room subdivision.
- Distance-field/inward-offset corridor seed plus A* circulation repair.
- Deterministic unit/apartment and room subdivision with corridor/door topology.
- Advanced standards/settings panel and independent material-role selection.
- Additive BuildingRecord persistence / world-model schema v3.
- Fail-soft Axiom 5.4.2 icon/group presentation mixin so custom tools are not all identical pencils.
- Additive neutral alignment records for future rail, canal, seawall, retaining-wall, levee, path, utility and runway/taxiway systems.
- FacadeBalconyPlanner semantic kernel added; in-game balcony placement UI is not part of this candidate.

## Verification before distribution
- `CITYPLUS_0103_OCCUPANCY_SELF_TEST_OK floors=12 units=94 cores=6 corridor=4692`
- `CITYPLUS_0103_BALCONY_PLANNER_OK floors=11 bays=6 width=6.833`
- `RESOLVE_OK 207 BAD 0`
- runtime namespace audit: PASS
- no test/runtime stub classes packaged: PASS
- exact Axiom 5.4.2 visual-mixin target audit: PASS
- historically sensitive BlockStateCodec byte-identical to v0.10.0 known-good: PASS
- selected road/bridge/parking runtime baseline classes byte-identical: `78/78`, zero differences.

## Status
Installable Fabric runtime **candidate**, not yet declared in-game successful. Riley's real Axiom/Fabric modpack test remains authoritative.

Older version records are not replaced by this file.