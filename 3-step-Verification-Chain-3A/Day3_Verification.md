# Day 3 — Verification Chain Lab (Lab 3A)

**Mentor:** Duvvu Lakshmi Prasanna  
**Date:** 11 June 2026  
**Lab Duration:** 90 minutes  
**Objective:** Verify 5 AI-generated Indian campus placement statistics through a 3-step chain: Gemini → Perplexity → Primary Source. At least one verdict must be PARTIAL or FALSE.

---

## Step 1 — Claims Generated via Gemini

**Prompt used:**
```
List 5 specific statistics about Indian campus placement in 2025-2026.
For each:
1. State the statistic.
2. State the year.
3. State the source organisation.
Format as a numbered list.
```

**Gemini Output:**

1. **PPOs Growth Rate** — Pre-Placement Offers extended to students at top IITs witnessed a significant surge of approximately 33%. Year: 2025–2026. Source: CollegeDekho.
2. **Day-1 Record Offers at IIT Kanpur** — IIT Kanpur secured its highest-ever opening day recruitment numbers, logging a total of 672 job offers on Day 1 of the formal placement season. Year: 2025–2026. Source: IITian Vibes.
3. **Average National IT Fresher Salary** — The national average salary for general engineering graduates entering standard IT service-based roles stagnated between ₹3.5 LPA and ₹4.5 LPA. Year: 2025–2026. Source: Hyring (referencing Economic Times tracking data).
4. **CSE Placement Rates at Top-Tier Institutions** — Computer Science and Engineering (CSE) branches maintained an elite hiring status across top-tier institutions, achieving a 95% to 100% total placement rate with average packages exceeding ₹40 LPA. Year: 2025–2026. Source: CollegeDekho Educational Portal.
5. **Multi-Tier Salary Gap** — Baseline starting salary for BTech freshers inside Tier-1 institutions (IITs & top NITs) averaged between ₹12–18 LPA, contrasting with Tier-2/Private colleges which recorded average initial packages of ₹3–6 LPA. Year: 2025–2026. Source: FindMyCollege Placement Analytics Platform.

---

## Step 2 — Perplexity Verification

**Prompt used for each claim:**
```
Verify: "<claim pasted exactly>"
Cite 2 primary sources.
```

**Perplexity summary of findings:**

- **Claim 1 (PPO 33%):** Perplexity confirmed a 33%+ PPO surge — but only for IIT Delhi specifically, not all top IITs collectively. Cited: collegedunia.com, testbook.com
- **Claim 2 (672 offers):** Perplexity confirmed 672 Day-1 offers at IIT Kanpur with 627 students placed and 27% rise in PPOs. Cited: collegehai.com, bestcolleges.indiatoday.in
- **Claim 3 (₹3.5–4.5 LPA):** Perplexity could not locate the specific Hyring/Economic Times dataset. Found only general Tier-3 salary ranges (₹3–5 LPA) but no verified national average for generic IT freshers. No direct confirming source found.
- **Claim 4 (CSE 95–100%, ₹40 LPA avg):** Perplexity returned CollegeDekho as a source, but the actual CollegeDekho data showed IIT average packages at ~₹23.5 LPA, not ₹40+ LPA. No source confirmed 95–100% CSE placement universally across top-tier institutions.
- **Claim 5 (Tier-1 vs Tier-2 salary gap):** Perplexity found directionally similar ranges at ccbp.in and LinkedIn sources (Tier-1: ₹12–25 LPA; Tier-2: ₹3–8 LPA), but no FindMyCollege Placement Analytics document was directly retrieved.

**Primary source URLs provided by Perplexity:**

1. https://home.iitd.ac.in/show.php?id=804&in_sections=News
2. https://collegedunia.com/news/iit-delhi-placements-records-2025-26-alertid-144613
3. https://www.educationtimes.com/article/newsroom/99740568/iit-delhi-placements-2025-26-pre-placement-offers-witness-over-33-surge
4. https://www.iitk.ac.in/day-1-of-2025-26-placement-season
5. https://collegedunia.com/news/iit-kanpur-placement-2025-26-day-1-breaks-record-with-672-job-offers-alertid-142053
6. https://indianexpress.com/article/education/record-672-job-offers-on-day-1-of-iit-kanpurs-placement-season-2025-26-10399502/

---

## Step 3 — Primary Source Check

Each URL was opened and the actual content was compared against Gemini's claim.

**Claim 1:** IIT Delhi's official placement page and Collegedunia confirmed the 33%+ PPO rise — but this figure is specific to IIT Delhi, not generalised across all top IITs as Gemini stated. The number is real; the scope is overstated.

**Claim 2:** Multiple independent sources (CollegeHai, India Today) confirmed exactly 672 Day-1 offers at IIT Kanpur in 2025–26. The number, year, and institution all match.

**Claim 3:** No Hyring report or Economic Times dataset was accessible that reported a verified national average of ₹3.5–4.5 LPA for generic IT freshers in 2025–26. The Perplexity-cited sources did not contain this specific figure.

**Claim 4:** The CollegeDekho page opened correctly. It reported IIT average packages rising from ~₹21.8 LPA to ~₹23.5 LPA — not the ₹40+ LPA average Gemini claimed. The ₹40 LPA figure may reflect peak/highest individual offers, not the institutional average across top-tier colleges.

**Claim 5:** The ccbp.in source confirmed similar salary ranges (Tier-1: ₹12–25 LPA, Tier-2: ₹3–8 LPA), which partially supports Gemini's claim. However, the FindMyCollege Placement Analytics Platform as a named primary source was not directly verifiable from retrieved pages.

---

## Step 4 — Verification Matrix

| # | Claim | AI Source | Perplexity Check | Primary Source URL | Verdict |
|---|-------|-----------|------------------|--------------------|---------|
| 1 | PPOs at top IITs surged ~33% in 2025–26 | CollegeDekho | Confirmed for IIT Delhi only — not all top IITs collectively. Sources: collegedunia.com, testbook.com | https://collegedunia.com/news/iit-delhi-placements-records-2025-26-alertid-144613 | PARTIAL |
| 2 | IIT Kanpur recorded 672 job offers on Day 1 of 2025–26 placements | IITian Vibes | Confirmed by multiple independent sources — 672 offers, 627 placed, 27% PPO rise. Sources: collegehai.com, bestcolleges.indiatoday.in | https://collegedunia.com/news/iit-kanpur-placement-2025-26-day-1-breaks-record-with-672-job-offers-alertid-142053 | VERIFIED |
| 3 | National average salary for generic IT service freshers was ₹3.5–4.5 LPA in 2025–26 | Hyring (referencing Economic Times data) | No Hyring report or Economic Times dataset confirmed this specific figure. General Tier-3 ranges found (₹3–5 LPA) but not a national average. | No primary source found | NO PRIMARY SOURCE FOUND |
| 4 | CSE at top-tier institutions achieved 95–100% placement with avg packages >₹40 LPA in 2025–26 | CollegeDekho Educational Portal | CollegeDekho data shows IIT avg packages at ~₹23.5 LPA — not ₹40+ LPA. No source confirms 95–100% CSE placement universally. | https://www.collegedekho.com/articles/highest-packages-at-iit-placements/ | FALSE |
| 5 | Tier-1 (IITs/NITs) avg ₹12–18 LPA vs Tier-2/Private avg ₹3–6 LPA in 2025–26 | FindMyCollege Placement Analytics Platform | Directionally supported by ccbp.in and LinkedIn sources (Tier-1: ₹12–25 LPA; Tier-2: ₹3–8 LPA). FindMyCollege as named source not directly verified. | https://www.ccbp.in/blog/articles/what-is-the-placement-difference-between-tier-1-and-tier-2-colleges | PARTIAL |

---

## Step 5 — Verdict Summary

| Verdict | Count |
|---------|-------|
| ✅ VERIFIED | 1 |
| ⚠️ PARTIAL | 2 |
| ❌ FALSE | 1 |
| 🔴 NO PRIMARY SOURCE FOUND | 1 |

**4 out of 5 claims (80%) did not pass full verification.**

---

## Step 6 — Reflection

The claim that looked most authoritative but was actually weakest was **Claim #4**: *"Computer Science and Engineering (CSE) branches maintained an elite hiring status across top-tier institutions, achieving a 95% to 100% total placement rate with average packages exceeding ₹40 LPA (CollegeDekho Educational Portal, 2025–26)."*

Gemini cited CollegeDekho confidently, and Perplexity initially appeared to confirm it by returning CollegeDekho as a source. The claim sounded credible — it named a well-known portal, used precise percentages, and referenced a plausible organisation. But when I opened the actual CollegeDekho page, I found that the reported IIT average package for 2025–26 was approximately ₹23.5 LPA — not ₹40+ LPA. The ₹40 LPA figure likely reflects peak or highest individual offers at select institutions, which Gemini had misrepresented as a broad institutional average. No source confirmed a 95–100% CSE placement rate universally across top-tier colleges either.

The lesson: **confidence does not equal correctness.** The most dangerous AI-generated statistic is not the one that sounds wrong — it is the one that sounds exactly right. Perplexity confirmed the source name without verifying the number. Only opening the primary source directly revealed the error. The verification step belongs to the human, every time.

---

## Primary Sources Referenced

| Source | URL | Used For |
|--------|-----|----------|
| IIT Delhi Placements 2025–26 — Collegedunia | https://collegedunia.com/news/iit-delhi-placements-records-2025-26-alertid-144613 | Verifying Claim 1 (PPO growth — PARTIAL) |
| IIT Delhi Official News Page | https://home.iitd.ac.in/show.php?id=804&in_sections=News | Verifying Claim 1 (PPO growth) |
| Education Times — IIT Delhi PPOs | https://www.educationtimes.com/article/newsroom/99740568/iit-delhi-placements-2025-26-pre-placement-offers-witness-over-33-surge | Verifying Claim 1 |
| IIT Kanpur Day-1 Record — Collegedunia | https://collegedunia.com/news/iit-kanpur-placement-2025-26-day-1-breaks-record-with-672-job-offers-alertid-142053 | Verifying Claim 2 (VERIFIED) |
| IIT Kanpur Official Press Release | https://www.iitk.ac.in/day-1-of-2025-26-placement-season | Verifying Claim 2 |
| CollegeDekho — IIT Highest Packages | https://www.collegedekho.com/articles/highest-packages-at-iit-placements/ | Falsifying Claim 4 (FALSE) |
| CCBP — Tier-1 vs Tier-2 Placement Comparison | https://www.ccbp.in/blog/articles/what-is-the-placement-difference-between-tier-1-and-tier-2-colleges | Partially verifying Claim 5 (PARTIAL) |

---

## Acceptance Checklist

- ✅ Matrix has all 5 rows × 5 columns filled (claim, AI source, Perplexity check, primary source URL, verdict)
- ✅ At least 1 verdict is PARTIAL, FALSE, or NO PRIMARY SOURCE FOUND *(4 out of 5)*
- ✅ Reflection paragraph identifies the weakest-sounding-yet-most-authoritative claim (Claim #4)
- ✅ Saved as `Day3_Verification.md`
- ✅ Pushed to ai-mentor-portfolio repository
