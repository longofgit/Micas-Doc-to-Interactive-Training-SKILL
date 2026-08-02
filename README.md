# Micas Doc-to-Interactive-Training Skill

Version: **3.0.0**

This repository is now organized as a modular document-to-experience framework.

The default configuration still generates the established Micas interactive training course. The structural refactor separates reusable logic from company identity and output purpose, making it easier to switch brands or experience types without rewriting the whole Skill.

# Recommended Structure

```text
Micas-Doc-to-Interactive-Training-SKILL/
├── SKILL.md
├── README.md
├── CHANGELOG.md
├── prompts/
│   ├── MODULAR_PROMPT.md
│   └── QUICK_PROMPT.md
└── modules/
    ├── CORE.md
    ├── UI.md
    ├── QA.md
    ├── brands/
    │   ├── BRAND_TEMPLATE.md
    │   └── micas/
    │       ├── BRAND.md
    │       └── references/
    │           ├── header-lockup-reference.svg
    │           ├── content-hero-product-split-reference.svg
    │           ├── content-checkpoint-positioning-reference.svg
    │           ├── content-checkpoint-redundancy-airflow-reference.svg
    │           ├── content-key-metrics-power-reference.svg
    │           └── header-action-icons-reference.svg
    └── modes/
        ├── MODE_TEMPLATE.md
        ├── interactive-training.md
        ├── gamified-learning.md
        ├── executive-report.md
        └── marketing-content.md
```

# Why This Structure Is Better

## One responsibility per module

- `CORE.md` contains facts, source handling, traceability, language equivalence, and safe inference.
- `UI.md` contains all visual and interface rules in one place.
- `QA.md` contains all release checks in one place.
- each brand pack contains its own logo, colors, tone, and visual references together;
- each mode contains its own purpose, information architecture, interaction, narration, assessment, and deliverables.

## No patch-file accumulation

Files such as `COURSE_EXPERIENCE_FIXES_v2.4.1.md` are no longer needed. Corrective rules are consolidated into the authoritative module instead of being loaded as a growing sequence of overrides.

## Brand assets are colocated

Micas visual references now live with the Micas brand definition under:

`modules/brands/micas/`

A different company can be added by copying `BRAND_TEMPLATE.md` and placing that company's logo and visual references in its own brand folder.

## Modes are independently switchable

The default mode is `interactive-training`, but the framework also includes optional starter profiles for:

- gamified learning;
- executive reporting;
- marketing content.

Only the selected mode is loaded.

# Default Invocation

```text
Please use the Micas Doc-to-Interactive-Training Skill v3.

brand_profile: micas
experience_mode: interactive-training

Read SKILL.md and the selected modules in the mandatory order.
Convert the uploaded source files into the complete production-ready deliverables.
Do not stop at an outline or sample.
```

For the full configurable prompt, use:

`prompts/MODULAR_PROMPT.md`

For a concise Chinese prompt, use:

`prompts/QUICK_PROMPT.md`

# Switching the Brand

1. Copy `modules/brands/BRAND_TEMPLATE.md` to `modules/brands/<brand-id>/BRAND.md`.
2. Add the logo and reference images under `modules/brands/<brand-id>/references/`.
3. Define semantic color tokens, logo rules, tone, and brand QA.
4. Select the new brand in the prompt.

Do not modify Core, UI, or Mode merely to change the company identity.

# Switching the Experience Mode

Select one mode:

```text
experience_mode: interactive-training
experience_mode: gamified-learning
experience_mode: executive-report
experience_mode: marketing-content
```

Create another mode by copying `modules/modes/MODE_TEMPLATE.md`.

Do not combine modes unless the project explicitly needs a reviewed hybrid.

# Current Default Behavior Preserved

With `brand_profile: micas` and `experience_mode: interactive-training`, version 3.0.0 preserves the established behavior:

- Micas deep-navy stage and `#00899F` primary color;
- approved Micas header lockup and references;
- one-screen/PPT-like scenes;
- large body text and strong hierarchy;
- complete technical images;
- course → module → scene hierarchy;
- hidden bottom-left Course Menu;
- footer order Previous → Next → Search → narration → Audio settings;
- icon-only Search;
- global Next availability;
- Google-default voices when exposed by the runtime;
- Auto Play waits for complete narration;
- all graded questions in the final module;
- no narration or auto-skip on graded questions;
- English-first four-language delivery;
- desktop-first responsive behavior;
- self-contained offline HTML and mandatory QA.

# Architectural Recommendation

For long-term reuse across many companies, consider eventually separating the generic framework and company packs into two repositories:

1. a generic `Document-to-Experience-SKILL` engine;
2. a `Micas-Experience-Pack` containing the Micas brand and default mode choices.

The current v3 structure is compatible with that future separation, but keeps everything in one repository for simpler daily use today.
