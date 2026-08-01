# Changelog

## 2.1.0

### PPT-Like Viewport Experience

- Added a mandatory one-scene-per-viewport presentation contract.
- Prohibited vertical browser/page scrolling in normal learner scenes.
- Required a `100dvh` shell with fixed header, stage, and footer regions.
- Added required viewport QA at 1920×1080, 1600×900, and 1366×768.
- Added per-locale overflow validation for English, Simplified Chinese, Traditional Chinese, and Japanese.
- Required long content, tables, procedures, and quizzes to be divided into more scenes instead of extending downward.
- Added programmatic `scrollHeight <= clientHeight` and page-fit checks.
- Prohibited unreadably small text as an overflow workaround.

### Navigation Placement

- Moved the Course Menu trigger from the top-left header to the bottom-left footer/control rail.
- Kept the full course directory hidden by default in an overlay drawer.
- Clarified that only the drawer/settings surfaces may use internal scrolling; normal scenes may not.

### Narration UI

- Replaced the permanent footer voice selector and visible voice name with a compact icon-only narration control in the bottom-right.
- Removed the large `Narrate` / `语音讲解` text-button pattern from the default UI.
- Moved detailed voice, speed, captions, replay, and test controls into a compact popover/modal.

### Voice Quality Curation

- Limited the visible voice list to a maximum of three high-quality voices per active locale.
- Added automatic scoring and selection of the best available exact-locale voice.
- Added preferred Microsoft Natural, Google, and Apple voice families for `en-US`, `zh-CN`, `zh-TW`, and `ja-JP`.
- Added filtering/penalties for low-quality or legacy voice families such as eSpeak, Festival, MBROLA, Compact, Legacy, Robot, and Desktop.
- Required deduplication and a single fallback when no curated voice is available.

### Presentation Hygiene

- Removed learner-visible `Source mapping` / `源内容映射` sections.
- Removed learner-visible `Narration transcript` / `旁白文本` sections.
- Required source references to remain in internal data, Course Map, and QA Report.
- Required narration text to remain in localized data, with optional captions available through audio settings.
- Clarified that authoring notes, debug output, QA metadata, and review labels must be hidden in normal presentation mode.

### Updated Files

- Updated `SKILL.md` to version 2.1.0.
- Updated `UI_DESIGN_SPEC.md` with viewport, control-placement, presentation-hygiene, and narration specifications.
- Updated `MASTER_PROMPT.md` and `QUICK_PROMPT.md` to enforce the new output behavior.
- Updated `README.md` with the new fixed defaults and QA requirements.

## 2.0.0

### UI and Branding

- Fixed the Micas primary color at `#00899F`.
- Added a coherent dark navy visual system derived from the successful preview design.
- Added explicit rules preventing an accidental white rectangular logo block.
- Added explicit rules preventing a dominant plain-white main content panel.
- Added hero-layout, product-frame, card, typography, motion, and responsive specifications.
- Added a dedicated `UI_DESIGN_SPEC.md` visual contract.

### Navigation

- Changed the full course directory from a permanently docked sidebar to a hidden-by-default overlay drawer.
- Added drawer behavior for selection, Escape, backdrop click, fullscreen, Video mode, mobile, and accessibility focus management.

### Languages

- Expanded language support to English, Simplified Chinese, Traditional Chinese, and Japanese.
- Set English as the mandatory first-load default.
- Replaced large language toggles with a compact dropdown.
- Required the visible language button label to remain `Language` in every locale.
- Added locale-specific TTS preferences and four-language completeness checks.

### Prompt and QA

- Updated `SKILL.md`, `MASTER_PROMPT.md`, and `QUICK_PROMPT.md` to enforce the new UI and language requirements.
- Updated `README.md` with new defaults and package structure.
- Added UI/brand, language, drawer, offline, accessibility, and functional QA acceptance checks.
