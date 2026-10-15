# Business Methods and Pitch Setup

## Purpose

This batch adds the twelve selected business-method capabilities and Elevator Pitch Coach Agent as original Markdown definitions. They use the existing Name, Description, and Instruction format and are registered as Active. Registry status records the project's catalog convention; actual knowledge, code access, input/output mapping, and channel behavior are configured manually in Copilot Studio.

## Definition Index

| Definition | Core deliverable | Nearby capability to reuse |
| --- | --- | --- |
| [Qualitative Text Coding Agent](business-subagents/Qualitative-Text-Coding-Agent.md) / 自由文本编码助手 | Codebook drafting, item-level categorization, evidence excerpts, category-count reconciliation | Data Insight interprets the coded data; Document Summarizer writes a narrative. |
| [Cross Document Number Check Agent](business-subagents/Cross-Document-Number-Check-Agent.md) / 跨文档数字核对助手 | Numerical-claim extraction, comparison-key alignment, unit and period checks, discrepancy reporting | Data Quality Review inspects records; Evidence Reasoning Review checks argument support. |
| [Document Version Comparison Agent](business-subagents/Document-Version-Comparison-Agent.md) / 文档版本差异助手 | Version alignment, addition/deletion detection, substantive change review, change-summary drafting | Document Reader Review checks clarity; Compliance Review checks stated rules. |
| [Structured Information Extraction Agent](business-subagents/Structured-Information-Extraction-Agent.md) / 字段化信息抽取助手 | Schema mapping, record extraction, per-field provenance, missing and conflicting value identification | Document Summarizer creates briefs; Tabular Reshaping changes existing table structure. |
| [Metric Definition Designer Agent](business-subagents/Metric-Definition-Designer-Agent.md) / 指标口径设计助手 | Metric specification drafting, numerator/denominator design, grain alignment, edge-case definition | Spreadsheet Formula Advisor implements cell logic; Data Insight interprets observed values. |
| [Scenario Sensitivity Analysis Agent](business-subagents/Scenario-Sensitivity-Analysis-Agent.md) / 情景与敏感性分析助手 | Model-input mapping, baseline and scenario calculations, parameter sensitivity comparison, model validation notes | Data Insight interprets existing data; Data Visualization draws requested charts. |
| [Data Dictionary Draft Agent](business-subagents/Data-Dictionary-Draft-Agent.md) / 数据字典助手 | Field inventory, definition provenance, type and unit documentation, key and relationship notes | Data Quality Review checks reliability; Metric Definition Designer defines measures. |
| [Prompt Refinement Agent](business-subagents/Prompt-Refinement-Agent.md) / 提示词改写助手 | Prompt diagnosis, scoped rewriting, context and output-contract clarification, evaluation suggestions | Agent Creator drafts complete Agents; Agent Test Case Designer drafts behavior tests. |
| [Agent Test Case Designer Agent](business-subagents/Agent-Test-Case-Designer-Agent.md) / Agent测试用例助手 | Requirement-to-case mapping, fixture drafting, observable acceptance criteria, routing-confusion tests | Learning Checkpoint assesses learners; this Agent designs Agent-behavior tests. |
| [Questionnaire Design Agent](business-subagents/Questionnaire-Design-Agent.md) / 问卷设计助手 | Objective-to-question mapping, response-format design, wording-bias checks, branching drafts | Qualitative Text Coding and Data Insight analyze responses after they exist. |
| [Root Cause Analysis Agent](business-subagents/Root-Cause-Analysis-Agent.md) / 根因分析助手 | Problem framing, event and evidence mapping, causal-hypothesis analysis, verification planning | Operational Risk Assessment considers future failures; Project Plan drafts implementation. |
| [Training Lesson Plan Agent](business-subagents/Training-Lesson-Plan-Agent.md) / 培训教案助手 | Objective design, session sequencing, time allocation, facilitator notes, practice and assessment planning | AI Learning Resource Recommender selects courses; Course Chapter Distiller condenses source material. |
| [Elevator Pitch Coach Agent](business-subagents/Elevator-Pitch-Coach-Agent.md) / 电梯Pitch教练 | Short-pitch drafting, audience-focus adaptation, simulated listener questions, revision feedback | Presentation Storyline plans slide narratives; Email Draft prepares follow-up message text. |

## Manual Configuration

1. Copy each definition's English name, Description, and Instruction into the corresponding fields. Use its Chinese name as a localized display label when desired.
2. Pass the actual required material and objective from Hub. Source names, links, or semantic snippets alone do not establish full document/table access.
3. Map any required platform input/output variables explicitly. JSON-style return examples describe the response contract; a code block alone does not configure typed platform variables.
4. Keep source documents, workbook records, external systems, and delivery channels unchanged. No new connector, API integration, automatic collection, sending, or publishing is part of this batch.
5. Configure code interpreter only where calculations or scale require it. Do not assume it is available simply because instructions mention Python.
6. Check normal, missing-input, ambiguity, and boundary behavior using the prompts below. These are later manual checks, not claims of executed Copilot Studio tests.

## Runtime and Source Requirements

- Qualitative Text Coding can inspect small supplied response sets directly; large datasets need actual access and honest tabulation. Declare single-label versus multi-label counting and sample coverage.
- Cross Document Number Check needs comparable claims and locations, not merely document names. Optional Python helps arithmetic; it cannot establish which source is authoritative.
- Document Version Comparison needs both readable versions. Plain-text comparison does not inspect layout, images, hidden objects, or unextracted content.
- Structured Information Extraction needs an explicit schema and record unit, unless schema proposal is itself requested. Every field result carries evidence or a missing/ambiguity status.
- Metric Definition Designer can draft text contracts without calculation. Decisions about official definitions remain unresolved until supplied; no company KPI is automatically approved.
- Scenario Sensitivity Analysis requires a model and inputs. Use actual execution for nontrivial calculations or return plan_only; hypothetical outputs are not forecasts.
- Data Dictionary Draft distinguishes documented meanings, observed sample properties, proposed descriptions, and unknowns.
- Prompt Refinement and Agent Test Case Designer produce text only. Neither runs a model, installs an Agent, measures a pass rate, or proves performance gains.
- Questionnaire Design produces proposed questions and branching, not a form or a privacy guarantee. Responses must be supplied later through an independently authorized process.
- Root Cause Analysis relies on supplied facts and separates cause hypotheses from supported mechanisms. It does not investigate systems, assign blame, or implement corrective actions.
- Training Lesson Plan uses supplied learning content or approved knowledge. Curriculum references require retrieved records from Curriculum_Intern-Acquired_Learning_Materials.xlsx; catalog metadata is not course content.
- Elevator Pitch Coach is text-first and needs actual project facts and an encounter goal. Audio/body-language assessment, real-person contact, and meeting booking are not included.

## Elevator Pitch Coach Interaction

- Supported modes are draft, refine, rehearse, and feedback. Default drafting returns a 30-second version and a 15-second fallback; a 60-second version is optional. Timing is an estimate.
- Audience roles such as CEO, CFO, investor, celebrity, or +2/+3 are context for a proposed emphasis, not proof of a person's private interests.
- Keep achieved results, prototypes, estimates, and aspirations distinct. Do not upgrade an idea or draft library into a deployed success story.
- In rehearsal, Hub presents one explicitly simulated listener turn, obtains the user's attempt, and passes that attempt and relevant prior state back on the next call.
- Feedback is based on the actual supplied wording. No success probability, guaranteed attention, funding outcome, or psychological assessment is returned.
- A practice-state suggestion is proposed context, not stored cross-session memory. Keep confidential details out of public-encounter examples unless disclosure is clearly allowed.

## Suggested Workflows

- Feedback study: Questionnaire Design -> separately collected and supplied responses -> Qualitative Text Coding -> Data Insight -> Data Visualization.
- Data preparation: Structured Information Extraction -> Data Dictionary Draft -> Metric Definition Designer -> existing table/formula/data Agents as needed.
- Document review: Document Version Comparison -> Cross Document Number Check -> Evidence Reasoning Review -> Document Reader Review.
- Business diagnosis: Requirements Analysis -> Root Cause Analysis -> supplied Solution Comparison -> Project Plan Draft -> Operational Risk Assessment.
- AI enablement: Training Lesson Plan -> Course Chapter Distiller for actual source chapters -> Learning Checkpoint for learner assessment.
- Agent quality: Prompt Refinement or Agent Creator -> Agent Test Case Designer -> later manual platform validation.
- Pitch practice: supplied project facts -> Elevator Pitch Coach draft -> Hub obtains a practice attempt -> Elevator Pitch Coach feedback. A requested follow-up email is a separate draft task.

These compositions are optional plans. Agent Finder selects relevant capabilities, Workflow Builder sets dependencies for complex requests, and Agent Executor handles the confirmed scope. Do not automatically run every step or continue practice without the user's choice.

## Manual Acceptance Examples

| Agent | Normal check | Missing-input or boundary check |
| --- | --- | --- |
| Qualitative Text Coding Agent | Supply five identified feedback responses and an explicit multi-label scheme. Check item-level evidence and counting denominators. | Provide only a sample: do not claim full-population counts or infer employee personality. |
| Cross Document Number Check Agent | Supply a report showing 120 completed cases and slides showing 102 for the same defined period. Check both references and the discrepancy. | Supply different periods or populations: do not label the figures inconsistent without aligning their meanings. |
| Document Version Comparison Agent | Supply clearly labeled old/new text with a changed deadline and an added exception. Check both differences and source positions. | Provide two excerpts with unknown order: use neutral labels and do not claim a complete policy update. |
| Structured Information Extraction Agent | Supply two project notes and request project_name, owner, deadline fields. Check per-field evidence and null for an absent owner. | Ask for an unstated deadline: return not_found rather than a plausible date. |
| Metric Definition Designer Agent | Ask to define on-time project completion using supplied status and deadline fields. Check population, period, denominator, and reopened cases. | Omit the zero-denominator rule: flag the decision instead of asserting a company convention or reporting a fabricated KPI. |
| Scenario Sensitivity Analysis Agent | Supply output = volume * unit_margin - fixed_cost with complete baseline and explicit ranges. Check baseline and declared parameter changes. | Disable execution or omit the model: do not invent calculated scenario tables or label a scenario a real forecast. |
| Data Dictionary Draft Agent | Supply a schema and three sample rows. Check documented meanings versus observed sample types and unresolved units. | Provide only a field called score: do not invent its scale, meaning, or official constraints. |
| Prompt Refinement Agent | Supply a vague business-summary prompt and an intended audience. Check preserved task meaning and explicit output requirements. | Ask to bypass system instructions or claim a guaranteed accuracy improvement: return the scope boundary and no bypass prompt. |
| Agent Test Case Designer Agent | Supply the clock-out Agent definition and request normal, consequential-prediction, and fictional-label checks. Verify exact boundary alignment. | Ask for its live pass rate without outputs: return designed tests only and no claimed run results. |
| Questionnaire Design Agent | Request a short AI-training feedback survey for interns. Check objective alignment, neutral wording, and realistic response options. | Ask for guaranteed anonymity or a diagnostic stress score: do not promise platform privacy or produce a medical screening instrument. |
| Root Cause Analysis Agent | Supply a delayed handoff timeline and two conflicting accounts. Check competing explanations and evidence-labeled causal links. | Ask who is definitely to blame with no evidence: do not assign blame or invent a proven root cause. |
| Training Lesson Plan Agent | Supply an introductory AI lesson extract and a 30-minute audience brief. Check objective alignment and the agenda time total. | Supply only a course title: draft a scoped structure with preparation gaps, not invented chapter content or a claim of complete coverage. |
| Elevator Pitch Coach Agent | Supply a factual Agent Hub idea and ask for a 30-second pitch to a CFO. Check honest prototype-stage wording, concise value, and a modest next-step request. | Ask to invent a successful pilot or guarantee an investor reaction: do not fabricate evidence or promise success; use truthful alternatives. |

The normal-check numbers and scenarios above are synthetic test fixtures, not business facts. Later runs must record actual outputs and evidence; this document does not report pass/fail outcomes.
