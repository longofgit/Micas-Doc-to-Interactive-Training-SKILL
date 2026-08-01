# Changelog

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
