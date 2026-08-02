# Changelog

## 3.0.0 — Modular Architecture Refactor

### Structure

- Reorganized the repository into Core, UI, Brand, Mode, QA, and Prompt layers.
- Removed the legacy `core/` archive structure and the separate global `assets/ui-reference/` folder.
- Colocated Micas brand rules and visual references under `modules/brands/micas/`.
- Consolidated all UI-related rules into `modules/UI.md`.
- Consolidated all release checks into `modules/QA.md`.
- Consolidated v2.4.0 and v2.4.1 experience behavior into the authoritative default mode and UI modules.
- Removed the redundant corrective file pattern represented by `COURSE_EXPERIENCE_FIXES_v2.4.1.md`.

### Modular Brand Support

- Added `modules/brands/BRAND_TEMPLATE.md`.
- Kept Micas as the default brand pack.
- Defined brand packs as independent containers for logo, colors, tone, references, and brand-specific QA.
- Enabled future company changes without rewriting Core, UI, or Mode rules.

### Modular Experience Modes

- Preserved `interactive-training` as the default behavior.
- Added optional starter profiles for:
  - gamified learning;
  - executive reports;
  - marketing content.
- Added `modules/modes/MODE_TEMPLATE.md` for future modes.
- Only the selected mode is active.

### Prompts

- Added `prompts/MODULAR_PROMPT.md` as the recommended configurable project prompt.
- Added `prompts/QUICK_PROMPT.md` as the concise Chinese launcher.
- Added explicit brand and mode selection fields.

### Compatibility

The default selection:

```text
brand_profile: micas
experience_mode: interactive-training
```

preserves the established v2.4.1 behavior, including:

- Micas deep-navy visual system;
- one-screen/PPT-like scenes;
- large body text;
- complete technical images;
- global navigation;
- icon-only Search after Next;
- Google-default voices when available;
- narration-completion Auto Play;
- final-only graded assessment;
- manual assessment pages;
- four languages;
- offline HTML delivery;
- strict QA.

### Scope

Version 3.0.0 is primarily an information-architecture and maintainability release. It does not intentionally change the default Micas interactive-training logic.

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
