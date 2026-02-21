# EMPE Prompt Library

### AI-Driven Execution Prompts

This document contains the structured prompts used within the EMPE
(Structure → Map → Plan → Execute) methodology.

These prompts are not isolated commands — they are part of a layered
engineering workflow designed to provide deterministic context for
AI-assisted development.

---

# Phase 1 — Structure

## Generate Initial Technical Blueprint

Use this prompt to transform an idea into a structured PRD draft.

```
PROMPT:

I want to develop a web application that [describe the idea and core concept].
The application should include the following features and capabilities:
[describe features].

Based on this information, ask as many questions as necessary in order
to generate a complete technical PRD for this application.
```

---

# Phase 2 — Map

## Step 1 — Generate UX Flowchart (Mermaid)

```
PROMPT:

Based on the Technical Blueprint below, generate a Mermaid flowchart
representing the user interaction flow (UX).

[Paste your finalized Technical Blueprint here]
```

---

## Step 2 — Generate Data Schema (Prisma)

```
PROMPT:

Based on the Technical Blueprint and the Mermaid Flowchart below,
generate a complete Prisma schema in a single .prisma file.

Ensure all relationships between entities are included to maintain
data integrity.

[Paste Technical Blueprint]

[Paste Mermaid Flowchart]
```

---

# Phase 3 — Plan

## Execution Workspace Architecture

This phase creates a structured planning environment.

---

## Step 3.1 — Create `docs` Folder

```
PROMPT:

Based on @PRD.md, @flowchart_ux.mermaid and schema_prisma.prisma,
create a folder called docs.

Inside this directory generate Markdown files describing project
guidelines and standards.

Create a docs/README.md that serves as an index of all documentation.
```

---

## Step 3.2 — Create `agents` Folder

```
PROMPT:

Analyze docs/README.md to understand the project context.

Create an agents folder containing Markdown files representing
specialized engineering roles such as:

- Software Architect
- Backend Developer
- Frontend Developer
- QA Engineer

Also create agents/README.md acting as an index describing when
each agent should be used.
```

---

## Step 3.3 — Create Development Plan

```
PROMPT:

Analyze docs/README.md for project context.
Consult agents/README.md to select the most appropriate AI agent.

Generate a detailed development roadmap divided into logical phases.

FOCUS ONLY ON ENGINEERING TASKS:

- coding
- infrastructure setup
- database configuration
- API implementation
- UI development
- testing
- deployment

DO NOT include management tasks, meetings, research or timelines.

Create a plans folder and save the result as a Markdown file.
```

---

## Step 3.4 — Generate Specific Task Plan

```
PROMPT:

Goal: [Describe the objective, e.g. Implement OAuth2 authentication]

Instructions:
Analyze docs/README.md for project context.
Consult agents/README.md to select the appropriate agent.

Generate a detailed task plan and save it inside task-plans/
with a descriptive name.
```

---

## Step 3.5 — Task Plan Refinement Prompts

Run each prompt individually:

```
PROMPT 1:
Add the folder structure where components, pages and API endpoints
should be organized.

PROMPT 2:
List files that must be created, modified or deleted in each task.

PROMPT 3:
Identify possible side effects and propose mitigation strategies.

PROMPT 4:
Detect duplicated logic opportunities and apply SOLID and DRY principles.

PROMPT 5:
Remove timelines and any temporal references.

PROMPT 6:
Move validation and testing tasks into a separate human-check.md file.

PROMPT 7:
Generate commit messages for each task and phase.
```

---

## Step 3.6 — Optional Deep Detailing

```
PROMPT:

Create a folder for [task name] and break down the phases into
smaller, more detailed steps.
```

---

# Phase 4 — Execute

## Execution Prompt

```
PROMPT:

Goal: Execute the plan located at task-plans/[example_plan].md.

Instructions:
Use docs/README.md as project context.
Use agents/README.md to understand AI agent roles.
Execute each task sequentially according to the plan.
```

---

# Additional Useful Prompts

## Generate .gitignore

```
PROMPT:

Analyze this project and generate a proper .gitignore file.

Requirements:

- Exclude node_modules, build folders, cache and logs
- Follow Node.js and Next.js best practices
- Keep only essential source files tracked
```

---

## Generate Visual Layout Development Plan

```
PROMPT:

Analyze docs/README.md and consult agents/README.md.

Generate a detailed visual layout development plan to be executed
before backend implementation.

Include only technical tasks.
Exclude management activities, meetings or timelines.

Save the plan inside the plans folder as Markdown.
```

---

## Custom Prompt Template

```
PROMPT:

[Insert your custom prompt here]
```

---

# Notes

These prompts should be used sequentially according to the EMPE lifecycle.

They are designed to build layered context rather than isolated instructions,
reducing AI hallucination and improving execution consistency.
