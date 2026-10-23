---
name: short-drama-toolkit
version: 1.3.0
description: A WorkBuddy Pay Skill for short-drama pre-production. Script doctor (with audience gender-fit diagnosis), character bios, Hollywood-format screenplay, shot breakdown, AI storyboard, location scouting, shooting schedule, and video preview — all the documents a director needs before the first slate. Now with Quick Start, Capability Scope, and FAQ.
agent_created: true
---

> ⚠️ **Showcase / documentation mirror only.**  
> This file documents the workflow and taste standards used by the skill. The runnable implementation (including the per-use payment gate) is published on SkillHub:  
> [https://skillhub.cn/skills/user_839f3063/short-drama-toolkit](https://skillhub.cn/skills/user_839f3063/short-drama-toolkit)

# Short-Drama Toolkit — Director's Field Manual

A complete pre-production pipeline for short-form drama / micro-drama, from script revision to the day-before-shoot package.

## Quick Start (first time, follow in order)

1. **Send the script to the AI** (txt / docx / md all work), with one line: "Use the short-drama director's toolkit to diagnose my script first."
2. **The first call triggers an Alipay payment** (¥6.8 CNY per project). Pay as prompted; after payment the platform retries automatically — you do nothing.
3. **Repeated calls for the same project within the same day incur no extra charge** — just keep asking for each stage: revise → format → shot breakdown → AI board → schedule → preview.
4. **Not sure where to start?** Just describe your current state, e.g. "I have director notes to land on the script" or "the script is locked, break it into shots." The AI enters at the right step.
5. Each step's how-to lives in the End-to-End Workflow below; the taste red lines before you start are in the judgment handbook (Step 0).

## When to Use

- External notes (AI feedback, actor voice messages) need to land as a real revised draft
- A new script needs an overall health diagnosis before any rewrite
- You have no script yet and want the AI to draft a rough first version to revise on
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
9. **Audience gender comes before content design.** Label the target audience (male-frequency / female-frequency) before writing — hook structures, taboos, and the romance-vs-intrigue ratio all shift with the label. Writing a female-frequency script with male-frequency instincts earns rewrites.
10. **Pure romance must carry background weight.** A love story never floats free: the lead's personal choices must be tied to background stakes (nation / class / survival), there must be a "damned either way" dilemma at the climax, and the romance needs real obstacles. Miss one and it reads as naive fluff.

## End-to-End Workflow

### Step 0: Read the judgment handbook

Before any output, read `references/taste-and-judgment.md`. The 10 red lines above are a summary; the handbook is the full record of user corrections and project-specific standards. For romance / emotion-driven scripts, also read `references/audience-gender-fit.md` (audience gender-fit handbook).

### Step 1: Script revision

**Diagnose first.** Run the script-doctor evaluation from `references/script-doctor.md` (label the audience gender first, then 6 categories, 27 items, 4-grade scale, 100-point total, 7-dimension revision notes). Confirm the issue list with the director before rewriting.

If character scores are low (motivation contradictions, tool-like roles, intelligence drops), rebuild the character using `references/character-sheet.md` (59 items across physical / psychological / social layers). The "decisive past moment" field is usually the source of the protagonist's single dominant motivation.

If gender-fit / dramatic-weight scores are low (naive fluff, no dilemma, romance too smooth), fix them with `references/audience-gender-fit.md` (male/female-frequency hook tables, the three-layer weight formula, and obstacle design).

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
- Body: bold Chinese sans-serif font; US Letter paper

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

## Capability Scope (read this so you don't mis-scope)

**In scope:** the full document chain for short-form / micro-drama **pre-production** — script draft assistance, diagnosis, revision, Hollywood-format screenplay, shot breakdown, AI storyboard, shooting schedule, location scouting, character bible, pre-shoot video preview.

- **Script draft assistance (supported):** based on your idea or logline, the AI can produce a rough first draft for you to revise directly; when that draft is weak, the script doctor pinpoints its problems before you rewrite. This skill owns "diagnosis + polish"; the zero-to-one first draft is carried by the AI's general writing ability in the conversation — the two connect seamlessly.
- **Length-agnostic parts (supported):** the Hollywood-format screenplay and the script-doctor evaluation diagnose by structure, not length — they work for short-form, long-form, and theatrical features alike. A feature-length project only means more volume and a schedule layout that needs to scale; this skill has not been specifically hardened for feature-length volume.

**Areas with a focus, calibrated on demand (not unsupported):**
- **Overseas projects:** the default values for scouting, transition time, and golden hour come from domestic (China) locations; for overseas scenes you calibrate those data sources yourself. The diagnosis / format / shot-breakdown methods are otherwise universal.
- **On-set execution during shooting:** this skill already covers pre-shoot on-set preparation (the 28-field location-scouting record + photo walk-line SOP is on-set in nature); execution tasks during the shoot itself (DIT data management, on-set coordination) have no ready-made tool yet and need to be supplemented separately.

## FAQ

**Q: A 402 payment prompt appeared; after paying nothing happened?**
After payment the platform retries the call automatically — wait a few seconds. If there's no response for a long time, just resend the same line; a paid project within the 24-hour window passes straight through, with no second charge.

**Q: Will I be charged twice?**
Two safeguards: the gateway is idempotent by order number (one order is never charged or delivered twice), and the local 24-hour session window for the same project prevents repeat charges.

**Q: If I use the same project again after 24 hours, do I pay again?**
After the window expires, a new call re-checks payment; when the prompt appears, pay as instructed.

**Q: Video preview is slow and burns credits?**
Video preview runs image-to-video on every board; dozens of shots add up to tens of minutes and significant credits. If the static AI storyboard PDF already conveys the intent, skip the video preview — Step 7 has a mandatory confirmation gate, so it never runs without your explicit go-ahead.

**Q: Does it work on Mac / Linux?**
The core flow (payment gate, diagnosis, revision, shot breakdown) is cross-platform. The default fonts for the AI board and schedule are Windows Chinese fonts; on macOS / Linux the script falls back to system Chinese fonts (PingFang / Noto / WenQuanYi). Set the dependency directory per the Environment section for your machine.

**Q: Does it work with a purely literary script (no shot hints)?**
Yes — use the "shot translation" path in Step 3: break scenes into beats, design framing and camera moves, show the board design to the director for approval, then freeze into shots.json. It never batch-generates images before you approve.

**Q: The format check returned FAIL — what now?**
The checker reports each failing line with its page and actual indent; fix the docx layout parameters line by line, then re-run. Note: even if you changed only a few lines, re-run the full check (format degrades — a hard-won lesson).

**Q: What data do I have to fill for a new project?**
Only two places: the CONFIG block of the AI board assembler (7 items: image dir / shots.json / output path / project name / total shots / start shot / post-shots notes), and the data blocks of the schedule builder (BLOCKS / CHECK / SCENE_MAP + the trailing assertion values). All other scripts are zero-config or CLI-parameterized. When you leave a placeholder unfilled or a file missing, the script reports it in Chinese with the exact fix.

## License

Tiered license — see [LICENSE.txt](./LICENSE.txt):

- Documentation (SKILL.md, references/*): CC BY-NC-ND 4.0
- Code: proprietary, not included in this showcase repository

© 2026 南京新菁年影视科技有限责任公司（Nanjing New-Youth Film & Technology Co., Ltd.）. All rights reserved.

## Changelog

- **v1.3.0** (2026-10-23): Added three chapters — Quick Start, Capability Scope, and FAQ. Unified the payment wording to "¥6.8 CNY per project; repeated calls for the same project within the 24-hour session window are never charged again," removing internal phrasing that contradicted the actual billing experience. Cross-platform font fallback in the AI board assembler, and Chinese error messages with fixes across the four scripts. Removed the obsolete legacy payment gate script to eliminate a double-charge risk.
- **v1.2.3**: Price 2.68 → 6.8 CNY per project (aligned across the SKILL.md price, the SkillHub form, and the Alipay bill amount).
- **v1.2.0**: Added the audience-gender-fit dimension (audience-gender-fit.md, script-doctor category 6, judgment-handbook 2.7, two new red lines).
- **v1.1.2**: Baseline (payment gate + 7-step SOP + 8 red lines).
