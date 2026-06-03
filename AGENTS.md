# Repository Guidelines

## Project Structure & Module Organization
This repository is an Assetto Corsa car package for `tcr_peugeot_308_gti`. The root directory contains compiled car models (`tcr_308.kn5`, LOD variants, rollover meshes), packed physics in `data.acd`, and shared textures such as `logo.png` and the tyre/body shadow PNGs. `animations/` stores `*.ksanim` files, `sfx/` contains FMOD banks plus `GUIDs.txt`, `ui/ui_car.json` defines showroom metadata, and `texture/flames/` holds exhaust flame assets. Each livery lives in `skins/<skin_name>/` with files such as `livery.png`, `preview.jpg`, `ui_skin.json`, and optional `skin.ini`.

## Build, Test, and Development Commands
There is no build system or automated test suite in this repo. Use lightweight inspection commands while editing:

- `find skins -mindepth 1 -maxdepth 1 -type d | sort` lists available skins.
- `sed -n '1,80p' ui/ui_car.json` reviews car metadata before packaging.
- `sed -n '1,80p' skins/00_Base/ui_skin.json` checks livery metadata structure.

For functional validation, copy the folder into `content/cars/` in an Assetto Corsa install or open it through Content Manager, then verify the car loads, previews render, and sounds resolve without errors.

## Coding Style & Naming Conventions
Preserve the existing flat Assetto Corsa layout and keep filenames lowercase where the repo already does so. Follow current naming patterns: root assets use descriptive names like `tcr_308_lod_c.kn5`, skin folders use stable identifiers such as `00_Base` or `308_Peugeot_308_gti_official`, and preview files stay named `preview.jpg`. Use 2-space indentation in JSON and keep key names consistent with existing metadata (`skinname`, `drivername`, `number`).

## Testing Guidelines
Test changes in game. At minimum, verify:

- the car appears in the UI with correct `ui/ui_car.json` data,
- edited skins load with the expected preview and livery textures,
- SFX banks and `GUIDs.txt` still map to `event:/cars/tcr_peugeot_308_gti/...`.

If you touch physics, unpack and validate `data.acd` with your usual Assetto Corsa tooling before repacking.

## Commit & Pull Request Guidelines
Git history is not included in this exported directory, so no project-specific commit convention can be inferred here. Use short imperative commit subjects, for example `Add fantasy skin preview` or `Update Peugeot UI specs`. Pull requests should summarize changed assets, list in-game validation performed, and include screenshots whenever visuals, UI, or liveries change.
