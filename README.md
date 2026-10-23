# Short-Drama Toolkit

A director's field toolkit for short-form drama / micro-drama projects, covering the full pipeline from script revision to shoot scheduling. Validated end-to-end on a real short-drama project and hardened through multiple rounds of director feedback.

> This repository is the **public showcase / documentation mirror** for the [WorkBuddy](https://www.workbuddy.cn) Pay Skill `short-drama-toolkit`.  
> The runnable skill package (with the real per-use payment gate) is published on **SkillHub**:  
> 👉 [https://skillhub.cn/skills/user_839f3063/short-drama-toolkit](https://skillhub.cn/skills/user_839f3063/short-drama-toolkit)

> The v1.3.0 documentation adds a **Quick Start**, a **Capability Scope**, and an **FAQ** to SKILL.md — start there if you're new.

## What It Does

| Module | Artifact | Highlights |
| ------ | -------- | ---------- |
| Script Doctor | Diagnostic report | Audience gender labeled first, then 6 categories / 27 items on a 4-grade scale + 100-point overall score + 7-dimension revision notes — diagnose before you rewrite |
| Audience Gender Fit | Fit handbook | Male/female-audience hook & taboo tables, the three-layer dramatic weight formula (stakes / self-knowledge / dilemma), and romance obstacle design — the cure for naive-fluff romance scripts |
| Character Sheet | 59-item questionnaire | 3-layer character bible (physical / psychological / social) — doubles as the visual-anchoring source for AI storyboard art |
| Hollywood Format | Screenplay docx | Industry-standard indent-column layout adapted for Chinese screenplays; auto-verified against a PASS/FAIL checker |
| Shot Breakdown | shots.json + xlsx | Structured intermediate data shared by 4 downstream consumers |
| AI Storyboard | Cadrage-style PDF | Hand-drawn comic look, per-shot AI generation, camera-move marks, auto-assembled |
| Location Scouting | 28-field checklist | Field SOP + 4-category decision framework; feeds real transition times into the schedule |
| Shooting Schedule | xlsx | Single-day schedule with makeup/wardrobe continuity verification |
| Video Preview | MP4 | Image-to-video motion preview assembled from static storyboards, default silent |

## Pricing

This is a **Pay Skill**: **¥6.8 CNY per project**, paid through the SkillHub platform. After payment, repeated calls for the same project within the 24-hour session window are never charged again; a new call after the window expires simply re-checks payment.

## Repository Layout

```
short-drama-toolkit/
├── SKILL.md                  # Showcase-friendly workflow SOP + director's taste guidelines
├── LICENSE.txt               # Tiered license notice
└── references/
    ├── taste-and-judgment.md # Judgment handbook: what gets rejected, and why
    ├── audience-gender-fit.md # Audience gender-fit handbook: hooks, taboos, dramatic weight, romance obstacles
    ├── script-doctor.md      # Evaluation framework (pre-rewrite diagnosis)
    ├── character-sheet.md    # 59-item character bible questionnaire
    ├── hollywood-format.md   # Format spec with measured parameters
    ├── shots-schema.md       # shots.json schema + image-gen prompt template
    ├── scouting.md           # Location scouting checklist + field SOP
    └── video-preview.md      # Image-to-video preview SOP (cost warning + silent default)
```

The `scripts/` folder (format checker, AI board assembler, schedule builder, video-preview builder, and the payment gate) is **not included here** — it ships only with the paid SkillHub package to prevent unpaid use.

## Workflow at a Glance

1. **Diagnose** — run the script doctor; confirm the issue list with the director before touching the script
2. **Rewrite** — check external feedback line by line; never move locked camera blocking
3. **Format** — Hollywood-standard docx; re-run the format checker until PASS on every revision
4. **Break down** — produce shots.json (the quality hub of the whole pipeline; image prompts come from here, never from raw script text)
5. **Generate** — 3 style samples first, batch only after approval; report the full budget upfront
6. **Assemble** — Cadrage-layout storyboard PDF with camera-move marks
7. **Schedule** — scouting data → single-day schedule with continuity checks
8. **Preview** *(optional)* — image-to-video motion preview from storyboards; silent by default

## License

Tiered license — see [LICENSE.txt](./LICENSE.txt) for full terms:

- **Documentation** (SKILL.md, references/*): [CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/en) — attribution required, non-commercial, no derivatives
- **Code**: Proprietary. Direct code-level reuse, modification, redistribution, or embedding in other projects is **not permitted** without prior written consent from the copyright holder.

© 2026 南京新菁年影视科技有限责任公司（Nanjing New-Youth Film & Technology Co., Ltd.）. All rights reserved.
