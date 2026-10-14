---
name: short-drama-toolkit
version: 1.1.2
description: A WorkBuddy Pay Skill for short-drama pre-production. Script doctor, character bios, Hollywood-format screenplay, shot breakdown, AI storyboard, location scouting, shooting schedule, and video preview — all the documents a director needs before the first slate.
agent_created: true
---

> ⚠️ **Showcase / documentation mirror only.**  
> This file documents the workflow and taste standards used by the skill. The runnable implementation (including the per-use payment gate) is published on SkillHub:  
> [https://skillhub.cn/skills/user_839f3063/short-drama-toolkit](https://skillhub.cn/skills/user_839f3063/short-drama-toolkit)

# Short-Drama Toolkit — Director's Field Manual

A complete pre-production pipeline for short-form drama / micro-drama, from script revision to the day-before-shoot package.

## When to Use

- External notes (AI feedback, actor voice messages) need to land as a real revised draft
- A new script needs an overall health diagnosis before any rewrite
- Actors need a Hollywood-standard screenplay for table reads
- The script is locked and needs to be broken down into shots
- You need a Cadrage-style AI storyboard PDF
- A single shooting day needs a schedule with makeup/wardrobe continuity
- You are location-scouting and need a 28-field decision record
- Characters feel flat and need a full 3-layer bible
- Static boards are approved and you want an optional motion preview

## Director's Taste Red Lines (read before touching any file)

0. **Script first.** Content quality is the highest law. Formatting, boards, and schedules are downstream of the script — fix the story before you polish the pipe.
1. **Storyboards must be readable at a glance.** Abstract stick-figure or silhouette boards get rejected; generate per-shot AI art with a hand-drawn comic look.
2. **Batch only after samples.** Run 3 style samples (close / medium / wide), get director approval, then report the full budget before batching.
3. **Dialogue balance = structural health.** If a main character goes two episodes without a line, suspect structure, not coincidence.
4. **Formatting serves the first reader.** A screenplay is for actors to read aloud — cue columns and dialogue columns must be visually separated. "Hard to read" is a rejection reason.
5. **External notes checked line by line.** Do not absorb them as general guidance; mark each one satisfied / not satisfied.
6. **Fix upstream bugs before downstream output.** Verify logic consistency before generating boards, schedules, or previews.
7. **Archive only head and tail.** Keep the original and the final; delete intermediate files without regret when the user says delete.
8. **Video preview is silent by default.** Code-generated BGM tends to sound cheap or uncanny. Add music only when the user supplies a properly licensed track. Sound effects live on their own tracks.

## End-to-End Workflow

### Step 0: Read the judgment handbook

Before any output, read `references/taste-and-judgment.md`. The 8 red lines above are a summary; the handbook is the full record of user corrections and project-specific standards.

### Step 1: Script revision

**Diagnose first.** Run the script-doctor evaluation from `references/script-doctor.md` (5 categories, 23 items, 4-grade scale, 100-point total, 7-dimension revision notes). Confirm the issue list with the director before rewriting.

If character scores are low (motivation contradictions, tool-like roles, intelligence drops), rebuild the character using `references/character-sheet.md` (59 items across physical / psychological / social layers). The "decisive past moment" field is usually the source of the protagonist's single dominant motivation.

Principles:
- Add dialogue and polish wording only; do not move locked blocking.
- Check external notes line by line: satisfied → mark ✓; not satisfied → embed new lines in existing shots.
- After revision, run a two-way check: every script line appears in the shot list, and every shot-list line traces back to the script.

### Step 2: Hollywood-format screenplay docx

Layout rules (full spec in `references/hollywood-format.md`):
- Scene headings: 12 pt bold, flush left
- Action lines: flush left
- Character cues: left indent ~150 pt, kept with the dialogue block
- Dialogue: left indent ~70 pt, right indent ~60 pt
- Parentheticals merged into the cue line
- Transitions: right aligned
- Line spacing 1.3
- Body: 黑体 / Heiti, US Letter paper

Verification: after every format change, run the format checker against the exported PDF and do not deliver until PASS.

### Step 3: Shot breakdown → shots.json

`shots.json` is the quality hub of the whole pipeline. The storyboard table, AI image generation, AI board PDF, and schedule all consume it.

Rules:
- **Never generate images directly from raw script text.** AI will default to medium shots, lose cutting logic, and ignore directorial intent.
- High-granularity input (existing shot/action hints): extract and structure, then design framing and camera movement.
- Low-granularity input (literary script only): translate to beats first, design shots per beat, and get director approval before freezing into `shots.json`.
- Lock character appearance in a fixed style prefix before batching.

### Step 4: AI storyboard generation

1. 3 style samples first, director approval second, batch third.
2. Prompts come from `shots.json` (framing / subject / light / mood), not from the script.
3. Target 1536×1024, report the full image-generation budget before running.
4. Rename outputs to `shot_NN.png` and verify zero missing frames.
5. Skip post-production cards (title / credits) for image generation; render them as black explanation cards during assembly.

### Step 5: AI storyboard PDF assembly

Center-crop to 1.85:1 (face bias toward top 35%), overlay camera-move marks, mark episode cut points, and lay out in Cadrage-style 8-panel Letter pages with two caption lines per frame.

### Step 6: Shooting schedule

Build the single-day schedule from real scouting data. Core rules:
- Makeup/wardrobe states must form continuous time intervals; switches only happen during transitions or meal breaks.
- Wound makeup is applied once and removed once.
- Never schedule "pre-injury" scenes inside the injured window.
- Transition times come from `references/scouting.md` (road conditions, gear transport, orientation, lighting window). If no scouting data exists yet, reserve a conservative 30-minute independent block plus a contingency block.
- Golden-hour scenes are reverse-scheduled from local sunset.
- VFX-heavy shots get extra coverage (wide / hand / close / insert).

### Step 7: Video preview (optional)

Turn static storyboards into a motion preview to align rhythm, shot duration, and transition feel. See `references/video-preview.md`.

Mandatory cost warning before starting:
> This runs image-to-video on every board. Dozens of shots can consume significant compute credits and take tens of minutes. If the static PDF is enough, skip this step. Confirm explicitly before batching.

Flow:
1. Per-shot image-to-video using the storyboard as first frame; motion prompt = camera move + visual description
2. Normalize duration from `shots.json` `dur` (crop or slow-motion + tail-frame hold)
3. Post-production cards: opening flash-forward from reversed ending clip; title / credits as black cards
4. Concatenate and mux audio; default silent (`-an`); only add user-supplied licensed BGM when explicitly requested

## License

Tiered license — see [LICENSE.txt](./LICENSE.txt):

- Documentation (SKILL.md, references/*): CC BY-NC-ND 4.0
- Code: proprietary, not included in this showcase repository

© 2026 南京新菁年影视科技有限责任公司（Nanjing New-Youth Film & Technology Co., Ltd.）. All rights reserved.
