# Master Prompt — Micas Doc-to- Interactive-Training

Copy this prompt, attach the source documents, and replace bracketed project variables where needed.

---

You are an instructional designer, technical trainer, UX designer, multilingual content engineer, and front-end developer.

Transform the attached source documents into a complete, source-grounded, premium Micas interactive training course.

## Project Settings

- Course title: `[AUTO-GENERATE OR ENTER TITLE]`
- Target audience: `[AUDIENCE]`
- Learning goal: `[LEARNING GOAL]`
- Desired duration: `[E.G. 30–45 MINUTES]`
- Assessment level: `[BASIC / INTERMEDIATE / CERTIFICATION-STYLE]`
- Output: `[DEFAULT: ONE SELF-CONTAINED OFFLINE HTML FILE]`
- Brand: `Micas Networks`
- Primary brand color: `#00899F`
- Default language: `English`
- Required languages: `English / 简体中文 / 繁體中文 / 日本語`
- Tone: `Professional, practical, engaging, not childish`

## Source and Accuracy Rules

1. Use the attached files as the primary and authoritative basis.
2. Read complete relevant documents, including tables, diagrams, screenshots, warnings, procedures, appendices, and embedded images.
3. Preserve exact terminology, product names, numerical limits, procedure order, warnings, and operational boundaries.
4. Do not silently add unsupported claims or correct suspected source errors.
5. If the source is ambiguous or inconsistent, flag it in the QA report and avoid inventing a resolution.
6. Maintain a source map from every scene and assessment item to a source section, page, table, or figure.
7. Preserve the seriousness and exact action of safety-critical content.

## Instructional Design Requirements

Do not convert the document page by page. Reorganize it into a coherent learning journey.

Create:

- Welcome and learning outcomes
- Competency-based modules
- Focused scenes, each teaching one primary objective
- Authentic visual explanations using source figures
- Step-by-step procedures for operational tasks
- Realistic troubleshooting and safety decisions
- Short knowledge checks after major modules
- Final assessment with score and explanatory feedback
- Completion scene and review guidance

Prioritize:

- What the learner must perform
- What the learner must recognize
- What the learner must understand
- Keep reference-only detail searchable but do not narrate every row

## Mandatory UI Direction

The course must visually follow a unified preview-style Micas design:

- Dark navy full-page environment
- Micas cyan `#00899F` as the primary accent
- Large high-impact titles and generous spacing
- Rounded dark or blue-tinted translucent cards
- Authentic product/process imagery in intentionally designed frames
- Coherent header, stage, and footer
- Restrained professional animation

Do not create a generic LMS appearance.

### Forbidden UI Outcomes

- A white rectangular logo image dropped onto the dark header
- A dominant plain-white main content block
- A permanently visible left course directory
- A two-language-only toggle
- A language button translated away from English
- Generic blue that replaces the Micas primary color

### Logo

- Use a transparent Micas logo suitable for a dark header.
- Preserve aspect ratio and clear space.
- If only a white-background logo is available, crop excess whitespace and create a transparent version only when safe; otherwise use a deliberately designed compact plaque rather than an accidental white box.

### Course Directory

- Hide the complete course directory by default.
- Add a compact header menu button.
- Open the directory as an overlay drawer/modal sheet.
- Include module list, scene count, progress, search, and quick jump.
- Close it after selection, on Escape, on backdrop click, or with a close button.
- Keep it closed during normal teaching, fullscreen, and Video mode unless explicitly opened.

### Main Stage

- Use available width; do not reserve permanent space for navigation.
- Keep a dark background across the main stage.
- Use blue-tinted cards and deliberate image frames.
- White is allowed only in controlled canvases such as a product-image frame, chart, table, or print/reference view—not as the entire scene background.

### Suggested Hero Layout

- Left: mission label, large title, short learning promise, three objective cards
- Right: product/process visual in a rounded frame plus concise specification chips

## Mandatory Language Requirements

Support exactly these four locales unless the project explicitly requests more:

- `en` — English
- `zh-CN` — 简体中文
- `zh-TW` — 繁體中文
- `ja` — 日本語

Rules:

1. English is the default on first load.
2. Use a compact dropdown whose visible button label is always `Language` in English.
3. Dropdown options are English, 简体中文, 繁體中文, 日本語.
4. Localize scene titles, body content, narration, module names, questions, answers, feedback, transcripts, and completion messages.
5. Keep product names, commands, standards, and port labels unchanged where translation would reduce technical accuracy.
6. Author independent language content. Do not rely on runtime machine translation.
7. Persist learner language selection, but fall back to English when no preference is stored.
8. Use locale-aware narration voices: `en-US`, `zh-CN`, `zh-TW`, and `ja-JP`, with graceful fallback.

Prefer a central data model:

```js
const courseData = {
  defaultLanguage: 'en',
  supportedLanguages: ['en', 'zh-CN', 'zh-TW', 'ja'],
  scenes: [
    {
      id: 'scene-01',
      moduleId: 'module-01',
      sourceRefs: ['p.1', 'Section 1.1'],
      content: {
        en: { title: '', body: '', narration: '', question: null },
        'zh-CN': { title: '', body: '', narration: '', question: null },
        'zh-TW': { title: '', body: '', narration: '', question: null },
        ja: { title: '', body: '', narration: '', question: null }
      }
    }
  ]
};
```

## Visual Asset Requirements

- Extract and reuse useful source images and diagrams.
- Crop page margins and unrelated text.
- Add numbered markers, highlights, arrows, callouts, or zooms when useful.
- Do not invent hardware features or modify products inaccurately.
- Optimize and embed all images so the final HTML works offline.
- Use responsive layouts: hero, image-plus-text, hotspot map, timelines, comparison cards, process flows, and troubleshooting paths.

## Narration Requirements

Create a separate natural narration script for every scene in all four languages.

- Explain rather than read screen text word for word.
- Use concise spoken sentences.
- Explain why critical steps matter when supported by the source.
- Make numbers and abbreviations easy for TTS.
- Cancel speech when changing scene or language.
- Never weaken a warning.

## Interaction Requirements

Include realistic work decisions such as:

- Identify the correct port, LED, module, cable, or status
- Put procedures in the correct order
- Choose the safest next action
- Diagnose a symptom from evidence
- Match an indicator with its meaning

Each question must have one source-supported answer, plausible distractors, immediate explanatory feedback, and source mapping.

## Technical Requirements

Generate one complete self-contained HTML file with embedded CSS, JavaScript, images, and course data. Do not rely on external CDNs, web fonts, scripts, or image URLs.

Include:

- Responsive desktop/tablet/mobile interface
- Hidden overlay course-directory drawer
- Compact fixed-English `Language` dropdown
- Four authored languages with English default
- Scene counter and progress bar
- Previous and Next controls
- Left/right keyboard navigation
- Fullscreen mode
- Search in a compact overlay or hidden drawer
- Browser Web Speech API narration
- Locale-aware voice selector
- Automatic presentation/Video mode
- Speech cancellation on navigation or language change
- Module completion state
- Immediate quiz feedback
- Final score and passing threshold
- `localStorage` persistence for progress, language, voice/audio settings, and relevant learning state
- Accessible buttons, focus states, contrast, alt text, drawer focus trap, Escape behavior, and reduced-motion support

## Micas CSS Tokens

Use or closely follow:

```css
:root {
  --micas-primary: #00899f;
  --micas-primary-bright: #29c5d8;
  --micas-primary-soft: #76e4ee;
  --micas-bg: #031f2b;
  --micas-bg-deep: #021720;
  --micas-surface: #0a3140;
  --micas-surface-raised: #123f4f;
  --micas-surface-glass: rgba(18, 63, 79, 0.72);
  --micas-border: rgba(118, 228, 238, 0.22);
  --micas-text: #f5fbfd;
  --micas-text-muted: #b7d4dc;
  --micas-success: #43d6a0;
  --micas-warning: #ffbf47;
  --micas-danger: #ff5d68;
}
```

## Required Deliverables

Create and attach:

1. `[COURSE_NAME]_Interactive_Training.html`
2. `[COURSE_NAME]_Course_Map.md`
3. `[COURSE_NAME]_QA_Report.md`
4. `[COURSE_NAME]_README.md`

The QA report must explicitly verify:

- Source accuracy and warnings
- `#00899F` primary color
- Integrated transparent logo treatment
- No dominant white main panel
- Hidden-by-default course directory
- English default
- Fixed-English `Language` button
- English, 简体中文, 繁體中文, 日本語 completeness
- Locale-aware narration behavior
- Offline asset completeness
- Functional and accessibility tests

Do not stop at an outline or prototype. Generate the complete requested artifacts and provide download links.

---
