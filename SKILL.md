---
name: micas-doc-to-interactive-training
display_name: Micas Doc-to-Interactive-Training Skill
description: A modular, source-grounded document-to-experience framework. The default configuration generates Micas-branded interactive training, while brand and experience-mode packs can be switched independently.
version: 3.0.0
---

# Micas Doc-to-Interactive-Training Skill

## Purpose

This repository is a modular document-to-experience framework.

The default configuration remains:

- **Brand pack:** `micas`
- **Experience mode:** `interactive-training`
- **Primary output:** one self-contained offline interactive HTML course plus Course Map, QA Report, and README
- **Default language and visual master:** English
- **Supported languages:** English, Simplified Chinese, Traditional Chinese, and Japanese

Version 3.0.0 is a structural refactor. It does not weaken or remove the established Micas interactive-training behavior.

## Mandatory Module Load Order

For every project, load exactly one module from each required layer:

1. `modules/CORE.md`
2. selected experience mode under `modules/modes/`
3. selected brand pack under `modules/brands/`
4. `modules/UI.md`
5. `modules/QA.md`
6. `prompts/MODULAR_PROMPT.md` or `prompts/QUICK_PROMPT.md`

Default selection:

```text
core: modules/CORE.md
mode: modules/modes/interactive-training.md
brand: modules/brands/micas/BRAND.md
ui: modules/UI.md
qa: modules/QA.md
prompt: prompts/MODULAR_PROMPT.md
```

Do not load multiple brand packs or multiple experience modes unless the user explicitly requests a hybrid and the combination is reviewed for conflicts.

## Module Responsibilities

### Core

`modules/CORE.md` contains invariant rules:

- source grounding and factual accuracy;
- source audit and traceability;
- content prioritization;
- multilingual equivalence;
- artifact integrity;
- module precedence and safe assumptions.

### Experience Mode

The selected file under `modules/modes/` defines:

- purpose and audience;
- information architecture;
- interaction model;
- narration and playback behavior;
- assessment or decision model;
- output form and mode-specific deliverables.

The default mode is `interactive-training.md`.

### Brand

The selected brand pack defines:

- logo and brand identity;
- color tokens;
- typography and tone;
- visual references and brand assets;
- brand-specific UI constraints.

The default brand is `modules/brands/micas/BRAND.md`.

### UI

`modules/UI.md` defines one consolidated interface and visual implementation contract:

- viewport and no-scroll behavior;
- layout, hierarchy, typography, imagery, controls, icons, responsive behavior, and accessibility;
- header, stage, footer, search, and settings presentation;
- learner-mode cleanliness and visual QA rules.

### QA

`modules/QA.md` is the final release gate for source accuracy, functionality, rendering, multilingual behavior, accessibility, and selected mode/brand requirements.

## Rule Precedence

Use this precedence order:

1. source facts, safety limits, and explicit user constraints;
2. `modules/CORE.md` accuracy and traceability rules;
3. selected experience mode;
4. selected brand pack;
5. `modules/UI.md` implementation rules;
6. project variables in the selected prompt;
7. stylistic inference that is not technically consequential.

A brand or mode may change presentation and interaction, but it may not override source facts, safety requirements, or mandatory QA.

## Available Experience Modes

- `interactive-training.md` — default Micas interactive course behavior
- `gamified-learning.md` — optional mission, level, points, and challenge experience
- `executive-report.md` — optional management-report and decision-support experience
- `marketing-content.md` — optional evidence-grounded marketing and campaign experience

Only the selected mode is active.

## Available Brand Packs

- `modules/brands/micas/BRAND.md` — default Micas identity and references
- `modules/brands/BRAND_TEMPLATE.md` — copy this to create another company or product brand

Brand replacement should normally require only a new brand pack and its colocated reference assets. Do not rewrite core, UI, or mode logic merely to change the company identity.

## Completion Standard

1. Read the complete source materials.
2. Load the selected modules in the required order.
3. Generate the complete requested artifacts, not only an outline or sample.
4. Run every applicable check in `modules/QA.md`.
5. Correct all release-blocking defects before delivery.
