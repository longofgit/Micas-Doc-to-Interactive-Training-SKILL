# Master Prompt — Interactive Training

Use this prompt for formal projects. Replace bracketed values only when needed.

---

Use the **Micas Doc-to-Interactive-Training Skill v3.5**.

This Skill is only for creating interactive training materials. Do not use it to create executive reports, company reports, marketing campaigns, or other non-training deliverables.

## Training Configuration

```text
brand_profile: [micas | path to another brand pack]
training_mode: [interactive-training | gamified-learning]
ui_system: modules/UI.md
qa_system: modules/QA.md
```

Default configuration:

```text
brand_profile: micas
training_mode: interactive-training
```

`interactive-training` is always the default. Use `gamified-learning` only when the user explicitly requests missions, levels, points, badges, branching challenges, or another game-based learning experience.

Read the selected modules in this exact order:

1. `modules/CORE.md`
2. selected training mode under `modules/modes/`
3. selected brand pack under `modules/brands/`
4. `modules/UI.md`
5. `modules/QA.md`

Load exactly one training mode. Do not combine standard and gamified modes unless the user explicitly requests a reviewed hybrid.

## Project Inputs

- Source files: `[UPLOADED FILES]`
- Project title: `[AUTO-GENERATE OR ENTER]`
- Audience: `[Technical Support Engineers]`
- Learning objective: `[Convert the source into complete job-ready interactive training]`
- Expected duration: `[30–45 minutes]`
- Default language: `[English]`
- Required languages: `[English / 简体中文 / 繁體中文 / 日本語]`
- Assessment difficulty: `[Intermediate]`
- Additional constraints: `[OPTIONAL]`

Project inputs configure authoring and delivery. Do not automatically expose duration, language count, difficulty, output format, or similar project metadata as learner-facing homepage content.

## Required Execution

1. Read the complete relevant source material, including body text, tables, figures, warnings, procedures, appendices, and embedded images.
2. Build a source audit and traceability map before authoring.
3. Preserve exact technical facts, limits, commands, terminology, dependencies, and safety boundaries.
4. Do not invent unsupported technical, performance, compliance, warranty, customer, or market claims.
5. Organize the learning journey as a clear Course → Module → Scene hierarchy rather than copying source pages mechanically.
6. Apply the selected training mode for learning structure, interactions, narration, assessment, and completion behavior.
7. Apply the selected brand pack only for logo, colors, visual tone, and brand references.
8. Apply `modules/UI.md` for the complete interface and responsive presentation contract.
9. Use English as the visual master unless another master language is explicitly requested.
10. Generate the complete deliverables, not only an outline, sample, or proposal.
11. Run all applicable checks in `modules/QA.md` and correct every release-blocking defect before delivery.

## Default Micas Interactive-Training Requirements

When the default configuration is used, preserve all established behavior:

- unified deep-navy Micas stage with localized light cards or technical-image frames only;
- Micas primary color `#00899F`;
- approved Micas header lockup and references;
- inspect and use the current implementation examples under `modules/brands/micas/example/` as concrete UI and interaction references; do not depend on a specific example filename or version because the directory contents may be replaced;
- keep the approved top and bottom fixed control rails unchanged;
- one-screen/PPT-like scenes with no normal-page scrolling;
- clear Course → Module → Scene hierarchy;
- large learner-facing text and strong visual hierarchy;
- complete technical images using `object-fit: contain`;
- hidden bottom-left Course Menu;
- right-side footer order: Previous → Next → Search → narration → Audio settings;
- Search icon only, with no visible Search text;
- global Next availability across module boundaries and unanswered questions;
- matching Google voice selected by default for every locale whenever the runtime exposes one;
- Auto Play waits for the complete scene narration before advancing;
- Auto Play pauses before assessment and never narrates or skips graded questions;
- all graded questions consolidated in the final Review & Assessment module;
- dedicated assessment introduction, results, and completion scenes;
- English, Simplified Chinese, Traditional Chinese, and Japanese;
- desktop-first design with tablet and phone adaptation;
- self-contained offline HTML with embedded assets and search index.

## Source-Grounded Homepage Requirements

The first learner-facing scene must introduce the actual training subject, not the course-generation configuration.

- Derive the headline, summary, and visible content anchors from the source materials.
- Show the product, system, process, service, safety objective, workflow, architecture, or job outcome that learners actually need to understand.
- Use one to three concise, source-supported content anchors.
- Do not use course duration, number of languages, difficulty, `Offline HTML`, file format, output package, QA status, or similar implementation metadata as homepage teaching cards unless the user explicitly requests them or the source itself teaches them.
- Use the most relevant authentic image from the source materials: actual product, architecture/topology, workflow/process, or real supported scenario.
- When a relevant source image exists, do not replace it with an acronym tile, abstract placeholder, generic illustration, or empty decorative frame.
- Crop irrelevant source-page margins and keep the meaningful visual complete and large.
- Do not invent technical or marketing claims to make the homepage look impressive.

## Normal Browser Window Fit

Every scene must fit the browser's actual document viewport after tabs, address bars, bookmarks, or operating-system chrome reduce the available height.

- Calculate layout from `window.innerHeight` / `100dvh` and the actual remaining scene row.
- Do not assume the physical monitor height equals the document viewport height.
- Test normal desktop sizes and constrained browser-content viewports including `1920×930`, `1600×780`, and `1366×650` at 100% zoom.
- Fullscreen may improve scale but must never be required to reveal hidden content.
- Keep the approved header and footer controls unchanged.
- Solve fit issues by shortening copy, rebalancing the composition, reducing nonessential middle-stage padding, or splitting content into additional scenes.
- Do not hide content, crop real images, or shrink instructional text below approved minimums.

## Delivery Package

For the default `interactive-training` mode, return:

1. `[PROJECT_NAME]_Interactive_Training.html`
2. `[PROJECT_NAME]_Course_Map.md`
3. `[PROJECT_NAME]_QA_Report.md`
4. `[PROJECT_NAME]_README.md`

For `gamified-learning`, follow the gamified mode's training deliverables while still providing a QA Report and README.

Do not deliver until all release-blocking defects have been corrected.

---

## Selection Examples

### Default Micas interactive training

```text
brand_profile: micas
training_mode: interactive-training
```

### Micas game-based interactive training

```text
brand_profile: micas
training_mode: gamified-learning
```

### Another company's standard interactive training

```text
brand_profile: modules/brands/acme/BRAND.md
training_mode: interactive-training
```
