# Changelog

## 2.3.2

### Auto Play Narration Completion

- Required Auto Play and Video mode to remain on the current scene until its complete narration finishes.
- Made the final narration utterance `onend` the only normal narrated-scene advance trigger.
- Prohibited fixed timers, estimated reading durations, character-count timing, and animation timing from advancing while speech is active.
- Required multi-chunk narration to finish every chunk before navigation.
- Required narration pause to pause page advancement.
- Required narration errors to stop Auto Play on the current scene instead of skipping it.
- Required manual navigation to invalidate stale narration callbacks and prevent duplicate page advances.

### Scope

- Made no other UI, navigation availability, footer alignment, image, language, voice-selection, assessment, or visual-design changes.

## 2.3.1

### Sequential Navigation

- Required Next to remain enabled on every scene with a following global scene.
- Fixed module-ending scenes so they advance directly to the next module.
- Removed answer, submission, feedback, score, pass/fail, and module-completion gates from Next.
- Required every module-check and final-assessment question to allow Next even when unanswered.
- Kept unanswered questions revisit-able without blocking navigation.
- Limited Next disabling/replacement to the absolute terminal completion scene.

### Footer Alignment

- Moved Previous and Next into the right-side action cluster.
- Kept narration and Audio settings at the far right.
- Fixed the action order as Previous → Next → narration → Audio settings.
- Left Course Menu, scene count, and progress on the left.

### Scope

- Made no other UI, image, language, voice, visual hierarchy, or course-structure changes.

## 2.3.0

### Package Naming

- Corrected the display name to **Micas Doc-to-Interactive-Training Skill**.
- Deprecated the mistaken form `Micas Doc-to- Interactive-Training Skill`.
- Updated the name consistently in `SKILL.md`, `UI_DESIGN_SPEC.md`, `MASTER_PROMPT.md`, `QUICK_PROMPT.md`, and `README.md`.

### Strict Overflow and Production QA

- Made scene or page overflow a release-blocking defect.
- Prohibited learner-visible `Layout overflow detected`, fit warnings, debug badges, QA messages, and authoring diagnostics.
- Required overflow checks to run silently after fonts and images load.
- Added reviewer-mode separation so diagnostics remain off in production.
- Required correction, redesign, or scene splitting before delivery.

### Stage Utilization

- Prohibited empty image frames, blank columns, placeholder panels, and accidental half-empty pages.
- Required two-column layouts to contain meaningful content on both sides.
- Added a normal target of approximately 65–90% meaningful stage utilization.
- Added visual QA for avoidable empty regions occupying roughly one-third or more of a scene.
- Required purposeful single-column alternatives when a planned visual is unavailable.

### Control Sizing

- Restored substantial presentation controls.
- Required labeled Previous and Next buttons on desktop.
- Set recommended desktop control height to 58–64 px.
- Set icon controls to at least 58×58 px.
- Prevented footer controls from shrinking with `flex-shrink: 0`.
- Enlarged the recommended progress bar to 340–520 px on wide screens and 240–320 px around 1366 px.

### Google-First Voice Policy

- Added exact-locale Google voices as the preferred default for English, Simplified Chinese, Traditional Chinese, and Japanese.
- Required an available Google voice to appear first in the curated list.
- Added fallback order: Google → Microsoft Natural/Neural → Apple → exact-locale fallback.
- Kept the visible list limited to three high-quality voices.
- Clarified that unavailable voices must not be fabricated and fallback behavior must be documented.

### Technical Image Integrity

- Strengthened the complete-image contract.
- Required technical visuals to use `object-fit: contain`.
- Prohibited half-visible, unintentionally cropped, or missing technical images.
- Required image checks after loading and decoding.
- Added checks for natural dimensions, ancestor clipping, viewport intersection, label readability, and excessive source whitespace.
- Required full-view plus explicit detail scenes when one page cannot keep a visual both complete and legible.

### Assessment Transition

- Added a mandatory assessment-introduction scene before the first final-exam question.
- Required question count, expected duration, scoring/pass information, instructions, readiness message, and a `Start Assessment` button.
- Required Video/Auto mode to pause on the transition scene.

### English-First Visual Master

- Established English as the primary visual-reference locale.
- Required English to be designed first for the strongest spacing, typography, image scale, and hierarchy.
- Allowed other locales to use authored wording, line breaks, column ratios, layout variants, or additional semantic sub-scenes.
- Prohibited weakening the English design merely to force identical multilingual density.

### Documentation Updated

- Replaced `SKILL.md` with the v2.3.0 production workflow and release criteria.
- Replaced `UI_DESIGN_SPEC.md` with stricter visual, control, image, voice, and QA rules.
- Updated `MASTER_PROMPT.md` to enforce complete production validation.
- Updated `QUICK_PROMPT.md` with concise Chinese execution requirements.
- Updated `README.md` with corrected naming, defaults, browser voice limitations, and release-blocking defects.

## 2.2.0

### Visual Hierarchy

- Added a mandatory one-dominant-element rule for every scene.
- Added `primaryMessage`, `supportingPoints`, `referenceDetails`, and `focalVisual` planning before layout.
- Increased recommended hero, scene-title, and key-metric typography scales.
- Required clear contrast between primary and supporting content.
- Preferred asymmetric 55/45, 58/42, and 60/40 compositions.
- Added a rule to use one primary card larger than secondary cards.
- Prohibited repetitive flat equal-size 2×2 card grids as the default scene pattern.

### Language Control

- Removed the visible `Language` prefix from the language selector.
- The selector displays only `English`, `简体中文`, `繁體中文`, or `日本語`.
- Retained `aria-label="Language"` for accessibility.

### Progress and Images

- Increased recommended progress-bar width and thickness.
- Added a complete-display contract for product images, diagrams, screenshots, and installation figures.
- Required `object-fit: contain` for technical visuals.
- Required larger stage allocation and source-margin cropping.

## 2.1.0

### PPT-Like Viewport Experience

- Added a mandatory one-scene-per-viewport presentation contract.
- Prohibited vertical browser/page scrolling in normal learner scenes.
- Required a `100dvh` shell with fixed header, stage, and footer regions.
- Added viewport QA at 1920×1080, 1600×900, and 1366×768.
- Added per-locale overflow validation.

### Navigation and Narration

- Moved Course Menu to the bottom-left footer.
- Replaced the permanent voice selector with a compact narration control.
- Moved detailed audio settings into a popover.
- Limited visible voices to curated high-quality options.

### Presentation Hygiene

- Removed learner-visible source mapping and narration transcript sections.
- Kept traceability in data, Course Map, and QA Report.

## 2.0.0

### UI and Branding

- Fixed the Micas primary color at `#00899F`.
- Added a coherent dark navy visual system based on the Preview design.
- Prevented accidental white logo rectangles and dominant white content panels.
- Added `UI_DESIGN_SPEC.md`.

### Navigation and Languages

- Changed the course directory from a docked sidebar to a hidden overlay drawer.
- Expanded support to English, Simplified Chinese, Traditional Chinese, and Japanese.
- Set English as the first-load default.