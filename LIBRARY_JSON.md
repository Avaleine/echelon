# Echelon's library.json

Echelon (the Helldivers 2 mod manager) keeps a small file that describes the user's mod library, so other tools can read it: which mods there are, what they are called, which of their files are in the game right now and under which name, and which options are switched on. It is an open format. Read it however you like; please don't write to it.

## Where it is

```
%APPDATA%\Echelon\library.json
```

Under Proton or Wine, `%APPDATA%` is inside the prefix Echelon runs in (`.../pfx/drive_c/users/steamuser/AppData/Roaming/Echelon/library.json`).

It exists from Echelon 0.36.2 on. Echelon rewrites it, all at once, whenever the library, the active profile or what is deployed in the game changes, and only when something in it changed. It is UTF-8 JSON.

## Format

```json
{
  "format": "echelon-library",
  "version": 1,
  "mods": [
    {
      "id": "78eae3c5a284",
      "name": "Aggro Counter v1.4",
      "folder": "C:\\Users\\me\\AppData\\Roaming\\Echelon\\mods\\Aggro Counter v1.4 (78eae3c5a284)",
      "enabled": true,
      "deployed": true,
      "sets": [
        {
          "hash": "9ba626afa44a3aa3",
          "files": ["opt/0/9ba626afa44a3aa3.patch_0", "opt/0/9ba626afa44a3aa3.patch_0.gpu_resources"],
          "deployed_as": "9ba626afa44a3aa3.patch_0"
        },
        {
          "hash": "9ba626afa44a3aa3",
          "files": ["opt/1/9ba626afa44a3aa3.patch_0"],
          "deployed_as": null
        }
      ],
      "options": [
        {
          "name": "Style",
          "enabled": true,
          "sets": [],
          "choices": [ {"name": "Native", "sets": [0]}, {"name": "Pixel", "sets": [1]} ],
          "selected": 0
        }
      ]
    }
  ]
}
```

| Field | Meaning |
|---|---|
| `format`, `version` | Always `"echelon-library"` and `1` for this layout. A breaking change would raise `version`. |
| `mods` | Every mod in the user's library, whether or not it is in a profile. |
| `id` | Echelon's id for the mod. Stable for the life of the mod. |
| `name` | The mod's name as shown in Echelon (the user can rename it). |
| `folder` | Full path of Echelon's copy of the mod. |
| `enabled` | Switched on in the user's active profile. |
| `deployed` | All of the mod's chosen files are in the game folder right now. |
| `sets` | The mod's patch sets: one archive change each, in the mod's own order. |
| `sets[].hash` | The game archive the set changes (the 16 hex characters of the file name). |
| `sets[].files` | The set's files, relative to `folder`, with `/` as separator: the main `.patch_N` file first, then `.gpu_resources` / `.stream` if there are any. |
| `sets[].deployed_as` | The main file's name in the game's `data` folder right now, e.g. `"9ba626afa44a3aa3.patch_3"`, or `null` if this set isn't deployed. Its `.gpu_resources` / `.stream` files use the same name plus their extension. |
| `options` | The mod's options (empty list if it has none). |
| `options[].enabled` | Switched on in the active profile. |
| `options[].sets` | Indexes into `sets` that the option always installs. |
| `options[].choices` | For pick-one options: each choice's name and the indexes into `sets` it installs. Empty for a plain on/off option. |
| `options[].selected` | Index into `choices` of the chosen one, or `null` when the option has no choices. |

## Common use: which mod is this file in the game folder?

Build a lookup from `deployed_as` to the mod name:

```python
import json, os
path = os.path.join(os.environ["APPDATA"], "Echelon", "library.json")
lib = json.load(open(path, encoding="utf-8"))
owner = {s["deployed_as"]: m["name"]
         for m in lib["mods"] for s in m["sets"] if s["deployed_as"]}
# owner["9ba626afa44a3aa3.patch_3"] -> "Aggro Counter v1.4"
```

Strip `.gpu_resources` / `.stream` from a file name before looking it up. Files in the game folder that aren't in the lookup were not put there by Echelon.

## Questions

Ask Avaleine on the Echelon Discord (https://discord.gg/ybSbUjXDht) or on Echelon's Nexus or AyakaMods page. Format changes will be announced there first.
