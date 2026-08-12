# FNF Modchart Editor (Web) — Troll Engine / Psych

Standalone browser-based modchart / sequence editor for Friday Night Funkin' mods (Troll Engine + Vanilla Psych exports).

**Live demo (GitHub Pages):** once published, open the repository's Pages URL (e.g. `https://YOURUSER.github.io/REPO/`).

## Features

- Timeline keyframe editor for modifiers (transform, drunk, tipsy, bumpy, reverse, confusion, scale, stealth, etc.)
- Continuous functions (sine / cosine / pulse / saw / square / hold)
- Timed events: `queueFuncOnce`, `queueFunc`, blank mods, ProxyField helpers
- Live canvas preview of receptors + falling notes with modifier paths
- Chart JSON import (Psych / Troll formats) for note preview
- Audio (Inst/Vocals) scrubbing
- Export:
  - **Troll Engine** Lua / HScript
  - **Vanilla Psych** Lua (+ Enhanced Modchart Template)
  - sequence.json (re-importable)
- Undo / redo, snap, zoom, import/export scripts

## Deploy to GitHub Pages

1. Create a new GitHub repository (public).
2. Upload the contents of this folder (or push via git):
   ```bash
   git init
   git add .
   git commit -m "FNF Modchart Editor for GitHub Pages"
   git branch -M main
   git remote add origin https://github.com/YOURUSER/YOURREPO.git
   git push -u origin main
   ```
3. In the repo **Settings → Pages**:
   - Source: **Deploy from a branch**
   - Branch: `main` / root (`/`)
4. Wait ~1 minute, then open `https://YOURUSER.github.io/YOURREPO/`.

The site is pure static HTML/JS/CSS — no build step required. All logic is self-contained in `index.html`.

## Local use

Keep the `assets/` folder next to `index.html` and open the page in any modern browser (Chrome / Edge / Firefox).  

For best results (especially with audio + sprites) serve the folder with a tiny static server, e.g.:

```bash
npx serve .
# or
python -m http.server 8000
```

Opening via `file://` still works for the editor itself; sprites simply fall back to procedural arrows if the browser blocks local image loads.

## Assets & real sprites

The `assets/` folder ships the standard FNF note spritesheets (NOTE_assets, noteSplashes, QUANT variants, alphabet, checkboxes, event arrows, backdrop, etc.).

The live preview now **loads the real note sprites** by default:

- Receptors → `arrowLEFT / DOWN / UP / RIGHT`
- Falling notes → `purple / blue / green / red` heads
- **Hold notes** → tiled `hold piece` sprites + `hold end` tip (follows curved paths from modifiers)
- Event markers on the timeline use `eventArrow.png`
- Soft tiled `backdrop.png` under the playfield

A checkbox **“Use real note sprites”** in the Chart Preview panel lets you switch back to the original procedural arrows + line holds at any time. If the images fail to load (e.g. opening the single HTML via `file://` without the assets folder), the editor automatically falls back to procedural drawing.

### Resizable panels

Drag the **three-dot grips**:

- **Vertical grip** (between preview and settings) → both the preview and the inspector scale in real time.
- **Horizontal grip** (above the timeline) → timeline height vs preview area scale in real time.

Sizes are remembered in `localStorage` across sessions.

## Credits

- Modchart math / modifiers inspired by Troll Engine (TheZoroForce240 & contributors)
- Enhanced Psych template based on common community modchart patterns
- Web editor UI & sequence system: standalone HTML version

---

Open the page, load a chart + audio, add tracks/keyframes/events, then export Lua/HScript for your engine.
