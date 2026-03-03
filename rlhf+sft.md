# Model Response Evaluation Playbook (ICON REAL)

This document provides a generic, practical framework for evaluating AI model responses in RLHF-style workflows. It defines what “good” looks like, how to score quality, and how to write professional Strengths, Areas of Improvement, and Preference Ranking rationales.

This is an educational, generic guide and does not reference any company or proprietary project.

---

## 1. How to Evaluate a Model Response

A strong response is “ICON REAL.” Use the table below as a quick mental checklist.

| Letter | Metric | Meaning | Question to ask |
|---|---|---|---|
| I | Intent | Understanding user intent | Does it understand what the user is asking? |
| C | Complete | Completeness | Does it answer all parts of the request? |
| O | On-truth | Factual accuracy | Are the factual claims correct and verifiable? |
| N | No contradictions | Logical consistency | Does the response remain internally consistent and make sense? |
| R | Relevant | Relevance | Is everything included directly related to the user’s goal? |
| E | Efficient | Avoid repetition | Is it concise without repeating itself or adding fluff? |
| A | Articulate | Grammar and formatting | Is it clearly written and easy to scan? |
| L | Length right | Appropriate length | Is the response the right length for the question? |

---

## 1.1 Deep Dive With Examples (Good vs Minor vs Substantial)

Use the examples below to distinguish between small issues and major failures.

### 1) Instruction Following

#### 1A. Intent (Understanding user intent)
Key question: Does it answer what the user is actually asking?

- Good response  
  User: “Who wrote Pride and Prejudice?”  
  Model: “Jane Austen wrote Pride and Prejudice.”  
  Why: Directly answers the question.

- Minor error  
  User: “Who wrote Pride and Prejudice?”  
  Model: “Jane Austen wrote it in 1813.”  
  Why: Answers correctly but adds unnecessary detail.

- Substantial error  
  User: “Who wrote Pride and Prejudice?”  
  Model: “It’s a novel about romance and class.”  
  Why: Does not answer the question.

#### 1B. Complete (Covers all parts)
Key question: Does it cover all parts of the request?

- Good response  
  User: “Name the capital of France and Germany.”  
  Model: “Paris and Berlin.”  
  Why: Answers both parts.

- Minor error  
  User: “Name the capital of France and Germany.”  
  Model: “Paris.”  
  Why: Answers only one part.

- Substantial error  
  User: “Name the capital of France and Germany.”  
  Model: “France is in Europe.”  
  Why: Does not answer the request.

---

### 2) Truthfulness

#### 2A. On-truth (Factual accuracy and credibility)
Key question: Are all facts stated correct, and are citations (if present) credible?

- Good response  
  User: “When is Boxing Day?”  
  Model: “December 26.”  
  Why: Factually correct.

- Minor error  
  User: “When is Boxing Day?”  
  Model: “December 25.”  
  Why: A small but meaningful factual error.

- Substantial error  
  User: “When is Boxing Day?”  
  Model: “January 1.”  
  Why: Clearly incorrect.

#### 2B. No contradictions (Logical consistency)
Key question: Does the response avoid contradicting itself?

- Good response  
  User: “Should people tell the truth?”  
  Model: “Generally yes, because honesty builds trust.”  
  Why: Consistent reasoning.

- Minor error  
  User: “Should people tell the truth?”  
  Model: “Usually yes, but sometimes it depends.”  
  Why: Vague, but not contradictory.

- Substantial error  
  User: “Should people tell the truth?”  
  Model: “People should always tell the truth, but lying is usually better.”  
  Why: Direct contradiction.

---

### 3) Coherence

#### 3A. Relevant (Stays on topic)
Key question: Is the response relevant to the user’s query?

- Good response  
  User: “What year did the American Revolutionary War start?”  
  Model: “1775.”  
  Why: Fully relevant.

- Minor error  
  User: “What year did the American Revolutionary War start?”  
  Model: “1775. George Washington later became president.”  
  Why: Slightly off-topic extra detail.

- Substantial error  
  User: “What year did the American Revolutionary War start?”  
  Model: “1775. I love history and war stories.”  
  Why: Irrelevant personal commentary.

#### 3B. Efficient (No repetition)
Key question: Does it avoid repeating itself?

- Good response  
  User: “Name one fruit.”  
  Model: “Apple.”  
  Why: Clear and concise.

- Minor error  
  User: “Name one fruit.”  
  Model: “Apple. Apples are fruits.”  
  Why: Slight repetition.

- Substantial error  
  User: “Name one fruit.”  
  Model: “Apple. Apple is a fruit. Apples are fruits. Apple is a fruit.”  
  Why: Excessive repetition.

#### 3C. Articulate (Grammar and formatting)
Key question: Is it well written and easy to understand?

- Good response  
  User: “What is photosynthesis?”  
  Model: “Photosynthesis is the process plants use to turn sunlight into energy.”  
  Why: Clear language and structure.

- Minor error  
  User: “What is photosynthesis?”  
  Model: “Photosynthesis is process plants use to turn sunlight into energy.”  
  Why: Minor grammar issue.

- Substantial error  
  User: “What is photosynthesis?”  
  Model: “photosynthesis plant make sun energy thing yes.”  
  Why: Hard to understand.

---

### 4) Length

Key question: Is the response to the point without being unnecessarily wordy?

- Good response  
  User: “What is 2+2?”  
  Model: “4.”  
  Why: Correct and concise.

- Minor error  
  User: “What is 2+2?”  
  Model: “4. This is basic arithmetic taught in early school.”  
  Why: Slightly verbose.

- Substantial error  
  User: “What is 2+2?”  
  Model: “To understand 2+2, we must first explore the history of mathematics…”  
  Why: Excessively long for a simple question.

---

## 2. How to Score a Model Response (1 to 5)

After identifying what the response does well and where it fails, assign a single overall quality score.

### 5 — Cannot be meaningfully improved
Definition: The response is accurate, fully aligned to the prompt, clear, and appropriately concise. If the request cannot be fulfilled, the response handles it responsibly with useful context.

Common attributes:
- Fully answers all necessary aspects of the request.
- All factual claims are accurate.
- Clear, easy to follow, and appropriately formatted.
- Clarifies ambiguity when needed.

Evaluation checks:
- Is there any real improvement needed?
- Would a revision be unnecessary?

### 4 — Mostly high quality but can be improved
Definition: The response is helpful and largely aligned, but has small weaknesses that do not significantly undermine usefulness.

Common attributes:
- Mostly follows instructions, with minor misses.
- Mostly accurate, with small errors that do not change the core usefulness.
- Minor clarity or formatting issues.

Evaluation checks:
- Would small edits noticeably improve it?
- Is it already helpful as-is?

### 3 — Partially adequate
Definition: The response is somewhat helpful but misses the overall goal or key parts of the request. It does not fully satisfy the user.

Common attributes:
- Answers some parts but misses others.
- Contains inaccuracies that make it less reliable.
- Clarity issues reduce usability.

Evaluation checks:
- Does it have a solid base but miss something crucial?
- Would targeted revisions meaningfully improve it?

### 2 — Mostly low quality
Definition: The response falls short in several key areas (missing details, factual errors, lack of clarity) but still contains some potentially useful content.

Common attributes:
- Partially misinterprets user intent.
- Omits important details.
- Includes significant factual errors.
- Includes irrelevant content or redundancy.
- Hard to read but partially understandable.

Evaluation checks:
- Does it barely meet the user’s needs?
- Would it require a rewrite to become reliably useful?

### 1 — Complete miss
Definition: The response provides little to no value. It fails the user’s intent and may be inaccurate, contradictory, irrelevant, or unreadable.

Common attributes:
- Misinterprets the request.
- Fails key instructions.
- Contains major factual errors.
- Contains contradictions or nonsensical content.
- Completely irrelevant or unusable formatting.

Evaluation checks:
- Does it provide almost no value?
- Would a full rewrite be required?

---

## 3. Writing Guidelines — Strengths

Strengths describe what the response does well in an objective and specific way.

### Requirements
- Use complete sentences starting with “The response…” or “The model…”
- Be objective and observable
- Be specific and relevant to user intent (accuracy, completeness, reasoning, clarity)
- Be self-contained
- Use present tense only
- Avoid first person statements

### Do not do the following
- Do not include links or tools used for validation
- Do not write vague praise
- Do not list baseline expectations (grammar alone is not a meaningful strength)
- Do not claim “absence of mistakes” as a strength

### Suggested format
“The response [what it does well], [why it provides meaningful value to the user].”

### Examples
Bad: “The response is accurate.”  
Good: “The response correctly lists the key differences between decision trees and random forests, which directly supports the user’s request for a comparison.”

Bad: “The grammar is perfect.”  
Good: “The response explains the process in a clear step-by-step structure that makes the instructions easy to follow.”

### Strength limits
Do not exceed five strengths. If the response is very poor, it is acceptable to record no strengths.

---

## 4. Writing Guidelines — Areas of Improvement (AOIs)

Areas of Improvement describe what must change for the response to become perfect.

Helpful mental model: If every AOI is fully fixed, the response should reach a 5/5 score.

### AOI Structure (4 parts)
1) Response Excerpt  
Copy the part of the response demonstrating the issue. Use ellipses for long text. If it applies to the whole answer, write “Full response.”

2) Description  
A complete, objective sentence explaining what is wrong and why it matters.

3) Severity  
- Minor: Improvement opportunity that does not undermine the core utility.
- Substantial: Significantly harms correctness, usefulness, or trust.

4) Sources (when applicable)  
Use sources only when the AOI involves factual inaccuracies or missing key facts. Do not add sources for tone, structure, verbosity, or style.

### AOI Writing Rules
- Use complete sentences starting with “The response…” or “The model…”
- Use present tense only
- Do not use first person statements
- Be specific and self-contained
- Do not include links or tools in the AOI description

### Handling unsupported claims
If the response includes a claim that cannot be verified or cited, write:  
“This information is unsupported.”  
Do not add sources for that AOI.

### AOI cap and grouping
Limit AOIs to 10 maximum per response. Group related issues where possible (verbosity, tone, formatting, repeated errors).

---

## 5. Preference Ranking Guidelines

Preference ranking selects whether Response 1 (R1) or Response 2 (R2) is preferred, and by what strength.

### Ranking strength guidance
- Slightly Better: Difference is small (often 0–1 point). Both are mostly acceptable; differences are minor or cosmetic.
- Better: Noticeable difference (often 1–2 points). One response is clearly more helpful or correct.
- Much Better: Large difference (2+ points). One response is strong while the other has major problems.
- Neither Response is Valid: Both responses score 2 or below. Avoid rewarding a poor response as “preferred.”

### Preference explanation rules
- Write 1–2 sentences (10–50 words)
- Use present tense
- Refer to answers as R1 and R2
- No first person statements
- No lists
- Do not include tools or sources
- Do not write phrases like “R1 is much better than R2” or “Neither response is valid” inside the explanation

### Good example (short and specific)
“R1 answers both parts of the user’s request with accurate details and clear structure. R2 omits key requested information and includes irrelevant content, which reduces usefulness and trust.”

---

## 6. Quick Templates

### Strength template
“The response [does X well], [which helps the user by Y].”

### AOI template
Response Excerpt: “...”  
Description: “The response [does not meet standard X], which [harms usefulness/trust by Y].”  
Severity: Minor or Substantial  
Sources: Add only if factual verification is required

### Preference explanation template
“R1 [main advantage]. R2 [main weakness], which [impact on user].”

---

## 7. Final Evaluator Checklist (ICON REAL)

Before submitting:
- Intent: Does it answer what the user asks?
- Complete: Are all parts covered?
- On-truth: Are facts correct and supportable?
- No contradictions: Is logic consistent?
- Relevant: Is all content on-topic?
- Efficient: Is it concise without repetition?
- Articulate: Is it clear and readable?
- Length right: Is the length appropriate for the request?

If these are met, the response typically deserves a high score.
