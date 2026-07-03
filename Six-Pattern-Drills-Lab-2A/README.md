### Six Pattern Drills
**Batch:** OWL Coder
**Program:** AI Mentor Bootcamp — Aditya University
**Completed:** June 2026


## Lab 2A — Six Pattern Drills

**File:** `Day2_SixPatterns_DuvvuLakshmiPrasanna.md`
**Time:** 90 minutes
**Format:** Individual writing + paired peer-scoring

### What This Lab Covers

The same student question — *"Explain Big-O notation for a placement interview"* — was rewritten six structurally distinct ways, each targeting a different prompting pattern. Both ChatGPT and Claude were run on every prompt, and outputs were compared side by side.

### The Six Patterns

| # | Pattern | Core Technique | Best For |
|---|---------|---------------|----------|
| 1 | **Persona** | Assign a specific, named role with context | Consistent tone and domain awareness |
| 2 | **Few-Shot** | Show 2–3 example Q&A pairs before asking | Controlling output format and length |
| 3 | **Chain-of-Thought** | Force step-by-step reasoning before the answer | Transparent, structured explanations |
| 4 | **Structured Output** | Demand JSON with a strict schema | Downstream parsing, APIs, automation |
| 5 | **System Prompt** | Reusable role in custom instructions + minimal user prompt | Consistent behaviour across all chats |
| 6 | **Prompt Chaining** | 3 sequential calls — Extract → Expand → Polish | Complex tasks requiring build-up quality |

---

## Key Findings — ChatGPT vs Claude

| Pattern | Winner | Reason |
|---------|--------|--------|
| Persona | Claude | Focused cheat-sheet; ATM analogy more memorable |
| Few-Shot | Claude | Matched compact format exactly; ChatGPT wrote too much |
| Chain-of-Thought | Tie | Both followed all 4 steps correctly |
| Structured Output | Claude | Better pitfall explanation; more realistic interview question |
| System Prompt | Claude | Closing line "separates you from 80% of candidates" is far more motivating |
| Prompt Chaining | Claude | Chat 1 produced more actionable sub-concepts; better snowball effect |

**Overall Self Scores:** Claude 27/30 · ChatGPT 24/30

**Observation:** ChatGPT produces better comprehensive study guides. Claude produces sharper, more interview-ready, more student-motivating outputs. For placement prep, Claude's focused style wins consistently.

---

## Scoring Rubric (5 Criteria, 10 Points Per Prompt)

Each prompt was peer-scored on:

| Criterion | What It Checks | Max |
|-----------|---------------|-----|
| **Clarity** | Single intent — no "do everything" prompts | 2 |
| **Context** | Audience and situation supplied | 2 |
| **Specificity** | Concrete subject and scope | 2 |
| **Format** | Output shape explicitly requested | 2 |
| **Verification** | Follow-up or verify step included | 2 |

**Pass threshold:** 7/10 per prompt

---

## Patterns I Will Use Most With Students

**Persona + Prompt Chaining.**

Persona works because B.Tech placement prep has a very specific audience, tone, and goal — once the persona is set correctly, every response is placement-relevant without extra instructions. Prompt Chaining works because complex topics like Big-O, recursion, or dynamic programming cannot be explained well in a single pass; breaking it into Extract → Expand → Polish produces outputs that are both accurate and student-ready.

---

## Notable Observations

- **Pattern 4 (Structured Output):** Both ChatGPT and Claude added ` ```json ` fences despite being explicitly told not to. This is a known model behaviour and will be fixed in Lab 2B using `response_schema` + Pydantic validation.
- **Pattern 2 (Few-Shot):** ChatGPT broke the compact Q&A format by adding paragraphs of context. Claude matched the format exactly. This shows that Claude is more sensitive to format cues in few-shot examples.
- **Pattern 6 (Prompt Chaining):** The three-step chain produced a richer, more accurate final output than any single pattern. The key insight: the quality of Chat 3 (Polish) is directly determined by the specificity of Chat 1 (Extract). Garbage list in → generic synthesis out.

---

## How to Reproduce Any Prompt

All six prompts are complete and copy-pasteable in the lab file. Requirements:

- ChatGPT free tier (chat.openai.com)
- Claude free tier (claude.ai)
- No plugins, no paid features, no API keys required
- Pattern 5 uses Claude's Custom Instructions under Profile → Settings → Customize

Every result in this portfolio is reproducible on free tools.

---

*Portfolio maintained as part of the OWL Coder AI Mentor Bootcamp, Aditya University.*
