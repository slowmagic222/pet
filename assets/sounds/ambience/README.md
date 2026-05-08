# assets/sounds/ambience/

Looping background audio for the bedroom environment. Referenced in `settings.json` under `ambience[key].url`.

Each entry also has a `volume` float (0.0–1.0) stored in settings.

## Expected Files

| settings.json key | Suggested filename      | Description                                      |
|-------------------|-------------------------|--------------------------------------------------|
| `room`            | `ambience-room.mp3`     | General indoor room tone, always present         |
| `fridgeHum`       | `fridge-hum.mp3`        | Low electrical hum from the vending machine      |
| `night`           | `ambience-night.mp3`    | Night-specific layer (crickets, quieter, etc.)   |
| `outside`         | `ambience-outside.mp3`  | Outside layer — rain, city, wind, etc.           |

## How URLs are stored in settings.json

After placing your files here, update `settings.json`:

```json
"ambience": {
  "room":      { "url": "assets/sounds/ambience/ambience-room.mp3",    "volume": 0.3 },
  "fridgeHum": { "url": "assets/sounds/ambience/fridge-hum.mp3",       "volume": 0.15 },
  "night":     { "url": "assets/sounds/ambience/ambience-night.mp3",   "volume": 0.25 },
  "outside":   { "url": "assets/sounds/ambience/ambience-outside.mp3", "volume": 0.2  }
}
```

> **Note:** The saved settings file may have empty `url` values (`""`) from a previous session — update to static paths above before shipping.

## Format & Quality

- **MP3 at 96–128kbps** — ambience loops don't need high bitrate
- Files should loop seamlessly — use a DAW to trim to a clean loop point
- Recommended length: 30s–2min (shorter loops with smooth crossfade points are fine)
- Keep them quiet relative to sfx — the `volume` in settings compensates, but it's easier to work with naturally quiet source files
