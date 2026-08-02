---
name: micas-doc-to-interactive-training
display_name: Micas Doc-to-Interactive-Training Skill
description: A source-grounded framework for converting documents into Micas-branded interactive training. Standard interactive training is the default; game-based interactive training is optional.
version: 3.5.0
---

# Micas Doc-to-Interactive-Training Skill

## Purpose

This repository creates **interactive training materials only**.

It is not a general document-to-experience framework and must not be used to generate:

- executive or management reports;
- company-review presentations;
- marketing campaigns or sales collateral;
- other non-training deliverables.

The supported training modes are:

1. `interactive-training` — the default standard interactive course;
2. `gamified-learning` — an optional game-based learning course used only when explicitly requested.

The default configuration remains:

```text
brand_profile: micas
training_mode: interactive-training
```

The default primary output is one self-contained offline interactive HTML course plus Course Map, QA Report, and README. English remains the default language and visual master, with Simplified Chinese, Traditional Chinese, and Japanese also supported.

## Mandatory Module Load Order

For every project, load exactly one training mode:

1. `modules/CORE.md`
2. selected training mode under `modules/modes/`
3. selected brand pack under `modules/brands/`
4. `modules/UI.md`
5. `modules/QA.md`
6. `prompts/MASTER_PROMPT.md` or `prompts/QUICK_PROMPT.md`

Default selection:

```text
core: modules/CORE.md
training_mode: modules/modes/interactive-training.md
brand: modules/brands/micas/BRAND.md
ui: modules/UI.md
qa: modules/QA.md
prompt: prompts/MASTER_PROMPT.md
```

Do not load `gamified-learning.md` unless the user explicitly asks for game-based learning, missions, levels, points, badges, branching challenges, or similar mechanics.

Do not load both training modes unless the user explicitly requests a reviewed hybrid.

When `brand_profile: micas` is selected, inspect the current files under `modules/brands/micas/example/` as concrete UI and interaction references after loading the required modules. Do not depend on a specific example filename or version because the directory contents may be replaced. Source facts, explicit user constraints, and the latest Core, mode, Brand, UI, and QA rules remain authoritative.

## Module Responsibilities

### Core

`modules/CORE.md` contains invariant rules for:

- source grounding and factual accuracy;
- source audit and traceability;
- content prioritization;
- multilingual equivalence;
- artifact integrity;
- safe assumptions and rule precedence.

### Training Mode

The selected file under `modules/modes/` defines:

- learning architecture;
- scene and interaction model;
- narration and playback behavior;
- assessment and completion model;
- training-specific deliverables.

The default is `interactive-training.md`.

### Brand

The selected brand pack defines:

- logo and brand identity;
- color tokens;
- typography and tone;
- visual references and brand assets;
- brand-specific UI constraints.

The default is `modules/brands/micas/BRAND.md`.

Brand packs remain modular so another company's logo, colors, and visual references can be used without changing training logic.

### UI

`modules/UI.md` defines the consolidated interface contract for:

- one-screen/PPT-like viewport behavior;
- layout, hierarchy, typography, imagery, controls, icons, and responsive behavior;
- header, stage, footer, search, narration, settings, accessibility, and learner-mode cleanliness.

### QA

`modules/QA.md` is the final release gate for source accuracy, functionality, rendering, multilingual behavior, accessibility, selected training mode, and selected brand requirements.

## Rule Precedence

Use this precedence order:

1. source facts, safety limits, and explicit user constraints;
2. `modules/CORE.md` accuracy and traceability rules;
3. selected training mode;
4. selected brand pack;
5. `modules/UI.md` implementation rules;
6. project variables in the selected prompt;
7. nontechnical stylistic inference.

A training mode or brand pack may change presentation and interaction, but it may not override source facts, safety requirements, or mandatory QA.

## Available Training Modes

### Standard interactive training — default

```text
training_mode: interactive-training
```

Use for normal technical, product, service, process, safety, operational, onboarding, and certification training.

### Gamified interactive learning — optional

```text
training_mode: gamified-learning
```

Use only when explicitly requested for missions, levels, points, badges, branching decisions, or challenge-based learning.

No executive-report, marketing-content, or other non-training modes are supported by this Skill.

## Available Brand Packs

- `modules/brands/micas/BRAND.md` — default Micas identity and visual references;
- `modules/brands/BRAND_TEMPLATE.md` — copy this to create another company's training brand pack.

Changing the company identity should normally require only a new brand pack. Do not rewrite Core, UI, QA, or training-mode logic merely to change the logo, colors, or brand tone.

## Completion Standard

1. Read the complete source materials.
2. Load the selected training mode and brand pack in the required order.
3. Generate the complete requested training artifacts, not only an outline or sample.
4. Run every applicable check in `modules/QA.md`.
5. Correct all release-blocking defects before delivery.
