---
name: godot-naming-guide
description: Godot naming conventions for nodes, scripts, variables, functions, signals, constants, folders, resources, autoloads, enums, and more. Use when establishing or reviewing naming standards in a Godot project.
---

# Godot Naming Guide

Use this skill when establishing or reviewing naming standards in a Godot project. Consistent naming makes scenes, scripts, and resources easier to find, refactor, and maintain.

## General principles

- Use clear, descriptive English names. Avoid abbreviations unless they are universally understood in the project (e.g. `ui`, `fx`, `ai`).
- Be consistent across the entire project. Pick one convention per category and apply it everywhere.
- Avoid Godot reserved keywords and built-in class names as identifiers (e.g. do not name a node `Node`, `CanvasItem`, or `Position2D`).
- Do not start names with numbers.
- Avoid spaces and special characters. Use only letters, digits, and underscores.

## Node and scene naming

| Category | Convention | Example |
|----------|-----------|---------|
| Scene files | `PascalCase.tscn` | `Player.tscn`, `MainMenu.tscn` |
| Instanced nodes | `PascalCase` matching the scene | `<Player name="Player" ...>` |
| UI nodes | `PascalCase` with UI suffix | `HealthBar`, `StartButton`, `SettingsPanel` |
| Collision/physics nodes | Descriptive + area/shape suffix | `Hurtbox`, `DetectionArea`, `FloorCollision` |
| Camera nodes | `Camera2D`/`Camera3D` + purpose | `GameCamera`, `MenuCamera` |
| CanvasLayer nodes | `PascalCase` + layer purpose | `HUDLayer`, `DialogLayer` |
| Empty organizational nodes | `PascalCase` describing contents | `Enemies`, `SpawnPoints`, `Map` |

### Node name rules

- Node names should match their scene file name when instanced. A scene saved as `Player.tscn` should have its root node named `Player`.
- If multiple instances of the same scene exist, append a number or descriptor: `Player1`, `Player2`, `BossEnemy`, `MinionEnemy`.
- Do not rename nodes after instancing unless necessary; Godot uses node paths for references.

## Script naming

| Category | Convention | Example |
|----------|-----------|---------|
| Script files | `PascalCase.gd` matching the node/class | `player.gd`, `health_bar.gd` |
| Class name (class_name) | `PascalCase` | `class_name Player` |
| Script attached to a node | Same name as the node | `Player.gd` → `<Node name="Player" ...>` |

## Variable and property naming

| Category | Convention | Example |
|----------|-----------|---------|
| Variables | `snake_case` | `move_speed`, `health`, `is_alive` |
| Exported variables | `snake_case` | `@export var move_speed: float` |
| Constants | `UPPER_SNAKE_CASE` | `MAX_HEALTH`, `GRAVITY` |
| Boolean variables | `snake_case` starting with `is_`, `has_`, `can_`, `should_` | `is_alive`, `has_key`, `can_jump` |
| Arrays/Dictionaries | `snake_case`, plural for collections | `enemies`, `player_stats`, `spawn_points` |
| Node references | `snake_case` with `_node` suffix optional | `player_node`, `sprite`, `animation_player` |

### Variable rules

- Use `snake_case` for all variables, including exported ones. Do not use `camelCase` or `PascalCase` for variables.
- Private/internal variables (not meant to be accessed outside the class) may be prefixed with `_`: `_cooldown_timer`, `_target_position`.
- Booleans should read like questions or assertions: `is_ready`, `has_line_of_sight`, `can_attack`.

## Function and method naming

| Category | Convention | Example |
|----------|-----------|---------|
| Functions | `snake_case` | `take_damage()`, `spawn_enemy()`, `reset_game()` |
| Built-in virtual functions | `snake_case` (Godot standard) | `_ready()`, `_process()`, `_physics_process()` |
| Private helper functions | `_snake_case` prefixed with underscore | `_calculate_damage()`, `_update_ui()` |
| Getters/Setters | `get_` / `set_` prefix or use `setget` | `get_health()`, `set_health(value)` |

### Function rules

- All functions use `snake_case`. Do not use `camelCase`.
- Functions that modify state should use verbs: `heal()`, `die()`, `pause_game()`.
- Functions that return a boolean should read like a question: `is_dead()`, `can_afford()`, `has_line_of_sight()`.
- Internal helper functions should start with `_` to signal they are private.

## Signal naming

| Category | Convention | Example |
|----------|-----------|---------|
| Signals | `snake_case`, past tense or descriptive | `health_changed`, `enemy_spawned`, `game_over`, `item_collected` |
| Button/toggle signals | Descriptive state change | `toggled`, `pressed`, `value_changed` |

### Signal rules

- Use past tense for events that already happened: `enemy_spawned`, `player_died`, `level_completed`.
- Use present/descriptive for state changes: `health_changed`, `speed_updated`.
- Signals connected to built-in nodes follow Godot's conventions: `pressed`, `toggled`, `text_changed`.

## Autoload / Singleton naming

| Category | Convention | Example |
|----------|-----------|---------|
| Autoload script file | `PascalCase.gd` | `GameManager.gd`, `AudioManager.gd` |
| Autoload class name | `PascalCase` | `class_name GameManager` |
| Autoload node name | `PascalCase` | `GameManager`, `AudioManager` |

### Autoload rules

- Name autoloads after their responsibility: `GameManager`, `SaveManager`, `AudioManager`, `LocalizationManager`.
- Use `class_name` so they can be referenced globally without explicit node paths.

## Folder and directory naming

| Category | Convention | Example |
|----------|-----------|---------|
| Project folders | `snake_case`, no leading dot | `assets/`, `scenes/`, `scripts/`, `audio/` |
| Hidden Godot folders | `.godot/` (do not rename or create hidden folders) | `.godot/` |
| Folder names | Lowercase, plural where appropriate | `textures/`, `fonts/`, `levels/`, `ui/` |

### Folder rules

- Use lowercase `snake_case` for folders. Do not start folder names with a dot (except `.godot/` which Godot manages internally).
- Use plural nouns for folders containing multiple items: `scenes/`, `scripts/`, `audio/`, `textures/`.
- Avoid spaces in folder names.

## Resource naming

| Category | Convention | Example |
|----------|-----------|---------|
| Resource files | `PascalCase.tres` or `snake_case.tres` | `PlayerStats.tres`, `wood_sword.tres` |
| PackedScene resources | `PascalCase.tscn` | `Enemy.tscn`, `Level1.tscn` |
| Font/Theme resources | `snake_case` | `default_font.tres`, `ui_theme.tres` |
| Shader resources | `snake_case` | `water_shader.gdshader`, `toon.gdshader` |

## Enum naming

| Category | Convention | Example |
|----------|-----------|---------|
| Enum type | `PascalCase` | `enum Element { FIRE, WATER, EARTH, AIR }` |
| Enum values | `UPPER_SNAKE_CASE` | `FIRE`, `WATER`, `EARTH`, `AIR` |

### Enum rules

- Enum type names use `PascalCase`.
- Enum values use `UPPER_SNAKE_CASE`.

## File naming summary

| File type | Extension | Convention | Example |
|-----------|-----------|-----------|---------|
| Scene | `.tscn` | `PascalCase` | `MainMenu.tscn` |
| Script | `.gd` | `PascalCase` | `main_menu.gd` |
| Resource | `.tres` | `PascalCase` or `snake_case` | `GameSettings.tres` |
| Shader | `.gdshader` | `snake_case` | `sprite_flash.gdshader` |
| Font | `.tres` / `.ttf` | `snake_case` | `pixel_font.tres` |
| Translation | `.csv` / `.po` | `snake_case` | `en.csv`, `fr.po` |

## Anti-patterns (avoid these)

- `camelCase` variables or functions: `moveSpeed`, `takeDamage` → use `move_speed`, `take_damage`
- `PascalCase` variables: `PlayerSpeed`, `Health` → use `player_speed`, `health`
- Leading dots on project folders: `.assets`, `.scenes` → use `assets/`, `scenes/`
- Abbreviations that are unclear: `tmp`, `data`, `stuff` → use descriptive names
- Node names that don't match their scene file: scene `Enemy.tscn` with root node named `Mob`
- Spaces in names: `My Level.tscn`, `Player Script.gd`

## Quick reference

```
Nodes / Scenes:        PascalCase  →  Player.tscn, HealthBar
Scripts:               PascalCase  →  player.gd, class_name Player
Variables:             snake_case  →  move_speed, is_alive
Constants:             UPPER_SNAKE_CASE  →  MAX_HEALTH
Functions:             snake_case  →  take_damage(), _ready()
Private helpers:       _snake_case  →  _calculate_damage()
Signals:               snake_case  →  health_changed, enemy_spawned
Autoloads:             PascalCase  →  GameManager
Folders:               snake_case  →  assets/, scenes/, scripts/
Enums:                 PascalCase type, UPPER_SNAKE_CASE values
Resources:             PascalCase or snake_case  →  PlayerStats.tres
```

Apply these conventions consistently across your Godot project. When working in an existing project, follow the project's established conventions even if they differ slightly from this guide.