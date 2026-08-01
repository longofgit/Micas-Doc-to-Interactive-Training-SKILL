# Micas Doc-to-Interactive-Training Skill

Version: **2.1.0**

This package converts technical documents into polished, source-grounded Micas interactive training courses.

## Package Contents

- `SKILL.md` — complete workflow, grounding rules, PPT-like viewport contract, four-language standard, curated narration rules, HTML requirements, and QA checklist.
- `UI_DESIGN_SPEC.md` — visual and interaction contract covering Micas colors, logo integration, one-screen scene layouts, bottom-left hidden navigation, bottom-right narration control, responsive behavior, and failure conditions.
- `MASTER_PROMPT.md` — detailed copy-and-paste prompt for full or safety-critical projects.
- `QUICK_PROMPT.md` — concise Chinese prompt for routine projects.
- `CHANGELOG.md` — release history.

## Recommended Use

1. Attach the source manual, SOP, policy, presentation, or product guide.
2. Use `MASTER_PROMPT.md` for a full production course.
3. Use `QUICK_PROMPT.md` for routine conversion.
4. Provide audience, goal, duration, and assessment level.
5. Review the generated Course Map and QA Report before publication.

## Fixed Defaults

- Brand: Micas Networks
- Primary color: `#00899F`
- Visual style: dark premium technical UI based on the successful preview layout
- Scene behavior: one browser viewport per scene, PPT-like Previous/Next navigation
- Normal-page scrolling: disabled; long content must be split into more scenes
- Default language: English
- Required languages: English, 简体中文, 繁體中文, 日本語
- Language button label: always `Language`
- Course directory: hidden by default; trigger in the bottom-left footer
- Narration control: compact icon-only button in the bottom-right
- Voice list: curated, maximum three high-quality voices per active locale
- Source mapping and narration transcript: retained in data/reports, hidden from learner presentation pages
- Default output: one self-contained offline HTML file

## Required Viewport QA

At 100% browser zoom, all four languages should fit without vertical page or scene scrolling at:

- 1920 × 1080
- 1600 × 900
- 1366 × 768

If a scene does not fit, divide or redesign it. Do not shrink text below a readable presentation size.

## Narration Notes

Browser voices vary by operating system and browser. The generated course should:

- automatically rank exact-locale, Natural/Neural/Premium/Enhanced voices;
- prefer the curated Microsoft, Google, and Apple voice families listed in the Skill;
- filter legacy or low-quality voices;
- show no more than three choices per locale;
- show only the compact narration icon in the normal footer;
- place detailed voice and speed settings in a popover.

Production deployments may replace browser TTS with recorded audio while retaining the same four-language course data model and UI.
