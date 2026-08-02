# Micas Doc-to-Interactive-Training Skill

Version: **3.5.0**

This repository converts source documents into complete interactive training courses.

It supports only two training modes:

- **Standard interactive training** — default;
- **Gamified interactive learning** — optional and used only when explicitly requested.

The Skill no longer includes company-report, executive-report, marketing-content, or other non-training modes.

# Current Structure

```text
Micas-Doc-to-Interactive-Training-SKILL/
├── SKILL.md
├── README.md
├── QUICK_USER_GUIDE.md
├── CHANGELOG.md
├── prompts/
│   ├── MASTER_PROMPT.md
│   └── QUICK_PROMPT.md
└── modules/
    ├── CORE.md
    ├── UI.md
    ├── QA.md
    ├── brands/
    │   ├── BRAND_TEMPLATE.md
    │   └── micas/
    │       ├── BRAND.md
    │       └── references/
    │           ├── header-lockup-reference.svg
    │           ├── content-hero-product-split-reference.svg
    │           ├── content-checkpoint-positioning-reference.svg
    │           ├── content-checkpoint-redundancy-airflow-reference.svg
    │           ├── content-key-metrics-power-reference.svg
    │           └── header-action-icons-reference.svg
    └── modes/
        ├── interactive-training.md
        └── gamified-learning.md
```

# Why This Structure Is Simpler

## One clear purpose

Everything in the repository now supports training creation. There are no report, marketing, campaign, or generic content-experience modes.

## One default mode

The normal default is always:

```text
training_mode: interactive-training
```

The Skill must not add game mechanics by itself.

Use the optional game mode only when the user explicitly selects:

```text
training_mode: gamified-learning
```

## One responsibility per module

- `CORE.md` — source reading, factual accuracy, traceability, multilingual equivalence, and safe inference;
- `interactive-training.md` — standard course structure, navigation, narration, search, assessment, completion, source-grounded opening scenes, and browser-window fit;
- `gamified-learning.md` — optional missions, levels, points, badges, branching challenges, and game-specific QA;
- `UI.md` — all interface, layout, typography, imagery, controls, responsive, and accessibility rules;
- `QA.md` — all release checks;
- brand packs — logo, colors, tone, and colocated visual references.

## Brand switching remains independent

Although the Skill only creates training, the brand can still be changed without rewriting training logic.

Copy:

```text
modules/brands/BRAND_TEMPLATE.md
```

and create:

```text
modules/brands/<brand-id>/
├── BRAND.md
└── references/
```

# Default Invocation

```text
请使用 Micas Doc-to-Interactive-Training Skill v3.5。

brand_profile: micas
training_mode: interactive-training

把我上传的资料制作成完整互动培训课程。
请读取SKILL.md和规定模块，直接生成完整成品，不要只给方案或样章。
```

For the full formal prompt, use:

```text
prompts/MASTER_PROMPT.md
```

For the concise Chinese prompt, use:

```text
prompts/QUICK_PROMPT.md
```

For default values and daily-use examples, read:

```text
QUICK_USER_GUIDE.md
```

# Training Mode Selection

## Standard interactive training — default

```text
training_mode: interactive-training
```

Suitable for:

- technical product training;
- installation and operation training;
- service-sales training;
- SOP and process training;
- safety and compliance training;
- onboarding and certification courses;
- troubleshooting and maintenance training.

## Gamified interactive learning — optional

```text
training_mode: gamified-learning
```

Suitable for explicitly requested:

- mission-based learning;
- levels and progression;
- points or XP;
- competency badges;
- branching scenarios;
- challenge-based troubleshooting;
- final missions or game-style assessments.

Game mechanics must serve learning. They must not invent technical outcomes, encourage unsafe speed, or obscure the source content.

# Preserved Default Behavior

With the default Micas standard mode, version 3.5.0 preserves:

- Micas deep-navy stage and primary color `#00899F`;
- approved Micas header lockup and visual references;
- the approved top and bottom fixed control rails without redesign;
- one-screen/PPT-like scenes;
- large learner-facing text and strong hierarchy;
- complete technical images;
- Course → Module → Scene architecture;
- hidden bottom-left Course Menu;
- footer order Previous → Next → Search → narration → Audio settings;
- icon-only Search;
- global Next availability;
- matching Google voice as default when the runtime exposes one;
- Auto Play waits for complete narration;
- all graded questions in the final module;
- no narration or auto-skip on graded questions;
- assessment introduction, results, and completion;
- English-first four-language delivery;
- desktop-first responsive behavior;
- self-contained offline HTML and mandatory QA.

Version 3.5.0 additionally requires:

- the homepage to introduce the real source topic rather than duration, language count, difficulty, Offline HTML, or other project metadata;
- the homepage to use concise source-supported learning anchors;
- the most relevant authentic source image to be used when available;
- every scene to fit normal browser-content viewports after tabs/address bars reduce vertical space;
- Fullscreen not to be required to reveal hidden content.

# Recommended Use

For repeated use, keep the repository connected to the AI or installed in a dedicated Project or Agent. Each time:

1. upload the source materials;
2. use the default standard-training prompt;
3. change audience, objective, duration, or brand only when needed;
4. select `gamified-learning` only when game-based learning is explicitly required;
5. require complete deliverables and QA results.
