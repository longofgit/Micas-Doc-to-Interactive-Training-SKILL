---
name: micas-doc-to-interactive-training
display_name: Micas Doc-to-Interactive-Training Skill
description: Convert technical documents into source-grounded, Micas-branded, self-contained interactive training courses with PPT-like scenes, strict production QA, multilingual narration, assessment, and an approved Micas header lockup.
version: 2.3.3
---

# Micas Doc-to-Interactive-Training Skill

## Mandatory Load Order

For every document-to-training task, read and apply these files in order:

1. `core/SKILL_v2.3.2.md` — the complete v2.3.2 production workflow and all existing content, navigation, image, language, voice, assessment, Auto Play, and QA rules.
2. `UI_DESIGN_SPEC.md` — the complete general Micas visual implementation contract.
3. `HEADER_UI_SPEC.md` — the mandatory v2.3.3 upper-left header override.
4. `MASTER_PROMPT.md` or `QUICK_PROMPT.md` — the task launcher selected for the project.

Do not skip the referenced files. The core rules remain fully active.

## Rule Precedence

- Source-grounding, technical accuracy, safety, navigation, image integrity, language, narration, Auto Play, assessment, one-screen behavior, and QA rules remain exactly as defined in `core/SKILL_v2.3.2.md`.
- `HEADER_UI_SPEC.md` overrides only the upper-left header/brand-lockup design where it is more specific than the older core or `UI_DESIGN_SPEC.md` wording.
- No other UI or functional behavior is changed by v2.3.3.

## v2.3.3 Header Requirement

The upper-left course header must follow the approved visual reference:

`assets/ui-reference/header-lockup-reference.svg`

The generated header must use live HTML/CSS and the real transparent Micas logo. The reference image is for visual inspection and proportion guidance; do not insert the screenshot itself as the course header.

Required result:

- a large transparent Micas logo on the left;
- a bold white course title immediately to its right;
- a smaller muted product/platform/module subtitle below the title;
- logo and text vertically centered as one horizontal lockup;
- generous logo-to-text spacing;
- deep-navy integration with no white box or card;
- a subtle cyan divider along the header bottom;
- language, Video, Fullscreen, and other utilities kept at the far right without squeezing or overlapping the lockup.

Desktop target ranges:

- logo width: `190–250px`;
- logo height: `52–72px`;
- course title: `30–44px`, bold;
- subtitle: `18–28px`;
- logo-to-text gap: `28–42px`.

A tiny logo, weak title hierarchy, white logo rectangle, misalignment, overlap, crowding, or right-side controls compressing the brand lockup is a release-blocking UI defect.

## Completion Standard

Generate the complete deliverables, apply the mandatory load order, inspect the bundled header reference, run the existing v2.3.2 production QA plus the v2.3.3 header QA, correct all defects, and only then deliver.