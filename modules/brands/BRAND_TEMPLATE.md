# Brand Pack Template

Copy this file into `modules/brands/<brand-id>/BRAND.md` and place all related logos and visual references in the same brand folder.

# 1. Identity

- Brand ID: `[brand-id]`
- Company or organization: `[name]`
- Primary color: `[hex]`
- Secondary colors: `[values]`
- Visual character: `[e.g. premium, technical, friendly, bold, minimal]`
- Default stage theme: `[dark / light / mixed]`
- Logo asset: `[relative path]`

# 2. Semantic Tokens

```css
:root {
  --brand-primary: [value];
  --brand-primary-bright: [value];
  --brand-primary-soft: [value];
  --stage-bg: [value];
  --stage-bg-deep: [value];
  --surface: [value];
  --surface-raised: [value];
  --surface-glass: [value];
  --border: [value];
  --text: [value];
  --text-muted: [value];
  --success: [value];
  --warning: [value];
  --danger: [value];
}
```

# 3. Logo and Header

Define:

- approved logo version;
- clear space and minimum size;
- header lockup composition;
- title and subtitle treatment;
- forbidden treatments such as distortion, white boxes, or low contrast.

# 4. Tone

Define:

- preferred voice;
- terminology;
- level of formality;
- claims policy;
- prohibited phrases or unsupported superlatives.

# 5. Reference Assets

Place assets under:

`modules/brands/<brand-id>/references/`

List every asset and explain what it demonstrates. References are guidance only and must not replace live, localizable production content.

# 6. Brand QA

List release blockers for color, logo, typography, hierarchy, accessibility, tone, and reference-asset misuse.

A brand pack may change identity and visual direction, but it may not override source facts, safety rules, selected-mode behavior, or mandatory QA.
