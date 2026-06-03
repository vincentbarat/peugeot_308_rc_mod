# Repository Guidelines

## Project Structure & Module Organization
This repository is an Assetto Corsa car mod for the Peugeot 308 TCR. Root-level `.kn5` files are the main car and LOD meshes (`tcr_308.kn5`, `tcr_308_lod_*.kn5`); rollover meshes and shadow textures also live at the root. Use `animations/` for `.ksanim` files, `sfx/` for FMOD banks and `GUIDs.txt`, `ui/` for car metadata such as `ui/ui_car.json`, and `texture/flames/` for flame textures. Liveries live in `skins/<skin_name>/` and usually include `livery.png`, `preview.jpg`, and `ui_skin.json`. Physics data may appear packed as `data.acd` or unpacked in `data/`; keep those in sync.

## Build, Test, and Development Commands
There is no repo-local build or test runner. Typical maintenance commands are:

```bash
git status --short
git diff --stat
find skins -maxdepth 1 -mindepth 1 -type d | sort
```

Use `git status --short` to confirm exactly which assets changed, `git diff --stat` to review binary-heavy commits, and `find ...` to inspect available skin packages. Validate changes in Assetto Corsa or Content Manager by loading the car, checking that skins render correctly, and confirming the UI, sounds, and animations still load.

## Coding Style & Naming Conventions
Preserve the game’s expected filenames and directory layout; many files are loaded by exact name. Keep JSON formatted with 2-space indentation, preserve existing INI key casing, and prefer lowercase or established asset naming such as `lights.ini`, `preview.jpg`, and `tyre_0_shadow.png`. New skin folders should use a clear prefix plus descriptor, for example `91_Peugeot_308_fantasy`.

## Testing Guidelines
Test every asset change in-game. For physics edits, ensure the car boots without errors, torque/power behavior matches expectations, and no stale unpacked `data/` files override `data.acd`. For skins, verify `preview.jpg`, number plates, crew textures, and `ui_skin.json` metadata. There is no automated coverage target; manual validation is the release gate.

## Commit & Pull Request Guidelines
Keep commits short, imperative, and specific, matching the existing history: `Revert to original TCR`, `Ignore .DS_Store`. Group one logical change per commit, especially for physics, meshes, or liveries. Pull requests should summarize gameplay impact, list edited paths, and include screenshots for visual changes. If `data/` was unpacked for editing, note whether the release should ship `data/`, `data.acd`, or both.
