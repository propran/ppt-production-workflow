# PPT Production Workflow Skill

[中文说明](#中文说明) · [English Documentation](#english-documentation)

## 中文说明

### 这是什么

`ppt-production-workflow` 是一个用于专业 PPT 制作与迭代修改的总控 Skill。它不会把“内容梳理、视觉设计、PPTX 制作”混成一步，而是按阶段调用本项目实际使用过的 PPT Skills：

| 阶段 | 调用的 Skill | 主要职责 |
|---|---|---|
| 1. 总控与版本安全 | `ppt-production-workflow` | 判断新建、修改或续改模式，锁定最新源文件，保护用户手工修改 |
| 2. 学术内容结构 | `academic-pptx` | 提炼核心目标、论证链、行动式标题、页面任务和证据层级 |
| 3. 视觉叙事优化 | `baoyu-slide-deck` | 优化页面节奏、信息层级、科学视觉语言和布局方向 |
| 4. 可编辑文件与质检 | `presentations:Presentations` | 创建或编辑可编辑 PPTX，添加备注，并完成渲染、溢出和一致性检查 |

它适合科研课题汇报、项目申报、学术会议、答辩、技术方案和已有 PPT 的持续修改。

### 核心原则

- 最新的用户修改版 PPTX 是续改时唯一的源演示文稿。
- 不编造数据、样本量、结果、日期、字段、政策或预算。
- 区分“已确认事实”“拟开展方案”和“待确认事项”。
- 先稳定内容结构，再优化视觉，最后生成并检查可编辑 PPTX。
- 默认**不设置 10 分钟限制，也不预设固定页数**；只有用户明确给出时间或页数时才做控量。
- 修改已有 PPT 时采用最小充分修改，并保留原文件。

### 依赖

本仓库只包含总控 Skill，不复制第三方 Skill 的源文件。

1. [`academic-pptx`](https://github.com/Gabberflast/academic-pptx-skill) — 学术内容和论证结构。
2. [`baoyu-slide-deck`](https://github.com/JimLiu/baoyu-skills#baoyu-slide-deck) — 视觉叙事和版式设计。
3. `presentations:Presentations` — Codex 桌面版提供的演示文稿制作能力，用于可编辑 PPTX 和最终质检。

请分别遵守上述项目或工具各自的许可证与使用条款。

### 安装

将本仓库克隆或下载到本地，然后把整个目录放到 Codex Skills 目录：

```text
~/.codex/skills/ppt-production-workflow/
├── SKILL.md
├── README.md
└── evals/
    └── evals.json
```

同时确保上面列出的依赖 Skills 在当前环境中可用。

### 调用示例

```text
调用 ppt-production-workflow，根据这几份 Word 和会议截图制作一份科研项目汇报 PPT。
```

```text
我已经手工修改了上一版 PPT，请以最新修改的同名文件为基础，只增加一页“核心目标”，其他页面不要改。
```

```text
帮我检查这份 PPT 的逻辑、版式、文字溢出和演讲者备注，并输出可编辑终稿。
```

### 仓库内容

- `SKILL.md`：完整工作流和执行规则。
- `evals/evals.json`：覆盖新建、续改、限时汇报和 Skill 披露的测试提示。
- `README.md`：中英文使用说明。

本仓库不包含患者资料、课题原始文档、用户 PPT、截图或任何项目敏感数据。

## English Documentation

### What this is

`ppt-production-workflow` is an orchestration skill for creating and iteratively revising professional presentations. It separates content reasoning, visual design, editable PPTX production, and quality assurance into a staged workflow using the same PPT-related skills used during development:

| Stage | Skill | Primary responsibility |
|---|---|---|
| 1. Orchestration and version safety | `ppt-production-workflow` | Select create, revision, or continuation mode; lock current sources; preserve user edits |
| 2. Academic content structure | `academic-pptx` | Build the core objective, evidence chain, action titles, slide jobs, and argument hierarchy |
| 3. Visual narrative refinement | `baoyu-slide-deck` | Improve pacing, hierarchy, scientific visual language, and layout direction |
| 4. Editable production and QA | `presentations:Presentations` | Create or edit editable PPTX files, add speaker notes, render slides, and validate overflow and consistency |

It is designed for research proposals, grant or project briefings, conference talks, defenses, technical presentations, and continued editing of an existing deck.

### Core principles

- The latest user-edited PPTX is the only source deck in continuation mode.
- Never invent data, sample sizes, results, dates, fields, policies, or budgets.
- Separate confirmed facts, proposed plans, and items that still require confirmation.
- Stabilize the content structure first, refine the visual narrative second, and generate and validate the editable PPTX last.
- The workflow has **no default 10-minute limit and no fixed slide count**. Timing or slide-count constraints are applied only when the user explicitly provides them.
- Use the smallest sufficient change when editing an existing deck, and preserve the original file.

### Dependencies

This repository contains only the orchestration skill. It does not redistribute third-party skill source files.

1. [`academic-pptx`](https://github.com/Gabberflast/academic-pptx-skill) — academic content and argument structure.
2. [`baoyu-slide-deck`](https://github.com/JimLiu/baoyu-skills#baoyu-slide-deck) — visual narrative and slide design.
3. `presentations:Presentations` — the presentation capability bundled with the Codex desktop environment for editable PPTX production and final QA.

Follow the license and usage terms of each dependency separately.

### Installation

Clone or download this repository and place the complete directory in your Codex Skills folder:

```text
~/.codex/skills/ppt-production-workflow/
├── SKILL.md
├── README.md
└── evals/
    └── evals.json
```

Make sure the dependencies listed above are also available in the active environment.

### Example prompts

```text
Use ppt-production-workflow to create a research-project presentation from these Word documents and the meeting screenshot.
```

```text
I manually edited the previous deck. Use the newest same-named PPTX as the source, add only one Core Objective slide, and leave every other slide unchanged.
```

```text
Audit this deck for narrative clarity, layout consistency, text overflow, and speaker notes, then deliver an editable final PPTX.
```

### Repository contents

- `SKILL.md`: the complete orchestration workflow and operating rules.
- `evals/evals.json`: test prompts covering new-deck creation, continuation editing, explicit timing constraints, and skill-use disclosure.
- `README.md`: bilingual user documentation.

This repository contains no patient information, proposal source documents, user presentations, screenshots, or project-sensitive data.
