# Master Prompt — Micas Doc-to-Interactive-Training

Attach the source documents, replace the bracketed variables, and execute the complete project.

---

You are an instructional designer, technical trainer, UX designer, multilingual content engineer, front-end developer, and production QA reviewer.

Transform the attached source documents into a complete, source-grounded, premium Micas interactive training course.

## Project Settings

- Course title: `[AUTO-GENERATE OR ENTER TITLE]`
- Target audience: `[AUDIENCE]`
- Learning goal: `[LEARNING GOAL]`
- Desired duration: `[E.G. 30–45 MINUTES]`
- Assessment level: `[BASIC / INTERMEDIATE / CERTIFICATION-STYLE]`
- Brand: `Micas Networks`
- Primary color: `#00899F`
- Visual master locale: `English`
- Default language: `English`
- Required languages: `English / 简体中文 / 繁體中文 / 日本語`
- Output: `One self-contained offline HTML plus Course Map, QA Report, and README`

## Source and Accuracy

1. Use the attached files as the primary and authoritative basis.
2. Read complete relevant material, including tables, figures, screenshots, warnings, procedures, appendices, and embedded images.
3. Preserve exact terminology, product names, numerical limits, procedure order, warnings, and operational boundaries.
4. Do not silently invent unsupported technical information or correct suspected source errors.
5. Flag ambiguity or inconsistency in the QA Report.
6. Maintain source mapping from every scene and assessment item to a source section, page, table, or figure.
7. Keep source mapping in course data, Course Map, and QA Report—not in learner presentation pages.

## Learning Architecture

Do not convert the source page by page. Reorganize it around learner competencies.

Create:

- orientation and learning outcomes;
- focused competency modules;
- scenes with one primary objective each;
- authentic visual explanations;
- step-by-step procedures;
- realistic troubleshooting and safety decisions;
- module checks;
- learning review;
- a dedicated final-assessment introduction scene;
- final assessment with explanatory feedback;
- completion and next-actions scene.

Before laying out each scene, define:

- `primaryMessage`;
- `supportingPoints`;
- `referenceDetails`;
- `focalVisual`;
- English `layoutVariant`;
- any required locale-specific variants.

Every scene must have one visually dominant element. Do not make all cards and text blocks look equally important.

## English-First Visual Master

Design English first for the strongest composition, title scale, spacing, image size, and line breaks.

Other locales may use:

- shorter authored wording with identical meaning;
- deliberate line breaks;
- slightly adjusted readable typography;
- different column proportions;
- locale-specific layout variants;
- additional semantic sub-scenes when necessary.

Do not weaken the English page merely to force identical multilingual density. All locales must still pass functional and viewport QA.

## Mandatory PPT-Like Behavior

The course behaves like a presentation deck, not a scrolling webpage.

1. One scene occupies one complete browser viewport.
2. Header, stage, and footer fit within `100dvh`.
3. Body and normal scene stage use `overflow: hidden`.
4. No normal learner scene requires vertical scrolling.
5. Previous/Next, progress, Course Menu, narration, and settings remain visible.
6. Long content is divided into additional scenes.
7. Do not solve overflow by clipping content, clipping images, or making text unreadably small.
8. Validate at 100% zoom for 1920×1080, 1600×900, and 1366×768.
9. Validate English first, then Simplified Chinese, Traditional Chinese, and Japanese.

Recommended checks:

```js
const sceneFits = activeScene.scrollHeight <= activeScene.clientHeight + 1;
const pageFits = document.documentElement.scrollHeight <= window.innerHeight + 1;
```

## Strict Production Overflow Policy

The final learner UI must never display:

- `Layout overflow detected`;
- overflow or fit warnings;
- debug badges;
- source-review messages;
- QA metadata;
- authoring diagnostics.

Overflow diagnostics may exist only in explicit reviewer mode and must be off by default.

If a scene fails fit checks:

1. shorten nonessential presentation wording;
2. redesign the composition;
3. move secondary details to another scene;
4. split the scene;
5. rerender and retest.

A visible overflow notice or an overflowing scene is a release-blocking defect.

## Stage Utilization

Do not produce pages with one populated side and a large accidental blank half.

- Never render an empty image frame, blank column, or placeholder card.
- Use two columns only when both contain meaningful teaching content.
- If a planned visual is missing, use a purposeful single-column composition.
- Meaningful content should normally occupy roughly 65–90% of the usable stage.
- Avoidable empty regions of about one-third or more of the stage fail visual QA.
- Intentional whitespace is allowed only when it strengthens the focal message.

## Visual Direction

Use the successful Micas preview style:

- deep-navy unified shell;
- Micas cyan `#00899F`;
- large selective typography;
- one strong focal element;
- asymmetric 55/45, 58/42, or 60/40 layouts where appropriate;
- one primary card or visual larger than supporting elements;
- rounded blue-tinted translucent cards;
- restrained professional motion;
- no generic LMS look;
- no dominant plain-white body panel;
- no accidental white logo rectangle.

Suggested typography:

```css
.hero-title { font-size: clamp(56px, 6vw, 96px); }
.scene-title { font-size: clamp(40px, 4.2vw, 68px); }
.key-metric { font-size: clamp(52px, 5.5vw, 88px); }
```

Do not use repetitive equal-sized grids as the default layout.

## Technical Image Integrity

Technical images must be complete and useful.

- Use authentic source figures.
- Pre-crop source page margins, headers, footers, and irrelevant whitespace.
- Use `object-fit: contain` for products, diagrams, screenshots, and installation figures.
- Never use `cover` for technical content.
- Preserve the full device, labels, arrows, and aspect ratio.
- Allocate about 40–55% of the stage for a normal image/text scene and 55–75% when the image is the primary learning object.
- If a complete image cannot remain legible, use a full-view scene followed by explicit zoom/detail scenes.
- Never show only half of a technical image.
- Never leave a large frame containing a tiny image with excessive unused space.

Run image QA after fonts and all images load/decode. Verify nonzero natural dimensions, complete visibility, no ancestor clipping, readable labels, and `object-fit: contain`.

A missing, half-visible, or unintentionally cropped image is a release-blocking defect.

## Header and Language

Header contains:

- integrated transparent Micas logo;
- course/product title and compact scene subtitle;
- selected language;
- Video mode;
- Fullscreen.

The visible language selector shows only:

- `English`
- `简体中文`
- `繁體中文`
- `日本語`

Do not display a visible `Language` prefix. Keep `aria-label="Language"`.

## Footer Controls

Use substantial controls on desktop.

- Course Menu, scene count, and the prominent progress bar on the left;
- one far-right control cluster in this exact order: Previous, Next, narration, Audio settings.

Do not center Previous/Next and do not move narration/settings away from the right edge.

Recommended minimums:

```css
.nav-button {
  min-width: 150px;
  min-height: 58px;
  padding: 0 24px;
  font-size: 18px;
  border-radius: 18px;
  flex-shrink: 0;
}

.icon-control {
  width: 58px;
  height: 58px;
  min-width: 58px;
  min-height: 58px;
  flex-shrink: 0;
}

.progress-group {
  min-width: 260px;
  max-width: 560px;
}

.progress-track { height: 9px; }
```

Desktop Previous/Next must use labels plus arrows. Tiny arrow-only squares are allowed only in compact/mobile mode.

## Sequential Navigation Logic

- Treat all scenes as one global ordered sequence.
- Next must be enabled whenever a following scene exists.
- A module-ending scene must advance to the next module.
- Module checks and final-assessment questions must allow Next even when unanswered.
- Do not gate Next on `answered`, `submitted`, `passed`, feedback, score, or module-completion state.
- Preserve unanswered questions as unanswered so the learner can revisit them.
- Only the absolute final completion scene may disable or replace Next.
- Keep the right-side control order: Previous → Next → narration → Audio settings.

## Auto Play Narration Timing

When Auto Play or Video mode is active:

- keep the current scene visible until its complete narration finishes;
- advance only from the final narration utterance's `onend` event;
- never use a fixed timer or estimated reading duration to advance while speech is active;
- if narration is split into chunks, wait until the final chunk ends;
- pausing narration must pause the page transition;
- narration errors must stop Auto Play on the current scene rather than skip it;
- manual navigation must cancel and invalidate active narration so stale callbacks cannot advance again;
- only scenes with intentionally no narration may use a short explicit visual dwell.

## Narration and Google-First Voices

The normal footer uses an icon-only speaker/play button; detailed settings are in a popover.

For every locale, search for a matching Google voice and select it by default when available.

Preferred fragments:

- English: `Google US English`, `Google English`;
- Simplified Chinese: `Google 普通话`, `Google Mandarin`, `Google 中文`;
- Traditional Chinese: `Google 國語`, `Google Chinese (Taiwan)`, `Google 中文（台灣）`;
- Japanese: `Google 日本語`, `Google Japanese`.

Priority:

1. exact-locale Google;
2. exact-language Google;
3. exact-locale Microsoft Natural/Neural;
4. exact-locale Apple;
5. best exact-locale fallback.

Show no more than three curated voices. Put an available Google option first. Do not fabricate voices that the browser does not expose; record unavailable Google voices and fallback behavior in the QA Report and README.

## Assessment Introduction

Before the first final-assessment question, insert a separate transition scene with:

- confirmation that the teaching section is complete;
- assessment purpose;
- number of questions;
- estimated duration;
- pass score or scoring method;
- answer/feedback instructions;
- readiness message;
- clear `Start Assessment` button.

Video/Auto mode pauses and waits on this scene.

## Presentation Hygiene

Learner pages must not show:

- source mapping;
- narration transcript accordions;
- raw page references;
- QA labels;
- debug information;
- overflow notices;
- missing-asset placeholders;
- generation metadata.

## Technical Output

Generate one self-contained HTML file with embedded CSS, JavaScript, images, and course data. Do not depend on external CDNs, web fonts, scripts, or runtime image URLs.

Include:

- fixed `100dvh` shell;
- no normal-page scrolling;
- English-first design and four authored languages;
- hidden course drawer opened from bottom-left;
- selected-language-only dropdown;
- substantial Previous/Next and audio controls;
- prominent progress bar;
- Fullscreen and Video mode;
- Google-first narration selection when available;
- module checks and final scoring;
- assessment-introduction scene;
- `localStorage` persistence;
- optional captions;
- accessibility and reduced-motion support.

## Mandatory Pre-Delivery QA

Render and inspect every scene at:

- 1920×1080;
- 1600×900;
- 1366×768.

Run English first, then all other locales.

Verify:

- no page or scene overflow;
- no visible diagnostic or QA message;
- no header/footer clipping;
- no horizontal clipping;
- one obvious focal point;
- no accidental half-empty page or blank panel;
- no tiny desktop controls;
- technical images are complete, large, and readable;
- no image is half-visible or unintentionally cropped;
- Google is selected by default when available;
- final assessment has a transition scene;
- Next works across every module boundary and every unanswered assessment page;
- the footer action group is right-aligned in the order Previous, Next, narration, Audio settings;
- Auto Play advances only after the final narration completion event and never while speech is active or paused;
- English remains the strongest visual master;
- offline assets, quizzes, navigation, persistence, narration, and accessibility work.

Do not deliver until every release-blocking defect has been corrected.

## Required Deliverables

1. `[COURSE_NAME]_Interactive_Training.html`
2. `[COURSE_NAME]_Course_Map.md`
3. `[COURSE_NAME]_QA_Report.md`
4. `[COURSE_NAME]_README.md`

The QA Report must document viewport results, image integrity, stage utilization, control sizes, English-master review, multilingual completeness, Google voice availability/fallback, assessment transition, technical accuracy, and source issues.

Do not stop at an outline or prototype. Generate the complete artifacts, validate them, fix defects, and provide the final downloadable files.

---