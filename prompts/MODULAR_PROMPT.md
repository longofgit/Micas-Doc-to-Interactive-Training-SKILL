# Modular Project Prompt

Use this prompt for formal projects. Replace the bracketed values.

---

Use the **Micas Doc-to-Interactive-Training Skill v3 modular framework**.

## Module Selection

```text
brand_profile: [micas | path to another brand pack]
experience_mode: [interactive-training | gamified-learning | executive-report | marketing-content | path to another mode]
ui_system: modules/UI.md
qa_system: modules/QA.md
```

Default selection when omitted:

```text
brand_profile: micas
experience_mode: interactive-training
```

Read the selected modules in this exact order:

1. `modules/CORE.md`
2. selected file under `modules/modes/`
3. selected file under `modules/brands/`
4. `modules/UI.md`
5. `modules/QA.md`

Do not mix multiple brands or modes unless I explicitly request a hybrid.

## Project Inputs

- Source files: `[UPLOADED FILES]`
- Project title: `[AUTO-GENERATE OR ENTER]`
- Audience: `[AUDIENCE]`
- Business or learning objective: `[OBJECTIVE]`
- Desired duration or length: `[VALUE]`
- Default language: `[English]`
- Required languages: `[English / 简体中文 / 繁體中文 / 日本語]`
- Primary output: `[MODE DEFAULT OR CUSTOM OUTPUT]`
- Additional constraints: `[CONSTRAINTS]`

## Required Execution

1. Read the complete relevant source material, including body text, tables, figures, warnings, procedures, appendices, and embedded images.
2. Build a source audit and traceability map before authoring.
3. Preserve exact technical facts, limits, commands, terminology, dependencies, and safety boundaries.
4. Do not invent unsupported technical, performance, compliance, warranty, customer, or market claims.
5. Apply the selected experience mode for structure, interaction, narration, assessment, and deliverables.
6. Apply the selected brand pack for logo, colors, tone, and visual references only.
7. Apply the shared UI system and selected mode's control behavior.
8. Use English as the visual master unless another master locale is explicitly specified.
9. Generate the complete deliverables, not only an outline, sample, or proposal.
10. Run every applicable QA check and correct all release-blocking defects before delivery.

## Default Micas Interactive-Training Requirements

When `brand_profile: micas` and `experience_mode: interactive-training` are selected, preserve the established behavior:

- unified deep-navy Micas stage with localized light cards or image frames only;
- Micas primary color `#00899F`;
- approved Micas header lockup and brand references;
- one-screen/PPT-like scenes with no normal-page scrolling;
- clear course → module → scene hierarchy;
- large learner-facing text and strong visual hierarchy;
- complete technical images using `object-fit: contain`;
- hidden bottom-left Course Menu;
- right-side footer order: Previous → Next → Search → narration → Audio settings;
- Search icon only, with no visible Search text;
- global Next availability across module boundaries and unanswered questions;
- Google voice selected by default for every locale whenever the runtime exposes one;
- Auto Play waits for complete narration before advancing;
- Auto Play pauses for the assessment introduction and never narrates or skips graded questions;
- all graded questions consolidated in the final Review & Assessment module;
- final assessment transition, results, and completion;
- English, Simplified Chinese, Traditional Chinese, and Japanese;
- desktop-first design with tablet and phone adaptation;
- self-contained offline HTML with embedded search index and assets.

## Delivery Package

Return the selected mode's required artifacts. For the default interactive-training mode, return:

1. `[PROJECT_NAME]_Interactive_Training.html`
2. `[PROJECT_NAME]_Course_Map.md`
3. `[PROJECT_NAME]_QA_Report.md`
4. `[PROJECT_NAME]_README.md`

In the QA Report, identify source issues, assumptions, viewport results, typography, image integrity, controls, voice fallback, Auto Play, assessment, search, responsive behavior, accessibility, and any limitation.

Do not deliver until all release-blocking defects have been corrected.

---

## Selection Examples

### Micas interactive training

```text
brand_profile: micas
experience_mode: interactive-training
```

### Another company's interactive training

```text
brand_profile: modules/brands/acme/BRAND.md
experience_mode: interactive-training
```

### Micas gamified learning

```text
brand_profile: micas
experience_mode: gamified-learning
```

### Executive company report

```text
brand_profile: modules/brands/acme/BRAND.md
experience_mode: executive-report
```

### Marketing experience

```text
brand_profile: modules/brands/acme/BRAND.md
experience_mode: marketing-content
```
