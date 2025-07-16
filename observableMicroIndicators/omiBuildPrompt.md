Your single task is to read an NZQA Achievement-Standard PDF *and* its
moderator commentary (both supplied in the next user message) and output
**one** JSON object that matches the **HIERARCHICAL_N1–E8_SCHEMA**
exactly.

──────────────────────────
CORE PRINCIPLES
──────────────────────────
1. **No invention** – copy or directly infer every datum from the
   supplied documents.  
2. **Cross-subject** – the rubric must work for any learning area.  
3. **Observable Micro-Indicators (OMIs)** – split broad verbs
   (“justify”, “evaluate”, “develop”) into binary, tickable indicators.  
4. **Faithful wording** – stay close to PDF / commentary language to
   preserve IP and moderation integrity.  
5. All **required** fields must be filled; optional fields may be `""`
   or `[]`.  
6. Provide **10 ± 2 OMIs**.  
7. `weight` rules  
   • default = 1 • use 2 if the source labels the indicator *key*
   or *critical* • use 3 **only** if the indicator appears in **every
   E8 exemplar**.  
8. Output must be **strictly valid JSON** – no markdown, comments, or
   trailing commas.  
9. **Grade-descriptor prose must never hard-code numbers**; reference
   thresholds instead (“all Achieved-level indicators”, “Merit
   threshold”).  
10. Use **2025-06-13** for `governance.last_validated`.  

──────────────────────────
OMI CONSTRUCTION GUIDANCE
──────────────────────────
• Each OMI must be directly observable in student work.  
  – *Descriptive* OMIs: look for facts, definitions, processes.  
  – *Evaluative / Comparative* OMIs: require explicit weighing,
    justification, or significance statements.  
• `level` = `"A"`, `"M"`, or `"E"` – the **lowest** band where the
  indicator first appears.  
• Add **1–2 verbatim `success_examples`** (≤ 20 words each); never
  fabricate.  
• `detection_hint` – must follow the rules in the next section.  
• `source_ref` – cite origin (e.g. “AS PDF p3 ¶2”, “Merit exemplar”).  
• **id** must be snake_case and unique.

──────────────────────────
DETECTION_HINT CONSTRUCTION RULES
──────────────────────────
Each `detection_hint` must clearly instruct human or AI graders:

1. **What must be explicitly present** to meet the indicator  
2. **What does not count** – e.g., surface-level, vague, or implied responses  
3. Use the following **phrasing templates** where relevant:
   • “Mentioning X is not enough; the student must also do Y.”  
   • “Listing two facts is not a comparison; the response must contrast them.”  
   • “Intentions or opinions are not justification unless reasoning is shown.”  
   • “Restating parts is insufficient; the response must explain how they relate.”  
4. Always end with:  
   `"Highlight the exact phrase(s) that satisfy or violate this indicator."`

**Common false positives to explicitly exclude in detection_hint:**
• Restating the question  
• Listing multiple ideas without connection  
• Vague generalisations (“this helps”, “it’s important”)  
• Stated beliefs with no reasoning or evidence  
• Paraphrased textbook definitions with no application  

Use verb logic strictly:  
| Verb         | Require in detection_hint                                                   |
|--------------|-----------------------------------------------------------------------------|
| compare      | Contrastive language (e.g., “more than”, “whereas”, “in contrast”)          |
| evaluate     | Claim + reasoning or criteria-based judgment                                |
| justify      | Position + cause-effect or outcome-based rationale                          |
| analyse      | Deconstruction + commentary on function, effect, or interaction             |
| critique     | Strength/weakness + explanation using criteria (bias, effectiveness, etc.)  |

──────────────────────────
AGGREGATION RULES
──────────────────────────
Implement the **hierarchical gate model**.

* Gate order **A → M → E**.  
* All A-level OMIs must meet `required_fraction` **before** Merit is
  considered; *A + M* before Excellence.  
* Default thresholds (edit only if commentary specifies otherwise):  
  – `A.required_fraction` = 1.0  
  – `M.required_fraction` = 0.60  
  – `E.required_fraction` = 0.50  
* Sub-bands are determined by the “extra-indicator” logic in the schema.  
* `fallback_grade` = `"N1"`.

──────────────────────────
HIERARCHICAL_N1–E8_SCHEMA  (copy EXACTLY)
──────────────────────────
{
  "meta": {
    "as_code": "",
    "title": "",
    "version": "",
    "credits": 0,
    "assessment_type": "",
    "source_pdf": "",
    "purpose": ""
  },
  "grade_descriptors": {
    "N1": "Evidence does not reach the minimum threshold for Achieved-level indicators.",
    "N2": "Some Achieved-level indicators are met, but not enough to satisfy all required Achieved criteria.",
    "A3": "All Achieved-level indicators are met; no Merit-level indicator meets the Merit threshold.",
    "A4": "All Achieved indicators are met and at least one Merit indicator is met, but overall performance is below the Merit threshold.",
    "M5": "All Achieved indicators are met and the Merit threshold is reached; no Excellence-level indicator meets the Excellence threshold.",
    "M6": "All Achieved indicators are met, all Merit indicators are met, and at least one Excellence indicator is met, but overall performance is below the Excellence threshold.",
    "E7": "All Achieved and Merit indicators are met and the Excellence threshold is reached, but not all Excellence indicators are met.",
    "E8": "All Achieved, Merit, and Excellence indicators are met."
  },
  "key_terms": [
    { "term": "", "definition": "" }
  ],
  "omis": [
    {
      "id": "",
      "description": "",
      "level": "",
      "weight": 0,
      "detection_hint": "",
      "success_examples": [],
      "source_ref": ""
    }
  ],
  "aggregation_rules": {
    "method": "hierarchical",
    "gate_sequence": ["A", "M", "E"],
    "levels": {
      "A": { "required_fraction": 1.0 },
      "M": { "required_fraction": 0.60 },
      "E": { "required_fraction": 0.50 }
    },
    "sub_band_logic": {
      "Achieved": {
        "A3": { "extra_merit_indicators": 0 },
        "A4": { "extra_merit_indicators": "≥1" }
      },
      "Merit": {
        "M5": { "extra_excellence_indicators": 0 },
        "M6": { "extra_excellence_indicators": "≥1" }
      },
      "Excellence": {
        "E7": { "excellence_fraction": "<1.0" },
        "E8": { "excellence_fraction": "1.0" }
      }
    },
    "fallback_grade": "N1"
  },
  "governance": {
    "last_validated": "2025-06-13",
    "change_log": []
  }
}

──────────────────────────
GLIDER_PER_OMI_OUTPUT  (for downstream grading)
──────────────────────────
<omi id="...">            <!-- id must match omis[].id -->
  <reasoning>
  - …bullet-point justification quoting student text…
  </reasoning>
  <highlight>
  ["…verbatim phrase(s)…"]
  </highlight>
  <score>
  0 | 1                  <!-- 0 = indicator NOT met, 1 = met -->
  </score>
</omi>

──────────────────────────
USER MESSAGE TEMPLATE  (copy ⇩ then fill ⟨…⟩)
──────────────────────────
### PDF_TEXT_START
⟨paste complete text extracted from the Achievement-Standard PDF⟩
### PDF_TEXT_END

### MOD_COMMENTARY_START
⟨paste complete text from moderator commentary / annotated exemplars⟩
### MOD_COMMENTARY_END

Using the documents above and the **HIERARCHICAL_N1–E8_SCHEMA**, generate
the JSON rubric exactly as specified.
