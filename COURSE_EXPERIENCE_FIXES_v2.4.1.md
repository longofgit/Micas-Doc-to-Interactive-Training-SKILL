# Micas Course Experience Fixes

Version: **2.4.1**

This is a narrowly scoped corrective override for the **Micas Doc-to-Interactive-Training Skill**. It changes only the five items defined below. All existing content, header, layout, navigation, assessment, image, language, responsive, and QA rules remain active unless this file is more specific.

# 1. Restore the Deep-Navy Learner Stage

The normal learner-facing course shell, scene stage, and scene background must remain dark.

Required baseline:

```css
html,
body,
.course-shell,
.scene-stage,
.scene {
  background: var(--micas-bg, #031f2b);
  color: var(--micas-text, #f5fbfd);
}
```

Rules:

- Do not turn the whole main-content stage into a pale, white, light-gray, or light-grid canvas.
- The bundled reference screenshots contain **localized light surfaces** such as product-image frames, metric tiles, or selected information cards. They do not authorize a light full-page background.
- Light surfaces may be used only as bounded components with deliberate contrast.
- The area surrounding cards, images, titles, and content remains the unified Micas deep-navy stage.
- A full-width or full-height pale content background, pale grid background, or white document-like body is a release-blocking visual defect.
- Keep the existing Micas color tokens and do not introduce a new global theme.

Recommended localized treatment:

```css
.light-visual-frame,
.metric-tile-light {
  background: #f5f8f9;
  color: #073543;
  border-radius: 24px;
}
```

These light components must remain visually bounded and must not become the scene background.

# 2. Search Is Icon-Only and Moves After Next

This section supersedes the footer order in `COURSE_EXPERIENCE_SPEC.md`.

Required right-side footer action order:

```text
Previous → Next → Search → narration → Audio settings
```

Rules:

- Search is immediately after Next and immediately before narration.
- Search uses only a magnifying-glass icon.
- Do not render visible text such as `Search`, `Search course`, `搜索`, or any translated label inside the button.
- Keep `aria-label="Search course"` and a localized tooltip for accessibility.
- Match the existing narration/settings icon-button size, border, radius, focus, hover, and active treatment.
- Keep the entire action cluster right-aligned.
- Do not change Previous, Next, narration, or Audio settings behavior or relative order except for inserting Search at the required position.

Recommended markup:

```html
<button class="icon-control search-control" aria-label="Search course" title="Search course">
  <svg aria-hidden="true" viewBox="0 0 24 24">...</svg>
</button>
```

There must be no visible text node inside `.search-control`.

# 3. Deterministic Google-Default Voice Selection

Every supported locale must target Google as its generated default voice provider.

Supported locale targets:

- English: exact-locale Google English, preferably `Google US English`;
- Simplified Chinese: exact-locale Google Mandarin/普通话;
- Traditional Chinese: exact-locale Google 國語/Chinese Taiwan;
- Japanese: exact-locale Google 日本語/Japanese.

Required behavior:

1. Wait for `speechSynthesis.getVoices()` to populate and listen for `voiceschanged` before finalizing the default.
2. On first course load, select the highest-ranked matching Google voice for the active locale.
3. On language change, select the highest-ranked matching Google voice for the new locale.
4. Do not default to the first operating-system voice, the first alphabetical voice, Samantha, Microsoft, Apple, or a previously cached arbitrary voice when a matching Google voice is available.
5. A non-Google voice may override the default only after an explicit learner selection.
6. Persist an explicit learner selection separately from the generated default provider preference.
7. If no matching Google voice is exposed by the current browser/OS, use the existing quality-ranked fallback and record the fallback in the QA Report. Do not pretend an unavailable voice exists.

Recommended state model:

```js
const DEFAULT_VOICE_PROVIDER = 'google';
let explicitVoiceChoice = false;

function chooseDefaultVoice(locale, voices) {
  const exactGoogle = voices
    .filter(v => isGoogleVoice(v) && normalizeLocale(v.lang) === normalizeLocale(locale))
    .sort((a, b) => qualityScore(b, locale) - qualityScore(a, locale));

  if (exactGoogle.length) return exactGoogle[0];

  const languageGoogle = voices
    .filter(v => isGoogleVoice(v) && sameLanguage(v.lang, locale))
    .sort((a, b) => qualityScore(b, locale) - qualityScore(a, locale));

  return languageGoogle[0] || chooseExistingQualityFallback(locale, voices);
}
```

QA must confirm that each locale selects Google by default whenever the runtime exposes a matching Google voice.

# 4. Center Every Control Icon Precisely

All icons in header and footer controls must be optically and geometrically centered.

This applies to:

- language icon;
- Auto Play/Video icon;
- Fullscreen icon;
- Previous and Next arrows;
- Search icon;
- narration icon;
- Audio settings icon;
- Course Menu icon and any other control icon.

Required CSS pattern:

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

.icon-control {
  padding: 0;
  line-height: 0;
}
```

Rules:

- Do not position icons with arbitrary `top`, `left`, negative margins, baseline nudges, or translate offsets unless a documented optical correction is required for that exact SVG.
- Icon-only controls use `padding: 0` and center the SVG in both axes.
- Icon-plus-label controls center the combined icon-and-label group inside the button.
- SVG `viewBox` must be tight enough that invisible whitespace does not make the icon appear off-center.
- All icons must be visually inspected at 1920×1080, 1600×900, and 1366×768.
- An obviously off-center icon is a release-blocking UI defect.

# 5. Enforce a Larger Body-Text Floor

All learner-facing instructional body text must remain comfortably readable. This section supersedes the lower body-copy targets in `COURSE_EXPERIENCE_SPEC.md` and older UI examples.

Recommended desktop typography:

```css
:root {
  --body-primary: clamp(24px, 1.65vw, 31px);
  --body-secondary: clamp(22px, 1.4vw, 27px);
  --body-compact: clamp(20px, 1.15vw, 23px);
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

Desktop rules:

- At 1366×768, ordinary instructional body text must not fall below `20px`.
- Important explanatory text, answer options, steps, bullets, and card body copy should normally be `22px` or larger.
- Only true non-instructional metadata, such as page count or compact system status, may be smaller than `20px`.
- Do not classify useful learning content as metadata merely to shrink it.
- Do not shrink text to solve overflow. Shorten wording, redesign the composition, or split the scene.
- Preserve the established large-title hierarchy; larger body text must not reduce hero or scene-title emphasis.

Responsive rules:

- Tablet instructional body text should normally remain at least `18px`.
- Phone instructional body text should normally remain at least `17px`, with scene splitting preferred over further reduction.
- Desktop remains the visual-quality master.

Recommended QA scan for the active learner stage:

```js
function findUndersizedInstructionalText(scene) {
  const selectors = [
    '.scene-lead', '.hero-description', '.question-text', '.explanation-text',
    '.card-body', '.step-body', '.answer-option', '.supporting-copy',
    '.bullet-item', '.warning-body', '.procedure-copy', '.technical-note'
  ];

  return [...scene.querySelectorAll(selectors.join(','))].filter(el => {
    const style = getComputedStyle(el);
    return el.getClientRects().length && parseFloat(style.fontSize) < 20;
  });
}
```

Any desktop learner scene containing undersized instructional body text fails QA.

# 6. Targeted QA Checklist

In addition to all existing QA, verify:

- the entire learner stage remains deep navy and no pale full-page canvas is present;
- localized light cards and image frames remain bounded components;
- the footer action order is Previous → Next → Search → narration → Audio settings;
- Search is icon-only with no visible label;
- each available locale defaults to a matching Google voice;
- explicit user voice choices are distinguished from generated defaults;
- every header and footer icon is centered in both axes;
- all desktop instructional body text meets the `20px` minimum and important body copy meets the larger target;
- no other established design or behavior changed.

# 7. Scope Lock

Version 2.4.1 changes only:

1. restoration and enforcement of the deep-navy learner-stage background;
2. icon-only Search placement after Next;
3. deterministic Google-default voice selection;
4. centering of all control icons;
5. a stricter learner-facing body-text minimum.

Do not alter the approved header lockup, module hierarchy, responsive priority, assessment consolidation, Auto Play assessment behavior, global Next availability, button dimensions, image-integrity rules, source grounding, multilingual content policy, colors, or any other established behavior except where this file explicitly requires it.