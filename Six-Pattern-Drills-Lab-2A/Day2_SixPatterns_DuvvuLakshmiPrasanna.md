# Day 2 – Six Pattern Drills

**Name:** Duvvu Lakshmi Prasanna
**Date:** 10-06-2026
**Batch:** OWL Coder

---

## Pattern 1 – Persona

**Prompt:**
> You are a senior placement coach at Aditya University. You have prepared 200 B.Tech CSE students for TCS, Infosys, and Cognizant placement interviews. A 3rd-year CSE student with 7.5 CGPA asks you about Big-O notation. Explain it the way you would in a 1-on-1 prep session — concrete, conversational, exam-relevant.

---

### ChatGPT Output

Sure. In placements, Big-O is one of those topics where companies don't expect you to be a researcher — they expect you to think logically about efficiency.

Let's do this like we're sitting in a prep session before a TCS Digital or Infosys interview.

**First: Why Big-O Exists**

Suppose I give you two programs:
- Program A sorts 1 lakh numbers in 2 seconds
- Program B sorts them in 20 seconds

Interviewer asks: "Which algorithm is better?"

You cannot answer just by timing because: different laptops, different CPUs, different programming languages. So we measure **how fast the algorithm grows as input grows**. That measurement is called **Time Complexity**. Big-O notation is the language used to express it.

**Most Important Complexities for Placements**

| Complexity | Name | Example |
|------------|------|---------|
| O(1) | Constant | Access array index |
| O(log n) | Logarithmic | Binary Search |
| O(n) | Linear | Single loop |
| O(n log n) | Linearithmic | Merge Sort |
| O(n²) | Quadratic | Nested loops |
| O(2ⁿ) | Exponential | Recursive subsets |
| O(n!) | Factorial | Traveling salesman brute force |

**Important Interview Trick** — Big-O ignores constants and lower-order terms. Example: `n² + n + 5` → Big-O = O(n²). Because for very large n, n² dominates everything.

**Final Placement Advice** — For your CGPA range (7.5), strong basics can easily help you clear coding discussions. Focus on: Big-O, Arrays, Strings, Sorting, Binary Search, Recursion basics, Hashing.

---

### Claude Output

Good, now let's break this down the way I'd explain it sitting across from you before your TCS/Infosys drive.

**What is Big-O? The one-line answer:**
Big-O tells you how your code behaves as input gets bigger. It's not about milliseconds. It's about *growth rate*.

Think of it this way — TCS gives you an array of 10 elements today. Tomorrow their system has 10 million. Will your code still work, or will it time out? That's what Big-O answers.

**The 5 complexities you MUST know:**

| Complexity | Name | Example |
|------------|------|---------|
| O(1) | Constant | Array index access — always instant |
| O(log n) | Logarithmic | Binary search — ~20 comparisons for 1M elements |
| O(n) | Linear | Single loop — one pass through data |
| O(n log n) | Linearithmic | Merge Sort, Quick Sort — best possible for sorting |
| O(n²) | Quadratic | Nested loops — gets you rejected |

**The ATM analogy (used every session):**

| Operation | What it does | Big-O |
|-----------|-------------|-------|
| Card number → instant lookup | Hash map | O(1) |
| Search alphabetically by name | Binary search | O(log n) |
| Send SMS to every customer | One loop | O(n) |
| Sort all transactions | Merge sort | O(n log n) |
| Compare every pair of accounts | Nested loop | O(n²) |

**The one rule that separates average from good answers:**
Always mention both time AND space complexity. Most students only talk about time. Saying "this is O(n) time and O(1) space" immediately makes you stand out.

---

### Comparison – Pattern 1 (Persona)

| Aspect | ChatGPT | Claude |
|--------|---------|--------|
| Tone | Conversational, coaching style | Conversational, more concise |
| Depth | Very detailed — 7 complexities, code per complexity, space complexity | Focused — 5 core complexities, ATM analogy, key interview tip |
| Placement-relevance | High — mentions CGPA, TCS Ninja/Digital, 7 topics to cover | High — TCS/Infosys context, time + space tip |
| Analogy quality | Class roll number analogy | ATM analogy (more memorable) |
| Best for student | Better as a study guide (comprehensive) | Better as interview cheat-sheet (focused) |

**Winner:** Claude for exam-day recall; ChatGPT for deep study sessions.

**Self Score — ChatGPT: 4/5 | Claude: 5/5**

---

## Pattern 2 – Few-Shot

**Prompt:**
> Here are example explanations from a placement coach:
>
> Q: What is recursion?
> A: A function calling itself with a smaller problem. Like Russian dolls — open one, find a smaller one inside. Stops at base case. Example: factorial.
>
> Q: What is a stack?
> A: LIFO data structure. Push to add, pop to remove. Like a stack of plates — you take from the top.
>
> Q: What is Big-O notation?
> A:

---

### ChatGPT Output

Q: What is Big-O notation?
A: Big-O notation measures how an algorithm's running time or memory usage grows as the input size increases. It focuses on growth, not exact seconds. Think of it like estimating travel time: Walking 1 km takes about twice as long as walking 0.5 km → O(n). Checking a phone contact using search halves the options repeatedly → O(log n). Common examples: O(1) → Access an array element; O(n) → Traverse an array once; O(n²) → Nested loops; O(log n) → Binary Search. In interviews, Big-O helps compare algorithms and identify which solution scales better for large inputs.

---

### Claude Output

O(1) constant, O(n) linear, O(n²) quadratic. Like a library — O(1) is knowing exactly which shelf, O(n) is checking every book, O(n²) is comparing every book with every other book.

---

### Comparison – Pattern 2 (Few-Shot)

| Aspect | ChatGPT | Claude |
|--------|---------|--------|
| Format matching | Partially followed — much longer than examples | Perfectly matched — short, analogy-driven |
| Analogy | Travel time analogy (decent) | Library shelf analogy (crisp and memorable) |
| Code example | None | None |
| Placement-relevance | Mentions interview at the end | Implicit only |
| Pattern fidelity | Did not copy the compact Q&A format | Nailed the format exactly |

**Winner:** Claude — followed the few-shot format precisely. ChatGPT broke the pattern by adding too much context.

**Self Score — ChatGPT: 3/5 | Claude: 3/5**
*(Both lacked a concrete code example; format-following is the key metric here.)*

---

## Pattern 3 – Chain-of-Thought

**Prompt:**
> Explain Big-O notation to a placement interview candidate. Think step by step before answering.
> Step 1: define Big-O in one sentence.
> Step 2: give one concrete example with code.
> Step 3: explain why interviewers ask about it.
> Step 4: synthesise into a 3-sentence summary.

---

### ChatGPT Output

**Step 1: Define Big-O in one sentence**
Big-O notation describes how the time or space required by an algorithm grows as the input size (n) increases.

**Step 2: One concrete example with code**
```cpp
for (int i = 0; i < n; i++) {
    cout << arr[i];
}
```
This loop visits every element once. If n = 10, it runs about 10 times. If n = 1000, it runs about 1000 times. The work grows directly with n, so the time complexity is: O(n).

**Step 3: Why interviewers ask about it**
Interviewers ask about Big-O because they want to know whether you can evaluate the efficiency of your solution. Two programs may produce the same output, but the better engineer chooses the one that scales well when the input becomes very large.

**Step 4: Three-sentence summary**
Big-O notation measures how an algorithm's resource usage grows as the input size increases. For example, a single loop through an array has O(n) time complexity because the number of operations grows linearly with the input size. Interviewers ask about Big-O to check whether you can write solutions that remain efficient for large datasets.

---

### Claude Output

**Step 1:** Big-O describes how your algorithm's runtime grows as input size grows — not the exact time, just the shape of the growth.

**Step 2:**
```cpp
for (int i = 0; i < n; i++)
    cout << arr[i];
```
Double the input, double the work. That's O(n) — linear growth.

**Step 3:** Interviewers ask because two solutions can give the same correct output, but one dies on large inputs. They want to know you'll write code that scales.

**Step 4:** Big-O measures how an algorithm's resource usage grows with input size. A single loop is O(n) because work grows linearly with n. Interviewers test this to confirm you can choose solutions that stay efficient when data gets large.

---

### Comparison – Pattern 3 (Chain-of-Thought)

| Aspect | ChatGPT | Claude |
|--------|---------|--------|
| Step structure | All 4 steps clearly labelled | All 4 steps clearly labelled |
| Definition quality | Formal and precise | Casual — "shape of growth" adds intuition |
| Code example | More verbose (line-by-line explanation) | More concise ("double the input, double the work") |
| Interviewer reasoning | Formal but good | More direct and punchy |
| Summary quality | Equally strong | Equally strong |

**Winner:** Tie — both followed CoT format correctly. Claude's language is slightly more student-friendly.

**Self Score — ChatGPT: 5/5 | Claude: 5/5**

---

## Pattern 4 – Structured Output

**Prompt:**
> Explain Big-O notation for a placement interview.
> Return ONLY valid JSON with this exact shape — no markdown fences, no commentary:
> {
>   "definition": "one-sentence definition",
>   "intuition": "concrete analogy",
>   "code_example": "Python snippet showing O(n) and O(n²)",
>   "common_pitfall": "what students get wrong",
>   "interview_test_question": "a follow-up question an interviewer might ask"
> }

---

### ChatGPT Output

```json
{
  "definition": "Big-O notation describes how the running time or memory usage of an algorithm grows as the input size increases.",
  "intuition": "Think of checking names in a class list: reading every name once grows linearly with class size (O(n)), while comparing every student with every other student grows much faster (O(n²)).",
  "code_example": "# O(n)\nfor i in range(n):\n print(i)\n\n# O(n^2)\nfor i in range(n):\n for j in range(n):\n print(i, j)",
  "common_pitfall": "Students often count exact operations and constants; Big-O focuses on the growth rate for large inputs, so O(2n) simplifies to O(n).",
  "interview_test_question": "Why is Binary Search O(log n), and what condition must be true for Binary Search to work?"
}
```

---

### Claude Output

```json
{
  "definition": "Big-O notation describes how an algorithm's runtime or memory usage grows as the input size n increases.",
  "intuition": "Like a library search — O(1) is knowing the exact shelf, O(n) is checking every book one by one, O(n²) is comparing every book with every other book.",
  "code_example": "# O(n) — one loop\nfor i in range(n):\n    print(arr[i])\n\n# O(n²) — loop inside a loop\nfor i in range(n):\n    for j in range(n):\n        print(arr[i], arr[j])",
  "common_pitfall": "Students confuse O(2n) with O(n²) — constants are dropped in Big-O, so O(2n) is still O(n), but two nested loops give O(n²), which is fundamentally different.",
  "interview_test_question": "If I give you an unsorted array and ask you to find whether two numbers sum to a target value, what is the time complexity of your brute-force solution and how would you optimise it?"
}
```

**Note:** Both ChatGPT and Claude added ```json fences despite being asked not to. This is a known behaviour — to be fixed in Day 2 Lab 2B with response_schema + Pydantic validation.

---

### Comparison – Pattern 4 (Structured Output)

| Aspect | ChatGPT | Claude |
|--------|---------|--------|
| JSON fences added? | Yes (violated prompt constraint) | Yes (violated prompt constraint) |
| Definition | Clear and complete | Nearly identical, slightly more formal |
| Analogy | Class list analogy | Library shelf analogy (consistent across patterns) |
| Code example | Uses print(i) — less realistic | Uses print(arr[i]) — array-context more realistic |
| Common pitfall | O(2n) simplification — good | Same + explains why nested loops differ — better |
| Interview question | Binary Search condition — standard | Unsorted array + optimise — more realistic interview format |

**Winner:** Claude — better pitfall explanation and more realistic interview question.

**Self Score — ChatGPT: 4/5 | Claude: 4/5**
*(Both violated the "no markdown fences" constraint.)*

---

## Pattern 5 – System Prompt

**System Prompt (Custom Instructions):**
> You are a senior placement coach for B.Tech CSE students at an Indian engineering college. You prepare students for TCS / Infosys / Cognizant interviews. You explain technical concepts in 50-80 words max, conversationally, with one concrete code example.

**User Prompt:**
> Explain Big-O notation.

---

### ChatGPT Output

Big-O notation tells us how an algorithm's running time grows as the input size (n) increases. Interviewers use it to check whether you can judge solution efficiency.

Example:
```cpp
for(int i = 0; i < n; i++) {
    cout << arr[i];
}
```
This loop runs n times, so its time complexity is O(n). A single loop is usually O(n), while nested loops are often O(n²). In placements, you should be able to identify such complexities quickly.

---

### Claude Output

Big-O tells you how your code behaves when input gets large. One loop over n elements? O(n). Nested loops? O(n²) — avoid this in interviews.

```python
for i in range(n):        # O(n) — acceptable
    for j in range(n):    # O(n²) — red flag
```

In your TCS interview, don't just write correct code — always say "this runs in O(n) time." That one line separates you from 80% of candidates.

---

### Comparison – Pattern 5 (System Prompt)

| Aspect | ChatGPT | Claude |
|--------|---------|--------|
| Word count | ~75 words | ~60 words |
| Followed 50-80 word limit? | Yes | Yes |
| Code language | C++ | Python |
| Domain-aware? | Mentions placement context at end | Weaves TCS reference directly into tip |
| Most impactful line | "identify such complexities quickly" | "That one line separates you from 80% of candidates" — much stronger |
| Shorter than Pattern 1? | Yes — system prompt working correctly | Yes — system prompt working correctly |

**Winner:** Claude — closing line is significantly more motivating and placement-specific.

**Self Score — ChatGPT: 4/5 | Claude: 5/5**

---

## Pattern 6 – Prompt Chaining

### Chat 1 — Extract

**Prompt:**
> List the 5 most important sub-concepts a B.Tech student must understand about Big-O notation. Just the list, no explanation.

**ChatGPT Output:**
1. Time Complexity
2. Space Complexity
3. Best, Average, and Worst Case Analysis
4. Common Complexity Classes (O(1), O(log n), O(n), O(n log n), O(n²))
5. Calculating Complexity from Loops and Recursion

**Claude Output:**
1. Time complexity vs space complexity
2. Best / average / worst case
3. Drop constants and lower-order terms
4. Common complexities ranked: O(1) < O(log n) < O(n) < O(n log n) < O(n²)
5. How to read nested loops and recursive calls

---

### Chat 2 — Expand

**Prompt:**
> For each of these 5 sub-concepts of Big-O notation, write a 1-paragraph explanation tailored to a 3rd-year B.Tech CSE student preparing for placement interviews:
> [list from Chat 1 pasted here]

**ChatGPT Output:**

1. **Time Complexity** — Time Complexity measures how the number of operations performed by an algorithm grows as the input size (n) increases. It does not measure actual time in seconds; instead, it describes the growth rate of the algorithm. For example, traversing an array once requires visiting every element, so the complexity is O(n). In placement interviews, you are often asked to identify the time complexity of loops, searching algorithms, and sorting algorithms.

2. **Space Complexity** — Space Complexity measures how much extra memory an algorithm uses as the input size grows. This includes temporary arrays, recursion stacks, and auxiliary data structures. For example, creating an additional array of size n requires O(n) extra space, while using only a few variables requires O(1) space. Interviewers ask about space complexity because an efficient solution should use memory wisely, especially when handling large datasets.

3. **Best, Average, and Worst Case Analysis** — An algorithm can behave differently depending on the input. The best case is the minimum work required, the worst case is the maximum work required, and the average case is the expected work over typical inputs. For example, in Linear Search, finding the target at the first position is O(1), while finding it at the last position is O(n). In interviews, Big-O usually refers to the worst-case complexity unless specified otherwise.

4. **Common Complexity Classes** — These complexity classes help compare algorithms based on scalability. O(1) is constant time, O(log n) appears in Binary Search, O(n) is common in array traversal, O(n log n) is seen in efficient sorting algorithms like Merge Sort, and O(n²) often comes from nested loops. Placement interviews frequently test whether you can recognize these patterns and determine which algorithm is more efficient for large inputs.

5. **Calculating Complexity from Loops and Recursion** — A major interview skill is determining complexity directly from code. A single loop running n times is usually O(n), while two nested loops often result in O(n²). If a loop repeatedly halves the input size, the complexity is typically O(log n). For recursive functions, complexity depends on the number of recursive calls and the work done in each call. Interviewers often provide a code snippet and ask you to calculate its complexity without executing it, making this one of the most important Big-O skills to master.

---

**Claude Output:**

1. **Time Complexity** — Time complexity measures how the number of operations grows as input size n increases — not actual seconds, just the growth pattern. One loop over an array = O(n). Two nested loops = O(n²). In your TCS or Infosys interview, every time you write code, the interviewer expects you to say "this is O(n)" without being asked. That habit alone puts you ahead.

2. **Space Complexity** — Space complexity measures how much extra memory your code uses as input grows. Creating a new array of size n costs O(n) space. Using just a few variables costs O(1). In placements, interviewers often ask "can you do this in O(1) space?" — that's their way of checking if you can solve it without creating extra data structures. Always mention both time and space in your answer.

3. **Best, Average, and Worst Case** — The same algorithm can behave differently on different inputs. Linear search finds the element at index 0 in O(1) best case, but scans all n elements in O(n) worst case. In interviews, when someone says "what is the time complexity?", they almost always mean worst case — unless they specifically say otherwise. Never assume best case and call it done.

4. **Common Complexity Classes** — Memorise this order cold: O(1) < O(log n) < O(n) < O(n log n) < O(n²). Hash map lookup is O(1). Binary search is O(log n). Merge sort is O(n log n) — the best you can do for comparison-based sorting. Bubble sort is O(n²) — never suggest it for large inputs in an interview. When asked to compare two solutions, rank them using this order.

5. **Calculating Complexity from Code** — This is the skill interviewers test most directly — they show you a snippet and ask "what is the complexity?" One loop = O(n). Loop inside a loop = O(n²). Loop that halves the input each iteration = O(log n). For recursion, ask yourself: how many times does the function call itself, and what work happens each time? Practice reading code and stating complexity out loud — because in a real interview, you need to answer in under 30 seconds.

---

### Chat 3 — Polish

**Prompt:**
> Synthesise these 5 paragraphs into ONE concise 80-word interview-prep explanation of Big-O notation. Preserve all 5 sub-concepts. Conversational tone. End with one practice question.
> [5 paragraphs pasted here]

**ChatGPT Output:**

Big-O notation helps you measure an algorithm's efficiency by analyzing both time complexity (operations performed) and space complexity (extra memory used) as input size grows. You should understand best, average, and worst-case analysis, though interviews usually focus on the worst case. Common complexity classes include O(1), O(log n), O(n), O(n log n), and O(n²). A key interview skill is calculating complexity from loops and recursion by recognizing common patterns.

*Practice Question:* What is the time complexity of a nested loop where both loops run from 0 to n?

---

**Claude Output:**

Big-O measures how your algorithm's time and memory grow as input size increases — not actual seconds, just the growth pattern. Always assume worst case unless told otherwise. Memorise the order: O(1) < O(log n) < O(n) < O(n log n) < O(n²). One loop is O(n), nested loops are O(n²), halving each step is O(log n). Always state both time and space complexity in interviews — most candidates only mention one.

*Practice question:* Given this code, what is the time and space complexity — and how would you optimise it?
```python
def find_duplicates(arr):
    result = []
    for i in range(len(arr)):
        for j in range(i+1, len(arr)):
            if arr[i] == arr[j]:
                result.append(arr[i])
    return result
```

---

### Comparison – Pattern 6 (Prompt Chaining)

| Aspect | ChatGPT | Claude |
|--------|---------|--------|
| Chat 1 list quality | Broad topic labels | More specific and actionable (e.g., "drop constants") |
| Chat 2 paragraph depth | Academic and thorough | Student-facing and practical — uses interview commands |
| Chat 3 synthesis | Covers all 5 sub-concepts, clean | Covers all 5 + code-based practice question |
| Practice question quality | Trivial — answer is simply O(n²) | Requires analysis + optimisation — much more realistic |
| Demonstrates chaining benefit? | Yes | Yes — each stage built better context |

**Winner:** Claude — Chat 1 produced more actionable sub-concepts, which made Chat 2 more practical, and Chat 3 stronger.

**Self Score — ChatGPT: 4/5 | Claude: 5/5**

---

## Self Score Summary

| Pattern | ChatGPT /5 | Claude /5 |
|---------|-----------|----------|
| 1 – Persona | 4 | 5 |
| 2 – Few-Shot | 3 | 3 |
| 3 – Chain-of-Thought | 5 | 5 |
| 4 – Structured Output | 4 | 4 |
| 5 – System Prompt | 4 | 5 |
| 6 – Prompt Chaining | 4 | 5 |
| **Total** | **24/30** | **27/30** |

---

## Peer Score Summary

| Pattern | Clarity /2 | Context /2 | Specificity /2 | Format /2 | Verification /2 | Total /10 |
|---------|-----------|-----------|---------------|----------|----------------|----------|
| 1 – Persona | /2 | /2 | /2 | /2 | /2 | /10 |
| 2 – Few-Shot | /2 | /2 | /2 | /2 | /2 | /10 |
| 3 – Chain-of-Thought | /2 | /2 | /2 | /2 | /2 | /10 |
| 4 – Structured Output | /2 | /2 | /2 | /2 | /2 | /10 |
| 5 – System Prompt | /2 | /2 | /2 | /2 | /2 | /10 |
| 6 – Prompt Chaining | /2 | /2 | /2 | /2 | /2 | /10 |

*(To be completed by peer reviewer)*

---

## Overall Tool Comparison

| Dimension | ChatGPT | Claude |
|-----------|---------|--------|
| Format following | Broke few-shot format; added JSON fences | Nailed few-shot format; also added JSON fences |
| Depth vs conciseness | Tends toward comprehensive | Tends toward focused and punchy |
| Placement-specific language | Good — mentions TCS Ninja/Digital, CGPA | Better — weaves interview commands throughout |
| Analogy consistency | Varies per pattern | Consistent library/ATM analogy across patterns |
| Best use case | Deep study material, reference notes | Exam-day prep, quick recall, interview practice |

---

## Reflection

For my placement-prep students, the patterns I will use most are **Persona** and **Prompt Chaining**, because Persona gives the model a deeply specific role that produces placement-relevant tone and context without extra instructions in every message, while Prompt Chaining consistently delivers higher-quality explanations by breaking a complex topic into focused stages — extract, expand, polish — where each step builds meaningfully on the last. No single prompt produced an output as complete and student-ready as the three-step chain did for Pattern 6.


