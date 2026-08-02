# Core Rules

Version: **3.1.0**

This module contains the invariant source-grounding and content-engineering rules used by every supported training mode and brand pack.

# 1. Source Authority

1. Treat user-supplied source files as the primary and authoritative basis.
2. Read complete relevant sections, including body text, tables, figures, captions, warnings, procedures, appendices, screenshots, notes, and embedded images.
3. Preserve exact product names, commands, terminology, numerical values, safety limits, procedure order, dependencies, and operational boundaries.
4. Do not silently invent, correct, reconcile, or supplement unsupported technical information.
5. When the source is inconsistent, incomplete, or ambiguous, record the issue in the QA Report instead of silently choosing an answer.
6. Preserve the source's framing and level of detail unless the user explicitly asks for expansion or outside research.
7. Represent safety-critical content accurately and prominently.
8. Keep source traceability for every generated module, scene, claim, interaction, and graded question.

# 2. Source Audit

Before authoring, build an internal source map covering:

- document hierarchy;
- audience, prerequisites, and intended use;
- key concepts and specifications;
- procedures, order, and dependencies;
- warnings, cautions, and prohibited actions;
- reusable images and diagrams;
- troubleshooting symptoms, causes, checks, and resolutions;
- reference-only material;
- contradictions, missing information, suspected errors, and unsupported claims.

Do not construct a complete course from isolated snippets when surrounding context affects meaning.

# 3. Content Prioritization

Classify source material as:

- **Must perform:** procedures, checks, limits, and safety actions
- **Must recognize:** ports, LEDs, modules, labels, symptoms, states, and visual cues
- **Must understand:** architecture, rationale, dependencies, airflow, redundancy, tradeoffs, and decision logic
- **Reference only:** exhaustive tables, regulations, dimensions, and rarely used appendices

The selected training mode determines how these categories are taught, but it must not remove required facts or safety boundaries.

# 4. Learning-Message Hierarchy

For each scene or learning unit, define:

- `primaryMessage`: the one fact, action, decision, conclusion, or limit the learner should retain;
- `supportingPoints`: normally two to five concise supporting items;
- `referenceDetails`: secondary content moved to another scene, reference layer, overlay, or companion file;
- `focalEvidence`: image, number, diagram, warning, example, or source fact that deserves the most attention;
- `sourceRefs`: exact source locations supporting the unit;
- `localeVariants`: language-specific wording or layout changes that preserve meaning.

Avoid treating all source content as equal weight.

# 5. Traceability and Learner-View Hygiene

Maintain source mapping in structured data and companion reports.

Normal learner-facing pages must not show:

- raw source mapping;
- page-reference accordions;
- authoring notes;
- QA flags;
- generation metadata;
- debug output;
- internal narration scripts unless captions are intentionally enabled.

Source mapping belongs in the Course Map, QA Report, course data model, or dedicated reviewer mode.

# 6. Multilingual Content

Default locale model:

| Locale key | Display label | TTS target |
|---|---|---|
| `en` | English | `en-US` |
| `zh-CN` | 简体中文 | `zh-CN` |
| `zh-TW` | 繁體中文 | `zh-TW` |
| `ja` | 日本語 | `ja-JP` |

Rules:

1. English is the default and visual master unless the user selects another master locale.
2. Author independent language versions; do not rely on runtime machine translation.
3. Preserve technical names, commands, standards, model names, and port labels when translation reduces accuracy.
4. Other locales may use different line breaks, wording length, scene splitting, and layout variants while preserving equivalent meaning.
5. Do not weaken the English master merely to force identical density across languages.
6. Every supported locale must pass content, fit, image, control, narration, assessment, and accessibility QA.

# 7. Safe Inference

When the source does not specify a nontechnical presentation detail, reasonable instructional-design inference is allowed, such as:

- learning sequence;
- visual grouping;
- scene titles;
- transition wording;
- icon selection;
- animation restraint;
- navigation labels;
- practice format when supported by the learning objective.

Do not infer unsupported technical facts, performance claims, compliance status, warranties, customer outcomes, safety assurances, or assessment answers.

# 8. Module Isolation

- Core rules are brand-neutral and training-mode-neutral.
- Brand packs may change identity, colors, logo, tone, and visual references only.
- Training modes may change learning architecture, interaction, assessment presentation, narration, and completion behavior only.
- UI may change rendering and interface behavior only.
- QA may add validation requirements but may not rewrite source facts.

The default Micas `interactive-training` configuration must remain behaviorally equivalent to the established production course behavior.

# 9. Artifact Integrity

Generated training artifacts must:

- contain all required local assets;
- avoid broken runtime dependencies;
- preserve source-supported facts;
- include meaningful alt text and accessible labels;
- separate learner-facing content from reviewer metadata;
- document assumptions and fallbacks;
- be complete rather than a partial prototype when the user requests a full course.

# 10. Required Companion Documentation

For standard interactive training, produce:

1. interactive training HTML;
2. Course Map;
3. QA Report;
4. usage README.

For gamified learning, follow the selected training mode's training-specific deliverables while still providing a QA Report and README.

The QA Report must identify source issues, assumptions, missing assets, fallback behavior, and any requirement that could not be completed.
