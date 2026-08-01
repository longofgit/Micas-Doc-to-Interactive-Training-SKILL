# Micas Interactive Training UI Design Specification

Version: **2.1.0**

This file is the visual and interaction implementation contract for courses generated with the **Micas Doc-to- Interactive-Training Skill**.

## 1. Design Goal

Match the successful preview experience:

- one coherent dark-blue stage;
- Micas cyan as the primary accent;
- large, confident titles;
- product imagery framed intentionally;
- rounded, low-contrast glass or blue-tinted cards;
- clear PPT-like progress and presentation controls;
- no permanently visible course directory;
- no abrupt oversized white content panel;
- no vertical scrolling inside normal learner scenes.

The interface should feel like a premium technical product launch and field-engineer mission console—not an LMS template, document reader, or long webpage.

## 2. Brand Tokens

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
  --footer-h: clamp(64px, 8vh, 84px);
}
```

Do not substitute a generic bright blue for `#00899F`.

## 3. PPT-Like Viewport Shell

The course is a slide-stage application. The normal learner view must occupy exactly one browser viewport and must not scroll vertically.

Recommended shell:

```css
html,
body {
  width: 100%;
  height: 100%;
  margin: 0;
  overflow: hidden;
  background: var(--micas-bg-deep);
}

.course-shell {
  width: 100%;
  height: 100dvh;
  min-height: 100vh;
  display: grid;
  grid-template-rows: var(--header-h) minmax(0, 1fr) var(--footer-h);
  overflow: hidden;
}

.course-header,
.scene-stage,
.control-rail {
  min-width: 0;
}

.scene-stage {
  min-height: 0;
  overflow: hidden;
}

.scene {
  width: 100%;
  height: 100%;
  min-width: 0;
  min-height: 0;
  overflow: hidden;
}
```

### Required Behavior

- Header, active scene, and footer fit within `100dvh`.
- The browser body does not gain a vertical scrollbar.
- The active scene does not gain a vertical scrollbar.
- Previous/Next and utility controls remain visible at all times.
- Learners move between scenes like PPT slides.
- Long content is split into additional scenes.
- Do not hide essential content below the fold.
- Do not reduce fonts below readable presentation sizes to force a fit.

### Required QA Viewports

Validate at 100% browser zoom:

- 1920 × 1080;
- 1600 × 900;
- 1366 × 768.

All four locales must pass. Chinese and Japanese line wrapping must be tested separately.

### Programmatic Fit Check

```js
function sceneFits(scene) {
  return scene.scrollHeight <= scene.clientHeight + 1;
}

function pageFits() {
  return document.documentElement.scrollHeight <= window.innerHeight + 1;
}
```

If a scene fails, revise or divide it. Do not ship with overflow.

### Content Budget

- Hero title: preferably 1–2 lines; no more than 3 short lines.
- Scene title: preferably 1–2 lines.
- Subtitle: no more than 2 lines.
- Main points: usually 3–5.
- Large cards: usually 3–4.
- Compact chips: usually 3–6.
- Quiz: one question per scene where possible.
- Table: essential rows only; divide long tables into paged reference scenes.
- Warning: one focused warning block per scene unless the layout clearly supports more.

## 4. Page Shell

### Header

- Dark integrated background; height normally 64–86 px.
- Left: transparent Micas logo, course/product title, compact scene subtitle.
- Right: `Language` dropdown, Video mode, Fullscreen, and only genuinely necessary compact controls.
- Utility controls should be visually secondary.
- The `Language` button text remains English in every locale.
- **Do not place Course Menu in the header.**

### Content Stage

- Uses the full available width because the directory is not docked.
- Maintains the dark background across the stage.
- May use blue-tinted surfaces, transparent cards, gradients, framed images, and compact light canvases.
- Never put the entire main area inside a plain white rectangle.
- Must fit without vertical scrolling.

### Footer / Control Rail

The footer is always visible and compact.

Recommended layout:

- left: Course Menu, scene counter, and progress;
- center: Previous and Next;
- right: compact icon-only narration control.

The footer must not display a full voice selector or long voice name.

## 5. Hidden Course Directory

- Default state: closed.
- Trigger location: **bottom-left footer/control rail**.
- Trigger appearance: compact menu icon plus short label, or icon with clear tooltip on narrow screens.
- Presentation: left overlay drawer on desktop, nearly full-screen sheet on mobile.
- Contents: module list, scene list/counts, progress, search, and quick jump.
- Drawer closes after selecting a scene.
- Escape, backdrop click, and close button must work.
- Use focus trapping while open.
- It must not automatically open in Video mode or Fullscreen.
- It may internally scroll when needed; the normal learner scene may not.

## 6. Preferred Scene Layouts

### Hero Scene

- Two-column split around 52/48 or 50/50.
- Left: small mission label, 2–4 line large title, short promise, three outcome cards.
- Right: framed product/process image with 3–5 chips.
- Background remains dark.
- If the translated title becomes too long, create a language-aware compact variant or divide the phrase—not page overflow.

### Hardware Identification

- Large authentic equipment image.
- Numbered hotspots with accessible labels.
- Side or bottom detail cards appear on selection.
- Avoid shrinking the image to accommodate a permanent sidebar.
- Keep hotspot detail inside the viewport using an overlay, swap panel, or modal.

### Procedure

- Horizontal or compact vertical step timeline.
- One active step at a time.
- Safety gate before hazardous steps.
- Use diagrams or photographs where available.
- Divide long procedures into multiple scenes.

### Specification

- Use grouped chips and cards, not a copied full table unless the table is the learning objective.
- Divide exhaustive details into multiple reference scenes or a searchable reference overlay.
- Do not create a tall scrolling table in the main stage.

### Troubleshooting

- Symptom card → evidence → learner decision → guided next check.
- Use dark cards with accent borders.
- Feedback explains why, not merely correct/incorrect.
- One decision point per scene is preferred.

### Quiz

- One question per scene where possible.
- Large touch-friendly choices.
- Immediate localized feedback.
- If feedback cannot fit, transition to a dedicated answer/explanation scene.
- Keep warning scenarios serious.

## 7. Logo Handling

Preferred order:

1. Transparent SVG or PNG designed for dark backgrounds
2. Transparent standard Micas logo with sufficient contrast
3. Carefully cropped logo inside a compact designed plaque

Forbidden:

- stretched logo;
- white rectangular image dropped directly into dark header;
- unapproved recoloring;
- cropping that removes any part of the mark.

## 8. Language Control

The compact control must look like:

`Language ▾`

Dropdown entries:

- English
- 简体中文
- 繁體中文
- 日本語

English is the default. The button label stays `Language`; do not translate it to 中文, 語言, or 言語.

## 9. Narration Control

### Normal Footer Appearance

Use an icon-only speaker/play control in the bottom-right, matching the successful preview style.

Requirements:

- 44–52 px compact button;
- speaker/play icon, with playing/paused/muted states;
- no visible voice name in the footer;
- no full select element in the footer;
- no large text label such as `Narrate` or `语音讲解`;
- localized tooltip and accessible `aria-label`;
- one click starts/stops or pauses narration;
- a small secondary affordance opens detailed audio settings.

### Audio Settings Popover

Detailed audio controls belong in a popover or modal, not the permanent footer.

Allowed settings:

- narration on/off;
- play/pause/replay;
- speed from roughly `0.85×` to `1.25×`;
- optional captions/subtitles;
- voice test;
- curated voice selection.

The settings surface may internally scroll on very small screens.

### Curated Voice List

Show no more than three high-quality voices for the active locale. Auto-select the highest-scoring available voice.

Preferred voice families:

| Locale | Preferred names, approximate priority |
|---|---|
| `en-US` | Microsoft Aria Online (Natural), Microsoft Jenny Online (Natural), Microsoft Guy Online (Natural), Apple Ava, Apple Samantha, Google US English |
| `zh-CN` | Microsoft Xiaoxiao Online (Natural), Microsoft Yunxi Online (Natural), Microsoft Xiaoyi Online (Natural), Google 普通话（中国大陆）, Apple Tingting |
| `zh-TW` | Microsoft HsiaoChen Online (Natural), Microsoft YunJhe Online (Natural), Google 國語（臺灣）, Apple Mei-Jia |
| `ja-JP` | Microsoft Nanami Online (Natural), Microsoft Keita Online (Natural), Google 日本語, Apple Kyoko, Apple Otoya |

Filter out or heavily penalize names containing:

`eSpeak`, `Festival`, `MBROLA`, `Compact`, `Legacy`, `Robot`, or `Desktop`.

Do not show dozens of voices. Do not show language-mismatched voices. If no preferred voice exists, choose one best exact-locale fallback and show at most that single fallback.

## 10. Presentation Hygiene

Normal teaching pages must not expose authoring or QA metadata.

Do not show:

- `Source mapping` / `源内容映射`;
- raw page/section references;
- `Narration transcript` / `旁白文本` accordions;
- generation notes;
- debug output;
- internal QA warnings;
- `source review required` labels unless the actual learning content requires a learner-visible warning.

Instead:

- keep source references in internal scene data;
- publish mapping in Course Map and QA Report;
- keep narration text in the course data for TTS;
- offer optional captions/subtitles from audio settings when needed;
- hide any instructor/reviewer mode behind settings and keep it off by default.

A presentation screenshot must look like a polished course slide, not a content-authoring workspace.

## 11. Color Use

- `#00899F`: primary actions, active state, progress, highlights
- Deep navy: page background
- Blue-tinted surfaces: cards and controls
- Near-white: text and small controlled canvases
- Red/orange/yellow: only for source-supported warning states
- Green: success/completion

A white image frame is acceptable when it deliberately showcases a product image. A large white body area is not.

## 12. Typography

Use a robust system-font stack to preserve offline behavior:

```css
font-family: Inter, ui-sans-serif, system-ui, -apple-system,
  BlinkMacSystemFont, "Segoe UI", "Noto Sans", "Noto Sans SC",
  "Noto Sans TC", "Noto Sans JP", Arial, sans-serif;
```

Do not load external web fonts in a self-contained offline course.

Recommended scale:

- Hero title: `clamp(38px, 4.6vw, 76px)`
- Scene title: `clamp(30px, 3vw, 54px)`
- Body: `clamp(16px, 1.3vw, 22px)`
- Labels/chips: `13–16px`

Never shrink core body text below 15–16 px on desktop merely to avoid overflow. Split the scene instead.

## 13. Motion

Allowed:

- 150–300 ms fades and transforms;
- subtle card elevation;
- progress animation;
- hotspot pulse;
- drawer slide;
- compact audio-state animation.

Avoid:

- continuous decorative motion;
- excessive bouncing;
- rapid flashing;
- motion that competes with narration.

Respect `prefers-reduced-motion`.

## 14. Responsive Rules

- At wide sizes, retain strong two-column composition.
- Around 900–1200 px, reduce gaps, card counts, and title scale while preserving the viewport fit.
- On 1366×768, use the compact desktop layout; do not switch to a tall stacked page.
- On narrow tablets/mobile, use alternate compositions, tabs, carousels, accordions in modals, or additional scenes.
- Do not turn the course into a long stacked article on mobile.
- Drawer becomes nearly full-screen on mobile.
- Minimum touch target: 44 × 44 px.
- No unintended horizontal or vertical page scrolling.

## 15. UI Acceptance Checklist

A course fails UI QA when any of the following is true:

- The browser page or active learner scene requires vertical scrolling.
- Content or controls are clipped at 1920×1080, 1600×900, or 1366×768.
- Overflow is solved by unreadably small text.
- The header logo appears inside an accidental white rectangle.
- The main scene contains a dominant plain-white block unrelated to an image/table need.
- The course directory remains permanently docked during normal teaching.
- The Course Menu trigger appears in the top-left header instead of bottom-left footer.
- The brand primary is not `#00899F`.
- English is not the first-load language.
- The language control is a large toggle or its button label is translated.
- Any required locale is missing.
- The dark visual system is inconsistent between header, body, and footer.
- A full voice selector or voice name is permanently visible in the footer.
- More than three voice choices appear for the active locale.
- Low-quality or language-mismatched voices are shown.
- `Source mapping`, raw source references, `Narration transcript`, or `旁白文本` appear in normal learner scenes.
- The bottom-right narration control is a large text button instead of a compact icon.
