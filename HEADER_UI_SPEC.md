# Micas Header UI Specification

Version: **2.3.3**

This file is the mandatory upper-left header override for the **Micas Doc-to-Interactive-Training Skill**.

Visual reference:

`assets/ui-reference/header-lockup-reference.svg`

The reference image is part of the Skill package and should be inspected when the runtime supports image reading. The written rules below remain authoritative.

## 1. Design Intent

The left side of the header should feel like a confident Micas product-training identity, not a small website logo beside generic navigation.

Use one integrated horizontal brand lockup:

- large Micas logo on the left;
- stacked course title and product/module subtitle on the right;
- all elements vertically centered;
- strong hierarchy and generous spacing;
- direct integration into the dark header background.

## 2. Required Structure

```html
<header class="course-header">
  <div class="brand-lockup">
    <img class="brand-logo" src="..." alt="Micas Networks">
    <div class="brand-copy">
      <div class="course-title">Micas CPO Training</div>
      <div class="course-subtitle">M2-W6940-128X1-FR4 Hardware</div>
    </div>
  </div>

  <div class="header-actions">
    <!-- language, Video, Fullscreen, and required compact utilities -->
  </div>
</header>
```

## 3. Desktop Sizing and Hierarchy

Target ranges at the required desktop QA viewports:

- logo width: **190–250 px**;
- logo height: **52–72 px**;
- logo-to-text gap: **28–42 px**;
- course title: **30–44 px**, bold, bright white;
- product/module subtitle: **18–28 px**, muted blue-white;
- title/subtitle gap: approximately **3–7 px**.

The title is visually dominant. The subtitle supports it and must not compete with it.

## 4. Layout Rules

1. Use a transparent Micas logo designed for a dark background.
2. Preserve the logo aspect ratio and clear space.
3. Vertically center the logo and the complete two-line text block as one unit.
4. Keep the title and subtitle left-aligned.
5. Keep the brand lockup directly on the deep-navy header background.
6. Do not use a white rectangle, card, raised panel, or independent container behind the logo or title.
7. Add a restrained cyan/teal divider along the bottom of the header.
8. Keep the right-side utilities at the far right.
9. Header utilities must not squeeze, overlap, cover, or visually dominate the left brand lockup.
10. Avoid unnecessary wrapping of the main course title at 1920×1080, 1600×900, and 1366×768.
11. When horizontal space becomes tight, apply this priority:
    - compact nonessential utility labels;
    - reduce gaps within safe limits;
    - shorten the contextual subtitle without changing technical meaning;
    - proportionally scale the entire lockup;
    - only then allow controlled wrapping.
12. Do not shrink only the logo or only the text until the hierarchy becomes unbalanced.

## 5. Recommended CSS

```css
.course-header {
  display: flex;
  align-items: center;
  min-width: 0;
  gap: 24px;
  padding-inline: clamp(28px, 3vw, 56px);
  background: var(--micas-bg-deep);
  border-bottom: 1px solid rgba(118, 228, 238, .24);
}

.brand-lockup {
  min-width: 0;
  display: flex;
  align-items: center;
  gap: clamp(28px, 2.4vw, 42px);
}

.brand-logo {
  display: block;
  width: clamp(190px, 15vw, 250px);
  max-height: 72px;
  object-fit: contain;
  flex: 0 0 auto;
}

.brand-copy {
  min-width: 0;
  display: grid;
  align-content: center;
  gap: 4px;
}

.brand-copy .course-title {
  margin: 0;
  font-size: clamp(30px, 2.45vw, 44px);
  line-height: 1.02;
  letter-spacing: -.025em;
  font-weight: 800;
  color: var(--micas-text);
}

.brand-copy .course-subtitle {
  margin: 0;
  font-size: clamp(18px, 1.55vw, 28px);
  line-height: 1.18;
  font-weight: 500;
  color: var(--micas-text-muted);
}

.header-actions {
  margin-left: auto;
  display: flex;
  align-items: center;
  gap: 12px;
  flex: 0 0 auto;
}
```

## 6. Responsive Behavior

- Retain the same visual identity on medium screens.
- Scale the logo, title, subtitle, and spacing proportionally.
- Do not switch to a tiny icon-only brand mark while ample header width remains.
- On compact/mobile layouts, a smaller proportional lockup is allowed, but the title/subtitle relationship must remain recognizable.
- If utilities cannot coexist comfortably, use compact icon controls or an overflow utility menu rather than damaging the brand lockup.
- The header must still fit within the one-screen course shell and must not create scene overflow.

## 7. Asset Usage

The bundled screenshot is a reference asset, not a production header image.

Do:

- inspect it for proportions, hierarchy, spacing, and color relationship;
- use the actual transparent Micas logo from the source or approved brand assets;
- implement the title and subtitle as selectable, localizable live text.

Do not:

- embed the screenshot as a flattened header;
- crop the reference image and use it as the logo;
- make text nonlocalizable by baking it into an image.

## 8. Multilingual Behavior

English remains the visual master.

For Simplified Chinese, Traditional Chinese, and Japanese:

- keep the same brand lockup identity;
- allow locale-specific title/subtitle widths, line breaks, and slight size adjustments;
- preserve the logo size and visual prominence where possible;
- do not weaken the English layout to force identical multilingual line breaks.

## 9. Header QA

At 1920×1080, 1600×900, and 1366×768, confirm:

- the logo is large, sharp, and fully visible;
- the course title is clearly dominant;
- the subtitle is readable and subordinate;
- logo and text are vertically centered;
- spacing resembles the approved reference;
- the header background remains unified deep navy;
- no white logo rectangle or card appears;
- the cyan divider is restrained;
- right-side utilities do not crowd or overlap the lockup;
- no title or subtitle is clipped;
- all supported languages remain usable;
- the one-screen viewport contract still passes.

## 10. Release-Blocking Defects

Do not deliver when any of the following occurs:

- tiny or visually weak Micas logo;
- title and subtitle have nearly equal visual weight;
- logo/title/subtitle are vertically misaligned;
- white rectangle or separate card behind the logo;
- excessive or cramped logo-to-text gap;
- utilities overlap or squeeze the lockup;
- main title is unnecessarily wrapped or clipped at a required desktop viewport;
- screenshot is embedded as a flattened production header;
- multilingual text breaks the header or causes viewport overflow.