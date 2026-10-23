# MLM Animator (Multi-limbed Model Animator)

A Minecraft Forge library mod that animates player models with any number of limbs: poses, limb animations and model resizing. It is used by [CultivationCraft](https://github.com/lNalator/Cultivationcraft).

- Mod id `mlmanimator`, Maven coordinates `lnalator.mlmanimator:mlmanimator`
- Minecraft **1.19.2**, Forge **43.1.47** or later, official Mojang mappings

## Requirements

- **JDK 17** (Temurin, Oracle or any other build). Gradle runs with the JDK in `JAVA_HOME`.
- Gradle itself is not needed: use the wrapper (`./gradlew`, Gradle 7.6.6).

## Set up the development environment

```bash
git clone https://github.com/lNalator/MultilLimbedModel.git
cd MultilLimbedModel
./gradlew build
```

If your default Java is not 17, point Gradle to a JDK 17 first:

```bash
export JAVA_HOME=/path/to/jdk-17
```

### IDE

- **IntelliJ IDEA:** open `build.gradle` as a project, then run `./gradlew genIntellijRuns`.
- **Eclipse:** `./gradlew genEclipseRuns`, then import the folder as an existing Gradle project.
- **VS Code:** install the Java and Gradle extensions, then `./gradlew genVSCodeRuns`.

The first import decompiles Minecraft and can take several minutes.

## Build

```bash
./gradlew build
```

The jar is written to `build/libs/mlmanimator-<version>.jar` (the version comes from `mod_version` in `gradle.properties`). Put it in the `mods` folder of a Forge 1.19.2 profile, next to the mods that use it.

## Test in game

| Command | What it does |
|---|---|
| `./gradlew runClient` | Starts Minecraft with the mod loaded, in the `run/` folder |
| `./gradlew runServer` | Starts a dedicated server. The first time, set `eula=true` in `run/eula.txt` and run it again |

This mod has no gameplay of its own: the easiest way to see the animations is to run CultivationCraft, which uses it.

## Working on it together with CultivationCraft

CultivationCraft builds against this repository's **sources**. Clone both side by side:

```
some-folder/
├── Cultivationcraft/
└── MultilLimbedModel/
```

`Cultivationcraft/settings.gradle` includes this checkout as a composite build, so a change made here is used the next time you build or run CultivationCraft (`./gradlew runClient` from `Cultivationcraft/`), without publishing anything. Another location can be passed with `-PmlmSourceDir=/path/to/MultilLimbedModel`.

CultivationCraft's release workflow builds against the `v0.2.2` tag of this repository: when a CultivationCraft change needs a new MLM Animator version, tag it, then update the `ref` in `Cultivationcraft/.github/workflows/release.yml` and the `mlmanimator` version range in CultivationCraft's `mods.toml`.

Changes are listed in [CHANGELOG.md](CHANGELOG.md).
