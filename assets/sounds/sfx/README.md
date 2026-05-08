# assets/sounds/sfx/

One-shot sound effects triggered by interactions. Referenced in `settings.json` under `soundEffects[key].url`.

Each entry also has a `volume` float (0.0–1.0) stored in settings.

## Expected Files

| settings.json key | Suggested filename     | Triggered by                          |
|-------------------|------------------------|---------------------------------------|
| `pickup`          | `pickup.mp3`           | Character picks up an item            |
| `drop`            | `drop.mp3`             | Item dropped / placed                 |
| `trashThrow`      | `trash-throw.mp3`      | Throwing item toward trash            |
| `trashCan`        | `trash-can.mp3`        | Item lands in trash                   |
| `fridgeOpen`      | `fridge-open.mp3`      | Fridge / vending machine opened       |
| `cdInsert`        | `cd-insert.mp3`        | CD inserted into player               |
| `cdEject`         | `cd-eject.mp3`         | CD ejected                            |
| `lampClick`       | `lamp-click.mp3`       | Lamp toggled on/off                   |
| `yawn`            | `yawn.mp3`             | Character yawn (low energy/boredom)   |

## How URLs are stored in settings.json

After placing your files here, update `settings.json` so each sound points to its path:

```json
"soundEffects": {
  "pickup": { "url": "assets/sounds/sfx/pickup.mp3", "volume": 0.6 },
  "drop":   { "url": "assets/sounds/sfx/drop.mp3",   "volume": 0.5 },
  ...
}
```

> **Note:** The saved settings file may have empty `url` values (`""`) or stale `blob:` URLs from a previous session — these need to be updated to the static paths above before shipping.

## Format & Quality

- **MP3 at 128kbps** is fine for all sfx
- Keep files short — most sfx should be under 2 seconds
- Normalize volume to around -6dBFS peak before export so the in-game volume slider has useful range
