# 参考资料索引

> 本目录存放架构设计技能的所有参考章节。新增章节请按编号命名并更新此索引。

## 命名规范

文件名格式：`XX-主题名.md`（XX 为两位数编号，递增）

## 章节目录

| 编号 | 文件 | 主题 | 核心内容 |
|------|------|------|---------|
| 01 | [01-architecture-thinking.md](01-architecture-thinking.md) | 为什么先有架构思维 | 架构定义三特征、实现 vs 判断、两问检验法、A/B 团队案例、Knight Capital 案例 |
| 02 | [02-systematic-architecture-judgment.md](02-systematic-architecture-judgment.md) | 做架构判断是有章法的 | 六步框架、灵魂六问、质量属性清单、取舍矩阵、短链接服务案例 |
| 03 | [03-c4-model-architecture-diagrams.md](03-c4-model-architecture-diagrams.md) | 读懂与画好架构图：C4 模型 | C4 四层缩放、烂图四宗罪、五条画图原则、ASCII 画图技巧 |
| 04 | [04-ten-core-architecture-patterns.md](04-ten-core-architecture-patterns.md) | 十大核心架构模式 | 分层/单体/微服务/事件驱动/消息队列/CQRS/Pub-Sub/BFF/管道/微内核、选型决策流程 |
| 05 | [05-data-and-state.md](05-data-and-state.md) | 数据与状态：系统真正的难点 | 存储选型九种、一致性谱系/CAP/ACID vs BASE、复制/分片/缓存三张牌、缓存三大难题 |
| 06 | [06-quality-attributes-and-tradeoffs.md](06-quality-attributes-and-tradeoffs.md) | 质量属性与取舍 | 七大属性度量/实现/冲突、经典冲突矩阵、不可能三角、和业务方谈取舍的沟通心法 |
| 07 | [07-system-design-methodology.md](07-system-design-methodology.md) | 从 0 到 1 设计系统：实战方法论 | 八步流程、信封背面估算锚点、先粗后细、架构迭代、短链接实战推演 |

## 更新指南

新增章节时：
1. 按编号创建 `XX-主题名.md` 文件
2. 在上表添加一行索引
3. 如有新的分析维度/工作流程，同步更新 `SKILL.md`
