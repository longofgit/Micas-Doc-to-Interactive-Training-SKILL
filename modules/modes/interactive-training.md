# Experience Mode: Interactive Training

Version: **3.5.0**

Mode ID: `interactive-training`

This is the default experience mode. It preserves the established Micas interactive-training behavior while separating it from brand and shared UI rules.

# 1. Purpose

Transform source documents into a complete interactive learning course—not a page-by-page summary, document viewer, generic LMS, or narrated document dump.

Default primary deliverable:

- one self-contained offline HTML course;
- Course Map;
- QA Report;
- course README.

The course supports self-study, instructor-led presentation, fullscreen delivery, field reference, narration, search, and final assessment.

# 2. Learning Architecture

Organize the content as a clear hierarchy:

```text
Course
  ├─ Module 1: Orientation / Why it matters
  │    ├─ Scene 1
  │    ├─ Scene 2
  │    └─ Scene 3
  ├─ Module 2: Recognition / Concepts
  ├─ Module 3: Preparation / Workflow
  ├─ Module 4: Operation / Installation
  ├─ Module 5: Troubleshooting / Maintenance
  └─ Final Module: Review & Assessment
```

Adapt module names and count to the source. Do not copy the source page order mechanically and do not create one flat list of dozens of scenes.

Each module must have a clear learning purpose and coherent sequence.

# 3. Scene Design

Each scene normally contains:

- module or mission label;
- one clear title;
- one short subtitle or promise;
- two to five supporting points;
- one dominant visual, number, action, warning, or decision;
- dedicated narration written for listening;
- optional ungraded interaction;
- source mapping stored outside learner view.

Recommended scene patterns:

- premium hero/cover;
- product positioning;
- hardware anatomy and hotspots;
- front/rear panel identification;
- oversized key metric;
- step timeline;
- do/do-not contrast;
- safety gate;
- troubleshooting decision path;
- procedure checkpoint;
- review/recap;
- assessment introduction;
- one-question assessment scene;
- results and completion.

## 3.1 Learner-Relevance Filter

Every learner-facing scene must teach, reinforce, demonstrate, or assess the actual subject of the source materials.

Do not place project-generation metadata into the instructional body merely because it is available in the prompt or configuration. The following items are not suitable homepage or teaching-card content unless the source itself teaches them or the user explicitly requests that they be shown to learners:

- course duration or estimated minutes;
- number of supported languages;
- default language;
- delivery format such as `Offline HTML`;
- file type or packaging details;
- assessment difficulty labels such as `Intermediate`;
- QA status, generation settings, output names, or implementation capabilities;
- generic statements about the course framework instead of the training topic.

These values may remain in the README, Course Map, QA Report, settings, or internal metadata. They must not displace real training content on the homepage or normal instructional scenes.

When selecting content for a scene, ask:

1. Does this help the learner understand or perform the real job/topic?
2. Is it supported by the source materials?
3. Is it important enough to occupy visible screen space?

If any answer is no, remove it from the learner-facing scene.

## 3.2 Source-Grounded Opening Scene

The first learner-facing scene must be a concise, visually strong introduction to the real training subject.

Required behavior:

- derive the headline, supporting statement, and visible content anchors from the source materials;
- communicate what the product, process, service, system, or task actually is and what the learner will be able to recognize, decide, install, operate, sell, maintain, or troubleshoot;
- use one to three source-supported content anchors, such as product positioning, major capability, real workflow, important safety condition, architecture, or field outcome;
- prefer specific source terminology over generic phrases such as `New Product Training` when a more meaningful topic statement is available;
- do not fill the opening scene with course duration, language count, difficulty, output format, or other delivery metadata;
- do not invent performance claims, market positioning, customer outcomes, or technical capabilities not supported by the source.

The opening visual must be the most relevant authentic visual available in the source materials, for example:

- the actual product or device;
- a real architecture or topology diagram;
- a genuine workflow/process illustration;
- a service-delivery scenario supported by the source;
- a source photo or diagram that immediately identifies the training subject.

Visual selection rules:

- use a real source image before creating a generic decorative illustration;
- do not substitute a generic acronym tile, abstract placeholder, empty visual frame, or decorative icon when a relevant authentic source image exists;
- crop irrelevant page margins, headers, footers, and whitespace before embedding;
- preserve the full meaningful image with `object-fit: contain`;
- size the visual large enough to establish the subject immediately;
- pair the visual and text as one balanced composition rather than two unrelated halves.

If no useful source image exists, use a restrained source-grounded diagram or typographic composition and state the limitation in the QA Report. Do not fabricate a realistic product image.

## 3.3 Normal Browser Window Fit

The course must fit a normal browser content viewport, not only Fullscreen mode or a screenshot-sized canvas.

Browsers normally reserve vertical space for tabs, the address bar, bookmarks, download bars, or operating-system chrome. Therefore:

- calculate the layout from the actual `window.innerHeight` / `100dvh` available to the document;
- keep the approved header and footer rails unchanged and fit the scene into the remaining middle grid row;
- never assume that a 768px-tall display provides 768px of document content height;
- do not use hard-coded scene heights derived from the physical monitor resolution;
- do not hide the final card row, image caption, warning, result, or action behind the footer;
- do not require Fullscreen to reveal content;
- when the normal viewport is shorter, shorten copy, rebalance the visual/text ratio, reduce nonessential scene padding, or split the content into another scene;
- do not solve the problem by shrinking instructional text below the approved minimums or by changing the locked header/footer controls.

In addition to the normal desktop master sizes, validate representative browser-content viewports such as:

- `1920×930`;
- `1600×780`;
- `1366×650`.

These values represent common screens after browser chrome consumes part of the vertical space. Every normal scene must remain complete and usable at 100% zoom.

# 4. Course Drawer and Progress

- The Course Menu is hidden by default.
- Its trigger is in the bottom-left control area.
- The drawer shows course → module → scene hierarchy.
- The drawer may scroll internally.
- It closes after selection, Escape, backdrop click, or close action.
- It must not reserve permanent stage width.
- Progress shows global scene position and meaningful module progress.

# 5. Global Sequential Navigation

The entire course is one ordered scene sequence.

1. Next is enabled whenever a following scene exists.
2. The final scene of a module advances directly to the first scene of the next module.
3. Previous is enabled on every scene except the first global scene.
4. Unanswered assessment questions do not block Next.
5. Answer validation, feedback, score, pass/fail, narration, animation, and module-completion state must not gate global navigation.
6. Only the absolute terminal completion scene may disable, hide, or replace Next.
7. Visible controls, keyboard arrows, and Auto Play use the same `goNext()` and `goPrevious()` functions.

Recommended logic:

```js
function updateNavigationState() {
  previousButton.disabled = currentSceneIndex <= 0;
  nextButton.disabled = currentSceneIndex >= scenes.length - 1;
}

function goNext() {
  if (currentSceneIndex < scenes.length - 1) {
    showScene(currentSceneIndex + 1);
  }
}
```

# 6. Footer Action Order

The right-side action cluster is:

```text
Previous → Next → Search → narration → Audio settings
```

Search is icon-only. Narration and Audio settings are icon controls. The cluster remains right-aligned.

# 7. Full-Course Search

Search covers the complete active-language course:

- module titles;
- scene titles;
- body text;
- procedures;
- warnings;
- technical keywords;
- assessment content.

Behavior:

- use an embedded offline index;
- open results in an overlay, modal sheet, or drawer;
- keep the current scene unchanged until a result is selected;
- group results by module;
- show localized snippets;
- navigate directly to the selected scene;
- support keyboard focus, Enter, Escape, and accessible result counts;
- highlight the matching term where practical.

# 8. Narration UI

The normal footer shows:

- one compact narration play/pause icon;
- one Audio settings icon.

Do not display a permanent voice name, large voice dropdown, or large `Narrate`/`语音讲解` text button in the footer.

Detailed settings open in a compact popover.

# 9. Google-Default Voice Selection

Supported targets:

- English: `en-US`, preferably `Google US English` or matching Google English;
- Simplified Chinese: `zh-CN`, Google Mandarin/普通话;
- Traditional Chinese: `zh-TW`, Google 國語/Chinese Taiwan;
- Japanese: `ja-JP`, Google 日本語/Japanese.

Required behavior:

1. Wait for `speechSynthesis.getVoices()` and `voiceschanged` before finalizing the generated default.
2. On first load, select the highest-ranked matching Google voice.
3. On language change, select the highest-ranked Google voice for the new locale.
4. Do not default to the first OS voice, alphabetical voice, Samantha, Microsoft, Apple, or an arbitrary cached voice when a matching Google voice exists.
5. A non-Google voice may override the default only after an explicit learner selection.
6. Persist explicit learner choice separately from the generated provider default.
7. If Google is unavailable, use the best exact-language quality-ranked fallback and record it in the QA Report and README.
8. Show no more than three curated voices per locale.
9. Never fabricate a voice that the browser does not expose.

# 10. Auto Play for Instructional Scenes

For normal instructional scenes:

- remain on the current scene until the complete narration finishes;
- advance only after the final narration utterance fires `onend`;
- never use a fixed timer, character count, estimated reading time, or animation duration while speech is active;
- play narration chunks sequentially;
- pausing speech pauses page transition;
- narration error stops Auto Play on the current scene;
- manual navigation cancels and invalidates active narration to prevent stale callbacks or duplicate advances;
- scenes intentionally without narration may use a short explicit visual dwell.

Recommended pattern:

```js
let autoPlayRunId = 0;

async function playCurrentSceneThenAdvance() {
  const runId = ++autoPlayRunId;
  const scene = getCurrentScene();

  if (isAssessmentQuestion(scene)) {
    stopAutoPlay();
    setPlaybackState('manual-assessment');
    return;
  }

  try {
    await playNarrationToCompletion(scene, runId);
    if (autoPlayEnabled && runId === autoPlayRunId) goNext();
  } catch (_) {
    stopAutoPlay();
  }
}

function cancelCurrentPlayback() {
  autoPlayRunId += 1;
  speechSynthesis.cancel();
}
```

# 11. Assessment Structure

All graded questions are consolidated in the final `Review & Assessment` module.

Instructional modules may include ungraded learning interactions such as:

- hotspots;
- reveal cards;
- reflection prompts;
- guided decisions;
- scenario exploration;
- practice without a chapter-exam score.

Do not add a separate graded examination at the end of every module.

The final module contains:

1. review/recap scenes;
2. a dedicated assessment-introduction scene;
3. all graded questions;
4. results, feedback, and completion scenes.

Every graded question must map to the source.

# 12. Assessment Introduction

Before the first graded question, show a dedicated transition scene with:

- confirmation that instruction is complete;
- assessment purpose;
- question count;
- approximate duration;
- passing score or scoring method;
- answer and feedback instructions;
- readiness message;
- clear `Start Assessment` action.

Auto Play pauses and waits on this scene.

# 13. Assessment and Auto Play

Graded questions are learner-controlled.

- Do not auto-narrate graded question pages.
- Do not start a dwell timer.
- Do not auto-answer, auto-submit, or auto-advance.
- Entering the first graded question suspends Auto Play and shows a manual-assessment state.
- The learner chooses answers and navigates manually.
- After completion, results and completion remain manual unless the learner explicitly restarts Auto Play.

A graded question skipped before the learner can answer is a release-blocking defect.

# 14. Feedback and Scoring

- Provide explanatory feedback supported by the source.
- Distinguish correct, incorrect, and unanswered states.
- Preserve unanswered questions when the learner navigates away.
- Allow revisiting questions.
- Show final score and completion status.
- Do not invent explanations beyond the source.

# 15. Persistence

Use `localStorage` for:

- current scene;
- selected language;
- explicit voice selection;
- answers and unanswered states;
- completion and score;
- optional captions and playback preferences.

Do not let stale saved state override a new course version without a versioned storage key.

# 16. Four-Language Delivery

Default languages:

- English;
- 简体中文;
- 繁體中文;
- 日本語.

Localize:

- module and scene titles;
- body content;
- narration;
- questions and choices;
- feedback;
- assessment transition;
- results and completion;
- tooltips and accessible labels.

# 17. Technical Output

Generate one self-contained offline HTML application with embedded:

- CSS;
- JavaScript;
- images and diagrams;
- course data;
- language content;
- offline search index.

Do not depend on external CDNs, scripts, web fonts, or runtime image URLs.

# 18. Required Deliverables

1. `[COURSE_NAME]_Interactive_Training.html`
2. `[COURSE_NAME]_Course_Map.md`
3. `[COURSE_NAME]_QA_Report.md`
4. `[COURSE_NAME]_README.md`
