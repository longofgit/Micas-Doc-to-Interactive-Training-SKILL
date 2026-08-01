# Changelog

## 2.2.0

### Visual Hierarchy

- Added a mandatory one-dominant-element rule for every scene.
- Added explicit `primaryMessage`, `supportingPoints`, `referenceDetails`, and `focalVisual` planning before layout.
- Increased recommended hero, scene-title, and key-metric typography scales.
- Required clear contrast between primary and supporting content.
- Preferred asymmetric 55/45, 58/42, and 60/40 compositions.
- Added a rule to use one primary card larger than secondary cards.
- Prohibited repetitive flat equal-size 2×2 card grids as the default scene pattern.
- Required hero and key scenes to retain the impact of the successful Preview version.

### Language Control

- Removed the visible `Language` prefix from the language selector.
- The selector now displays only `English`, `简体中文`, `繁體中文`, or `日本語`.
- Retained an English `aria-label="Language"` for accessibility.

### Progress Control

- Increased recommended progress-bar width and thickness.
- Added target widths of roughly 300–480 px at 1600–1920 px viewports and 220–300 px at 1366 px.
- Added a recommended 8–12 px progress-track height.

### Technical Images

- Added a mandatory complete-display contract for product images, diagrams, screenshots, and installation figures.
- Required `object-fit: contain` for technical visuals.
- Prohibited `object-fit: cover` except for nontechnical decorative backgrounds.
- Required larger stage allocation for teaching visuals.
- Added rules to crop source-page margins and unrelated whitespace before embedding.
- Required full-view plus annotated-detail scenes when one image cannot remain legible.
- Added image QA for clipping, scale, aspect ratio, labels, and viewport fit.

### QA and Documentation

- Added per-scene visual-hierarchy acceptance checks.
- Added image-fit checks at all required viewports and locales.
- Updated `SKILL.md`, `UI_DESIGN_SPEC.md`, `MASTER_PROMPT.md`, `QUICK_PROMPT.md`, and `README.md`.

## 2.1.0

### PPT-Like Viewport Experience

- Added a mandatory one-scene-per-viewport presentation contract.
- Prohibited vertical browser/page scrolling in normal learner scenes.
- Required a `100dvh` shell with fixed header, stage, and footer regions.
- Added viewport QA at 1920×1080, 1600×900, and 1366×768.
- Added per-locale overflow validation for English, Simplified Chinese, Traditional Chinese, and Japanese.
- Required long content, tables, procedures, and quizzes to be divided into more scenes.
- Added programmatic `scrollHeight <= clientHeight` and page-fit checks.

### Navigation and Narration

- Moved Course Menu from the top-left header to the bottom-left footer.
- Replaced the permanent voice selector with a compact icon-only narration control.
- Moved detailed audio settings into a popover.
- Limited visible voices to three curated high-quality options per locale.
- Added filtering for low-quality and legacy voices.

### Presentation Hygiene

- Removed learner-visible Source mapping / 源内容映射.
- Removed learner-visible Narration transcript / 旁白文本.
- Kept traceability in data, Course Map, and QA Report.

## 2.0.0

### UI and Branding

- Fixed the Micas primary color at `#00899F`.
- Added a coherent dark navy visual system based on the Preview design.
- Prevented accidental white logo rectangles and dominant white content panels.
- Added hero layout, card, typography, motion, and responsive specifications.
- Added `UI_DESIGN_SPEC.md`.

### Navigation

- Changed the course directory from a docked sidebar to a hidden overlay drawer.

### Languages

- Expanded support to English, Simplified Chinese, Traditional Chinese, and Japanese.
- Set English as the first-load default.
- Added locale-specific TTS preferences and completeness checks.