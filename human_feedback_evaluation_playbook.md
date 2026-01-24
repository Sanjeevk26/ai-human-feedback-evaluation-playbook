# Reinforcement Learning from Human Feedback (RLHF)  
## Evaluation & Preference Ranking – Personal Learning Guide

This document contains **generic guidelines** for understanding how humans evaluate AI responses during RLHF-style workflows.

These notes are written purely for **learning and skill-building**.  
They do **not** reference any organization, proprietary system, or internal process.

---

## What RLHF Evaluation Is (Plain English)

RLHF evaluation answers one simple question:

> *“Which AI response would a normal human prefer, and why?”*

Humans compare AI outputs, judge their quality, and record preferences.  
These preferences later help models learn what *humans actually like*, not just what is technically correct.

---

## Two Core Evaluation Activities

### 1️⃣ Query Vetting (Before Evaluation)

Before comparing AI answers, the **prompt itself** must be good.

Ask yourself:
- Is the question clear?
- Would two AI answers realistically differ?
- Can a human judge which answer is better?

### Example
❌ Bad prompt:  
“What is 2 + 2?”

✅ Better prompt:  
“Explain why 2 + 2 equals 4 using a real-life example for a child.”

Good prompts create **learning signal**.  
Bad prompts create **noise**.

---

### 2️⃣ Side-by-Side Comparison (Main Evaluation)

Two AI responses are shown for the **same prompt**.

Your job:
- Read both carefully
- Judge them independently using rubrics
- Decide which one you prefer overall (or if they’re equal)
- Explain your reasoning clearly

---

## The Evaluator Mindset (Very Important)

You are:
- ❌ Not grading like an exam
- ❌ Not checking grammar only
- ❌ Not rewarding confidence

You *are*:
- ✅ Thinking like a real user
- ✅ Checking usefulness, clarity, correctness, and trust
- ✅ Asking “Would I be happy with this answer?”

---

# Evaluation Rubrics (Generic & Reusable)

Each response is evaluated **individually**, then compared.

---

## 1️⃣ Instruction Following

**Meaning:**  
Did the response actually do what the user asked?

### Good
- Follows all instructions clearly

### Minor issue
- Main task done, small detail missed

### Major issue
- Misunderstands or ignores the main request

### Example
User: “List 3 advantages”
- Lists 2 → major issue

---

## 2️⃣ Relevance & Focus

**Meaning:**  
Is the response on-topic and useful, or filled with unnecessary content?

### Example
User: “Capital of France”
- Correct answer + long history lesson → possibly too much

Key idea:
> Helpful > verbose

---

## 3️⃣ Completeness

**Meaning:**  
Does the response fully satisfy the user’s goal?

### Example
User: “Compare A and B”
- Explains only A → incomplete

---

## 4️⃣ Context Usage (If reference material exists)

**Meaning:**  
Did the response correctly use the provided information?

### Example
If a document says:
“Price = 10,000”

Response says:
“Price = 15,000”

→ major issue (even if tone is great)

---

## 5️⃣ Collaborativity

**Meaning:**  
Did the response behave like a helpful assistant *when clarification was needed*?

### Example
User: “Book a hotel for me”
Good response:
- Asks city, dates, budget

Bad response:
- Randomly picks a hotel

---

## 6️⃣ Grounded Accuracy

**Meaning:**  
Are claims based on provided material accurate?

This applies **only when reference material is given**.

Wrong use of reference = loss of trust.

---

## 7️⃣ General Truthfulness

**Meaning:**  
Are factual claims correct based on common knowledge?

### Example
Saying a non-existent product exists → major issue

---

## 8️⃣ Links (If present)

**Meaning:**  
Do links actually help the user?

Bad links:
- Broken
- Misleading
- Irrelevant

---

## 9️⃣ Overall Quality (Human Judgment)

Final gut check:

> “If I were the user, how satisfied would I be?”

Ratings typically range from:
- Excellent
- Good with small issues
- Acceptable
- Poor
- Very poor

---

# Preference Ranking (Choosing Between Two Responses)

After scoring both responses:

- Pick the one you **prefer overall**
- Or say they’re **about the same**

### Important Rule
A response can be:
- Factually correct but unhelpful
- Helpful but factually wrong

**Wrong core facts usually outweigh everything else.**

---

## How to Write a Good Preference Explanation

A strong explanation:
- Mentions **specific differences**
- Explains **why they matter**
- Sounds natural, not robotic

### Example
“I preferred Response A because it directly answers the question and stays focused. Response B adds extra information that wasn’t asked for and contains a factual error, which reduces trust.”

---

## Accuracy Severity (Simple Mental Model)

Not all mistakes are equal.

### High severity
- Wrong facts that affect decisions
- Medical, legal, financial misinformation
- Confident but false statements

### Low severity
- Minor wording issues
- Slight rounding differences
- Non-essential detail errors

Ask:
> *“Could this mislead a user in a meaningful way?”*

---

## Common Evaluation Pitfalls

- Rewarding confidence instead of correctness
- Ignoring missing parts of a question
- Accepting vague answers as “good enough”
- Forgetting the original user intent

---

## Final Mental Checklist (Memorable)

Before submitting:
1. Did it answer the question?
2. Is anything clearly wrong?
3. Is something important missing?
4. Would I trust this?
5. Which answer would I personally want?

If you can answer these, you’re doing RLHF evaluation correctly.

---

## Closing Thought

Good human feedback:
- Makes evaluation easy
- Makes models better
- Reflects real user needs

Clarity, usefulness, and truth matter more than style.

---

End of learning notes.
