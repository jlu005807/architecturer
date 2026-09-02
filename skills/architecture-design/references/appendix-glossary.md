# 附录 · 架构术语表

> 读教程或模板时撞到不认识的词？来这里查。每条只给一句话直觉 + 指向讲透它的章节。
> 不求严谨定义，只求你「秒懂它在说什么」。

## 规模与性能

| 术语 | 一句话直觉 | 讲透它的地方 |
|------|-----------|-------------|
| QPS / TPS | 每秒请求数 / 每秒事务数——衡量系统多忙。 | [07 信封背面估算](07-system-design-methodology.md) |
| 延迟（Latency） | 单次操作要等多久（快不快）。 | [06 质量属性](06-quality-attributes-and-tradeoffs.md) |
| 吞吐（Throughput） | 单位时间能处理多少（量大不大）。 | [06](06-quality-attributes-and-tradeoffs.md) |
| P99（尾延迟） | 99% 的请求比这个值快——看 P99 别看平均，因为最慢的那 1% 最伤体验。 | [06](06-quality-attributes-and-tradeoffs.md) |
| 读写比 | 读多还是写多——决定系统该往「读优化」还是「写优化」倾斜。 | [02 灵魂六问](02-systematic-architecture-judgment.md) |
| 尾延迟 / 对冲请求 | 平均数稀释长尾，p99 才是真实体验；扇出放大让整体 p99 趋近子调用的 p999——等 p95 再补发第二份砍长尾。 | [13 规模化力学](13-scaling-mechanics.md) |
| 排队直觉（Little 定律 / USL） | 利用率逼近 100% 排队按 1/(1−ρ) 爆炸，留余量是设计；协调开销让加机器收益递减甚至变负。 | [13](13-scaling-mechanics.md) |
| 信封背面估算 | 用几个除法快速估出数量级（QPS、存储量），判断系统会被什么压垮。 | [07](07-system-design-methodology.md) |

## 数据与一致性

| 术语 | 一句话直觉 | 讲透它的地方 |
|------|-----------|-------------|
| 强一致 / 最终一致 | 写完立刻全网都对（贵）/ 写完过一会儿才一致（便宜、高可用）。 | [05 数据与状态](05-data-and-state.md) |
| CAP | 网络一旦分区，只能在「一致」和「可用」里二选一。 | [05](05-data-and-state.md) |
| ACID / BASE | 严谨派（强一致、强保证）/ 务实派（高可用、最终一致）。 | [05](05-data-and-state.md) |
| 事务（Transaction） | 一组操作「要么全成、要么全不成」。 | [05](05-data-and-state.md) |
| 幂等（Idempotency） | 同一个操作重复执行多次，结果和执行一次一样——重试不会闯祸。 | [电商平台模板](../templates/03-ecommerce-platform.md) |
| PACELC | CAP 的补全版：分区时选 C/A；**平时 99% 的时间**还在拿延迟（L）换一致性（C）。 | [10 分布式硬道理](10-distributed-systems-hard-truths.md) |
| 共识（Raft / Paxos） | 让多数派机器对一件事达成铁板一致——最贵的协调，只用在选主/元数据/锁。 | [10](10-distributed-systems-hard-truths.md) |
| 逻辑时钟 | 没有全局钟，就靠「谁导致了谁」定先后：Lamport / 向量时钟 / HLC。 | [10](10-distributed-systems-hard-truths.md) |
| 至少一次 / 至多一次 / 恰好一次 | 传递保证只有前两种；恰好一次 = 至少一次 + 消费端幂等（效果上）。 | [10](10-distributed-systems-hard-truths.md) |
| 2PC（两阶段提交） | 把多个库框回一个事务的协议——同步阻塞、协调者单点，跨服务高并发别用。 | [11 一致性工程](11-data-consistency-engineering.md) |
| Saga | 把大事务拆成一串本地事务，失败反向补偿——补偿不是回滚，历史删不掉。 | [11](11-data-consistency-engineering.md) |
| Outbox（事务性发件箱） | 改库+发消息没法同事务？待发消息写进同一个本地事务的表，再由投递员发出。 | [11](11-data-consistency-engineering.md) |
| 双写（Dual Write） | 既改库又发消息，两步无共同事务——先写谁都有一个失败窗口，事件驱动头号陷阱。 | [11](11-data-consistency-engineering.md) |
| 事件溯源（Event Sourcing） | 存「发生过什么」而非「现在是什么」，当前状态靠重放事件算出来——审计/时间旅行的重武器。 | [11](11-data-consistency-engineering.md) |
| expand-contract | 数据迁移三步走：扩展→双写迁移→收缩，全程新旧兼容不停机——永不做一步到位的破坏性变更。 | [11](11-data-consistency-engineering.md) |
| 无状态 / 有状态 | 不记事（好复制好扩）/ 记事（难复制，一切麻烦的根）。 | [05](05-data-and-state.md) |

## 扩展手段

| 术语 | 一句话直觉 | 讲透它的地方 |
|------|-----------|-------------|
| 垂直扩展 / 水平扩展 | 把单机搞更强（治标、有上限）/ 加更多机器（治本、要求无状态）。 | [06](06-quality-attributes-and-tradeoffs.md) |
| 复制（Replication） | 做多份只读副本，主要为「扩读」。 | [05](05-data-and-state.md) |
| 分片（Sharding） | 按规则把数据切到多台机器，主要为「扩写」。 | [05](05-data-and-state.md) |
| 缓存（Cache） | 把热点数据放在更快的地方，降延迟 + 扩读；代价是一致性。 | [05](05-data-and-state.md) |
| CDN | 把内容铺到离用户最近的边缘节点，降延迟 + 省带宽。 | [视频流媒体模板](domains/realtime-and-storage.md) |
| 削峰 / 限流 | 用队列 / 排队把瞬时洪峰整形成平缓水流，别让后端被冲垮。 | [04 消息队列](04-ten-core-architecture-patterns.md) |
| 一致性哈希 / 虚拟节点 | 哈希环上顺时针找节点——加减节点只搬 1/N 数据；vnode 抹平不均与故障冲击。 | [13](13-scaling-mechanics.md) |
| 热点（hot key） | 幂律：一个热 key 能让分片形同虚设。打散 = 把一个点变成一片：加盐/本地缓存/只读副本/请求合并。 | [13](13-scaling-mechanics.md) |
| 缓存踩踏（single-flight） | 超热 key 过期瞬间万请求同时回源——并发重建只放一个去查，其余订阅结果。 | [13](13-scaling-mechanics.md) |
| 多区域多活 | 每个区域可读可写：买到本地性+区域容灾，几乎必然放松强一致（写冲突 LWW/CRDT/字段拆分）。 | [13](13-scaling-mechanics.md) |

## 架构模式

| 术语 | 一句话直觉 | 讲透它的地方 |
|------|-----------|-------------|
| 单体 / 微服务 | 一个部署单元（简单，被低估）/ 多个独立部署的小服务（解决「人」的扩展，被滥用）。 | [04](04-ten-core-architecture-patterns.md) |
| 事件驱动 / Pub-Sub | 广播「发生了什么」，谁关心谁响应——解耦与扇出。 | [04](04-ten-core-architecture-patterns.md) |
| CQRS | 把「写」和「读」拆成两套模型各自优化；重武器，CRUD 系统用它就是过度设计。 | [04](04-ten-core-architecture-patterns.md)、[11](11-data-consistency-engineering.md) |
| 扇出（Fan-out） | 一件事触发很多下游——推模型（写时扇出）vs 拉模型（读时聚合）。 | [社交信息流](domains/web-and-product.md) |
| 倒排索引 | 把「文档→词」翻转成「词→文档列表」，全文检索的根基。 | [搜索引擎](domains/web-and-product.md) |
| ANN（近似最近邻） | 用一点精度换巨大速度，在海量向量里快速找「最相似」。 | [向量数据库](domains/ai-native.md) |
| 绞杀者模式（Strangler Fig） | 在旧系统外围加一层门面/路由，逐块把流量引向新实现，旧的自然枯死——不推倒、只渐进。 | [14 演进与拆分](14-evolving-and-splitting-systems.md) |
| 抽象分支（Branch by Abstraction） | 立一层抽象当「插座」，新旧实现并存靠开关切换，全程在主干可发布——替代长命特性分支。 | [14](14-evolving-and-splitting-systems.md) |
| 防腐层（ACL） | 新服务与旧系统之间的「翻译+隔离」墙，旧模型的腐烂不会渗进新服务。 | [14](14-evolving-and-splitting-systems.md) |
| 模块化单体 | 一个部署单元但内部有强制模块边界——先把缝划对划稳，再按需抽服务；服务数量不是目标。 | [14](14-evolving-and-splitting-systems.md) |

## 可靠性与运维

| 术语 | 一句话直觉 | 讲透它的地方 |
|------|-----------|-------------|
| 可用性 / 几个 9 | 系统有多少时间是「活着」的；99.9% = 3 个 9，每多一个 9 成本数量级上涨。 | [06](06-quality-attributes-and-tradeoffs.md) |
| 持久性（Durability） | 存进去的数据丢失的概率有多低（如 S3 的 11 个 9）。 | [06](06-quality-attributes-and-tradeoffs.md) |
| SLO / 错误预算 | 给可用性定个目标（SLO），剩下的「不可用额度」就是错误预算，用完就停新功能保稳定。 | [06](06-quality-attributes-and-tradeoffs.md)、[12](12-resilience-engineering.md) |
| 单点故障（SPOF） | 某一处一挂全系统瘫——可用性的头号敌人，靠冗余消灭。 | [06](06-quality-attributes-and-tradeoffs.md) |
| MTBF / MTTR | 多久坏一次 / 坏了多久能恢复——可用性的杠杆绝大多数压在 MTTR 那一端。 | [12 韧性工程](12-resilience-engineering.md) |
| 级联失败 | 一个慢依赖顺着调用链拖垮全站；三个放大器：资源耗尽、重试风暴、超时堆叠。慢比宕机更致命。 | [12](12-resilience-engineering.md) |
| 熔断器 | 保险丝：失败率超阈值就跳闸快速失败，半开态先放探子试水再恢复。 | [12](12-resilience-engineering.md) |
| 舱壁 / 爆炸半径 | 把资源池切开，故障不串味；最该隔开的是核心与非核心。故障视角见 12，安全视角（一处被攻破只炸一舱）见 16。 | [12](12-resilience-engineering.md)、[16 安全与多租户](16-security-and-multi-tenancy.md) |
| 降载 / 背压 | 扛不住时主动丢一部分保整体——优雅地拒绝，远胜假装全扛然后一起崩。 | [12](12-resilience-engineering.md) |
| 优雅降级 | 提前把功能分「掉了会死/能忍」，事故时一键关非核心保核心——坏一部分远好过全挂。 | [12](12-resilience-engineering.md) |
| 指数退避 + 抖动 | 聪明重试的两半：越等越久 + 随机打散同步重试；再加预算与幂等前提，四样缺一不可。 | [12](12-resilience-engineering.md) |
| 混沌工程 | 别假设，去证明：主动可控地注入故障，提前暴露只有出事才会暴露的脆弱点。 | [12](12-resilience-engineering.md) |
| 部分失败 / 灰色失败 | 有的成了有的败了有的不知死活；你分不清「它死了」还是「它只是慢」，超时只是猜测。 | [10](10-distributed-systems-hard-truths.md) |

## 安全与合规

| 术语 | 一句话直觉 | 讲透它的地方 |
|------|-----------|-------------|
| 威胁建模 / STRIDE | 对着数据流图对每道边界问六问：假冒/篡改/抵赖/泄露/拒服/提权——系统性想坏事，而不是想起来就打补丁。 | [16 安全与多租户](16-security-and-multi-tenancy.md) |
| 信任边界 | 信任级别变化的那道线（公网→系统、服务→数据）；坏事几乎总发生在边界上，防御按边界投放。 | [16](16-security-and-multi-tenancy.md) |
| 纵深防御 / 零信任 | 层层设防破一层还有下一层；信任不绑网络位置（never trust, always verify），每次访问重新挣得。 | [16](16-security-and-multi-tenancy.md) |
| 多租户隔离谱系 | 池化→桥接→竖井，成本↔隔离强度；数据从行级→Schema→库级→物理级由软到硬。 | [16](16-security-and-multi-tenancy.md) |
| 租户串扰 | A 租户看到 B 租户的数据——多租户头号事故；行级隔离全靠每条 SQL 带 tenant_id，必须平台层强制注入而非靠人自觉。 | [16](16-security-and-multi-tenancy.md) |
| secrets 三铁律 | 集中保管、定期轮换、最小暴露；任何会被 grep/commit/打进日志的明文都该假设已泄露。 | [16](16-security-and-multi-tenancy.md) |
| 供应链安全 / SBOM | 你只写了 5% 的代码，信任却是传递的；锁版本+物料清单+最小化依赖+可复现构建。 | [16](16-security-and-multi-tenancy.md) |
| 合规即架构 | 数据驻留/被遗忘权/审计留痕是结构性约束，事后加不上只能重做——从第一张图就织进结构。 | [16](16-security-and-multi-tenancy.md) |
| slopsquatting | 抢注 AI 幻觉出的假包名投毒——AI 生成代码里约两成含幻觉包名，推荐的包先核实再进 lockfile。 | [16](16-security-and-multi-tenancy.md) |
| 提示注入 | 恶意文本藏在网页/邮件/工具返回里被模型当指令照做——堵不死只能层层防，硬约束落在权限与边界而非提示词。 | [16](16-security-and-multi-tenancy.md) |

## AI 时代判断

| 术语 | 一句话直觉 | 讲透它的地方 |
|------|-----------|-------------|
| vibe coding | 特指不审查就接受 AI 产出——玩具原型绝妙，推上生产等于把没读过的房子交给人住；瓶颈从「写」移到「想清楚」。 | [17 大模型时代的架构判断](17-llm-era-architecture-judgment.md) |
| 非确定性 / 评测驱动 | 同样输入不保证同样输出——assert 换成评测集+评分看质量分布，进 CI 防退化；护栏人审+可回退配套。 | [17](17-llm-era-architecture-judgment.md) |
| 上下文工程 | 把上下文窗口当新内存层级管：窗口装恰好、RAG 按需取、长期记忆落盘；长上下文 vs RAG vs 微调是取舍。 | [17](17-llm-era-architecture-judgment.md) |
| 成本/延迟/质量三角 | LLM 系统新质量属性：强模型贵慢、弱模型快糙，永远在三角里选位置；token 成本是一等公民。 | [17](17-llm-era-architecture-judgment.md) |
| 模型路由 / 预算上限 | 简单任务小模型、难任务大模型；agent 必须有步数/成本/超时上限——自主性越强越要装刹车。 | [17](17-llm-era-architecture-judgment.md) |
| 工作流 vs 自主 Agent | 能用确定的工作流解决就别上自主 Agent——Agentic 系统是进阶篇硬骨头的总和，不是捷径。 | [17](17-llm-era-architecture-judgment.md) |

## 流程与演进

| 术语 | 一句话直觉 | 讲透它的地方 |
|------|-----------|-------------|
| 质量属性 / 非功能性需求 | 系统「做得多好」（快/稳/扛得住），区别于「做什么」（功能）。 | [02](02-systematic-architecture-judgment.md) |
| 取舍（Trade-off） | 任何决策都是「用 A 换 B」；没有银弹。 | [02](02-systematic-architecture-judgment.md) |
| ADR | 架构决策记录：用一页纸记下「为什么这么决定、放弃了什么」。 | [08 ADR](08-architecture-decision-records.md) |
| 技术债 | 为「现在更快」有意识地选的权宜方案——关键是记账、按计划还。 | [08](08-architecture-decision-records.md) |
| 康威定律 | 系统架构会长得像设计它的组织的沟通结构——组织图是架构图的草稿。 | [08](08-architecture-decision-records.md)、[15 组织即架构](15-organization-as-architecture.md) |
| C4 模型 | 像地图缩放一样分四层画架构图：Context→Container→Component→Code。 | [03 画架构图](03-c4-model-architecture-diagrams.md) |
| 并行运行 / 影子流量 | 新旧实现对同一批真实流量同时跑，旧的给用户、新的只比对——用数据当裁判，不用自信。 | [14](14-evolving-and-splitting-systems.md) |
| 适应度函数 | 把架构约束写成会失败、能卡 CI 的自动化测试——架构的免疫系统，长大但不腐化。 | [14](14-evolving-and-splitting-systems.md) |
| 逆康威操作 | 想要什么架构，就先把团队组织成那个形状——让组织倒逼出架构。 | [15 组织即架构](15-organization-as-architecture.md) |
| 认知负荷 | 一个团队能装进脑子的复杂度有硬上限；桶溢出（疲于救火、说不清整体）才是该拆的信号。 | [15](15-organization-as-architecture.md) |
| Team Topologies 四类团队 | 流式对齐（主角，端到端包一条业务流）+ 平台/赋能/复杂子系统（都为给它减负）。 | [15](15-organization-as-architecture.md) |
| 平台工程 / 黄金路径 | 把 CI/CD、监控等偶然复杂度铺成自助的「铺好的路」——靠好用赢得采用，不靠审批强制。 | [15](15-organization-as-architecture.md) |
| 两个披萨团队 | 团队小到两个披萨能喂饱（6–10 人）——内部沟通 O(n²) 可控，自治的前提。 | [15](15-organization-as-architecture.md) |
| 接口即契约 | 跨团队只走稳定接口（版本化/向后兼容/契约测试）；契约越稳，团队越敢独立演进。 | [15](15-organization-as-architecture.md) |
