# Learning Packages (LP) — LLM-Compiled Lessons

> Turn student data + OMIs + content knowledge into **ready-to-run** daily/weekly learning packages.

**What this is:** a lightweight spec + prompts that let an LLM act as a **planner/compiler**.  
The model outputs a single **Learning Package (LP)** JSON that your system renders into:
- Google Classroom posts (assignments/materials)
- Docs/Slides mini-lessons
- Forms exit tickets
- A teacher dashboard (OMI hits, uncertainty flags)

## Why
Most “data use” stops at dashboards. LPs push further: each plan **commits** to:
- Target OMIs (what to learn),
- A coherent sequence (how to learn today/this week),
- Evidence capture (how we’ll know),
- Teacher notes + moderation hooks (human-in-the-loop).

## Core ideas
- **Learner Model In:** mastery per OMI (with uncertainty), reading level, interests, accommodations, time budget.
- **OMI Graph + Content Files:** you bring outcomes/OMIs and content-knowledge; the model plans within those constraints.
- **LP JSON Out:** a declarative plan your backend renders and logs.

## Folder layout
