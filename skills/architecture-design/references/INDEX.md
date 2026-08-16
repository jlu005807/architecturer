# 参考资料索引

> 本目录包含两类参考：**教程章节**（按编号，系统学习）和 **领域速查**（按系统类型，教练阶段 5 按需读取）。

## 命名规范

文件名格式：`XX-主题名.md`（XX 为两位数编号，递增）

## 章节目录

| 编号 | 文件 | 主题 | 核心内容 |
|------|------|------|---------|
| 01 | [01-architecture-thinking.md](01-architecture-thinking.md) | 为什么先有架构思维 | 架构定义三特征、实现 vs 判断、两问检验法、A/B 团队案例、Knight Capital 案例 |
| 02 | [02-systematic-architecture-judgment.md](02-systematic-architecture-judgment.md) | 做架构判断是有章法的 | 六步框架、灵魂六问、质量属性清单、取舍矩阵、短链接服务案例 |
| 03 | [03-c4-model-architecture-diagrams.md](03-c4-model-architecture-diagrams.md) | 读懂与画好架构图：C4 模型 | C4 四层缩放、烂图四宗罪、五条画图原则、ASCII 画图技巧 |
| 04 | [04-ten-core-architecture-patterns.md](04-ten-core-architecture-patterns.md) | 十大核心架构模式 | 分层/单体/微服务/事件驱动/消息队列/CQRS/Pub-Sub/BFF/管道/微内核、选型决策流程 |
| 05 | [05-data-and-state.md](05-data-and-state.md) | 数据与状态：系统真正的难点 | 存储选型九种、一致性三档（强/顺序因果/最终）+ 限量发放族、CAP/ACID vs BASE、扩展三张牌 + 先消解再扩容、客户端作为副本（离线优先：操作日志/同步游标/墓碑/LWW 边界）、缓存三大难题 |
| 06 | [06-quality-attributes-and-tradeoffs.md](06-quality-attributes-and-tradeoffs.md) | 质量属性与取舍 | 七大属性度量/实现/冲突、经典冲突矩阵、不可能三角、和业务方谈取舍的沟通心法 |
| 07 | [07-system-design-methodology.md](07-system-design-methodology.md) | 从 0 到 1 设计系统：实战方法论 | 八步流程、信封背面估算锚点、先粗后细、架构迭代、短链接实战推演 |
| 08 | [08-architecture-decision-records.md](08-architecture-decision-records.md) | 架构决策记录与演进 | ADR 模板六块、演进式架构/接缝、技术债管理、康威定律、升级判断两把尺子 |
| 09 | [09-architecture-taste.md](09-architecture-taste.md) | 架构品味：框架之外的差距 | 品味五面向、小团队默认审美五条、创新代币、大公司审美流派、练品味五件事 |

## 附录

| 文件 | 内容 |
|------|------|
| [appendix-glossary.md](appendix-glossary.md) | 架构术语表：一句话直觉 + 指向讲透它的章节，按规模/数据/扩展/模式/可靠性/流程分类 |
| [appendix-signals.md](appendix-signals.md) | 升级信号速查：数据层/体验层/稳定性/组织效率四层量化触发信号 + 破解手段 |

## 领域速查（教练阶段 5 按需加载）

来自 [architecture-copilot](https://github.com/study8677/architecture-copilot) 的领域参考文件。每个文件覆盖 4-6 个系统模板的「关键决策 / 反模式 / 演进信号」三节高密度摘要。教练在阶段 5 匹配用户系统类型后，**只读命中的那一个文件**。

| 文件 | 覆盖系统类型 |
|------|-------------|
| [web-and-product.md](domains/web-and-product.md) | 普通网站、移动 App、浏览器插件、短链、搜索、社交信息流 |
| [transactional.md](domains/transactional.md) | 电商、支付、在线票务/秒杀、通知推送、网约车 |
| [realtime-and-storage.md](domains/realtime-and-storage.md) | 聊天/IM、协同编辑、网盘/文件同步、视频流媒体 |
| [ai-native.md](domains/ai-native.md) | AI 对话/LLM、AI 网关、RAG 知识库、向量数据库、模型推理、AI Agent |
| [agent-and-org.md](domains/agent-and-org.md) | 编码 Agent、自托管智能体、系统提示词架构、AI 原生组织 |
| [embedded-industrial.md](domains/embedded-industrial.md) | 嵌入式/固件、物联网、工业边缘、汽车电子、机器人 |

### 跨模板通用

已整合至附录：[appendix-glossary.md](appendix-glossary.md)（术语速查）、[appendix-signals.md](appendix-signals.md)（升级信号，含 AI 层）。

> 完整 14 节模板（架构图/数据流/安全/参考原型）以上游 [awesome-architecture/templates](https://github.com/study8677/awesome-architecture/tree/main/templates) 为唯一权威源。

## 更新指南

新增章节时：
1. 按编号创建 `XX-主题名.md` 文件
2. 在上表添加一行索引
3. 如有新的分析维度/工作流程，同步更新 `SKILL.md`
