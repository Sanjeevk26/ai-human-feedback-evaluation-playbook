# Human Feedback Evaluation – Personal Playbook

These notes explain how to evaluate AI responses **the way a normal human would**, not like a machine.

The goal is simple:
> Decide which response actually helps the user more — and explain why.

---

## Step 1: Understand the user first (always)

Before looking at any answer, ask yourself:
- What is the user really trying to do?
- Is this a quick question or a complex task?
- Would a single response be enough, or would clarification help?

### Example
User asks:
“Suggest a phone under 20,000.”

This already implies:
- Budget matters
- Product comparison matters
- Accuracy matters

---

## Step 2: Use any provided context correctly

Sometimes the user also provides:
- Screenshots
- Documents
- Webpage snapshots

Treat these as **trusted reference material**.

A good AI response:
- Uses relevant information from the context
- Ignores unrelated information
- Does not invent facts that aren’t visible

---

# Evaluation Rubrics (Simplified)

You evaluate **each response separately**, then compare them.

---

## 1️⃣ Instruction Following

**What this checks:**  
Did the response actually do what the user asked?

### No issues
- Followed all instructions clearly

### Minor issue
- Main task done, but missed a small detail

### Major issue
- Ignored or misunderstood the main request

### Example
User: “Summarize this article in bullet points.”

- Paragraph summary → Minor issue  
- No summary at all → Major issue

---

## 2️⃣ Conciseness & Relevance

**What this checks:**  
Is the response focused and useful, or long and unnecessary?

### No issues
- Every part adds value

### Minor issue
- Slight repetition or small irrelevant section

### Major issue
- Lots of fluff or off-topic content

### Example
User: “What is the capital of India?”

If the answer includes a long history lesson → likely a minor or major issue depending on length.

---

## 3️⃣ Content Completeness

**What this checks:**  
Did the response cover *everything* the user asked for?

### No issues
- Fully answers the question

### Minor issue
- Partially helpful but missing some elements

### Major issue
- Missing key information, user goal not met

### Example
User: “Give 5 examples.”
Response gives only 3 → Major issue

---

## 4️⃣ Context Usage (when reference material is given)

**What this checks:**  
Did the response correctly use the provided material?

### No issues
- Used all relevant context correctly

### Minor issue
- Missed some context but still mostly helpful

### Major issue
- Used irrelevant context or ignored important info

---

## 5️⃣ Collaborativity

**What this checks:**  
Did the response act like a helpful assistant *when needed*?

> Not every question needs follow-ups.

### No issues
- Asked helpful clarifying questions or gave smart next steps

### Minor issue
- Very generic follow-up (“Let me know if you need more”)

### Major issue
- Clarification was clearly needed, but response guessed instead

### Not applicable
- Simple questions that can be answered in one line

### Example
User: “Book a flight for me.”

No clarification on dates or location → Major issue

---

## 6️⃣ Grounded Accuracy (based on provided material)

**What this checks:**  
Are claims that rely on the given reference material accurate?

### No issues
- Matches the provided content exactly

### Minor issue
- Small secondary detail is wrong

### Major issue
- Core information from the material is wrong

### Example
Reference says price is 10,000  
Response says 15,000 → Major issue

---

## 7️⃣ General Truthfulness

**What this checks:**  
Are factual claims correct based on general knowledge?

### No issues
- All facts are correct

### Minor issue
- Small factual error that doesn’t affect main goal

### Major issue
- Important facts are wrong or misleading

### Example
Saying a non-existent product exists → Major issue

---

## 8️⃣ Links (if included)

**What this checks:**  
Do links actually help the user?

### No issues
- Relevant and functional

### Minor issue
- Slightly indirect or one broken link

### Major issue
- Misleading, broken, or irrelevant links

---

## 9️⃣ Overall Quality

**Final human judgment.**

Ask yourself:
> If I were the user, how satisfied would I feel?

### Cannot be improved
- No noticeable issues anywhere

### Minor room for improvement
- Small flaws but still strong

### Okay
- Several minor issues affecting experience

### Poor
- One major issue

### Very poor
- Multiple major issues, frustrating to use

---

## Preference Ranking (Choosing between two responses)

After rating both responses:
- Decide which one you personally prefer
- Or say they’re about the same

### Important
Even if both are “technically correct”, one can still feel **more helpful or clearer**.

---

## Writing a good justification (human-style)

A good justification:
- Mentions specific differences
- Explains why they matter
- Avoids repeating rubric labels

### Example
“I preferred Response A because it stayed focused on the user’s question and used the reference material correctly. Response B added extra information that wasn’t asked for and included a factual error, which reduced trust.”

---

---

# Worked Examples: How to Actually Apply the Rubrics (Easy + Memorable)

This section shows **exactly how to think** when you see two responses.

Read this slowly once.  
After that, your brain will auto-pattern match during real evaluations.

---

## Example 1: Simple, Single-Turn Question

### User Prompt
“What is the capital of Australia?”

---

### Response A
“The capital of Australia is Canberra.”

### Response B
“The capital of Australia is Sydney, which is the largest city and an important cultural center.”

---

## Step-by-step rubric thinking

### 1️⃣ Instruction Following
- User asked a direct factual question.
- A answers correctly.
- B answers incorrectly.

**A:** No issues  
**B:** Major issue (wrong answer)

---

### 2️⃣ Conciseness & Relevance
- A is short and relevant.
- B adds extra info AND is wrong.

**A:** No issues  
**B:** Major issue (irrelevant + incorrect)

---

### 3️⃣ Content Completeness
- Both *attempt* to answer fully.

**A:** No issues  
**B:** Major issue (factually wrong → user goal not met)

---

### 4️⃣ Context Usage
- No reference material was provided.

**A:** N/A  
**B:** N/A  

---

### 5️⃣ Collaborativity
- This is a one-line factual question.
- No follow-up needed.

**A:** N/A  
**B:** N/A  

---

### 6️⃣ Grounded Accuracy
- No provided document or webpage.

**A:** N/A  
**B:** N/A  

---

### 7️⃣ General Truthfulness
- A is correct.
- B is wrong.

**A:** No issues  
**B:** Major issue

---

### 8️⃣ Links
- No links used.

**A:** N/A  
**B:** N/A  

---

### 9️⃣ Overall Quality
**A:** Cannot be improved  
**B:** Very poor

---

### ✅ Preference Ranking
**Response A is MUCH better**

---

### 📝 Human-style justification
“I preferred Response A because it gives the correct answer directly. Response B provides incorrect information, which would mislead the user, making it unreliable.”

---

## Memory Hook
> **One wrong core fact = game over**, even if the rest sounds confident.

---

---

## Example 2: Slightly Complex, Needs Careful Reading

### User Prompt
“Suggest 3 budget laptops suitable for students.”

---

### Response A
“Here are three budget laptops suitable for students:
1. Laptop X – affordable and lightweight  
2. Laptop Y – good battery life  
3. Laptop Z – balanced performance”

---

### Response B
“There are many laptops in the market. Students should focus on portability, battery life, and performance. Budget laptops are useful for daily tasks like browsing and assignments.”

---

## Rubric breakdown

### 1️⃣ Instruction Following
- User asked for **3 laptops**.
- A gives 3.
- B gives advice, not laptops.

**A:** No issues  
**B:** Major issue

---

### 2️⃣ Conciseness & Relevance
- A is focused.
- B is vague and generic.

**A:** No issues  
**B:** Major issue

---

### 3️⃣ Content Completeness
- A meets the request.
- B does not list any laptops.

**A:** No issues  
**B:** Major issue

---

### 4️⃣ Context Usage
- No external context provided.

**A:** N/A  
**B:** N/A  

---

### 5️⃣ Collaborativity
- The task could be answered in one turn.
- No clarification required.

**A:** N/A  
**B:** N/A  

---

### 6️⃣ Grounded Accuracy
- No reference material.

**A:** N/A  
**B:** N/A  

---

### 7️⃣ General Truthfulness
- B is factually true but irrelevant.
- Truth ≠ usefulness.

**A:** No issues  
**B:** No issues (but still fails overall)

---

### 8️⃣ Links
- No links.

---

### 9️⃣ Overall Quality
**A:** Cannot be improved  
**B:** Pretty bad (fails user intent)

---

### ✅ Preference Ranking
**Response A is MUCH better**

---

### 📝 Human-style justification
“I preferred Response A because it directly answers the user’s request by listing three suitable laptops. Response B remains generic and does not provide specific recommendations, which makes it unhelpful for the user.”

---

## Memory Hook
> **Being true but useless is still bad.**

---

---

## Example 3: When Both Answers Are Mostly Good (This Is Where People Get Confused)

### User Prompt
“Explain photosynthesis in simple terms.”

---

### Response A
“Photosynthesis is the process by which plants use sunlight, water, and carbon dioxide to make food and release oxygen.”

---

### Response B
“Photosynthesis is how green plants prepare their food. Using sunlight, plants convert water and carbon dioxide into glucose, which gives them energy.”

---

## Rubric thinking (carefully)

### 1️⃣ Instruction Following
- Both explain photosynthesis simply.

**A:** No issues  
**B:** No issues  

---

### 2️⃣ Conciseness & Relevance
- Both are concise.
- Both stay on topic.

**A:** No issues  
**B:** No issues  

---

### 3️⃣ Content Completeness
- Both cover the core idea.

**A:** No issues  
**B:** No issues  

---

### 4️⃣ Collaborativity
- Single-turn explanation.
- No follow-up needed.

**A:** N/A  
**B:** N/A  

---

### 5️⃣ Truthfulness
- Both are accurate.

**A:** No issues  
**B:** No issues  

---

### 9️⃣ Overall Quality
**A:** Cannot be improved  
**B:** Cannot be improved  

---

### ✅ Preference Ranking
**Both responses are about the same**

---

### 📝 Human-style justification
“Both responses clearly and accurately explain photosynthesis in simple terms. While the wording differs slightly, they are equally understandable and fulfill the user’s intent.”

---

## Memory Hook
> **Different wording ≠ different quality.**

---

---

## Example 4: When Preference Is Slight, Not Extreme

### User Prompt
“Give tips to improve concentration while studying.”

---

### Response A
“Here are some tips:
- Study in a quiet place
- Take regular breaks
- Avoid distractions”

---

### Response B
“To improve concentration, choose a quiet environment, break your study time into focused sessions, and keep your phone away to reduce distractions.”

---

## Rubric comparison (summary style)

- Both follow instructions ✔
- Both are relevant ✔
- Both are complete ✔
- No facts to verify ✔

**Key difference:**  
B flows more naturally and feels more conversational.

---

### ✅ Preference Ranking
**Response B is SLIGHTLY better**

---

### 📝 Human-style justification
“I slightly preferred Response B because it presents the same advice in a smoother, more natural way, which makes it easier to read, even though both responses are correct.”

---

## Memory Hook
> **When everything is correct, clarity decides preference.**

---

---

## One Final Mental Checklist (Remember This)

When stuck, ask yourself:

1. Did it answer what was asked?
2. Is anything clearly wrong?
3. Did it miss something important?
4. Would *I* trust this answer?
5. Which one would I actually want if I were the user?

If you answer these honestly, your ratings will almost always be right.

---

End of examples.
