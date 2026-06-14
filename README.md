# Navine Client Addon Template — Minecraft 26.1.2 — Fabric

**26.1.2 Fabric Template** for building third-party Navine Client addons.

Pre-built archive: [`navine-client-addon-template-26.1.2-fabric.zip`](navine-client-addon-template-26.1.2-fabric.zip) (same project as this repository, without `.git`).

## Requirements

- JDK 25
- Minecraft **26.1.2**
- Fabric Loader **0.19.3**
- Fabric API **0.150.0+26.1.2**
- Navine Client jar at `libs/Navine-Client.jar`

## Quick start

1. Clone this repo or extract the zip.
2. Place a built `Navine-Client.jar` in `libs/`.
3. Rename the mod id in `src/main/resources/fabric.mod.json` and update packages under `src/main/java`.
4. Build:

```bat
gradlew.bat build
```

Output jar: `build/libs/example-navine-addon-1.0.0.jar`

## Registering your addon

`fabric.mod.json` must declare a `navine` entrypoint:

```json
"entrypoints": {
  "navine": [
    "com.example.navineaddon.NavineExampleAddon"
  ]
}
```

## API overview

Extend `nv.navineclient.NavineAddon` and implement:

- `onInitialize()` — register modules and commands
- `getPackage()` — unique addon id, e.g. `com.example.navineaddon`
- `onRegisterCategories()` — optional custom categories hook

Use `registerModule(Module)` and `registerCommand(Command)` inside `onInitialize()`.

Navine Client loads addons through Fabric entrypoints before `ModuleManager.init()`.

## Example files

- `NavineExampleAddon.java` — addon entry class
- `modules/ExampleModule.java` — sample toggle module with settings
- `commands/ExampleCommand.java` — sample chat command

## Install

Put Navine Client and your addon jar in the same mods folder, launch the game, and verify your module appears in ClickGUI.

## Policy

Addons may add modules, commands, and UI extensions. Do not ship anti-cheat bypass, packet evasion, or stealth evasion features in public templates or examples.
