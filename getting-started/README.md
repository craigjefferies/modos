# Getting Started with Modos

Modos helps you create AI tutors that teach like real educators: shifting strategies, asking good questions, and adapting when students get stuck.

This guide is designed for teachers with little or no technical background.
You only need two things to get started:

---

## What You Need

1. Instruction Prompt  
   - We've provided a generic AI tutor prompt you can use right away. It tells the AI how to behave like a real tutor: switching modes, asking questions, and explaining clearly.  
   - Copy this into your GPT Builder, Custom GPT, or platform of choice.

2. OMI File (JSON)  
   - This file contains the key learning indicators your tutor will use to guide feedback and questions. Think of it as your teaching checklist.  
   - You don’t need to code. You can use our OMI Build Prompt (included below) to help the AI generate your OMI file for you.

---

## Step-by-Step

### 1. Copy the Generic Instruction Prompt  
You'll find this in the `understand/` or `process/` folder, depending on your use case. Paste it into your GPT custom instructions.

Example location: `modos/understand/instruction_prompt.txt`

---

### 2. Create Your OMI File Using the OMI Build Prompt  
Open ChatGPT or your AI tool and paste in the prompt below:
location: `modos/obervableMicroIndicators/build-prompt.txt`
The AI will return a structured file you can copy into your folder (e.g., `as91354_omis.json` or `ecosystems_omis.json`).

---

## Folder Structure Example
```
modos/
  getting-started/
    README.md
  understand/
    instruction_prompt.txt
    sample_omis.json
  process/
    instruction_prompt.txt
    sample_omis.json
```

---

## Ready to Go?  
Once you have your:
- Instruction Prompt  
- OMI JSON file  

...you can paste both into your AI tool and start tutoring.

Your AI tutor will now:
- Ask better questions  
- Switch teaching strategies when students get stuck  
- Give feedback based on the learning goals you care about

---

## Need Help?
- Use the `examples/` folder to see working versions  
- Modify the prompts slowly—small changes go a long way  
- Reach out if you want more scaffolds or ready-made OMIs

Modos is about teaching that adapts. You're still the teacher—this just gives you a smarter assistant.
