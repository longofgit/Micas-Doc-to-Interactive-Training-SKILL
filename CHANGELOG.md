# Changelog

## 2.4.1

### Deep-Navy Stage Restoration

- Reaffirmed that the complete learner-facing shell, stage, and scene background remain deep navy.
- Clarified that light colors from reference screenshots are allowed only inside bounded cards, metric tiles, and technical-image frames.
- Added a release blocker for pale, white, light-gray, or light-grid full-page learner stages.

### Search Placement and Label

- Kept Search as an icon-only magnifying-glass control with no visible text.
- Moved Search after Next and before narration.
- Defined the footer action order as Previous → Next → Search → narration → Audio settings.

### Deterministic Google Default Voices

- Required every locale to target a matching Google voice as the generated default whenever the current runtime exposes one.
- Required voice selection to wait for `voiceschanged` before finalizing the default.
- Prevented arbitrary operating-system, alphabetical, cached, Microsoft, Apple, or Samantha defaults from winning over an available Google voice.
- Preserved quality-ranked fallback only when no matching Google voice is available.

### Icon Centering

- Required all header and footer buttons to center their icons in both axes.
- Added shared inline-flex/grid alignment guidance, tight SVG viewBox requirements, and icon-only zero-padding rules.
- Added a release blocker for visibly off-center control icons.

### Body-Text Minimum

- Raised the desktop instructional-body minimum to `20px` at 1366×768.
- Set important explanatory text, answers, steps, bullets, and card body copy to normally use `22px` or larger.
- Required scene redesign or splitting instead of shrinking instructional text to fit.

### Scope

- Added `COURSE_EXPERIENCE_FIXES_v2.4.1.md` as a narrow corrective override.
- Changed only background enforcement, Search placement/label, Google-default voice selection, icon centering, and body-text minimums.
- Did not change the header lockup, module architecture, responsive priority, final assessment structure, Auto Play assessment behavior, global Next logic, button dimensions, image integrity, source grounding, multilingual policy, or other established behavior.

## 2.4.0

### Learner Readability

- Increased normal learner-facing body-copy targets while preserving the existing large-title hierarchy.
- Prohibited shrinking body text merely to force crowded scenes to fit.

### Main-Content References

- Added `content-hero-product-split-reference.svg`.
- Added `content-checkpoint-positioning-reference.svg`.
- Added `content-checkpoint-redundancy-airflow-reference.svg`.
- Added `content-key-metrics-power-reference.svg`.
- Added `header-action-icons-reference.svg`.
- Expanded `assets/ui-reference/README.md` with intended usage for every reference.

### Course Architecture

- Required a clear course → module → scene hierarchy.
- Required multiple logically ordered learning modules based on competencies and work sequence rather than source page order.

### Responsive Priority

- Added tablet and phone adaptation requirements.
- Kept PC/desktop presentation quality as the first visual priority.
- Allowed responsive scene variants, stacked layouts, compact controls, and additional scene splitting without weakening the desktop design.

### Header Utility Icons

- Required a suitable language/globe/translation icon for the language selector.
- Required a video-camera or play icon for Auto Play/Video mode.
- Required a fullscreen-corners icon for Fullscreen.
- Preserved the existing header lockup and right-side control order.

### Assessment Consolidation

- Moved all graded questions into the final `Review & Assessment` module.
- Prohibited separate graded examinations at the end of each instructional module.
- Preserved optional ungraded learning interactions inside instructional modules.

### Auto Play and Assessment

- Required Auto Play to pause at the assessment introduction.
- Disabled narration, timers, auto-submit, and auto-advance on graded question pages.
- Required assessment questions to remain under manual learner control.

### Full-Course Search

- Added an icon-only Search control.
- Required offline search across active-language module titles, scene titles, body text, warnings, procedures, keywords, and assessment content.
- The final placement and footer order are superseded by v2.4.1.

### Scope

- Added `COURSE_EXPERIENCE_SPEC.md` as a focused override.
- Did not change the approved header lockup, Micas color system, global navigation availability, footer button sizing, Google-first voice priority, normal-scene narration-completion timing, technical-image integrity, source grounding, multilingual policy, or other existing behavior except where explicitly stated above.

## 2.3.3

### Header Brand Lockup

- Added `assets/ui-reference/header-lockup-reference.svg` as the approved upper-left header screenshot reference.
- Added `assets/ui-reference/README.md` explaining how the reference should be interpreted.
- Added `HEADER_UI_SPEC.md` as a mandatory focused header override.
- Required a large transparent Micas logo with a stacked bold course title and muted product/module subtitle.
- Added explicit desktop sizing, spacing, vertical alignment, deep-navy integration, cyan divider, responsive-priority, and utility-crowding rules.
- Added release blockers for tiny logos, weak title hierarchy, white logo boxes, misalignment, overlap, crowding, and flattened screenshot headers.
- Reorganized `SKILL.md` as a v2.3.3 entry point while preserving the complete v2.3.2 rules in `core/SKILL_v2.3.2.md`.

### Scope

- Changed only the upper-left header visual specification and bundled reference assets.
- Did not change navigation, footer alignment, Auto Play, narration, voice selection, assessment, image handling, language behavior, source grounding, or other course UI rules.

## Previous History

The complete v2.3.2 and earlier history is preserved in:

`core/CHANGELOG_v2.3.2.md`