# Lean production commands

Use the installed project-pinned HyperFrames executable, Node and FFmpeg. Do not
upgrade the global runtime as part of making a film. Scripts below are relative
to this Skill directory; use absolute script paths from a different cwd.

One project contains originals, a compact plan, compositions, and shared assets.
`broll-plan.json` example (adjust to the actual SRT, never fabricate cue times):

```json
{
  "schemaVersion": "lean-1",
  "title": "One clear idea",
  "inputs": {"srt": "input/original.srt", "design": "input/design.md"},
  "profile": {"width": 3840, "height": 2160, "fps": 30},
  "shots": [{
    "id": "S01", "startMs": 0, "endMs": 6000, "cueIds": [1],
    "intent": "Understand the actual product change",
    "subject": "The supplied before and after screenshots",
    "material": {"route": "provided"},
    "composition": "compositions/S01.html"
  }]
}
```

Group cues by meaning. Cover zero through the last cue end, including gaps, with
contiguous shots. Every referenced cue must overlap its shot. Short projects can
have one shot. `cueIds` are one-based file order, independent of printed SRT
numbers. The renderer quantizes global boundaries to video frames so rounding
does not accumulate across shots; the plan keeps original milliseconds.
Defaults are 4K/30; respect portrait and other explicit profiles.
Record selected material/font source, licence and local file in a short shared
asset index. Never fabricate product evidence or silently buy generated media.

Each HTML file has a sized root with its shot id, profile width/height and local
duration `(endMs-startMs)/1000`. With the pinned HyperFrames **0.7.104** renderer,
use project-root paths such as `assets/photo.jpg` inside compositions, not
`../assets/photo.jpg`. Declare local `@font-face` rules in each HTML; linking a
shared font stylesheet alone does not satisfy this version's strict check.
Explicitly initialize and register the finite seekable timeline:

```js
window.__timelines = window.__timelines || {};
const tl = gsap.timeline({ paused: true });
// Add the shot's meaningful motion using locally available GSAP.
window.__timelines['S01'] = tl;
```

These pinned-version requirements take precedence over newer general
HyperFrames examples. Use local assets; rendering must not fetch media, scripts
or fonts from the network.

```sh
node scripts/lean-plan.mjs --project /path/to/project
node scripts/lean-render.mjs --project /path/to/project --quality draft --hyperframes /path/to/hyperframes
node scripts/lean-render.mjs --project /path/to/project --quality final --hyperframes /path/to/hyperframes
```

Draft and final have separate output folders. Draft uses at most 15fps and half
the output width/height. For a 1080p source, this pinned runtime still captures
at the source raster before downscaling; it has no sub-1080p capture preset.
A draft never counts as final media. After a local repair, rerun the same command; use
`--shots S02` to work on a selected shot. A complete preview requires all shots.
The renderer records actual work/reuse/time and refreshes previews after changed
inputs. It validates media once per changed render and reuses unchanged results.

View the generated contact sheets and moving preview. Correct unreadable text,
vague subjects, missing media, misleading imagery and rough motion in source.
Only investigate a suspicious animation window more deeply when needed. The
creator's brief completion note states what was viewed and what was repaired.
