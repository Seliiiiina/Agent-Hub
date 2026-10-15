# Anthropic Skill Adaptation Notes

## Purpose

This batch uses the capability areas in [Anthropic's example skills repository](https://github.com/anthropics/skills/tree/main/skills) as design references for original Agent Hub Subagents. All 19 requested SKILL.md files were reviewed on 2026-10-15.

The repository's [README](https://github.com/anthropics/skills/blob/main/README.md) describes examples spanning Creative & Design, Development & Technical, Enterprise & Communication, and Document Skills. These are reference areas, not an official per-skill Primary Category schema. Agent Hub continues to use its existing eight-category taxonomy and Registry metadata.

## Adaptation Principles

- Deduplicate by capability, required input, and deliverable rather than create a new Agent for each file extension or original skill name.
- Prefer text deliverables and calculations on provided data. No SDK/API integration, deployment, application control, browser testing, cloud write-back, or external delivery is included.
- Retain skills only as design references. The original instructions, tools, triggers, scripts, templates, branding, and runtime assumptions are not installed or copied.
- Agent Hub's main/functional/business Agent boundaries remain in force. New definitions return structured results upstream and are registered as Active under the project's established convention.
- The source README distinguishes open-source examples from source-available document skills. No blanket license assumption is made; this batch independently expresses capability requirements and retains source links.

## Source-by-Source Decision

The reference-area labels below are our adaptation labels. There are 8 Adapt decisions, 5 Reuse decisions, and 6 Defer decisions. Several sources combine into one definition, while xlsx contributes three distinct definitions; the result is 8 new Business Subagents.

| Source skill | Reference area | Decision | Agent Hub destination | Rationale and boundary |
| --- | --- | --- | --- | --- |
| [academy-guide](https://github.com/anthropics/skills/blob/main/skills/academy-guide/SKILL.md) | Learning resources | Reuse | AI Learning Resource Recommender; AI Tool Guide | Existing course matching and product onboarding cover the goal; use the connected internal curriculum rather than importing a Claude-specific catalog. |
| [algorithmic-art](https://github.com/anthropics/skills/blob/main/skills/algorithmic-art/SKILL.md) | Creative and design | Defer | None | The main deliverable depends on p5.js and interactive HTML generation; a generic art concept alone does not justify a new Agent now. |
| [brand-guidelines](https://github.com/anthropics/skills/blob/main/skills/brand-guidelines/SKILL.md) | Enterprise branding | Reuse | Compliance Review Agent | Checking supplied brand rules is an existing criteria-based review. New visual proposals use Visual Design Brief Agent; never import Anthropic's brand. |
| [canvas-design](https://github.com/anthropics/skills/blob/main/skills/canvas-design/SKILL.md) | Creative and design | Adapt | Visual Design Brief Agent | Keep the textual visual brief; defer rendered posters, PNG/PDF creation, and original canvas tooling. |
| [claude-api](https://github.com/anthropics/skills/blob/main/skills/claude-api/SKILL.md) | Development and technical | Defer | None | Provider SDK integration and execution are outside the current connector-free scope. General tool explanations can use AI Tool Guide. |
| [discernment-nudge](https://github.com/anthropics/skills/blob/main/skills/discernment-nudge/SKILL.md) | Reasoning review | Adapt | Evidence Reasoning Review Agent | Make evidence and assumption review an explicit task, not an automatic nudge on every Hub answer. |
| [doc-coauthoring](https://github.com/anthropics/skills/blob/main/skills/doc-coauthoring/SKILL.md) | Document workflow | Adapt | Document Reader Review Agent | Existing Agents draft reports, SOPs, and requirements. Add the uncovered reader-comprehension check; do not claim independent reader testing. |
| [docx](https://github.com/anthropics/skills/blob/main/skills/docx/SKILL.md) | Document processing | Reuse | Document Summarizer Agent; Business Report Draft Agent; SOP Draft Agent | Reuse semantic reading and drafting. Word file generation, tracked changes, templates, and binary editing are deferred. |
| [frontend-design](https://github.com/anthropics/skills/blob/main/skills/frontend-design/SKILL.md) | Creative and design | Adapt | Visual Design Brief Agent | Retain a text-only interface visual direction; defer frontend code, behavior, hosting, and implementation. |
| [internal-comms](https://github.com/anthropics/skills/blob/main/skills/internal-comms/SKILL.md) | Enterprise communication | Adapt | Internal FAQ Draft Agent | Emails and reports already exist. Add only reusable source-grounded FAQs; newsletters and updates can compose existing drafts. |
| [mcp-builder](https://github.com/anthropics/skills/blob/main/skills/mcp-builder/SKILL.md) | Development and technical | Defer | None | MCP server development, authentication, and external service integration require implementation work outside this batch. |
| [pdf](https://github.com/anthropics/skills/blob/main/skills/pdf/SKILL.md) | Document processing | Reuse | Document Summarizer Agent | Reuse reading of accessible text; do not promise scan OCR, form filling, encryption, merge/split, or PDF file generation. |
| [pptx](https://github.com/anthropics/skills/blob/main/skills/pptx/SKILL.md) | Document processing | Adapt | Presentation Storyline Agent | Add slide-by-slide narrative and speaker-note text. Do not promise a PPTX file, layout rendering, or template modification. |
| [skill-creator](https://github.com/anthropics/skills/blob/main/skills/skill-creator/SKILL.md) | Agent development | Reuse | Agent Creator; Capability Registry Manager Agent | Existing components draft Agent definitions and review overlap/metadata. Skill installation and benchmark execution are not added. |
| [slack-gif-creator](https://github.com/anthropics/skills/blob/main/skills/slack-gif-creator/SKILL.md) | Creative media | Defer | None | Animation rendering and Slack-specific delivery/validation are outside the selected text/data scope. |
| [theme-factory](https://github.com/anthropics/skills/blob/main/skills/theme-factory/SKILL.md) | Creative and design | Adapt | Visual Design Brief Agent | Combine theme proposals with the visual brief. Do not import the original theme gallery or claim styles were applied to files. |
| [web-artifacts-builder](https://github.com/anthropics/skills/blob/main/skills/web-artifacts-builder/SKILL.md) | Development and technical | Defer | None | Bundling interactive web artifacts needs a frontend runtime and build process; no placeholder builder Agent is created. |
| [webapp-testing](https://github.com/anthropics/skills/blob/main/skills/webapp-testing/SKILL.md) | Development and technical | Defer | None | Browser automation and application tests need runtime access; no claims of unperformed tests or screenshots. |
| [xlsx](https://github.com/anthropics/skills/blob/main/skills/xlsx/SKILL.md) | Spreadsheet and data | Adapt | Spreadsheet Formula Advisor Agent; Tabular Reshaping Agent; Data Visualization Agent | Keep three distinct gaps: formula logic, derived table structure, and chart delivery. Reuse Data Insight Agent and Data Quality Review Agent for existing analysis and audits. |

## New Definitions and Existing-Capability Boundaries

| New definition | Distinct deliverable | Existing capability to reuse |
| --- | --- | --- |
| [Evidence Reasoning Review Agent](business-subagents/Evidence-Reasoning-Review-Agent.md) | Claim-evidence map and reasoning gaps | Compliance Review checks stated rules; Data Quality Review checks source data |
| [Document Reader Review Agent](business-subagents/Document-Reader-Review-Agent.md) | Reader comprehension and clarity findings | Business Report Draft, SOP Draft, and Requirements Analysis already draft content |
| [Internal FAQ Draft Agent](business-subagents/Internal-FAQ-Draft-Agent.md) | Reusable sourced Q&A with pending answers | Email Draft writes messages; Business Report Draft writes reports |
| [Presentation Storyline Agent](business-subagents/Presentation-Storyline-Agent.md) | Slide-by-slide text storyboard and speaker notes | Business Report Draft provides report content |
| [Visual Design Brief Agent](business-subagents/Visual-Design-Brief-Agent.md) | Textual visual direction and proposed layout/theme | Compliance Review checks supplied brand rules; no separate brand-review Agent is added |
| [Spreadsheet Formula Advisor Agent](business-subagents/Spreadsheet-Formula-Advisor-Agent.md) | Formula text, reference map, and logic checks | Data Insight interprets metrics; Data Quality Review audits datasets |
| [Tabular Reshaping Agent](business-subagents/Tabular-Reshaping-Agent.md) | Explicitly derived table structure and reconciliation checks | Data Quality Review inspects issues without transforming records |
| [Data Visualization Agent](business-subagents/Data-Visualization-Agent.md) | Chart specification and optional actually rendered chart | Data Insight interprets findings; Visual Design Brief supplies general visual direction |

## Copilot Studio Configuration Scope

Microsoft documents code interpreter as Python execution for data/file processing and visualization in [code interpreter for prompts](https://learn.microsoft.com/en-us/microsoft-copilot-studio/code-interpreter-for-prompts). Its [FAQ](https://learn.microsoft.com/en-us/microsoft-copilot-studio/faq-code-interpreter) describes sandbox/network limitations and channel-dependent image delivery. These references were reviewed on 2026-10-15; verify the actual tenant, authoring surface, file-input path, and enabled capabilities when configuring.

- Five text Agents need readable supplied text; optional approved references can support their tasks. No external connector is required by their baseline definitions.
- Spreadsheet Formula Advisor can draft text without code. Python checks equivalent arithmetic only; it is not evidence that Excel parsed or recalculated a formula.
- Tabular Reshaping needs accessible source tables. Enable code interpreter for nontrivial transformations; otherwise return plan-only output. Keep original files unchanged.
- Data Visualization can return a specification without code. Render only with an available runtime and return a chart artifact only when the tool actually exposes one; include a text/table fallback.
- Semantic knowledge snippets are not automatically complete tables or runtime-accessible workbook bytes. Confirm what the execution context actually receives.
- Do not hardcode that one prompt accepts multiple uploaded files. Use supported tables or a single workbook with the required sheets when applicable, then check actual context availability.
- Do not assume browser JavaScript, Node.js, arbitrary package installation, network access, Office applications, or a full Excel calculation engine.
- Native Word/PDF/PowerPoint file production is deliberately outside this batch. Existing text Agents can supply content; that does not establish a file-generation workflow.

## Suggested Workflows

- Research/report quality: Research Scout Agent -> Business Report Draft Agent -> Evidence Reasoning Review Agent -> Document Reader Review Agent.
- Presentation preparation: Data Quality Review Agent -> Data Insight Agent -> Presentation Storyline Agent, with Data Visualization Agent for a requested chart and Visual Design Brief Agent for optional styling.
- Table preparation: Tabular Reshaping Agent -> Data Quality Review Agent -> Data Insight Agent -> Data Visualization Agent.
- Internal communication: supplied approved announcement -> Internal FAQ Draft Agent -> Compliance Review Agent when explicit review criteria are available -> optional Email Draft Agent for a delivery draft.

These are proposed compositions. Agent Finder matches actual needs, Workflow Builder defines dependencies, and Agent Executor runs the confirmed scope. Do not invoke every review or styling step for a simple request.

## Manual Acceptance Checks

These checks are for later target-environment validation, not claims of executed Copilot Studio tests.

| Agent | Normal check | Boundary check |
| --- | --- | --- |
| Evidence Reasoning Review Agent | Supply a short AI-generated business conclusion and its evidence. Check that the review points to specific premises and does not claim an independent fact check. | Supply no sources: report evidence gaps without inventing citations or declaring every unsupported claim false. |
| Document Reader Review Agent | Supply a draft full of unexplained internal abbreviations and identify a new-joiner audience. Check location-specific clarity findings. | Ask whether real readers passed the document: state that the perspective is simulated and no user test was conducted. |
| Internal FAQ Draft Agent | Supply an internal project announcement and request a newcomer FAQ. Check every answer against the announcement. | Ask about an unstated reimbursement exception: leave it pending instead of inventing company policy. |
| Presentation Storyline Agent | Supply a short research summary and ask for a five-slide management presentation. Check evidence placement and separation of notes. | Ask for a downloadable PPTX: return the text scope and do not invent a file or download link. |
| Visual Design Brief Agent | Ask for an AI-learning event poster concept with supplied copy. Check concrete layout guidance and clearly proposed colors. | Request company-brand compliance without a brand guide: label the output as a proposal, not an official branded design. |
| Spreadsheet Formula Advisor Agent | Supply named columns and request a conditional total formula. Check exact references, blank handling, and the validation label. | Provide no sheet coordinates: use explicit placeholders or clarify; do not claim the formula ran in Excel. |
| Tabular Reshaping Agent | Supply a small wide table and request a long table. Check row grain, identifiers, transformation log, and conserved totals. | Supply duplicate join keys without a policy: clarify cardinality rather than silently multiplying or deleting rows. |
| Data Visualization Agent | Supply monthly totals and request a line chart. Check actual values, units, ordering, and truthful rendering status. | Disable the interpreter or image delivery: return a specification/table without inventing a chart file. |

Always confirm the final Hub response preserves whether output was drafted, manually checked, Python-computed, or actually rendered. Never report plan-only output as a completed transformation, an unexecuted formula as a verified Excel result, or a text storyboard as a generated file.
