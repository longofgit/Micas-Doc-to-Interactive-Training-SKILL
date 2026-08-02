# Micas Doc-to-Interactive-Training Skill

Version: **2.4.1**

This repository converts manuals, SOPs, product guides, policies, presentations, and technical documents into source-grounded, Micas-branded interactive training courses.

## Required Reading Order

For reliable execution, the AI must read:

1. `SKILL.md`
2. `core/SKILL_v2.3.2.md`
3. `UI_DESIGN_SPEC.md`
4. `HEADER_UI_SPEC.md`
5. `COURSE_EXPERIENCE_SPEC.md`
6. `COURSE_EXPERIENCE_FIXES_v2.4.1.md`
7. `MASTER_PROMPT.md` or `QUICK_PROMPT.md`

The preserved v2.3.2 core remains the complete production workflow. `HEADER_UI_SPEC.md` is the focused header override. `COURSE_EXPERIENCE_SPEC.md` defines the v2.4.0 refinements. `COURSE_EXPERIENCE_FIXES_v2.4.1.md` is a narrow corrective override and changes only five explicitly named items.

## Package Contents

- `SKILL.md` — current entry point, mandatory load order, precedence, and completion requirements.
- `core/SKILL_v2.3.2.md` — preserved complete production workflow and existing functional rules.
- `UI_DESIGN_SPEC.md` — general Micas visual implementation contract.
- `HEADER_UI_SPEC.md` — mandatory upper-left header/brand-lockup specification.
- `COURSE_EXPERIENCE_SPEC.md` — body typography, content references, module hierarchy, responsive adaptation, header utility icons, final-only assessment, assessment Auto Play behavior, and full-course Search.
- `COURSE_EXPERIENCE_FIXES_v2.4.1.md` — dark-stage enforcement, icon-only Search after Next, deterministic Google-default voices, icon centering, and larger body-text minimums.
- `MASTER_PROMPT.md` — full formal-project prompt.
- `QUICK_PROMPT.md` — concise Chinese project prompt.
- `assets/ui-reference/` — approved visual references and usage documentation.
- `CHANGELOG.md` — current release notes.
- `core/CHANGELOG_v2.3.2.md` and `core/README_v2.3.2.md` — preserved earlier history and documentation.

## Visual Reference Assets

Reference images can be included inside a Skill folder. This repository stores them under `assets/ui-reference/` and references them from mandatory specification files.

Current references:

- `header-lockup-reference.svg`
- `content-hero-product-split-reference.svg`
- `content-checkpoint-positioning-reference.svg`
- `content-checkpoint-redundancy-airflow-reference.svg`
- `content-key-metrics-power-reference.svg`
- `header-action-icons-reference.svg`

They are composition guidance. Generated courses must recreate the style with live HTML/CSS, localizable text, the actual transparent Micas logo, and authentic source-document images. Do not use a reference asset as a flattened production page.

## v2.4.0 Targeted Refinements

Version 2.4.0 introduced:

1. Larger learner-facing body-copy targets.
2. Approved main-content visual references.
3. A clear course → module → scene hierarchy.
4. Tablet and phone adaptation with PC/desktop as the visual-quality priority.
5. Icons on language, Auto Play/Video, and Fullscreen controls.
6. All graded questions consolidated into the final `Review & Assessment` module.
7. Manual learner control for graded questions under Auto Play.
8. Full-course offline Search.

## v2.4.1 Corrective Refinements

Version 2.4.1 changes only the following five items:

1. Restores and enforces the unified deep-navy learner-stage background. Light colors are limited to bounded cards, metric tiles, and image frames.
2. Makes Search icon-only and moves it after Next. The footer action order is now Previous → Next → Search → narration → Audio settings.
3. Makes Google the deterministic default voice provider for every locale whenever the current browser/OS exposes a matching Google voice.
4. Requires every header and footer icon to be precisely centered in both axes.
5. Raises the desktop instructional-body minimum to `20px`, with important body copy normally `22px` or larger.

Detailed implementation and QA rules are in `COURSE_EXPERIENCE_FIXES_v2.4.1.md`.

## Existing Behaviors Preserved

Unless an item is explicitly listed in the relevant focused override, v2.4.1 does not change:

- the approved upper-left header lockup;
- the Micas color token system;
- one-screen/PPT-like behavior;
- course → module → scene hierarchy;
- global Previous/Next availability;
- footer button dimensions and right alignment;
- narration-completion timing for normal instructional scenes;
- final-only graded assessment structure;
- assessment pause behavior under Auto Play;
- complete technical-image requirements;
- English-first multilingual design;
- source grounding and source mapping;
- offline single-file HTML delivery;
- existing production QA and release blockers.

## Standard Invocation

```text
Please use the Micas Doc-to-Interactive-Training Skill.
Read SKILL.md and every mandatory referenced file in its load order.
Convert the uploaded source document into the complete production-ready interactive course.
Do not stop at an outline or sample.
```

## Output Standard

The normal deliverables remain:

1. one self-contained offline interactive HTML course;
2. Course Map;
3. QA Report;
4. course README.

The course must pass the preserved production QA, the header QA, the v2.4.0 targeted QA, and the v2.4.1 corrective QA before delivery.