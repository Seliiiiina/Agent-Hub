# Agent Registry

## Description

Central Markdown registry for Agent metadata used by Agent Finder to browse, retrieve, match, score, and recommend Agents.

## Introduction

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
| Agent Creator | Functional Agent | Analyzes capability gaps and drafts new Agent definitions. | Active | 2026-10-14 |

## Business Subagents

No Business Subagents are registered yet. Add future Subagents here using the registry fields above.
