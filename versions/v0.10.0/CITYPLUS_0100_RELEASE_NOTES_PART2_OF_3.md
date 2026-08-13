# Axiom-CityPlus 0.10.0 Alpha 10.0 — Build Mode Release Notes (Part 2 of 3)

## Road / infrastructure additions
- Motor-vehicle lane rendering now has a 3-block minimum. Bike/cycle/path families may use 2-block lanes.
- Semantic lane classes: GENERAL, BIKE, BUS, TAXI, HOV, TOLL.
- Special lanes receive distinct lane-surface colors and stay tied to lane rails rather than recoloring the entire corridor.
- Package Maker exposes left/right special lane class, count, inner/outer placement, toll booth settings, and edge fencing.
- Toll road packages can place periodic booth markers away from junction conflict zones.
- Ten additional built-in packages: Local Street 2-Lane; Collector 4-Lane; Bus Lane Avenue 4-Lane; Cycle Boulevard 4-Lane; Managed HOV Highway 4+4; Toll Expressway 3+3; Dedicated Busway 1+1; Bidirectional Cycleway; Rural Local 2-Lane; Parking Access 2-Lane.
- New scalable **Parking Lot** tool with minimum 3-block stalls, stall depth/aisle controls, perimeter curb, stall markings, and optional landscaped islands.
- New **Edit Road Spline** tool: select a semantic road section and move START / BEND / END handles, adjust vertical crest/sag and banking, and rebuild only that road record while protecting known overlapping roads.
- Elevated supported spans sanitize accidental grass/dirt/moss verge/median surfaces into structural curb/sidewalk material.

## Persistence / semantic model
- World model can replace semantic rooms and road geometry records in place.
- Road registry can replace an existing road alignment without creating a new semantic road identity.
- Multi-floor facade movement propagates to matching room records above the selected floor.
