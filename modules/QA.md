# Unified QA and Release Gate

Version: **3.5.0**

This module validates every generated artifact after the selected Core, Mode, Brand, and UI modules have been applied.

# 1. Source Accuracy QA

Verify:

- complete relevant source sections were read;
- terminology, product names, commands, numerical values, warnings, and procedure order match the source;
- every technical claim has source support;
- every graded question and answer maps to the source;
- source conflicts and ambiguities are recorded rather than silently resolved;
- safety-critical information is prominent and accurate;
- source mapping exists outside the normal audience-facing pages;
- the opening scene headline, summary, content anchors, and visual are derived from the actual source topic;
- learner-facing pages do not replace source content with project configuration or delivery metadata;
- any visible claim about capability, use case, workflow, safety, value, or outcome is supported by the source.

# 2. Artifact Completeness QA

Verify:

- all requested deliverables exist;
- the primary artifact opens and functions without missing files;
- embedded or local assets resolve correctly;
- no placeholder content remains;
- no partial prototype is delivered when a complete artifact was requested;
- README and QA Report explain usage, limitations, and fallbacks.

# 3. Viewport and Overflow QA

For presentation-style modes, test at 100% browser zoom:

- 1920×1080;
- 1600×900;
- 1366×768.

Also test representative non-Fullscreen browser-content viewports after browser chrome reduces the available document height:

- 1920×930;
- 1600×780;
- 1366×650.

Then test representative responsive sizes:

- tablet landscape: 1180×820 or 1024×768;
- tablet portrait: 820×1180 or 768×1024;
- phone portrait: 430×932 and 390×844.

For every required page and locale:

- use the actual `window.innerWidth` and `window.innerHeight` available to the document;
- wait for fonts and images;
- render the page;
- verify `scene.scrollHeight <= scene.clientHeight + 1` when the selected mode requires one-screen behavior;
- verify the document does not scroll vertically in normal learner/presentation mode;
- verify header and footer remain visible;
- verify no horizontal clipping;
- verify the lowest card row, captions, warnings, answer choices, and actions remain fully visible above the footer;
- verify overlays scroll internally without moving the underlying page;
- verify no visible diagnostic or overflow banner appears;
- verify Fullscreen is not required to reveal hidden content.

Do not pass QA by changing the approved fixed header/footer controls. Shorten, rebalance, or split the middle-scene content instead.

# 4. Typography QA

For the default interactive-training UI:

- ordinary desktop instructional body text is at least `20px` at 1366×768;
- important explanations, answer options, steps, bullets, and card body copy are normally `22px` or larger;
- tablet instructional text is normally at least `18px`;
- phone instructional text is normally at least `17px`;
- useful learning content is not misclassified as metadata to shrink it;
- overflow is solved by wording, layout, or page splitting rather than unreadably small text;
- title hierarchy remains visually stronger than body copy.

# 5. Visual Hierarchy and Stage Utilization QA

Confirm:

- every page has one obvious focal point;
- the layout is not a repetitive flat grid across most pages;
- two-column layouts contain meaningful content in both columns;
- no empty image frame, blank card, placeholder panel, or missing half-page remains;
- meaningful composition uses the stage effectively;
- intentional whitespace supports the focal message;
- the selected brand's stage theme, colors, and surface rules are respected;
- the opening scene communicates the real training subject rather than the course-generation framework;
- the opening scene uses one to three meaningful, source-supported content anchors;
- course duration, language count, difficulty, delivery format, file type, QA status, and similar configuration values are not used as homepage teaching cards unless explicitly required by the source or user;
- the opening visual is the most relevant authentic source visual available, not a generic acronym tile, abstract placeholder, or decorative icon when a real product/process/architecture image exists;
- opening text and visual form one balanced, attractive composition.

# 6. Image Integrity QA

After all images load and decode, verify:

- nonzero natural dimensions;
- meaningful rendered dimensions;
- full visibility inside the page and viewport;
- no ancestor clips the image;
- technical visuals use `object-fit: contain`;
- the complete device, diagram, labels, arrows, and callouts remain visible;
- source margins and irrelevant page whitespace were removed;
- labels remain readable;
- intentional detail crops are labeled and paired with a complete view;
- the opening image is genuinely relevant to the source topic and large enough to identify the subject immediately.

A missing, half-visible, unintentionally cropped, generic-placeholder, or source-irrelevant opening visual blocks release when a suitable source image was available.

# 7. Header, Footer, and Icon QA

Verify:

- selected brand lockup is intact and readable;
- utilities do not overlap or compress the brand area;
- visible language value has no unnecessary `Language` prefix;
- header utility icons are appropriate and accessible;
- all icons are geometrically and optically centered;
- desktop controls remain substantial and easy to hit;
- the selected mode's control order is correct;
- the default interactive-training order is Previous → Next → Search → narration → Audio settings;
- Search is icon-only;
- the right-side action cluster remains right-aligned;
- progress remains prominent.

For v3.5.0 content refinements, the approved Micas top and bottom control rails are regression-locked. Do not alter their established dimensions, control order, button shells, icon sizes, spacing, or typography to solve middle-scene content issues.

# 8. Navigation QA

For interactive training:

- Next is enabled on every nonterminal scene;
- module-ending scenes advance to the next module;
- unanswered assessment questions do not block Next;
- Previous is enabled except on the first scene;
- visible controls, keyboard navigation, and Auto Play call the same navigation functions;
- score, feedback, answer, narration, animation, and completion state do not gate global scene navigation;
- only the absolute terminal completion scene disables or replaces Next.

# 9. Narration and Voice QA

Verify for each supported locale:

- the runtime voice list is allowed to populate before default selection;
- `voiceschanged` is handled;
- a matching Google voice is selected by default whenever exposed by the browser/OS;
- arbitrary OS, alphabetical, cached, Microsoft, Apple, or Samantha defaults do not override an available Google voice;
- explicit learner voice choice is stored separately from generated default preference;
- no more than three curated voices are shown;
- unavailable voices are not fabricated;
- fallback is documented when Google is unavailable.

# 10. Auto Play QA

For normal narrated pages:

- the page remains visible until the final narration chunk completes;
- `goNext()` is not called before the final `onend`;
- pause/resume pauses and resumes transition correctly;
- narration errors stop Auto Play on the current page;
- manual navigation cancels and invalidates active narration;
- stale callbacks cannot cause duplicate advances;
- pages intentionally without narration use only the configured short dwell.

For graded assessment pages:

- Auto Play pauses at the assessment introduction;
- questions are not narrated automatically;
- no dwell timer, auto-submit, or auto-advance runs;
- the learner answers and navigates manually.

# 11. Assessment QA

For the default interactive-training mode:

- all graded questions are in the final Review & Assessment module;
- instructional modules do not end with separate graded exams;
- the dedicated assessment-introduction page exists;
- question count, duration, scoring, and instructions are clear;
- every question maps to the source;
- correct, incorrect, and unanswered states work;
- revisiting questions preserves state;
- results, feedback, and completion work.

# 12. Search QA

Verify:

- Search covers the complete active-language content;
- module titles, scene titles, body text, warnings, procedures, keywords, and assessment content are indexed;
- Search works offline;
- results are grouped and localized;
- the current page does not change until a result is selected;
- result selection navigates correctly;
- Escape, keyboard focus, Enter, and accessible result counts work;
- the search panel scrolls internally only.

# 13. Multilingual QA

For every supported locale:

- all required content is authored and complete;
- technical meaning remains equivalent;
- commands, model names, and standards remain accurate;
- fit, image, control, search, narration, assessment, and accessibility checks pass;
- English remains the strongest visual master unless another locale was explicitly selected;
- locale-specific layout variants do not remove content.

# 14. Responsive QA

Confirm:

- desktop quality is perfected first;
- tablet and phone remain usable without overlap, clipped images, inaccessible controls, or missing content;
- compact controls and stacked layouts activate only at appropriate breakpoints;
- responsive adaptation does not shrink the desktop master unnecessarily;
- touch targets remain large enough;
- overlays and drawers remain usable.

# 15. Accessibility QA

Verify:

- keyboard navigation;
- visible focus states;
- accessible names for icon-only controls;
- meaningful alt text;
- Escape behavior for overlays;
- contrast;
- reduced-motion support;
- no color-only state communication;
- screen-reader-friendly structure where applicable.

# 16. Release-Blocking Defects

Do not deliver when any of these occurs:

- unsupported or invented technical fact;
- visible `Layout overflow detected` or similar diagnostic;
- normal presentation page scrolls or overflows;
- content fits only after entering Fullscreen;
- content is clipped in a browser-content viewport such as 1366×650;
- missing or half-visible technical image;
- a generic or irrelevant opening visual is used while a suitable source visual exists;
- the opening scene is dominated by duration, language count, difficulty, Offline HTML, file type, QA status, or other project metadata rather than the real training subject;
- large accidental empty region or blank panel;
- undersized instructional body text;
- tiny or off-center primary controls;
- selected brand identity is broken;
- the approved fixed header/footer controls are altered merely to make middle-scene content fit;
- Next is disabled while a following scene exists in interactive-training mode;
- Auto Play advances before narration completes;
- stale narration callback causes duplicate advance;
- graded question is skipped automatically;
- final assessment lacks its transition page;
- per-module graded exams appear when the selected mode requires final-only assessment;
- Search is broken or not offline;
- source mapping, debug data, or authoring metadata is visible in normal audience mode;
- required local asset is missing;
- the artifact cannot be used as delivered.

# 17. QA Report

The QA Report must record:

- source coverage and unresolved source issues;
- selected brand and mode;
- opening-scene content and visual source;
- viewport results, including constrained browser-content viewports;
- typography results;
- image-integrity results;
- stage-utilization review;
- navigation and control review;
- voice availability and fallback;
- Auto Play and assessment behavior;
- search results;
- multilingual completeness;
- responsive and accessibility checks;
- any known limitation.

# 18. Micas Approved-Shell Regression QA

When `brand_profile: micas` and `training_mode: interactive-training` are active, verify every desktop build against:

- `modules/brands/micas/references/header-lockup-reference.svg`;
- `modules/brands/micas/references/top-right-controls-reference.svg`;
- `modules/brands/micas/references/footer-fixed-controls-reference.svg`.

Mandatory checks:

- the left header contains the official Micas logo, a large primary title, and a visibly smaller subtitle below it;
- the subtitle is not missing, hidden, clipped, or merged into the primary title;
- the right header contains Language → Auto Play → Fullscreen in that order;
- Language has an appropriate icon and dropdown indicator;
- Auto Play and Fullscreen are visible in normal desktop mode;
- progress/module/question counters do not replace the right-header controls;
- the footer contains Course Menu, scene count, visible progress, Previous, Next, Search, narration, and Audio settings in the approved grouping and order;
- the footer does not cover scene content;
- each scene fits at 1920×1080, 1600×900, 1366×768, 1920×930, 1600×780, and 1366×650 without requiring Fullscreen;
- cards, source previews, images, assessment results, and explanatory text remain fully visible above the footer;
- a complete technical image is never clipped by a fixed-height container;
- semantic highlights are restrained, attractive, and limited to brand cyan, warning amber, success green, and genuine danger red;
- highlighted meaning remains understandable without color alone;
- the approved header/footer rails remain unchanged by v3.5.0 homepage and fit refinements.

The following are release-blocking regressions:

- missing desktop subtitle;
- missing Auto Play or Fullscreen button;
- language selector without its icon;
- progress controls moved into the right header in place of utilities;
- footer reduced to a materially smaller or different control strip than the approved reference;
- any page that reveals hidden content only after entering Fullscreen;
- content, image, results panel, or captions clipped behind the footer;
- opening-scene metadata cards unrelated to the real training topic;
- opening scene lacks a relevant source visual when one exists;
- excessive or visually conflicting highlight colors.
