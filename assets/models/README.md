# assets/models/

GLB files for all 3D objects in the scene. Each file is referenced by name in `settings.json`.

## Room Models

These replace the default geometry for named object groups in the scene.

| settings.json key | Expected filename                          | Notes                          |
|-------------------|--------------------------------------------|--------------------------------|
| `desk_group`      | `home_studio.glb`                          | ⚠ compress heavily, was ~70MB  |
| `tv_group`        | `crt-tv.glb`                               |                                |
| `sidetable_group` | `panasonic_sa-pm02_stereo_system.glb`      |                                |
| `fridge_group`    | `vending_machine.glb`                      | also used as snack item model  |
| `lamp_group`      | `lamp.glb`                                 |                                |
| `ball_toy`        | `duck_plush.glb`                           |                                |
| `water_bottle`    | `water_bottle.glb`                         |                                |

## Item / Consumable Models

Held and consumed by the character during interactions.

| settings.json key | Expected filename       | Notes                              |
|-------------------|-------------------------|------------------------------------|
| `snack`           | `vending_machine.glb`   | shared with fridge_group above     |
| `drink`           | `coffeecan.glb`         |                                    |
| `trash_drink`     | `coffeecan.glb`         | same model, used for trash state   |

## Character Model

| Expected filename  | Notes                                                        |
|--------------------|--------------------------------------------------------------|
| `character.glb`    | Loaded separately from settings. Must include animations:    |
|                    | `idle_neutral`, `walk`, `sleep` at minimum.                  |
|                    | See animation names in the debug panel → GLB Animations.     |

## Decoration Models

Any extra GLB files dragged into the scene via the debug panel (decorations) will also land here conceptually. Their filenames vary — they're stored in the `decorations` array in `settings.json`.

## Compression

All models should be processed with [gltf-transform](https://gltf-transform.dev/) before shipping:

```bash
npm install -g @gltf-transform/cli

# Basic optimize + draco compression
gltf-transform optimize input.glb output.glb --compress draco

# More aggressive — also resizes embedded textures
gltf-transform optimize input.glb output.glb --compress draco --texture-size 512
```

Target sizes:
- Character: under 3MB
- Room props: under 1MB each
- `home_studio.glb` (desk): target under 5MB after compression
