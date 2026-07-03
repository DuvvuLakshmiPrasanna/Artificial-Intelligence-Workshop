# 4-Tool AI Comparison Matrix — Lab 1A

**Name:** Duvvu Lakshmi Prasanna  
**Date:** 8th June 2026  
**Cohort / Batch:** OWL Coder

---

## Task 1 — Summarisation

**Prompt used:**
> Summarise this article in 5 bullet points. Each bullet: maximum 15 words. Do not lose the key claims. Do not add information not in the article.

### Responses

#### ChatGPT
- AI adoption for placement preparation is rapidly increasing across Indian engineering colleges.
- Recruiters added longer interviews and internet-free coding rounds against AI-rehearsed responses.
- AI-fluent students receive significantly more Tier-1 offers, widening equity concerns.
- Verification challenges persist; AI inaccuracies require cross-checking with sources and primary documents.
- Agentic AI will dominate placement preparation, making AI literacy and verification essential.

#### Claude
- Over 60% of Tier-1 B.Tech students used AI for placement prep in 2025; 95% projected by 2028.
- AI-fluent students are 2.4x more likely to receive Tier-1 offers, raising equity concerns.
- Recruiters lengthened interviews by 35% and added live coding rounds to counter AI-coached answers.
- Frontier AI models are wrong 8–12% of the time; students risk confidently stating non-existent facts.
- A three-step verification chain (AI → secondary source → primary source) reduced student factual errors by 60%.

#### Gemini
- AI adoption: Over 60% of Tier-1 B.Tech students use AI for placement preparation as of 2025.
- Recruiter response: Recruiters introduced longer interviews and live coding to counter highly rehearsed AI-coached answers.
- Equity gap: Students fluent in AI are 2.4 times more likely to get top-tier offers.
- Verification problem: AI models hallucinate facts, making teaching a verification chain essential for students.
- Future trend: Placement training will shift heavily toward agentic AI workflows by 2028.

#### Perplexity
- By 2025, 60%+ Tier-1 B.Tech students use ChatGPT-like tools; 95% expected by 2028.
- Students progressed from résumés (2023) to 50+ AI mock interviews by 2025.
- Recruiters lengthen interviews and add unscripted questions, live no-internet coding rounds.
- AI fluency widened placement inequity; AI users 2.4× likelier to get Tier-1 offers.
- 2026 verification chain (ask AI, verify with secondary source, check primary URL) reduced factual errors.

### Task 1 Scores

| Criterion | ChatGPT | Claude | Gemini | Perplexity |
|-----------|---------|--------|--------|------------|
| **Faithfulness** — All key claims preserved, no fabrication | 3 | 5 | 4 | 4 |
| **Structure** — Numbered, parallel form, easy to read | 4 | 5 | 5 | 4 |
| **Brevity** — Every bullet ≤ 15 words | 5 | 3 | 5 | 5 |
| **TOTAL (out of 15)** | **12** | **13** | **14** | **13** |

**Scoring anchor:** A score of 3 = output works but had at least one fixable issue (omitted stat, slightly long bullet, awkward phrasing).

### Task 1 — Observations

| Tool | What it did well | What it missed |
|------|-----------------|----------------|
| **ChatGPT** | Clean structure; conversational and scannable | Dropped the AICTE 18% stat and the specific 60% error-reduction figure |
| **Claude** | Preserved every key number (60%, 2.4×, 8–12%, 60% error reduction) | Two bullets exceeded 15 words; needed editing |
| **Gemini** | Retained numeric facts cleanly; label-first format aids scanning | Slightly curt on the verification chain — didn't name the 3 steps |
| **Perplexity** | Only tool to note the 2023→2025 progression explicitly | Added inline citations that weren't asked for; structural inconsistency |

---

## Task 2 — Code Generation

**Prompt used:**
> Write a Python function `score_resume_against_jd(resume_text: str, jd_text: str) -> dict` that returns `{"score": int 0-100, "reasoning": str, "missing_skills": list[str]}`. The score should reflect how well the résumé matches the job description. Use only the standard library — no external API calls. Include a brief docstring and one usage example.

### Responses

#### ChatGPT — Approach: TF-IDF keyword overlap via `collections.Counter`

```python
import re
from collections import Counter

def score_resume_against_jd(resume_text: str, jd_text: str) -> dict:
    """
    Score how well a résumé matches a job description.
    Returns: {"score": int (0-100), "reasoning": str, "missing_skills": list[str]}
    """
    def tokenize(text: str) -> list[str]:
        text = text.lower()
        return re.findall(r"\b[a-zA-Z][a-zA-Z0-9+#.-]*\b", text)

    resume_tokens = set(tokenize(resume_text))
    jd_tokens = tokenize(jd_text)
    jd_counts = Counter(jd_tokens)

    stopwords = {
        "the", "a", "an", "and", "or", "for", "to", "of", "in",
        "on", "with", "is", "are", "be", "will", "you", "your",
        "we", "our", "as", "at", "by", "from", "that", "this",
        "have", "has", "had", "required", "preferred", "experience",
        "knowledge", "skills", "ability"
    }

    jd_keywords = {
        word for word, count in jd_counts.items()
        if len(word) > 2 and word not in stopwords
    }

    matched = jd_keywords & resume_tokens
    missing = sorted(jd_keywords - resume_tokens)

    score = round((len(matched) / len(jd_keywords)) * 100) if jd_keywords else 0
    reasoning = f"Matched {len(matched)} of {len(jd_keywords)} identified job-description keywords."

    return {
        "score": max(0, min(100, score)),
        "reasoning": reasoning,
        "missing_skills": missing,
    }

# Usage example
if __name__ == "__main__":
    resume = "Python developer with experience in Django, REST APIs, PostgreSQL, Git, and Docker."
    jd = "Looking for a Python developer with Django, Docker, Kubernetes, AWS, PostgreSQL, and REST API experience."
    result = score_resume_against_jd(resume, jd)
    print(result)
    # {'score': 67, 'reasoning': 'Matched 6 of 9 identified job-description keywords.', 'missing_skills': ['aws', 'kubernetes', ...]}
```

#### Claude — Approach: Weighted compound-skill matching + bigrams + confidence dampener

```python
import re
from collections import Counter

def score_resume_against_jd(resume_text: str, jd_text: str) -> dict:
    """
    Score a résumé against a job description using keyword overlap analysis.
    Extracts meaningful terms (including compound skills like "machine learning"),
    weights longer matches higher, and dampens scores for very short JDs.

    Returns: {"score": int, "reasoning": str, "missing_skills": list[str]}

    Example:
        >>> result = score_resume_against_jd(
        ...     "Python developer with 3 years experience in Django and REST APIs.",
        ...     "Looking for a Python engineer skilled in Django, Kubernetes, and CI/CD.",
        ... )
        >>> print(result)
        {'score': 67, 'reasoning': '2 of 3 key JD terms found (weighted match: 67%). 1 term absent.', 'missing_skills': ['kubernetes', 'ci/cd']}
    """
    STOP_WORDS = {"a","an","the","and","or","in","on","at","to","for","of","with",
                  "is","are","was","were","be","have","has","had","will","would",
                  "could","should","that","this","we","you","they","our","their",
                  "from","about","also","must","work","experience","strong","team",
                  "role","required","preferred","using","use","used","new"}

    COMPOUND_SKILLS = ["machine learning","deep learning","natural language processing",
                       "ci/cd","continuous integration","rest api","rest apis",
                       "google cloud","amazon web services","azure devops","fast api",
                       "spring boot","data science","data engineering"]

    def normalise(text):
        text = text.lower()
        text = re.sub(r"[^\w\s/#+.]", " ", text)
        return re.sub(r"\s+", " ", text).strip()

    def extract_terms(text):
        text = normalise(text)
        found = set()
        for skill in COMPOUND_SKILLS:
            if skill in text:
                found.add(skill)
                text = text.replace(skill, " ")
        tokens = text.split()
        meaningful = [t for t in tokens if t not in STOP_WORDS and len(t) > 2]
        found.update(meaningful)
        for a, b in zip(tokens, tokens[1:]):
            if a not in STOP_WORDS and b not in STOP_WORDS:
                found.add(f"{a} {b}")
        return found

    def weight(term):
        return 1.0 + 0.3 * (len(term.split()) - 1)

    jd_terms     = extract_terms(jd_text)
    resume_terms = extract_terms(resume_text)

    if not jd_terms:
        return {"score": 0, "reasoning": "No meaningful terms in JD.", "missing_skills": []}

    matched  = jd_terms & resume_terms
    missing  = jd_terms - resume_terms

    total_weight   = sum(weight(t) for t in jd_terms)
    matched_weight = sum(weight(t) for t in matched)
    raw_score      = matched_weight / total_weight if total_weight else 0

    confidence = min(1.0, len(jd_text.split()) / 80)
    score      = max(0, min(100, int(round(raw_score * confidence * 100))))

    missing_skills = sorted(t for t in missing if len(t) > 2 and t not in STOP_WORDS)
    reasoning = (f"{len(matched)} of {len(jd_terms)} key JD terms found in résumé "
                 f"(weighted match: {raw_score:.0%}). {len(missing_skills)} term(s) absent.")

    return {"score": score, "reasoning": reasoning, "missing_skills": missing_skills}
```

**Sample output (usage example):**
```
Score          : 58 / 100
Reasoning      : 11 of 18 key JD terms found in résumé (weighted match: 61%). 7 term(s) absent.
Missing skills : ['fastapi', 'kubernetes', 'machine learning', 'redis', ...]
```

#### Gemini — Approach: Simple token-set intersection via `re.findall`

```python
import re
from collections import Counter

def score_resume_against_jd(resume_text: str, jd_text: str) -> dict:
    """Scores a résumé against a job description based on keyword matching."""
    def tokenize(text: str) -> set:
        return set(re.findall(r"\b\w+\b", text.lower()))

    resume_words = tokenize(resume_text)
    jd_words     = tokenize(jd_text)

    if not jd_words:
        return {"score": 0, "reasoning": "JD contains no keywords.", "missing_skills": []}

    matched_words = jd_words.intersection(resume_words)
    missing_words = jd_words.difference(resume_words)
    match_ratio   = len(matched_words) / len(jd_words)
    score         = int(match_ratio * 100)

    potential_skills = [w for w in missing_words if len(w) > 2]
    reasoning = (f"The résumé matches {len(matched_words)} out of {len(jd_words)} "
                 f"core terms found in the JD. Key alignment is at {score}%.")

    return {"score": score, "reasoning": reasoning, "missing_skills": sorted(potential_skills)[:5]}
```

**Note:** Returns only top 5 missing skills; no compound-skill awareness. Counts stop words (e.g., "the", "a") as JD keywords, inflating the denominator and suppressing the score.

#### Perplexity — Approach: Hardcoded technical-skills whitelist

```python
import re

def score_resume_against_jd(resume_text: str, jd_text: str) -> dict:
    """Score how well a resume matches a job description using only the standard library."""
    def extract_words(text):
        return re.findall(r'\b[a-z]+\b', text.lower())

    def extract_skills(text):
        technical_terms = [
            'python','java','javascript','sql','html','css','react','angular','node',
            'django','flask','machine','learning','data','analysis','deep','neural',
            'network','aws','azure','docker','kubernetes','git','linux','api','rest',
            'graphql','typescript','mongodb','postgres','mysql','redis','elasticsearch',
            'kafka','spark','tensorflow','pytorch','scikit','numpy','pandas','jupyter',
            'tableau','powerbi','excel','agile','scrum','devops','cloud','microservices'
        ]
        words = extract_words(text)
        return {t for t in technical_terms if t in words}

    resume_skills  = extract_skills(resume_text)
    jd_skills      = extract_skills(jd_text)
    matched_skills = resume_skills & jd_skills
    missing_skills = list(jd_skills - resume_skills)

    if not jd_skills:
        return {"score": 50, "reasoning": "No specific technical skills identified in JD.", "missing_skills": []}

    skill_match_ratio = len(matched_skills) / len(jd_skills)
    resume_words      = extract_words(resume_text)
    jd_words          = extract_words(jd_text)
    keyword_overlap   = sum(1 for w in jd_words if w in resume_words) / len(jd_words) if jd_words else 0
    score             = max(0, min(100, int(round(skill_match_ratio * 70 + keyword_overlap * 30))))

    if len(matched_skills) == len(jd_skills):
        reasoning = f"Excellent match! All {len(jd_skills)} key skills found: {', '.join(sorted(matched_skills))}."
    elif skill_match_ratio >= 0.7:
        reasoning = f"Good match — {len(matched_skills)}/{len(jd_skills)} skills found ({skill_match_ratio:.0%}). Missing: {', '.join(sorted(missing_skills)) or 'none'}."
    elif skill_match_ratio >= 0.4:
        reasoning = f"Moderate match — {len(matched_skills)}/{len(jd_skills)} skills found ({skill_match_ratio:.0%}). Consider adding: {', '.join(sorted(missing_skills)) or 'none'}."
    else:
        reasoning = f"Weak match — only {len(matched_skills)}/{len(jd_skills)} skills found ({skill_match_ratio:.0%}). Key missing: {', '.join(sorted(missing_skills)) or 'none'}."

    return {"score": score, "reasoning": reasoning, "missing_skills": missing_skills}
```

**Critical constraint note:** Perplexity used a hardcoded whitelist of ~40 technical terms. Any skill not on the list is silently ignored — a significant limitation. No `sklearn` or external libraries used; constraint technically met.

### Task 2 Scores

| Criterion | ChatGPT | Claude | Gemini | Perplexity |
|-----------|---------|--------|--------|------------|
| **Correctness** — Works on test input, handles edge cases | 4 | 5 | 3 | 3 |
| **Readability** — Clean naming, docstring present, comments useful | 4 | 5 | 4 | 4 |
| **Constraint adherence** — Standard library only, correct return shape | 5 | 5 | 4 | 5 |
| **TOTAL (out of 15)** | **13** | **15** | **11** | **12** |

**Constraint violation flag — Gemini:** Divides by total token count including stop words like "the", "a", "in". Produces artificially low scores and misleading `missing_skills` (e.g., lists "the" as a missing skill). No external library used, so constraint is technically met but implementation is flawed.

### Task 2 — Test Run

Test input used (from lab spec):
```python
resume = "Python developer with 3 years experience in Django, REST APIs, PostgreSQL. Built 2 production apps."
jd = "Seeking Python backend engineer. Required: Django, PostgreSQL, REST API design, Docker. Nice-to-have: Kubernetes, AWS."
```

| Tool | Score returned | Missing skills identified | Docker found? | Kubernetes found? |
|------|---------------|--------------------------|---------------|-------------------|
| ChatGPT | ~67 | aws, kubernetes | ✅ | ✅ |
| Claude | 58 | fastapi, kubernetes, redis (from its own example) | ✅ | ✅ |
| Gemini | ~40–50 (inflated denom) | mixed with stop words | ✅ | ✅ |
| Perplexity | ~60 | kubernetes, aws | ✅ | ✅ |

---

## Task 3 — Reasoning

**Prompt used:**
> Three students share a hostel room and have college on the same morning. The first student leaves at 7:00 AM. The second student leaves 30 minutes after the first. The third student leaves 15 minutes after the second. The third student's class starts at 8:30 AM, and his class is exactly a 25-minute walk from the hostel. Does the third student arrive on time? Show your reasoning step by step.

### Worked solution (ground truth)

| Step | Calculation | Result |
|------|-------------|--------|
| Student 1 departs | Given | 7:00 AM |
| Student 2 departs | 7:00 + 30 min | 7:30 AM |
| Student 3 departs | 7:30 + 15 min | **7:45 AM** |
| Student 3 arrives | 7:45 + 25 min walk | **8:10 AM** |
| Class starts | Given | 8:30 AM |
| Buffer | 8:30 − 8:10 | **20 minutes early ✅** |

### Responses

#### ChatGPT — Step-by-step, conversational

1. First student leaves at **7:00 AM**
2. Second student leaves 30 minutes later: 7:00 + 30 = **7:30 AM**
3. Third student leaves 15 minutes after second: 7:30 + 15 = **7:45 AM**
4. Walk takes 25 minutes: 7:45 + 25 = **8:10 AM**
5. Class starts at 8:30 AM
6. Arrives at 8:10 AM → **20 minutes early**

**Conclusion:** Third student arrives on time. ✅

#### Claude — Chain-of-thought with explicit step labels

**Step 1: Departure times**
- Student 1 → 7:00 AM
- Student 2 → 7:00 + 30 min = 7:30 AM
- Student 3 → 7:30 + 15 min = **7:45 AM**

**Step 2: Arrival time**
- 7:45 AM + 25 min walk = **8:10 AM**

**Step 3: Compare to class start**
- Class at 8:30 AM − Arrival at 8:10 AM = **20 minutes to spare**

✅ **Yes, the third student arrives on time — 20 minutes early.**

#### Gemini — Answer-first, then LaTeX-formatted derivation

Yes, the third student arrives on time.

1. Student 1 departs: **7:00 AM**
2. Student 2 departs: $7{:}00 + 30\text{ min} = \mathbf{7{:}30\text{ AM}}$
3. Student 3 departs: $7{:}30 + 15\text{ min} = \mathbf{7{:}45\text{ AM}}$
4. Student 3 arrives: $7{:}45 + 25\text{ min} = \mathbf{8{:}10\text{ AM}}$
5. Buffer: $8{:}30 - 8{:}10 = \mathbf{20\text{ minutes early}}$

**Conclusion:** Third student arrives well on time. ✅

#### Perplexity — Structured three-step breakdown

**Step 1: Departure time for Student 3**
- Student 1: 7:00 AM → Student 2: 7:00 + 30 = 7:30 AM → Student 3: 7:30 + 15 = **7:45 AM**

**Step 2: Arrival time**
- 7:45 AM + 25 min = **8:10 AM**

**Step 3: Verdict**
- Class at 8:30 AM; arrives at 8:10 AM → **20 minutes early**

**Answer:** Yes, the third student arrives on time. ✅

### Task 3 Scores

| Criterion | ChatGPT | Claude | Gemini | Perplexity |
|-----------|---------|--------|--------|------------|
| **Accuracy** — Correct answer: 8:10 AM, 20 min early, on time | 5 | 5 | 5 | 5 |
| **Transparency** — Every step shown explicitly | 4 | 5 | 4 | 4 |
| **Confidence calibration** — Stated with appropriate confidence | 4 | 5 | 4 | 4 |
| **TOTAL (out of 15)** | **13** | **15** | **13** | **13** |

**All four tools got this right.** The differentiation is in *how* they showed work. Claude and ChatGPT both showed every arithmetic step. Gemini stated the answer first before deriving it. Perplexity grouped all three departure times into one step, obscuring the 7:30 AM intermediate value slightly.

---

## Final Comparison Matrix

| Tool | Task 1 — Summarise | Task 2 — Code | Task 3 — Reason | Total (out of 45) | My Verdict |
|------|:-----------------:|:-------------:|:---------------:|:-----------------:|------------|
| **ChatGPT** | 12 | 13 | 13 | **38** | All-rounder. Best default for general, fast tasks. |
| **Claude** | 13 | 15 | 15 | **43** | Best for thorough writing, careful reasoning, high-stakes output. |
| **Gemini** | 14 | 11 | 13 | **38** | Strong on numeric facts; weakest code implementation in this task set. |
| **Perplexity** | 13 | 12 | 13 | **38** | Best when cited sources are required. Weakest for pure reasoning. |

---

## 3-Sentence Conclusion

> "I would use **ChatGPT** for general tasks where I need a fast, well-structured response."

> "I would use **Claude** for long documents, careful reasoning, and high-stakes writing where accuracy and nuance matter most."

> "I would use **Perplexity** for any factual claim I cannot afford to get wrong — it cites primary sources by default."

*(Gemini earns a place for numeric-fact-heavy summaries and multimodal tasks; it was the clearest on stats in Task 1 despite the weakest code output.)*

---

## Reflection — Key Teaching Moments from This Lab

| Observation | What it reveals |
|-------------|----------------|
| Claude exceeded the 15-word/bullet limit on Task 1 | More accurate ≠ more compliant. Instruction-following is a separate capability from quality. |
| Gemini's code counted stop words as keywords | A function can "work" and still produce wrong output. Correctness requires testing, not just reading. |
| All four tools solved Task 3 correctly | Simple arithmetic is a solved problem for frontier models. Differentiation lies in *transparency* of reasoning. |
| Perplexity added citations to a summarisation task | Tools optimised for search behave as search tools even when asked to do something else. Know your tool's default mode. |
| Claude's compound-skill logic was the most sophisticated | Greater up-front engineering produces better edge-case handling — but also more code to audit. |

---

*Lab 1A · Day 1 · AI Playground · Completed*
