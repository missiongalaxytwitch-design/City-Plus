# Axiom-CityPlus 0.10.0 Alpha 10.0 — Build Mode Release Notes (Part 3 of 3)

## Verification performed
- Full Java source compilation succeeded against the Minecraft 1.20.1 Mojang-mapped client, Fabric/Axiom compile interfaces, and Java 17.
- Final release jar was remapped to Fabric runtime intermediary namespace with ForgeAutoRenamingTool.
- Final jar class-resolution check: `RESOLVE_OK 141/141`.
- Runtime linkage spot-checks confirmed `BlockGetter.method_8320`, `Registry.method_10221`, and `Registry.method_10223` in the remapped output.
- New test: `CITYPLUS_010_SELF_TEST_OK laneMin=3 cycle=2 room=30->40 stalls=80 busCells=422`.
- Current road regressions 0.9.0, 0.9.1 and 0.9.2 pass unchanged. Older 0.3.6 contains an obsolete endpoint-classification expectation and is not a valid regression for the current connection kernel.

## Known alpha limitations
- Build push/pull is a semantic facade/room-plane transform, not yet a complete building constraint solver. Highly non-planar roofs, stairs, structural cores, attached balconies, and arbitrary neighboring-object dependencies are not all re-solved automatically yet.
- Multi-floor wall movement updates semantic rooms that share the selected facade plane, but does not yet treat an entire building as one rigid/constraint graph.
- Vertical Stretch extends the selected section; it does not yet synthesize a complete new storey with replicated rooms/windows/furniture.
- The road spline editor currently exposes START/BEND/END plus vertical profile/bank. A full multi-control-point Move It editor is the next logical expansion.
- Parking lots are rectangular in this vertical slice.
- Special-lane sidecars currently support a left/right class subset with inner/outer placement, not an arbitrary ordered heterogeneous lane stack.
- Elevated branch/interchange structural clipping still needs a dedicated shared-deck/node ownership pass; this release fixes elevated landscape material but does not claim that bridge-to-bridge clipping problem is solved.
