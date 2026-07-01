# World Transvoxel Gameworld

Reusable Godot game-world addon for the World Transvoxel stack.

Status: P1 production boundary candidate.

This repository provides the `world_transvoxel_gameworld` addon. It sits above
the terrain addon and gives games a standard world node, terrain setup,
optional player-driven viewer updates, terrain edit bridge, and telemetry
summary.

## Dependencies

Consuming projects must also install and enable:

- `res://addons/world_transvoxel/plugin.cfg`
- `res://addons/world_transvoxel_terrain/plugin.cfg`
- `res://addons/world_transvoxel_gameworld/plugin.cfg`

The low-level Transvoxel backend remains hidden behind `world-transvoxel-terrain`.
Games should use this addon and the terrain addon APIs instead of direct backend
calls.

## Public API

Main script:

```text
res://addons/world_transvoxel_gameworld/wt_game_world_node.gd
```

Primary node/class name:

```text
WtGameWorld
```

Supported API groups:

- `configure_game_world(...)`
- `setup_standard_world()`
- `attach_player(...)`
- `start_world()`
- `update_player_viewer(...)`
- `submit_sphere_edit(...)`
- `wait_for_cold_idle(...)`
- `wait_for_world_revision(...)`
- `get_terrain_world()`
- `get_game_world_summary()`

`configure_game_world(...)` accepts an optional final `viewer_maximum_lod`
argument. Use `0` for flat/LOD0-only profiles and `1` for the compact
procedural 2K profile so the gameworld path exercises the same LOD hierarchy as
the current validation human playtest.

## Boundary

This addon must not contain validation-game scripts, scenes, tests, tools, or
artifacts. Validation belongs in `world-transvoxel-validation-game`; this repo
contains only reusable gameworld code and documentation.
