# Micas Course Experience Specification

Version: **2.4.0**

This is a narrowly scoped override for the **Micas Doc-to-Interactive-Training Skill**. It changes only the eight items defined below. All rules in `core/SKILL_v2.3.2.md`, `UI_DESIGN_SPEC.md`, and `HEADER_UI_SPEC.md` remain active unless this file is more specific.

# 1. Larger Learner-Facing Body Typography

The current visual direction is retained, but learner-facing body copy must be easier to read on desktop.

Recommended desktop typography:

```css
:root {
  --body-primary: clamp(21px, 1.45vw, 27px);
  --body-secondary: clamp(19px, 1.25vw, 23px);
  --body-compact: clamp(18px, 1.05vw, 21px);
}

.scene-lead,
.hero-description,
.question-text {
  font-size: var(--body-primary);
  line-height: 1.45;
}

.card-body,
.step-body,
.answer-option,
.supporting-copy {
  font-size: var(--body-secondary);
  line-height: 1.42;
}

.caption,
.microcopy,
.meta-copy {
  font-size: var(--body-compact);
  line-height: 1.35;
}
```

Rules:

- At 1366×768 desktop QA, normal learner-facing body text should generally not fall below `18px`.
- Important explanatory copy should normally be `20px` or larger.
- Do not make text smaller merely to force a crowded page to fit. Shorten, redesign, or split the scene instead.
- Preserve the existing large-title hierarchy; this change raises body readability without flattening title emphasis.

# 2. Approved Main-Content Visual References

Inspect these bundled references before designing the main learning scenes:

- `assets/ui-reference/content-hero-product-split-reference.svg`
- `assets/ui-reference/content-checkpoint-positioning-reference.svg`
- `assets/ui-reference/content-checkpoint-redundancy-airflow-reference.svg`
- `assets/ui-reference/content-key-metrics-power-reference.svg`

They demonstrate preferred patterns:

- very large selective headline typography;
- a clear eyebrow/module label;
- strong 50/50 or 55/45 text-and-product-image composition;
- complete, large technical images inside controlled light frames;
- three or fewer substantial support cards when appropriate;
- oversized numbers and short labels for memorable specifications;
- cyan accent chips, restrained white surfaces, and deep-navy page integration;
- obvious visual hierarchy rather than equal-weight grids.

Use these screenshots as composition guidance, not as literal course pages. Recreate the design language with live HTML/CSS, localizable text, and authentic source images.

# 3. Hierarchical Course Architecture

The course directory and learning content must have a clear layered structure:

```text
Course
  ├─ Module 1: Orientation / Why it matters
  │    ├─ Scene 1
  │    ├─ Scene 2
  │    └─ Scene 3
  ├─ Module 2: Recognition / Concepts
  ├─ Module 3: Preparation / Workflow
  ├─ Module 4: Operation / Installation
  ├─ Module 5: Troubleshooting / Maintenance
  └─ Final Module: Review & Assessment
```

Rules:

- Organize content into multiple logical learning modules based on competencies and work sequence, not source-document page numbers.
- Each module must have a clear learning purpose and coherent scene order.
- Directory hierarchy must visually distinguish course, module, and scene levels.
- Modules may contain orientation, explanation, demonstration, practice, and summary scenes.
- Avoid one flat list of dozens of scenes with no learning hierarchy.
- Typical full courses should use enough modules to make navigation meaningful; do not force an arbitrary count when the source does not support it.

# 4. Desktop-First Responsive Adaptation

The course must adapt to desktop, tablet, and phone. Priority is:

1. desktop presentation quality;
2. tablet usability;
3. phone usability.

Desktop remains the visual master and must be perfected first at:

- 1920×1080;
- 1600×900;
- 1366×768.

Then validate responsive variants at representative sizes such as:

- tablet landscape: 1180×820 or 1024×768;
- tablet portrait: 820×1180 or 768×1024;
- phone portrait: 430×932 and 390×844.

Responsive rules:

- Preserve the same course content and navigation logic.
- Tablet and phone may use stacked columns, compact headers, icon-only secondary controls, shortened contextual subtitles, and locale-specific line breaks.
- Do not shrink desktop typography, images, or hierarchy merely to make all devices share one identical layout.
- Prefer responsive scene variants and additional scene splitting over unreadably small text.
- Mobile/tablet must remain functional with no overlap, inaccessible controls, missing content, or clipped technical images.
- If perfect visual parity is impossible, retain the best PC composition while providing a clean, usable tablet/phone variant.

# 5. Icons for Header Utility Controls

The upper-right controls must include small, clear icons while preserving their existing order and behavior.

Reference:

`assets/ui-reference/header-action-icons-reference.svg`

Required controls:

- language selector: language/globe/translation icon plus the current language;
- Auto Play or Video mode: video-camera or play icon plus its label;
- Fullscreen: four-corner fullscreen icon plus its label, or icon-only at compact widths.

Rules:

- Use inline SVG icons or a bundled local icon set; do not use emoji.
- Normal desktop icon size: about `20–24px`.
- Keep icon and label vertically centered with a `10–14px` gap.
- Icons use the same bright neutral text color as their labels.
- Maintain accessible names with `aria-label`; decorative icon SVGs use `aria-hidden="true"`.
- Do not change the approved header brand lockup or crowd it with oversized controls.

# 6. Consolidated Final Assessment Only

All graded quiz and examination questions must be consolidated into the final course module.

Rules:

- Do not create a separate graded quiz at the end of every instructional module.
- Instructional modules should focus on learning, demonstration, guided decisions, and concise summaries.
- Ungraded interactions such as hotspots, reveal cards, reflection prompts, or scenario exploration are allowed when useful, but they must not appear as chapter examinations.
- Create one final module named according to the locale, such as `Review & Assessment`.
- The final module contains:
  1. review/recap scenes;
  2. the existing dedicated assessment-introduction scene;
  3. all graded questions;
  4. results, feedback, and completion scenes.
- Every graded question must still map back to the source material.

# 7. Auto Play Behavior for Assessment Pages

Assessment pages are learner-controlled and must not behave like narrated video slides.

Rules:

- Auto Play/Video mode may narrate and advance normal instructional scenes according to the existing narration-completion contract.
- Auto Play must pause at the dedicated assessment-introduction scene and wait for the learner to select `Start Assessment`.
- Graded question pages do **not** auto-narrate, auto-answer, auto-submit, or auto-advance.
- On entering the first graded question, suspend Auto Play and show a clear paused/manual state.
- The learner must choose an answer and navigate manually.
- Do not start a fixed dwell timer on a question page.
- Do not call `goNext()` from speech, animation, or timeout callbacks while an assessment question is active.
- After the assessment is completed, the course may proceed to results/completion under manual control. Auto Play may be restarted only through an explicit learner action.

Recommended guard:

```js
function isAssessmentQuestion(scene) {
  return scene?.type === 'assessment-question';
}

async function playCurrentSceneThenAdvance() {
  const scene = getCurrentScene();
  if (isAssessmentQuestion(scene)) {
    stopAutoPlay();
    setPlaybackState('manual-assessment');
    return;
  }
  await playNarrationToCompletion(scene);
  if (autoPlayEnabled) goNext();
}
```

An assessment question that is skipped before the learner can answer is a release-blocking defect.

# 8. Full-Course Search

Add an icon-only search control to the footer.

Required footer action order:

```text
Search → Previous → Next → narration → Audio settings
```

Placement and appearance:

- Search is immediately to the left of Previous.
- Use a magnifying-glass icon only; no visible `Search` text on the button.
- Match the existing footer icon-button size, border, radius, and hover/focus treatment.
- Keep `aria-label="Search course"` and a localized tooltip.

Behavior:

- Search across module titles, scene titles, body text, keywords, procedures, warnings, and assessment content.
- Search the active language by default.
- Open results in an overlay, modal sheet, or drawer without changing the current scene until the learner selects a result.
- Group results by module and show a short localized snippet.
- Selecting a result navigates directly to the scene, closes the search UI, and visually highlights the matching term where practical.
- Search UI may scroll internally; the underlying course page remains fixed.
- Support keyboard focus, Escape to close, Enter to open a result, and accessible result counts.
- The search button and panel must work offline because the entire index is embedded in the course.

# 9. Targeted QA Additions

In addition to all existing QA, verify:

- body text meets the larger readability targets at desktop viewports;
- all four main-content reference assets and the header-control reference were inspected;
- course navigation shows clear course → module → scene hierarchy;
- graded questions exist only in the final assessment module;
- Auto Play stops before graded questions and never skips a question;
- language, Auto Play, and Fullscreen controls show appropriate icons;
- Search appears immediately before Previous and searches the complete active-language course;
- desktop quality remains the visual priority while tablet and phone remain clean and functional.

# 10. Scope Lock

Version 2.4.0 changes only:

1. learner-facing body-text size;
2. bundled main-content visual references;
3. hierarchical module structure;
4. desktop-first tablet/phone adaptation;
5. icons for language, Auto Play, and Fullscreen;
6. final-module-only graded assessment;
7. manual assessment behavior under Auto Play;
8. full-course Search before Previous.

Do not alter the existing header brand lockup, colors, footer button sizing, global Next availability, narration voice priority, image-integrity rules, source grounding, multilingual policy, or any other established behavior except where this specification explicitly requires it.