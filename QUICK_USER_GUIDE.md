# Quick User Guide

This guide shows the fastest recommended way to use the **Micas Doc-to-Interactive-Training Skill v3 modular framework**.

## 1. Default Recommended Configuration

Use these defaults unless the project clearly requires something different:

```text
brand_profile: micas
experience_mode: interactive-training
ui_system: modules/UI.md
qa_system: modules/QA.md
project_title: auto-generate from the source material
audience: Technical Support Engineers
objective: Convert the source material into a complete, job-ready interactive training course
duration: 30–45 minutes
default_language: English
supported_languages: English, 简体中文, 繁體中文, 日本語
visual_master_language: English
primary_output: self-contained offline HTML
additional_outputs: Course Map, QA Report, README
assessment: one consolidated final Review & Assessment module
assessment_difficulty: Intermediate
```

The default module load order is:

```text
1. modules/CORE.md
2. modules/modes/interactive-training.md
3. modules/brands/micas/BRAND.md
4. modules/UI.md
5. modules/QA.md
```

## 2. What to Upload

Upload the source materials that should be converted, for example:

- Word manuals or SOPs;
- PDF installation guides;
- PowerPoint product material;
- Excel product or service lists;
- safety documents;
- process documents;
- product images, diagrams, screenshots, and logos.

The AI should treat the uploaded source files as the primary factual basis and must not invent unsupported technical, safety, performance, compliance, warranty, customer, or marketing claims.

## 3. Default Recommended Prompt

Copy and use the prompt below after uploading the source files:

```text
请使用 Micas Doc-to-Interactive-Training Skill v3 模块化框架，
把我刚上传的资料制作成一套完整、可直接使用的互动培训课程。

模块选择：

brand_profile: micas
experience_mode: interactive-training
ui_system: modules/UI.md
qa_system: modules/QA.md

请严格按以下顺序读取并执行：

1. modules/CORE.md
2. modules/modes/interactive-training.md
3. modules/brands/micas/BRAND.md
4. modules/UI.md
5. modules/QA.md

项目默认值：

- 项目名称：根据源资料自动生成
- 受众：Technical Support Engineers
- 培训目标：把源资料转化为完整、实用、可用于工作场景的互动培训课程
- 预计时长：30–45分钟
- 默认语言：English
- 支持语言：English、简体中文、繁體中文、日本語
- 视觉主版本：English
- 品牌：Micas Networks
- 主色：#00899F
- 输出形式：单文件离线HTML
- 附加输出：Course Map、QA Report、README
- 考核方式：所有正式评分题统一放在最后的 Review & Assessment 模块
- 考核难度：Intermediate

执行要求：

1. 完整读取正文、表格、图片、警告、步骤、附录和嵌入素材。
2. 以源文件为主要事实依据，不得编造技术、安全、性能、合规、保修、客户或市场信息。
3. 按学习目标重组为 Course → Module → Scene 的分层结构，不要逐页照搬原文档。
4. 默认生成 Micas 深蓝色、PPT式一页一屏的互动课程，正常页面禁止上下滚动。
5. English 先作为视觉母版做到最美观、最清晰；其他语言可以采用独立换行、比例或布局变体。
6. 技术图片必须完整显示并充分放大，禁止只显示一半或意外裁切。
7. 默认使用各语言可用的 Google 语音；Auto Play 必须等待本页全部旁白播放完成后再翻页。
8. 正式考试题只放在最后模块；进入考试前必须有单独的过渡页；考题不自动播放或自动跳过。
9. 直接生成完整可下载成品，不要只给方案、目录或样章。
10. 交付前执行 modules/QA.md 中所有适用检查，修复全部 Release-blocking defects 后再交付。

最终交付：

1. [PROJECT_NAME]_Interactive_Training.html
2. [PROJECT_NAME]_Course_Map.md
3. [PROJECT_NAME]_QA_Report.md
4. [PROJECT_NAME]_README.md
```

## 4. Minimal Prompt for Daily Use

When the Skill is already installed or available in the current Project, use:

```text
请使用 Micas Doc-to-Interactive-Training Skill v3 的默认配置：

brand_profile: micas
experience_mode: interactive-training

把我刚上传的资料制作成完整互动培训课程。
默认English，支持简体中文、繁體中文和日本語；预计30–45分钟；
输出单文件离线HTML、Course Map、QA Report和README。
请直接生成完整成品，并在通过modules/QA.md全部检查后再交付。
```

## 5. Change the Experience Mode

Only change `experience_mode` when a different output purpose is required.

### Gamified learning

```text
experience_mode: gamified-learning
```

Use for missions, levels, points, badges, branching decisions, and challenge-based learning.

### Executive report

```text
experience_mode: executive-report
```

Use for management summaries, business reviews, results, risks, decisions, owners, and action plans.

### Marketing content

```text
experience_mode: marketing-content
```

Use for value propositions, use cases, differentiation, evidence, FAQs, campaigns, and calls to action.

Do not load more than one experience mode unless a hybrid is explicitly requested and the combination is checked for conflicts.

## 6. Change the Company or Brand

To use another company, create a new brand pack from:

```text
modules/brands/BRAND_TEMPLATE.md
```

Recommended structure:

```text
modules/brands/[brand-name]/
├── BRAND.md
└── references/
    ├── logo.svg
    ├── header-reference.png
    └── content-reference.png
```

Then change:

```text
brand_profile: modules/brands/[brand-name]/BRAND.md
```

Changing the company should normally require only a new brand pack. Do not rewrite `CORE.md`, `UI.md`, or the selected experience mode just to change the logo, colors, or brand tone.

## 7. Default Behavior Summary

With the default values, the framework generates:

- a Micas-branded interactive training course;
- a unified deep-navy stage using Micas cyan `#00899F`;
- one-screen/PPT-like scenes with no normal-page scrolling;
- a clear Course → Module → Scene hierarchy;
- large learner-facing text and strong visual hierarchy;
- complete technical images using `object-fit: contain`;
- English as the default and visual-master language;
- Simplified Chinese, Traditional Chinese, and Japanese versions;
- Google-default narration whenever the browser exposes a matching voice;
- Auto Play that waits for complete narration before advancing;
- final-only graded assessment with an introduction page;
- icon-only full-course Search;
- desktop-first presentation with tablet and phone adaptation;
- a self-contained offline HTML package plus documentation and QA results.

## 8. Recommended Working Method

For repeated use, keep the entire repository installed in a dedicated Project or Agent. For each new course:

1. upload only the new source files;
2. use the Default Recommended Prompt above;
3. change only the audience, objective, duration, brand, or experience mode when necessary;
4. require the complete deliverables and QA results;
5. do not ask the AI to reinterpret or rewrite the Skill rules unless you are intentionally updating the framework.
