# Business Subagents

## Description

Folder for future Business Subagent Markdown definitions used by Agent Finder, Workflow Builder, and Agent Executor.

## Introduction

Store only Business Subagent Markdown files in this folder. Do not add Python, JSON, or implementation code at this stage.

Each Business Subagent file must use:
- Name
- Description
- Introduction

Name requirements:
- Include English name as the main heading.
- Include Chinese name below the heading.

Description requirements:
- Keep it short.
- State the core capability and when to use the Subagent.

Introduction requirements:
- Define responsibilities, trigger conditions, input requirements, output expectations, execution rules, limitations, and structured result format.
- Keep the file under 8000 characters.
- Return upstream results as JSON-like objects inside Markdown code blocks when needed.

Registry requirements:
- Add Business Subagent metadata to `Agent-Registry.md` before it is discoverable by Agent Finder.
- Keep Name, Chinese Name, Description, Primary Category, Capability Tags, Domain Tags, Permission Level, Status, and Last Updated consistent between the Subagent file and Agent Registry.
- Use exactly one Primary Category.
- Use multiple Capability Tags and Domain Tags when useful.
- Use one fixed Status value: Active, Draft, Deprecated, or Unavailable.
- Use one fixed Permission Level value: Read-only, Draft-only, External Action, or Data Modification.
- Use `YYYY-MM-DD` for Last Updated.

Primary Category values:
- Knowledge and Research
- Document and Content
- Data and Analytics
- Business Operations
- Communication and Collaboration
- Development and Technology
- Compliance and Quality
- Specialized Business
