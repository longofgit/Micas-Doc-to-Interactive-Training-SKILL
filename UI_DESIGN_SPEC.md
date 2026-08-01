# Micas Interactive Training UI Design Specification

This file is the visual implementation contract for courses generated with the **Micas Doc-to- Interactive-Training Skill**.

## 1. Design Goal

Match the successful preview experience:

- One coherent dark blue stage
- Micas cyan used as the primary accent
- Large, confident titles
- Product imagery framed intentionally
- Rounded, low-contrast glass or blue-tinted cards
- Clear progress and presentation controls
- No permanently visible course directory
- No abrupt oversized white content panel

The interface should feel like a premium technical product launch and field-engineer mission console, not an LMS template or document reader.

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
}
```

Do not substitute a generic bright blue for `#00899F`.

## 3. Page Shell

### Header

- Dark integrated background; height normally 72–84 px.
- Left: transparent Micas logo, course/product title, compact scene subtitle.
- Right: optional search icon, `Language` dropdown, Video mode, Fullscreen.
- Utility controls should be compact and visually secondary.
- The `Language` button text remains English in every locale.

### Content Stage

- Uses the full available width because the directory is not docked.
- Maintain dark background across the stage.
- Main content may use blue-tinted surfaces, transparent cards, gradients, framed images, and compact light canvases.
- Never put the entire main area inside a plain white rectangle.

### Footer / Control Rail

- Scene counter and progress on the left.
- Previous/Next centered or logically grouped.
- Audio/voice controls and other utility controls on the right.
- Keep height compact and preserve content focus.

## 4. Hidden Course Directory

- Default state: closed.
- Trigger: compact menu button in the header.
- Presentation: left overlay drawer on desktop, full-width sheet on mobile.
- Includes module list, scene list/counts, progress, search, and quick jump.
- Drawer closes after selecting a scene.
- Escape, backdrop click, and close button must work.
- Use focus trapping while open.
- It must not automatically open in Video mode or Fullscreen.

## 5. Preferred Scene Layouts

### Hero Scene

- Two-column split around 52/48 or 50/50.
- Left: small mission label, 2–4 line large title, short promise, three outcome cards.
- Right: framed product/process image with 3–5 chips.
- Background remains dark.

### Hardware Identification

- Large authentic equipment image.
- Numbered hotspots with accessible labels.
- Side or bottom detail cards appear on selection.
- Avoid shrinking the image to accommodate a permanent sidebar.

### Procedure

- Horizontal or vertical step timeline.
- One active step at a time.
- Safety gate before hazardous steps.
- Use diagrams or photographs where available.

### Specification

- Use grouped chips and cards, not a copied full table unless the table itself is the learning objective.
- Keep exhaustive details in an expandable reference panel.

### Troubleshooting

- Symptom card → evidence → learner decision → guided next check.
- Use dark cards with accent borders.
- Feedback must explain why, not merely mark correct/incorrect.

### Quiz

- One question per scene where possible.
- Large touch-friendly choices.
- Immediate, localized feedback.
- Keep warning scenarios serious.

## 6. Logo Handling

Preferred order:

1. Transparent SVG or PNG designed for dark backgrounds
2. Transparent standard Micas logo with sufficient contrast
3. Carefully cropped logo inside a compact designed plaque

Forbidden:

- Stretched logo
- White rectangular image dropped directly into dark header
- Unapproved recoloring
- Cropping that removes any part of the mark

## 7. Language Control

The compact control must look like:

`Language ▾`

Dropdown entries:

- English
- 简体中文
- 繁體中文
- 日本語

English is the default. The button label stays `Language`; do not translate it to 中文, 語言, or 言語.

## 8. Color Use

- `#00899F`: primary actions, active state, progress, highlights
- Deep navy: page background
- Blue-tinted surfaces: cards and controls
- Near-white: text and small controlled canvases
- Red/orange/yellow: only for source-supported warning states
- Green: success/completion

A white image frame is acceptable when it deliberately showcases a product image. A large white body area is not.

## 9. Typography

Use a robust system-font stack to preserve offline behavior:

```css
font-family: Inter, ui-sans-serif, system-ui, -apple-system,
  BlinkMacSystemFont, "Segoe UI", "Noto Sans", "Noto Sans SC",
  "Noto Sans TC", "Noto Sans JP", Arial, sans-serif;
```

Do not load external web fonts in a self-contained offline course.

Recommended scale:

- Hero title: `clamp(42px, 5vw, 78px)`
- Scene title: `clamp(32px, 3.2vw, 56px)`
- Body: `18–22px` on desktop, `16–18px` on mobile
- Labels/chips: `13–16px`

## 10. Motion

Allowed:

- 150–300 ms fades and transforms
- Subtle card elevation
- Progress animation
- Hotspot pulse
- Drawer slide

Avoid:

- Continuous decorative motion
- Excessive bouncing
- Rapid flashing
- Motion that competes with narration

Respect `prefers-reduced-motion`.

## 11. Responsive Rules

- At wide sizes, retain strong two-column composition.
- Below roughly 900 px, stack hero sections while keeping image prominent.
- Below roughly 640 px, simplify header controls into icons or compact buttons.
- Drawer becomes nearly full-screen on mobile.
- Minimum touch target: 44 × 44 px.
- No unintended horizontal scrolling.

## 12. UI Acceptance Checklist

A course fails UI QA when any of the following is true:

- The header logo appears inside an accidental white rectangle.
- The main scene contains a dominant plain white block unrelated to an image/table need.
- The course directory remains permanently docked during normal teaching.
- The brand primary is not `#00899F`.
- English is not the first-load language.
- The language control is a large toggle or its button label is translated.
- Any of the four required locales is missing.
- The dark visual system is inconsistent between header, body, and footer.
- Content is cramped because navigation consumes permanent width.
