# CityPlus Direct Container Release Pipeline

Recorded: 2026-08-13

CityPlus release builds use the working container directly rather than assuming a normal Gradle-wrapper workflow.

1. Edit the real Java source tree.
2. Compile against the exact Minecraft 1.20.1 / Java 17 / Fabric / Axiom classpath.
3. Produce Mojang-named compiled classes.
4. Run CityPlus self-tests and regressions.
5. Package the named classes.
6. Remap Mojang names to Fabric intermediary runtime names.
7. Package the remapped classes with fabric.mod.json and resources.
8. Run class-resolution checks in the runtime namespace.
9. Inspect sensitive remapped Minecraft registry/world linkage.
10. Hash and package the runtime JAR and matching source snapshot.
11. Deliver the installable JAR in chat for real-modpack testing.

Build scopes must remain distinct: source compilation is not runtime linkage verification, and runtime linkage verification is not a successful real-modpack test.

Target: Minecraft 1.20.1, Java 17, Fabric Loader 0.18.4, Fabric API 0.92.8+1.20.1, Axiom 5.4.2, Axiom Client API 1.0.25, WorldEdit 7.2.15 optional.
