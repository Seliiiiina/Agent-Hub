# Agent Hub TODO

## 当前状态

- [x] 建立 Agent Hub、4 个 Functional Agent 和业务 Subagent 目录。
- [x] 建立学习、代码、数据、合规注册、部门协作、周期报告和外部动作类 Agent。
- [x] 为 `Read-only`、`Draft-only`、`Data Modification`、`External Action` 定义权限边界。
- [x] 在 README 中记录多步骤案例和 Copilot Studio 外部工具触发矩阵。
- [x] 完成第一轮重复能力清理：9 组移除 10 个定义，现有 172 个；别名、引用和计数已同步。
- [ ] 对 Agent Registry 做最终去重、计数和字段一致性审查。

## 本轮审查修正（2026-10-15）

- [x] 删除过时的六 Agent 手工流程推演记录 `Flow-Validation.md`。
- [x] Agent Creator 返回字段统一为 `instruction`。
- [x] 补齐缺输入状态，并明确 Executor 的暂停和回传契约。
- [x] 为 12 个通用模板 Agent 补充具体输入、交付物、边界和示例，不合并定义。
- [x] 将 Active 明确为 TXT 定义已完成，不代表已部署或已通过平台验收。

## Finder 检索边界修正（2026-10-17）

- [x] 保留原四步匹配、分类、评分权重和最多五个推荐，限定 Finder 仅检索已连接的 SharePoint `Agent-Registry.md`。
- [x] 禁止 Finder 公网搜索；加入一次优先、最多两次检索及错误／重复结果停止规则。
- [x] 增加知识源 Description、检索覆盖说明和 Hub 防止重复调用的处理规则，详见 README 的 Finder knowledge scope。
- [x] 将 Hub 新增兜底合并进已有输出规则，精简重复表述，使完整 TXT 和 Instruction 都小于 8000 字符。
- [ ] 在 Copilot Studio 更新 Finder、Hub 和知识源 Description；新会话验证公网调用为零，成功后及时停止。
- [ ] 验证无权限、空结果、部分召回和重复片段时的退出行为；需要时配置限定知识源的 Generative answers 节点。

## 第一阶段：整理仓库

- [x] 检查 `Agent-Registry.txt` 的 Business Subagent 数量与 `business-subagents/*.txt` 文件数量一致。
- [x] 确认每个 Agent 只有一条 Registry 记录。
- [ ] 确认每个定义包含名称、描述、触发条件、输入要求、执行规则、限制和结构化返回格式。
- [x] 去除业务 Agent 重复元数据块，并核对分类、权限、状态及更新时间与 Registry 一致。
- [x] 检查分类统计、权限统计和总数是否一致。
- [x] 运行 TXT 空白、JSON返回格式和本地链接检查。
- [ ] 提交并推送当前仓库变更。

## 第二阶段：准备 Copilot Studio

- [ ] 创建或确认 Copilot Studio 环境、Solution、连接引用和环境变量。
- [ ] 将每个 Agent 的 Name、Description 和 Instruction 手动配置到 Copilot Studio。
- [ ] 为只读 Agent 配置知识源、SharePoint、Dataverse、CRM 或其他只读 Connector。
- [ ] 为代码和 API Agent 配置允许使用的代码、API 或 MCP 工具。
- [ ] 为 `Data Modification` Agent 配置可写 Connector 或 Agent Flow，并限制字段、记录范围和操作类型。
- [ ] 为 `External Action` Agent 配置邮件、日历、工单、通知和文件发布 Connector 或 Flow。
- [ ] 根据数据敏感度选择 Agent author authentication、User authentication 或 OBO。
- [ ] 配置 DLP、连接共享、环境权限、最小权限和审计日志。
- [ ] 为外部动作配置明确的触发短语和动作前确认。

## 第三阶段：权限与安全验证

- [ ] 验证 `Read-only` Agent 不能写入、发送、发布或修改外部记录。
- [ ] 验证 `Draft-only` Agent 只能返回草稿，不能自动执行后续动作。
- [ ] 验证 `Data Modification` Agent 会先返回预览，再等待用户确认。
- [ ] 验证 `External Action` Agent 会展示目标、内容、收件人、时间和权限范围。
- [ ] 验证用户没有权限时，Agent 会停止并返回清晰的授权错误。
- [ ] 验证重复请求不会导致重复发送、重复工单或重复写入。
- [ ] 验证失败时返回外部系统错误、已完成步骤、失败步骤和重试建议。
- [ ] 验证可用时保存回滚引用、变更日志或取消操作信息。

## 第四阶段：功能验收

- [ ] 单独测试 Finder：从已上传的 Agent-Registry.txt 检索 Budget Variance Agent 的名称、分类和权限，并核对来源证据。
- [ ] 验证 Finder 的知识源处理状态为 Ready；目录问题能检索到 Registry Overview、分类汇总和具体条目。
- [ ] 从 Hub 测试 “what agent do you have?”，检查实际运行记录是否调用 Finder 并返回检索证据。
- [ ] 验证 Registry 无法检索时返回 registry_unavailable，部分检索时展示有证据的条目，不编造完整计数或搜索能力。

- [ ] 用 5 个 Agent Finder 查询检查分类、匹配分数和推荐理由。
- [ ] 验收客户反馈 → 产品改进简报工作流。
- [ ] 验收 API 变更 → 集成代码与测试草稿工作流。
- [ ] 验收项目复盘 → 决策记录与交接包工作流。
- [ ] 验收课程推荐 → 学习路径 → 笔记 → 练习 → 学习检查流程。
- [ ] 验收注册适用性 → 注册清单 → 证据包 → 表单映射 → 准备度审查流程。
- [ ] 验收日报、周报、月报、年报的周期边界和数据口径。
- [ ] 验收邮件、日历、工单、通知和文件发布的预览与确认流程。

## 第五阶段：发布与维护

- [ ] 为每个已连接 Agent 记录实际工具、连接身份、数据源和环境。
- [ ] 标记尚未部署或尚未连接数据源的 Agent，避免误称为已上线。
- [ ] 为高风险 Agent 指定业务负责人和技术负责人。
- [ ] 为外部动作和数据修改保留审计记录。
- [ ] 每月检查 Agent 使用率、误匹配、重复能力和失败记录。
- [ ] 将重复或长期未使用的 Agent 标记为 Draft、Deprecated 或 Unavailable。
- [ ] 每次定义、权限、工具或数据源变化后更新 `Last Updated`。

## 完成标准

- Registry 数量与实际定义文件一致。
- 每个 Agent 的权限、触发条件、工具和输出范围已验证。
- 所有外部动作和数据修改都经过用户确认并留下结果记录。
- 至少一条简单任务和一条多步骤工作流通过验收。
- Copilot Studio 中的连接、认证、DLP 和审计配置已有记录。

## GitHub 与 Copilot Studio 参考资源

### Copilot Studio 是否可以连接 GitHub

可以。Copilot Studio 可以通过 Connector、Agent Flow/Power Automate、MCP Server、REST API 或其他工具连接外部系统；Microsoft 的官方工具文档明确将 GitHub 列为可通过 MCP 等方式接入的服务。连接是否可用还取决于租户策略、连接权限、认证方式、区域和管理员治理设置。

建议的接入路径：

- 只读仓库检索：GitHub Connector、GitHub MCP 或自建 REST API。
- 创建 Issue、评论或更新项目：GitHub Connector/Flow，使用 User authentication 或 OBO，并要求确认。
- Pull Request 或代码修改：使用受限的 Agent Flow/API，限定仓库、分支、文件范围和操作类型。
- 企业内部 GitHub：优先使用组织批准的连接和最小权限 Token，禁止把个人 Token 写入 Agent 指令或代码。

### 推荐优先研究的 GitHub 资源

| 资源 | 用途 | 建议动作 |
| --- | --- | --- |
| [microsoft/CopilotStudioSamples](https://github.com/microsoft/CopilotStudioSamples) | 官方 Copilot Studio 样例，包含 authoring、extensibility、SSO、testing 和基础设施目录 | 作为 Copilot Studio 配置和验收样例的第一参考 |
| [microsoft/new-copilot-studio-tech-guide](https://github.com/microsoft/new-copilot-studio-tech-guide) | Copilot Studio Agents and Workflows 技术指南与可部署示例 | 研究 Agent、工具和工作流的组合方式 |
| [microsoft/agent-framework](https://github.com/microsoft/agent-framework) | Microsoft Agents Framework 与 Copilot Studio 连接示例 | 需要代码调用 Copilot Studio Agent 时参考认证和环境变量配置 |
| [microsoft/Agents](https://github.com/microsoft/Agents) | Microsoft Agents 生态、SDK 与 Copilot Studio 链接汇总 | 评估 SDK、MCP 和跨 Agent 集成路线 |

GitHub 仓库只能作为设计、代码和配置参考。引入任何外部样例前，需要检查许可证、维护状态、依赖、权限范围、Secrets 处理方式和安全公告；不要直接把仓库代码当作已验证的企业生产方案。

### GitHub 接入验收清单

- [ ] 确认租户允许使用目标 Connector、MCP 或自定义 API。
- [ ] 为只读检索和写入操作创建不同连接或权限范围。
- [ ] 使用测试仓库验证搜索、读取、Issue、Pull Request 和文件操作。
- [ ] 验证 User authentication/OBO 是否符合用户数据访问要求。
- [ ] 验证 Agent 不会在未确认时创建 Issue、评论、提交或修改文件。
- [ ] 记录仓库、组织、分支、路径、连接身份和审计信息。
- [ ] 在发布前完成许可证、依赖、DLP、Secrets 和回滚审查。
