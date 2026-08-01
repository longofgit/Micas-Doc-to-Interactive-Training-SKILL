---
name: micas-doc-to-interactive-training
display_name: Micas Doc-to- Interactive-Training Skill
description: Convert manuals, SOPs, product guides, policies, and technical documents into source-grounded, Micas-branded, self-contained interactive training courses with PPT-like viewport scenes, strong visual hierarchy, four-language support, curated narration, quizzes, progress tracking, hidden course navigation, and offline delivery.
version: 2.2.0
---

# Micas Doc-to- Interactive-Training Skill

## Purpose

Transform static technical documents into a polished interactive course—not a page-by-page summary, document viewer, generic LMS, or narrated slide dump.

The default deliverable is a **single self-contained offline HTML course** that opens in modern Chrome or Edge without a server. It combines instructional design, authentic source visuals, multilingual content, narration, interactions, assessment, progress tracking, and a premium Micas visual system.

The learner experience must behave like a presentation deck:

- one scene occupies one browser viewport;
- normal scenes never require vertical page scrolling;
- learners move with Previous/Next or keyboard arrows;
- long material is divided into additional scenes;
- every scene has one obvious visual and instructional focal point.

## Default Project Settings

Unless explicitly overridden, use these defaults:

- **Brand:** Micas Networks
- **Primary brand color:** `#00899F`
- **Visual direction:** dark, premium, technical, spacious, mission-oriented
- **Default language:** English
- **Supported languages:** English, Simplified Chinese, Traditional Chinese, Japanese
- **Locale keys:** `en`, `zh-CN`, `zh-TW`, `ja`
- **Output:** one offline HTML file plus Course Map, QA Report, and README
- **Scene behavior:** PPT-like, one viewport per scene, no normal-page vertical scrolling
- **Navigation:** hidden course directory opened from the bottom-left control rail
- **Language control:** compact selected-language dropdown with no `Language` prefix
- **Narration:** Web Speech API with curated voices and an icon-only control in the bottom-right
- **Tone:** professional, practical, engaging, not childish

When inputs are incomplete, infer reasonable values from the source and record assumptions in the QA Report.

## Non-Negotiable Source-Grounding Rules

1. Treat supplied source files as the primary and authoritative basis.
2. Read complete relevant sections, including tables, figures, captions, warnings, procedures, appendices, screenshots, and embedded images.
3. Preserve terminology, product names, numerical values, safety limits, procedure order, and operational boundaries.
4. Do not silently invent, correct, reconcile, or supplement missing technical facts.
5. If source passages conflict, flag the inconsistency instead of silently choosing one.
6. Distinguish source-derived content from instructional wording, inference, or external research.
7. Represent safety-critical content accurately and prominently.
8. Do not turn dangerous operations into playful interactions that reduce perceived risk.
9. Maintain traceability from every scene and assessment item to a source page, heading, table, or figure.
10. Keep traceability metadata out of normal presentation pages; store it in course data, Course Map, and QA Report.

## Production Workflow

### Phase 1 — Source Audit

Inspect the full source and build an internal source map containing:

- document hierarchy;
- intended audience and prerequisites;
- key concepts and specifications;
- procedures and exact sequence;
- warnings and prohibited actions;
- reusable visual assets;
- troubleshooting symptoms and resolutions;
- low-value reference content;
- ambiguities and suspected source errors.

Do not build a course from isolated snippets when the surrounding section matters.

### Phase 2 — Learning Architecture

Convert the source hierarchy into a learning journey rather than one scene per source page.

Use this hierarchy:

- **Course:** complete learning goal
- **Module:** coherent competence area
- **Scene:** one focused learning objective, normally 30–90 seconds of narration
- **Interaction:** identification, decision, sequence, match, or diagnosis
- **Assessment:** module checks plus final challenge

Recommended technical-course pattern:

1. Orientation and outcomes
2. Product positioning and hardware anatomy
3. Interfaces, indicators, power, airflow, and key specifications
4. Safety and site preparation
5. Unpacking and installation readiness
6. Installation and connection workflow
7. Commissioning and verification
8. Monitoring and maintenance
9. Troubleshooting scenarios
10. Final assessment and completion

Adapt this pattern to the source.

### Phase 3 — Content Prioritization

Classify material as:

- **Must perform:** procedures, checks, limits, and safety actions
- **Must recognize:** ports, LEDs, modules, labels, symptoms, and states
- **Must understand:** architecture, airflow, redundancy, dependencies, and rationale
- **Reference only:** exhaustive tables, regulations, dimensions, or rarely used appendices

Actively teach the first three. Put reference-only material in paged reference scenes or a searchable overlay.

### Phase 4 — Message Hierarchy Before Layout

Before designing each scene, identify:

- `primaryMessage`: the single fact, decision, or action learners must remember;
- `supportingPoints`: normally two to four items that explain or support it;
- `referenceDetails`: material that can move to another scene or report;
- `focalVisual`: the image, diagram, number, warning, or action that deserves the most space.

A scene fails instructional design when all text blocks and cards appear equally important.

### Phase 5 — Scene Design

Each scene should usually contain:

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
- oversized key metric or decision;
- hardware hotspot map;
- front/rear panel identification;
- step timeline;
- do/do-not contrast;
- asymmetric specification composition;
- troubleshooting decision path;
- scenario question;
- final score and completion.

Do not use the same equal-card grid on every scene. Equal grids are appropriate only when the items genuinely have equal importance.

## PPT-Like Viewport Contract

The normal learner scene is a fixed presentation stage, not a scrolling webpage.

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
  min-height: 0;
  overflow: hidden;
}

.scene { height: 100%; }
```

Requirements:

1. Header, stage, and footer fit inside `100dvh`.
2. Body and normal scene stage use `overflow: hidden`.
3. No normal scene requires vertical browser scrolling.
4. Previous/Next, progress, Course Menu, and narration controls remain visible.
5. Validate at 100% zoom for 1920×1080, 1600×900, and 1366×768.
6. Validate all four languages independently.
7. Use responsive scene variants, tabs, or more scenes for small screens.
8. Never solve overflow by hiding required content or shrinking text below readable size.

### Content Budget

Treat each scene like a designed slide:

- title: preferably one or two lines;
- subtitle: no more than two lines;
- supporting points: normally two to five;
- cards: normally one dominant card plus two or three supporting cards;
- quiz: one question per scene;
- warning: one focused warning block;
- tables: essential rows only, or divide into more scenes.

Validate:

```js
const sceneFits = activeScene.scrollHeight <= activeScene.clientHeight + 1;
const pageFits = document.documentElement.scrollHeight <= window.innerHeight + 1;
```

A failed fit check is a production defect.

## Micas UI Design Standard

The UI must follow the successful preview style: unified dark-blue environment, bold typography, restrained cyan accents, carefully framed large imagery, rounded translucent cards, and strong spatial balance.

### Required Tokens

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
  --header-h: clamp(64px, 8vh, 86px);
  --footer-h: clamp(68px, 8.5vh, 90px);
}
```

## Visual Hierarchy Contract

Every scene must have a clearly visible hierarchy.

### One Dominant Element

Each scene must contain one element that visually dominates:

- a hero title;
- a product image;
- an annotated diagram;
- a key number or limit;
- a warning or decision;
- the active installation step.

The dominant element should normally occupy roughly **40–60% of the usable stage area** or carry substantially greater typographic weight than supporting content.

### Typography Scale

Use meaningful contrast, not one uniform size:

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

.scene-subtitle {
  font-size: clamp(20px, 1.7vw, 28px);
  line-height: 1.35;
}

.card-title { font-size: clamp(20px, 1.6vw, 28px); }
.card-body  { font-size: clamp(17px, 1.25vw, 22px); }
```

Chinese and Japanese may use slightly smaller maximum sizes when needed, but must retain obvious contrast between title, key message, and support text.

### Composition Rules

1. Prefer asymmetric `58/42`, `60/40`, or `55/45` compositions when a focal visual exists.
2. Use one primary card spanning more width or height than secondary cards.
3. Keep whitespace around the focal element.
4. Use chips only for concise metadata, not as the main teaching method.
5. Avoid rigid repeated 2×2 card grids unless the content is a true equal comparison.
6. Do not fill empty space with extra low-value text merely to balance the page.
7. A hero/cover scene should feel closer to a product launch slide than an LMS dashboard.

## Visual Asset and Image-Fit Contract

Authentic product and procedure visuals are primary teaching assets, not decoration.

### Required Behavior

- Technical product images, diagrams, screenshots, and figures must display **completely** by default.
- Use `object-fit: contain`, not `cover`, for technical visuals.
- Preserve aspect ratio and labels.
- Do not clip the top, bottom, or sides because a frame has fixed dimensions.
- Allocate enough stage area for the image to be useful; normally at least 38% of stage width in a two-column scene.
- When the image is the learning objective, allocate 50–70% of the stage.
- Crop page margins and irrelevant whitespace from the source asset before embedding.
- If one image still cannot be legible in the available viewport, create a full-image scene followed by annotated detail scenes.
- Intentional detail crops are allowed only when clearly designed as zoom views and when the learner has access to a complete view in the same or adjacent scene.

Recommended CSS:

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

`object-fit: cover` is permitted only for decorative backgrounds that contain no technical information.

## Logo Integration

- Use a transparent Micas logo suitable for a dark header.
- Never drop a white rectangular logo file directly onto the header.
- Preserve aspect ratio and clear space.
- Keep the logo normally 34–56 px high.

## Navigation and Controls

### Course Menu

- Hidden by default.
- Trigger placed in the bottom-left footer/control rail.
- Opens as an overlay drawer or modal sheet.
- Closes after selection, Escape, backdrop click, or close button.
- Must not reserve permanent horizontal space.

### Header

Contains only:

- Micas logo;
- course/product title and compact scene subtitle;
- selected-language dropdown;
- Video mode;
- Fullscreen;
- optional truly necessary compact utilities.

### Language Control

The compact dropdown displays **only the currently selected language name**:

- `English`
- `简体中文`
- `繁體中文`
- `日本語`

Do not display `Language`, `Language · English`, `Language: English`, or an equivalent prefix. Keep an accessible `aria-label="Language"` and tooltip if needed.

English is the first-load default. Persist the selected locale.

### Footer / Control Rail

Recommended arrangement:

- **left:** Course Menu and scene counter;
- **middle-left or center:** a prominent progress group;
- **center:** Previous and Next;
- **right:** icon-only narration and optional audio settings.

The progress bar must be visibly useful rather than a tiny decorative line:

```css
.progress-group {
  flex: 1 1 320px;
  min-width: 240px;
  max-width: 520px;
}

.progress-track {
  height: clamp(8px, .8vh, 12px);
  border-radius: 999px;
}
```

At 1600–1920 px width, target roughly 300–480 px of progress-bar width. At 1366 px, keep at least about 220–300 px where practical.

## Presentation Hygiene

Do not display in normal learner scenes:

- source mapping accordions or raw page references;
- narration transcript accordions;
- authoring notes;
- QA flags or debug information;
- generation metadata.

Store source references in course data and reports. Keep narration text in localized data and optional captions.

## Four-Language Standard

Support:

| Locale | Display label | TTS preference |
|---|---|---|
| `en` | English | `en-US` |
| `zh-CN` | 简体中文 | `zh-CN` |
| `zh-TW` | 繁體中文 | `zh-TW` |
| `ja` | 日本語 | `ja-JP` |

Rules:

1. English is the default.
2. The visible control shows only the selected display label.
3. Localize titles, body content, narration, questions, choices, feedback, module names, and completion messages.
4. Preserve technical names, commands, standards, and port labels where translation reduces accuracy.
5. Author independent language versions; do not rely on runtime machine translation.
6. Validate viewport fit and image composition in all four languages.

## Narration UI and Voice Quality

### Default Control

Use a compact icon-only speaker/play button in the bottom-right.

- normally 44–52 px;
- no visible voice name in the footer;
- no full voice dropdown in the footer;
- no large `Narrate` or `语音讲解` text button;
- localized tooltip and accessible label;
- secondary action opens audio settings.

### Voice Curation

Show no more than three high-quality voices for the active locale and auto-select the highest-scoring available voice.

Preferred families:

- `en-US`: Microsoft Aria/Jenny/Guy Natural, Apple Ava/Samantha, Google US English
- `zh-CN`: Microsoft Xiaoxiao/Yunxi/Xiaoyi Natural, Google 普通话（中国大陆）, Apple Tingting
- `zh-TW`: Microsoft HsiaoChen/YunJhe Natural, Google 國語（臺灣）, Apple Mei-Jia
- `ja-JP`: Microsoft Nanami/Keita Natural, Google 日本語, Apple Kyoko/Otoya

Reward exact locale, preferred names, and Natural/Neural/Premium/Enhanced voices. Filter or heavily penalize `eSpeak`, `Festival`, `MBROLA`, `Compact`, `Legacy`, `Robot`, and `Desktop`. Deduplicate similar voices. If no curated voice exists, expose at most one exact-locale fallback.

## Narration Content

Write a dedicated natural script for every locale and scene.

- Explain rather than read the screen verbatim.
- Use short spoken sentences.
- Explain why critical steps matter when supported by the source.
- Format numbers and abbreviations for TTS.
- Cancel speech on scene or language change.
- Keep narration in data and optional captions, not a permanent transcript block.

## Interaction Standard

Use realistic interactions:

- identify a port, module, LED, or cable;
- order a procedure;
- diagnose a symptom;
- choose the safest next action;
- match an indicator with its meaning.

Every question needs one source-supported answer, plausible distractors, immediate explanatory feedback, and internal source mapping.

## HTML Implementation Requirements

The self-contained offline HTML must include:

- fixed-height `100dvh` presentation shell;
- no vertical browser scrolling in normal scenes;
- responsive desktop, tablet, and mobile scene variants;
- bottom-left hidden Course Menu drawer trigger;
- selected-language-only dropdown;
- English default and four authored locales;
- larger visible progress bar;
- Previous/Next and keyboard arrows;
- Fullscreen and Video mode;
- course search in drawer or overlay;
- icon-only narration control;
- curated voices in an audio popover;
- immediate quiz feedback and final score;
- `localStorage` for language, progress, and audio settings;
- accessible contrast, focus states, alt text, Escape behavior, and ARIA labels;
- embedded CSS, JavaScript, images, and course data;
- no external CDN, font, script, or image dependency;
- no learner-visible source mapping, transcript, QA metadata, or authoring notes.

## Responsive Behavior

- Large screens use strong asymmetric layouts and large focal visuals.
- Medium screens preserve hierarchy; they must not flatten everything into equal cards.
- Mobile uses compact variants, tabs, or extra scenes rather than a long article.
- Prevent unintended horizontal and vertical page scrolling.
- Keep touch targets at least 44×44 px.

## Quality Assurance

### Source Accuracy

- Technical values and procedures match the source.
- Warnings remain prominent.
- No unsupported capabilities are introduced.
- Source conflicts are flagged in the QA Report.

### Viewport Fit

- Every scene fits at 1920×1080, 1600×900, and 1366×768 at 100% zoom.
- Page and scene fit checks pass in all four locales.
- Header/footer remain visible.
- No title, image, or content is clipped.
- Long content is split rather than scrolled or made unreadably small.

### Visual Hierarchy

- Every scene has one obvious dominant element.
- Hero and key scenes use meaningfully larger titles or focal visuals.
- Supporting cards are visibly secondary.
- The course does not repeat a flat equal-card grid on most pages.
- Critical limits, actions, and warnings are visually emphasized.
- Whitespace and asymmetry feel intentional.

### Image QA

- Technical images use `object-fit: contain` or equivalent complete-fit behavior.
- No meaningful image content is clipped.
- Images are large enough to teach from, not merely decorate.
- Source page margins and irrelevant whitespace are cropped before embedding.
- Detail crops have a complete-view counterpart.
- Image frames pass visual inspection at every required viewport.

### Controls and Brand

- Micas primary color is `#00899F`.
- Logo integrates without an accidental white rectangle.
- Main stage has no dominant plain-white panel.
- Course Menu is bottom-left and hidden by default.
- Language control shows only the selected language name.
- Progress bar meets the larger width and thickness guidance.
- Narration remains an icon-only bottom-right control.

### Voice and Audio

- No footer voice name or full voice dropdown.
- No more than three curated voices per locale.
- Low-quality and duplicate voices are filtered.
- Speech stops on scene/language change.

### Functional and Accessibility Tests

- Previous/Next, keyboard navigation, Fullscreen, Video mode, quizzes, scoring, persistence, drawer, and search work.
- Controls have accessible names and visible focus.
- Drawers/dialogs trap and restore focus.
- Images have alt text.
- Reduced-motion preferences are respected.

## Required Deliverables

1. `[COURSE_NAME]_Interactive_Training.html`
2. `[COURSE_NAME]_Course_Map.md`
3. `[COURSE_NAME]_QA_Report.md`
4. `[COURSE_NAME]_README.md`

The QA Report must include source checks, viewport results for every locale, visual-hierarchy review, image-fit review, brand/control acceptance, voice curation, functional tests, source uncertainties, and browser/TTS limitations.

## Completion Standard

The result must feel like a premium Micas technical presentation suitable for self-study, instructor-led delivery, fullscreen/video playback, and quick field reference.

Do not stop at an outline or prototype when a complete course is requested.