# Micas Interactive Training UI Design Specification

Version: **2.3.2**

This is the mandatory visual implementation contract for courses generated with the **Micas Doc-to-Interactive-Training Skill**.

# 1. Design Goal

The course must feel like a premium Micas presentation rather than an LMS, document reader, or debug build.

Required character:

- coherent deep-navy stage;
- Micas cyan `#00899F` as the primary accent;
- English-first visual design;
- large confident titles where emphasis is deserved;
- one obvious focal element per scene;
- complete, large, useful product and procedure visuals;
- substantial presentation controls;
- PPT-like scene navigation;
- no scrolling in normal learner scenes;
- no visible QA, overflow, or authoring information;
- no accidental half-empty pages.

# 2. Brand Tokens

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
  --header-h: clamp(68px, 8vh, 88px);
  --footer-h: clamp(78px, 9vh, 96px);
}
```

Do not substitute a generic bright blue for Micas cyan.

# 3. Presentation Shell

```css
html, body {
  width: 100%;
  height: 100%;
  margin: 0;
  overflow: hidden;
}

.course-shell {
  width: 100%;
  height: 100dvh;
  min-height: 100vh;
  display: grid;
  grid-template-rows: var(--header-h) minmax(0, 1fr) var(--footer-h);
  overflow: hidden;
}

.scene-stage,
.scene {
  min-width: 0;
  min-height: 0;
  overflow: hidden;
}

.scene { height: 100%; }
```

Normal learner scenes must never use `overflow-y: auto`. Internal scrolling is allowed only inside deliberately opened drawers, settings panels, reference overlays, or reviewer tools.

# 4. Production vs Reviewer Mode

The production learner UI must never display:

- `Layout overflow detected`;
- fit or overflow warnings;
- debug badges;
- source-review notices;
- raw source mapping;
- narration transcripts;
- QA labels;
- missing-asset placeholders;
- generation metadata.

Reviewer diagnostics may exist only behind an explicit opt-in mode such as `?review=1` or an internal build flag. Default production state must be:

```js
const REVIEW_MODE = false;
```

Overflow is corrected before release, not announced to learners.

# 5. English-First Layout System

English is the visual master.

- Establish the best composition, spacing, title scale, image size, and line breaks in English first.
- Other languages may use locale-specific wording, line breaks, dimensions, or layout variants.
- Do not weaken the English layout to make every locale occupy identical space.
- Every locale must still pass viewport and image QA.

Recommended data model:

```js
scene.layout = {
  masterLocale: 'en',
  defaultVariant: 'hero-58-42',
  localeVariants: {
    'zh-CN': 'hero-55-45',
    'zh-TW': 'hero-55-45',
    ja: 'hero-55-45'
  }
};
```

# 6. Visual Hierarchy

Every scene must contain one dominant teaching element:

- hero statement;
- product image;
- annotated diagram;
- key number;
- warning;
- decision;
- current installation action.

The focal element should normally occupy 40–65% of the usable stage or carry clearly greater typographic weight than supporting material.

## Typography

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
.card-body { font-size: clamp(17px, 1.25vw, 22px); }
```

Use large typography selectively. Do not make every item large or every card identical.

# 7. Composition Rules

Preferred compositions:

- 58/42 or 60/40 hero split;
- large technical image plus short explanation;
- one dominant card with two smaller supporting cards;
- oversized metric plus evidence band;
- full-width process ribbon;
- hardware image with hotspots;
- scenario prompt plus decision area;
- full-stage assessment introduction.

Avoid using a repeated equal-sized 2×2 grid as the default solution.

## Empty-Space Rule

Intentional breathing room is good. A missing half-page is not.

1. Do not render empty visual containers, blank columns, or placeholder panels.
2. Use two columns only when both contain meaningful content.
3. If a planned image is absent or unsuitable, switch to a purposeful single-column composition.
4. Meaningful content should normally occupy about 65–90% of the usable stage.
5. An avoidable empty region occupying roughly one-third or more of the stage fails visual QA.
6. Do not fill space with low-value prose; redesign the page.

# 8. Header

Header content:

- transparent Micas logo integrated into the dark background;
- course/product title;
- compact scene subtitle;
- selected language;
- Video mode;
- Fullscreen;
- only necessary utilities.

Do not place Course Menu in the header.

## Logo

- Use a transparent SVG/PNG designed for dark backgrounds.
- Never drop a white rectangular logo image into the header.
- Preserve aspect ratio and clear space.
- Normal logo height: 36–58 px.

# 9. Language Control

Visible value is only the selected language:

- `English`
- `简体中文`
- `繁體中文`
- `日本語`

Forbidden visible labels:

- `Language`;
- `Language · English`;
- `Language: English`;
- translated equivalents of the prefix.

Keep `aria-label="Language"` and a tooltip where useful.

# 10. Footer and Control Rail

Required layout:

- **left group:** Course Menu, scene count, and prominent progress;
- **right group:** Previous, Next, narration, Audio settings—in that exact order.

Previous/Next are no longer centered. All four action controls stay together and align to the far right.

Desktop controls must remain substantial.

```css
.footer-rail {
  display: flex;
  align-items: center;
  gap: 16px;
}

.footer-meta {
  display: flex;
  align-items: center;
  gap: 16px;
  min-width: 0;
}

.footer-actions {
  margin-left: auto;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  gap: 12px;
  flex: 0 0 auto;
}

.footer-control,
.nav-button {
  min-height: 58px;
  padding: 0 24px;
  border-radius: 18px;
  font-size: 18px;
  font-weight: 700;
  flex: 0 0 auto;
}

.nav-button {
  min-width: 150px;
}

.icon-control {
  width: 58px;
  height: 58px;
  min-width: 58px;
  min-height: 58px;
  border-radius: 18px;
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

Rules:

- Desktop Previous/Next use text labels plus arrows.
- Tiny arrow-only square buttons are allowed only in compact/mobile mode.
- Course Menu, narration, and settings may not shrink below 56×56 px on desktop.
- Progress target: 340–520 px at 1600–1920 width; 240–320 px at 1366 width where practical.
- Controls remain visible at all required viewports.
- The DOM and visual order must remain: Previous → Next → narration → Audio settings.
- The entire `.footer-actions` group is right-aligned with `margin-left: auto`; none of its controls may be moved to the center or left.

## Sequential Navigation Availability

- Next is enabled on every scene that has a following global scene.
- The last scene in a module advances to the first scene in the next module.
- Module-check and final-assessment pages do not require an answer before Next becomes available.
- Unanswered questions are stored as unanswered and may be revisited; navigation remains available.
- Feedback, score, pass/fail, submitted state, narration, and animation must not gate Next.
- Only the absolute final completion scene may disable or replace Next.
- Previous is enabled on every scene except the first global scene.
- Visible buttons, keyboard arrows, and Video mode share the same navigation functions.

## Auto Play Timing

- Auto Play/Video mode must keep the current scene visible until that scene's complete narration has ended.
- The next scene is triggered by the final utterance `onend`, not by a fixed timeout or estimated duration.
- Multi-part narration waits for every chunk in order and advances only after the final chunk.
- Pausing narration pauses the scene transition.
- A narration error stops Auto Play on the current scene rather than skipping it.
- Manual Previous/Next cancels and invalidates the active narration so stale callbacks cannot advance again.
- Scenes with no narration may use a short explicit visual dwell.

# 11. Course Menu

- Trigger is bottom-left.
- Directory is hidden by default.
- Opens as an overlay drawer or modal sheet.
- Closes after selection, Escape, backdrop click, or close button.
- Must not reserve permanent stage width.
- May scroll internally when open.

# 12. Technical Image Contract

Technical visuals include products, chassis diagrams, screenshots, connector diagrams, installation figures, LED tables, and process illustrations.

Required behavior:

- fully visible by default;
- `object-fit: contain`;
- preserved aspect ratio;
- readable labels;
- no top/bottom/side clipping;
- no use of `cover` for technical content;
- source white margins and unrelated page content cropped before embedding;
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

- normal image/text scene: image receives 40–55% of stage;
- image-led scene: 55–75%;
- hardware identification: at least half the stage.

If a complete visual is not legible, use a full-view scene followed by explicit zoom/detail scenes. Never solve the problem by showing only half of the technical image.

# 13. Image Preflight

Preflight runs after fonts and all images load.

```js
async function waitForSceneAssets(scene) {
  await document.fonts?.ready;
  const images = [...scene.querySelectorAll('img')];
  await Promise.all(images.map(async img => {
    if (!img.complete) {
      await new Promise(resolve => {
        img.addEventListener('load', resolve, { once: true });
        img.addEventListener('error', resolve, { once: true });
      });
    }
    try { await img.decode?.(); } catch (_) {}
  }));
  await new Promise(requestAnimationFrame);
  await new Promise(requestAnimationFrame);
}
```

For every technical visual, verify:

- nonzero natural dimensions;
- meaningful rendered dimensions;
- full intersection with scene and viewport;
- no clipping by ancestors;
- `object-fit: contain`;
- acceptable source whitespace;
- readable labels.

A missing, half-visible, or unintentionally cropped image blocks release.

# 14. Narration UI

The normal footer shows a speaker/play icon. A separate settings icon or secondary action opens a compact popover.

- icon size: at least 58×58 px desktop;
- no voice name in the footer;
- no full voice dropdown in the footer;
- no large text button labeled `Narrate` or `语音讲解`;
- localized tooltip and accessible label.

# 15. Google-First Voice Selection

For each locale, the curated voice list must place an available Google voice first and select it by default.

Preferred name fragments:

- English: `Google US English`, `Google English`;
- Simplified Chinese: `Google 普通话`, `Google Mandarin`, `Google 中文`;
- Traditional Chinese: `Google 國語`, `Google Chinese (Taiwan)`, `Google 中文（台灣）`;
- Japanese: `Google 日本語`, `Google Japanese`.

Priority:

1. exact-locale Google;
2. exact-language Google;
3. exact-locale Microsoft Natural/Neural;
4. exact-locale Apple;
5. best exact-locale fallback.

Show no more than three voices. Include Google whenever the browser exposes a matching voice. Never invent unavailable voices.

# 16. Assessment Introduction Scene

Before the first final-assessment question, show a dedicated transition scene with:

- learning-section completion message;
- assessment purpose;
- question count;
- estimated duration;
- scoring/pass information;
- answer/feedback instructions;
- `Start Assessment` button;
- calm readiness message.

Auto/Video mode pauses here until the learner starts.

# 17. Responsive Rules

- Large screens retain strong asymmetry and large visuals.
- Medium screens may rebalance columns while preserving hierarchy.
- Mobile uses compact controls, tabs, or additional scenes.
- Do not turn mobile into a long article.
- Previous/Next may become icon-only only below the defined compact breakpoint.
- Technical images remain complete at every breakpoint.

# 18. Mandatory QA Viewports

At 100% browser zoom:

- 1920×1080;
- 1600×900;
- 1366×768.

Run English first, then all other locales.

# 19. UI Acceptance Checklist

The course fails UI QA when any of the following is true:

- visible `Layout overflow detected` or similar diagnostic;
- page or scene scrolls in normal learner mode;
- header/footer is clipped;
- an image is missing, half-visible, or unintentionally cropped;
- an empty visual frame or blank column remains;
- roughly one-third or more of the stage is avoidably empty;
- Previous/Next or audio controls are tiny on desktop;
- Next is disabled on a nonterminal scene, at a module boundary, or on an unanswered assessment question;
- Auto Play advances before the current scene narration finishes;
- narration pause, error, cancellation, or stale callbacks cause premature or duplicate navigation;
- Previous, Next, narration, and Audio settings are not grouped at the far right in the required order;
- English visual quality was weakened for multilingual uniformity;
- the language control displays a `Language` prefix;
- final assessment starts without a transition scene;
- source mapping, transcript, QA, or debug data is visible;
- the logo has an accidental white rectangle;
- a dominant plain-white main panel appears;
- Micas primary color is not `#00899F`.

# 20. Release Standard

Generate, render, inspect, correct, and rerun QA. Do not deliver merely because the HTML opens. The final result must look presentation-ready at every required viewport, with complete images, substantial controls, balanced stage utilization, and no visible production defects.