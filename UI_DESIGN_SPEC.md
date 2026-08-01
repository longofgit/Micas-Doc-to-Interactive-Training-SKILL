# Micas Interactive Training UI Design Specification

Version: **2.2.0**

This is the mandatory visual implementation contract for courses generated with the **Micas Doc-to- Interactive-Training Skill**.

## 1. Design Goal

Match the successful preview experience:

- one coherent dark-blue stage;
- Micas cyan as the primary accent;
- large, confident titles where the content deserves emphasis;
- one obvious focal element per scene;
- large, complete, useful product and procedure visuals;
- rounded, low-contrast glass or blue-tinted cards;
- clear PPT-like navigation and progress;
- no permanently visible course directory;
- no vertical scrolling in normal scenes;
- no abrupt oversized white content panel.

The interface should feel like a premium technical product launch and field-engineer mission console, not a generic LMS dashboard or document reader.

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
  --footer-h: clamp(68px, 8.5vh, 90px);
}
```

Do not substitute a generic bright blue for `#00899F`.

## 3. Viewport Shell

One scene must fit one viewport.

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

Normal scenes may not scroll vertically. Split content into more scenes instead.

## 4. Page Shell

### Header

- Dark integrated background.
- Left: transparent Micas logo, course/product title, compact scene subtitle.
- Right: selected-language dropdown, Video mode, Fullscreen.
- The language control shows only the selected language name.
- Do not put Course Menu in the header.

### Content Stage

- Uses the full width because navigation is not docked.
- Maintains the dark visual environment.
- Uses asymmetry, large typography, meaningful whitespace, and large visuals.
- Never place the entire stage inside a plain white rectangle.

### Footer / Control Rail

- Bottom-left: Course Menu and scene counter.
- Middle-left or center: larger progress group.
- Center: Previous and Next.
- Bottom-right: compact narration icon and optional settings icon/popover.
- Remains visible at all times.

## 5. Visual Hierarchy Contract

### One Scene, One Focal Point

Every scene must have one clearly dominant element:

- hero title;
- product image;
- annotated diagram;
- key specification or limit;
- warning or decision;
- active installation step;
- quiz question.

The focal element should normally occupy about 40–60% of the usable stage or have substantially greater typographic weight than support content.

A scene fails when all cards, paragraphs, and labels look equally important.

### Semantic Content Levels

Design from these levels:

1. **Primary message** — what must be remembered.
2. **Supporting evidence** — two to four concise points.
3. **Reference details** — move to another scene, drawer, Course Map, or QA report.

Do not render all three levels with the same font size, card size, or visual weight.

### Typography Scale

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

Chinese and Japanese may reduce the maximum slightly, but the hierarchy must remain obvious.

### Composition Rules

- Prefer `58/42`, `60/40`, or `55/45` split layouts when a focal visual exists.
- Use one dominant card or visual and smaller secondary cards.
- Use whitespace as part of the hierarchy.
- Avoid repeating equal-size 2×2 grids across many scenes.
- Equal grids are reserved for genuinely equal comparisons or checklists.
- Do not fill empty space with low-value text.
- Do not make all scene titles the same conservative size merely for implementation convenience.

## 6. Preferred Scene Layouts

### Hero / Course Opening

- Two-column split around `55/45` or `52/48`.
- Left: mission label, very large title, brief promise, three outcome cards.
- Right: large product/process image with concise chips.
- The title and image are dominant; cards are supporting.

### Key Specification

- Lead with one oversized value or statement.
- Place secondary values in smaller cards or chips.
- Do not turn every specification into an equal card.

### Hardware Identification

- Large complete equipment image.
- Numbered hotspots with accessible labels.
- Details appear in a compact side/bottom panel after selection.
- The equipment image should occupy at least half the stage when identification is the learning goal.

### Procedure

- One active step receives the largest space and strongest contrast.
- Completed/upcoming steps remain smaller.
- Use one or two large source visuals rather than several tiny images.

### Troubleshooting

- Symptom → evidence → learner decision → next check.
- The current decision or symptom is visually dominant.
- Feedback explains why.

### Quiz

- One question per scene where possible.
- Question title is large.
- Choices are touch-friendly but visually secondary.

## 7. Technical Image Contract

Technical images are teaching content, not decoration.

### Complete Display by Default

- Product photos, diagrams, screenshots, flowcharts, and installation figures must display completely.
- Use `object-fit: contain`, not `cover`.
- Preserve aspect ratio, labels, and boundaries.
- Never clip the top or bottom because a frame height is too small.
- Never hide part of a procedure figure inside `overflow: hidden` without an intentional zoom design.

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

`object-fit: cover` is allowed only for decorative backgrounds containing no technical information.

### Image Size Allocation

- Two-column technical scene: image normally receives at least 38–45% of stage width.
- Image-led scene: image receives 50–70% of stage.
- Hardware identification: image should be large enough for ports, labels, or modules to be distinguished.
- Avoid a large empty frame with a small centered image.

### Source Asset Preparation

Before embedding:

- crop page margins, headers, footers, and unrelated whitespace;
- preserve the complete figure itself;
- optimize the image without making labels unreadable;
- choose a crop aligned to the teaching objective;
- create separate full-view and zoom/detail scenes when needed.

Intentional detail crops are allowed only when the complete image is available in the same or adjacent scene.

## 8. Logo Handling

Preferred order:

1. Transparent SVG/PNG for dark backgrounds
2. Transparent standard Micas logo with sufficient contrast
3. Carefully cropped logo inside a deliberate compact plaque

Forbidden:

- stretched logo;
- accidental white rectangle in the dark header;
- unapproved recoloring;
- cropping part of the mark.

## 9. Course Directory

- Hidden by default.
- Trigger placed in the bottom-left footer.
- Opens as an overlay drawer on desktop and near-full-screen sheet on mobile.
- Includes modules, scene counts, progress, search, and quick jump.
- Closes after selection, Escape, backdrop click, or close button.
- Must not open automatically in Video mode or Fullscreen.

## 10. Language Control

The compact control displays only the selected language:

- `English`
- `简体中文`
- `繁體中文`
- `日本語`

Do not display:

- `Language`
- `Language · English`
- `Language: English`
- translated equivalents of that prefix.

Use `aria-label="Language"` and a tooltip for accessibility. English remains the first-load default.

## 11. Progress Control

The progress indicator must be easy to see and useful in presentation mode.

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

Targets:

- 1600–1920 px viewport: roughly 300–480 px bar width;
- 1366 px viewport: roughly 220–300 px where practical;
- visibly thicker than a 2–4 px decorative line;
- current/total scene count remains legible.

## 12. Narration Controls

- Bottom-right compact icon-only speaker/play button.
- No visible voice name in the footer.
- No large `Narrate` or `语音讲解` text button.
- Detailed settings open in a compact popover.
- Show no more than three curated voices for the active locale.
- Filter low-quality and duplicate voices.

## 13. Presentation Hygiene

Do not show in learner mode:

- Source mapping / 源内容映射;
- narration transcript / 旁白文本 accordions;
- authoring notes;
- QA labels;
- generation/debug metadata.

Keep source references in internal data, Course Map, and QA Report. Offer optional captions through audio settings.

## 14. Motion

Allowed:

- 150–300 ms fades and transforms;
- subtle card elevation;
- progress animation;
- hotspot pulse;
- drawer slide.

Avoid continuous decorative movement, bouncing, flashing, or motion competing with narration. Respect `prefers-reduced-motion`.

## 15. Responsive Rules

- Wide screens retain strong hierarchy and asymmetric composition.
- Medium screens may adjust ratios but must not flatten every item into equal cards.
- Mobile uses alternate layouts, tabs, or additional scenes rather than a long article.
- Minimum touch target: 44×44 px.
- No unintended horizontal or vertical page scrolling.

## 16. UI Acceptance Checklist

A course fails UI QA when any of the following is true:

- a normal scene scrolls vertically;
- all major elements look the same size or importance;
- most scenes use repetitive equal-card grids;
- a hero or key scene lacks a strong focal title/image/message;
- technical images are cropped, truncated, or too small to teach from;
- `object-fit: cover` is used for a technical figure;
- large source whitespace remains while the useful image is tiny;
- the progress bar is too short or thin to read comfortably;
- the language button includes the `Language` prefix;
- Course Menu is in the header or permanently visible;
- the narration footer shows a voice name or full dropdown;
- source mapping or transcript blocks appear in presentation mode;
- the header logo appears in an accidental white rectangle;
- the stage contains a dominant unrelated plain-white block;
- Micas primary is not `#00899F`;
- one of the four required locales is missing;
- the dark visual system is inconsistent between header, body, and footer.

## 17. Required Visual QA

Review every scene at:

- 1920×1080;
- 1600×900;
- 1366×768;
- all four locales.

Verify:

- one dominant focal element;
- title and key content hierarchy;
- complete image visibility;
- image size sufficient for instruction;
- no clipping or overflow;
- larger readable progress;
- selected-language-only control;
- stable footer controls;
- preview-style visual quality.