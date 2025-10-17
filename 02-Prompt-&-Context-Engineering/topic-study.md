# Fundamentals of Prompt and Context Engineering (Roman Urdu with Examples)

## 1. Prompt Engineering aur Context Engineering ke Primary Goals aur Differences

**Explanation (Roman Urdu):**  
Prompt engineering ka maqsad hai clear aur specific instructions banana jo LLM se desired output hasil karein, jaise ke koi specific jawab ya task. Yeh ek single command ya question pe focus karta hai. Context engineering ziada comprehensive hai; yeh poora context window (prompts, documents, tools, memory) ko design karta hai taake AI complex tasks ko autonomously handle kar sake. Prompt engineering conversational hai, jabke context engineering code-like aur agent-based systems ke liye hota hai.

**Example:**  
- **Prompt Engineering:** “Ek formal email likho jo client ko project delay ke baare mein bataye.”  
  - Yeh ek simple instruction hai jo direct output mangta hai.  
- **Context Engineering:** “Ek AI agent banaye jo client emails handle kare, Gmail API se data fetch kare, company policy ke mutabiq tone rakhe, aur sensitive info redact kare.”  
  - Yeh poora system design karta hai, including tools aur memory.

**Study Tip:** Prompt engineering ke liye clear verbs (jaise “likho,” “analyze”) use karo. Context engineering ke liye tools aur data integration pe focus karo.

---

## 2. LLMs Kaise Kaam Karte Hain (Prediction Engines)

**Explanation (Roman Urdu):**  
LLMs human jaise nahi sochte; yeh prediction engines hain jo agla token (word ya symbol) guess karte hain based on patterns jo training data mein hote hain. Yeh statistical models hain jo probability ke hisaab se kaam karte hain, na ke samajh ke saath. Har output pehlay input aur training ke patterns pe depend karta hai.

**Example:**  
Agar aap input dete hain: “Mera naam Ali hai aur main…”  
LLM predict karega agla word, jaise “ek” ya “student,” based on common patterns. Agar aap poochte hain “2+2=?”, toh yeh “4” predict karega kyunki yeh pattern training mein common hai, lekin yeh actually samajh nahi raha.

**Study Tip:** Yaad rakho ke LLMs sophisticated autocomplete hain. Unki accuracy context aur clear prompts pe depend karti hai.

---

## 3. Common Failure Modes

**Explanation (Roman Urdu):**  
LLMs ke common failure modes mein shamil hain:  
- **Hallucinations:** Jab LLM ghalat ya banayi hui information deta hai kyunki context ya data missing hai.  
- **Messy Outputs:** Agar instructions vague ya unclear hain, toh output disorganized ya irrelevant hota hai.  
- **MoE-Specific (ChatGPT, Gemini, Grok):** Routing errors jab domain-specific signals clear na hon, aur ghalat experts activate hon.

**Example:**  
- **Hallucination:** Prompt: “Mujhe Pakistan ke 2026 ke elections ke baare mein bataye.”  
  - Output: “2026 ke elections mein XYZ jeeta” (ghalat, kyunki future data nahi hai).  
  - Solution: Context provide karo, jaise recent election trends.  
- **Messy Output:** Prompt: “AI ke baare mein likho.”  
  - Output: Random, unorganized info kyunki prompt vague hai.  
  - Solution: Specific prompt, “AI ke medical applications ke baare mein 200 words mein likho.”  

**Study Tip:** Hallucinations se bachne ke liye RAG ya relevant documents use karo. Messy outputs ke liye specific aur structured prompts banaye.

---

## 4. Recommended Workflows

**Explanation (Roman Urdu):**  
Effective workflow yeh hai ke pehle clear prompt banaye jo behavior guide kare (e.g., tone, format), phir context add karein (jaise documents ya tool outputs) taake output accurate ho. Agentic flows mein, tool outputs (jaise API data) ko wapas LLM mein feed kiya jata hai taake iterative refinement ho sake.

**Example:**  
- **Workflow:**  
  1. **Prompt:** “Ek customer feedback report banaye jo positive aur negative sentiments ko JSON format mein summarize kare.”  
  2. **Context:** RAG se retrieved feedback: “App acha hai lekin slow hai.”  
  3. **Tool Output:** Sentiment analysis tool se: {“positive”: 60%, “negative”: 40%}.  
  4. **Feed Back:** LLM is data ko refine karta hai aur final JSON output deta hai:  
     ```json
     {
       "positive": "App user-friendly hai (60%)",
       "negative": "App speed issues (40%)"
     }
     ```

**Study Tip:** Practice karein ke pehle prompt design karein, phir context (jaise PDF sections) add karein. Tool outputs ko wapas feed karne ka flow samjhein.

---

## 5. LLMs as Sophisticated Autocomplete Systems

**Explanation (Roman Urdu):**  
LLMs ko sophisticated autocomplete systems ke taur pe dekha jata hai kyunki yeh sirf agla word ya token predict karte hain based on input aur training patterns. Yeh human understanding ki tarah nahi sochte; inka kaam hai patterns match karna aur probable outputs generate karna.

**Example:**  
Prompt: “Mera favorite color blue hai, aur main…”  
LLM predict karega: “…isliye blue shirt pehnta hoon” kyunki yeh pattern common hai. Yeh samajh nahi raha ke aap blue kyun pasand karte hain, bas pattern follow karta hai.

**Study Tip:** Yaad rakho ke LLMs ke outputs context aur prompt clarity pe depend karte hain. Inko human jaise intelligence na samjhein.

---

## Practice Questions for Exam Prep (Roman Urdu)

1. **Prompt Engineering ka primary goal kya hai?**  
   - **Jawab:** Clear instructions banana desired output ke liye.  
   - **Example:** “Ek 200-word blog post likho AI ke benefits pe.”  

2. **Context Engineering ka focus kya hai?**  
   - **Jawab:** Poora context window (prompts, tools, memory) design karna.  
   - **Example:** “Ek AI agent banaye jo HR policy PDF summarize kare aur remote work questions ka jawab de.”  

3. **LLM kaise kaam karta hai?**  
   - **Jawab:** Prediction engine ke taur pe, agla token guess karta hai.  
   - **Example:** Input: “2+2=”, Output: “4” (pattern-based).  

4. **Hallucination ka ek example kya hai?**  
   - **Jawab:** Ghalat info jab context missing ho.  
   - **Example:** “2026 election results” bina data ke.  

5. **Recommended workflow kya hai?**  
   - **Jawab:** Pehle prompt, phir context, aur tool outputs feed back.  
   - **Example:** Feedback analysis ke liye prompt, RAG data, aur JSON output.

**Study Tips (Roman Urdu):**  
- **Practice:** Har concept ke liye prompts banaye aur test karein (Grok, ChatGPT pe).  
- **Memorize:** Prompt vs. context ka difference, failure modes (hallucinations, messy outputs).  
- **Examples:** Syllabus ke examples analyze karein aur weak prompts ko improve karein.  
- **Tools:** Grok pe Thinking Mode use karein CoT prompts ke liye.