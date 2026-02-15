# 💡 AI Startup Idea Validator

### 🚀 Project Overview
Validating a business idea usually takes weeks of market research. This automated agent cuts that time down to seconds. It acts as an unbiased "Digital Consultant," taking a raw startup concept and providing an instant, comprehensive analysis using **Google Gemini AI**.

It doesn't just email the results—it also logs the detailed analysis back into the database, creating a permanent repository of vetted ideas.

---

### 🛠️ Tech Stack
* **Orchestration:** Make.com
* **AI Engine:** Google Gemini (Generative AI)
* **Database:** Google Sheets (Two-way sync: Read & Write)
* **Communication:** Gmail

---

### ⚙️ The Workflow Logic
The system operates on a "Enrichment Loop":

1.  **Input:** A user enters their startup idea into a Google Sheet (via Form or direct entry).
2.  **Processing:** Make.com detects the new row and sends the idea to **Google Gemini**.
3.  **The Prompt:** The AI is instructed to act as a [e.g., Venture Capitalist / Market Analyst] and evaluate:
    * *Viability Score (1-10)*
    * *Potential Competitors*
    * *Monetization Strategy*
4.  **Enrichment:** The system **updates the original Google Sheet row** with the AI's analysis (so the data is saved centrally).
5.  **Notification:** Finally, a formatted email with the feedback is sent to the user.

<img width="1266" height="612" alt="image" src="https://github.com/user-attachments/assets/628ebd89-146a-4cc3-82d8-ecfe7d21979e" />


---
### 🧠 The AI "Brain" (Prompt Engineering)
I engineered a specific prompt to ensure the AI didn't just "chat," but returned structured data suitable for database entry.

**The Prompt Strategy:**
* **Context Injection:** I dynamically inserted the `Startup Name`, `Problem`, and `Target Audience` from the form data using Make.com variable mapping.
* **Constraint Prompting:** I restricted the output to a *single* "Fatal Flaw" to force the AI to identify the highest-risk factor.
* **Data Formatting:** I explicitly requested a "2-sentence summary" to ensure the output fit cleanly into the Google Sheets cell limit.

**The Actual Prompt:**
> "Analyze this startup idea: 
> Startup Name: {{2.`2`}} 
> The Problem: {{2.`3`}} 
> Target Audience: {{2.`4`}} 
> Solution: {{2.`5`}}
>
> **Output Requirements:**
> 1. Give a Viability Score (1-10).
> 2. Identify one Fatal Flaw.
> 3. Provide a 2-sentence summary for my database."

---

### 🏆 Key Features
* **Database Enrichment:** Unlike simple notifications, this workflow saves the AI's output back to the source (Google Sheets), allowing for historical analysis.
* **Instant Feedback Loop:** Reduces the feedback time from days to <1 minute.
* **Structured Output:** AI response is formatted for easy reading in both email and spreadsheet cells.
