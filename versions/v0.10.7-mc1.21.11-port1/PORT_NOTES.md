# Axiom-CityPlus v0.10.7 — Minecraft 1.21.11 forward-port experiment

This is a one-off experimental forward port of the v0.10.7 PURE CURVE build. It does not move the mainline project away from Minecraft 1.20.1.

## Target
- Minecraft 1.21.11
- Java 21
- Fabric Loader 0.19.3
- Fabric API 0.141.6+1.21.11
- Axiom 5.4.2 for Minecraft 1.21.11

## Result
The complete v0.10.7 source compiled and Loom-remapped against the 1.21.11 dependency set without requiring a functional Java algorithm rewrite. The port changes are build/runtime targeting, dependency selection, Java level, mod metadata, and version/diagnostic identity.

A second clean build was performed after removing the transferred 1.20.1 local `libs/axiomclientapi.jar`; the build still passed using the matching Axiom 5.4.2 Minecraft 1.21.11 artifact.

Verification includes Java 21 classfiles, Fabric intermediary namespace checks, packaged-class resolution against the 1.21.11 runtime namespace, validation of the private Axiom presentation mixin target against the exact matching Axiom artifact, and the existing platform-neutral regression suite through PURE CURVE.

Interactive Minecraft/Axiom runtime success is intentionally not claimed until the JAR is tested in a real 1.21.11 instance.
