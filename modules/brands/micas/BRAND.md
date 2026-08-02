# Micas Brand Pack

Version: **3.1.9**

Brand ID: `micas`

This pack contains all Micas-specific identity, color, logo, tone, and visual-reference rules. It does not define source-grounding, assessment, narration, navigation, or training-mode logic.

# 1. Identity

- Company: **Micas Networks**
- Primary color: `#00899F`
- Visual character: dark, premium, technical, spacious, confident, mission-oriented
- Default stage: unified deep navy
- Accent behavior: cyan highlights, restrained glows, blue-tinted translucent surfaces
- Official default logo: `modules/brands/micas/references/micas-logo-default.png`

## Official Default Logo Lock

For every project using `brand_profile: micas`, the mandatory default company logo is:

`modules/brands/micas/references/micas-logo-default.png`

Rules:

- Use this exact transparent PNG consistently in the course header, cover, and any other location that requires the primary Micas company logo.
- The asset is the latest clear `415×148` artwork supplied by the user and must remain the single authoritative Micas logo asset.
- Do not replace it with a white-background logo, legacy logo, alternate Micas lockup, text-only substitute, generated approximation, traced SVG, or another logo variant.
- Do not recolor, redraw, retrace, vectorize, distort, crop, stretch, simplify, blur, sharpen, or rebuild the logo.
- Preserve its transparent background, intrinsic pixels, and original aspect ratio.
- Do not place it inside a white rectangle, white card, or unrelated background panel.
- Do not upscale it beyond its intrinsic `415px` width. Normal header rendering is a downscale to the approved range.
- Render it with `image-rendering: auto`, no CSS filter, no transform scaling, and no browser-generated shadow or stroke.
- A different Micas logo may be used only when the user explicitly supplies and requests a replacement official asset for that project.
- Visual-reference screenshots are layout references only and must never override this official logo asset.

# 2. Brand Tokens

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

Do not substitute a generic bright blue for Micas cyan.

# 3. Stage Theme

The complete learner-facing shell, stage, and scene background remain deep navy.

```css
html,
body,
.course-shell,
.scene-stage,
.scene {
  background: var(--stage-bg);
  color: var(--text);
}
```

Light colors may be used only as bounded elements such as:

- technical-image frames;
- metric tiles;
- selected comparison cards;
- controlled data surfaces.

A white, pale-gray, or light-grid full-page content background is not part of the Micas course identity.

# 4. Header Brand Lockup

The required desktop header lockup follows:

`modules/brands/micas/references/header-lockup-reference.svg`

Use one integrated horizontal lockup:

- the official default Micas logo asset on the left;
- a bold white course title immediately to its right;
- a smaller muted product, platform, lesson, or module subtitle directly below the title;
- logo and the two-line text block vertically centered as one unit;
- generous logo-to-text spacing;
- direct integration into the deep-navy header;
- subtle cyan divider along the header bottom;
- utilities on the far right without squeezing or overlapping the lockup.

The title/subtitle hierarchy is mandatory on normal desktop pages. Do not omit the subtitle merely to save space. When the source does not provide a subtitle, create a short factual subtitle from available project metadata, such as the product/platform plus the current lesson or module topic. Do not invent marketing claims.

Desktop target ranges:

- logo width: `150–195px`;
- logo height: `auto`, normally `42–55px` after proportional downscaling;
- course title: `26–36px`;
- subtitle: `16–21px`;
- logo-to-text gap: `24–34px`.

The brand lockup must not touch the viewport edges. Follow the spacing shown in `header-lockup-reference.svg`.

Recommended desktop implementation:

```css
.course-shell {
  /* Keep the approved thinner top and bottom rails. */
  --header-h: clamp(60px, calc(8vh - 10px), 82px);
  --footer-h: clamp(68px, calc(9vh - 10px), 90px);
}

.course-header-inner {
  display: flex;
  align-items: center;
  padding-top: clamp(9px, 1vh, 13px);
  padding-bottom: clamp(4px, .5vh, 7px);
  padding-inline: clamp(24px, 2.4vw, 44px);
}

.course-footer-inner {
  display: flex;
  align-items: center;
  padding-block: clamp(6px, .65vh, 10px);
  padding-inline: clamp(20px, 2vw, 38px);
}

.header-brand-lockup {
  display: flex;
  align-items: center;
  min-width: 0;
  margin: 0;
}

.header-brand-lockup img {
  display: block;
  width: clamp(150px, 10.8vw, 195px);
  height: auto;
  max-width: 195px;
  margin-left: clamp(6px, .45vw, 10px);
  margin-top: clamp(4px, .35vh, 6px);
  object-fit: contain;
  image-rendering: auto;
  filter: none;
  transform: none;
}

.header-title-group {
  margin-left: clamp(24px, 2vw, 34px);
  padding-block: 2px;
  min-width: 0;
}

.header-course-title {
  font-size: clamp(26px, 2.15vw, 36px);
  line-height: 1.05;
}

.header-course-subtitle {
  margin-top: 3px;
  font-size: clamp(16px, 1.25vw, 21px);
  line-height: 1.15;
}

.header-control {
  min-height: clamp(48px, 5.2vh, 54px);
  padding-inline: clamp(16px, 1.3vw, 22px);
  border-radius: 16px;
  font-size: clamp(16px, 1.05vw, 18px);
  line-height: 1;
  flex: 0 0 auto;
}

.header-control .control-content {
  gap: clamp(8px, .7vw, 10px);
}

.course-menu-button,
.nav-button {
  min-height: clamp(50px, 5.6vh, 56px);
  padding-inline: clamp(18px, 1.45vw, 22px);
  border-radius: 16px;
  font-size: clamp(16px, 1.08vw, 18px);
  line-height: 1;
  flex: 0 0 auto;
}

.nav-button {
  min-width: clamp(128px, 10vw, 146px);
}

.icon-control {
  width: clamp(50px, 5.6vh, 56px);
  height: clamp(50px, 5.6vh, 56px);
  min-width: clamp(50px, 5.6vh, 56px);
  min-height: clamp(50px, 5.6vh, 56px);
  border-radius: 16px;
  padding: 0;
  flex: 0 0 auto;
}

.footer-control-group,
.header-utility-group {
  align-items: center;
  gap: clamp(10px, .8vw, 14px);
}

.footer-progress-label,
.footer-scene-count {
  font-size: clamp(15px, 1vw, 17px);
  line-height: 1.1;
}
```

Rules:

- keep at least `24px` horizontal inset between the viewport edge and the logo on desktop;
- apply the additional small intrinsic logo offset shown above so the visible logo artwork has slightly more top and left breathing room;
- this logo-only offset must not move or resize the course title, subtitle, header utilities, or fixed control rails;
- use the slightly larger top inset in the header so the brand lockup and utility controls do not visually hug the top viewport edge;
- keep visible vertical breathing room between every header/footer control and the rail borders;
- reduce the left/right rail inset only; do not change control order, button shells, labels, progress proportions, or the content-stage margins;
- keep title and subtitle inside the same padded header container;
- keep the approved thinner rail heights and compact content sizing;
- keep all controls vertically centered inside both fixed rails;
- do not compensate for reduced horizontal padding by enlarging the logo, typography, button shells, or icon glyphs;
- do not place the logo in a white rectangle, card, or independent panel.

## Compact Fixed Rail Lock

For the Micas desktop shell, the top header rail and bottom fixed control rail retain the previously approved approximately `10px` height reduction. Their internal content remains compact.

Rules:

- retain the approved compact rail heights;
- use the reduced icon glyph ranges below and keep every icon centered;
- give the top header slightly more top breathing room than bottom breathing room;
- use shorter left/right padding for both rails so the control groups sit closer to the viewport edges without touching them;
- maintain visible breathing space between every control outline and the top/bottom rail borders;
- keep all controls vertically centered;
- the footer must still reserve its own grid row and must never overlap scene content;
- the header must still preserve the complete logo, main title, subtitle, and Language → Auto Play → Fullscreen group;
- if the viewport becomes too compact, use the existing responsive breakpoint behavior instead of compressing desktop content below these approved ranges.

## Header Utility Lock

For standard Micas interactive training on desktop, the far-right header utility group must contain, in this order:

1. selected language with a centered globe/language icon and dropdown chevron;
2. Auto Play with a centered play icon;
3. Fullscreen with a centered four-corner icon.

Use this reference:

`modules/brands/micas/references/top-right-controls-reference.svg`

Rules:

- do not remove Auto Play or Fullscreen from the normal desktop header;
- do not replace the three controls with progress, module count, scene count, or assessment count;
- progress belongs in the fixed footer control area;
- the visible language control shows the selected language value without a `Language` prefix;
- all icons and labels remain vertically centered and visually balanced;
- compact responsive variants are allowed only at tablet/phone breakpoints.

## Control Icon Size Lock

Keep the surrounding buttons, labels, order, spacing, and rail dimensions unchanged. Only reduce the icon glyphs to the following ranges and keep every glyph centered.

Desktop icon targets:

- Course Menu hamburger icon: `21–23px`;
- language globe icon: `21–23px`;
- language dropdown chevron: `14–16px`;
- Auto Play icon: `21–23px`;
- Fullscreen icon: `21–23px`;
- Previous and Next arrow icons: `20–23px`;
- Search icon: `21–23px`;
- narration/speaker icon: `21–23px`;
- Audio settings icon: `21–23px`.

Recommended implementation:

```css
.course-menu-icon,
.header-language-icon,
.header-autoplay-icon,
.header-fullscreen-icon,
.footer-search-icon,
.footer-narration-icon,
.footer-audio-settings-icon {
  width: clamp(21px, 1.22vw, 23px);
  height: clamp(21px, 1.22vw, 23px);
  flex: 0 0 auto;
}

.nav-button .nav-arrow {
  width: clamp(20px, 1.18vw, 23px);
  height: clamp(20px, 1.18vw, 23px);
  flex: 0 0 auto;
}

.language-chevron {
  width: clamp(14px, .88vw, 16px);
  height: clamp(14px, .88vw, 16px);
  flex: 0 0 auto;
}
```

Rules:

- change only the icon glyph sizes; do not resize the button shells, labels, spacing, rail height, progress area, or control order;
- the official company logo follows only the slightly reduced header lockup range above and is not treated as a utility icon;
- do not size these icons through `1em` when the surrounding text makes them exceed the approved ranges;
- retain geometric and optical centering;
- keep disabled-state icons the same physical size as enabled-state icons;
- tablet icons may reduce to approximately `19–21px` and phone icons to approximately `17–19px` only when required by the compact breakpoint.

# 5. Tone and Copy

Preferred tone:

- technically credible;
- direct and operational;
- confident without exaggerated marketing language;
- concise but not cryptic;
- learner-focused and field-oriented;
- explicit about limits, exceptions, and safety conditions.

Avoid unsupported superlatives and generic corporate filler.

# 6. Controlled Emphasis and Highlight Colors

Important learning content may use restrained semantic emphasis while preserving the dark Micas visual system.

Preferred emphasis:

- Micas cyan or bright cyan for key numbers, required actions, product identifiers, and primary conclusions;
- brand-soft cyan for supportive highlights and chips;
- warning amber for exceptions, limitations, cautions, and conditions requiring verification;
- success green for confirmed correct states or completed actions;
- danger red only for genuine hazards, critical failures, or prohibited actions.

Use emphasis selectively. A normal page should usually contain one dominant emphasis treatment and no more than two supporting accent treatments. Do not turn entire paragraphs into multiple colors, use rainbow styling, or apply bright fills that conflict with the deep-navy stage.

## Body Classification and Sequence Number Lock

When the learner-facing body groups content into categories, phases, stages, steps, modules, checkpoints, priorities, outcomes, or numbered cards, the category marker must be intentionally prominent. Small eyebrow-style numbers such as `01`, `02`, `03`, or `04` must not look like secondary metadata.

Apply this rule to visible body markers such as:

- `01`, `02`, `03`, `04` category numbers;
- `STEP 1`, `PHASE 2`, `STAGE 3`, or equivalent labels;
- numbered process cards;
- learning-flow cards;
- outcome or capability groups;
- sequence, priority, checkpoint, and milestone markers.

Recommended desktop implementation:

```css
.category-number,
.step-number,
.phase-number,
.stage-number,
.sequence-number,
.card-index,
.flow-index,
.checkpoint-number {
  display: inline-flex;
  align-items: center;
  min-height: 1em;
  color: var(--brand-primary-soft);
  font-size: clamp(30px, 2.1vw, 42px);
  line-height: .95;
  font-weight: 820;
  letter-spacing: .04em;
  font-variant-numeric: tabular-nums;
}

.category-label,
.step-label,
.phase-label,
.stage-label,
.sequence-label,
.checkpoint-label {
  font-size: clamp(24px, 1.55vw, 30px);
  line-height: 1.1;
  font-weight: 760;
}
```

Rules:

- at `1366×768`, a primary category or sequence number should normally render at least `30px`;
- the number must be visually stronger than supporting body copy and clearly visible before the learner reads the card title;
- use Micas cyan or brand-soft cyan with strong weight and sufficient contrast;
- keep equal-width number alignment when several cards form one row;
- do not reduce the number to caption size, metadata size, or a tiny corner tag;
- do not enlarge the marker by making the entire card header excessively tall; balance number size, padding, and title placement;
- when space is insufficient, shorten the label, rebalance the card, or split the scene instead of shrinking the category number;
- this rule applies only to learner-facing body content and must not change the fixed header or footer control rails.

# 7. Visual Reference Assets

All Micas logo and visual-reference assets are colocated in:

`modules/brands/micas/references/`

Official logo asset:

- `micas-logo-default.png`

Current layout references:

- `header-lockup-reference.svg`
- `top-right-controls-reference.svg`
- `footer-fixed-controls-reference.svg`
- `content-hero-product-split-reference.svg`
- `content-checkpoint-positioning-reference.svg`
- `content-checkpoint-redundancy-airflow-reference.svg`
- `content-key-metrics-power-reference.svg`
- `header-action-icons-reference.svg`

These references demonstrate:

- large selective headline typography;
- mandatory title/subtitle hierarchy in the header;
- the fixed Language → Auto Play → Fullscreen utility group;
- the fixed footer with substantial navigation and utility controls;
- deep-navy page integration;
- strong text/image balance;
- complete technical imagery in controlled light frames;
- three or fewer substantial support cards where appropriate;
- oversized numbers and short labels;
- Micas cyan chips and restrained light surfaces;
- clearly visible utility icons aligned with labels.

Use the references for proportion, hierarchy, spacing, and component treatment only. Recreate the result with live HTML/CSS, localizable text, the official default logo asset, and source-document visuals. Do not insert a reference screenshot as a flattened production page and do not extract or substitute a logo from a screenshot.

# 8. Micas Brand QA

The Micas presentation fails brand QA when:

- the official `micas-logo-default.png` asset is not used while `brand_profile: micas` is active;
- the Logo is redrawn, retraced, vectorized, blurred, sharpened, upscaled beyond intrinsic size, or processed through CSS filters/transforms;
- a white-background, legacy, alternate, generated, recolored, cropped, stretched, or distorted Micas logo appears;
- different Micas logo variants appear across different scenes;
- the logo or title/subtitle group touches the viewport edge or lacks the approved breathing room;
- the visible logo artwork does not retain the approved small additional top and left breathing room;
- the logo exceeds the approved `195px` desktop maximum or the title/subtitle exceed their reduced target ranges without a documented responsive reason;
- the header lockup or utility controls visually hug the top viewport edge instead of preserving the approved top inset;
- the top or bottom rails retain excessive left/right empty space beyond the approved compact insets;
- the top or bottom rail content visually crowds or nearly touches the rail borders;
- header utility buttons exceed the approved compact `48–54px` height range without a responsive reason;
- footer navigation, Course Menu, or icon-button shells exceed the approved compact `50–56px` range without a responsive reason;
- the compact fixed rails are achieved by clipping controls rather than proportionally sizing and centering their internal content;
- the desktop header omits the factual subtitle below the main course title;
- Auto Play or Fullscreen is missing from the normal desktop header;
- language loses its icon or the right-side control order differs from Language → Auto Play → Fullscreen;
- any required desktop control icon falls outside the reduced approved ranges without a responsive breakpoint reason;
- the icon glyphs look materially larger than the reduced control references;
- header progress/module counters replace the required utility group;
- the fixed footer materially differs from the reference structure without a responsive breakpoint reason;
- a learner-facing category, phase, step, or sequence number is rendered as tiny metadata rather than a prominent body marker;
- a category marker falls below the approved desktop minimum without a responsive breakpoint reason;
- the stage becomes a pale or white full-page canvas;
- the logo is tiny, boxed in white, or visually detached;
- a generic bright blue replaces Micas cyan;
- header utilities overlap or compress the brand lockup;
- visual hierarchy is weak and every card looks equal;
- technical pages look like a generic LMS or document viewer;
- localized light components expand into the global page background;
- emphasis colors are excessive, inconsistent, or decorative rather than semantic;
- reference images are copied directly instead of recreated with live content.
