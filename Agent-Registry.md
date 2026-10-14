# Agent Registry

## Description

Central Markdown registry for Agent metadata used by Agent Finder to browse, retrieve, match, score, and recommend Agents.

## Instruction

This file is the single source of truth for Agent classification, counts, and recommendation metadata. Keep it Markdown-only. Do not create JSON configuration files or databases for registry data at this stage.

Registry rules:
- Distinguish the standalone main Agent, Functional Agents, and Business Subagents.
- Agent Hub is the standalone main Agent and is not included in ordinary Business Subagent recommendation or ranking.
- Functional Agents are platform components and are not included in ordinary Business Subagent recommendation or ranking.
- Business Subagents are callable business Agents stored in `business-subagents/` and are the main retrieval target for Agent Finder.
- Each Business Subagent must have exactly one Primary Category.
- Each Business Subagent can have multiple Capability Tags and Domain Tags.
- Do not add a Business Subagent to Active status unless its Markdown definition is ready enough for discovery and use.

Primary Category values:
- Knowledge and Research
- Document and Content
- Data and Analytics
- Business Operations
- Communication and Collaboration
- Development and Technology
- Compliance and Quality
- Specialized Business

Common Capability Tags:
- Search
- Retrieve
- Extract
- Compare
- Analyze
- Validate
- Summarize
- Generate
- Automate

Common Domain Tags:
- Clinical Research
- Regulatory
- Finance
- HR
- Supply Chain

Status values:
- Active: can be recommended and can be executed after user confirmation.
- Draft: can be browsed or discussed but should not be recommended for execution.
- Deprecated: should not be recommended unless the user explicitly asks about it.
- Unavailable: cannot be executed and should not be recommended for execution.

Permission Level values:
- Read-only: can inspect, retrieve, summarize, or analyze information without changing external state.
- Draft-only: can generate drafts, plans, recommendations, or content but cannot send, publish, modify, or submit anything.
- External Action: can perform outward-facing actions such as sending messages, creating tickets, or triggering external workflows after confirmation.
- Data Modification: can create, update, delete, submit, or otherwise modify records, files, systems, or business data after confirmation.

Date rule:
- Last Updated must use `YYYY-MM-DD` format.

Registry fields:
- Name
- Chinese Name
- Type
- Primary Category
- Capability Tags
- Domain Tags
- Description
- Keywords
- Capabilities
- Use When
- Limitations
- Permission Level
- Status
- Last Updated

## Main Agent

| Name | Type | Description | Status | Last Updated |
| --- | --- | --- | --- | --- |
| Agent Hub | Main Agent | Main user-facing Agent for intent understanding, routing, confirmation, and final response. | Active | 2026-10-14 |

## Functional Agents

| Name | Type | Description | Status | Last Updated |
| --- | --- | --- | --- | --- |
| Agent Finder | Functional Agent | Registry-based discovery, matching, scoring, and recommendation. | Active | 2026-10-14 |
| Workflow Builder | Functional Agent | Decomposes complex tasks into executable Workflow Blueprints. | Active | 2026-10-14 |
| Agent Executor | Functional Agent | Handles authorized execution scheduling, status tracking, and result aggregation. | Active | 2026-10-14 |
| Agent Creator | Functional Agent | Analyzes capability gaps, searches reusable internal or external solutions, and drafts new Agent definitions only when needed. | Active | 2026-10-14 |

## Business Subagents

| Name | Chinese Name | Type | Primary Category | Capability Tags | Domain Tags | Description | Keywords | Capabilities | Use When | Limitations | Permission Level | Status | Last Updated |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Research Scout Agent | 研究侦察智能体 | Business Subagent | Knowledge and Research | Search, Retrieve, Compare, Summarize | General Research, Market Research, Technology | Finds, compares, and summarizes information from provided sources or approved web searches for research-oriented tasks. | research, search, source review, compare, brief | Source discovery, evidence extraction, comparison, research synthesis | Use for topic research, market scans, competitor research, technology research, or source summaries. | Does not perform external actions or treat low-confidence sources as authoritative. | Read-only | Active | 2026-10-14 |
| Document Summarizer Agent | 文档总结智能体 | Business Subagent | Document and Content | Extract, Summarize, Analyze | General Business, Documentation | Summarizes documents into briefs, key points, decisions, risks, and action items. | document, summary, notes, transcript, action items | Document summarization, decision extraction, risk extraction, action item extraction | Use for documents, notes, articles, reports, policies, transcripts, or long text. | Does not invent missing details or provide professional approval. | Read-only | Active | 2026-10-14 |
| Data Insight Agent | 数据洞察智能体 | Business Subagent | Data and Analytics | Analyze, Compare, Summarize | Finance, Operations, Sales, HR | Analyzes provided data or metrics to identify trends, anomalies, drivers, and business insights. | data, metrics, KPI, trend, anomaly, insight | Trend analysis, anomaly detection, metric comparison, business insight generation | Use for KPI reviews, metric analysis, survey results, financial metrics, or performance data. | Does not modify data or claim statistical certainty without sufficient evidence. | Read-only | Active | 2026-10-14 |
| Email Draft Agent | 邮件草稿智能体 | Business Subagent | Communication and Collaboration | Generate, Summarize | General Business, Communication | Drafts clear business emails, replies, follow-ups, and stakeholder messages without sending them. | email, draft, reply, follow-up, message | Email drafting, rewriting, tone adjustment, subject line generation | Use for preparing emails, replies, stakeholder updates, or follow-up messages. | Draft-only; does not send messages or claim delivery. | Draft-only | Active | 2026-10-14 |
| Compliance Review Agent | 合规审查智能体 | Business Subagent | Compliance and Quality | Validate, Analyze, Compare | Regulatory, Legal, Quality | Reviews provided content against stated rules, policies, or requirements and flags potential issues. | compliance, policy, review, quality, regulatory, risk | Policy review, issue identification, severity classification, remediation suggestion | Use before sending, publishing, submitting, or approving content that must meet defined criteria. | Does not provide legal certification or final regulatory approval. | Read-only | Active | 2026-10-14 |
| GitHub Repository Research Agent | GitHub 仓库研究智能体 | Business Subagent | Development and Technology | Search, Retrieve, Compare, Analyze | Technology, Open Source, Agent Development | Searches and evaluates GitHub repositories, examples, and open-source patterns for reusable technical or Agent designs. | GitHub, repository, template, open source, agent pattern, reusable design | Repository search, reuse evaluation, risk notes, license signal review | Use when searching for technical examples, Agent templates, repositories, or implementation references. | Does not install, clone, execute, or approve license safety. | Read-only | Active | 2026-10-14 |
| Capability Registry Manager Agent | 能力目录管理助手 | Business Subagent | Business Operations | Analyze, Compare, Validate, Summarize | Agent Governance, Enterprise Architecture, Operations | Manages and reviews enterprise Agent capability information to keep the Agent Registry clear, consistent, and non-duplicative. | capability registry, agent catalog, metadata, duplicate capabilities, governance | Registry review, metadata cleanup, duplicate capability detection, catalog governance | Use when managing Agent Registry quality, reviewing capability metadata, or checking whether proposed Agents duplicate existing ones. | Does not directly modify Registry content, create Agents, or activate Agents. | Read-only | Active | 2026-10-14 |
| Agent Portfolio Advisor Agent | 智能体组合规划助手 | Business Subagent | Business Operations | Analyze, Compare, Summarize, Validate | Agent Governance, Enterprise Architecture, Portfolio Planning | Analyzes enterprise Agent portfolio coverage, duplicate capabilities, capability gaps, and optimization opportunities. | agent portfolio, coverage, capability gaps, duplicate agents, roadmap, optimization | Portfolio coverage analysis, gap detection, duplicate capability analysis, roadmap recommendations | Use for enterprise Agent portfolio planning, duplicate reduction, coverage analysis, and capability investment recommendations. | Does not make investment decisions, modify Registry data, or retire Agents without human review. | Read-only | Active | 2026-10-14 |
