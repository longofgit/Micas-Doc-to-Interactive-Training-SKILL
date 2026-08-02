---
name: micas-doc-to-interactive-training
display_name: Micas Doc-to-Interactive-Training Skill
description: Convert technical documents into source-grounded, Micas-branded, self-contained interactive training courses with PPT-like scenes, strict production QA, multilingual narration, hierarchical modules, final assessment, responsive delivery, search, and approved Micas UI references.
version: 2.4.1
---

# Micas Doc-to-Interactive-Training Skill

## Mandatory Load Order

For every document-to-training task, read and apply these files in order:

1. `core/SKILL_v2.3.2.md` — the complete v2.3.2 production workflow and all existing content, navigation, image, language, voice, assessment, Auto Play, and QA rules.
2. `UI_DESIGN_SPEC.md` — the complete general Micas visual implementation contract.
3. `HEADER_UI_SPEC.md` — the mandatory v2.3.3 upper-left header override.
4. `COURSE_EXPERIENCE_SPEC.md` — the mandatory v2.4.0 targeted override for typography, content references, module hierarchy, responsive adaptation, header utility icons, final-only assessment, assessment behavior in Auto Play, and full-course Search.
5. `COURSE_EXPERIENCE_FIXES_v2.4.1.md` — the mandatory corrective override for dark-stage enforcement, Search placement, deterministic Google-default voices, icon centering, and larger body-text minimums.
6. `MASTER_PROMPT.md` or `QUICK_PROMPT.md` — the task launcher selected for the project.

Do not skip the referenced files. The preserved core rules remain fully active.

## Rule Precedence

- Source-grounding, technical accuracy, safety, global navigation, image integrity, language, narration, one-screen behavior, and existing production QA remain defined by `core/SKILL_v2.3.2.md` and `UI_DESIGN_SPEC.md`.
- `HEADER_UI_SPEC.md` overrides only the upper-left header/brand-lockup design where it is more specific.
- `COURSE_EXPERIENCE_SPEC.md` overrides only its eight explicitly named v2.4.0 areas.
- `COURSE_EXPERIENCE_FIXES_v2.4.1.md` overrides only its five explicitly named corrections and takes precedence where it is more specific than v2.4.0.
- No other established UI or functional behavior may be changed merely because v2.4.1 was added.

## Approved Visual References

Inspect the reference assets under `assets/ui-reference/` before implementation:

- `header-lockup-reference.svg`
- `content-hero-product-split-reference.svg`
- `content-checkpoint-positioning-reference.svg`
- `content-checkpoint-redundancy-airflow-reference.svg`
- `content-key-metrics-power-reference.svg`
- `header-action-icons-reference.svg`

The generated course must use live HTML/CSS, localizable text, the real transparent Micas logo, and authentic source-document visuals. Reference assets guide composition and hierarchy; do not insert them as flattened production pages.

## v2.4.0 Targeted Requirements

Apply only these refinements:

1. Increase learner-facing body-copy readability while preserving large-title hierarchy.
2. Use the bundled main-content references as design guidance.
3. Organize the course as a clear course → module → scene hierarchy.
4. Support tablet and phone with PC/desktop visual quality as the first priority.
5. Add appropriate icons to language, Auto Play/Video, and Fullscreen controls.
6. Place all graded questions in the final `Review & Assessment` module; do not add per-module graded exams.
7. Stop Auto Play on assessment questions; do not narrate or skip graded question pages.
8. Add full-course Search to the footer.

## v2.4.1 Corrective Requirements

Apply only these corrections:

1. Keep the entire learner stage deep navy; light backgrounds are allowed only inside bounded cards, metric tiles, or image frames.
2. Make Search icon-only and place it after Next, producing the order Previous → Next → Search → narration → Audio settings.
3. Select an available matching Google voice as the deterministic default for every locale; use fallback only when the runtime does not expose Google.
4. Center every header and footer icon precisely in both axes.
5. Enforce a `20px` desktop minimum for instructional body text, with important body copy normally `22px` or larger.

The exact implementation and QA requirements are defined in `COURSE_EXPERIENCE_FIXES_v2.4.1.md`.

## Completion Standard

Generate the complete deliverables, apply the mandatory load order, inspect all bundled references, run the preserved production QA plus the v2.3.3 header QA, v2.4.0 targeted QA, and v2.4.1 corrective QA, correct every release-blocking defect, and only then deliver.