# Axiom-CityPlus 0.10.0 Alpha 10.0 — Build Mode test card

Target: Minecraft 1.20.1 / Fabric Loader 0.18.4 / Axiom 5.4.2.

## Install
Remove the older Axiom-CityPlus jar and install only `axiom-cityplus-0.10.0-alpha.10.0-build-mode+mc1.20.1.jar`.

Diagnostics remain under `config/architect/diagnostics/architect-latest.jsonl`.

## 1 — Sims-style room push/pull
1. Make an ordinary enclosed room, preferably with a 2-block-thick exterior wall and a window/trim detail.
2. Select **Axiom-CityPlus: Build / Push-Pull**.
3. Click inside the room. If it is not already semantic, Build Mode will attempt an automatic room scan.
4. In **PUSH WALL**, click/hold a wall and drag across the wall normal, then release.
5. Repeat on a diagonal/stair-stepped room boundary.

Watch for: wall thickness preserved; facade blocks/windows/trim translated rather than flattened; floor/ceiling extension; reconnects at both ends; no orphan copy left behind.

## 2 — Multi-floor facade push
1. Use stacked semantic rooms/floors that share an exterior facade plane.
2. Set **Floors / storeys affected** to 2–5.
3. Push an exterior wall.

Watch for: actual block facade moves across the selected vertical range; semantic rooms on matching upper facade planes update with it. This is an alpha section move, not yet a full building constraint solver.

## 3 — Vertical stretch
1. Select a room in Build / Push-Pull.
2. Switch to **VERTICAL STRETCH**.
3. Click/hold and drag the mouse upward/downward.

Watch for: roof/top layer moves; boundary walls extend/shorten; no duplicate old roof remains. Test one floor first, then multiple floors.

## 4 — Floor / ceiling
Use **Axiom-CityPlus: Floor / Ceiling**, click a semantic room, choose floor/ceiling, choose an active block, and commit with Enter.

## 5 — Lane scale and special lanes
Normal motor roads should render at **3 blocks per lane minimum**. `Bidirectional Cycleway` may use 2-block lanes.

Test built-ins: Bus Lane Avenue 4-Lane, Cycle Boulevard 4-Lane, Managed HOV Highway 4+4, Toll Expressway 3+3, Dedicated Busway 1+1, Bidirectional Cycleway. Package Maker can assign BIKE / BUS / TAXI / HOV / TOLL lane classes, toll booths, and edge fencing.

## 6 — Parking lot
Use **Axiom-CityPlus: Parking Lot**. Click opposite corners and test stall width/depth, drive aisle width, islands, and active-block materials.

## 7 — Move-It-style road section edit
Use **Axiom-CityPlus: Edit Road Spline**, select a semantic CityPlus road, cycle START / BEND / END, move a handle, preview it, then Enter to commit. Test a curved ramp and a connected section.

## 8 — Elevated-road grass sanity
Build an elevated road that normally has landscaped verge/median material. Grass/dirt/moss road-edge landscape cells should be replaced by structural curb/sidewalk material in supported spans.

## Please send back
Screenshots plus the diagnostics file after anything weird. Especially useful: thick-wall push/pull, diagonal room, 3+ floors facade move, vertical stretch, a special-lane road, a parking lot, and a spline edit near another road.
