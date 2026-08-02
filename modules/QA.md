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
- verify `document.documentElement.scrollWidth <= window.innerWidth + 1`;
- verify the document does not scroll vertically or horizontally in normal learner/presentation mode;
- verify header and footer remain visible;
- verify no horizontal clipping;
- verify every fixed header/footer control bounding box remains fully inside the viewport with the approved edge inset;
- verify the lowest card row, captions, warnings, answer choices, and actions remain fully visible above the footer;
- verify no scene grid, image, table, code sample, metric, translated string, or long technical token widens the fixed shell;
- verify overlays scroll internally without moving the underlying page;
- verify no visible diagnostic or overflow banner appears;
- verify Fullscreen is not required to reveal hidden content.

Do not pass QA by changing the approved fixed header/footer controls or by masking a width defect with document-level clipping. Shorten, rebalance, reflow, or split the middle-scene content instead.

# 4. Typography and Card-Fit QA

For the default interactive-training UI:

- ordinary desktop instructional body text is at least `20px` at 1366×768;
- important explanations, answer options, steps, bullets, and card body copy are normally `22px` or larger;
- tablet instructional text is normally at least `18px`;
- phone instructional text is normally at least `17px`;
- useful learning content is not misclassified as metadata to shrink it;
- overflow is solved by wording, layout, or page splitting rather than unreadably small text;
- title hierarchy remains visually stronger than body copy;
- every learner-facing card satisfies `scrollWidth <= clientWidth + 1` and `scrollHeight <= clientHeight + 1` after fonts load;
- metric values, dimensions, units, model names, commands, and translated text remain fully inside their cards;
- long values use meaningful line breaks, wider cards, fewer cards, or a different composition rather than crossing borders;
- a `2×2` card grid is used only when all four items fit comfortably;
- no card text is clipped, covered, ellipsized, or hidden merely to preserve a fixed layout.

# 5. Visual Hierarchy, Layout Diversity, and Stage Utilization QA

Confirm:

- every page has one obvious focal point;
- the layout is not a repetitive flat grid across most pages;
- the course does not repeat a left-text/right-image `50/50` split across most scenes;
- the same major composition is normally not repeated for more than two consecutive scenes unless the source requires it;
- scene composition is selected from actual content needs, including text-led, image-led, full-width visual, timeline, comparison, metric, warning, process, decision, and troubleshooting patterns;
- two-column layouts contain meaningful content in both columns;
- no image column is reserved when no meaningful visual exists;
- no empty image frame, blank card, placeholder panel, or missing half-page remains;
- light or white technical-image frames hug meaningful content and do not contain large accidental blank regions;
- meaningful composition uses the stage effectively;
- intentional whitespace supports the focal message;
- the selected brand's stage theme, colors, and surface rules are respected;
- the opening scene communicates the real training subject rather than the course-generation framework;
- the opening scene uses one to three meaningful, source-supported content anchors;
- course duration, language count, difficulty, delivery format, file type, QA status, and similar configuration values are not used as homepage teaching cards unless explicitly required by the source or user;
- the opening visual is the most relevant authentic source visual available, not a generic acronym tile, abstract placeholder, or decorative icon when a real product/process/architecture image exists;
- opening text and visual form one balanced, attractive composition;
- source-page screenshots are cropped, extracted, enlarged, or annotated so the useful content is readable rather than surrounded by unused page margins.

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
- the opening image is genuinely relevant to the source topic and large enough to identify the subject immediately;
- image containers are sized from the useful visual content rather than a rigid page template;
- a full source page is not displayed at unreadable scale when a useful region can be extracted or enlarged.

A missing, half-visible, unintentionally cropped, generic-placeholder, source-irrelevant, or unreadably small opening visual blocks release when a suitable source image was available.

# 7. Header, Footer, Subtitle, and Icon QA

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
- the right-side action cluster remains right-aligned and completely visible;
- progress remains prominent;
- the header subtitle is a concise explanation of the course title rather than a scene-by-scene caption;
- the normal course subtitle remains stable across scenes;
- scene-specific context appears in the body eyebrow, module label, scene title, or footer rather than rewriting the fixed subtitle on every page;
- an optional subtitle change occurs only at a meaningful module boundary and remains concise.

For v3.5.0 content refinements, the approved Micas top and bottom control rails are regression-locked. Do not alter their established dimensions, control order, button shells, icon sizes, spacing, or typography to solve middle-scene content issues.

# 8. Semantic Emphasis QA

Verify:

- important facts and normal key actions may use Micas cyan;
- cautions, prerequisites, limits, and conditions requiring confirmation use restrained warning amber where source-supported;
- genuine hazards, prohibited actions, severe failures, or injury/equipment-damage risks use restrained danger red where source-supported;
- verified safe/correct states may use success green;
- semantic color is paired with a label, icon, border, or explanatory text;
- meaning does not depend on color alone;
- red is not used decoratively;
- a normal scene does not contain a visually conflicting collection of bright accent colors;
- warning and danger treatments remain harmonious with the deep-navy stage while still being immediately noticeable.

# 9. Navigation QA

For interactive training:

- Next is enabled on every nonterminal scene;
- module-ending scenes advance to the next module;
- unanswered assessment questions do not block Next;
- Previous is enabled except on the first scene;
- visible controls, keyboard navigation, and Auto Play call the same navigation functions;
- score, feedback, answer, narration, animation, and completion state do not gate global scene navigation;
- only the absolute terminal completion scene disables or replaces Next.

# 10. Narration and Voice QA

Verify for each supported locale:

- the runtime voice list is allowed to populate before default selection;
- `voiceschanged` is handled;
- a matching Google voice is selected by default whenever exposed by the browser/OS;
- arbitrary OS, alphabetical, cached, Microsoft, Apple, or Samantha defaults do not override an available Google voice;
- explicit learner voice choice is stored separately from generated default preference;
- no more than three curated voices are shown;
- unavailable voices are not fabricated;
- fallback is documented when Google is unavailable.

# 11. Auto Play QA

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

# 12. Assessment QA

For the default interactive-training mode:

- all graded questions are in the final Review & Assessment module;
- instructional modules do not end with separate graded exams;
- the dedicated assessment-introduction page exists;
- question count, duration, scoring, and instructions are clear;
- every question maps to the source;
- correct, incorrect, and unanswered states work;
- revisiting questions preserves state;
- results, feedback, and completion work.

# 13. Search QA

Verify:

- Search covers the complete active-language content;
- module titles, scene titles, body text, warnings, procedures, keywords, and assessment content are indexed;
- Search works offline;
- results are grouped and localized;
- the current page does not change until a result is selected;
- result selection navigates correctly;
- Escape, keyboard focus, Enter, and accessible result counts work;
- the search panel scrolls internally only.

# 14. Multilingual QA

For every supported locale:

- all required content is authored and complete;
- technical meaning remains equivalent;
- commands, model names, and standards remain accurate;
- fit, image, control, search, narration, assessment, and accessibility checks pass;
- English remains the strongest visual master unless another locale was explicitly selected;
- locale-specific layout variants do not remove content;
- locale expansion does not push fixed controls outside the viewport;
- cards and metric grids may change composition by locale when needed for clean fit.

# 15. Responsive QA

Confirm:

- desktop quality is perfected first;
- tablet and phone remain usable without overlap, clipped images, inaccessible controls, or missing content;
- compact controls and stacked layouts activate only at appropriate breakpoints;
- responsive adaptation does not shrink the desktop master unnecessarily;
- touch targets remain large enough;
- overlays and drawers remain usable.

# 16. Accessibility QA

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

# 17. Release-Blocking Defects

Do not deliver when any of these occurs:

- unsupported or invented technical fact;
- visible `Layout overflow detected` or similar diagnostic;
- normal presentation page scrolls or overflows;
- document-level horizontal scrolling;
- any header/footer control is pushed partly or fully beyond the viewport;
- content fits only after entering Fullscreen;
- content is clipped in a browser-content viewport such as 1366×650;
- missing or half-visible technical image;
- a generic or irrelevant opening visual is used while a suitable source visual exists;
- the opening scene is dominated by duration, language count, difficulty, Offline HTML, file type, QA status, or other project metadata rather than the real training subject;
- large accidental empty region or blank panel;
- repeated rigid left-text/right-image layouts make most of the course visually identical;
- a large white or pale image frame contains substantial unused blank space;
- undersized instructional body text;
- card, metric, label, or translated text crosses its border, overlaps another element, or is clipped;
- tiny or off-center primary controls;
- selected brand identity is broken;
- the approved fixed header/footer controls are altered merely to make middle-scene content fit;
- the header subtitle is rewritten as a different scene summary on every page;
- a source-supported safety hazard, prohibited action, or critical warning is visually indistinguishable from ordinary information;
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

# 18. QA Report

The QA Report must record:

- source coverage and unresolved source issues;
- selected brand and mode;
- opening-scene content and visual source;
- viewport results, including constrained browser-content viewports and horizontal containment;
- typography and card-fit results;
- image-integrity results;
- layout-diversity and stage-utilization review;
- fixed-control boundary review;
- stable-subtitle review;
- semantic emphasis and safety-highlight review;
- navigation and control review;
- voice availability and fallback;
- Auto Play and assessment behavior;
- search results;
- multilingual completeness;
- responsive and accessibility checks;
- any known limitation.

# 19. Micas Approved-Shell Regression QA

When `brand_profile: micas` and `training_mode: interactive-training` are active, verify every desktop build against:

- `modules/brands/micas/references/header-lockup-reference.svg`;
- `modules/brands/micas/references/top-right-controls-reference.svg`;
- `modules/brands/micas/references/footer-fixed-controls-reference.svg`.

Mandatory checks:

- the left header contains the official Micas logo, a large primary title, and a visibly smaller subtitle below it;
- the subtitle is not missing, hidden, clipped, or merged into the primary title;
- the subtitle remains a stable course-level explanation rather than changing into a new scene summary on every page;
- the right header contains Language → Auto Play → Fullscreen in that order;
- Language has an appropriate icon and dropdown indicator;
- Auto Play and Fullscreen are visible in normal desktop mode;
- progress/module/question counters do not replace the right-header controls;
- the footer contains Course Menu, scene count, visible progress, Previous, Next, Search, narration, and Audio settings in the approved grouping and order;
- the footer does not cover scene content;
- every fixed header/footer control remains fully inside the viewport;
- each scene fits at 1920×1080, 1600×900, 1366×768, 1920×930, 1600×780, and 1366×650 without requiring Fullscreen;
- cards, source previews, images, assessment results, and explanatory text remain fully visible above the footer;
- a complete technical image is never clipped by a fixed-height container;
- semantic highlights are restrained, attractive, and limited to brand cyan, warning amber, success green, and genuine danger red;
- highlighted meaning remains understandable without color alone;
- the approved header/footer rails remain unchanged by content-layout refinements.

The following are release-blocking regressions:

- missing desktop subtitle;
- scene-by-scene replacement of the course subtitle;
- missing Auto Play or Fullscreen button;
- language selector without its icon;
- progress controls moved into the right header in place of utilities;
- footer reduced to a materially smaller or different control strip than the approved reference;
- any fixed control pushed outside the viewport by middle-scene content;
- any page that reveals hidden content only after entering Fullscreen;
- content, image, results panel, or captions clipped behind the footer;
- opening-scene metadata cards unrelated to the real training topic;
- opening scene lacks a relevant source visual when one exists;
- rigid repetition of one split-screen composition across most scenes;
- overflowing text inside cards or metric panels;
- excessive, visually conflicting, or semantically incorrect highlight colors.
