# Erduo B-roll Loop Engineering

**Turn original SRT and design into polished, editable B-roll with meaningful motion.**

[简体中文](README.md) · English · [日本語](README.ja.md) · [한국어](README.ko.md) · [繁體中文](README.zh-TW.md)

> `main` uses a quality-first creative relay. The latest versioned Release is still [v1.0.1](https://github.com/erduo1998-cell/erduo-broll-loop-engineering/releases/tag/v1.0.1); its archives retain the older workflow. Install from this repository for the current flow.

## Workflow

Original SRT + design + optional media → independent Director → fresh chapter creators → scripted rendering and independent visual review → targeted repair by the original creator → final shots, complete preview and editable project.

Picture quality comes first. Even short films retain separate directing, creation and review contexts. Creators receive the complete original inputs, compact shared direction, their shot cards and adjacent seams; the parent conversation and entire Skill library are not their handoff. Divide longer films into coherent chapters, parallelizing only with clear file ownership and shared visual rules. Add a material specialist when needed.

The parent runs timing checks, rendering, decode, caching and assembly. Creators and an independent reviewer inspect actual media; successful rendering cannot approve aesthetics. Use a representative passage for an uncertain style, without a mandatory sample count. Preserve requested review stops and complete necessary repairs.

Three compact motion references and an original runnable example make state changes and focus handoffs concrete. They are not a fixed paper-card skin. Use recognizable media when it carries the subject. SVG is appropriate for clear relationships, charts, masks and paths, not an automatic substitute for the subject.

## Install

For the current main workflow:

```sh
git clone https://github.com/erduo1998-cell/erduo-broll-loop-engineering.git
cd erduo-broll-loop-engineering
./Install.command
```

The installer prepares the pinned HyperFrames environment, browser, FFmpeg and Skill links. Keep the installation directory and restart Codex or Claude Code afterward. The older v1.0.1 downloadable archives follow their own README. Uninstall retains user data by default.

```sh
node scripts/doctor.mjs
node scripts/uninstall.mjs
```

## First request

```text
Use erduo-broll-loop-engineering to turn this original SRT and design into B-roll.
Keep the Director, chapter creators and visual reviewer in separate contexts.
Prioritize picture quality; view and repair the real output before delivering the complete preview.
```

The deliverable includes editable HTML/CSS/JS, media sources, ordered H.264 shot files and a complete preview. Default final output is silent 3840×2160 at 30fps; explicit user dimensions/rate take priority. Full subtitles and music are not added automatically.

## Evidence and limits

In one 32-second same-input experiment, an independent Sol review of contact sheets and sampled seams preferred the relay, and the user selected it. Both outputs were 1080p/30fps and passed real decode. A change to shot S02 took 8.569 seconds to update; the other three videos remained byte-identical.

Time/token savings are **not established**: the relay's model phase took 611.281 seconds versus 325.136 seconds, including environment failures and unnecessary searches. This is not a clean end-to-end speed benchmark. The task helper prepares focused input files; it does not automatically remove host-injected context or enforce a sandbox. See [validation](docs/LEAN-WORKFLOW-VALIDATION.md).

Existing Recipe/runtime-plan v1–v4 projects and explicit Remotion/hybrid requests keep the [legacy route](erduo-broll-loop-engineering/references/legacy-production.md). Do not silently migrate them. The 152 Shotcraft cards are optional references, not 152 validated HyperFrames components. Long-film gains, Windows rendering, editor GUI workflows and cross-backend visual parity remain unverified for this flow.

## Development

```sh
npm test
npm run task:creative -- --project /path/to/project --role director
npm run plan:lean -- --project /path/to/project
npm run render:lean -- --project /path/to/project --quality draft
```

[Production commands](erduo-broll-loop-engineering/references/lean-production.md) · [Motion references](erduo-broll-loop-engineering/references/motion-patterns.md) · [Privacy](PRIVACY.md) · [Support](SUPPORT-MATRIX.md) · [Changelog](CHANGELOG.md) · [MIT License](LICENSE)

Author: Liu Ran / Erduo · [GitHub](https://github.com/erduo1998-cell)
