# Micas Doc-to- Interactive-Training Skill

Version: **2.0.0**

This package converts technical documents into polished, source-grounded Micas interactive training courses.

## Package Contents

- `SKILL.md` — complete workflow, grounding rules, four-language standard, HTML requirements, UI acceptance criteria, and QA checklist.
- `UI_DESIGN_SPEC.md` — dedicated visual contract covering Micas colors, logo integration, preview-style layouts, hidden navigation, responsive behavior, and failure conditions.
- `MASTER_PROMPT.md` — detailed copy-and-paste prompt for full or safety-critical projects.
- `QUICK_PROMPT.md` — concise Chinese prompt for routine projects.
- `CHANGELOG.md` — summary of changes in this release.

## Recommended Use

1. Attach the source manual, SOP, policy, presentation, or product guide.
2. Use `MASTER_PROMPT.md` for a full production course.
3. Use `QUICK_PROMPT.md` for routine conversion.
4. Provide audience, goal, duration, and assessment level.
5. Review the generated course map and QA report before publication.

## Fixed Defaults

- Brand: Micas Networks
- Primary color: `#00899F`
- Visual style: dark premium technical UI, based on the successful preview layout
- Default language: English
- Required languages: English, 简体中文, 繁體中文, 日本語
- Language button label: always `Language`
- Course directory: hidden by default in an overlay drawer
- Default output: one self-contained offline HTML file

## Publishing Note

Browser voices vary by operating system and browser. Production deployments may replace browser TTS with recorded audio while retaining the same four-language course data model and UI.
