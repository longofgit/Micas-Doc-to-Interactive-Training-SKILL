# Master Prompt — Micas Doc-to- Interactive-Training

Attach the source documents, then use this prompt and replace bracketed variables where needed.

---

You are an instructional designer, technical trainer, UX designer, multilingual content engineer, and front-end developer.

Transform the attached source documents into a complete, source-grounded, premium Micas interactive training course.

## Project Settings

- Course title: `[AUTO-GENERATE OR ENTER TITLE]`
- Target audience: `[AUDIENCE]`
- Learning goal: `[LEARNING GOAL]`
- Desired duration: `[E.G. 30–45 MINUTES]`
- Assessment level: `[BASIC / INTERMEDIATE / CERTIFICATION-STYLE]`
- Output: `[DEFAULT: ONE SELF-CONTAINED OFFLINE HTML FILE]`
- Brand: `Micas Networks`
- Primary brand color: `#00899F`
- Default language: `English`
- Required languages: `English / 简体中文 / 繁體中文 / 日本語`
- Tone: `Professional, practical, engaging, not childish`

## Source and Accuracy Rules

1. Use the attached files as the primary and authoritative basis.
2. Read complete relevant material, including tables, figures, screenshots, warnings, procedures, appendices, and embedded images.
3. Preserve exact terminology, product names, numerical limits, procedure order, warnings, and operational boundaries.
4. Do not silently add unsupported claims or correct suspected source errors.
5. Flag ambiguity or inconsistency in the QA Report.
6. Maintain source mapping from every scene and assessment item to a source section, page, table, or figure.
7. Keep source mapping in course data, Course Map, and QA Report—not in normal presentation pages.
8. Preserve the seriousness and exact action of safety-critical content.

## Learning Architecture

Do not convert the source page by page. Reorganize it into a coherent learning journey.

Create:

- welcome and learning outcomes;
- competency-based modules;
- focused scenes, each teaching one primary objective;
- authentic visual explanations using source figures;
- step-by-step procedures;
- realistic troubleshooting and safety decisions;
- short module checks;
- final assessment with explanatory feedback;
- completion scene and review guidance.

Prioritize what learners must perform, recognize, and understand. Keep reference-only detail searchable or in dedicated reference scenes.

## Mandatory Message Hierarchy

Before laying out each scene, identify:

- `primaryMessage`: the one fact, action, or decision learners must remember;
- `supportingPoints`: normally two to four concise points;
- `referenceDetails`: material moved to another scene/report;
- `focalVisual`: the image, key number, warning, or active step deserving the most space.

Every scene must have one visually dominant element. Do not make all cards, paragraphs, and titles look equally important.

## Mandatory PPT-Like Viewport Behavior

The final course behaves like a presentation deck, not a scrolling webpage.

1. One scene occupies one complete browser viewport.
2. Header, stage, and footer fit within `100dvh`.
3. Body and normal scene stage use `overflow: hidden`.
4. No normal learner scene requires vertical scrolling.
5. Previous/Next, progress, Course Menu, and narration remain visible.
6. Long content is divided into additional scenes.
7. Do not solve overflow by making text unreadably small.
8. Validate at 100% zoom for 1920×1080, 1600×900, and 1366×768.
9. Validate English, Simplified Chinese, Traditional Chinese, and Japanese separately.
10. Mobile uses compact alternate layouts, tabs, or additional scenes—not a long stacked article.

Recommended shell:

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
```

Programmatically verify:

```js
const sceneFits = activeScene.scrollHeight <= activeScene.clientHeight + 1;
const pageFits = document.documentElement.scrollHeight <= window.innerHeight + 1;
```

A failed fit check is a production defect. Split or redesign the scene.

## Mandatory UI Direction

Use a unified preview-style Micas design:

- dark navy full-page environment;
- Micas cyan `#00899F` as the primary accent;
- large high-impact typography where content is important;
- one dominant focal element per scene;
- large authentic images in carefully designed frames;
- rounded dark/blue translucent cards;
- coherent header, stage, and footer;
- restrained professional animation;
- PPT-like one-screen composition.

Do not create a generic LMS appearance.

### Visual Hierarchy

Use meaningful scale contrast:

```css
.hero-title {
  font-size: clamp(56px, 6vw, 96px);
  line-height: .98;
  font-weight: 800;
}

.scene-title {
  font-size: clamp(40px, 4.2vw, 68px);
  line-height: 1.04;
  font-weight: 780;
}

.key-metric {
  font-size: clamp(52px, 5.5vw, 88px);
  line-height: 1;
  font-weight: 820;
}
```

Rules:

- use one dominant title, image, key value, warning, or active step;
- prefer asymmetric `58/42`, `60/40`, or `55/45` layouts;
- use one primary card larger than secondary cards;
- use equal card grids only for genuinely equal comparisons;
- do not repeat flat 2×2 grids across most scenes;
- keep intentional whitespace around important content;
- hero scenes should feel like premium product-launch slides.

### Forbidden UI Outcomes

- vertically scrolling normal scene;
- flat scenes where everything has similar visual weight;
- repetitive equal-card grids on most pages;
- white rectangular logo on the dark header;
- dominant plain-white main content block;
- permanently visible course directory;
- Course Menu in the top-left header;
- language control containing a `Language` prefix;
- full voice dropdown or voice name permanently visible in the footer;
- large `Narrate` / `语音讲解` button;
- learner-visible Source mapping / 源内容映射;
- learner-visible Narration transcript / 旁白文本;
- cropped or half-visible technical images;
- tiny images floating in large unused frames;
- generic blue replacing `#00899F`.

## Header and Language Control

Header contains:

- transparent Micas logo;
- course/product title and compact subtitle;
- selected-language dropdown;
- Video mode;
- Fullscreen.

The language dropdown displays only:

- `English`
- `简体中文`
- `繁體中文`
- `日本語`

Do not display `Language`, `Language · English`, or `Language: English`. Keep `aria-label="Language"` for accessibility. English is the first-load default.

## Course Directory

- Hide the full directory by default.
- Place Course Menu in the bottom-left footer/control rail.
- Open it as an overlay drawer/modal.
- Include modules, scene count, progress, search, and quick jump.
- Close after selection, Escape, backdrop click, or close button.
- Keep closed during normal teaching, Fullscreen, and Video mode unless explicitly opened.

## Footer and Progress

Recommended footer:

- left: Course Menu and scene counter;
- middle-left/center: prominent progress group;
- center: Previous and Next;
- right: icon-only narration control and optional settings.

Use a larger progress indicator:

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

Target approximately 300–480 px width at 1600–1920 px and 220–300 px at 1366 px where practical.

## Technical Image Requirements

Technical images are primary instructional content.

1. Display product images, diagrams, screenshots, and installation figures completely by default.
2. Use `object-fit: contain`, never `cover`, for technical visuals.
3. Preserve aspect ratio, labels, and boundaries.
4. Do not clip the top, bottom, or sides because a frame is too small.
5. Allocate at least about 38–45% of stage width in a two-column technical scene.
6. Allocate 50–70% of the stage when the image itself is the learning objective.
7. Crop page margins and irrelevant whitespace before embedding.
8. If an image cannot remain legible, create a full-image scene followed by annotated detail scenes.
9. Intentional zoom crops require a complete-view counterpart in the same or adjacent scene.

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

`object-fit: cover` is permitted only for decorative backgrounds containing no technical information.

## Four-Language Requirements

Support:

- `en` — English
- `zh-CN` — 简体中文
- `zh-TW` — 繁體中文
- `ja` — 日本語

Rules:

1. English is the first-load default.
2. The visible dropdown shows only the selected language name.
3. Localize scene titles, body content, narration, module names, questions, answers, feedback, captions, and completion messages.
4. Preserve product names, commands, standards, and port labels where translation reduces accuracy.
5. Author independent language content; do not rely on runtime machine translation.
6. Persist locale choice.
7. Use `en-US`, `zh-CN`, `zh-TW`, and `ja-JP` narration preferences.
8. Run viewport and image-composition QA for every locale.

## Narration UI and Voice Quality

- Use a compact icon-only speaker/play button in the bottom-right.
- Do not show a voice name or complete voice dropdown in the footer.
- Do not use a large `Narrate`/`语音讲解` text button.
- Open detailed settings in a small popover.
- Show no more than three curated voices for the active locale.
- Auto-select the highest-scoring exact-locale voice.
- Prefer Microsoft Natural, Google, and Apple high-quality families.
- Filter or heavily penalize `eSpeak`, `Festival`, `MBROLA`, `Compact`, `Legacy`, `Robot`, and `Desktop`.
- If no curated voice is available, expose at most one exact-locale fallback.

Keep narration text in localized data and optional captions, not a permanent transcript block.

## Interaction Requirements

Include realistic work decisions such as hardware identification, procedure ordering, safest-next-action choices, symptom diagnosis, and LED/status matching.

Each question must have one source-supported answer, plausible distractors, immediate explanatory feedback, and internal source mapping. Use one question per scene where possible.

## Technical Requirements

Generate one self-contained HTML file with embedded CSS, JavaScript, images, and course data. Do not rely on external CDNs, web fonts, scripts, or image URLs.

Include:

- `100dvh` PPT-like shell;
- no vertical scrolling in normal scenes;
- responsive scene variants;
- hidden Course Menu triggered bottom-left;
- selected-language-only dropdown;
- English default and four authored languages;
- larger progress bar;
- Previous/Next and keyboard navigation;
- Fullscreen and Video mode;
- search in drawer or compact overlay;
- Web Speech narration;
- icon-only narration control;
- curated voices in an audio popover;
- speech cancellation on navigation/language change;
- quizzes, score, and passing threshold;
- `localStorage` for progress, language, and audio settings;
- accessible controls, focus states, contrast, alt text, Escape behavior, and reduced-motion support;
- no learner-visible mapping, transcript, QA, debug, or authoring metadata.

## Required Deliverables

Create and attach:

1. `[COURSE_NAME]_Interactive_Training.html`
2. `[COURSE_NAME]_Course_Map.md`
3. `[COURSE_NAME]_QA_Report.md`
4. `[COURSE_NAME]_README.md`

The QA Report must verify:

- source accuracy and warnings;
- one-screen fit at all required viewports and locales;
- strong visual hierarchy and one focal point per scene;
- hero/key typography scale;
- avoidance of repetitive flat card grids;
- complete, large, uncropped technical images;
- `object-fit: contain` for technical figures;
- larger progress dimensions;
- selected-language-only control;
- `#00899F` primary color and integrated logo;
- bottom-left hidden Course Menu;
- bottom-right icon-only narration;
- curated voice quality;
- offline completeness;
- functional and accessibility tests.

Do not stop at an outline or prototype. Generate the complete artifacts and validate them before delivery.

---