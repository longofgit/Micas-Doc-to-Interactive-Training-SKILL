# Micas Doc-to-Interactive-Training Skill

Version: **2.3.3**

This repository converts manuals, SOPs, product guides, policies, presentations, and technical documents into source-grounded, Micas-branded interactive training courses.

## Required Reading Order

For reliable execution, the AI must read:

1. `SKILL.md`
2. `core/SKILL_v2.3.2.md`
3. `UI_DESIGN_SPEC.md`
4. `HEADER_UI_SPEC.md`
5. `MASTER_PROMPT.md` or `QUICK_PROMPT.md`

`HEADER_UI_SPEC.md` is a focused v2.3.3 override. All non-header rules remain defined by the preserved v2.3.2 core.

## Package Contents

- `SKILL.md` — v2.3.3 entry point, load order, precedence, and completion requirements.
- `core/SKILL_v2.3.2.md` — complete preserved production workflow and rules from v2.3.2.
- `UI_DESIGN_SPEC.md` — general Micas visual implementation contract.
- `HEADER_UI_SPEC.md` — mandatory upper-left header/brand-lockup specification.
- `MASTER_PROMPT.md` — full formal-project prompt.
- `QUICK_PROMPT.md` — concise Chinese project prompt.
- `assets/ui-reference/header-lockup-reference.svg` — approved header composition screenshot reference.
- `assets/ui-reference/README.md` — instructions for using the visual asset.
- `CHANGELOG.md` — current release notes.
- `core/CHANGELOG_v2.3.2.md` — preserved earlier release history.
- `core/README_v2.3.2.md` — preserved earlier package documentation.

## Can Images Be Included in a Skill?

Yes. Reference screenshots, diagrams, templates, and other visual assets can be stored inside the Skill folder.

Best practice is to:

- place them in a clearly named directory such as `assets/ui-reference/`;
- reference their exact path from `SKILL.md` or a mandatory specification file;
- explain what the image demonstrates and how it should be used;
- provide a written specification as the authoritative fallback;
- avoid making critical instructions depend only on image inspection;
- distinguish visual reference assets from source-document images used in generated courses.

The bundled header screenshot is supplemental design guidance. Generated courses must recreate its style using live HTML/CSS, localizable text, and the actual transparent Micas logo; the screenshot itself must not be used as a flattened production header.

## v2.3.3 Header Style

The upper-left header now requires:

- a large Micas logo on the left;
- a bold white course title on the right;
- a smaller muted product/module subtitle below the title;
- vertical centering and generous spacing;
- direct integration into the deep-navy header;
- a restrained cyan bottom divider;
- far-right utilities that do not squeeze or overlap the brand lockup.

Desktop reference ranges:

- logo: `190–250px` wide;
- title: `30–44px`;
- subtitle: `18–28px`;
- logo-to-text gap: `28–42px`.

See `HEADER_UI_SPEC.md` for the complete rules and QA criteria.

## Scope of v2.3.3

This release changes only the upper-left header visual specification and adds the bundled visual reference.

It does **not** change:

- one-screen/PPT-like behavior;
- global Previous/Next navigation;
- footer button order or alignment;
- Auto Play narration-completion behavior;
- Google-first voice selection;
- image integrity rules;
- multilingual behavior;
- assessment structure;
- source mapping or technical-accuracy requirements.

## Standard Invocation

```text
Please use the Micas Doc-to-Interactive-Training Skill.
Read SKILL.md and every mandatory referenced file in its load order.
Convert the uploaded source document into the complete production-ready interactive course.
Do not stop at an outline or sample.
```

## Output Standard

The normal deliverables remain:

1. one self-contained offline interactive HTML course;
2. Course Map;
3. QA Report;
4. course README.

The course must pass the preserved v2.3.2 QA requirements plus the v2.3.3 header QA before delivery.