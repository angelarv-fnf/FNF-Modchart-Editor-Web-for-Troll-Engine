# FNF-Modchart-Editor-Web-for-Troll-Engine
check out the github.io version

this is still probably a **WIP**, but you can still use it if you want lol

## Engines You Should Use:
* Recommended Engine Version: **"v0.2.0-beta.1"** or higher
* Recommended Engine: "Troll Engine"

## How to Find Troll Engine Release Tags (or something like that):
https://github.com/troll-slaiyers/FNF-Troll-Engine/tags

**If you want to stick with the v0.2.0-beta.1, here it is:**
* https://github.com/troll-slaiyers/FNF-Troll-Engine/releases/tag/0.2.0-beta.1

*oh, and also here is my github.io link lol:*
* https://angelarv-fnf.github.io/FNF-Modchart-Editor-Web-for-Troll-Engine/

---

## Features

- Visual timeline with keyframes (add, move, delete, multi-select)
- Multiple tracks, each targeting a modifier + player/opponent/lane
- Live canvas preview of receptors with applied modifiers
- Snap quantization (1/4 → 1/192) and zoom
- Undo / Redo
- Audio import (Inst OR Vocals) for scrubbing & playback
- Continuous modifier functions (sine, cosine, linear, pulse, saw, square, hold, etc.)
- Export formats:
  - **Lua** (Troll Engine style)
  - **HScript**
  - **JSON** (sequence.json)
- Import:
  - JSON sequences
  - Lua / HScript (best-effort parse of `queueSet` / `queueEase`)

### Supported modifiers (partial list)
`transformX/Y/Z`, `confusionOffset`, `alpha`, `dark`, `reverse`, `flip`, `invert`, `centered`, `mini`, `tiny`, `squish`, `stretch`, `tipsy`, `drunk`, `bumpy`, `zigzag`, `sawtooth`, `square`, `bounce`, `tornado`, `xmod`, `opponentSwap`, `stealth`, `sudden`, camera mods, and many more.

---

HOW TO USE MODCHART EDITOR:

1. Open the editor (local HTML or the GitHub Pages link above).
2. Set **Song** name and **BPM** in the Sequence panel.
3. (Optional) Load an audio file with the **Audio** button.
4. Select or add tracks. Choose a **Modifier** and **target** (both / player / opponent / lane0-3).
5. Click on the timeline (or press **Enter**) to place keyframes at the playhead.
6. Select a keyframe to edit its **value**, **mode** (Set / Ease / Both), **API** (normal / percent), **ease type**, and **duration**.
7. Use the continuous panel if you want a modifier that runs every frame between two steps.
8. Preview the receptors in the top canvas while scrubbing or playing.
9. Export:
   - **Lua** → drop into your Troll Engine modchart as a script
   - **HScript** → alternative script format (probably not working i think, still in the works just to make it fully functionable i think, thats probably why, i think im using the troll-slaiyers version of troll engine instead of the riconuts version i think)
   - **JSON** → save / share the sequence data

### Keyboard shortcuts

| Key | Action |
|-----|--------|
| `Space` | Play / Pause |
| `Enter` | Add keyframe at playhead |
| `Delete` / `Backspace` | Delete selected keyframes |
| `Ctrl/Cmd + Z` | Undo |
| `Ctrl/Cmd + Y` / `Ctrl/Cmd + Shift + Z` | Redo |
| `Ctrl/Cmd + A` | Select all keyframes in current track |
| `Z` / `X` | Zoom in / out |
| `←` / `→` | Change snap quantization |

---

## Export Notes (Troll Engine)

The Lua exporter generates a ready-to-use script with:

- `queueSet` / `queueEase` (and `P` variants)
- Continuous function support via `queueContFunc`
- Standard runtime hooks (`onCreate`, `onStepHit`, `onUpdate`, camera zoom handling, etc.)

Only safe utility/camera mods are registered as blank mods so core note-effect modifiers keep their real engine implementations.

---

## Local usage

Just open the HTML file in any modern browser (Chrome / Firefox / Edge recommended).  
No build step or server required.

---

## Credits / License

Created as a faithful web port of my SequenceEditorState concepts for Troll Engine. (yes, it was a concept but i moved it to the web so it's easier)

have fun modcharting lol byee

Reminder:
If you find bugs or want features, open an issue or PR on the repo.
