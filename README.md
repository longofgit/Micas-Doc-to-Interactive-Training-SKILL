# Micas Doc-to-Interactive-Training Skill

Version: **2.4.0**

This repository converts manuals, SOPs, product guides, policies, presentations, and technical documents into source-grounded, Micas-branded interactive training courses.

## Required Reading Order

For reliable execution, the AI must read:

1. `SKILL.md`
2. `core/SKILL_v2.3.2.md`
3. `UI_DESIGN_SPEC.md`
4. `HEADER_UI_SPEC.md`
5. `COURSE_EXPERIENCE_SPEC.md`
6. `MASTER_PROMPT.md` or `QUICK_PROMPT.md`

The preserved v2.3.2 core remains the complete production workflow. `HEADER_UI_SPEC.md` is the focused header override. `COURSE_EXPERIENCE_SPEC.md` is the focused v2.4.0 override and may change only the eight areas named in that file.

## Package Contents

- `SKILL.md` — current entry point, mandatory load order, precedence, and completion requirements.
- `core/SKILL_v2.3.2.md` — preserved complete production workflow and existing functional rules.
- `UI_DESIGN_SPEC.md` — general Micas visual implementation contract.
- `HEADER_UI_SPEC.md` — mandatory upper-left header/brand-lockup specification.
- `COURSE_EXPERIENCE_SPEC.md` — body typography, content references, module hierarchy, responsive adaptation, header utility icons, final-only assessment, assessment Auto Play behavior, and Search.
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

This release makes only the following changes:

1. Raises normal learner-facing body-copy sizes while retaining the established large-title hierarchy.
2. Adds approved main-content references for hero, checkpoint, hardware-memory, and key-metric scenes.
3. Requires a clear course → module → scene hierarchy and multiple logically ordered learning modules.
4. Adds tablet and phone adaptation while preserving PC/desktop as the visual-quality priority.
5. Requires suitable icons on language, Auto Play/Video, and Fullscreen controls.
6. Consolidates all graded questions into the final `Review & Assessment` module; instructional modules do not end with separate graded exams.
7. Suspends Auto Play on graded question pages so questions are not narrated, skipped, auto-submitted, or auto-advanced.
8. Adds an icon-only full-course Search immediately before Previous in the footer action order.

Detailed implementation and QA rules are in `COURSE_EXPERIENCE_SPEC.md`.

## Existing Behaviors Preserved

Unless an item is explicitly listed above, v2.4.0 does not change:

- the approved upper-left header lockup;
- Micas colors and overall visual direction;
- one-screen/PPT-like behavior;
- global Previous/Next availability;
- footer control sizing and right alignment;
- narration-completion timing for normal instructional scenes;
- Google-first voice selection;
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

The course must pass the preserved production QA, the header QA, and the targeted v2.4.0 QA before delivery.