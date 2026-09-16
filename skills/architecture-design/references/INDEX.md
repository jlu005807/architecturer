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
| 10 | [10-distributed-systems-hard-truths.md](10-distributed-systems-hard-truths.md) | 分布式系统的硬道理：部分失败、时间与共识 | 单机三奢侈/灰色失败、一致性四档光谱、PACELC、逻辑时钟、共识别滥用、exactly-once 幻觉+幂等、GitHub 43 秒分区案例 |
| 11 | [11-data-consistency-engineering.md](11-data-consistency-engineering.md) | 数据一致性工程：没有跨服务事务怎么把数据弄对 | 2PC 代价、Saga（补偿≠回滚/编排 vs 编舞）、双写→Outbox（at-least-once+幂等）、幂等三件套、事件溯源、CQRS、expand-contract 契约演进、DoorDash Cadence 案例 |
| 12 | [12-resilience-engineering.md](12-resilience-engineering.md) | 为失败而设计：韧性工程 | MTBF→MTTR 思维翻转、级联失败三放大器、爆炸半径（舱壁/cell/shuffle sharding）、熔断/超时预算/降载、退避+抖动重试、优雅降级、SLI/SLO/SLA 与错误预算、混沌工程、三大真实事故案例 |
| 13 | [13-scaling-mechanics.md](13-scaling-mechanics.md) | 规模化的力学：加机器不是免费的 | 垂直 vs 水平/无状态好扩、范围 vs 哈希分片与一致性哈希+虚拟节点、热点（把一个点变成一片）、多级缓存与踩踏、多区域多活、尾延迟扇出放大与对冲请求、排队论/USL、Discord/Twitter/Tail at Scale 案例 |
| 14 | [14-evolving-and-splitting-systems.md](14-evolving-and-splitting-systems.md) | 演进与拆分大型系统：给飞行中的飞机换引擎 | 大重写为何注定失败、绞杀者模式、抽象分支、并行运行/影子流量（Scientist）、零停机数据迁移五步、拆单体（限界上下文/防腐层/模块化单体先行）、适应度函数、五大真实案例 |
| 15 | [15-organization-as-architecture.md](15-organization-as-architecture.md) | 组织即架构：你的系统会长得像你的组织 | 康威定律扶正为主梁、逆康威操作、认知负荷与 Team Topologies 四类团队、平台工程/黄金路径、微服务=组织扩展手段、两个披萨+接口即契约、自建vs采购、三大真实案例 |
| 16 | [16-security-and-multi-tenancy.md](16-security-and-multi-tenancy.md) | 安全与多租户架构：把安全当结构，而非补丁 | STRIDE 威胁建模/信任边界、纵深防御+零信任（BeyondCorp）、爆炸半径与隔离、多租户隔离谱系（池化/桥接/竖井+行级→物理级）、密钥三铁律、供应链安全（xz/Log4Shell/SolarWinds/Capital One）、合规即架构、slopsquatting+提示注入 |
| 17 | [17-llm-era-architecture-judgment.md](17-llm-era-architecture-judgment.md) | 大模型时代的架构判断：vibe coding 时代，你靠什么不可替代 | 两个转变（实现廉价/新物种）、vibe coding 放大架构错误、非确定性→评测驱动、上下文工程=新内存层级、成本/延迟/质量三角、Agentic 系统=进阶篇总和、什么没变；进阶篇收官 capstone |

> **01–09 是入门篇**（看懂系统、从 0 设计中小系统）；**10 起是进阶篇**（系统做大做关键后才露牙的硬骨头：分布式、失败、规模、演进、组织和安全）。

## 附录

| 文件 | 内容 |
|------|------|
| [appendix-glossary.md](appendix-glossary.md) | 架构术语表：一句话直觉 + 指向讲透它的章节，按规模/数据/扩展/模式/可靠性/流程分类 |
| [appendix-signals.md](appendix-signals.md) | 升级信号速查：数据层/体验层/稳定性/组织效率四层量化触发信号 + 破解手段 |
| [appendix-reflexes.md](appendix-reflexes.md) | 条件反射自查卡：触发场景→条件反射（估算选型/数据一致性/扩展韧性/安全信任边界/AI 时代判断/沟通决策六组 + 决策前三问，63 条），源自二十一轮拷问复盘 |

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
