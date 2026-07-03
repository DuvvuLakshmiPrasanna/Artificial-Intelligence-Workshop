# AI Mentor Portfolio — Day 3: Verification Chain Lab

> **"Confidence does not equal correctness. The verification step belongs to the human — every time."**

---

## Overview

This repository contains the completed submission for **Lab 3A: Verification Chain**, conducted on Day 3 of the AI Mentor Training Program. The lab demonstrates a structured 3-step fact-checking methodology for AI-generated statistics:

```
AI Output (Gemini)  →  Secondary Check (Perplexity)  →  Primary Source (Direct URL)
```

The exercise used Indian campus placement statistics for 2025–26 as the verification domain.

---

## Files

| File | Description |
|------|-------------|
| `Day3_Verification.md` | Completed verification matrix, verdicts, reflection, and primary sources |
| `README.md` | This file — context, methodology, and key findings |

---

## Methodology

### Step 1 — Generate Claims (Gemini)
Used the following prompt in Gemini:
> *"List 5 specific statistics about Indian campus placement in 2025-2026. For each: state the statistic, the year, and the source organisation. Format as a numbered list."*

### Step 2 — Secondary Verification (Perplexity)
Each claim was submitted to Perplexity with instructions to cite 2 primary sources. Perplexity responses were recorded but **not treated as final verification**.

### Step 3 — Primary Source Check (Direct URL)
Every Perplexity-cited URL was opened manually. The actual number, year, and context were compared directly against the AI-generated claim.

---

## Results at a Glance

| # | Claim (Summary) | Verdict |
|---|-----------------|---------|
| 1 | ~33% PPO growth at top IITs (CollegeDekho) | **PARTIAL** |
| 2 | IIT Kanpur: 672 Day-1 offers, record high (IITian Vibes) | **VERIFIED** |
| 3 | National IT fresher avg salary ₹3.5–4.5 LPA (Hyring/ET) | **NO PRIMARY SOURCE FOUND** |
| 4 | CSE: 95–100% placement, avg >₹40 LPA (CollegeDekho) | **FALSE** |
| 5 | Tier-1 avg ₹12–18 LPA vs Tier-2 ₹3–6 LPA (FindMyCollege) | **PARTIAL** |

**4 out of 5 claims (80%) failed full verification** — consistent with the lab's expected 70–80% non-VERIFIED rate for AI-generated statistics.

---

## Key Finding

**Claim #4 was the most instructive failure.** Gemini stated that CSE branches at top-tier institutions averaged packages *exceeding ₹40 LPA* in 2025–26 — a confident, specific, sourced claim. Perplexity returned CollegeDekho as a confirming source. But opening the actual CollegeDekho page revealed the true IIT average was approximately **₹23.5 LPA** — nearly half the claimed figure. The ₹40 LPA number likely reflects peak/highest offers, not institutional averages, yet Gemini presented it as a broad average without qualification.

This is the core lesson: **the most authoritative-sounding claims are often the most dangerous**, precisely because they bypass skepticism.

---

## Takeaway for Teaching

When mentoring students on AI-assisted research, this lab establishes three non-negotiable rules:

1. **Never cite an AI output directly.** AI tools generate plausible-sounding statistics that may be fabricated, misattributed, or out of context.
2. **Secondary AI verification (Perplexity) is not primary verification.** A second AI confirming a first AI's claim is circular — it is not evidence.
3. **The primary source is the only source.** If the original document doesn't contain the exact number, year, and context, the claim is unverified — regardless of how confident the AI appeared.

---

## Acceptance Checklist

- ✅ 5 claims generated via Gemini
- ✅ 5 Perplexity verification checks completed
- ✅ 5 primary source URLs opened and reviewed
- ✅ All 5 verdicts assigned
- ✅ At least 1 verdict is PARTIAL, FALSE, or NO PRIMARY SOURCE FOUND *(4 out of 5)*
- ✅ Reflection paragraph written and identifies weakest-yet-authoritative-looking claim
- ✅ Saved as `Day3_Verification.md`
- ✅ README documents methodology and findings

---

*Submitted as part of the AI Mentor Training Program — Day 3 Lab 3A*
