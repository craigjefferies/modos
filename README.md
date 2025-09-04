# Context Engineering for NCEA Assessments

> **This is essentially a hack to make any LLM work effectively as a teaching assistant within the context of NCEA.**

This framework creates a structured context scaffold—guiding an LLM to function as a tutor, grader, or guide aligned with New Zealand’s NCEA standards. It carefully designs the input ecosystem to shape behavior, evaluation, and domain specificity.

## Core Artifacts

1. **LLM Instructions**  
2. **Assessment (Observable Micro-Indicators, OMIs)**  
3. **Content-Knowledge** *(optional)*

---

## In-Depth Artifact Breakdown

### 1. LLM Instructions  
Defines the specific instructional roles an LLM can adopt:

- **Process Instructor**  
  Guides students through procedural steps—offering structure and direction on how to plan, approach, and solve tasks.

- **Knowledge Instructor**  
  Serves as a tutor—explaining concepts clearly, helping students grasp subject matter, and articulate their understanding.

- **Grader**  
  Evaluates student submissions by mapping them to observable indicators aligned with NZQA Achievement Standards—providing standards-based, structured feedback.

### 2. Assessment (Observable Micro-Indicators, OMIs)  
This is the heart of the framework. OMIs decompose Achievement Standards into actionable elements:

- **Observable Elements**  
  Clearly defined, assessable performance markers.

- **Detection Hints**  
  Indicators the LLM can look for to recognize student understanding or skill demonstration.

- **Examples of Expected Work**  
  Sample responses or artifacts that illustrate successful performance.

This ensures LLM assessments are precise, transparent, and tightly coupled to NZQA criteria.

### 3. Content-Knowledge *(Optional Artifact)*  
A curated repository of domain-specific content—examples, definitions, scaffolds—that narrows the LLM’s output scope. Including this artifact provides factual grounding, improving output relevance and pedagogical accuracy.

---

## Why This Structure Works

By assembling these artifacts:

- **LLM Instructions** guide the behavior and roles of the model.
- **OMIs** anchor evaluations to clear, observable student outcomes.
- **Content-Knowledge** grounds responses in accurate, focused domain context.

Together, they form a **context engineering** approach—where you're not just instructing the LLM, you're crafting the environment it needs to act effectively as an NCEA-aligned teaching assistant.

> Context engineering is "building dynamic systems to provide the right information and tools in the right format such that the LLM can plausibly accomplish the task." :contentReference[oaicite:1]{index=1}

---

