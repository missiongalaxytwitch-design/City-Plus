# CityPlus v0.10.3 — Building Studio test card

Use only `axiom-cityplus-0.10.3-alpha.10.3-building-studio+mc1.20.1.jar` for this run.

## Launch / UI
- Confirm Axiom starts with no CityPlus mixin/bootstrap crash.
- Confirm custom tools use distinct role glyphs/grouped names instead of every tool being the same pencil.
- Confirm Circle/Arc, Point-Click Wall/Room and Level Wall are not duplicated.

## Skyscraper shell
- Open **Axiom-CityPlus: Building Studio** in **Occupy Empty Shell** mode.
- Click inside the known large skyscraper shell.
- First test 10–20 storeys before committing the entire tower.
- Set typical floor height to the visible facade/storey rhythm.
- Try 6–10 units/storey, 3–5 rooms/unit, 2 exit stair stacks and 2–4 elevator shafts.
- Preview low/middle/high storeys and confirm footprint follows taper/setbacks with per-storey rescan enabled.

## Vertical-core torture test
- For the first test, use a full cube block for stair material.
- Physically follow every exit stair down multiple floors.
- Confirm landings align, corridor openings reach the stair, no apartment/slab blocks obstruct it, and no extra stair flight escapes above the top occupied storey.
- Confirm elevator shafts remain in the same XY position through all generated floors.

Current scope validates floor-corridor-to-stair reachability and vertical stair continuity. It does not yet claim a complete exterior exit-discharge route through the facade.

## Materials
Assign deliberately different active blocks to floor slab, corridor, partition, core wall, stair and service floor. Confirm each generated role uses its own selected material.

## Standards
Open Advanced settings, select IBC 2024 model, set Minecraft scale, apply nominal recommendations, then manually override them. User values must remain authoritative and under-spec choices should warn rather than silently change themselves.

## Existing-plan protection
Switch to **Recognize Existing Plan** and click an authored floor plan. It may recognize/semanticize rooms but must not replace the layout with generated apartments/corridors.

## Regression smoke
Test one straight road, one curved road, one elevated/bridge case, one parking lot, Build/Push-Pull, Floor/Ceiling, Circle/Arc, Point-Click Wall/Room, and Level Wall.

If anything fails, capture screenshot, latest.log, `config/architect/diagnostics/architect-latest.jsonl`, settings, affected storey, and whether Axiom Undo restored the voxel world.