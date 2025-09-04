# How to Build a Context-Engineered LLM Tutor for AS92006

**Goal:** Enable teachers to quickly assemble a purpose-built LLM tutoring tool using pre-made context artifacts, aligned to NCEA Achievement Standard AS92006.

---

##  Overview

This guide shows how to construct a **context-engineered LLM assistant** by combining:

1. **LLM Instructions** – defining the role (Process Instructor, Knowledge Instructor, Grader)  
2. **Assessment (OMIs)** – finely—decomposed indicators  
3. **Content-Knowledge (Optional)** – focused domain resources  

Rather than creating these artifacts yourself, you’ll **download the premade files** from the repository and integrate them into your chosen LLM platform.

---

##  Step-by-Step Guide

### 1. Download the Pre-Made Artifacts

From the Modos repository (AS92006 experiment), grab:

- `AS92006.json` — contains the **LLM Instructions** and **OMIs**
- `content-knowledge.txt` — contains targeted domain material (optional but recommended)  
  *These files are accessible in the `experiments/AS92006` directory.* :contentReference[oaicite:1]{index=1}

### 2. Prepare Your LLM Environment

Open your preferred LLM-as-service platform:
- **Gemini Gem**, **CustomGPT**, **Replit.ai**, or similar

### 3. Upload or Paste the Artifacts

- **File Upload Area**: Upload both `AS92006.json` and `content-knowledge.txt` (if using).
- **Instruction Prompt Field**: Open the JSON file and **copy the instructions section** into the instruction/system prompt area.

### 4. Configure Your Instructional Roles

Within the JSON, you'll find definitions for three roles:

- **Process Instructor** – To guide students through step-by-step tasks
- **Knowledge Instructor** – To explain concepts and support understanding
- **Grader** – To evaluate student responses against OMIs mapped to the Achievement Standard

Ensure these instructions are correctly pasted into the platform’s system or instruction prompt area.

### 5. Load the Assessment (OMIs)

From the same JSON file, locate the **OMIs**—the finely grained, observable indicators. Paste them into a section (or file) labeled "Assessment" or similar so the LLM can reference what to look for.

### 6. (Optional) Add Domain Content

If using `content-knowledge.txt`, upload or paste that to provide context-limited, domain-specific examples and scaffolded materials. This helps the LLM keep focused and accurate in outputs.

### 7. Finalize and Test

- Save your LLM setup.
- Try out simple prompts like:
  - *“Explain usability in a human-computer interface.”*
  - *“Evaluate this student response: [insert answer].”*
- Observe how the assistant responds—instructor mode, grader mode, etc.

Based on performance, iterate:
- Refine the instruction prompts
- Adjust OMI alignment
- Tweak content knowledge inclusion

---

##  Why This Works

You are engineering the **context**—not just giving a prompt—so the LLM receives:

| Artifact              | Role in Context Engineering                                 |
|-----------------------|-------------------------------------------------------------|
| **LLM Instructions**  | Defines tutor’s behavior (process, knowledge, evaluation)    |
| **OMIs (Assessment)** | Targets evaluation against clear, observable criteria        |
| **Content-Knowledge** | Provides domain grounding and keeps outputs focused           |

This method embodies **context engineering**, ensuring the LLM has just the right inputs to reliably perform as a teaching assistant tailored to NCEA AS92006.

---

##  Next Steps

- Train other teachers to replicate this workflow easily
- Develop similar artifacts for other standards
- Build a shared library of LLM Gems/CustomGPTs for NCEA teaching across standards

---

Need help drafting a template JSON for another standard, or supporting more intuitive upload instructions? Let me know—I’m happy to help!
::contentReference[oaicite:2]{index=2}
