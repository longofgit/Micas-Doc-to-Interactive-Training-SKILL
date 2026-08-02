# Micas Brand Pack

Version: **3.1.2**

Brand ID: `micas`

This pack contains all Micas-specific identity, color, logo, tone, and visual-reference rules. It does not define source-grounding, assessment, narration, navigation, or training-mode logic.

# 1. Identity

- Company: **Micas Networks**
- Primary color: `#00899F`
- Visual character: dark, premium, technical, spacious, confident, mission-oriented
- Default stage: unified deep navy
- Accent behavior: cyan highlights, restrained glows, blue-tinted translucent surfaces
- Official default logo: `modules/brands/micas/references/micas-logo-default.svg`

## Official Default Logo Lock

For every project using `brand_profile: micas`, the mandatory default company logo is:

`modules/brands/micas/references/micas-logo-default.svg`

Rules:

- Use this asset consistently in the course header, cover, and any other location that requires the primary Micas company logo.
- The asset is based on the latest clear transparent artwork supplied by the user and must remain the single authoritative Micas logo asset.
- Do not replace it with a white-background logo, legacy logo, alternate Micas lockup, text-only substitute, generated approximation, or another logo variant.
- Do not recolor, redraw, retrace, distort, crop, stretch, simplify, blur, sharpen, or rebuild the logo.
- Preserve its transparent background and original aspect ratio.
- Do not place it inside a white rectangle, white card, or unrelated background panel.
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

- logo width: `190–250px`;
- logo height: `52–72px`;
- course title: `30–44px`;
- subtitle: `18–28px`;
- logo-to-text gap: `28–42px`.

Do not place the logo in a white rectangle, card, or independent panel.

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

The icons inside the existing approved controls must be clearly larger than the previous undersized implementation. Do not enlarge or redesign the surrounding buttons; enlarge only the icon glyphs and keep them centered.

Desktop icon targets:

- language globe icon: `28–32px`;
- language dropdown chevron: `18–22px`;
- Auto Play icon: `28–32px`;
- Fullscreen icon: `28–32px`;
- Previous and Next arrow icons: `26–30px`;
- Search icon: `28–32px`;
- narration/speaker icon: `28–32px`;
- Audio settings icon: `28–32px`.

Recommended implementation:

```css
.header-language-icon,
.header-autoplay-icon,
.header-fullscreen-icon,
.footer-search-icon,
.footer-narration-icon,
.footer-audio-settings-icon {
  width: clamp(28px, 1.7vw, 32px);
  height: clamp(28px, 1.7vw, 32px);
  flex: 0 0 auto;
}

.nav-button .nav-arrow {
  width: clamp(26px, 1.55vw, 30px);
  height: clamp(26px, 1.55vw, 30px);
  flex: 0 0 auto;
}

.language-chevron {
  width: clamp(18px, 1.15vw, 22px);
  height: clamp(18px, 1.15vw, 22px);
  flex: 0 0 auto;
}
```

Rules:

- do not size these icons only through `1em` when the surrounding text size makes the icons too small;
- preserve the approved button dimensions, order, spacing, and labels;
- retain geometric and optical centering;
- icons must remain visually substantial in both enabled and disabled button states;
- tablet icons may reduce to approximately `24–28px` and phone icons to approximately `22–26px` only when required by the compact breakpoint.

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

# 7. Visual Reference Assets

All Micas logo and visual-reference assets are colocated in:

`modules/brands/micas/references/`

Official logo asset:

- `micas-logo-default.svg`

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

- the official `micas-logo-default.svg` asset is not used while `brand_profile: micas` is active;
- a white-background, legacy, alternate, generated, redrawn, recolored, cropped, stretched, blurred, or distorted Micas logo appears;
- different Micas logo variants appear across different scenes;
- the desktop header omits the factual subtitle below the main course title;
- Auto Play or Fullscreen is missing from the normal desktop header;
- language loses its icon or the right-side control order differs from Language → Auto Play → Fullscreen;
- any of the required desktop control icons is visibly undersized, generally below `26px` except the language chevron;
- the icon glyphs look materially smaller than the approved control references;
- header progress/module counters replace the required utility group;
- the fixed footer materially differs from the reference structure without a responsive breakpoint reason;
- the stage becomes a pale or white full-page canvas;
- the logo is tiny, boxed in white, or visually detached;
- a generic bright blue replaces Micas cyan;
- header utilities overlap or compress the brand lockup;
- visual hierarchy is weak and every card looks equal;
- technical pages look like a generic LMS or document viewer;
- localized light components expand into the global page background;
- emphasis colors are excessive, inconsistent, or decorative rather than semantic;
- reference images are copied directly instead of recreated with live content.
