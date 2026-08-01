---
name: micas-doc-to-interactive-training
display_name: Micas Doc-to- Interactive-Training Skill
description: Convert manuals, SOPs, product guides, policies, and technical documents into source-grounded, Micas-branded, self-contained interactive training courses with polished UI, four-language support, narration, quizzes, progress tracking, hidden course navigation, and offline delivery.
version: 2.0.0
---

# Micas Doc-to- Interactive-Training Skill

## Purpose

Transform static technical documents into an engaging, accurate, and reusable interactive course—not a page-by-page summary, document viewer, or slide deck with narration.

The default deliverable is a **single self-contained offline HTML file** that opens in modern Chrome or Edge without a server. It combines instructional design, source visuals, multilingual content, narration, interactions, assessment, progress tracking, and a polished Micas visual system.

## Default Project Settings

Unless the user explicitly overrides them, use these defaults:

- **Brand:** Micas Networks
- **Primary brand color:** `#00899F`
- **Visual direction:** dark, premium, technical, spacious, mission-oriented
- **Default language:** English
- **Supported languages:** English, Simplified Chinese, Traditional Chinese, Japanese
- **Locale keys:** `en`, `zh-CN`, `zh-TW`, `ja`
- **Output:** one offline HTML file plus course map, QA report, and README
- **Navigation:** complete course directory hidden by default in an overlay drawer
- **Narration:** browser Web Speech API with locale-aware voice selection
- **Tone:** professional, practical, engaging, not childish

When inputs are incomplete, infer reasonable values from the source and continue without unnecessary clarification. Explicitly record assumptions in the QA report.

## Non-Negotiable Source-Grounding Rules

1. Treat supplied source files as the primary and authoritative basis.
2. Read complete relevant sections, including tables, figures, captions, warnings, procedures, appendices, screenshots, and embedded images.
3. Preserve terminology, product names, numerical values, safety limits, procedural order, and operational boundaries.
4. Do not silently invent, correct, reconcile, or supplement missing technical facts.
5. If two source passages conflict, flag the inconsistency for review instead of choosing one silently.
6. Distinguish source-derived content from instructional wording, inference, or external research.
7. Represent safety-critical steps, electrical limits, laser safety, ESD controls, lifting rules, and restricted maintenance procedures accurately and prominently.
8. Do not turn dangerous operations into playful interactions that reduce perceived risk.
9. Maintain traceability: every scene, question, and answer must map to a source page, heading, table, or figure.

## Production Workflow

### Phase 1 — Source Audit

Read and inspect the full source material, including embedded visuals. Build an internal source map containing:

- Document hierarchy and table of contents
- Intended audience and prerequisites
- Key concepts and specifications
- Procedures and exact sequence
- Safety warnings and prohibited actions
- Reusable visual assets
- Troubleshooting symptoms, checks, and resolutions
- Repeated or low-value reference content
- Ambiguities, contradictions, and suspected source errors

Do not build a complete course from isolated snippets when the surrounding chapter is relevant.

### Phase 2 — Learning Architecture

Convert the document hierarchy into a learning journey. Do not create one scene per document page.

Use this hierarchy:

- **Course:** complete learning goal
- **Module:** one coherent competence area
- **Scene:** one focused learning objective, normally 30–90 seconds of narration
- **Interaction:** identification, decision, sequencing, matching, or diagnosis
- **Assessment:** module checks plus final challenge

Recommended technical-course pattern:

1. Course orientation and outcomes
2. Product positioning and hardware anatomy
3. Interfaces, indicators, power, airflow, and key specifications
4. Safety and site preparation
5. Unpacking and installation readiness
6. Installation and connection workflow
7. Commissioning and verification
8. Monitoring and maintenance
9. Troubleshooting scenarios
10. Final assessment and completion

Adapt the pattern to the source instead of forcing irrelevant sections.

### Phase 3 — Content Prioritization

Classify content as:

- **Must perform:** procedures, checks, limits, and safety actions
- **Must recognize:** ports, LEDs, modules, labels, symptoms, and states
- **Must understand:** architecture, airflow, redundancy, dependencies, and rationale
- **Reference only:** exhaustive pin tables, dimensions, regulations, or rarely used appendices

Actively teach the first three. Place reference-only content in searchable, expandable reference scenes instead of narrating every row.

### Phase 4 — Scene Design

Each scene should usually contain:

- Mission or context label
- One clear title
- One short explanation or learning objective
- Three to five key points maximum
- One authentic source image, diagram, simplified visual, or interaction when useful
- Dedicated narration written for listening
- Optional checkpoint
- Prominent warning block when supported by the source

Use varied layouts:

- Premium hero/cover scene
- Image plus explanation
- Hardware hotspot map
- Front/rear panel identification
- Step-by-step timeline
- Do / Do-not comparison
- Specification chips or cards
- Troubleshooting decision path
- Scenario question
- Final score and completion screen

Avoid dense document-like pages and oversized blank panels. Split complex procedures into multiple scenes.

## Micas UI Design Standard

The UI must visually follow the successful preview style: unified dark-blue environment, large high-impact title, carefully framed product imagery, restrained cyan accents, rounded translucent cards, and strong spatial balance.

### Required Design Tokens

Use CSS custom properties and derive secondary tones from the Micas primary color.

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
  --micas-radius-lg: 24px;
  --micas-radius-md: 16px;
  --micas-shadow: 0 18px 60px rgba(0, 0, 0, 0.28);
}
```

### Visual Composition Rules

1. Keep the header, stage, footer, and controls within one coherent dark visual system.
2. Do **not** introduce a sudden full-width white main panel. White or near-white may appear only in controlled areas such as a product-image frame, chart canvas, printable reference, or focused modal.
3. Prefer dark or blue-tinted cards with subtle borders and glass-like depth.
4. Use large typography and generous spacing rather than filling the screen with many small elements.
5. The first scene should generally use a two-column hero layout:
   - Left: mission label, large title, brief promise, three learning-goal cards
   - Right: product or process visual in a rounded framed panel with concise specification chips
6. Keep animations restrained: short fades, slide-ins, progress changes, hotspot pulses, and subtle hover elevation.
7. Maintain high contrast and clear focus states.
8. Avoid decorative emoji as primary UI icons in formal courses; use consistent inline SVG icons where possible.

### Logo Integration Rules

1. Use a transparent-background Micas logo or a version specifically designed for dark backgrounds.
2. Never place a white rectangular logo image directly on the dark header when it creates a visible white block.
3. If only a white-background logo is available:
   - crop excess whitespace;
   - create a transparent version only when it can be done without changing the logo;
   - otherwise place it inside a deliberately designed compact logo plaque that matches the UI, not an accidental white rectangle.
4. Preserve aspect ratio; never stretch, recolor, or distort the logo.
5. Keep the logo visually integrated with the header, typically 34–56 px high depending on viewport.

### Navigation Rules

The complete course directory is valuable, but it must **not remain permanently visible during teaching or presentation**.

Required behavior:

- Hide the directory by default on all screen sizes.
- Provide a compact top-left **Course Menu** button with an accessible English `aria-label`.
- Open the directory as an overlay drawer or modal sheet.
- The drawer may show modules, scene counts, completion state, search, and quick jump.
- Close it by selecting a scene, pressing Escape, clicking the backdrop, or using a close button.
- In fullscreen and video mode, keep it closed unless the learner explicitly opens it.
- Do not reserve permanent horizontal space for the hidden directory.

### Main Stage Rules

- The stage should be visually centered and use the available width.
- Use a dark base with cards, images, or panels layered inside it.
- Avoid a large empty white rectangle.
- Keep scene content within a readable maximum width while allowing wide diagrams and product images.
- Keep previous/next controls and progress visually secondary to the learning content.

## Four-Language Standard

Every course must support these locales unless explicitly overridden:

| Locale key | Language | TTS preference |
|---|---|---|
| `en` | English | `en-US` or best available English voice |
| `zh-CN` | 简体中文 | `zh-CN` |
| `zh-TW` | 繁體中文 | `zh-TW` |
| `ja` | 日本語 | `ja-JP` |

Rules:

1. English is always the default on first load.
2. The language control is a compact dropdown button whose visible button label remains **`Language`** in English in every locale.
3. Dropdown options must be exactly or equivalently presented as:
   - English
   - 简体中文
   - 繁體中文
   - 日本語
4. Do not use a large language toggle or two-language-only switch.
5. Localize scene titles, body text, narration, questions, answer choices, feedback, transcripts, module names, and completion messages.
6. Keep technical product names, commands, port labels, and standard identifiers unchanged where translation would reduce accuracy.
7. Store four independent authored language versions. Do not rely on runtime machine translation.
8. Persist the learner's selected language, but use English when no preference exists.
9. Map narration to locale-specific voices and provide a graceful fallback when a voice is unavailable.

Recommended data model:

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
        en:    { title: '', body: '', narration: '', question: null },
        'zh-CN': { title: '', body: '', narration: '', question: null },
        'zh-TW': { title: '', body: '', narration: '', question: null },
        ja:    { title: '', body: '', narration: '', question: null }
      }
    }
  ]
};
```

## Visual Asset Treatment

Reuse authentic source figures whenever possible.

- Crop page margins and unrelated text.
- Preserve labels and aspect ratio.
- Add highlights, numbered markers, arrows, callouts, or zoom areas only when they improve learning.
- Do not alter product appearance or invent ports and components.
- Provide alt text in all supported languages when practical.
- Compress images to WebP or optimized PNG/JPEG.
- Embed assets as data URIs for single-file output.
- When source images are inadequate, create simple schematics rather than photorealistic invented equipment.

## Narration Standard

Write a dedicated narration script for every locale and scene.

- Explain meaning and action; do not read screen text verbatim.
- Use short natural spoken sentences.
- Expand abbreviations on first use when appropriate.
- Format numbers for clear TTS pronunciation.
- Keep one scene focused on one objective.
- Explain the reason behind critical steps when the source supports it.
- Never dilute warnings.
- Cancel speech immediately when the learner changes scenes or language.

## Interaction Standard

Use realistic interactions:

- Identify a port, module, LED, or cable
- Choose the correct procedural sequence
- Diagnose a symptom
- Select the safest next action
- Match a status indication to its meaning
- Distinguish acceptable and unacceptable site conditions

Every question must include:

- One unambiguous source-supported correct answer
- Plausible distractors
- Immediate explanatory feedback in all supported languages
- Source mapping in production notes

Avoid trivia that does not improve field performance.

## HTML Implementation Requirements

The default artifact is a self-contained HTML application with no external CDN or network dependency.

Required features:

- Responsive desktop, tablet, and mobile layout
- Hidden course directory drawer
- Compact `Language` dropdown with four languages
- English default locale
- Current scene title, scene counter, and progress bar
- Previous and next controls
- Left/right keyboard navigation
- Fullscreen mode
- Course search inside the hidden drawer or a compact overlay
- Per-scene narration using the Web Speech API
- Locale-aware voice selector
- Automatic presentation/video mode
- Immediate quiz feedback
- Final assessment and score
- `localStorage` persistence for language, progress, audio settings, and relevant learning state
- Visible transcript or equivalent screen content when speech is unavailable
- Accessible contrast, focus states, semantic controls, alt text, Escape behavior, and ARIA labels
- No external CDNs, web fonts, scripts, or image URLs in the final offline file

Recommended auto-mode behavior:

- Use minimum scene time plus narration-length estimate.
- Pause at interactions requiring learner input.
- Cancel current speech when scenes or locale change.
- Keep navigation drawer closed during playback.

## Responsive Behavior

- **Large screens:** hero or content stage uses the full width; no permanently docked sidebar.
- **Medium screens:** two-column scenes may collapse to balanced stacked sections.
- **Mobile:** header controls compress into icon buttons, cards stack, touch targets remain at least 44 px, and the course directory opens full-screen or nearly full-screen.
- Prevent horizontal scrolling except inside intentionally scrollable tables.

## Quality Assurance

Before delivery, verify:

### Source Accuracy

- Technical values match the source.
- No unsupported capabilities are introduced.
- Procedures preserve order.
- Warnings are present and prominent.
- Questions and feedback are source-supported.
- Source conflicts are flagged.

### UI and Brand

- Micas primary color is `#00899F`.
- Logo is visually integrated and has no accidental white box.
- Main stage has no abrupt oversized white area.
- Preview-style dark composition is maintained across all scenes.
- Cards, borders, chips, buttons, and progress indicators use a consistent token system.
- Course directory is hidden by default and works as a drawer.
- Fullscreen and video mode do not expose the drawer automatically.

### Language

- First load is English.
- `Language` button label remains English.
- English, 简体中文, 繁體中文, and 日本語 are selectable.
- All scene content, narration, questions, feedback, and completion messages have four versions.
- Voice selection follows the active locale and falls back gracefully.

### Functional Tests

- Previous/next and keyboard navigation work.
- Progress persists after refresh.
- Drawer open/close and Escape behavior work.
- Language persists after refresh.
- Speech stops when changing scene or language.
- Video mode pauses correctly for interactions.
- Search finds scenes in the current locale and preferably all locales.
- Quizzes score correctly.
- Fullscreen works where the browser permits.
- The final file opens offline with no missing assets.

### Accessibility

- Contrast is adequate.
- Focus states are visible.
- Controls have accessible names.
- Drawer traps focus while open and restores focus when closed.
- Dialogs and feedback are keyboard accessible.
- Images have alt text.
- Reduced-motion preferences are respected.

## Required Deliverables

Create and attach:

1. `[COURSE_NAME]_Interactive_Training.html`
2. `[COURSE_NAME]_Course_Map.md`
3. `[COURSE_NAME]_QA_Report.md`
4. `[COURSE_NAME]_README.md`

The course map must list modules and scenes with learning objectives and source mapping.

The QA report must include:

- Technical values checked
- Warnings preserved
- Four-language completeness
- UI/brand acceptance checks
- Functional tests completed
- Source inconsistencies or uncertain points
- Browser and TTS limitations

## Completion Standard

The result must feel like a premium Micas interactive technical course suitable for:

- Self-study
- Instructor-led classroom presentation
- Fullscreen/video-style playback
- Quick field reference

Do not stop at an outline or prototype when the user asks for a complete course. Generate the complete artifacts and provide download links.
