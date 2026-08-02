# Core Rules

Version: **3.0.0**

This module contains the invariant source-grounding and content-engineering rules used by every brand and experience mode.

# 1. Source Authority

1. Treat user-supplied source files as the primary and authoritative basis.
2. Read complete relevant sections, including body text, tables, figures, captions, warnings, procedures, appendices, screenshots, notes, and embedded images.
3. Preserve exact product names, commands, terminology, numerical values, safety limits, procedure order, dependencies, and operational boundaries.
4. Do not silently invent, correct, reconcile, or supplement unsupported technical information.
5. When the source is inconsistent, incomplete, or ambiguous, record the issue in the QA Report instead of silently choosing an answer.
6. Preserve the source's framing and level of detail unless the user explicitly asks for expansion or outside research.
7. Represent safety-critical content accurately and prominently.
8. Keep source traceability for every generated section, scene, claim, and graded question.

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

Do not construct a complete artifact from isolated snippets when surrounding context affects meaning.

# 3. Content Prioritization

Classify source material as:

- **Must perform:** procedures, checks, limits, and safety actions
- **Must recognize:** ports, LEDs, modules, labels, symptoms, states, and visual cues
- **Must understand:** architecture, rationale, dependencies, airflow, redundancy, tradeoffs, and decision logic
- **Reference only:** exhaustive tables, regulations, dimensions, and rarely used appendices

The selected experience mode determines how these categories are presented, but it must not remove required facts or safety boundaries.

# 4. Message Hierarchy

For each generated unit, define:

- `primaryMessage`: the one fact, action, decision, conclusion, or limit the audience should retain;
- `supportingPoints`: normally two to five concise supporting items;
- `referenceDetails`: secondary content moved to another unit, appendix, overlay, or report;
- `focalEvidence`: image, number, diagram, warning, quote, chart, or source fact that deserves the most attention;
- `sourceRefs`: exact source locations supporting the unit;
- `localeVariants`: language-specific wording or layout changes that preserve meaning.

Avoid treating all source content as equal weight.

# 5. Traceability and Presentation Hygiene

Maintain source mapping in structured data and companion reports.

Normal audience-facing pages must not show:

- raw source mapping;
- page-reference accordions;
- authoring notes;
- QA flags;
- generation metadata;
- debug output;
- internal narration scripts unless captions are intentionally enabled.

Source mapping belongs in the Course Map, QA Report, data model, or dedicated reviewer mode.

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
6. Every supported locale must pass content, fit, image, control, and accessibility QA.

# 7. Safe Inference

When the source does not specify a nontechnical presentation detail, reasonable design inference is allowed, such as:

- visual grouping;
- page titles;
- transition wording;
- icon selection;
- animation restraint;
- navigation labels;
- learning sequence when the source order is not pedagogically useful.

Do not infer unsupported technical facts, performance claims, compliance status, warranties, customer outcomes, or safety assurances.

# 8. Module Isolation

- Core rules are brand-neutral and mode-neutral.
- Brand packs may change identity, colors, logo, tone, and references only.
- Experience modes may change information architecture, interaction, assessment, narration, and output type only.
- UI may change rendering and interface behavior only.
- QA may add validation requirements but may not rewrite source facts.

The default Micas interactive-training configuration must remain behaviorally equivalent to the established v2.4.1 course behavior.

# 9. Artifact Integrity

Generated artifacts must:

- contain all required local assets;
- avoid broken runtime dependencies;
- preserve source-supported facts;
- include meaningful alt text and accessible labels;
- separate learner-facing content from reviewer metadata;
- document assumptions and fallbacks;
- be complete rather than a partial prototype when the user requests a full deliverable.

# 10. Required Companion Documentation

Unless the selected mode explicitly defines a different package, produce:

1. primary deliverable;
2. content or course map;
3. QA report;
4. usage README.

The QA Report must identify source issues, assumptions, missing assets, fallback behavior, and any requirement that could not be completed.
