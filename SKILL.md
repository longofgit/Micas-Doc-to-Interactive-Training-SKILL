---
name: micas-doc-to-interactive-training
display_name: Micas Doc-to- Interactive-Training Skill
description: Convert manuals, SOPs, product guides, policies, and technical documents into source-grounded, Micas-branded, self-contained interactive training courses with PPT-like viewport scenes, polished UI, four-language support, curated narration, quizzes, progress tracking, hidden course navigation, and offline delivery.
version: 2.1.0
---

# Micas Doc-to- Interactive-Training Skill

## Purpose

Transform static technical documents into an engaging, accurate, reusable interactive course—not a page-by-page summary, document viewer, or narrated slide dump.

The default deliverable is a **single self-contained offline HTML course** that opens in modern Chrome or Edge without a server. It combines instructional design, authentic source visuals, multilingual content, narration, interactions, assessment, progress tracking, and a polished Micas visual system.

The learner experience must behave like a presentation deck:

- one scene occupies one browser viewport;
- the main scene never requires vertical scrolling;
- learners move with Previous/Next or keyboard arrows;
- long content is divided into additional scenes instead of extending the page.

## Default Project Settings

Unless the user explicitly overrides them, use these defaults:

- **Brand:** Micas Networks
- **Primary brand color:** `#00899F`
- **Visual direction:** dark, premium, technical, spacious, mission-oriented
- **Default language:** English
- **Supported languages:** English, Simplified Chinese, Traditional Chinese, Japanese
- **Locale keys:** `en`, `zh-CN`, `zh-TW`, `ja`
- **Output:** one offline HTML file plus course map, QA report, and README
- **Scene behavior:** PPT-like, one viewport per scene, no normal-page vertical scrolling
- **Navigation:** complete course directory hidden by default in an overlay drawer; trigger located in the bottom-left control rail
- **Narration:** browser Web Speech API with automatic high-quality voice selection and a compact icon-only control in the bottom-right
- **Tone:** professional, practical, engaging, not childish

When inputs are incomplete, infer reasonable values from the source and continue without unnecessary clarification. Record assumptions in the QA report.

## Non-Negotiable Source-Grounding Rules

1. Treat supplied source files as the primary and authoritative basis.
2. Read complete relevant sections, including tables, figures, captions, warnings, procedures, appendices, screenshots, and embedded images.
3. Preserve terminology, product names, numerical values, safety limits, procedural order, and operational boundaries.
4. Do not silently invent, correct, reconcile, or supplement missing technical facts.
5. If source passages conflict, flag the inconsistency instead of silently choosing one.
6. Distinguish source-derived content from instructional wording, inference, or external research.
7. Represent safety-critical steps, electrical limits, laser safety, ESD controls, lifting rules, and restricted maintenance procedures accurately and prominently.
8. Do not turn dangerous operations into playful interactions that reduce perceived risk.
9. Maintain traceability: every scene, question, and answer must map to a source page, heading, table, or figure.
10. Keep traceability metadata out of the normal presentation UI; store it in course data, Course Map, and QA Report.

## Production Workflow

### Phase 1 — Source Audit

Read and inspect the full source material, including embedded visuals. Build an internal source map containing:

- document hierarchy and table of contents;
- intended audience and prerequisites;
- key concepts and specifications;
- procedures and exact sequence;
- safety warnings and prohibited actions;
- reusable visual assets;
- troubleshooting symptoms, checks, and resolutions;
- repeated or low-value reference content;
- ambiguities, contradictions, and suspected source errors.

Do not build a complete course from isolated snippets when the surrounding chapter is relevant.

### Phase 2 — Learning Architecture

Convert the document hierarchy into a learning journey. Do not create one scene per source page.

Use this hierarchy:

- **Course:** complete learning goal
- **Module:** one coherent competence area
- **Scene:** one focused learning objective, normally 30–90 seconds of narration
- **Interaction:** identification, decision, sequencing, matching, or diagnosis
- **Assessment:** module checks plus final challenge

Recommended technical-course pattern:

1. Course orientation and outcomes
2. Product positioning and hardware anatomy
3. Interfaces, indicators, power, airflow, and key specifications
4. Safety and site preparation
5. Unpacking and installation readiness
6. Installation and connection workflow
7. Commissioning and verification
8. Monitoring and maintenance
9. Troubleshooting scenarios
10. Final assessment and completion

Adapt the pattern to the source instead of forcing irrelevant sections.

### Phase 3 — Content Prioritization

Classify content as:

- **Must perform:** procedures, checks, limits, and safety actions
- **Must recognize:** ports, LEDs, modules, labels, symptoms, and states
- **Must understand:** architecture, airflow, redundancy, dependencies, and rationale
- **Reference only:** exhaustive pin tables, dimensions, regulations, or rarely used appendices

Actively teach the first three. Put reference-only content in dedicated paged reference scenes or a separate searchable reference overlay; do not narrate every row.

### Phase 4 — Scene Design

Each scene should usually contain:

- mission or context label;
- one clear title;
- one short explanation or learning objective;
- three to five key points maximum;
- one authentic source image, diagram, simplified visual, or interaction when useful;
- dedicated narration written for listening;
- optional checkpoint;
- prominent warning block when supported by the source.

Use varied layouts:

- premium hero/cover scene;
- image plus explanation;
- hardware hotspot map;
- front/rear panel identification;
- step-by-step timeline;
- do/do-not comparison;
- specification chips or cards;
- troubleshooting decision path;
- scenario question;
- final score and completion screen.

Avoid dense document-like pages. Split complex procedures and long quizzes into multiple scenes.

## PPT-Like Viewport Contract

The normal learner scene is a fixed presentation stage, not a scrolling webpage.

### Required Layout Model

Use a viewport shell similar to:

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

.scene-stage {
  min-height: 0;
  overflow: hidden;
}

.scene {
  height: 100%;
  min-height: 0;
  overflow: hidden;
}
```

Requirements:

1. Header, scene stage, and footer together must fit inside `100dvh`.
2. The body and normal scene stage must use `overflow: hidden`, not `overflow-y: auto`.
3. No normal scene may require the browser page to scroll vertically.
4. Previous/Next, progress, Course Menu, and narration controls remain visible without scrolling.
5. Content must fit at common presentation viewports, including at least:
   - 1920 × 1080;
   - 1600 × 900;
   - 1366 × 768.
6. Browser zoom at 100% is the QA baseline.
7. Use responsive scene variants for narrower screens rather than permitting vertical page scroll.
8. On very small mobile screens, preserve one-scene navigation. Use compact layouts, tabs, or paged sub-scenes; do not create a long vertical article.

### Content Budget

Treat each scene as a slide with a finite content budget:

- title: preferably 1–2 lines, maximum 3 short lines;
- subtitle: maximum 2 lines;
- key points: normally 3–5;
- cards: normally 3–4 large cards or 5–6 compact chips;
- quiz: one question per scene unless extremely short;
- warning: one focused warning block, not a full chapter of warnings;
- body copy: concise, presentation-ready, not document prose;
- tables: show only essential rows/columns, or divide into multiple scenes.

Do not solve overflow by shrinking text below readable sizes. If content does not fit, split it into more scenes.

### Overflow Validation

After rendering every language at each QA viewport, verify:

```js
const fits = scene.scrollHeight <= scene.clientHeight + 1;
```

Also verify the document itself does not scroll:

```js
const pageFits = document.documentElement.scrollHeight <= window.innerHeight + 1;
```

A scene fails QA if any required locale overflows. Correct it by:

1. reducing nonessential wording;
2. changing the layout;
3. moving details into another scene;
4. creating a follow-up reference scene;
5. never by hiding important content or making text unreadably small.

The Course Menu drawer, audio settings popover, and optional review/instructor panels may have their own internal scroll when open. The normal presentation scene may not.

## Micas UI Design Standard

The UI must follow the successful preview style: unified dark-blue environment, large high-impact title, carefully framed product imagery, restrained cyan accents, rounded translucent cards, and strong spatial balance.

### Required Design Tokens

```css
:root {
  --micas-primary: #00899f;
  --micas-primary-bright: #29c5d8;
  --micas-primary-soft: #76e4ee;
  --micas-bg: #031f2b;
  --micas-bg-deep: #021720;
  --micas-surface: #0a3140;
  --micas-surface-raised: #123f4f;
  --micas-surface-glass: rgba(18, 63, 79, 0.72);
  --micas-border: rgba(118, 228, 238, 0.22);
  --micas-text: #f5fbfd;
  --micas-text-muted: #b7d4dc;
  --micas-success: #43d6a0;
  --micas-warning: #ffbf47;
  --micas-danger: #ff5d68;
  --micas-radius-lg: 24px;
  --micas-radius-md: 16px;
  --micas-shadow: 0 18px 60px rgba(0, 0, 0, 0.28);
  --header-h: clamp(64px, 8vh, 86px);
  --footer-h: clamp(64px, 8vh, 84px);
}
```

### Visual Composition Rules

1. Keep header, stage, footer, and controls within one coherent dark visual system.
2. Do not introduce a sudden full-width white main panel. White or near-white may appear only in controlled areas such as a product-image frame, chart canvas, printable reference, or focused modal.
3. Prefer dark or blue-tinted cards with subtle borders and glass-like depth.
4. Use large typography and generous spacing instead of filling the screen with small elements.
5. The first scene should normally use a two-column hero layout:
   - left: mission label, large title, brief promise, three learning-goal cards;
   - right: product or process visual in a rounded framed panel with concise specification chips.
6. Keep animations restrained: short fades, slide-ins, progress changes, hotspot pulses, and subtle hover elevation.
7. Maintain high contrast and clear focus states.
8. Avoid decorative emoji as primary UI icons in formal courses; use consistent inline SVG icons where possible.

### Logo Integration Rules

1. Use a transparent-background Micas logo or a version designed for dark backgrounds.
2. Never place a white rectangular logo image directly on the dark header when it creates a visible block.
3. If only a white-background logo is available:
   - crop excess whitespace;
   - create a transparent version only when safe and without changing the mark;
   - otherwise place it inside a deliberately designed compact logo plaque.
4. Preserve aspect ratio; never stretch, recolor, or distort the logo.
5. Keep the logo visually integrated with the header, normally 34–56 px high.

## Navigation and Control Placement

The complete course directory is valuable, but it must not remain permanently visible.

### Course Menu

Required behavior:

- hide the directory by default on all screen sizes;
- place the **Course Menu trigger in the bottom-left control rail**, not in the top-left header;
- use a compact menu icon with a short label or localized tooltip;
- open the directory as an overlay drawer or modal sheet;
- the drawer may show modules, scene counts, completion state, search, and quick jump;
- close it by selecting a scene, pressing Escape, clicking the backdrop, or using a close button;
- in fullscreen and Video mode, keep it closed unless explicitly opened;
- do not reserve permanent horizontal space for it.

### Header

The header should contain only identity and high-level presentation controls:

- Micas logo;
- course/product title and compact scene subtitle;
- `Language` dropdown;
- Video mode;
- Fullscreen;
- optional compact search/settings icon when truly needed.

Do not place the Course Menu in the header.

### Footer / Control Rail

Recommended arrangement:

- **left:** Course Menu button, scene counter, progress;
- **center:** Previous and Next;
- **right:** compact narration icon and optional secondary audio settings popover.

Keep the footer compact and always visible.

## Presentation Hygiene

Normal learners and audiences should see only learning content and essential controls.

Do not display these elements inside normal scenes:

- `Source mapping` or `源内容映射` accordions;
- raw source page references;
- `Narration transcript` or `旁白文本` accordions;
- authoring notes;
- QA flags such as `source review required` unless the source issue itself must be disclosed to the learner;
- debug information;
- content-generation metadata.

Required handling:

- keep `sourceRefs` in the internal course data;
- include full mapping in `[COURSE_NAME]_Course_Map.md` and `[COURSE_NAME]_QA_Report.md`;
- keep narration text in localized data for TTS;
- provide optional captions/subtitles through an audio accessibility setting when needed, not as a large raw transcript block in every scene;
- if an instructor/reviewer mode is useful, hide it behind an explicit settings switch and keep it off by default;
- screenshots and presentation mode must never show review metadata by default.

## Four-Language Standard

Every course must support these locales unless explicitly overridden:

| Locale key | Language | TTS preference |
|---|---|---|
| `en` | English | `en-US` or best available English voice |
| `zh-CN` | 简体中文 | `zh-CN` |
| `zh-TW` | 繁體中文 | `zh-TW` |
| `ja` | 日本語 | `ja-JP` |

Rules:

1. English is always the default on first load.
2. The language control is a compact dropdown whose visible label remains **`Language`** in every locale.
3. Dropdown options are English, 简体中文, 繁體中文, 日本語.
4. Localize scene titles, body text, narration, questions, answer choices, feedback, module names, and completion messages.
5. Keep technical product names, commands, port labels, and standard identifiers unchanged where translation would reduce accuracy.
6. Store four independent authored language versions. Do not rely on runtime machine translation.
7. Persist the selected language, but use English when no preference exists.
8. Map narration to locale-specific voices and provide a graceful fallback.
9. Validate viewport fit independently for all four languages; Chinese and Japanese line wrapping must not create overflow.

Recommended data model:

```js
const courseData = {
  defaultLanguage: 'en',
  supportedLanguages: ['en', 'zh-CN', 'zh-TW', 'ja'],
  scenes: [
    {
      id: 'scene-01',
      moduleId: 'module-01',
      sourceRefs: ['p.1', 'Section 1.1'],
      content: {
        en: { title: '', body: '', narration: '', question: null },
        'zh-CN': { title: '', body: '', narration: '', question: null },
        'zh-TW': { title: '', body: '', narration: '', question: null },
        ja: { title: '', body: '', narration: '', question: null }
      }
    }
  ]
};
```

## Narration UI and Voice Quality Standard

### Default Narration Control

The normal footer must use a compact icon-only speaker button similar to the successful preview version.

- position: bottom-right;
- size: normally 44–52 px;
- icon states: play/speaker, playing, paused, muted or unavailable;
- no visible voice name such as `Samantha · en-US` in the normal footer;
- no large `Narrate` or `语音讲解` text button;
- include localized tooltip and accessible `aria-label`;
- one click starts/stops or pauses narration according to the current state;
- a secondary action, small chevron, long press, or settings icon opens audio settings.

### Audio Settings Popover

The detailed controls belong in a compact popover or modal opened from the narration icon. It may include:

- narration on/off;
- play/pause/replay;
- speed control, normally `0.85×` to `1.25×`;
- optional captions/subtitles;
- a short curated voice list;
- test voice button.

Do not permanently show the browser's complete voice inventory.

### Voice Curation

Browser voice availability differs by operating system. Build a scored shortlist and show **no more than three high-quality voices per active locale**. Auto-select the highest-scoring available voice.

Preferred high-quality name families, in approximate priority order:

- **English (`en-US`)**: Microsoft Aria Online (Natural), Microsoft Jenny Online (Natural), Microsoft Guy Online (Natural), Apple Ava, Apple Samantha, Google US English
- **Simplified Chinese (`zh-CN`)**: Microsoft Xiaoxiao Online (Natural), Microsoft Yunxi Online (Natural), Microsoft Xiaoyi Online (Natural), Google 普通话（中国大陆）, Apple Tingting
- **Traditional Chinese (`zh-TW`)**: Microsoft HsiaoChen Online (Natural), Microsoft YunJhe Online (Natural), Google 國語（臺灣）, Apple Mei-Jia
- **Japanese (`ja-JP`)**: Microsoft Nanami Online (Natural), Microsoft Keita Online (Natural), Google 日本語, Apple Kyoko, Apple Otoya

Names vary by browser and OS, so match case-insensitively by stable name fragments.

Recommended scoring:

```js
function scoreVoice(voice, locale, preferredFragments) {
  const name = voice.name.toLowerCase();
  const lang = (voice.lang || '').toLowerCase();
  const target = locale.toLowerCase();
  let score = 0;

  if (lang === target) score += 100;
  else if (lang.split('-')[0] === target.split('-')[0]) score += 35;
  else return -1000;

  const preferredIndex = preferredFragments.findIndex(
    part => name.includes(part.toLowerCase())
  );
  if (preferredIndex >= 0) score += 90 - preferredIndex * 8;

  if (/natural|neural|premium|enhanced/.test(name)) score += 35;
  if (/microsoft|google|apple/.test(name)) score += 12;
  if (voice.default) score += 5;

  if (/espeak|festival|mbrola|compact|legacy|robot|desktop/.test(name)) {
    score -= 120;
  }

  return score;
}
```

Filtering rules:

1. require exact locale where possible;
2. include only positive-scoring voices;
3. deduplicate near-identical names;
4. sort by score and show at most three;
5. do not show low-quality or mismatched voices merely to fill the list;
6. if no curated voice is available, auto-select the best exact-locale fallback and show at most one fallback option;
7. never list dozens of browser voices;
8. preserve the user's selected voice only while it remains valid for the active locale;
9. reassess voices after `voiceschanged` fires;
10. report platform-dependent limitations in the README and QA report.

## Visual Asset Treatment

Reuse authentic source figures whenever possible.

- Crop page margins and unrelated text.
- Preserve labels and aspect ratio.
- Add highlights, numbered markers, arrows, callouts, or zoom areas only when they improve learning.
- Do not alter product appearance or invent ports and components.
- Provide alt text in all supported languages when practical.
- Compress images to WebP or optimized PNG/JPEG.
- Embed assets as data URIs for single-file output.
- When source images are inadequate, create simple schematics rather than photorealistic invented equipment.

## Narration Content Standard

Write a dedicated narration script for every locale and scene.

- Explain meaning and action; do not read screen text verbatim.
- Use short natural spoken sentences.
- Expand abbreviations on first use when appropriate.
- Format numbers for clear TTS pronunciation.
- Keep one scene focused on one objective.
- Explain the reason behind critical steps when the source supports it.
- Never dilute warnings.
- Cancel speech immediately when the learner changes scenes or language.
- Keep narration text in data and optional captions; do not render a permanent transcript accordion.

## Interaction Standard

Use realistic interactions:

- identify a port, module, LED, or cable;
- choose the correct procedural sequence;
- diagnose a symptom;
- select the safest next action;
- match a status indication to its meaning;
- distinguish acceptable and unacceptable site conditions.

Every question must include:

- one unambiguous source-supported correct answer;
- plausible distractors;
- immediate explanatory feedback in all supported languages;
- source mapping in production data and reports.

Avoid trivia that does not improve field performance.

## HTML Implementation Requirements

The default artifact is a self-contained HTML application with no external CDN or network dependency.

Required features:

- fixed-height `100dvh` presentation shell;
- no vertical browser scrolling in normal scenes;
- responsive desktop, tablet, and mobile layouts;
- hidden course-directory drawer triggered from the bottom-left footer;
- compact `Language` dropdown with four languages;
- English default locale;
- current scene title, scene counter, and progress bar;
- Previous and Next controls;
- left/right keyboard navigation;
- Fullscreen mode;
- course search inside the hidden drawer or compact overlay;
- per-scene narration using Web Speech API;
- icon-only narration control in the bottom-right;
- curated high-quality voice selection inside a popover;
- automatic presentation/Video mode;
- immediate quiz feedback;
- final assessment and score;
- `localStorage` persistence for language, progress, audio settings, and relevant learning state;
- optional captions or equivalent screen content when speech is unavailable;
- accessible contrast, focus states, semantic controls, alt text, Escape behavior, and ARIA labels;
- no external CDNs, web fonts, scripts, or image URLs in the final offline file;
- no visible source mapping, raw narration transcript, QA metadata, or authoring notes in learner mode.

Recommended Video mode behavior:

- use minimum scene time plus narration-length estimate;
- pause at interactions requiring learner input;
- cancel current speech when scenes or locale change;
- keep navigation drawer and audio settings closed during playback;
- preserve the one-viewport scene contract.

## Responsive Behavior

- **Large screens:** hero or content stage uses the full width; no permanently docked sidebar.
- **Medium screens:** two-column scenes may collapse into compact balanced layouts that still fit the viewport.
- **Mobile:** header controls compress, cards may use tabs or paged sub-scenes, touch targets remain at least 44 px, and the course directory opens nearly full-screen.
- Prevent unintended horizontal and vertical page scrolling.
- Do not allow a long stacked mobile article; split it into scenes.

## Quality Assurance

Before delivery, verify:

### Source Accuracy

- Technical values match the source.
- No unsupported capabilities are introduced.
- Procedures preserve order.
- Warnings are present and prominent.
- Questions and feedback are source-supported.
- Source conflicts are flagged in the QA report.

### Viewport and Presentation

- Every scene fits at 1920×1080, 1600×900, and 1366×768 at 100% zoom.
- `document.documentElement.scrollHeight <= window.innerHeight + 1` in normal learner mode.
- Each active scene satisfies `scrollHeight <= clientHeight + 1` in every locale.
- Header and footer controls remain visible.
- No title or content is clipped horizontally.
- Long content is split rather than made scrollable or unreadably small.
- Previous/Next behaves like PPT slide navigation.

### UI and Brand

- Micas primary color is `#00899F`.
- Logo is visually integrated and has no accidental white box.
- Main stage has no abrupt oversized white area.
- Preview-style dark composition is maintained across all scenes.
- Cards, borders, chips, buttons, and progress indicators use a consistent token system.
- Course Menu is bottom-left, hidden by default, and opens as a drawer.
- Fullscreen and Video mode do not expose the drawer automatically.
- Source mapping and narration transcript are absent from normal learner scenes.
- Narration is an icon-only control in the bottom-right.

### Language

- First load is English.
- `Language` button label remains English.
- English, 简体中文, 繁體中文, and 日本語 are selectable.
- All scene content, narration, questions, feedback, and completion messages have four versions.
- Voice selection follows the active locale and falls back gracefully.
- Every locale passes viewport-fit checks.

### Voice and Audio

- The footer does not display a voice name or full voice dropdown.
- The audio popover shows no more than three curated voices per locale.
- Low-quality, legacy, mismatched, and duplicate voices are filtered.
- The highest-scoring available voice is auto-selected.
- Speech stops when changing scene or language.
- Audio settings close in Video mode.

### Functional Tests

- Previous/Next and keyboard navigation work.
- Progress persists after refresh.
- Drawer open/close and Escape behavior work.
- Language persists after refresh.
- Video mode pauses correctly for interactions.
- Search finds scenes in the current locale and preferably all locales.
- Quizzes score correctly.
- Fullscreen works where the browser permits.
- The final file opens offline with no missing assets.

### Accessibility

- Contrast is adequate.
- Focus states are visible.
- Controls have accessible names.
- Drawer and settings dialog trap focus while open and restore focus when closed.
- Dialogs and feedback are keyboard accessible.
- Images have alt text.
- Optional captions are available when appropriate.
- Reduced-motion preferences are respected.

## Required Deliverables

Create and attach:

1. `[COURSE_NAME]_Interactive_Training.html`
2. `[COURSE_NAME]_Course_Map.md`
3. `[COURSE_NAME]_QA_Report.md`
4. `[COURSE_NAME]_README.md`

The Course Map must list modules and scenes with learning objectives and source mapping. Source mapping belongs in this report, not in the normal presentation pages.

The QA Report must include:

- technical values checked;
- warnings preserved;
- four-language completeness;
- viewport-fit test results for required resolutions and all locales;
- UI/brand acceptance checks;
- voice curation and narration-control checks;
- functional tests completed;
- source inconsistencies or uncertain points;
- browser and TTS limitations.

## Completion Standard

The result must feel like a premium Micas interactive technical course suitable for:

- self-study;
- instructor-led classroom presentation;
- fullscreen/video-style playback;
- quick field reference.

Do not stop at an outline or prototype when the user asks for a complete course. Generate the complete artifacts and validate the presentation behavior before delivery.
