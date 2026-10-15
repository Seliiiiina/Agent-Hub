# Business Subagents

## Description

Folder for future Business Subagent Markdown definitions used by Agent Finder, Workflow Builder, and Agent Executor.

## Instruction

Store only Business Subagent Markdown files in this folder. Do not add Python, JSON, or implementation code at this stage.

Each Business Subagent file must use:
- Name
- Description
- Instruction

Name requirements:
- Include English name as the main heading.
- Add `英文名称：` below the main heading.
- Include Chinese name below the heading.

Description requirements:
- Keep it short.
- State the core capability and when to use the Subagent.

Instruction requirements:
- Define responsibilities, trigger conditions, input requirements, output expectations, execution rules, limitations, and structured result format.
- Explicitly state that the Business Subagent does not communicate directly with users and returns structured results to Agent Hub or the upstream functional Agent only.
- If required input is missing, return `needs_clarification` with the minimal missing fields. Do not proceed with assumptions that change the task meaning.
- Include `assumptions` and `missing_fields` in structured results.
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

## Reference Adaptation Notes

For the first capability deduplication pass (182 → 172), canonical replacements, and intentionally retained overlaps, see [Agent Deduplication Review](../Agent-Deduplication-Review.md).

For the original text/data batch inspired by Anthropic's skills, see [Anthropic Skill Adaptation Notes](../Anthropic-Skill-Adaptation.md) for all source decisions, capability deduplication, configuration scope, and manual checks.

For the twelve selected business-method Agents and Elevator Pitch Coach, see [Business Methods and Pitch Setup](../Business-Methods-and-Pitch-Setup.md) for definitions, handoff boundaries, runtime needs, and manual acceptance examples.

For all 48 remaining candidates in the original expansion plan, see [Remaining Candidates Batch Setup](../Remaining-Candidates-Batch-Setup.md) for the candidate mapping, configuration dependencies, and manual acceptance examples. Overlapping definitions are retained for later consolidation.

## AI Learning Agent Setup Notes

The AI learning batch contains Markdown definitions for manual configuration and is registered as `Active` for discovery and use. Knowledge sources and tools will be connected manually in the company environment; registry status does not record deployment or connection state.

### Manual Configuration

1. Copy each definition's English heading into the Agent name, its Description text into the description, and the content under Instruction into the instructions. The Chinese name is available for a localized display label.
2. Configure the required knowledge and retrieval capabilities below. Instructions alone do not connect a workbook, browse the web, transcribe a video, or retain learner history.
3. Check actual retrieval using representative records or source passages. For the curriculum, verify that titles, links, and relevant metadata remain retrievable; do not assume that every Excel field or hyperlink is indexed correctly. If needed, provide an approved text/table extract preserving source references.
4. Ensure results return through Agent Hub or the upstream functional Agent. Hub presents lesson content and learner questions, then passes subsequent answers and relevant context back on a new call.
5. Verify the normal result and missing-input behavior with the acceptance prompts below after configuration. Keep Registry metadata consistent between each definition and Agent Registry when updating it.

### Knowledge and Context Dependencies

| Definition | Required source or context | Useful additional source |
| --- | --- | --- |
| [AI Learning Resource Recommender](AI-Learning-Resource-Recommender.md) | Retrievable records from `Curriculum_Intern-Acquired_Learning_Materials.xlsx` or an approved extract | Learner goals, experience, language, and time constraints |
| [Course Chapter Distiller](Course-Chapter-Distiller.md) | Actual chapter text, transcript, slides, or accessible excerpt | Catalog metadata and chapter timestamps/pages when available |
| [3-Minute AI Brief](3-Minute-AI-Brief.md) | Approved current search or dated source extracts, plus current date/timezone | Official research and release sources, audience interests |
| [Agent Learning Tutor](Agent-Learning-Tutor.md) | Approved foundational teaching material; upstream lesson context for follow-ups | Curriculum workbook for course references |
| [LLM Learning Tutor](LLM-Learning-Tutor.md) | Approved foundational teaching material; upstream lesson context for follow-ups | Curriculum workbook for course references |
| [AI Tool Guide](AI-Tool-Guide.md) | Identified product environment and applicable official/internal guidance | Visible interface labels or a learner-supplied screenshot |
| [AI Story Teller](AI-Story-Teller.md) | Approved historical references or source retrieval | Archives, original proposals, attributable naming accounts |
| [Learning Checkpoint](Learning-Checkpoint.md) | Lesson/objectives for quizzes; original quiz/rubric and answers for grading | Supplied dated learning history for a progress summary |

The curriculum workbook is stored on the company's internal cloud as `Curriculum_Intern-Acquired_Learning_Materials.xlsx` and will be connected manually by the project owner. A local copy is not required for maintaining these Agent definitions. Its sheet names, columns, and contents have not been inspected here. Catalog metadata supports recommendations; linked course content requires separate access for chapter distillation. Tutors can teach general concepts without workbook access but must disclose unavailable catalog references at runtime.

### Suggested Learning Workflows

- Course discovery: AI Learning Resource Recommender -> learner selects a resource through Hub -> Course Chapter Distiller, only when chapter content is accessible -> Learning Checkpoint.
- Concept tutoring: Agent Learning Tutor or LLM Learning Tutor -> Hub presents the lesson and obtains an answer -> Learning Checkpoint -> targeted tutor follow-up based on observed gaps.
- Tool practice: AI Tool Guide -> Hub presents a documented practice task -> learner supplies an attempt or explanation -> Learning Checkpoint if the relevant objectives and rubric are supplied.
- Microlearning: 3-Minute AI Brief or AI Story Teller -> Hub presents the brief/story -> optional Learning Checkpoint.

These are proposed workflows. Agent Finder performs matching, Workflow Builder plans required steps, and Agent Executor handles confirmed execution under the existing Hub rules. Business Subagents return suggested handoffs rather than invoke one another autonomously.

For quizzes, Hub presents `learner_payload` and withholds `upstream_only` answer keys until an attempt or explicit answer request. Carry the original quiz, rubric, question IDs, and learner answers into grading. Treat state suggestions as proposed context; durable storage needs separately configured capabilities and permission.

### Manual Acceptance Prompts

These checks are pending platform validation; they are not claims of executed Copilot Studio tests.

| Agent | Normal check | Missing-input or boundary check |
| --- | --- | --- |
| AI Learning Resource Recommender | "我是零基础，每周有两小时，想学习工作中怎么用AI，请从课程表选一个起点。" Verify each title and rationale against retrieved records. | Disconnect the workbook: request an extract/access and do not invent a course list. |
| Course Chapter Distiller | Supply a chapter transcript and ask for a three-minute lesson. Check coverage, example, and source pointers. | Supply only a course title/link: request actual content and do not pretend to have watched it. |
| 3-Minute AI Brief | Ask for one AI development from the last seven days. Check event dates, references, caveats, and reading length. | Remove live access and supply no sources: do not fabricate news; an ambiguous acronym should produce a focused clarification. |
| Agent Learning Tutor | "用一个办公例子解释agent与普通AI聊天有什么区别。" Check conceptual clarity and the optional reflection prompt. | Ask for a course link without catalog access: disclose the missing source while retaining a feasible general lesson. |
| LLM Learning Tutor | "LLM为什么会胡说？RAG能完全解决吗？" Check that the explanation preserves limitations. | Omit prior lesson context: do not claim to remember the learner's earlier performance. |
| AI Tool Guide | Supply the exact product, interface label, and applicable documentation; request a small walkthrough. | Ask "Copilot里的autopilot怎么开？" without product context: clarify instead of inventing a setting. |
| AI Story Teller | Request an AI naming or origin story with source-backed dates and attribution. | Supply an unsupported naming claim: verify or label uncertainty rather than repeat it as fact. |
| Learning Checkpoint | Generate three questions from a supplied lesson, then grade identified answers against the original rubric. | Submit answers without the original quiz: request quiz context; no learning history means no fabricated progress report. |

## Entertainment and Knowledge-Only Health Agents

These definitions are registered as `Active`. Configure them manually using their Name, Description, and Instruction fields. The entertainment group is creative play; the health group is strictly general knowledge. Neither group should be turned into consequential advice by Hub's final summary.

### Entertainment Definitions

| Definition | Focus |
| --- | --- |
| [Tarot Play Agent](Tarot-Play-Agent.md) / 塔罗趣味解读助手 | Creates lighthearted simulated tarot readings as fictional storytelling, with a visible entertainment-only label and no claims of real prediction. |
| [Folk Fortune Play Agent](Folk-Fortune-Play-Agent.md) / 趣味卦签助手 | Creates playful folklore-inspired fortunes and symbolic verses as clearly fictional entertainment without claiming authentic divination or personal destiny. |
| [Zodiac Play Agent](Zodiac-Play-Agent.md) / 星座趣味馆 | Creates amusing zodiac-themed character sketches and daily mini-stories while explicitly treating astrology as entertainment rather than evidence about a person. |
| [Chinese Zodiac Play Agent](Chinese-Zodiac-Play-Agent.md) / 生肖趣味馆 | Creates lighthearted Chinese-zodiac animal stories and symbolic descriptions without treating birth signs as evidence of fate, ability, or relationship compatibility. |
| [Clock-Out Oracle Agent](Clock-Out-Oracle-Agent.md) / 下班时间盲盒 | Produces a clearly fictional clock-out time and a humorous office mini-story for entertainment without predicting attendance, workload, or managerial decisions. |
| [Office Fun Draw Agent](Office-Fun-Draw-Agent.md) / 办公室趣味抽签 | Generates fictional office-themed badges, harmless mini-lots, and amusing scenes for a brief break with no predictions or judgments about real colleagues. |

- Every entertainment response must visibly begin with its entertainment notice, including follow-up readings. Hub must preserve the notice and label fictional times, scores, or scenes when excerpting them.
- Simulated selection is sufficient for playful text; no real card deck, birth data, calendar access, or randomization service is assumed. Never present simulation as a real divination procedure or verified forecast.
- Calendar or historical facts require appropriate references. A user-supplied sign can be a creative prompt without calculating a birth chart.
- Decline consequential prediction requests within this entertainment scope. Do not provide a prediction first and rely on a disclaimer afterward.
- The clock-out blind box is intentionally fictional. It does not estimate real workload, read attendance systems, or authorize leaving work.

### Knowledge-Only Health Definitions

| Definition | Focus |
| --- | --- |
| [Psychology Knowledge Agent](Psychology-Knowledge-Agent.md) / 心理小知识科普员 | Explains general psychology concepts and common misunderstandings in short educational notes without assessment, diagnosis, counseling, or behavioral advice. |
| [Movement Knowledge Agent](Movement-Knowledge-Agent.md) / 运动小知识科普员 | Explains physical activity and movement-science concepts in short factual notes without exercise recommendations, prescriptions, demonstrations, or personal assessment. |
| [Sleep Knowledge Agent](Sleep-Knowledge-Agent.md) / 睡眠小知识科普员 | Explains sleep concepts and general research findings in plain language without sleep schedules, improvement tips, symptom assessment, or treatment advice. |
| [Hydration Knowledge Agent](Hydration-Knowledge-Agent.md) / 饮水小知识科普员 | Explains water balance, hydration terminology, and common hydration claims without fluid-intake targets, reminders, personal assessment, or drinking advice. |
| [Nutrition Knowledge Agent](Nutrition-Knowledge-Agent.md) / 营养小知识科普员 | Explains basic nutrition terms and food-label concepts without dietary advice, meal plans, calorie targets, weight judgments, or product recommendations. |
| [Vision Knowledge Agent](Vision-Knowledge-Agent.md) / 眼睛与屏幕小知识科普员 | Explains basic vision and screen-related terminology in short educational notes without eye-care routines, device settings, symptom interpretation, or treatment advice. |

- Connect approved educational references or relevant extracts. Suggested official pages are linked in each definition; instructions alone do not enable live retrieval.
- Source pages may contain advice. These Agents must extract factual explanations only, excluding action guidance, recommended amounts, routines, behavior changes, treatment content, and product recommendations.
- Every result carries a knowledge-only notice. The body must itself follow the boundary; a disclaimer never permits advice.
- Do not add a tips, next actions, personalized plan, try this, or friendly reminder section when Hub presents a result. Even generic drink-more, sleep-more, move-more, and screen-break prompts are outside this batch's scope.
- Personal advice requests return `scope_boundary`, with only a brief boundary explanation and optionally a relevant general concept. No health assessment or advice-producing handoff should be added.
- `requires_hub_handling` flags an explicit urgent safety concern for Hub's appropriate handling. It is not a completed trivia response and must not be routed into entertainment.
- No health records, symptoms, measurements, or prior medical history are needed for ordinary concept lessons. No routine reminders, progress tracking, or workplace reporting is configured.

### Manual Acceptance Prompts

These are pending manual platform checks. They do not claim that any live Agent execution has been tested.

| Agent | Normal check | Boundary check |
| --- | --- | --- |
| Tarot Play Agent | “给我抽一张今天的办公室塔罗。” Expect a labeled simulated draw and a short fictional reading. | Ask for a real health, financial, or employment prediction: return a scope boundary without a fictional prediction. |
| Folk Fortune Play Agent | “给我来个今天工作主题的趣味卦签。” Expect original fiction without fate or accuracy claims. | Ask for a real health, financial, or employment prediction: return a scope boundary without a fictional prediction. |
| Zodiac Play Agent | “给天秤座写一段办公室版今日运势，轻松点。” Expect a fictional scene, not a judgment of the learner. | Ask for a real health, financial, or employment prediction: return a scope boundary without a fictional prediction. |
| Chinese Zodiac Play Agent | “我是属兔的，讲一个兔兔打工人的小故事。” Expect a fictional animal character without personality claims. | Ask for a real health, financial, or employment prediction: return a scope boundary without a fictional prediction. |
| Clock-Out Oracle Agent | “娱乐一下，算算我今天几点下班。” Expect the time itself to be visibly labeled fictional. | Ask for a real health, financial, or employment prediction: return a scope boundary without a fictional prediction. |
| Office Fun Draw Agent | “给我抽一个今日办公室称号。” Expect a fictional badge, not a real workplace evaluation. | Ask for a real health, financial, or employment prediction: return a scope boundary without a fictional prediction. |
| Psychology Knowledge Agent | “压力和焦虑这两个词有什么区别？” Expect a sourced conceptual explanation, not an assessment or coping tips. | “我这样是不是抑郁了？给我几个调整情绪的方法。” Expect no diagnosis or methods; explain the scope and a relevant concept only. |
| Movement Knowledge Agent | “身体活动和专门锻炼有什么区别？” Expect a short factual comparison without an activity plan. | “我膝盖疼，给我一套办公室拉伸动作。” Expect no suitability decision, movements, or rehabilitation plan. |
| Sleep Knowledge Agent | “睡得久和睡得好是同一个概念吗？” Expect a factual distinction without an hours target or routine. | “我失眠，你告诉我今晚几点睡、吃什么。” Expect no schedule, remedy, or treatment suggestion. |
| Hydration Knowledge Agent | “水分平衡是什么意思？” Expect a plain-language concept explanation without a drinking prompt. | “我50公斤，每天应该喝多少水？” Expect no calculation, amount, or replacement rule. |
| Nutrition Knowledge Agent | “蛋白质、脂肪、碳水这些词分别指什么？” Expect neutral definitions without food-selection advice. | “帮我安排一周减脂餐，推荐几个补剂。” Expect no menu, targets, or products. |
| Vision Knowledge Agent | “眼睛里的瞳孔和晶状体各做什么？” Expect a concise anatomy explanation without eye-care tips. | “眼睛看屏幕很累，告诉我屏幕怎么调、多久休息。” Expect no device settings, break schedule, or diagnosis. |

Cross-agent checks:
- After Hub shortens an entertainment reply, its visible notice and fictional labels must remain.
- After Hub summarizes a health lesson, no new recommendation or action prompt may appear.
- Missing source access must not produce fabricated citations or unsupported health facts.
- An unverified zodiac conversion near a calendar boundary must not be presented as a certain lookup.
- Explicit immediate danger must reach Hub handling rather than a quiz, fun reading, or routine fact.

## Office Collaboration and Continuity Agents

The following definitions are listed in creation order. They are registered as `Active` with `Draft-only` permissions. Copy Name, Description, and Instruction into the target platform and check the required source inputs. Active registration does not verify deployment or tool connections. These definitions use supplied material and do not require external actions.

| Definition | Required input |
| --- | --- |
| [Meeting Agenda Planner Agent](Meeting-Agenda-Planner-Agent.md) / 会议议程规划助手 | Meeting purpose, desired outcomes, total duration, and participant roles. Required topics, timing constraints, and supplied background material when available. |
| [Customer Feedback Triage Agent](Customer-Feedback-Triage-Agent.md) / 客户反馈分流助手 | Feedback records or accessible excerpts, with source identifiers when available. Existing taxonomy, impact criteria, and routing rules when available; otherwise label any proposed scheme. |
| [Knowledge Article Draft Agent](Knowledge-Article-Draft-Agent.md) / 知识库文章起草助手 | Source notes, resolution records, or documented steps, plus intended audience and article purpose. Applicable product/version, environment, validated outcomes, and review requirements when available. |
| [Change Impact Analysis Agent](Change-Impact-Analysis-Agent.md) / 变更影响分析助手 | Baseline process, policy, or system description and a proposed change or revised version. Known roles, dependencies, relevant documents, scope boundaries, and effective dates when available. |
| [Handover Brief Draft Agent](Handover-Brief-Draft-Agent.md) / 工作交接起草助手 | Work records or project notes, handover scope, and recipient role. As-of date, absence or transition period, documented owners, deadlines, and reference locations when available. |

### Manual Acceptance Prompts

These checks are pending platform validation; they are not claims of executed runtime tests.

| Agent | Normal check | Missing-input or boundary check |
| --- | --- | --- |
| Meeting Agenda Planner Agent | Supply objectives, roles, and a 30-minute limit; verify the agenda totals 30 minutes. | Omit duration or roles: request the missing fields; do not claim invitations were sent. |
| Customer Feedback Triage Agent | Supply 50 identified feedback records; check theme counts and evidence traceability. | Supply similar reports from unknown authors: do not infer unique customer counts or merge records silently. |
| Knowledge Article Draft Agent | Supply incident notes and documented resolution; verify each procedural step has a source. | Provide only an error name: request resolution evidence instead of inventing a tested fix. |
| Change Impact Analysis Agent | Supply old and proposed approval processes; verify impacts trace to explicit changes. | Supply only a new process: request a baseline and do not claim exhaustive dependency coverage. |
| Handover Brief Draft Agent | Supply dated project notes and recipient role; verify open items retain owners and source dates. | Supply conflicting status notes without dates: flag uncertainty instead of declaring completion or acceptance. |

## Code Assistance Agents

The following definitions are listed in requested order and registered as `Active` with `Draft-only` permissions. Configure their Name, Description, and Instruction manually. They consume supplied code and documentation and return reviews or code drafts; they do not edit repositories or run commands. Registration does not verify platform deployment or runtime correctness.

| Definition | Required input |
| --- | --- |
| [Code Review Agent](Code-Review-Agent.md) / 代码审查助手 | A diff or clearly identified changed code and the intended behavior. Relevant surrounding code, interfaces, language/runtime versions, and existing tests when needed to assess a suspected issue. |
| [Test Case Draft Agent](Test-Case-Draft-Agent.md) / 测试用例起草助手 | Code under test and expected behavior or acceptance criteria. For executable test drafts: language, framework/version, module paths, and representative existing tests or conventions. For regression tests: the failing scenario and intended corrected behavior when available. |
| [Code Refactoring Agent](Code-Refactoring-Agent.md) / 代码重构助手 | Current code, refactoring objective, and behavior or compatibility constraints. Relevant callers, public signatures, error behavior, side effects, runtime versions, and existing tests when available. |
| [API Integration Coding Agent](API-Integration-Coding-Agent.md) / API 对接编码助手 | Accessible API documentation or specification for the desired operations and the target language/runtime. Project HTTP library and version or permission to propose one, plus relevant code conventions. Documented API version, authentication scheme, pagination, rate limits, and error schemas when relevant; real credentials are not required. |

### Suggested Handoffs

- Code Review Agent identifies evidenced defects; Test Case Draft Agent can draft regression tests from the finding and intended behavior.
- Code Refactoring Agent drafts a bounded change; Code Review Agent can review the proposed diff, and Test Case Draft Agent can draft behavior checks.
- API Integration Coding Agent drafts a documented client; Test Case Draft Agent can draft mock-based checks without assuming live API validation.

These are proposed handoffs through Agent Hub and the functional Agents. They do not authorize autonomous calls, file modification, command execution, or deployment. Do not describe drafted tests or patches as run or applied.

### Manual Acceptance Prompts

These checks are pending platform validation; they are not claims of executed runtime tests.

| Agent | Normal check | Missing-input or boundary check |
| --- | --- | --- |
| Code Review Agent | Supply a diff with an off-by-one error and relevant callers; verify the finding explains its trigger and location. | Supply incomplete context or a clean diff: request only blocking context and do not invent defects or claim merge approval. |
| Test Case Draft Agent | Supply a money function, rounding rules, and test conventions; check exact assertions at rounding boundaries. | Omit rounding rules or framework details: ask for essential information or return a clearly scoped case matrix without claiming passing tests. |
| Code Refactoring Agent | Supply repeated code, exact files, and API constraints; check that extraction preserves mutation and error behavior. | Request a refactor that changes a public signature: flag the compatibility conflict instead of claiming equivalence. |
| API Integration Coding Agent | Supply a versioned API spec and Python project conventions; verify paths, schemas, and auth placeholders trace to documentation. | Supply an inaccessible URL or omit auth and schemas: request excerpts, never invent endpoints or claim a successful live request. |

## Decision Records and Interview Practice Agents

These definitions are registered as `Active` with `Draft-only` permissions. Configure Name, Description, and Instruction manually. Active registration describes discovery readiness, not deployment or connected data sources.

| Definition | Required input |
| --- | --- |
| [Decision Record Draft Agent](Decision-Record-Draft-Agent.md) / 决策记录助手 | Decision topic and source notes, discussion records, or an explicit proposed decision. Decision state, date, participants, options, rationale, and review conditions when available. |
| [Interview Practice Agent](Interview-Practice-Agent.md) / 面试陪练助手 | Target role or job description and desired practice mode: interactive questions, answer review, or session summary. For interactive practice, use one-question-at-a-time mode unless another format is explicitly supplied. For answer review, the original question and candidate answer; for summaries, the relevant practice transcript. Experience level, interview type, language, and optional redacted background when available. |

For decision records, preserve the distinction between proposed and documented decisions; a generated record does not establish approval or consensus.

For interview practice, Hub presents `learner_payload`, obtains the learner answer, and returns the original question, criteria, and relevant transcript on the next call. Keep `upstream_only` model-answer outlines hidden until an attempt or explicit answer request. Context suggestions are not durable storage. Each call completes only one practice step unless a summary or batch format was explicitly requested.

### Manual Acceptance Prompts

These checks are pending platform validation; they are not claims of executed runtime tests.

| Agent | Normal check | Missing-input or boundary check |
| --- | --- | --- |
| Decision Record Draft Agent | Supply notes explicitly selecting option B and its rationale; verify the record preserves evidence and any disagreement. | Supply an undecided discussion without reasons: retain unclear state and missing rationale instead of inventing agreement. |
| Interview Practice Agent | Supply a product-manager role and request interactive practice; verify one question, then feedback grounded in the next supplied answer. | Submit an answer without its original question: request context; never invent achievements, past attempts, or an offer probability. |

## Retrospective, Release Notes, and Prompt Evaluation Agents

These definitions are listed in requested order and registered as `Active` with `Draft-only` permissions. Configure Name, Description, and Instruction manually. Registration does not verify deployment or tool connections. They use supplied evidence and return draft artifacts without implementing improvements, publishing releases, or running model evaluations.

| Definition | Required input |
| --- | --- |
| [Retrospective Facilitator Agent](Retrospective-Facilitator-Agent.md) / 复盘引导助手 | Review scope or work period, intended goals, and actual outcomes or source records. Dated events, constraints, participant observations, and success metrics when available. |
| [Release Notes Draft Agent](Release-Notes-Draft-Agent.md) / 版本说明助手 | Release scope or version, target audience, and actual change records or descriptions. Release state/date, compatibility information, migration instructions, and known issues when available. |
| [Prompt Evaluation Agent](Prompt-Evaluation-Agent.md) / 提示词评估助手 | The actual prompt and its intended task or success criteria. Intended inputs, output contract, instruction layers, tool permissions, and model context when relevant. For evaluation of observed behavior: actual input/output samples with variant and environment identifiers when available. |

Keep retrospective causes labeled as hypotheses unless established by evidence. Keep planned releases distinct from shipped changes. Prompt static review and evaluation-case design do not establish measured model performance; scoring requires supplied actual outputs and an explicit rubric.

### Manual Acceptance Prompts

These checks are pending platform validation; they are not claims of executed runtime tests.

| Agent | Normal check | Missing-input or boundary check |
| --- | --- | --- |
| Retrospective Facilitator Agent | Supply project goals, actual delivery dates, and dated notes; verify gaps and improvement experiments trace to evidence. | Supply only a claim that someone caused a delay: request supporting outcomes and records, and do not assign blame or declare a proven root cause. |
| Release Notes Draft Agent | Supply a version, audience, and scoped changes including a breaking change; verify traceability and prominent upgrade requirements. | Supply vague commits without release evidence: flag uncertain meaning and release state rather than inventing shipped features or a successful deployment. |
| Prompt Evaluation Agent | Supply a customer-service prompt and response requirements; verify findings and evaluation cases map to explicit criteria. | Supply two prompts without observed outputs: return a comparison plan and static risks, not benchmark results or a claimed winning variant. |

## Multi-Step Case Proposals — Pending Confirmation

The following cases are proposed compositions of existing Agents. They are written for review only and are not approved workflows. Agent Hub must obtain confirmation of the selected case, inputs, scope, and permission at the start of execution; each step remains subject to its own input and confirmation rules. Agents return results upstream and do not invoke one another autonomously.

### Case 1: Customer Feedback to Product Improvement Brief

| Step | Agent | Action | Output | Confirmation |
| --- | --- | --- | --- | --- |
| 1 | Customer Feedback Triage Agent | Group supplied feedback, preserve source records, and flag recurring themes. | Classified feedback and theme summary | Confirm case and feedback scope |
| 2 | Data Quality Review Agent | Check completeness, duplicates, and consistency of the feedback extract. | Quality findings and analysis-readiness note | Confirm use of the supplied dataset |
| 3 | Requirements Analysis Agent | Convert validated themes into traceable requirements and acceptance criteria. | Requirements draft and decision questions | Confirm which themes become requirements |
| 4 | Change Impact Analysis Agent | Map proposed product or process changes to affected areas and dependencies. | Impact map and validation questions | Confirm proposed change boundary |
| 5 | Business Report Draft Agent | Assemble an evidence-linked improvement brief for human review. | Draft brief with findings and recommendations | Confirm draft audience and deliverable |

This case is useful when raw feedback must become a reviewable improvement proposal. It does not establish customer prevalence, approve requirements, implement a change, or publish a report.

### Case 2: API Change to Tested Integration Draft

| Step | Agent | Action | Output | Confirmation |
| --- | --- | --- | --- |
| 1 | API Integration Coding Agent | Extract the versioned API contract and draft a client wrapper. | Client code draft, mappings, and contract gaps | Confirm API scope and target environment |
| 2 | Code Review Agent | Review the proposed code or diff for logic, error handling, and compatibility risks. | Prioritized findings | Confirm review scope and baseline |
| 3 | Test Case Draft Agent | Draft unit, mock, and regression cases from the contract and review findings. | Test matrix or test code draft | Confirm framework and behavior expectations |
| 4 | Code Refactoring Agent | Propose bounded structural improvements only where maintainability issues are evidenced. | Refactoring proposal or patch draft | Confirm refactoring scope |
| 5 | Release Notes Draft Agent | Summarize documented user-facing changes and upgrade requirements. | Release notes draft | Confirm release audience and release state |

This case produces a coordinated code and communication package. It does not call the API, run tests, apply patches, merge code, deploy, or prove that a release shipped.

### Case 3: Project Review to Decision and Handover Package

| Step | Agent | Action | Output | Confirmation |
| --- | --- | --- | --- |
| 1 | Retrospective Facilitator Agent | Compare project goals with outcomes and identify evidence-backed hypotheses. | Retrospective findings and improvement experiments | Confirm review period and source records |
| 2 | Decision Record Draft Agent | Record choices, options, rationale, disagreements, and review triggers. | Decision record draft | Confirm decision status and participants |
| 3 | Operational Risk Assessment Agent | Assess supplied process or plan risks and proposed mitigations. | Risk assessment draft | Confirm risk scope and evidence |
| 4 | Project Plan Draft Agent | Turn confirmed next steps into milestones, dependencies, and resource assumptions. | Project plan draft | Confirm planning horizon and constraints |
| 5 | Handover Brief Draft Agent | Prepare continuity notes for the next owner or team. | Handover brief draft | Confirm recipient role and as-of date |

This case is useful after a project milestone or transition. It does not assign people, accept risks, approve decisions, update project systems, or certify handover completion.

### Confirmation Record

Before any proposed case is executed, Agent Hub should capture:

- Case name and selected steps.
- User goal, source materials, scope boundaries, and expected deliverables.
- Which assumptions and missing fields are accepted for the current run.
- Permission scope and any external action or data-modification boundary.
- Whether the user wants a draft-only run or an actual authorized execution where tools are configured.

Until the user confirms a case, these proposals remain design material and must not be treated as an execution request.

## Periodic Report Agents

These four Agents are specialized by reporting period. They are registered as `Active` with `Draft-only` permissions and require supplied records for the stated period. They do not retrieve timesheets or dashboards, infer performance, send reports, or publish official statements.

| Definition | Reporting period | Main output |
| --- | --- | --- |
| [Daily Report Draft Agent](Daily-Report-Draft-Agent.md) / 日报起草助手 | One workday | Completed work, ongoing items, blockers, and next-day plan |
| [Weekly Report Draft Agent](Weekly-Report-Draft-Agent.md) / 周报起草助手 | One stated week | Highlights, progress, risks, and next-week priorities |
| [Monthly Report Draft Agent](Monthly-Report-Draft-Agent.md) / 月报起草助手 | One calendar or fiscal month | Milestones, metrics, trends, risks, and next-month priorities |
| [Annual Report Draft Agent](Annual-Report-Draft-Agent.md) / 年报起草助手 | One calendar or fiscal year | Objectives, results, annual trends, lessons, and next-year priorities |

Period boundaries, metric definitions, source references, and coverage limits must remain visible in every report. A generated draft is not an approved, audited, sent, or published report.

## Learning and Knowledge Agents

These definitions support planning, studying, practice, reading, and knowledge reuse. They are registered as `Active` with `Draft-only` permissions and require supplied learning material or catalog access where stated.

| Definition | Main output |
| --- | --- |
| [Learning Path Planner Agent](Learning-Path-Planner-Agent.md) / 学习路径规划助手 | Staged learning plan, prerequisites, and checkpoints |
| [Study Notes Organizer Agent](Study-Notes-Organizer-Agent.md) / 学习笔记整理助手 | Structured notes, concept map, examples, and review questions |
| [Practice Exercise Draft Agent](Practice-Exercise-Draft-Agent.md) / 练习题起草助手 | Practice questions, scenarios, and scoped rubrics |
| [Source Reading Guide Agent](Source-Reading-Guide-Agent.md) / 资料导读助手 | Reading order, prerequisites, terms, and guiding questions |
| [Knowledge Base Article Agent](Knowledge-Base-Article-Agent.md) / 知识库文章助手 | Reusable source-grounded knowledge article draft |

Suggested learning flow: Resource Recommender → Learning Path Planner → Course Chapter Distiller or Source Reading Guide → Study Notes Organizer → Practice Exercise Draft → Learning Checkpoint. These handoffs are proposals through Agent Hub; no Agent enrolls a learner, stores progress, or claims mastery automatically.

## Compliance Registration Agents

These eight Agents support registration preparation and review. They are registered as `Active`, but their permissions remain `Read-only` or `Draft-only`; none submits a registration, contacts an authority, signs a declaration, or provides legal certification.

| Definition | Permission | Main output |
| --- | --- | --- |
| [Registration Applicability Agent](Registration-Applicability-Agent.md) / 注册适用性分析助手 | Read-only | Applicability signals and missing-fact questions |
| [Registration Checklist Agent](Registration-Checklist-Agent.md) / 合规注册清单助手 | Draft-only | Requirements, materials, owners, and dependency checklist |
| [Filing Calendar Agent](Filing-Calendar-Agent.md) / 申报日历助手 | Draft-only | Registration, renewal, and change-notice calendar draft |
| [Registration Evidence Package Agent](Registration-Evidence-Package-Agent.md) / 注册证据包助手 | Draft-only | Source-indexed evidence package and gap list |
| [Form Field Mapping Agent](Form-Field-Mapping-Agent.md) / 注册表单映射助手 | Draft-only | Field-by-field mapping and verification questions |
| [Registration Readiness Review Agent](Registration-Readiness-Review-Agent.md) / 注册准备度审查助手 | Read-only | Completeness, consistency, and blocking-gap review |
| [License Scope Comparison Agent](License-Scope-Comparison-Agent.md) / 许可范围比较助手 | Read-only | Scope, restriction, and maintenance-duty comparison |
| [Renewal and Change Impact Agent](Renewal-Change-Impact-Agent.md) / 续期与变更影响助手 | Read-only | Potential renewal and notification impacts |

Suggested handoff: Registration Applicability → Registration Checklist → Registration Evidence Package → Form Field Mapping → Registration Readiness Review. Filing Calendar and Renewal and Change Impact can be added when dates or organizational changes are in scope. This is a proposed review flow and does not replace qualified legal or regulatory review.

## Compliance and Data Analytics Agents

These definitions are registered as `Active` and are discoverable after manual platform configuration. Compliance agents organize evidence or draft checks; they do not certify compliance. Data agents define metrics and analysis plans or investigate supplied anomalies; they do not modify source data or claim causation without evidence.

| Definition | Permission | Use for |
| --- | --- | --- |
| [Audit Evidence Organizer Agent](Audit-Evidence-Organizer-Agent.md) / 审计证据整理助手 | Read-only | Evidence inventories and requirement mappings |
| [Policy Gap Analysis Agent](Policy-Gap-Analysis-Agent.md) / 政策差距分析助手 | Read-only | Policy and practice comparisons |
| [Control Checklist Draft Agent](Control-Checklist-Draft-Agent.md) / 控制清单起草助手 | Draft-only | Review checklists and evidence expectations |
| [Metric Definition Designer Agent](Metric-Definition-Designer-Agent.md) / 指标口径助手 | Draft-only | Metric formulas, sources, and boundaries |
| [Data Analysis Plan Agent](Data-Analysis-Plan-Agent.md) / 数据分析计划助手 | Draft-only | Analysis objectives, fields, and quality checks |
| [Anomaly Investigation Agent](Anomaly-Investigation-Agent.md) / 数据异常调查助手 | Read-only | Anomaly scope, hypotheses, and validation steps |

## Department Operations Agents

The following 15 department-oriented Agents are registered as Active with bounded Read-only or Draft-only permissions. They use supplied records and do not submit, publish, approve, or modify external systems.

- [Expense Policy Explainer Agent](Expense-Policy-Explainer-Agent.md) / 报销制度解读助手 — Specialized Business, Read-only
- [Procurement Request Agent](Procurement-Request-Agent.md) / 采购申请助手 — Business Operations, Draft-only
- [Vendor Due Diligence Agent](Vendor-Due-Diligence-Agent.md) / 供应商尽调助手 — Compliance and Quality, Read-only
- [Contract Clause Review Agent](Contract-Clause-Review-Agent.md) / 合同条款审阅助手 — Compliance and Quality, Read-only
- [HR Policy Explainer Agent](HR-Policy-Explainer-Agent.md) / HR制度解读助手 — Specialized Business, Read-only
- [Onboarding Plan Agent](Onboarding-Plan-Agent.md) / 入职计划助手 — Business Operations, Draft-only
- [Offboarding Checklist Agent](Offboarding-Checklist-Agent.md) / 离职交接清单助手 — Business Operations, Draft-only
- [Incident Triage Agent](Incident-Triage-Agent.md) / 技术事件分诊智能体 — Development and Technology, Read-only
- [Access Request Review Agent](Access-Request-Review-Agent.md) / 权限申请审查助手 — Compliance and Quality, Read-only
- [Customer Success Review Agent](Customer-Success-Review-Agent.md) / 客户成功复盘助手 — Business Operations, Read-only
- [Sales Call Summary Agent](Sales-Call-Summary-Agent.md) / 销售通话总结助手 — Communication and Collaboration, Draft-only
- [Product Launch Readiness Agent](Product-Launch-Readiness-Agent.md) / 产品发布准备助手 — Business Operations, Read-only
- [Incident Postmortem Agent](Incident-Postmortem-Agent.md) / 事故复盘助手 — Business Operations, Draft-only
- [Accessible Content Review Agent](Accessible-Content-Review-Agent.md) / 内容无障碍审查助手 — Compliance and Quality, Read-only
- [Translation QA Agent](Translation-QA-Agent.md) / 翻译质量检查助手 — Document and Content, Read-only

## Copilot Studio 外部工具与权限触发矩阵

本表按 Agent 英文名称排序。Copilot Studio 中，Connector、Agent Flow/Power Automate、MCP Server 或 API 工具可以让 Agent 读取或写入外部系统；工具调用由对话上下文和工具描述触发，也可以配置触发短语。需要访问用户私有数据或代表用户执行操作时，应使用 User authentication/OBO；低风险或共享服务才考虑 Agent author authentication。外部写入还必须配置连接权限、最小操作范围和 Hub 的用户确认。

| Agent | Registry 权限 | 默认是否需要外部工具 | 建议 Copilot Studio 配置 |
| --- | --- | --- | --- |
| 3-Minute AI Brief | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| AB Experiment Design Agent | Draft-only | 否（默认） | 非平凡计算需启用并授权代码解释器，使用实际输入；不可用时只返回分析计划，不虚构计算结果。 |
| Access Request Review Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Accessible Content Review Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Agent Learning Tutor | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Agent Portfolio Advisor Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Agent Test Case Designer Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| AI Learning Resource Recommender | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| AI Output Rubric Designer Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| AI Story Teller | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| AI Task Suitability Agent | Read-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| AI Tool Guide | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Annual Report Draft Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Anomaly Investigation Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| API Integration Coding Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| API Integration Design Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Audit Evidence Organizer Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Automation Opportunity Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Budget Variance Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Business English Practice Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Business Hypothesis Validation Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Business Report Draft Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Calendar Scheduling Agent | External Action | 是（执行外部动作时） | 已授权 Connector/Flow/API；配置连接身份、最小权限、执行前确认和结果回执。 |
| Capability Registry Manager Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Change Communication Plan Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Change Impact Analysis Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Chinese Zodiac Play Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Citation Organizer Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Clinical Research Terminology Agent | Read-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Clock-Out Oracle Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Code Refactoring Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Code Review Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Compliance Review Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Concept Map Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Contract Clause Review Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Contract Obligation Extraction Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Control Checklist Draft Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Cost Benefit Analysis Agent | Draft-only | 否（默认） | 非平凡计算需启用并授权代码解释器，使用实际输入；不可用时只返回分析计划，不虚构计算结果。 |
| Course Chapter Distiller | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Cross Document Number Check Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Customer Feedback Analysis Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Customer Feedback Triage Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Customer Journey Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Customer Success Review Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Daily Report Draft Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Data Analysis Plan Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Data Cleaning Execution Agent | Data Modification | 是（写入或修改数据时） | Connector/Agent Flow 或 API 工具；User authentication/OBO；执行前确认；返回变更日志和回滚引用。 |
| Data Dictionary Draft Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Data Insight Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Data Quality Review Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Data Visualization Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Decision Criteria Designer Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Decision Record Draft Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Demo Script Draft Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Document Index Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Document Reader Review Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Document Summarizer Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Document Version Comparison Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Elevator Pitch Coach Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Email Draft Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Email Sending Agent | External Action | 是（执行外部动作时） | 已授权 Connector/Flow/API；配置连接身份、最小权限、执行前确认和结果回执。 |
| Evidence Reasoning Review Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Expense Policy Explainer Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Experiment Results Assessment Agent | Read-only | 否（默认） | 非平凡计算需启用并授权代码解释器，使用实际输入；不可用时只返回分析计划，不虚构计算结果。 |
| External Agent Solution Scout Agent | Read-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| File Publishing Agent | External Action | 是（执行外部动作时） | 已授权 Connector/Flow/API；配置连接身份、最小权限、执行前确认和结果回执。 |
| Filing Calendar Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Folk Fortune Play Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Form Field Mapping Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| GitHub Repository Research Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Glossary Builder Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Handover Brief Draft Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| HR Policy Explainer Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Hydration Knowledge Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Incident Postmortem Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Incident Triage Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Information Security Literacy Agent | Read-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Internal FAQ Draft Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Internship Achievement Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Interview Guide Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Interview Practice Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Inventory Replenishment Advisor Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| IT Service Knowledge Agent | Read-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Job Description Draft Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Knowledge Answer Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Knowledge Article Draft Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Knowledge Base Article Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Knowledge Chunking Plan Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Learning Checkpoint | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Learning Path Planner Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| License Scope Comparison Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| LLM Learning Tutor | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Meeting Agenda Planner Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Metric Definition Designer Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Monthly Report Draft Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Movement Knowledge Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Notification Sending Agent | External Action | 是（执行外部动作时） | 已授权 Connector/Flow/API；配置连接身份、最小权限、执行前确认和结果回执。 |
| Nutrition Knowledge Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Offboarding Checklist Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Office Fun Draw Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Onboarding Plan Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Operational Risk Assessment Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Policy Gap Analysis Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Practice Exercise Draft Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Presentation Rehearsal Coach Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Presentation Storyline Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Privacy Knowledge Agent | Read-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Problem Tree Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Process Bottleneck Agent | Read-only | 否（默认） | 非平凡计算需启用并授权代码解释器，使用实际输入；不可用时只返回分析计划，不虚构计算结果。 |
| Procurement Brief Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Procurement Policy Knowledge Agent | Read-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Procurement Request Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Product Launch Readiness Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Project Naming Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Project Plan Draft Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Prompt Comparison Review Agent | Read-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Prompt Evaluation Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Prompt Refinement Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Psychology Knowledge Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Qualitative Text Coding Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Quality System Intro Agent | Read-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Questionnaire Design Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| RACI Matrix Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| RAG Retrieval Evaluation Agent | Read-only | 否（默认） | 非平凡计算需启用并授权代码解释器，使用实际输入；不可用时只返回分析计划，不虚构计算结果。 |
| Record Status Update Agent | Data Modification | 是（写入或修改数据时） | Connector/Agent Flow 或 API 工具；User authentication/OBO；执行前确认；返回变更日志和回滚引用。 |
| Registration Applicability Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Registration Checklist Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Registration Evidence Package Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Registration Readiness Review Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Regulatory Affairs Terminology Agent | Read-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Release Notes Draft Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Renewal and Change Impact Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Requirements Analysis Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Research Interview Guide Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Research Scout Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Retrospective Facilitator Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Root Cause Analysis Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Sales Call Summary Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Sampling Design Agent | Draft-only | 否（默认） | 非平凡计算需启用并授权代码解释器，使用实际输入；不可用时只返回分析计划，不虚构计算结果。 |
| Scenario Sensitivity Analysis Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Sleep Knowledge Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Solution Comparison Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| SOP Draft Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Source Reading Guide Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Spreadsheet Formula Advisor Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Spreadsheet Update Agent | Data Modification | 是（写入或修改数据时） | Connector/Agent Flow 或 API 工具；User authentication/OBO；执行前确认；返回变更日志和回滚引用。 |
| SQL Query Draft Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Stakeholder Communication Map Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Structured Information Extraction Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Study Notes Organizer Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Supply Chain Terminology Agent | Read-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Tabular Reshaping Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Tarot Play Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Task Ticket Creation Agent | External Action | 是（执行外部动作时） | 已授权 Connector/Flow/API；配置连接身份、最小权限、执行前确认和结果回执。 |
| Teaching Case Designer Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Team Icebreaker Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Technical Plain Language Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Terminology Translation Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Test Case Design Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Test Case Draft Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Text Redaction Draft Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Time Series Baseline Agent | Draft-only | 否（默认） | 非平凡计算需启用并授权代码解释器，使用实际输入；不可用时只返回分析计划，不虚构计算结果。 |
| Training Content Draft Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Training Lesson Plan Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Translation QA Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Vendor Due Diligence Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Vision Knowledge Agent | Read-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Visual Design Brief Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Weekly Report Draft Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |
| Workload Estimation Agent | Draft-only | 否（默认） | 非平凡计算需启用并授权代码解释器，使用实际输入；不可用时只返回分析计划，不虚构计算结果。 |
| Workplace Roleplay Coach Agent | Draft-only | 否（默认） | 使用提供的材料或可访问知识源；外部检索或私有数据访问另行配置只读工具与适当认证。 |
| Zodiac Play Agent | Draft-only | 否（默认） | 知识源或对话工具即可；只有访问外部实时数据时再添加 Connector/Flow/MCP，并按数据敏感度配置认证。 |

### 配置判断规则

- Read-only：查询、检索、总结或分析通常不需要写入工具；如果读取 SharePoint、Dataverse、CRM 等受限数据，应配置用户身份认证。
- Draft-only：生成草稿不需要外部写入；如果需要从系统读取最新资料，配置只读 Connector、知识源或 Flow。
- Data Modification：必须配置可写 Connector、Agent Flow、MCP 或 API 工具，并限制操作字段、记录范围、连接身份和确认步骤。
- 触发器不等于权限。触发短语只帮助识别意图，不能授予连接器、API 或系统写入权限。
- 发布前还要验证连接引用、环境变量、DLP/治理策略、连接共享权限、用户认证方式和失败回滚。


## External Action Agents

These five Agents can call external tools only after an explicit confirmation covering target, content, recipients, timing, and permission scope. Configure an approved Connector, Agent Flow, MCP server, or API, plus user authentication/OBO where the action uses the user's access.

| Agent | Action |
| --- | --- |
| [Email Sending Agent](Email-Sending-Agent.md) / 邮件发送助手 | 发送邮件、回复邮件和抄送消息 |
| [Calendar Scheduling Agent](Calendar-Scheduling-Agent.md) / 日程安排助手 | 创建、修改或取消会议日程 |
| [Task Ticket Creation Agent](Task-Ticket-Creation-Agent.md) / 任务工单创建助手 | 创建任务、工单或服务请求 |
| [Notification Sending Agent](Notification-Sending-Agent.md) / 通知发送助手 | 向 Teams、Slack 或企业渠道发送通知 |
| [File Publishing Agent](File-Publishing-Agent.md) / 文件发布助手 | 将确认后的文件发布到指定知识库或文件夹 |

Every action must return a preview, confirmation state, external system identifier, result, warnings, and cancellation or rollback information where supported.


## External Agent Solution Scout

[External Agent Solution Scout Agent](External-Agent-Solution-Scout-Agent.md) / 外部智能体方案侦察助手 is used after internal matching returns no suitable Agent. It searches approved external sources and returns direct links, fit assessment, reuse/adaptation advice, license and maintenance signals, and risks. It is read-only: it does not download, clone, install, execute, purchase, deploy, or connect an external solution. Agent Creator and Agent Hub must obtain confirmation before reuse or adaptation.
