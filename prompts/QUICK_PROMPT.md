# Quick Prompt — Micas互动培训课程

请使用 **Micas Doc-to-Interactive-Training Skill v3.1**，把我上传的资料制作成完整互动培训课程。

本Skill只用于培训教学材料，不用于公司汇报、管理报告或市场营销材料。

## 培训配置

```text
品牌：[micas / 其他品牌包路径]
培训模式：[interactive-training / gamified-learning]
```

默认使用：

```text
品牌：micas
培训模式：interactive-training
```

只有我明确要求游戏闯关、任务、等级、积分、徽章或分支挑战时，才使用：

```text
培训模式：gamified-learning
```

请按顺序读取：

1. `modules/CORE.md`
2. 选中的`modules/modes/`培训模式文件
3. 选中的`modules/brands/`品牌文件
4. `modules/UI.md`
5. `modules/QA.md`

项目默认值：

- 标题：根据源资料自动生成
- 受众：Technical Support Engineers
- 目标：转换为完整、实用、可用于工作场景的互动培训课程
- 预计时长：30–45分钟
- 默认语言：English
- 支持语言：English、简体中文、繁體中文、日本語
- 视觉主版本：English
- 考核难度：Intermediate
- 输出：单文件离线HTML、Course Map、QA Report和README

强制要求：

- 完整读取正文、表格、图片、警告、步骤和附录。
- 以源资料为事实依据，不编造技术、安全、性能、合规、保修、客户或市场信息。
- 按Course → Module → Scene组织学习内容，不要逐页照搬原文档。
- 默认使用普通互动培训模式，不要自行加入游戏元素。
- 只有选择`gamified-learning`时才加入任务、等级、积分、徽章和挑战。
- 按品牌包使用Logo、色调、品牌语气和参考素材。
- 保持深蓝背景、一页一屏、完整大图、大正文、Google默认语音、完整旁白后翻页、最终统一考试、考试题不自动播放、全文搜索和离线单文件HTML。
- 直接生成完整可下载成品，不只给方案或样章。
- 交付前执行`modules/QA.md`全部适用检查并修复严重缺陷。
