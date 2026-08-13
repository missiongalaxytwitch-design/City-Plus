# Axiom-CityPlus 0.10.0 Alpha 10.0 — Build Mode Release Notes (Part 1 of 3)

This is the first release that reunifies the infrastructure work with the original semantic building-editor goal.

## Building / Sims-style editing
- New **Build / Push-Pull** Axiom tool.
- Selects existing semantic rooms and can automatically attempt room detection when no record exists yet.
- Push/pull a room or exterior facade side using a live in-world drag.
- Cardinal and diagonal/stair-stepped semantic boundaries are supported by the side solver.
- Existing facade blocks are copied rather than replaced with a flat material, so windows/trim/material variation can move with the facade.
- Wall/facade depth is detected outward (up to 7 block columns in this alpha), allowing multi-block walls to retain thickness.
- Overlapping source/destination cells are protected during short moves so a 2-block wall moved by 1 block does not erase itself.
- Floor/ceiling cells extend when the room expands.
- Endpoint reconnect sweeps close the moved wall back into neighboring geometry.
- **Floors / storeys affected** lets one exterior facade operation span multiple floors.
- Upper semantic rooms sharing the same facade plane/tangent range are updated during a multi-floor push.
- **Vertical Stretch** moves the top/roof layer and extends/shortens the semantic boundary walls; mouse vertical drag is approximately 18 screen pixels per block.
- New **Floor / Ceiling** semantic surface tool.
