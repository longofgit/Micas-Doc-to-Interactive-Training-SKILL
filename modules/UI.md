# Unified UI System

Version: **3.1.1**

This is the single UI and visual implementation contract for all training modes. Brand-specific tokens and references come from the selected brand pack.

# 1. Visual System Interface

The selected brand pack must provide these semantic tokens:

```css
:root {
  --brand-primary: #00899f;
  --brand-primary-bright: #29c5d8;
  --brand-primary-soft: #76e4ee;
  --stage-bg: #031f2b;
  --stage-bg-deep: #021720;
  --surface: #0a3140;
  --surface-raised: #123f4f;
  --surface-glass: rgba(18, 63, 79, .72);
  --border: rgba(118, 228, 238, .22);
  --text: #f5fbfd;
  --text-muted: #b7d4dc;
  --success: #43d6a0;
  --warning: #ffbf47;
  --danger: #ff5d68;
  --radius-lg: 24px;
  --radius-md: 16px;
  --shadow: 0 18px 60px rgba(0, 0, 0, .28);
}
```

Do not hard-code a different company's identity into the shared UI module. The Micas values above are the default fallback only.

# 2. Presentation Shell

The default interactive experience behaves like a presentation deck, not a scrolling article.

```css
html,
body {
  width: 100%;
  height: 100%;
  margin: 0;
  overflow: hidden;
  background: var(--stage-bg);
  color: var(--text);
}

.course-shell {
  width: 100%;
  height: 100dvh;
  min-height: 100vh;
  display: grid;
  grid-template-rows: var(--header-h, clamp(68px, 8vh, 92px)) minmax(0, 1fr) var(--footer-h, clamp(78px, 9vh, 100px));
  overflow: hidden;
  background: var(--stage-bg);
}

.scene-stage,
.scene {
  min-width: 0;
  min-height: 0;
  overflow: hidden;
  background: var(--stage-bg);
}

.scene { height: 100%; }
```

Normal audience-facing pages must not require vertical browser scrolling. Internal scrolling is allowed only inside intentionally opened drawers, search panels, settings panels, overlays, reference panels, or reviewer tools.

# 3. Dark Stage and Localized Light Surfaces

The selected brand pack controls the stage theme. For the default Micas pack, the entire shell, stage, and scene remain deep navy.

Light colors may appear only inside bounded components such as:

- technical-image frames;
- metric tiles;
- selected data cards;
- controlled tables or comparison surfaces.

Do not convert the complete content area into a pale, white, light-gray, or light-grid page unless the selected brand pack explicitly defines that theme.

# 4. English-First Layout

English is the default visual master.

- Establish the strongest English composition, title scale, line breaks, image size, and spacing first.
- Other locales may use shorter authored wording, different line breaks, adjusted column ratios, responsive variants, or additional semantic scenes.
- Do not flatten the English design to force identical multilingual density.
- Every locale must still pass fit, image, control, and accessibility QA.

# 5. Visual Hierarchy

Every page must have one dominant element:

- hero statement;
- product image;
- annotated diagram;
- key number;
- warning;
- decision;
- current action;
- chart or evidence block appropriate to the selected mode.

The dominant element should normally occupy about 40–65% of the usable stage or carry clearly greater visual weight than supporting material.

Preferred compositions include:

- 58/42 or 60/40 hero split;
- large technical image plus concise explanation;
- one dominant card plus two or three supporting cards;
- oversized metric plus evidence band;
- full-width process ribbon;
- scenario prompt plus decision area;
- hardware image with hotspots;
- full-stage transition or assessment introduction.

Avoid repetitive equal-sized grids as the default solution.

# 6. Learner-Facing Typography

Desktop typography:

```css
:root {
  --body-primary: clamp(24px, 1.65vw, 31px);
  --body-secondary: clamp(22px, 1.4vw, 27px);
  --body-compact: clamp(20px, 1.15vw, 23px);
}

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

.scene-lead,
.hero-description,
.question-text,
.explanation-text {
  font-size: var(--body-primary);
  line-height: 1.42;
}

.card-body,
.step-body,
.answer-option,
.supporting-copy,
.bullet-item,
.warning-body,
.procedure-copy {
  font-size: var(--body-secondary);
  line-height: 1.42;
}

.caption,
.instructional-label,
.technical-note {
  font-size: var(--body-compact);
  line-height: 1.35;
}
```

Rules:

- At 1366×768, ordinary instructional body text must not fall below `20px`.
- Important explanations, answer options, steps, bullets, and card body copy should normally be `22px` or larger.
- Only true non-instructional metadata may be smaller.
- Do not shrink useful content to solve overflow. Shorten, redesign, or split the page.
- Tablet body text should normally remain at least `18px`; phone body text at least `17px`.

# 7. Content Budget and Stage Utilization

Treat every page like a designed slide:

- title: preferably one or two lines;
- subtitle: no more than two lines;
- supporting points: normally two to five;
- cards: normally one dominant card plus two or three supporting cards;
- question: one primary question per page;
- warning: one focused warning block;
- large tables: essential rows only or split into additional pages.

Do not render empty visual frames, blank columns, placeholder cards, or unused panels.

Use a two-column layout only when both columns contain meaningful content. Meaningful composition should normally occupy about 65–90% of the usable stage. An avoidable empty area of roughly one-third or more fails visual QA.

# 8. Overflow and Reviewer Mode

The production UI must never display:

- `Layout overflow detected`;
- fit or overflow warnings;
- QA banners;
- source-review notices;
- debug badges;
- authoring diagnostics;
- missing-asset placeholders.

Reviewer diagnostics may exist only behind an explicit internal flag such as:

```js
const REVIEW_MODE = false;
```

If a page does not fit:

1. remove nonessential wording;
2. redesign the composition;
3. move secondary details to another page;
4. split the page;
5. rerender and retest.

Do not deliver an overflowing page or announce overflow to the audience.

# 9. Technical Image Integrity

Technical images are instructional assets, not decorative backgrounds.

Required behavior:

- fully visible by default;
- `object-fit: contain`;
- preserved aspect ratio;
- complete device boundaries, labels, arrows, and callouts;
- no top, bottom, or side clipping;
- source page margins, headers, footers, and irrelevant whitespace cropped before embedding;
- large enough to teach from.

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

Recommended allocation:

- normal image/text page: 40–55% of stage;
- image-led page: 55–75%;
- hardware identification: at least half the stage.

If a complete image is not legible, use a full-view page followed by labeled detail pages. Never solve the problem by showing only half of the image.

# 10. Header

The header contains:

- selected brand logo and lockup;
- course or artifact title;
- compact contextual subtitle;
- selected language;
- Auto Play/Video control when supported by the selected mode;
- Fullscreen when applicable;
- only necessary utilities.

Brand-specific logo sizing, title treatment, and visual references come from the selected brand pack.

The visible language selector shows only the selected language value. Do not add a visible `Language` prefix. Keep an accessible name such as `aria-label="Language"`.

Header utility controls use appropriate inline SVG icons:

- language: globe, language, or translation icon;
- Auto Play/Video: play or video-camera icon;
- Fullscreen: four-corner icon.

Normal desktop icon size is about `20–24px`.

# 11. Footer and Control Rail

For the default interactive-training mode, the footer uses:

- **left group:** Course Menu, scene count, module/scene progress;
- **right group:** Previous → Next → Search → narration → Audio settings.

The selected mode may remove controls that are not relevant, but it may not silently reorder controls defined by its own mode contract.

Desktop control sizing:

```css
.footer-control,
.nav-button {
  min-height: 58px;
  padding: 0 24px;
  border-radius: 18px;
  font-size: 18px;
  font-weight: 700;
  flex: 0 0 auto;
}

.nav-button { min-width: 150px; }

.icon-control {
  width: 58px;
  height: 58px;
  min-width: 58px;
  min-height: 58px;
  border-radius: 18px;
  padding: 0;
  line-height: 0;
  flex: 0 0 auto;
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

Desktop Previous/Next use text labels plus arrows. Tiny arrow-only controls are allowed only at compact breakpoints.

Search is icon-only with no visible text and appears immediately after Next in the default mode.

# 12. Icon Centering

All header and footer icons must be geometrically and optically centered.

```css
.header-control,
.footer-control,
.icon-control,
.nav-button,
.course-menu-button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  box-sizing: border-box;
}

.control-content {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  line-height: 1;
}

.header-control svg,
.footer-control svg,
.icon-control svg,
.nav-button svg,
.course-menu-button svg {
  display: block;
  width: 1em;
  height: 1em;
  flex: 0 0 auto;
  transform: none;
}
```

Do not use arbitrary top/left offsets, negative margins, or baseline nudges to position icons. SVG viewBoxes must not contain excessive invisible whitespace.

# 13. Search UI

When the selected mode enables full-content search:

- open results in an overlay, modal sheet, or drawer;
- keep the underlying page fixed;
- group results logically;
- show a short localized snippet;
- navigate only after the user selects a result;
- close with Escape and support keyboard navigation;
- use an embedded offline index;
- allow internal scrolling inside the search panel only.

# 14. Responsive Priority

Priority order:

1. desktop presentation quality;
2. tablet usability;
3. phone usability.

Desktop master viewports:

- 1920×1080;
- 1600×900;
- 1366×768.

Representative responsive checks:

- tablet landscape: 1180×820 or 1024×768;
- tablet portrait: 820×1180 or 768×1024;
- phone portrait: 430×932 and 390×844.

Tablet and phone may use stacked columns, compact headers, icon-only secondary controls, shorter contextual subtitles, alternate line breaks, and additional page splitting. Do not weaken the desktop design merely to force one identical layout across devices.

# 15. Accessibility and Interaction

- Provide keyboard-accessible controls and visible focus states.
- Use accessible names for icon-only controls.
- Use meaningful alt text for instructional images.
- Support Escape to close overlays.
- Respect reduced-motion preferences.
- Maintain adequate contrast.
- Keep touch targets large enough on tablet and phone.
- Do not rely on color alone to convey state.

# 16. Presentation Hygiene

Normal audience-facing pages must not show:

- source mapping;
- narration transcript accordions;
- raw page references;
- QA labels;
- debug information;
- generation metadata;
- missing-asset placeholders.

# 17. Brand Reference Assets

Visual reference assets must be colocated with the selected brand pack. The UI module may inspect those references for proportion, hierarchy, spacing, and component treatment, but must recreate the design with live HTML/CSS, localizable text, the selected brand logo, and authentic source visuals.

Do not use a full-page reference screenshot as the flattened production page.

# 18. Default Micas Interactive-Training Regression Lock

This section is a narrow compatibility lock for `brand_profile: micas` with `training_mode: interactive-training`. It restores the previously approved presentation shell without changing training logic.

## 18.1 Header Lockup

On desktop, the left header area must render:

- the official Micas logo;
- one large, bold primary course title;
- one visibly smaller contextual subtitle below it.

The subtitle is mandatory in normal desktop mode. It may identify the product/platform and current lesson or module context. It must remain factual and concise. Do not collapse the two-line lockup into a single title line unless a compact tablet/phone breakpoint requires it.

## 18.2 Right Header Utility Group

On desktop, the right header area contains exactly this primary sequence:

```text
Language → Auto Play → Fullscreen
```

Requirements:

- Language includes a centered globe/language icon, current-language label, and dropdown indicator;
- Auto Play includes a centered play icon and visible `Auto Play` label;
- Fullscreen includes a centered four-corner icon and visible `Fullscreen` label;
- do not remove Auto Play or Fullscreen;
- do not replace these controls with scene progress, module progress, question count, or assessment count;
- progress information belongs in the footer;
- use the selected brand reference asset when available.

## 18.3 Fixed Footer Contract

The fixed desktop footer uses the following composition:

```text
LEFT: Course Menu → Scene count → Module/scene progress bar
RIGHT: Previous → Next → Search → Narration → Audio settings
```

Requirements:

- Course Menu remains a substantial text-and-icon button;
- scene count and progress stay visible and readable;
- Previous and Next remain substantial text-and-arrow buttons;
- Search remains icon-only and immediately follows Next;
- Narration and Audio settings follow Search;
- the footer must not shrink into a thin strip of tiny icon buttons;
- the footer must be part of the grid layout, not overlaid on top of scene content;
- if `position: fixed` is used, reserve an equal content inset so no content is hidden behind it.

## 18.4 Non-Fullscreen Fit Contract

Every page must be designed and tested in a normal browser viewport, not only in Fullscreen.

Required layout behavior:

```css
.course-shell,
.scene-stage,
.scene,
.scene-inner,
.scene-grid,
.scene-column,
.visual-frame {
  box-sizing: border-box;
  min-width: 0;
  min-height: 0;
}

.scene-inner {
  width: 100%;
  height: 100%;
  max-height: 100%;
  overflow: hidden;
}

.scene-grid {
  width: 100%;
  height: 100%;
  display: grid;
  grid-template-columns: minmax(0, 1fr) minmax(0, 1fr);
  align-items: stretch;
}
```

Rules:

- compute scene height from the actual remaining grid row between header and footer;
- do not use fixed pixel scene heights copied from Fullscreen dimensions;
- do not let cards, images, result panels, captions, or source previews extend behind the footer;
- image and text columns must use `minmax(0, 1fr)` or an intentional ratio with both columns shrink-safe;
- every technical image remains complete with `object-fit: contain`;
- long content must be shortened, redesigned, or split into another scene;
- `overflow: hidden` must never be used to conceal unreviewed learning content;
- test every scene at 1920×1080, 1600×900, and 1366×768 at 100% zoom before release;
- Fullscreen may improve scale but must not be required to reveal missing content.

## 18.5 Controlled Semantic Highlighting

Important content may receive restrained color emphasis:

- brand cyan for required actions, product identifiers, key values, and main conclusions;
- warning amber for exceptions, limitations, and conditions;
- success green for verified correct states;
- danger red only for genuine hazards or prohibited actions.

Use emphasis to guide attention, not decorate the page. Do not color every line, use multiple competing highlight colors, or reduce contrast. A highlighted phrase must still be understandable without color alone.
