# Experience Mode: Gamified Learning

Version: **3.0.0 starter profile**

Mode ID: `gamified-learning`

This optional mode is inactive unless explicitly selected. It changes the experience structure while preserving all Core source-grounding and safety rules.

# Purpose

Turn source-supported learning objectives into missions, levels, challenges, decisions, feedback loops, and visible progress.

# Architecture

Recommended structure:

```text
Briefing
  → Mission Map
  → Level 1: Recognition
  → Level 2: Concepts
  → Level 3: Procedure
  → Level 4: Troubleshooting
  → Final Challenge
  → Results and Next Mission
```

# Interaction Model

Allowed elements:

- mission objectives;
- XP or points;
- badges tied to demonstrated competencies;
- unlockable levels based on completion;
- branching scenarios;
- timed choices only when timing is educationally justified;
- retry and feedback;
- progress map;
- final challenge.

Do not use manipulative streaks, artificial scarcity, gambling mechanics, or penalties unrelated to learning.

# Source and Difficulty

- Every challenge and correct answer must map to the source.
- Do not invent technical consequences for dramatic effect.
- Difficulty should come from realistic decisions, prioritization, sequencing, and troubleshooting—not obscure trivia.
- Safety-critical mistakes should receive clear corrective feedback.

# Narration and Playback

Narration is optional. Auto Play must stop at every interactive decision and wait for the learner. Challenges must never be skipped by timers or narration callbacks.

# Assessment

Use a final challenge or mission debrief instead of a conventional exam when appropriate. Scoring must be transparent and source-supported.

# Deliverables

1. self-contained gamified HTML experience;
2. Mission Map;
3. scoring and rules documentation;
4. QA Report;
5. README.

# Mode QA

Release blockers include:

- invented technical outcomes;
- challenges skipped automatically;
- unclear scoring;
- points that reward speed over safety without source justification;
- inaccessible game controls;
- progression dead ends;
- branding or UI that obscures learning content.
