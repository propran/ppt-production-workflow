---
name: ppt-production-workflow
description: Orchestrate academic-pptx, baoyu-slide-deck, and presentations:Presentations to create and iteratively revise professional, editable PowerPoint decks from documents, screenshots, outlines, data, or an existing user-edited PPTX. Use this skill whenever the user asks to make, optimize, restructure, continue editing, add slides to, prepare speaker notes for, or adapt a PPT/PPTX for a timed briefing—especially when the latest user-modified deck must remain the source of truth and factual accuracy, visual consistency, editability, and final rendering checks matter.
compatibility: Requires local file access plus presentations:Presentations for PPTX production. For academic or technical decks, also use academic-pptx. Use baoyu-slide-deck for visual narrative and design after the content structure is stable.
---

# PPT Production Workflow

Use this workflow to turn source material into a clear, editable presentation and to revise existing decks without losing the user's changes.

## Core outcome

By the end, the intended audience should understand the central message, see the evidence or logic that supports it, and know the requested decision, action, or discussion point.

Treat content accuracy, narrative clarity, visual hierarchy, editability, and version safety as equally important.

## Start by selecting the working mode

Choose one mode before editing:

1. **Create mode** — build a new deck from documents, notes, screenshots, data, or a brief.
2. **Revision mode** — improve an existing PPTX while preserving its structure and user edits.
3. **Continuation mode** — the user has manually edited a previously generated deck; use the newest user-modified PPTX as the only source deck for the next revision.

If a local PPTX already exists and the user refers to “最新版”, “我改过的版本”, “同名PPT”, “继续修改”, or similar language, default to continuation mode.

## Mandatory skill orchestration

This skill is the workflow coordinator. It does not replace the specialized PPT skills used in this workflow. For each PPT task, explicitly identify and invoke the applicable skills below rather than silently reproducing their behavior.

### Required order

Use the skills as a staged pipeline, not as competing alternatives:

1. **`ppt-production-workflow` — orchestration and version safety**
   - Select create, revision, or continuation mode.
   - Lock the latest source files and user-modified PPTX.
   - Define the audience, deliverable, QA contract, and any duration explicitly provided by the user.
   - Coordinate the specialized skills and preserve the user's changes.

2. **`academic-pptx` — academic content and argument structure**
   - Invoke this for research proposals, conference talks, thesis defenses, grant briefings, seminar presentations, technical reports, clinical projects, policy research, or any deck evaluated on reasoning and evidence.
   - Read its `SKILL.md` completely before content planning.
   - Read `content_guidelines.md` and the relevant portions of `slide_patterns.md` when the skill routes to them.
   - Use it to create the ghost deck, action-title sequence, evidence hierarchy, core objective, slide jobs, and academic density rules.
   - Do not use it as the PPTX file generator.

3. **`baoyu-slide-deck` — visual narrative and design refinement**
   - Invoke it after the content structure is stable.
   - Read its `SKILL.md` completely and follow the relevant analysis, outline, design, and layout references.
   - Use it to improve page rhythm, scientific visual language, layout options, hierarchy, and visual storytelling.
   - Do not allow it to change factual claims or invent evidence.
   - When editing an existing user-modified PPTX, the existing deck remains the visual source of truth; use baoyu-slide-deck for bounded refinement, not wholesale restyling.

4. **`presentations:Presentations` — editable PPTX implementation and validation**
   - Invoke it for all local PPTX creation or editing.
   - Read its `SKILL.md` and every required reference before implementation.
   - Use its imported-deck/template-following route for an existing PPTX.
   - Use it to create or edit editable objects, speaker notes, source blocks, slide renders, inspections, overflow tests, and template-fidelity checks.
   - Treat its final exported PPTX and latest render as the technical source of truth for delivery.

### Required skill-use disclosure

At the beginning of the task, tell the user which PPT skills will be used and why. Use a concise statement such as:

> 本次工作流：ppt-production-workflow 负责版本与流程控制，academic-pptx 负责学术结构，baoyu-slide-deck 负责视觉叙事，presentations:Presentations 负责可编辑PPT制作与最终校验。

At delivery, briefly report which skills were actually used and what each contributed.

Do not claim that a skill was invoked if it was unavailable or not read. If a required skill is unavailable:

- state the missing skill before proceeding;
- use the closest available fallback only when it remains within the user's scope;
- record the fallback in the final handoff;
- never omit `presentations:Presentations` when an editable local PPTX must be created or edited.

### Non-academic decks

For sales, internal operations, public communication, or other non-academic decks, `academic-pptx` may be skipped when its argument standards would not fit the communication job. State the reason briefly. Continue to use `ppt-production-workflow`, `baoyu-slide-deck`, and `presentations:Presentations` as applicable.

### General routing rules

- For an existing PPTX, import and edit the actual file; do not reconstruct it from an older script or visual approximation.
- Keep intermediate plans, renders, layouts, and audit files outside the final output directory.
- Do not treat a single visual-generation skill as the sole solution; content structure, design refinement, editable implementation, and QA are separate stages.

## Phase 1: Lock the source of truth

### Identify current inputs

Inventory all relevant materials:

- latest PPTX or template;
- source documents and spreadsheets;
- screenshots, meeting notices, emails, or instructions;
- data files and charts;
- time limit, audience, meeting purpose, and required topics;
- the user's latest corrections and preferences.

When several similarly named PPTX files exist:

1. compare filenames, modification times, and file sizes;
2. identify the latest user-modified file;
3. state which file will be used as the source deck;
4. preserve that source and export a newly named copy unless the user explicitly requests in-place editing.

Do not assume that an older generation script represents the latest deck after the user has edited the PPTX manually.

### Apply the evidence hierarchy

Use this order of authority:

1. the user's latest explicit instruction;
2. the latest user-modified PPTX for visible content and formatting;
3. current source documents, data, and official notices;
4. earlier drafts and working notes;
5. general domain knowledge.

If materials conflict, surface the conflict instead of silently choosing a convenient version.

### Protect factual accuracy

Never invent:

- data, sample sizes, results, statistics, dates, fields, policies, or budgets;
- access permissions or platform capabilities;
- confirmed deliverables when they are only proposed;
- payment standards or reimbursement amounts that are not present in the sources.

Label uncertain items accurately, for example:

- “申请范围” rather than “已获得数据”;
- “建议时间窗” rather than “平台已确认覆盖”；
- “待中心确认” rather than an assumed answer;
- “现有材料未提供预算金额” rather than an invented estimate.

## Phase 2: Define the communication job

Write one internal sentence before planning slides:

> By the end, [audience] should [understand, believe, approve, choose, or discuss] because [central takeaway].

Determine:

- who will listen;
- what they already know;
- what must be clear after the presentation;
- the decision or discussion needed;
- the strongest central takeaway;
- the time available for speaking and discussion.

Do not expose this planning sentence on the slides unless it is appropriate audience-facing copy.

## Phase 3: Extract and organize the content

Create a compact source map containing:

- project or presentation purpose;
- background and significance;
- core objective;
- essential questions or claims;
- scope, population, time range, and definitions;
- methods, workflow, or implementation path;
- data and field requirements;
- expected outputs;
- decisions, dependencies, risks, and open questions;
- source for every non-trivial claim.

Separate three kinds of information:

1. **Confirmed facts** — directly supported by current materials.
2. **Proposed design** — what the project or plan intends to do.
3. **Items to confirm** — missing fields, permissions, budget, dates, owners, or platform conditions.

This separation prevents proposals from being presented as completed facts.

## Phase 4: Build the narrative

Choose a cumulative story, not a topic inventory. Common arcs include:

- context → problem → objective → approach → evidence/data → output → decision;
- question → analysis → answer → implication;
- current state → gap → proposed change → implementation → next step;
- project significance → core goal → research questions → data → methods → deliverables → collaboration needs.

Give every slide one narrative job and one primary claim. Use takeaway-style titles that state the point rather than merely naming the topic.

### Add a core-objective slide when useful

If the audience may not understand the project after the title slide, add an early “核心目标” or “What this project does” slide.

Write the objective as one audience-facing paragraph that answers:

- what data or foundation is used;
- who or what is studied;
- what is analyzed or changed;
- what problem is ultimately solved;
- what practical output or decision it supports.

Use this pattern as guidance, not as fixed wording:

> 本项目拟依托[数据或基础]，面向[对象或场景]，通过[关键分析或实施路径]，系统解决[核心问题]，并形成可用于[应用、决策或管理目的]的[成果或工具]。

Keep it to one clear sentence or a short paragraph. Do not turn the slide into an abstract.

### Apply timing constraints only when the user provides them

Do not assume a 10-minute limit, a fixed slide count, or any default relationship between speaking time and number of slides.

When the user explicitly provides a duration or page-count target:

- adapt the narrative and notes to that stated constraint;
- reserve reasonable time for opening, transitions, and closing;
- move lower-priority detail to backup slides when helpful;
- estimate the total from speaker-note timings before delivery.

When no duration or slide-count target is provided, determine scope from the communication job and source complexity rather than imposing an arbitrary limit.

## Phase 5: Choose the visual route

### Existing or user-modified deck

- Treat the actual PPTX as the visual source and template.
- Inspect every slide and its layout before editing.
- Duplicate the most suitable source slide for new content.
- Edit inherited elements in place.
- Preserve fonts, colors, spacing, masters, layouts, notes, and page order unless change is requested.
- Make the smallest sufficient edit.
- Do not add a parallel design system over the user's slide.

### New deck

- Define a small visual system: palette, typography, margins, title hierarchy, body style, and source/footer treatment.
- Match the visual style to the audience and subject.
- Use diagrams, tables, charts, or timelines only when they materially improve understanding.
- Avoid decorative visuals that do not advance the message.
- Keep all audience-facing objects editable whenever practical.

### General layout rules

- Keep one main message per slide.
- Shorten content before shrinking type.
- Never allow a one-line title to wrap unexpectedly.
- Use consistent left and right margins.
- Avoid dense card grids and dashboard-like decoration unless the presentation genuinely requires them.
- Make important conclusions visible at presentation distance.

## Phase 6: Build the editable deck

- Use the available PPTX creation/editing tool rather than a screenshot-only workflow.
- Preserve the existing deck's hierarchy when importing a PPTX.
- Keep text, shapes, tables, and charts editable.
- Export a new clearly named PPTX for non-in-place revisions.
- Keep the user's original file unchanged.
- Store scratch files and renders separately from user-facing outputs.

When adding a slide to an existing deck, record:

- which source slide was duplicated;
- which objects were rewritten, repositioned, replaced, cleared, or deleted;
- why the change was necessary;
- which other slides must remain unchanged.

## Phase 7: Write speaker notes

For timed presentations, add natural spoken notes to the main slides:

- write concise, conversational language that can be read in Presenter View;
- explain the slide's meaning instead of repeating every visible word;
- include a suggested duration when useful;
- use short paragraphs and natural transitions;
- keep appendices to brief answers for likely questions;
- preserve or add a `[Sources]` block for non-trivial claims and external assets.

Do not put production instructions such as “skip this slide” or “the user asked for” in visible slide content.

## Phase 8: Run quality assurance

Before delivery:

1. render every final slide;
2. inspect every slide at full size;
3. check for clipping, overlap, unexpected wrapping, broken connectors, missing fonts, and unreadable contrast;
4. run the available overflow test;
5. confirm slide count, notes count, and output editability;
6. verify all uncertain facts are labeled correctly;
7. verify the narrative fits the duration only when the user requested one;
8. for template-following edits, run the template-fidelity check;
9. compare all preserved slides against the user's source deck and confirm that only requested slides changed;
10. reopen or inspect the exported PPTX rather than assuming the build succeeded.

If a visual or wording defect is found, fix it and rerun the relevant checks.

## Phase 9: Deliver and continue iteratively

In the final response:

- lead with the completed outcome;
- cite or link the final PPTX once;
- summarize the representative changes;
- identify any unresolved decision such as missing budget, fields, dates, or permissions;
- confirm whether the user's source file was preserved;
- mention the most relevant QA result without listing scratch artifacts.

For the next revision:

1. locate the user's newest modified PPTX;
2. confirm it is newer or materially different from the previous output;
3. import that file as the new source of truth;
4. apply only the requested incremental edits;
5. save another clearly named version.

## Completion checklist

Do not mark the task complete until these are true:

- the correct source version was used;
- the audience and communication goal are clear;
- the core objective can be understood quickly;
- every main slide advances the story;
- factual claims are traceable to sources;
- requested uncertainty is not disguised as fact;
- the deck remains editable;
- speaker notes match the speaking duration when requested;
- every slide has been rendered and checked;
- the user's existing edits are preserved;
- the final PPTX is saved in the requested output location.

## Example trigger requests

- “根据这几个Word和会议截图做一份项目汇报PPT。”
- “我已经修改过你做的PPT，请在我的最新版上继续优化。”
- “给现有PPT增加一页核心目标，但不要改变其他页面。”
- “把这个学术报告压缩成8页，并给每页写演讲者备注。”
- “帮我检查PPT有没有溢出、断行和逻辑重复，并输出可编辑终稿。”
