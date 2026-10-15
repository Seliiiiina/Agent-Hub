# Agent Hub 重复能力清理记录

更新日期：2026-10-15

本轮基于 main 的 `2476447` 检查 182 个业务子 Agent。文件 SHA-256 检查没有发现字节完全相同的文件；这里的“完全重复”指业务能力入口重复：核心任务、必要输入、交付物和执行边界相同，名称、措辞、JSON键名或详略不同不足以形成独立能力。不同知识域、执行权限或专门交付物不能只因共用模板就合并。

本轮整理 **9 组**，移除 **10 个**冗余定义，保留 **172 个**业务子 Agent。包括主 Agent 和 4 个功能 Agent，仓库共 177 个 Agent 定义。数量与权限以 [Agent Registry](Agent-Registry.md) 为准。

## 已清理的重复入口

| 能力 | 保留的唯一入口 | 移除的定义 | 对照依据 |
| --- | --- | --- | --- |
| 文档版本比较 | [Document Version Comparison Agent](business-subagents/Document-Version-Comparison-Agent.md) / 文档版本差异助手 | Document Change Review Agent | 两个文本版本 → 对齐章节、增删改移、出处、可能影响与待审问题；均不编辑原件。 |
| 指标口径设计 | [Metric Definition Designer Agent](business-subagents/Metric-Definition-Designer-Agent.md) / 指标口径设计助手 | Metric Definition Agent；KPI Definition Agent | 业务目标与字段 → 指标定义、分子分母、粒度、周期、来源与未决口径；均不实施或批准指标。 |
| 问卷设计 | [Questionnaire Design Agent](business-subagents/Questionnaire-Design-Agent.md) / 问卷设计助手 | Survey Design Agent | 研究目标与受众 → 问题、选项、跳转、目标映射与预测试检查；均不发布或收集答案。 |
| 业务变更影响分析 | [Change Impact Analysis Agent](business-subagents/Change-Impact-Analysis-Agent.md) / 变更影响分析助手 | Business Change Impact Analysis Agent | 现状与拟议变更 → 影响地图、依赖、证据和验证问题；均不实施变更。 |
| 会议议程 | [Meeting Agenda Planner Agent](business-subagents/Meeting-Agenda-Planner-Agent.md) / 会议议程规划助手 | Meeting Agenda Agent | 会议目标、时长与角色 → 分钟级议程、讨论问题、准备清单和决策依赖；均不预订会议。 |
| HR制度问答 | [HR Policy Explainer Agent](business-subagents/HR-Policy-Explainer-Agent.md) / HR制度解读助手 | HR Policy Q&A Agent | 适用HR制度与问题 → 有出处的制度解释和未决事项；旧通用模板未定义额外交付物或动作。 |
| 报销制度问答 | [Expense Policy Explainer Agent](business-subagents/Expense-Policy-Explainer-Agent.md) / 报销制度解读助手 | Expense Policy Assistant Agent | 适用报销制度与问题 → 条款、凭证和适用范围解释；旧通用模板未定义报销提交或个人单据核算能力。 |
| 技术事件分诊 | [Incident Triage Agent](business-subagents/Incident-Triage-Agent.md) / 技术事件分诊智能体 | IT Incident Triage Agent | 事件事实与路由规则 → 分诊、证据缺口和升级材料；旧通用模板没有额外IT执行能力。 |
| 项目复盘 | [Retrospective Facilitator Agent](business-subagents/Retrospective-Facilitator-Agent.md) / 复盘引导助手 | Project Retrospective Agent | 目标、结果和事件证据 → 事实时间线、得失、原因假设、复盘问题与改进草案；均不作人员判断或执行改进。 |

选择保留项依据是定义完整度、明确边界与已有工作流引用，不按贡献者或创建先后机械取舍。HR、报销与IT分诊的旧入口是通用模板，未提供额外工具、数据契约或独立任务，保留具体领域定义。

## 兼容与细节保留

- 已删除重复 Markdown 文件及对应注册记录；没有创建可调用的旧名占位 Agent。历史版本可从 Git 提交中恢复。
- 旧英文名与中文名放入保留定义的路由别名和 Registry Keywords。Finder 应返回唯一规范名称，而不是把别名当成另一候选。
- 指标口径保留来源映射、刷新频率与语义检查；问卷保留分析映射、跳转环和不可达问题检查。
- 变更影响保留数据／控制、例外、可逆性与未受影响范围；会议议程保留决策依赖；复盘保留显式经验教训、证据与适用限制。
- 同步修正其余 Agent 中的调用名称、配置文档链接、目录数量和权限矩阵；原 60 个候选方向仍全部覆盖。
- 保留入口沿用其注册的 Read-only 或 Draft-only 权限。变更影响分析统一使用已有 Change Impact Analysis Agent 的 Draft-only 契约；不会因此允许实施变更或外部写入。
- 名称搜索兼容不等于旧JSON返回结构兼容。若公司环境已经配置过被移除入口，需手动改用上述保留名称、说明和返回字段，并重新验证对应工作流；本次没有操作 Copilot Studio。

## 暂不合并的部分重叠能力

| 相近能力 | 保留理由 |
| --- | --- |
| Agent Test Case Designer / Test Case Design / Test Case Draft | 分别产出 Agent 路由与边界验收、软件／业务验收案例、框架兼容测试代码；后两者的代码生成边界不同。 |
| Training Lesson Plan / Training Content Draft / Teaching Case Designer | 分别产出授课步骤与时间安排、培训正文及练习答案、完整教学案例。 |
| Prompt Refinement / Prompt Evaluation / Prompt Comparison Review | 分别改写提示词、诊断设计并设计评测、对齐多个变体及实际输出作对照；仍有部分交叉，留待下一轮。 |
| Knowledge Article Draft / Knowledge Base Article | 前者围绕已记录的解决步骤生成操作／排障文章；后者也覆盖概念、定义与FAQ文章，暂保留。 |
| Customer Feedback Analysis / Customer Feedback Triage / Qualitative Text Coding | 分别产出需求与改进假设、问题类型与建议队列、逐条编码数据及统计；路由与数据交付不同。 |
| AI Learning Resource Recommender / Learning Path Planner | 前者从指定Excel课程库选资源并排序；后者规划阶段、练习、检查点与截止日期，且不限于AI课程库。 |
| Automation Opportunity / AI Task Suitability | 前者诊断流程中的多个自动化机会并测算收益；后者判断单个任务的AI适用性与限制。 |
| Change Communication Plan / Stakeholder Communication Map | 前者围绕变更发布安排消息、时间与反馈；后者建立一般项目的信息需求及沟通关系地图。 |
| Incident Postmortem / Retrospective Facilitator / Root Cause Analysis | 分别保留技术事故复盘、项目整体复盘、具体问题的因果假设与验证；事故定义目前较通用，不能仅凭模板相同直接删除。 |
| Procurement Request / Procurement Brief / Procurement Policy Knowledge | 分别针对采购申请材料、供应商需求书及响应问题、采购制度知识；申请模板尚需进一步明确，暂不合并。 |
| Daily / Weekly / Monthly / Annual Report Draft | 报告周期及比较范围不同，本轮保持现有设计；是否参数化为统一报告Agent另议。 |
| 文档总结 / 销售通话总结，以及各种通用模板 | 只共享模板或步骤并不等于业务目的完全重复；通用占位定义需要进一步补齐边界，本轮不以此为由批量删除。 |

本轮是明确重复入口的第一轮清理，不声称所有部分重叠或宽泛定义都已解决。下一轮可优先明确提示词评测、知识库文章、客户反馈和采购申请的调用边界，再决定是否合并。

## 检查范围

静态检查覆盖定义文件与注册表一一对应、唯一规范名称、9个保留定义的元数据与结构化返回、旧文件链接、目录计数、172行权限矩阵和原分析／工作流段落保留。平台路由、知识源连接和实际执行效果仍需在公司环境验收；不把静态检查称为运行测试。
