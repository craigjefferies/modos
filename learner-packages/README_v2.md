# Modos – Context-Engineered Learner Packages

Modos is an experimental framework for building **LLM-powered learning tools** that combine assessment criteria, teaching content, and tutor instructions into a single **Learner Package**.

At its core, Modos is built on three parts:

1. **OMI JSON**  
   - Observable Micro-Indicators (OMIs) define *what success looks like*.  
   - These are structured, machine-readable criteria aligned to standards.  

2. **Content-Knowledge Files**  
   - Short, learner-friendly resources written in a consistent schema.  
   - Each file covers a single topic with:  
     - Summary  
     - Example  
     - Mistake  
     - Checks  

3. **Instruction Prompts**  
   - Guide the behaviour of the LLM tutor.  
   - Two core pathways:  
     - **Understand** → explainer / scaffold  
     - **Process** → practice / application  

Together, these pieces form the building blocks for **context-engineering**: the art of feeding an LLM the *right mix of information* in a structured way.

---

## The Learner Package Flow

```
Learner Input
   │ (subject, year, topic, goals)
   ▼
OMI JSON (assessment backbone)
   ▼
Content-Knowledge Files (teaching content)
   ▼
Instruction Prompts (tutor behaviour)
   ▼
Context-Assembly Layer (smart retrieval & packaging)
   ▼
Learner Package Output
   - mini lesson
   - common pitfalls
   - practice tasks
   - evidence hooks
```

---

## The Context-Assembly Layer

The **context-assembly layer** is the engine room.  
Instead of dumping everything into the model (“RAG rot”), it:

1. **Retrieves only what’s needed**  
   - Pulls the specific content-knowledge sections relevant to the learner’s query.  
   - Filters by subject, topic, and year level.  

2. **Aligns with assessment criteria**  
   - Maps the selected content back to OMIs (without putting grading logic in the file itself).  
   - Ensures evidence hooks are available for later evaluation.  

3. **Assembles a structured context window**  
   - Always ordered and predictable: Summary → Example → Mistake → Checks.  
   - Keeps sections short (≤500 tokens each) to avoid context rot.  
   - Drops in the right instruction prompt (understand vs process).  

4. **Builds the Learner Package**  
   - Outputs a ready-to-use mini lesson, practice questions, and feedback anchors.  
   - Learners see coherent content; teachers see transparent links to standards.  

---

## Why This Matters

- **For Learners** – Packages feel like real mini-lessons, not AI “blobs of text.”  
- **For Teachers** – Evidence hooks and alignment to OMIs make grading and moderation transparent.  
- **For Developers** – Simple, reusable schemas keep files lean and retrieval predictable.  

---

## Roadmap

- [ ] Flesh out seed examples for Physics, English, and Technology.  
- [ ] Add sample instruction prompts for both pathways.  
- [ ] Prototype a lightweight context-assembly script (filter + re-rank + assemble).  
- [ ] Explore packaging into daily/weekly “learning plans.”  

---

## Contributing

The design principle is **simplicity**:  
- One topic = one file.  
- Short sections, learner-friendly tone.  
- Grading logic lives in OMI JSON, not content files.  

Start by writing a content-knowledge file in `/content-knowledge` using the minimal schema. Then test how it flows into a Learner Package.
