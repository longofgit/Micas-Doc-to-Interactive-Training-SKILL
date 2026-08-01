# Micas Doc-to-Interactive-Training Skill

Version: **2.3.1**

This package converts manuals, SOPs, product guides, policies, and technical documents into polished, source-grounded Micas interactive training courses.

## Package Contents

- `SKILL.md` — complete workflow, source-grounding rules, English-first visual master, one-screen behavior, image integrity, controls, narration, assessment, and strict QA.
- `UI_DESIGN_SPEC.md` — mandatory visual contract covering Micas colors, page utilization, image fit, control sizing, multilingual layouts, Google-first voices, and release-blocking defects.
- `MASTER_PROMPT.md` — detailed prompt for full, formal, or safety-critical projects.
- `QUICK_PROMPT.md` — concise Chinese prompt for routine document conversion.
- `CHANGELOG.md` — release history.

## Correct Package Name

Use this exact name:

> **Micas Doc-to-Interactive-Training Skill**

The earlier form `Micas Doc-to- Interactive-Training Skill` contained an unintended space and is deprecated.

## Recommended Use

1. Attach the source manual, SOP, policy, presentation, or product guide.
2. Tell the AI to read and follow `SKILL.md` first.
3. Treat `UI_DESIGN_SPEC.md` as a mandatory implementation and acceptance contract.
4. Use `MASTER_PROMPT.md` for a full production project or `QUICK_PROMPT.md` for routine work.
5. Provide audience, learning goal, duration, and assessment level.
6. Require the AI to generate the complete artifacts, render/test them, fix defects, and only then deliver.

## Fixed Defaults

- Brand: Micas Networks
- Primary color: `#00899F`
- Visual style: dark premium technical presentation based on the successful preview design
- Visual master locale: English
- Default language: English
- Required languages: English, 简体中文, 繁體中文, 日本語
- Scene behavior: one viewport per scene, PPT-like Previous/Next navigation
- Normal-page scrolling: disabled
- Course directory: hidden drawer, triggered from the bottom-left footer
- Language selector: current language only; no visible `Language` prefix
- Previous/Next: substantial labeled desktop buttons with uninterrupted global sequential navigation
- Footer actions: right-aligned in the order Previous, Next, narration, Audio settings
- Narration: compact icon controls with a curated popover
- Voice default: matching Google voice when available
- Final assessment: preceded by a dedicated assessment-introduction scene
- Output: one self-contained offline HTML plus Course Map, QA Report, and README

## v2.3.1 Navigation and Footer Fix

- Next remains enabled on every scene that has a following global scene.
- Module-ending scenes advance directly into the next module.
- Module checks and final-assessment questions do not gate Next on answer state.
- Unanswered questions remain revisit-able without blocking navigation.
- Only the absolute terminal completion scene may disable or replace Next.
- Footer actions are grouped at the far right in the fixed order: Previous, Next, narration, Audio settings.
- No other UI, image, language, voice, or visual-design rules were changed in this release.

## v2.3.0 Production Rules

### No visible debug or overflow UI

The final learner course must never show `Layout overflow detected`, fit warnings, QA badges, source-review notices, or authoring diagnostics. Overflow is a build/QA defect that must be corrected before delivery.

### No accidental half-empty scenes

Two-column layouts are allowed only when both columns have meaningful content. Empty image frames, blank columns, and large accidental unused regions fail visual QA.

### Complete technical images

Product images, diagrams, screenshots, and installation figures must use `object-fit: contain`, preserve aspect ratio, remain fully visible, and be large enough to teach from. Missing, half-visible, or unintentionally cropped images block release.

### Substantial controls

Desktop Previous/Next buttons use labels and arrows. Main controls should normally be 58–64 px tall, icon controls at least 58×58 px, and the progress bar should remain prominent.

### Google-first voices

When the browser exposes a matching Google voice, it is placed first and selected by default for English, Simplified Chinese, Traditional Chinese, and Japanese. Because offline HTML cannot install browser voices, unavailable Google voices must use the best fallback and be documented in the QA Report.

### Assessment transition

The course must insert a separate assessment-introduction scene before the first final-exam question. Auto/Video mode pauses there until the learner starts.

### English-first design

English is designed first as the strongest visual version. Other languages may use layout variants or additional scene splitting without weakening the English composition.

## Mandatory Viewport QA

At 100% browser zoom, render and inspect all scenes at:

- 1920×1080
- 1600×900
- 1366×768

Run English first, then all other locales.

Check:

- no page or scene overflow;
- no visible diagnostic messages;
- no accidental blank half-page;
- no empty visual placeholders;
- no clipped header/footer;
- complete, readable technical images;
- substantial controls;
- Next enabled on every nonterminal scene, including module endings and unanswered assessment questions;
- right-aligned footer actions in the required order;
- correct language behavior;
- Google-first selection when available;
- assessment transition;
- navigation, audio, quizzes, scoring, persistence, fullscreen, and offline assets.

## Release-Blocking Defects

Do not publish when any of the following exists:

- visible `Layout overflow detected` or similar warning;
- page or scene overflow;
- missing or half-visible technical image;
- large accidental empty region;
- tiny/shrunken desktop controls;
- Next disabled while a following scene exists;
- module or assessment state blocks navigation;
- footer actions are not right-aligned or are reordered;
- final exam begins without an introduction scene;
- English visual quality was weakened for multilingual uniformity;
- source mapping, transcript, QA, or debug data appears in learner mode;
- an offline asset is missing.

## Browser Voice Note

Web Speech API voices vary by operating system and browser. Google voices are common in Chrome environments but are not guaranteed by the HTML standard. The generated course must prefer Google when available, never fabricate missing voices, and report fallback behavior.

## Publishing Note

The generated HTML is intended for Chrome or Edge. Production deployments may replace browser TTS with prerecorded audio while retaining the same course data model and compact narration UI.