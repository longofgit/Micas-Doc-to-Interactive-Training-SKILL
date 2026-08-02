# Micas Brand Pack

Version: **3.0.0**

Brand ID: `micas`

This pack contains all Micas-specific identity, color, logo, tone, and visual-reference rules. It does not define source-grounding, assessment, narration, navigation, or experience-mode logic.

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
- Do not replace it with a white-background logo, legacy logo, alternate Micas lockup, text-only substitute, generated approximation, or another logo variant.
- Do not recolor, redraw, distort, crop, stretch, simplify, or rebuild the logo.
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

Use one integrated horizontal lockup:

- the official default Micas logo asset on the left;
- bold white course title immediately to its right;
- smaller muted product, platform, or module subtitle below the title;
- logo and text vertically centered as one unit;
- generous logo-to-text spacing;
- direct integration into the deep-navy header;
- subtle cyan divider along the header bottom;
- utilities on the far right without squeezing or overlapping the lockup.

Desktop target ranges:

- logo width: `190–250px`;
- logo height: `52–72px`;
- course title: `30–44px`;
- subtitle: `18–28px`;
- logo-to-text gap: `28–42px`.

Do not place the logo in a white rectangle, card, or independent panel.

# 5. Tone and Copy

Preferred tone:

- technically credible;
- direct and operational;
- confident without exaggerated marketing language;
- concise but not cryptic;
- learner-focused and field-oriented;
- explicit about limits, exceptions, and safety conditions.

Avoid unsupported superlatives and generic corporate filler.

# 6. Visual Reference Assets

All Micas logo and visual-reference assets are colocated in:

`modules/brands/micas/references/`

Official logo asset:

- `micas-logo-default.svg`

Current layout references:

- `header-lockup-reference.svg`
- `content-hero-product-split-reference.svg`
- `content-checkpoint-positioning-reference.svg`
- `content-checkpoint-redundancy-airflow-reference.svg`
- `content-key-metrics-power-reference.svg`
- `header-action-icons-reference.svg`

These references demonstrate:

- large selective headline typography;
- deep-navy page integration;
- strong text/image balance;
- complete technical imagery in controlled light frames;
- three or fewer substantial support cards where appropriate;
- oversized numbers and short labels;
- Micas cyan chips and restrained light surfaces;
- integrated header identity;
- compact utility icons aligned with labels.

Use the screenshots for proportion, hierarchy, spacing, and component treatment only. Recreate the result with live HTML/CSS, localizable text, the official default logo asset, and source-document visuals. Do not insert a reference screenshot as a flattened production page and do not extract or substitute a logo from a screenshot.

# 7. Micas Brand QA

The Micas presentation fails brand QA when:

- the official `micas-logo-default.svg` asset is not used while `brand_profile: micas` is active;
- a white-background, legacy, alternate, generated, redrawn, recolored, cropped, stretched, or distorted Micas logo appears;
- different Micas logo variants appear across different scenes;
- the stage becomes a pale or white full-page canvas;
- the logo is tiny, boxed in white, or visually detached;
- a generic bright blue replaces Micas cyan;
- header utilities overlap or compress the brand lockup;
- visual hierarchy is weak and every card looks equal;
- technical pages look like a generic LMS or document viewer;
- localized light components expand into the global page background;
- reference images are copied directly instead of recreated with live content.
