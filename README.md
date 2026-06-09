# NoPickup Mod — Fabric 1.21.1

A simple Fabric mod that lets you toggle item pickup on/off using keybinds. Works on servers — the server enforces the pickup block, not just the client.

## Features

| Keybind | Action |
|---------|--------|
| **U** | **Activate** — Disable item pickup (items stay on ground) |
| **I** | **Deactivate** — Re-enable item pickup (normal behavior) |

- ✅ Server-side enforcement via Mixin on `ItemEntity#onPlayerCollision`
- ✅ Per-player state (each player controls their own toggle)
- ✅ HUD message feedback on toggle
- ✅ Keybinds rebindable in Controls settings

## Requirements

- Minecraft 1.21.1
- Fabric Loader ≥ 0.16.0
- Fabric API

## Building

```bash
git clone https://github.com/YOUR_USERNAME/nopickup-mod.git
cd nopickup-mod
./gradlew build
```

Output JAR will be in `build/libs/nopickup-1.0.0.jar`.

## Installation

1. Install [Fabric Loader](https://fabricmc.net/use/) for 1.21.1
2. Download [Fabric API](https://modrinth.com/mod/fabric-api)
3. Drop both JARs into your `mods/` folder
4. Launch the game!

## How It Works

- The **client** listens for U/I keypresses and sends a small network packet to the server.
- The **server** maintains a `Set<UUID>` of players who have pickup disabled.
- A **Mixin** on `ItemEntity#onPlayerCollision` cancels the pickup event for those players.

## License

MIT
