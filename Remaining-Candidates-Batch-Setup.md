# Remaining Candidates Batch Setup

## Batch Scope

This batch originally created all 48 candidates remaining in the expansion plan, increasing the synchronized baseline from 134 to 182 Business Subagents. The first deduplication pass subsequently removed 10 redundant definitions across 9 capability groups, leaving 172 canonical definitions. The original 60-candidate pool remains fully covered: 12 were implemented earlier and 48 in this batch. Links below now point to the retained canonical definitions.

All retained entries use Active status as requested. Fully redundant capability entries were consolidated in [Agent Deduplication Review](Agent-Deduplication-Review.md); partially overlapping capabilities remain separate. Candidate counts describe the original creation batch, not the number of surviving new files.

The original candidates 变更影响分析, 项目复盘, and 会议议程设计 are now covered by Change Impact Analysis Agent, Retrospective Facilitator Agent, and Meeting Agenda Planner Agent respectively. Their former batch definitions were removed, and relevant details were preserved in these canonical definitions.

Definitions and Registry metadata are ready for manual configuration; platform deployment, knowledge connections, code runtime access, and end-to-end acceptance remain separate activities. Agent Registry is the metadata source of truth.

## Candidate-to-Definition Mapping

### 数据与量化方法 (6)

| Original remaining candidate | Definition | Runtime requirement |
| --- | --- | --- |
| 抽样方案设计 | [Sampling Design Agent](business-subagents/Sampling-Design-Agent.md) / 抽样方案设计助手 | Actual data; enabled interpreter for nontrivial calculations; honest plan-only fallback. |
| A/B实验方案设计 | [AB Experiment Design Agent](business-subagents/AB-Experiment-Design-Agent.md) / A/B实验方案设计助手 | Actual data; enabled interpreter for nontrivial calculations; honest plan-only fallback. |
| 实验结果评估 | [Experiment Results Assessment Agent](business-subagents/Experiment-Results-Assessment-Agent.md) / 实验结果评估助手 | Actual data; enabled interpreter for nontrivial calculations; honest plan-only fallback. |
| 时间序列基线分析 | [Time Series Baseline Agent](business-subagents/Time-Series-Baseline-Agent.md) / 时间序列基线分析助手 | Actual data; enabled interpreter for nontrivial calculations; honest plan-only fallback. |
| 成本收益测算 | [Cost Benefit Analysis Agent](business-subagents/Cost-Benefit-Analysis-Agent.md) / 成本收益测算助手 | Actual data; enabled interpreter for nontrivial calculations; honest plan-only fallback. |
| SQL查询草稿 | [SQL Query Draft Agent](business-subagents/SQL-Query-Draft-Agent.md) / SQL查询草稿助手 | Readable supplied material; text-only drafting/review with source coverage. |

### 文本与材料加工 (7)

| Original remaining candidate | Definition | Runtime requirement |
| --- | --- | --- |
| 术语表建设 | [Glossary Builder Agent](business-subagents/Glossary-Builder-Agent.md) / 术语表建设助手 | Readable supplied material; text-only drafting/review with source coverage. |
| 引用目录整理 | [Citation Organizer Agent](business-subagents/Citation-Organizer-Agent.md) / 引用目录整理助手 | Readable supplied material; text-only drafting/review with source coverage. |
| 文本脱敏草稿 | [Text Redaction Draft Agent](business-subagents/Text-Redaction-Draft-Agent.md) / 文本脱敏草稿助手 | Readable supplied material; text-only drafting/review with source coverage. |
| 文档索引与定位 | [Document Index Agent](business-subagents/Document-Index-Agent.md) / 文档索引与定位助手 | Readable supplied material; text-only drafting/review with source coverage. |
| 技术内容通俗改写 | [Technical Plain Language Agent](business-subagents/Technical-Plain-Language-Agent.md) / 技术内容通俗改写助手 | Readable supplied material; text-only drafting/review with source coverage. |
| 操作演示脚本 | [Demo Script Draft Agent](business-subagents/Demo-Script-Draft-Agent.md) / 操作演示脚本助手 | Readable supplied material; text-only drafting/review with source coverage. |
| 岗位说明书起草 | [Job Description Draft Agent](business-subagents/Job-Description-Draft-Agent.md) / 岗位说明书起草助手 | Readable supplied material; text-only drafting/review with source coverage. |

### AI应用、培训与评测 (7)

| Original remaining candidate | Definition | Runtime requirement |
| --- | --- | --- |
| 提示词对照评审 | [Prompt Comparison Review Agent](business-subagents/Prompt-Comparison-Review-Agent.md) / 提示词对照评审助手 | Readable supplied material; text-only drafting/review with source coverage. |
| AI输出评分量表设计 | [AI Output Rubric Designer Agent](business-subagents/AI-Output-Rubric-Designer-Agent.md) / AI输出评分量表设计助手 | Readable supplied material; text-only drafting/review with source coverage. |
| RAG检索结果评测 | [RAG Retrieval Evaluation Agent](business-subagents/RAG-Retrieval-Evaluation-Agent.md) / RAG检索结果评测助手 | Actual data; enabled interpreter for nontrivial calculations; honest plan-only fallback. |
| 知识库分块方案 | [Knowledge Chunking Plan Agent](business-subagents/Knowledge-Chunking-Plan-Agent.md) / 知识库分块方案助手 | Readable supplied material; text-only drafting/review with source coverage. |
| AI任务适用性评估 | [AI Task Suitability Agent](business-subagents/AI-Task-Suitability-Agent.md) / AI任务适用性评估助手 | Readable supplied material; text-only drafting/review with source coverage. |
| 概念关系图谱 | [Concept Map Agent](business-subagents/Concept-Map-Agent.md) / 概念关系图谱助手 | Readable supplied material; text-only drafting/review with source coverage. |
| 案例教学材料设计 | [Teaching Case Designer Agent](business-subagents/Teaching-Case-Designer-Agent.md) / 案例教学材料设计助手 | Readable supplied material; text-only drafting/review with source coverage. |

### 业务诊断与决策 (9)

| Original remaining candidate | Definition | Runtime requirement |
| --- | --- | --- |
| 流程瓶颈诊断 | [Process Bottleneck Agent](business-subagents/Process-Bottleneck-Agent.md) / 流程瓶颈诊断助手 | Actual data; enabled interpreter for nontrivial calculations; honest plan-only fallback. |
| 决策标准设计 | [Decision Criteria Designer Agent](business-subagents/Decision-Criteria-Designer-Agent.md) / 决策标准设计助手 | Readable supplied material; text-only drafting/review with source coverage. |
| 业务假设验证方案 | [Business Hypothesis Validation Agent](business-subagents/Business-Hypothesis-Validation-Agent.md) / 业务假设验证方案助手 | Readable supplied material; text-only drafting/review with source coverage. |
| 变更影响分析 | [Change Impact Analysis Agent](business-subagents/Change-Impact-Analysis-Agent.md) / 变更影响分析助手 | Readable supplied material; text-only drafting/review with source coverage. |
| 问题树构建 | [Problem Tree Agent](business-subagents/Problem-Tree-Agent.md) / 问题树构建助手 | Readable supplied material; text-only drafting/review with source coverage. |
| 项目复盘 | [Retrospective Facilitator Agent](business-subagents/Retrospective-Facilitator-Agent.md) / 复盘引导助手 | Readable supplied material; text-only drafting/review with source coverage. |
| RACI职责矩阵 | [RACI Matrix Agent](business-subagents/RACI-Matrix-Agent.md) / RACI职责矩阵助手 | Readable supplied material; text-only drafting/review with source coverage. |
| 工作量估算 | [Workload Estimation Agent](business-subagents/Workload-Estimation-Agent.md) / 工作量估算助手 | Actual data; enabled interpreter for nontrivial calculations; honest plan-only fallback. |
| 客户旅程分析 | [Customer Journey Agent](business-subagents/Customer-Journey-Agent.md) / 客户旅程分析助手 | Readable supplied material; text-only drafting/review with source coverage. |

### 协作、调研与表达训练 (9)

| Original remaining candidate | Definition | Runtime requirement |
| --- | --- | --- |
| 会议议程设计 | [Meeting Agenda Planner Agent](business-subagents/Meeting-Agenda-Planner-Agent.md) / 会议议程规划助手 | Readable supplied material; text-only drafting/review with source coverage. |
| 访谈提纲设计 | [Research Interview Guide Agent](business-subagents/Research-Interview-Guide-Agent.md) / 研究访谈提纲助手 | Readable supplied material; text-only drafting/review with source coverage. |
| 利益相关方沟通地图 | [Stakeholder Communication Map Agent](business-subagents/Stakeholder-Communication-Map-Agent.md) / 利益相关方沟通地图助手 | Readable supplied material; text-only drafting/review with source coverage. |
| 演讲排练反馈 | [Presentation Rehearsal Coach Agent](business-subagents/Presentation-Rehearsal-Coach-Agent.md) / 演讲排练反馈助手 | Actual learner attempt and Hub-carried context; one explicitly simulated turn. |
| 沟通情景角色扮演 | [Workplace Roleplay Coach Agent](business-subagents/Workplace-Roleplay-Coach-Agent.md) / 沟通情景角色扮演助手 | Actual learner attempt and Hub-carried context; one explicitly simulated turn. |
| 实习成果梳理 | [Internship Achievement Agent](business-subagents/Internship-Achievement-Agent.md) / 实习成果梳理助手 | Readable supplied material; text-only drafting/review with source coverage. |
| 项目命名与口号创意 | [Project Naming Agent](business-subagents/Project-Naming-Agent.md) / 项目命名与口号创意助手 | Readable supplied material; text-only drafting/review with source coverage. |
| 团队破冰活动编排 | [Team Icebreaker Agent](business-subagents/Team-Icebreaker-Agent.md) / 团队破冰活动编排助手 | Readable supplied material; text-only drafting/review with source coverage. |
| 商务英语表达练习 | [Business English Practice Agent](business-subagents/Business-English-Practice-Agent.md) / 商务英语表达练习助手 | Actual learner attempt and Hub-carried context; one explicitly simulated turn. |

### 公司内部知识域 (10)

| Original remaining candidate | Definition | Runtime requirement |
| --- | --- | --- |
| HR制度解读 | [HR Policy Explainer Agent](business-subagents/HR-Policy-Explainer-Agent.md) / HR制度解读助手 | Approved applicable domain sources; no invented policy or professional determination. |
| IT服务知识 | [IT Service Knowledge Agent](business-subagents/IT-Service-Knowledge-Agent.md) / IT服务知识助手 | Approved applicable domain sources; no invented policy or professional determination. |
| 报销制度解读 | [Expense Policy Explainer Agent](business-subagents/Expense-Policy-Explainer-Agent.md) / 报销制度解读助手 | Approved applicable domain sources; no invented policy or professional determination. |
| 采购流程知识 | [Procurement Policy Knowledge Agent](business-subagents/Procurement-Policy-Knowledge-Agent.md) / 采购流程知识助手 | Approved applicable domain sources; no invented policy or professional determination. |
| 信息安全知识 | [Information Security Literacy Agent](business-subagents/Information-Security-Literacy-Agent.md) / 信息安全知识助手 | Approved applicable domain sources; no invented policy or professional determination. |
| 隐私保护知识 | [Privacy Knowledge Agent](business-subagents/Privacy-Knowledge-Agent.md) / 隐私保护知识助手 | Approved applicable domain sources; no invented policy or professional determination. |
| 供应链术语 | [Supply Chain Terminology Agent](business-subagents/Supply-Chain-Terminology-Agent.md) / 供应链术语助手 | Approved applicable domain sources; no invented policy or professional determination. |
| 质量体系入门 | [Quality System Intro Agent](business-subagents/Quality-System-Intro-Agent.md) / 质量体系入门助手 | Approved applicable domain sources; no invented policy or professional determination. |
| 临床研究术语 | [Clinical Research Terminology Agent](business-subagents/Clinical-Research-Terminology-Agent.md) / 临床研究术语助手 | Approved applicable domain sources; no invented policy or professional determination. |
| 监管事务术语 | [Regulatory Affairs Terminology Agent](business-subagents/Regulatory-Affairs-Terminology-Agent.md) / 监管事务术语助手 | Approved applicable domain sources; no invented policy or professional determination. |

## Manual Configuration

1. Copy Name, Description, and Instruction from each Markdown definition into the appropriate fields. Configure typed inputs/outputs explicitly where the platform requires them; a JSON code block alone does not create variables.
2. Supply actual inputs, references, and scope from Hub. Do not assume an uploaded filename, inaccessible URL, or semantic snippet is a complete runtime dataset.
3. Enable authorized code execution only for tasks that need it. No database, browser, network, shell, arbitrary package installation, or Excel recalculation engine is assumed.
4. Keep outputs within the confirmed scope. Derived results are session-local drafts or explanations; there is no cloud write-back, automatic collection, outreach, enrollment, publishing, or production change.
5. Preserve the output basis in Hub summaries: proposed, manually checked, computed, source-supported, or explicitly simulated. Never substitute a confident summary for missing evidence.
6. Practice Agents return one turn to Hub; Hub obtains the learner's real attempt and passes needed context back. No cross-session memory or actual voice/body-language assessment is assumed.
7. For domain knowledge, connect or supply relevant approved documents with effective dates, versions, and applicability. Missing evidence returns clarification rather than invented company rules.
8. Keep clinical-research and regulatory terminology explanatory. No personal or general health-action advice, clinical decisions, or professional approval is part of these definitions.
9. Run later manual checks using normal, missing-input, ambiguity, and boundary cases. Do not mark a platform test passed until actual execution evidence exists.

## Boundaries and Overlap

- AI Task Suitability is retained alongside Automation Opportunity; Teaching Case Designer alongside Training Content Draft; Stakeholder Communication Map alongside Change Communication Plan. The user requested expansion first and consolidation later.
- Research Interview Guide is for learning about users/business experiences; Interview Guide is for hiring. Do not confuse their purposes.
- Sampling, A/B design, and experimental evaluation apply to nonclinical business research. They do not design clinical protocols or interpret personal medical outcomes.
- SQL Query Draft generates explained read-only SQL text only. It does not connect, execute, modify data, or validate against an unavailable database engine.
- Text Redaction drafts replacements and residual-risk notes; it cannot certify anonymity or legal compliance.
- Naming proposals have no trademark/domain clearance. Icebreakers are optional and nonphysical, with no forced disclosure or penalties.
- Knowledge agents do not invent HR entitlements, reimbursement limits, procurement thresholds, security incidents, legal conclusions, quality release decisions, or authoritative definitions.
- For genuinely conflicting instructions or missing sources, return the structured clarification/boundary result upstream rather than silently changing the task.

## Manual Acceptance Examples

These are proposed acceptance checks, not reported Copilot Studio executions.

| Definition | Normal check | Boundary or missing-input check |
| --- | --- | --- |
| [Sampling Design Agent](business-subagents/Sampling-Design-Agent.md) | Define a population and precision objective; check selection rules and explicitly justified sample-size inputs. | Missing variability or confidence inputs must not produce a fabricated sample-size guarantee. |
| [AB Experiment Design Agent](business-subagents/AB-Experiment-Design-Agent.md) | Provide a nonclinical product change and outcome; check allocation, metric, analysis, and stopping rules. | No baseline inputs means no claimed powered sample size; clinical trials are outside scope. |
| [Experiment Results Assessment Agent](business-subagents/Experiment-Results-Assessment-Agent.md) | Supply a nonclinical randomized test and denominators; check effect definitions and appropriate uncertainty. | Do not claim causation or significance from incomplete summary figures. |
| [Time Series Baseline Agent](business-subagents/Time-Series-Baseline-Agent.md) | Supply monthly history and a holdout horizon; check leakage-free evaluation. | Insufficient history must not yield invented seasonality or guaranteed forecasts. |
| [Cost Benefit Analysis Agent](business-subagents/Cost-Benefit-Analysis-Agent.md) | Supply implementation and ongoing costs plus explicit benefit assumptions; check horizon and double-counting. | Unknown costs must remain gaps, not an invented positive ROI. |
| [SQL Query Draft Agent](business-subagents/SQL-Query-Draft-Agent.md) | Supply a schema and dialect for a grouped metric; check exact identifiers and grain. | Missing schema must not produce claimed runnable SQL or a fabricated result set. |
| [Glossary Builder Agent](business-subagents/Glossary-Builder-Agent.md) | Extract terms from supplied AI notes with two meanings of one abbreviation. | Do not invent a canonical definition when the source is ambiguous. |
| [Citation Organizer Agent](business-subagents/Citation-Organizer-Agent.md) | Format supplied mixed references and map three in-text citations. | Missing publication dates or identifiers must not be fabricated. |
| [Text Redaction Draft Agent](business-subagents/Text-Redaction-Draft-Agent.md) | Redact synthetic names and identifiers consistently in repeated passages. | No claim of guaranteed anonymity or coverage of unavailable attachments. |
| [Document Index Agent](business-subagents/Document-Index-Agent.md) | Index two supplied documents using headings and actual locators. | An excerpt must not yield a claimed whole-document index. |
| [Technical Plain Language Agent](business-subagents/Technical-Plain-Language-Agent.md) | Rewrite a supplied technical paragraph for nontechnical colleagues. | Do not turn tentative research claims into guaranteed product benefits. |
| [Demo Script Draft Agent](business-subagents/Demo-Script-Draft-Agent.md) | Draft a short demo using supplied verified product steps. | Unknown interface labels remain gaps, not invented controls. |
| [Job Description Draft Agent](business-subagents/Job-Description-Draft-Agent.md) | Draft a role from supplied responsibilities and an approved template. | No invented salary, benefits, reporting line, or personal-trait screening criteria. |
| [Prompt Comparison Review Agent](business-subagents/Prompt-Comparison-Review-Agent.md) | Compare matched actual outputs using the same rubric. | Prompt text alone supports static critique, not a measured accuracy claim. |
| [AI Output Rubric Designer Agent](business-subagents/AI-Output-Rubric-Designer-Agent.md) | Design a rubric for source-grounded summaries with clear failure gates. | No claim that proposed weights or thresholds are empirically validated. |
| [RAG Retrieval Evaluation Agent](business-subagents/RAG-Retrieval-Evaluation-Agent.md) | Evaluate ranked chunks with supplied relevance labels and stated k. | No gold relevant set means no asserted corpus-recall percentage. |
| [Knowledge Chunking Plan Agent](business-subagents/Knowledge-Chunking-Plan-Agent.md) | Chunk supplied policy sections while retaining heading and version context. | No invented token counts or claim that an index has been built. |
| [AI Task Suitability Agent](business-subagents/AI-Task-Suitability-Agent.md) | Assess a repetitive text task with explicit review and data constraints. | Missing baselines must not produce promised savings or guaranteed suitability. |
| [Concept Map Agent](business-subagents/Concept-Map-Agent.md) | Map concepts from a supplied introductory lesson with labeled relations. | Do not turn an associated concept into a proven cause. |
| [Teaching Case Designer Agent](business-subagents/Teaching-Case-Designer-Agent.md) | Design an explicitly fictional office AI case with source-grounded instructor notes. | Do not attribute fictional success or private events to a real company. |
| [Process Bottleneck Agent](business-subagents/Process-Bottleneck-Agent.md) | Supply case-level timestamps and check waiting versus processing time. | Incomplete logs must not produce precise throughput or savings claims. |
| [Decision Criteria Designer Agent](business-subagents/Decision-Criteria-Designer-Agent.md) | Design gates and preferences for a supplied tool-selection objective. | No arbitrary official weights or option selection without evidence. |
| [Business Hypothesis Validation Agent](business-subagents/Business-Hypothesis-Validation-Agent.md) | Turn a proposed user-need assumption into observable validation evidence. | Do not label a hypothesis validated before any evidence is supplied. |
| [Change Impact Analysis Agent](business-subagents/Change-Impact-Analysis-Agent.md) | Map a supplied process change to roles, data and controls. | Unknown dependencies remain gaps, not an asserted complete impact analysis. |
| [Problem Tree Agent](business-subagents/Problem-Tree-Agent.md) | Decompose a supplied adoption problem into researchable subquestions. | Do not report a proposed causal branch as a verified cause. |
| [Retrospective Facilitator Agent](business-subagents/Retrospective-Facilitator-Agent.md) | Review a supplied project timeline including a success and a missed goal. | Do not invent lessons, results, or blame from absent evidence. |
| [RACI Matrix Agent](business-subagents/RACI-Matrix-Agent.md) | Map supplied roles and deliverables and surface missing accountability. | A proposal must not create real decision authority. |
| [Workload Estimation Agent](business-subagents/Workload-Estimation-Agent.md) | Estimate provided task volumes using stated time and availability inputs. | No invented productivity, staffing savings, or guaranteed dates. |
| [Customer Journey Agent](business-subagents/Customer-Journey-Agent.md) | Map supplied interview excerpts to actual touchpoints with references. | No fictional customer history or inferred private emotions presented as facts. |
| [Meeting Agenda Planner Agent](business-subagents/Meeting-Agenda-Planner-Agent.md) | Plan a 30-minute decision meeting and check time totals. | Do not imply participants agreed or a calendar event was created. |
| [Research Interview Guide Agent](business-subagents/Research-Interview-Guide-Agent.md) | Design a neutral guide to study colleagues' AI-tool experiences. | No invented interview answers or diagnostic/hiring evaluation. |
| [Stakeholder Communication Map Agent](business-subagents/Stakeholder-Communication-Map-Agent.md) | Map supplied project roles to information needs and approval gates. | Do not infer named colleagues' attitudes or claim messages were sent. |
| [Presentation Rehearsal Coach Agent](business-subagents/Presentation-Rehearsal-Coach-Agent.md) | Review a supplied talk transcript against audience and time goals. | No invented delivery observations or guaranteed applause. |
| [Workplace Roleplay Coach Agent](business-subagents/Workplace-Roleplay-Coach-Agent.md) | Practice a fictional scope-negotiation conversation one turn at a time. | No real-person mind reading, invented user replies, or coercive scripts. |
| [Internship Achievement Agent](business-subagents/Internship-Achievement-Agent.md) | Summarize evidenced internship tasks with honest contribution attribution. | No inflated savings, titles, deployment claims, or invented achievements. |
| [Project Naming Agent](business-subagents/Project-Naming-Agent.md) | Generate project names with supplied tone and prohibited terms. | Do not claim trademark or domain clearance or promise product results. |
| [Team Icebreaker Agent](business-subagents/Team-Icebreaker-Agent.md) | Design a five-minute online icebreaker with a pass option. | No forced disclosure, physical challenge, humiliation, or prizes requiring spending. |
| [Business English Practice Agent](business-subagents/Business-English-Practice-Agent.md) | Review a supplied English update and explain respectful alternatives. | No pronunciation or certified proficiency claims from text alone. |
| [HR Policy Explainer Agent](business-subagents/HR-Policy-Explainer-Agent.md) | Supply an approved relevant extract and ask a general concept question; check citations and applicability. | No source means clarification, not invented rules. Requests for individual decisions or prohibited actions remain outside scope. |
| [IT Service Knowledge Agent](business-subagents/IT-Service-Knowledge-Agent.md) | Supply an approved relevant extract and ask a general concept question; check citations and applicability. | No source means clarification, not invented rules. Requests for individual decisions or prohibited actions remain outside scope. |
| [Expense Policy Explainer Agent](business-subagents/Expense-Policy-Explainer-Agent.md) | Supply an approved relevant extract and ask a general concept question; check citations and applicability. | No source means clarification, not invented rules. Requests for individual decisions or prohibited actions remain outside scope. |
| [Procurement Policy Knowledge Agent](business-subagents/Procurement-Policy-Knowledge-Agent.md) | Supply an approved relevant extract and ask a general concept question; check citations and applicability. | No source means clarification, not invented rules. Requests for individual decisions or prohibited actions remain outside scope. |
| [Information Security Literacy Agent](business-subagents/Information-Security-Literacy-Agent.md) | Supply an approved relevant extract and ask a general concept question; check citations and applicability. | No source means clarification, not invented rules. Requests for individual decisions or prohibited actions remain outside scope. |
| [Privacy Knowledge Agent](business-subagents/Privacy-Knowledge-Agent.md) | Supply an approved relevant extract and ask a general concept question; check citations and applicability. | No source means clarification, not invented rules. Requests for individual decisions or prohibited actions remain outside scope. |
| [Supply Chain Terminology Agent](business-subagents/Supply-Chain-Terminology-Agent.md) | Supply an approved relevant extract and ask a general concept question; check citations and applicability. | No source means clarification, not invented rules. Requests for individual decisions or prohibited actions remain outside scope. |
| [Quality System Intro Agent](business-subagents/Quality-System-Intro-Agent.md) | Supply an approved relevant extract and ask a general concept question; check citations and applicability. | No source means clarification, not invented rules. Requests for individual decisions or prohibited actions remain outside scope. |
| [Clinical Research Terminology Agent](business-subagents/Clinical-Research-Terminology-Agent.md) | Supply an approved relevant extract and ask a general concept question; check citations and applicability. | No source means clarification, not invented rules. Requests for individual decisions or prohibited actions remain outside scope. |
| [Regulatory Affairs Terminology Agent](business-subagents/Regulatory-Affairs-Terminology-Agent.md) | Supply an approved relevant extract and ask a general concept question; check citations and applicability. | No source means clarification, not invented rules. Requests for individual decisions or prohibited actions remain outside scope. |

## Suggested End-to-End Checks

- Evidence-based report: supplied data -> Metric Definition Designer -> SQL Query Draft or existing data preparation -> actual separately supplied results -> Data Insight -> Data Visualization -> citation/clarity review as needed.
- Research study: Sampling Design -> Questionnaire Design or Research Interview Guide -> separately collected supplied evidence -> Qualitative Text Coding -> Customer Feedback Analysis or Data Insight.
- Experiment: AB Experiment Design -> separately run nonclinical experiment -> actual supplied results -> Experiment Results Assessment -> Business Report Draft.
- Knowledge preparation: Glossary Builder -> Document Index or Knowledge Chunking Plan -> later configured retrieval -> supplied retrieval run -> RAG Retrieval Evaluation.
- Organizational change: Change Impact Analysis -> Stakeholder Communication Map or Change Communication Plan -> Training Lesson Plan/Teaching Case Designer -> draft communication.
- Presentation practice: supplied factual material -> Presentation Storyline -> Presentation Rehearsal Coach or Elevator Pitch Coach -> actual learner attempt -> focused feedback.

These are optional compositions, not automatic execution chains. Finder matches needs, Workflow Builder plans complex dependencies, and Executor runs the confirmed scope. Collecting data, running a real experiment, building an index, or contacting people is not performed by these definitions.
