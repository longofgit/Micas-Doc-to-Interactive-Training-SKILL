---
name: micas-doc-to-interactive-training
display_name: Micas Doc-to-Interactive-Training Skill
description: Convert manuals, SOPs, product guides, policies, and technical documents into source-grounded, Micas-branded, self-contained interactive training courses with PPT-like scenes, strict production QA, English-first visual design, complete technical images, curated Google-first narration, assessments, and offline delivery.
version: 2.3.0
---

# Micas Doc-to-Interactive-Training Skill

## Purpose

Transform static technical documents into a polished, source-grounded interactive course—not a page-by-page summary, document viewer, generic LMS, or narrated document dump.

The default deliverable is a **single self-contained offline HTML course** that opens in modern Chrome or Edge without a server. The learner experience must behave like a presentation deck:

- one scene occupies one browser viewport;
- normal learner scenes never require vertical page scrolling;
- learners move with Previous/Next or keyboard arrows;
- long material is divided into additional scenes;
- every scene has one obvious instructional and visual focal point;
- the final learner UI contains no authoring, debug, overflow, or QA messages.

## Default Project Settings

Unless explicitly overridden:

- **Brand:** Micas Networks
- **Primary color:** `#00899F`
- **Visual direction:** dark, premium, technical, spacious, mission-oriented
- **Visual master locale:** English
- **Default language:** English
- **Supported languages:** English, Simplified Chinese, Traditional Chinese, Japanese
- **Locale keys:** `en`, `zh-CN`, `zh-TW`, `ja`
- **Output:** one offline HTML file plus Course Map, QA Report, and README
- **Scene behavior:** PPT-like, one viewport per scene, no normal-page scrolling
- **Course navigation:** hidden drawer triggered from the bottom-left control rail
- **Language control:** selected language name only; no visible `Language` prefix
- **Narration:** Google-first exact-locale voice selection when available; compact icon control in the bottom-right
- **Assessment:** module checks, a dedicated assessment-introduction scene, final assessment, score, and completion scene

When information is incomplete, infer only nontechnical presentation details. Record assumptions in the QA Report. Never invent technical facts.

# 1. Source-Grounding Rules

1. Treat supplied source files as the primary and authoritative basis.
2. Read complete relevant sections, including tables, figures, captions, warnings, procedures, appendices, screenshots, and embedded images.
3. Preserve terminology, product names, numerical values, safety limits, procedure order, and operational boundaries.
4. Do not silently invent, correct, reconcile, or supplement unsupported technical information.
5. Flag source conflicts or ambiguities in the QA Report rather than choosing silently.
6. Represent safety-critical content accurately and prominently.
7. Maintain traceability from every scene and assessment item to a source page, heading, table, or figure.
8. Keep source mapping out of normal learner pages. Store it in course data, the Course Map, and the QA Report.

# 2. Production Workflow

## Phase 1 — Source Audit

Inspect the full source and build an internal map of:

- document hierarchy;
- audience and prerequisites;
- key concepts and specifications;
- exact procedures and dependencies;
- warnings and prohibited actions;
- reusable visual assets;
- troubleshooting symptoms and resolutions;
- reference-only material;
- contradictions, missing information, and suspected errors.

Do not build a complete course from isolated snippets when the surrounding section matters.

## Phase 2 — Learning Architecture

Convert the source into a competency-based journey, not one scene per source page.

Recommended pattern:

1. Orientation and outcomes
2. Product positioning and hardware anatomy
3. Interfaces, indicators, power, airflow, and specifications
4. Safety and site preparation
5. Unpacking and readiness
6. Installation and connection
7. Commissioning and verification
8. Monitoring and maintenance
9. Troubleshooting scenarios
10. Learning review
11. **Assessment introduction / readiness gate**
12. Final assessment
13. Completion and next actions

Adapt the pattern to the source, but never jump directly from instructional content into the first final-exam question.

## Phase 3 — Content Prioritization

Classify material as:

- **Must perform:** procedures, checks, limits, and safety actions
- **Must recognize:** ports, LEDs, modules, labels, symptoms, and states
- **Must understand:** architecture, airflow, redundancy, dependencies, and rationale
- **Reference only:** exhaustive tables, regulations, dimensions, and rarely used appendices

Actively teach the first three. Put reference-only material in paged reference scenes or a searchable overlay.

## Phase 4 — Message Hierarchy Before Layout

For every scene, explicitly identify:

- `primaryMessage`: the one fact, action, decision, or limit learners must remember;
- `supportingPoints`: normally two to four concise items;
- `referenceDetails`: content moved to another scene or report;
- `focalVisual`: the image, diagram, number, warning, or active step deserving the most space;
- `layoutVariant`: the composition chosen for the English visual master;
- `localeVariants`: only the changes needed for other languages without weakening the English design.

A scene fails instructional design when all cards, paragraphs, images, and headings appear equally important.

## Phase 5 — Scene Design

Each scene should normally contain:

- mission/context label;
- one clear title;
- one short subtitle or promise;
- two to five supporting points;
- one dominant focal visual or highlighted message;
- dedicated narration written for listening;
- optional checkpoint;
- prominent warning when supported by the source.

Use varied layouts:

- premium hero/cover;
- dominant image plus concise explanation;
- oversized key metric or limit;
- hardware hotspot map;
- front/rear panel identification;
- step timeline;
- do/do-not contrast;
- asymmetric specification composition;
- troubleshooting decision path;
- scenario question;
- assessment-introduction scene;
- final score and completion.

Do not use the same equal-card grid on every scene. Equal grids are appropriate only when the items genuinely have equal importance.

# 3. English-First Visual Master

English is the primary visual-reference locale.

1. Design the English scene first for the strongest hierarchy, spacing, line breaks, image scale, and presentation quality.
2. Do not flatten, shrink, or weaken the English layout merely to force identical text density across all languages.
3. Other locales may use:
   - authored shorter wording with identical meaning;
   - deliberate line breaks;
   - slightly adjusted typography within readable limits;
   - locale-specific column proportions;
   - locale-specific layout variants;
   - additional semantic sub-scenes when necessary.
4. Technical content and learning outcomes must remain equivalent across locales.
5. English must remain the first-load default and the visual QA reference.
6. All other locales must still pass fit, image, control, and accessibility QA.

# 4. PPT-Like Viewport Contract

Normal learner scenes are fixed presentation stages, not scrolling webpages.

```css
html, body {
  width: 100%;
  height: 100%;
  margin: 0;
  overflow: hidden;
}

.course-shell {
  height: 100dvh;
  min-height: 100vh;
  display: grid;
  grid-template-rows: var(--header-h) minmax(0, 1fr) var(--footer-h);
  overflow: hidden;
}

.scene-stage,
.scene {
  min-width: 0;
  min-height: 0;
  overflow: hidden;
}

.scene { height: 100%; }
```

Requirements:

1. Header, stage, and footer fit inside `100dvh`.
2. No normal learner scene requires vertical browser scrolling.
3. Previous/Next, progress, Course Menu, narration, and settings remain visible.
4. Validate at 100% zoom for at least:
   - 1920×1080;
   - 1600×900;
   - 1366×768.
5. Validate English first, then every other supported locale.
6. Use responsive scene variants, tabs, or more scenes for smaller screens.
7. Never solve overflow by hiding required content, clipping images, or making text unreadably small.

## Content Budget

Treat each scene like a designed slide:

- title: preferably one or two lines;
- subtitle: no more than two lines;
- supporting points: normally two to five;
- cards: normally one dominant card plus two or three supporting cards;
- quiz: one question per scene;
- warning: one focused warning block;
- tables: essential rows only, or divide into more scenes.

# 5. Strict Overflow Policy

## Production UI Rule

The final learner-facing HTML must never display messages such as:

- `Layout overflow detected`;
- `Overflow warning`;
- `Fit error`;
- `Source review required`;
- debug badges, QA banners, console output, or authoring diagnostics.

Visible diagnostic UI is a **release-blocking defect**.

Overflow detection must run silently in preflight/reviewer logic. It may log details to the developer console or QA report only when explicit reviewer mode is enabled. Production mode must keep reviewer mode off.

```js
const REVIEW_MODE = false;

async function scenePreflight(scene) {
  await document.fonts?.ready;
  const images = [...scene.querySelectorAll('img')];
  await Promise.all(images.map(async img => {
    if (!img.complete) await new Promise(resolve => {
      img.addEventListener('load', resolve, { once: true });
      img.addEventListener('error', resolve, { once: true });
    });
    try { await img.decode?.(); } catch (_) {}
  }));
  await new Promise(requestAnimationFrame);
  await new Promise(requestAnimationFrame);

  return {
    sceneFits: scene.scrollHeight <= scene.clientHeight + 1,
    pageFits: document.documentElement.scrollHeight <= window.innerHeight + 1
  };
}
```

If a scene fails:

1. remove nonessential wording;
2. redesign the layout;
3. move secondary details to another scene;
4. create a follow-up reference scene;
5. split the scene;
6. rerun preflight.

Do not deliver until every required scene passes.

# 6. Stage Utilization and Empty-Space Policy

Intentional whitespace around a focal element is valuable. Accidental empty half-pages are not.

1. Never render an empty visual frame, placeholder column, blank card, or unused panel.
2. Render a two-column layout only when both columns contain meaningful teaching content.
3. If the planned visual is missing, unusable, or too small, switch to a designed single-column layout rather than leaving half the stage empty.
4. A normal content scene should use approximately **65–90% of the usable stage** for meaningful composition, while preserving deliberate breathing room.
5. No avoidable empty region should dominate roughly one-third or more of the stage.
6. For text-only scenes, use a purposeful composition such as:
   - oversized key number;
   - large statement plus supporting band;
   - asymmetric cards;
   - process ribbon;
   - decision matrix;
   - full-width scenario.
7. Empty space is acceptable only when it clearly strengthens the focal message.

A scene fails visual QA when it looks like content was placed on one side while a planned image or panel was simply omitted.

# 7. Visual Hierarchy and Micas UI

Use the successful preview direction: unified dark blue, Micas cyan, bold typography, large complete visuals, rounded blue-tinted cards, and strong spatial balance.

```css
:root {
  --micas-primary: #00899f;
  --micas-primary-bright: #29c5d8;
  --micas-primary-soft: #76e4ee;
  --micas-bg: #031f2b;
  --micas-bg-deep: #021720;
  --micas-surface: #0a3140;
  --micas-surface-raised: #123f4f;
  --micas-surface-glass: rgba(18, 63, 79, .72);
  --micas-border: rgba(118, 228, 238, .22);
  --micas-text: #f5fbfd;
  --micas-text-muted: #b7d4dc;
  --micas-success: #43d6a0;
  --micas-warning: #ffbf47;
  --micas-danger: #ff5d68;
  --micas-radius-lg: 24px;
  --micas-radius-md: 16px;
  --micas-shadow: 0 18px 60px rgba(0, 0, 0, .28);
  --header-h: clamp(68px, 8vh, 88px);
  --footer-h: clamp(78px, 9vh, 96px);
}
```

## One Dominant Element

Every scene must contain one visually dominant element:

- hero title;
- product image;
- annotated diagram;
- key number or limit;
- warning or decision;
- active installation step.

It should normally occupy roughly 40–65% of the usable stage or carry clearly greater typographic weight than support content.

## Typography

```css
.hero-title {
  font-size: clamp(56px, 6vw, 96px);
  line-height: .98;
  letter-spacing: -.045em;
  font-weight: 800;
}

.scene-title {
  font-size: clamp(40px, 4.2vw, 68px);
  line-height: 1.04;
  letter-spacing: -.035em;
  font-weight: 780;
}

.key-metric {
  font-size: clamp(52px, 5.5vw, 88px);
  line-height: 1;
  font-weight: 820;
}

.scene-subtitle { font-size: clamp(20px, 1.7vw, 28px); }
.card-title { font-size: clamp(20px, 1.6vw, 28px); }
.card-body { font-size: clamp(17px, 1.25vw, 22px); }
```

Chinese and Japanese may use slightly smaller maxima, but must retain obvious hierarchy.

# 8. Technical Image Integrity Contract

Technical visuals are teaching assets, not decorative backgrounds.

## Mandatory Rules

1. Product images, diagrams, screenshots, panel drawings, and installation figures must be fully visible by default.
2. Use `object-fit: contain`, never `cover`, for technical visuals.
3. Preserve aspect ratio, labels, arrows, and device boundaries.
4. Do not clip the top, bottom, or sides because a container has a fixed height.
5. Pre-crop source page margins, headers, footers, and irrelevant whitespace before embedding.
6. Allocate enough stage area for the image to be useful:
   - normal image/text scene: about 40–55% of stage;
   - image-led teaching scene: about 55–75%;
   - hardware identification: normally at least half the stage.
7. If a complete image cannot remain legible, create:
   - a full-view scene;
   - one or more explicit detail/zoom scenes.
8. An intentional detail crop must be clearly labeled as a zoom and paired with a complete view in the same or adjacent scene.
9. Never use a huge frame containing a tiny technical image with excessive unused space.

```css
.visual-frame {
  min-width: 0;
  min-height: 0;
  display: grid;
  place-items: center;
  overflow: hidden;
}

.visual-frame img,
.visual-frame svg,
.visual-frame canvas {
  display: block;
  width: 100%;
  height: 100%;
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
  object-position: center;
}
```

## Image Preflight

Run image checks only after every image has loaded/decoded.

Verify:

- `naturalWidth > 0` and `naturalHeight > 0`;
- rendered width and height are meaningful;
- the image element is fully inside the visible scene and viewport;
- no ancestor clips the technical image;
- computed `object-fit` is `contain`;
- the source asset does not contain excessive blank margins;
- labels remain readable at required viewports.

A missing, half-visible, or unintentionally cropped technical image is a **release-blocking defect**.

# 9. Navigation and Control Sizing

## Header

Contains:

- integrated transparent Micas logo;
- course/product title and compact scene subtitle;
- selected-language dropdown;
- Video mode;
- Fullscreen;
- only truly necessary utilities.

## Language Control

Show only the current language:

- `English`
- `简体中文`
- `繁體中文`
- `日本語`

Do not show a visible `Language` prefix. Keep `aria-label="Language"`.

## Footer

Recommended structure:

- left: Course Menu and scene counter;
- middle-left: prominent progress group;
- center: labeled Previous and Next buttons;
- right: narration and audio settings.

Desktop controls must feel substantial:

```css
.footer-control,
.nav-button {
  min-height: 58px;
  padding: 0 24px;
  border-radius: 18px;
  font-size: 18px;
  font-weight: 700;
  flex-shrink: 0;
}

.nav-button {
  min-width: 150px;
}

.icon-control {
  width: 58px;
  height: 58px;
  min-width: 58px;
  min-height: 58px;
  border-radius: 18px;
  flex-shrink: 0;
}

.progress-group {
  flex: 1 1 360px;
  min-width: 260px;
  max-width: 560px;
}

.progress-track {
  height: clamp(9px, .9vh, 13px);
  border-radius: 999px;
}
```

Rules:

1. Desktop Previous/Next buttons use text labels plus arrows; do not default to tiny arrow-only squares.
2. Icon-only Previous/Next is allowed only in compact/mobile mode.
3. Course Menu, narration, and settings controls must not shrink below the defined minimums.
4. At 1600–1920 px, target a 340–520 px progress bar. At 1366 px, target at least 240–320 px where practical.
5. All controls remain visible and easy to hit.

# 10. Narration and Google-First Voice Policy

The normal footer uses a compact speaker/play icon. Detailed controls live in a popover.

## Default Selection

For each supported locale, prefer an exact-locale Google voice as the default whenever the browser exposes one:

- `en-US`: fragments such as `Google US English`, `Google English`;
- `zh-CN`: fragments such as `Google 普通话`, `Google Mandarin`, `Google 中文`;
- `zh-TW`: fragments such as `Google 國語`, `Google Chinese (Taiwan)`, `Google 中文（台灣）`;
- `ja-JP`: fragments such as `Google 日本語`, `Google Japanese`.

Voice priority:

1. exact-locale Google voice;
2. exact-language Google voice;
3. exact-locale Microsoft Natural/Neural voice;
4. exact-locale Apple voice;
5. best exact-locale fallback.

The curated list shows no more than three voices. A Google voice must be included and placed first whenever the browser exposes a matching Google voice.

```js
function scoreVoice(voice, locale) {
  const name = (voice.name || '').toLowerCase();
  const lang = (voice.lang || '').toLowerCase();
  const target = locale.toLowerCase();
  const exactLocale = lang === target;
  const exactLanguage = lang.split('-')[0] === target.split('-')[0];
  if (!exactLanguage) return -10000;

  let score = exactLocale ? 300 : 120;
  if (name.includes('google')) score += exactLocale ? 600 : 450;
  if (/natural|neural|premium|enhanced/.test(name)) score += 180;
  if (name.includes('microsoft')) score += 90;
  if (/apple|samantha|ava|tingting|kyoko|otoya|mei-jia/.test(name)) score += 60;
  if (/espeak|festival|mbrola|compact|legacy|robot|desktop/.test(name)) score -= 800;
  return score;
}
```

Browser/OS voice inventories cannot be guaranteed by an offline HTML file. Never fabricate unavailable voices. If Google is unavailable, select the best fallback and record the limitation in the README and QA Report.

# 11. Assessment Transition Scene

Before the final assessment, insert a dedicated transition scene that clearly separates learning from testing.

It must include:

- confirmation that the instructional section is complete;
- assessment purpose;
- number of questions;
- approximate duration;
- passing score or scoring method when applicable;
- how answers and feedback work;
- a clear `Start Assessment` button;
- a calm, encouraging readiness message.

Video/Auto mode must pause on this scene and wait for the learner to start the assessment.

Do not place the first final-exam question immediately after the last teaching scene.

# 12. Presentation Hygiene

Do not display in normal learner scenes:

- source mapping or raw page references;
- narration transcript accordions;
- authoring notes;
- QA flags;
- overflow notices;
- generation metadata;
- debug controls;
- missing-asset placeholders.

Keep source references in data and reports. Keep narration in localized data and optional captions.

# 13. Four-Language Standard

Support:

| Locale | Display label | TTS target |
|---|---|---|
| `en` | English | `en-US` |
| `zh-CN` | 简体中文 | `zh-CN` |
| `zh-TW` | 繁體中文 | `zh-TW` |
| `ja` | 日本語 | `ja-JP` |

Rules:

1. English is the default and visual master.
2. Localize titles, body content, narration, questions, choices, feedback, module names, assessment transition, and completion messages.
3. Preserve technical names, commands, standards, and port labels where translation reduces accuracy.
4. Author independent language versions; do not rely on runtime machine translation.
5. Other locales may use layout variants without degrading the English design.
6. Every locale must pass fit, image, control, and accessibility QA.

# 14. HTML Implementation Requirements

The default artifact is one self-contained HTML application with no external CDN or runtime asset dependency.

Required features:

- fixed-height `100dvh` shell;
- no vertical browser scrolling in normal scenes;
- English-first visual master and four authored languages;
- hidden course drawer from the bottom-left;
- selected-language-only dropdown;
- large labeled desktop Previous/Next buttons;
- prominent progress bar;
- Fullscreen and Video mode;
- icon narration and audio settings;
- Google-first voice selection when available;
- quizzes and immediate explanatory feedback;
- dedicated assessment-introduction scene;
- final score and completion;
- `localStorage` persistence;
- optional captions;
- accessible controls, focus states, alt text, Escape behavior, and reduced-motion support;
- no visible debug or QA UI;
- no missing or clipped embedded assets.

# 15. Mandatory Pre-Delivery QA

## Automated Fit QA

For every scene, viewport, and locale:

- wait for fonts and all images;
- render the scene;
- verify `scene.scrollHeight <= scene.clientHeight + 1`;
- verify `document.documentElement.scrollHeight <= window.innerHeight + 1`;
- verify header and footer remain visible;
- verify no horizontal clipping;
- verify no diagnostic badge exists in learner mode.

## Visual QA

Review rendered screenshots at 1920×1080, 1600×900, and 1366×768.

Confirm:

- one obvious focal point;
- meaningful hierarchy;
- no accidental half-empty composition;
- no empty placeholder panel;
- no repetitive flat grid across most scenes;
- technical images are complete and large enough;
- no image is half-visible or unintentionally cropped;
- controls are substantial and consistent;
- English is visually strongest;
- other locales remain readable and complete;
- assessment transition exists;
- no debug, overflow, or review message is visible.

## Release-Blocking Defects

Do not deliver when any of these occurs:

- visible `Layout overflow detected` or similar diagnostic;
- scene or page overflow;
- missing or half-visible technical image;
- large accidental empty region or blank column;
- tiny/shrunken primary controls;
- first exam question appears without an assessment-introduction scene;
- English layout was weakened to force identical multilingual density;
- source mapping, transcript, or QA metadata is visible in learner mode;
- required offline asset is missing.

# 16. Required Deliverables

Create and attach:

1. `[COURSE_NAME]_Interactive_Training.html`
2. `[COURSE_NAME]_Course_Map.md`
3. `[COURSE_NAME]_QA_Report.md`
4. `[COURSE_NAME]_README.md`

The QA Report must include:

- technical values checked;
- warnings preserved;
- source inconsistencies;
- English-master and multilingual completeness;
- viewport-fit results;
- image-integrity results;
- stage-utilization review;
- control-size review;
- Google voice availability and fallback status;
- assessment-transition verification;
- offline, functional, and accessibility tests.

# Completion Standard

The result must feel like a premium Micas technical course suitable for self-study, instructor-led presentation, fullscreen/video playback, and field reference.

Do not stop at an outline or prototype when the user requests a complete course. Generate the complete artifacts, run the mandatory preflight and visual QA, correct every release-blocking defect, and only then deliver.