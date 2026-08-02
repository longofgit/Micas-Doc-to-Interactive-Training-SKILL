# Changelog

## 3.5.0 — Source-Grounded Homepage and Browser-Viewport Fit

### Scope Lock

- Preserved the approved Micas top and bottom fixed control rails without changing their dimensions, button order, icon sizes, typography, or spacing.
- Limited this release to learner-facing content relevance, opening-scene quality, normal browser-window fit, prompts, and QA.

### Source-Grounded Homepage

- Required the first learner-facing scene to introduce the actual product, system, process, service, workflow, safety objective, or job outcome supported by the source materials.
- Prohibited filling the homepage with project metadata such as duration, language count, difficulty, `Offline HTML`, file format, QA status, or delivery-package details unless explicitly required by the user or source.
- Required one to three concise, source-supported content anchors.
- Required the most relevant authentic source visual when available, such as the real product, architecture/topology, workflow/process, or supported work scenario.
- Prohibited generic acronym tiles, abstract placeholders, or decorative substitutes when a suitable real source image exists.

### Normal Browser Window Fit

- Required layout calculation from the actual `window.innerHeight` / `100dvh` available to the document.
- Added constrained browser-content viewport checks for `1920×930`, `1600×780`, and `1366×650` at 100% zoom.
- Prohibited relying on Fullscreen to reveal content hidden by browser chrome.
- Required fit issues to be solved by copy refinement, composition changes, reduced nonessential middle-stage padding, or scene splitting—not by modifying the locked control rails or shrinking instructional text below approved minimums.

### QA and Prompts

- Added release-blocking checks for irrelevant homepage metadata, generic opening visuals, and browser-chrome clipping.
- Updated `SKILL.md`, `README.md`, `QUICK_USER_GUIDE.md`, `MASTER_PROMPT.md`, and `QUICK_PROMPT.md` to version 3.5.0.

## 3.1.0 — Training-Only Simplification

### Scope

- Reconfirmed that this repository creates interactive training materials only.
- Removed executive-report, company-report, marketing-content, campaign, and other non-training modes from the active structure.
- Kept standard interactive training as the default.
- Kept gamified interactive learning as the only optional alternative.
- Explicitly prohibited adding game mechanics unless `training_mode: gamified-learning` is selected.

### Structure

- Reduced `modules/modes/` to:
  - `interactive-training.md`;
  - `gamified-learning.md`.
- Removed `executive-report.md`.
- Removed `marketing-content.md`.
- Removed `MODE_TEMPLATE.md` to prevent expansion into unrelated output types.
- Replaced `prompts/MODULAR_PROMPT.md` with the clearer `prompts/MASTER_PROMPT.md`.
- Updated `SKILL.md`, `README.md`, `QUICK_USER_GUIDE.md`, `modules/CORE.md`, and `prompts/QUICK_PROMPT.md` to use training-only terminology.

### Default Configuration

```text
brand_profile: micas
training_mode: interactive-training
```

The optional game-based mode is selected only when explicitly requested:

```text
training_mode: gamified-learning
```

### Compatibility

The standard interactive-training logic remains unchanged, including:

- Micas deep-navy visual system;
- one-screen/PPT-like scenes;
- large learner-facing text;
- complete technical images;
- global sequential navigation;
- icon-only Search after Next;
- Google-default voices when available;
- narration-completion Auto Play;
- final-only graded assessment;
- manual assessment pages;
- four-language delivery;
- offline HTML output;
- strict QA.

Brand packs remain modular so another company's logo, colors, and visual references can be used without changing the training engine.

## 3.0.0 — Modular Architecture Refactor

### Structure

- Reorganized the repository into Core, UI, Brand, Mode, QA, and Prompt layers.
- Removed the legacy `core/` archive structure and the separate global `assets/ui-reference/` folder.
- Colocated Micas brand rules and visual references under `modules/brands/micas/`.
- Consolidated all UI-related rules into `modules/UI.md`.
- Consolidated all release checks into `modules/QA.md`.
- Removed the redundant corrective-file pattern used by earlier versions.

### Compatibility

The default Micas interactive-training behavior was preserved.

## 2.4.1 — Corrective UI Release

- Restored deep-navy stage enforcement.
- Moved icon-only Search after Next.
- Required deterministic Google-default voices.
- Required precise icon centering.
- Raised instructional-body minimums.

## 2.4.0 — Course Experience Refinements

- Added main-content visual references.
- Added course/module/scene hierarchy.
- Added desktop-first responsive behavior.
- Added utility icons.
- Consolidated graded assessment at the end.
- Paused Auto Play for assessment pages.
- Added full-course Search.

## Earlier History

Earlier revisions remain available through the Git history.
