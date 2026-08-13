# Design Addendum — Shell Occupancy vs Existing-Plan Recognition

Recorded: 2026-08-13

This addendum corrects an ambiguity in the Consolidated Expansion Vision. Two building workflows are architecturally distinct and must not be collapsed into one solver.

## Empty or mostly empty shell — generative workflow

`Occupy This Shell` applies only to an exterior/protected building envelope that does not already contain a deliberate complete floor plan.

The shell workflow is generative:

```text
protected shell
→ derive/store floor plates
→ place/solve vertical cores
→ circulation/egress
→ service space
→ room subdivision
→ openings/doors
→ furniture/decor
→ validation
```

The exterior shell, declared voids/atria, user locks, protected machinery, and other fixed geometry are constraints. CityPlus proposes an interior while preserving those constraints. Impossible constraint sets should be reported rather than solved by silently modifying the shell or violating requirements.

## Existing designed floor plan — interpretive workflow

A building or floor that already contains a deliberate plan must not be passed through the shell-occupancy generator by default.

The mental model is: **This floor already exists. Understand it.**

CityPlus should recognize and semanticize the existing design: rooms, corridors, atria, shafts, stairs, elevators, repeated floor patterns, facade-opening relationships, voids, and vertical relationships. The default operation is semantic recognition and later semantic editing/propagation, not automatic redesign.

Existing-plan recognition must make no block edits merely because it detected topology. A separate explicit re-plan/generative command may exist later, but it must never be silently invoked by recognition.

## Shared foundations

Both workflows may reuse room detection, topology, storey models, void/protected-region models, vertical-stack semantics, confidence scoring, and standards/profile data. They differ in authority:

- **Shell Occupancy:** generative; CityPlus may create a plausible interior inside protected constraints.
- **Existing Plan Recognition:** interpretive; CityPlus learns the authored plan and preserves it.

Planning-shell room detection can support both by improving understanding of unfinished/open-top construction, but detecting a shell must never automatically trigger occupancy generation.
