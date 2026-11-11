---
name: godot-init-project
description: "Initialize or organize a Godot game project using the included domain-oriented folder structure. Use when creating a new Godot project, scaffolding project directories, or restructuring an existing project."
---

# godot-init-project

Set up a Godot project with a maintainable, domain-oriented structure based on [product_structor.txt](./product_structor.txt).

## Workflow

1. Inspect the target directory and the Godot project configuration before changing anything. Preserve existing files and adapt the structure rather than overwriting project work.
2. Read `product_structor.txt` and use it as the source of truth for directory names, responsibilities, and architecture decisions.
3. Create the required directories at the project root:
   - `addons/`, `assets/`, `autoload/`, `common/`, `entities/`, `levels/`, `resources/`, `systems/`, `translations/`, and `ui/`.
   - Add the subdirectories described in the reference, such as `assets/audio/`, `common/components/`, and `levels/base/`.
4. Keep the architectural boundaries clear:
   - `ui/` contains UI scenes; `common/ui/` contains reusable UI widgets.
   - `systems/` contains game-wide systems; `common/services/` contains reusable services.
   - `entities/` contains scenes meant to be instanced into levels, not the game's entry scene.
   - `levels/environments/` contains playable levels, while `levels/test/` is for development sandboxes.
5. For a new project, place the entry scene at `levels/base/main.tscn` and configure `run/main_scene` in `project.godot` to `res://levels/base/main.tscn`. Do not replace an existing entry scene without confirming the change is intended.
6. Only create example scripts, scenes, or resources when requested or needed for a runnable starter. Do not create empty placeholder files just to represent the reference tree.
7. Verify the resulting directory layout and, when project configuration was changed, confirm the main scene path is valid.

## Notes

- Treat the included structure as a starting convention; preserve project-specific organization where it already works.
- Do not add autoloads, plugins, or Godot resources merely because their names appear in the reference. Configure them only when requested.
