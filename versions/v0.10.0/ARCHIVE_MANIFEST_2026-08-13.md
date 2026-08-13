# v0.10.0 Alpha 10.0 — Immutable Archive Manifest

Baseline: `0.10.0-alpha.10.0-build-mode`

Target stack:
- Minecraft 1.20.1
- Java 17
- Fabric Loader 0.18.4
- Fabric API 0.92.8+1.20.1
- Axiom 5.4.2
- Axiom Client API 1.0.25
- WorldEdit 7.2.15 optional

Authoritative artifact names:
- Runtime: `axiom-cityplus-0.10.0-alpha.10.0-build-mode+mc1.20.1.jar`
- Source: `axiom-cityplus-0.10.0-alpha.10.0-build-mode-source.zip`

Recorded hashes:
- Runtime SHA-256: `3bc43c62d0f1dc2524a51a5d7f19f61036ebab56d99535234c9cbee90664acd9`
- Source SHA-256: `17e85ac8769429985c0ed4334c2125d65ce4b1eafd676a6c6fe803a0f30a35eb`

Recorded release verification:
- Java source compile pass
- Fabric-runtime remap pass
- class resolution `RESOLVE_OK 141/141`
- sensitive Minecraft linkage spot-checks
- `CITYPLUS_010_SELF_TEST_OK laneMin=3 cycle=2 room=30->40 stalls=80 busCells=422`
- road regressions 0.9.0/0.9.1/0.9.2 passed unchanged

This record is an archive of build verification, not a claim that every behavior was accepted in the real modpack.
