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


## Quick start
1. Review `schema/lp.schema.json`.
2. Generate a package by giving the **planner prompt** your OMI JSON, content-knowledge file, and a small learner model.
3. Validate output against the schema.
4. Render assets (your infra) and log OMI-aligned evidence.

## Lifecycle
1. **Plan** → LLM emits LP JSON (targets, sequence, evidence hooks).  
2. **Teach** → Renderer creates Classroom/Docs/Forms.  
3. **Capture** → Student work + auto-tagged OMI evidence.  
4. **Moderate** → Teacher resolves uncertainty; mastery updates.  
5. **Stitch** → Four daily LPs → weekly synthesis.

## Ethos
- **Human-in-the-loop**: never auto-grade summatives.  
- **No guessing**: missing constraints → add a `teacher_todo` instead of inventing.  
- **Equity**: rationale for difficulty choices; surface repeated low-challenge plans.

## Status
- ✅ Schema + samples + prompts
- ⏳ Renderers (Classroom/Docs/Forms)
- ⏳ Dashboard (OMI hits, uncertainty)
- ⏳ Data adapters (to your SIS/LMS)

## License
MIT (or your choice)

