# architecturer

一套中文的**系统架构设计教练**。它不是可运行的应用，而是一个给 AI 助手用的技能：在动手写代码之前，把那些难以更改、影响全局、关乎质量属性的决策想清楚。

核心信念：**漂亮的代码救不了歪的地基。**

## 它做什么

当讨论系统设计、技术选型、系统拆分、数据流或架构评审时，这个技能会按教练方式推进，而不是直接甩出一个方案。

- **正向设计**：从一句话定位开始，经过业务范围、灵魂六问、数量级估算、质量属性取舍、关键决策，收敛成一版带假设和代价的架构。
- **读图 / 评审**：对已有方案走四步——本质、全景、取舍、死穴——输出一页评审笔记。
- **刻意不做**：用户只是要写代码、修 bug、查 API 时，不自动进入架构流程。

三条工作信念：架构是从约束里逼出来的；没有银弹，只有取舍；没有最好的架构，只有这组约束下最合适的。

## 目录

```
skills/architecture-design/
├── SKILL.md            技能入口：角色、六步判断、八步实战
├── COACHING.md         怎么陪人做架构：铁律、追问话术、七阶段
├── CONVENTIONS.md      新增章节与模板的格式规范
├── TEMPLATE.md         14 节架构输出模板
├── grilling-review.md  二十二轮拷问的学习记录
├── references/         教程章节 + 领域速查 + 附录
└── templates/          五个完整系统范例
```

### 教程章节（`references/`）

| 篇 | 章节 | 主题 |
|----|------|------|
| 入门 | 01–09 | 架构思维、六步判断、C4 画图、十大模式、数据与状态、质量属性取舍、从 0 设计系统、ADR、架构品味 |
| 进阶 | 10–17 | 分布式硬道理、一致性工程、韧性、规模化、演进与拆分、组织即架构、安全与多租户、大模型时代的架构判断 |

附录：术语表、升级信号速查、65 条条件反射自查卡。完整索引见 [`references/INDEX.md`](skills/architecture-design/references/INDEX.md)。

### 领域速查

按系统类型加载，每次只读命中的那一个：网站与产品、交易、实时与存储、AI 原生、Agent 与组织、嵌入式与工业。

### 系统范例（`templates/`）

短链接、AI 对话产品、电商平台、支付系统、群聊 IM。每个都按统一的 14 节结构写完：定位、需求与约束、全景图、数据流、数据模型、关键决策、规模化、安全、反模式、演进路线。

## 怎么用

把 `skills/architecture-design/` 作为技能目录交给支持技能的 AI 助手（如 Claude Code）。触发说法例如：

- 「我想做一个 X，该怎么设计」
- 「帮我评审这个方案」
- 「这个选型的代价是什么」

想自己读，从 [`SKILL.md`](skills/architecture-design/SKILL.md) 进判断流程，从 [`references/INDEX.md`](skills/architecture-design/references/INDEX.md) 按章节读。

## 来源

教练方法论与领域速查整理自 [architecture-copilot](https://github.com/study8677/architecture-copilot)；完整模板的上游权威源是 [awesome-architecture](https://github.com/study8677/awesome-architecture)。本仓库在此基础上持续打磨章节、范例与拷问复盘。
