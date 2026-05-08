# assets/textures/

Image files for surfaces in the bedroom scene. Referenced by `fileName` in `settings.json` under the `textures` key. Each texture also stores `tileX` / `tileY` repeat values in settings — those are preserved and don't need to be in the filename.

## Current Textures

| settings.json key | Expected filename              | Applied to       | Notes                         |
|-------------------|-------------------------------|------------------|-------------------------------|
| `floor`           | `GPAE01_282ad184_14.png`      | Floor plane      |                               |
| `rug`             | `grey-carpet-background.jpg`  | Rug mesh         | ⚠ was ~25MB — compress/replace |
| `wall_left`       | `GPAE01_1fa8e3a1_14.png`      | Left wall        |                               |
| `wall_right`      | `GPAE01_5f64d2c7_8.png`       | Right wall       |                               |
| `poster_group`    | `amazing poster.png`          | Poster on wall   | replace with final artwork    |

## Swapping Textures

You can swap any texture at runtime by dragging a new image onto the texture slot in the debug panel. To make a swap permanent, replace the file here and update `fileName` in `settings.json` to match.

## Compression

Large textures (especially the rug) should be downsized before shipping. Recommended tools:

**squoosh.app** (browser, no install)
- Resize to 1024×1024 or 2048×2048
- Export as WebP at ~80% quality

**ImageMagick (CLI)**
```bash
# Resize and convert to WebP
magick grey-carpet-background.jpg -resize 1024x1024 -quality 80 grey-carpet.webp

# Or just resize in place
magick input.png -resize 2048x2048\> output.png
```

Target sizes:
- Tiling textures (floor, walls): 512×512 to 1024×1024 PNG or WebP
- Rug: 1024×1024 WebP — from ~25MB down to under 200KB
- Poster: 512×512 or 1024×1024 PNG

## Format Notes

The game loads textures via `THREE.TextureLoader` which supports PNG, JPG, and WebP. WebP is preferred for anything photo-based (rug, poster). PNG is fine for tiling/pixel-art textures.
