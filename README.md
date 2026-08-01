# Micas Doc-to- Interactive-Training Skill

Version: **2.2.0**

This package converts technical documents into polished, source-grounded Micas interactive training courses.

## Package Contents

- `SKILL.md` — complete workflow, source-grounding rules, one-screen behavior, visual hierarchy, image handling, languages, narration, HTML requirements, and QA.
- `UI_DESIGN_SPEC.md` — mandatory visual contract covering Micas colors, typography scale, focal composition, image fit, controls, progress, responsive behavior, and failure conditions.
- `MASTER_PROMPT.md` — detailed prompt for full or safety-critical projects.
- `QUICK_PROMPT.md` — concise Chinese prompt for routine projects.
- `CHANGELOG.md` — release history.

## Recommended Use

1. Attach the source manual, SOP, policy, presentation, or product guide.
2. Instruct the AI to read `SKILL.md` and treat `UI_DESIGN_SPEC.md` as mandatory.
3. Use `MASTER_PROMPT.md` for a full production course or `QUICK_PROMPT.md` for routine work.
4. Provide audience, learning goal, duration, and assessment level.
5. Review the generated Course Map and QA Report before publication.

## Fixed Defaults

- Brand: Micas Networks
- Primary color: `#00899F`
- Visual style: dark premium technical presentation based on the successful Preview layout
- Scene behavior: one browser viewport per scene, no normal vertical scrolling
- Visual hierarchy: one dominant focal element per scene
- Typography: large hero/key titles and clearly secondary support content
- Layout: asymmetric compositions preferred over repetitive equal-card grids
- Technical images: large, complete, `object-fit: contain`, no accidental clipping
- Default language: English
- Required languages: English, 简体中文, 繁體中文, 日本語
- Language control: displays only the selected language name; no `Language` prefix
- Course directory: hidden by default, opened from bottom-left
- Progress: larger visible bar, approximately 8–12 px high
- Narration: icon-only control at bottom-right with curated high-quality voices
- Presentation pages: no source mapping, transcript, QA, or authoring metadata
- Output: one self-contained offline HTML file plus Course Map, QA Report, and README

## Core QA Viewports

Validate every scene at 100% zoom in every supported language:

- 1920×1080
- 1600×900
- 1366×768

The page and active scene must not overflow vertically. Titles, controls, and images must not be clipped.

## Visual Hierarchy Expectation

Every scene should make the main point obvious within a few seconds:

- one large title, visual, key metric, warning, or active step;
- two to four supporting points;
- one primary card or image larger than secondary elements;
- intentional whitespace;
- no default reliance on flat equal-size 2×2 card grids.

## Image Expectation

Technical visuals should be large enough to teach from and shown completely. Crop irrelevant source-page whitespace before embedding. If a figure cannot be legible in one scene, use a full-view scene followed by annotated detail scenes rather than cropping half of the figure.

## Publishing Note

Browser voices vary by operating system and browser. Generated courses shortlist no more than three high-quality voices per locale and may replace browser TTS with recorded audio in production while retaining the same multilingual data model and interface.