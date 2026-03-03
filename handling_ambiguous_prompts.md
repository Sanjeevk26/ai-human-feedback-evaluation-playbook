# Ambiguous Prompts: Evaluation Guide (RLHF)

This section explains how to handle and evaluate ambiguous or vague user prompts. Ambiguity may appear as a question or a statement. Even when the prompt is unclear, responses still require evaluation. When the model does not handle ambiguity appropriately, document the gaps using Areas of Improvement (AOIs).

Important: Some prompts look ambiguous in isolation but become clear when reading prior conversation turns. Always review the conversation history before deciding that a prompt is truly ambiguous.

---

## 1. Core Principle

When a prompt is ambiguous, the model’s job is to either:
- Provide a reasonable interpretation and respond, while making that interpretation clear, and optionally ask a clarifying question, or
- Ask for clarification before attempting the task, if the ambiguity is too high or required details are missing.

If the model guesses incorrectly, fails to clarify, or produces an unsafe or irrelevant response, capture that as AOIs.

---

## 2. Decide the Ambiguity Level

### A. Moderate Ambiguity (Intent is somewhat clear)
The user intent is partially inferable. The model should proceed with a best-effort response but should make its interpretation clear and optionally ask a clarifying question.

Expected model behavior:
- States or clearly implies what it thinks the user means, and
- Answers based on that interpretation, and
- Optionally asks one clarifying question to refine the answer.

### B. High Ambiguity (Intent is unclear)
The user intent is not reliably inferable, or essential details are missing. The model should request clarification before attempting the task.

Expected model behavior:
- Asks for clarification or required materials first, and
- Provides a helpful prompt for what information is needed.

---

## 3. How the Model Should Handle Moderate Ambiguity

For moderate ambiguity, the model should do at least one of the following:
- Explicit interpretation: Start by stating its interpretation of the request.
- Implicit interpretation: Make it obvious through the response what it is doing.
- Clarifying question: Ask one targeted question after the initial help.

### Examples (Moderate Ambiguity)

#### 3.1 Grammar or spelling errors
Prompt:
- "Who authored Pride and Prejuujuu?"

Expected model response:
- "Pride and Prejudice was authored by Jane Austen."

Why this works:
- The intent is clear despite the typo.

---

#### 3.2 Google-search-style queries
Prompt:
- "College degree"

Expected model response:
- Defines what a college degree is in plain language.
- Asks a clarifying question to refine.

Example:
- "A college degree is an academic qualification awarded by a college or university after completing a program of study. It shows you’ve gained knowledge and skills in a specific field. Are you interested in degrees in a specific field or a comparison of degree types?"

Why this works:
- Interprets the query as a request for a definition and guidance.

---

#### 3.3 Open-ended or vague request
Prompt:
- "Diet plan"

Expected model response:
- Provides a general starting point with a few common variants.
- Requests details to personalize.

Example:
- "Here is a simple balanced daily plan, plus a weight-loss and a muscle-gain version. If you share age, weight, height, activity level, and goal, I can tailor it."

Why this works:
- Gives immediate value without pretending to know missing details.

---

#### 3.4 Unclear request that still has a plausible meaning
Prompt:
- "=SUM(C2:C5)"

Expected model response:
- Explains what the formula does and what range means.
- Optionally offers to compute if values are provided.

Example:
- "This formula adds the values in cells C2 through C5 and returns the total. If you share the numbers in those cells, I can calculate the result."

Why this works:
- The user likely wants explanation or help using the formula.

---

#### 3.5 Necessary information missing, but the task is still guessable
Prompt:
- "Write me a product description"

Expected model response:
- Asks for key details (product, audience, platform, tone, features).
- Offers to draft a generic example if details are not available.

Example:
- "What is the product, who is it for, where will it be sold, and what tone do you want? If you prefer, I can draft a ready-to-use example and you can adjust details."

Why this works:
- Clarifies missing inputs while keeping momentum.

---

## 4. How the Model Should Handle High Ambiguity

For high ambiguity, the model should not guess. It should request clarification first.

Expected model behavior:
- Asks targeted questions to make the request answerable.
- Indicates what information is required to proceed.
- Maintains a helpful tone and provides examples of the needed context.

### Examples (High Ambiguity)

#### 4.1 No clearly worded or answerable request
Prompt:
- "hello"

Expected model response:
- "Hi. How can I help you today?"

Why this works:
- No task is present; the model invites the user to specify a goal.

---

#### 4.2 Necessary context is missing
Prompt:
- "Why did he do it?"

Expected model response:
- "I need more context: who is 'he' and what did he do? If you share the situation (historical event, movie plot, personal scenario), I can explain likely motivations."

Why this works:
- Prevents hallucination and ensures the next response is relevant.

---

#### 4.3 Severe spelling/grammar issues prevent understanding
Prompt:
- "who rote sng bndao pancakes?"

Expected model response:
- "Could you clarify what you’re asking? I want to make sure I respond correctly. Are you asking for a pancake recipe, a song, or something else?"

Why this works:
- The model does not pretend it understands; it requests clarification.

---

## 5. Evaluator Guidance: What to Penalize When the Model Handles Ambiguity Poorly

Write Areas of Improvement (AOIs) when the model:
- Fails to ask for clarification when ambiguity is high.
- Makes a confident guess without stating assumptions.
- Answers a different task than the user likely intended.
- Hallucinates details to fill missing context.
- Asks too many questions without giving any initial help (when moderate ambiguity exists).
- Provides generic filler rather than clarifying what it is doing.

---

## 6. Common AOI Patterns for Ambiguous Prompts

Use these as reusable AOI phrasing patterns. Keep AOIs in present tense and objective.

### 6.1 Missing clarification (high ambiguity)
- "The response attempts to answer despite missing essential context, which increases the risk of irrelevance or hallucination. It should request clarification before proceeding."

### 6.2 Unstated assumptions (moderate ambiguity)
- "The response does not clarify its interpretation of the ambiguous prompt, which makes it difficult to judge whether it addresses the user’s intent. It should state the assumed intent or ask a targeted clarifying question."

### 6.3 Over-questioning (moderate ambiguity)
- "The response asks multiple clarifying questions without providing any immediate helpful starting point, which slows progress. It should provide a reasonable default answer and ask one targeted follow-up question."

### 6.4 Hallucinated specifics
- "The response introduces specific details not provided by the user. This information is unsupported and reduces trust."

---

## 7. Quick Decision Checklist

Before evaluating a response to an ambiguous prompt:

1. Does conversation history reduce ambiguity?
2. Is the intent moderately clear or highly unclear?
3. If moderately clear: does the model give a best-effort response and clarify assumptions?
4. If highly unclear: does the model ask for clarification before answering?
5. Does the response avoid inventing details?

If the model fails any of these, capture the issue with AOIs.

---
