# Quick User Guide

Use this repository to convert source documents into **interactive training courses only**.

Two training modes are available:

- `interactive-training` — default standard mode;
- `gamified-learning` — optional and used only when explicitly requested.

## 1. Default Recommended Values

```text
brand_profile: micas
training_mode: interactive-training
project_title: auto-generate from the source material
audience: Technical Support Engineers
objective: Convert the source into complete job-ready interactive training
duration: 30–45 minutes
default_language: English
supported_languages: English, 简体中文, 繁體中文, 日本語
visual_master_language: English
assessment_difficulty: Intermediate
primary_output: self-contained offline HTML
additional_outputs: Course Map, QA Report, README
```

These values configure the project. They are not automatically displayed as learner-facing homepage content. The generated course homepage must prioritize the real source topic, real learning outcomes, and a relevant source image.

Default module order:

```text
1. modules/CORE.md
2. modules/modes/interactive-training.md
3. modules/brands/micas/BRAND.md
4. modules/UI.md
5. modules/QA.md
```

## 2. Default Recommended Prompt

Upload the source files, then copy this prompt:

```text
请使用 Micas Doc-to-Interactive-Training Skill v3.5，
把我刚上传的资料制作成一套完整、可直接使用的互动培训课程。

配置：
brand_profile: micas
training_mode: interactive-training

请依次读取：
1. modules/CORE.md
2. modules/modes/interactive-training.md
3. modules/brands/micas/BRAND.md
4. modules/UI.md
5. modules/QA.md

默认值：
- 项目名称：根据源资料自动生成
- 受众：Technical Support Engineers
- 培训目标：转换为完整、实用、可用于工作场景的互动培训课程
- 预计时长：30–45分钟
- 默认语言：English
- 支持语言：English、简体中文、繁體中文、日本語
- 视觉主版本：English
- 考核难度：Intermediate
- 输出：单文件离线HTML、Course Map、QA Report和README

要求：
1. 完整读取正文、表格、图片、警告、步骤、附录和嵌入素材。
2. 以源资料为主要事实依据，不得编造技术、安全、性能、合规、保修或客户信息。
3. 按Course → Module → Scene重组内容，不要逐页照搬原文档。
4. 默认使用普通互动培训，不要自行加入积分、等级、徽章或闯关元素。
5. 保持Micas深蓝背景、PPT式一页一屏、大正文、完整技术图片和清晰视觉层级。
6. 首页必须提炼源资料中的真实培训主题、关键能力或实际工作目标，不要把时长、语言数量、难度、Offline HTML或输出格式做成正文卡片。
7. 首页优先使用源资料中最相关的真实产品图、架构图、流程图或场景图；有真实源图时不要使用抽象占位图。
8. 所有页面必须适配普通浏览器窗口中实际可用的`window.innerHeight`，包括浏览器导航栏压缩后的高度；不能依赖Fullscreen才能显示完整内容。
9. English先作为视觉母版；其他语言可使用独立换行、比例或布局变体。
10. 默认使用各语言可用的Google语音；Auto Play必须等待本页全部旁白结束后再翻页。
11. 所有正式考试题统一放在最后模块；考试前必须有过渡页；考题不自动播放或跳过。
12. 直接生成完整成品，不要只给方案、目录或样章。
13. 交付前执行modules/QA.md全部适用检查并修复严重缺陷。
```

## 3. Minimal Daily Prompt

```text
请使用 Micas Doc-to-Interactive-Training Skill v3.5 的默认配置，
把我上传的资料制作成完整互动培训课程。

brand_profile: micas
training_mode: interactive-training

默认English，支持简体中文、繁體中文和日本語；预计30–45分钟；
输出单文件离线HTML、Course Map、QA Report和README。
首页只呈现源资料中的真实培训内容并使用最相关的真实源图，
不要展示时长、语言数量、难度或Offline HTML等项目配置。
所有页面必须适配普通浏览器窗口，不依赖Fullscreen显示完整内容。
不要添加游戏元素。通过modules/QA.md全部检查后再交付。
```

## 4. Optional Gamified Training

Only select this when game-based learning is explicitly required:

```text
training_mode: gamified-learning
```

Example:

```text
请把上传资料制作成游戏化互动培训课程。

brand_profile: micas
training_mode: gamified-learning

加入与学习目标直接相关的任务、等级、积分、徽章、分支决策和最终挑战。
所有挑战、答案、反馈和技术后果必须来自源资料。
Auto Play必须在所有互动决策和挑战页面暂停，等待学员操作。
```

Do not use gambling mechanics, manipulative streaks, artificial scarcity, or speed rewards that conflict with safety.

## 5. Change the Brand

Create another company's training brand pack from:

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

Then select:

```text
brand_profile: modules/brands/[brand-name]/BRAND.md
```

Changing the brand should not require changes to `CORE.md`, `UI.md`, `QA.md`, or the selected training mode.
