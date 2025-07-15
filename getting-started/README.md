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

