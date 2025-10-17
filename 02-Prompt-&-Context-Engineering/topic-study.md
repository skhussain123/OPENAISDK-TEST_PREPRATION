## 1
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


---

## 2
# Configuration Settings for LLMs (Roman Urdu with Examples)

## 1. Temperature (Randomness/Creativity Control)

**Explanation (Roman Urdu):**  
Temperature ek setting hai jo LLM ke output ki randomness ya creativity ko control karti hai. Yeh 0 se 1 (ya ziada) tak hoti hai:  
- **Low Temperature (0–0.3):** Consistent aur predictable outputs deta hai, kyunki model top probable tokens hi choose karta hai.  
- **High Temperature (0.8–1):** Ziada creative aur diverse outputs, lekin kabhi irrelevant ya random ho sakta hai.  
- **Medium Temperature (0.4–0.7):** Balance between consistency aur creativity.

**Example:**  
- **Prompt:** “Ek poem likho pyar ke baare mein.”  
  - **Temperature 0.2:** Output: “Pyar ek khubsurat ehsaas hai, dil se dil tak jata hai.” (consistent, predictable)  
  - **Temperature 0.9:** Output: “Pyar toofan hai, kabhi roshni, kabhi andhera!” (creative, diverse)  

**Study Tip:** Temperature ke effects ko samajhne ke liye Grok ya ChatGPT pe same prompt ke saath different values (0, 0.7, 1) test karo.

---

## 2. Top-K Sampling (Limits to Top Likely Tokens)

**Explanation (Roman Urdu):**  
Top-K sampling mein LLM sirf top K most likely tokens mein se choose karta hai agla word ya token predict karne ke liye. Yeh randomness ko control karta hai aur output ko focused rakhta hai. Chhota K (jaise 20) ziada strict hota hai, jabke bara K (jaise 100) ziada diversity deta hai.

**Example:**  
- **Prompt:** “Mera favorite color blue hai, agla word kya hai?”  
  - **Top-K 10:** Output: “aur” (limited to top 10 likely tokens, predictable).  
  - **Top-K 50:** Output: “kyunki” (more diverse, still relevant).  

**Study Tip:** Top-K ke saath experiments karein on [platform.openai.com](https://platform.openai.com/) ya [aistudio.google.com](https://aistudio.google.com/) to see kaise outputs change hote hain.

---

## 3. Top-P Sampling (Nucleus Sampling)

**Explanation (Roman Urdu):**  
Top-P (ya nucleus sampling) mein LLM un tokens ko choose karta hai jo ek specific probability threshold (P) tak cover karte hain. Maslan, agar Top-P 0.9 hai, toh model un tokens ko select karta hai jo 90% probability mass banate hain. Yeh dynamic hai aur Top-K se ziada flexible hota hai.

**Example:**  
- **Prompt:** “Ek kahani shuru karo jungle ke baare mein.”  
  - **Top-P 0.9:** Output: “Jungle mein ek sher rehta tha…” (focused, relevant).  
  - **Top-P 0.99:** Output: “Jungle mein ek anokha janwar tha…” (more diverse).  

**Study Tip:** Top-P aur Top-K ke differences ko samajhne ke liye same prompt ke saath dono test karo aur output ka variety compare karo.

---

## 4. Output/Token Limits (Length and Cost)

**Explanation (Roman Urdu):**  
Output ya token limits output ki length aur computational cost ko control karte hain. Har token ek word ya symbol hota hai, aur ziada tokens ka matlab hai ziada processing aur cost. Limits set karne se aap output ko concise rakhte hain aur budget control mein rakhte hain.

**Example:**  
- **Prompt:** “AI ke benefits ke baare mein 500 words mein likho.”  
  - **Token Limit 200:** Output: Chhota paragraph (50–100 words), incomplete.  
  - **Token Limit 1000:** Output: Poora 500-word essay, detailed aur complete.  

**Study Tip:** Token limits ke impact ko dekhne ke liye Grok pe chhote (100) aur bare (1000) limits ke saath test karo.

---

## 5. Starting Points for Configurations

**Explanation (Roman Urdu):**  
Configuration settings ke starting points task ke type pe depend karte hain:  
- **Conservative (Factual Tasks):** Low temperature (0–0.3), Top-P 0.9, Top-K 20 – consistent aur accurate outputs ke liye.  
- **Balanced (General Tasks):** Medium temperature (0.4–0.7), Top-P 0.95, Top-K 30 – creativity aur accuracy ka balance.  
- **Creative (Writing/Storytelling):** High temperature (0.8–1), Top-P 0.99, Top-K 40 – diverse aur unique outputs ke liye.

**Example:**  
- **Conservative (Math):** Prompt: “2 + 2 ka jawab do.”  
  - Settings: Temp 0, Top-P 0.9, Top-K 20  
  - Output: “4” (consistent, no randomness).  
- **Creative (Story):** Prompt: “Ek sci-fi kahani likho.”  
  - Settings: Temp 0.9, Top-P 0.99, Top-K 40  
  - Output: “Ek alien spaceship ne zameen pe attack kiya…” (diverse, creative).  

**Study Tip:** Har configuration type ke liye sample prompts banaye aur [console.anthropic.com](https://console.anthropic.com/) ya grok.com pe test karo.

---

## 6. Appropriate Uses of Configurations

**Explanation (Roman Urdu):**  
Different tasks ke liye alag configurations use hoti hain:  
- **Math/Factual Tasks:** Temperature 0 ya low (0–0.3) taake output consistent ho.  
- **Writing/Storytelling:** High temperature (0.8–1) taake creative aur diverse ho.  
- **General Analysis:** Medium temperature (0.4–0.7) taake balance rahe.  
- **Token Limits:** Chhote tasks ke liye low limits (100–200 tokens), lambay tasks ke liye high limits (1000+ tokens).

**Example:**  
- **Math Task:** Prompt: “Solve 5x + 3 = 18.”  
  - Settings: Temp 0, Top-P 0.9, Top-K 20  
  - Output: “x = 3” (step-by-step, accurate).  
- **Writing Task:** Prompt: “Ek blog post likho AI ke future ke baare mein.”  
  - Settings: Temp 0.7, Top-P 0.95, Top-K 30  
  - Output: “AI ka future healthcare aur education mein revolutionary hoga…” (balanced, engaging).  

**Study Tip:** Har task type ke liye appropriate settings yaad karo aur Grok ya Gemini pe test kar ke dekho kaise outputs change hote hain.

---

## Practice Questions for Exam Prep (Roman Urdu)

1. **Temperature ka kya kaam hai?**  
   - **Jawab:** Randomness aur creativity control karta hai.  
   - **Example:** Temp 0.2 se “Pyar ek ehsaas hai” (consistent); Temp 0.9 se “Pyar toofan hai” (creative).  

2. **Top-K sampling kya karta hai?**  
   - **Jawab:** Top K likely tokens mein se choose karta hai.  
   - **Example:** Top-K 10 se “aur” (predictable); Top-K 50 se “kyunki” (diverse).  

3. **Top-P sampling ka faida kya hai?**  
   - **Jawab:** Dynamic token selection probability threshold ke hisaab se.  
   - **Example:** Top-P 0.9 se “Jungle mein sher…” (focused); Top-P 0.99 se “Jungle mein anokha janwar…” (diverse).  

4. **Token limits kyun zaroori hain?**  
   - **Jawab:** Output length aur cost control karte hain.  
   - **Example:** 200-token limit se chhota output; 1000-token limit se poora essay.  

5. **Math tasks ke liye best configuration kya hai?**  
   - **Jawab:** Temp 0, Top-P 0.9, Top-K 20.  
   - **Example:** “2 + 2 = 4” (consistent, no randomness).

**Study Tips (Roman Urdu):**  
- **Practice:** Har setting (Temp, Top-K, Top-P) ke saath prompts test karein on grok.com ya [platform.openai.com](https://platform.openai.com/).  
- **Memorize:** Conservative (low Temp), balanced, aur creative settings ke differences yaad karo.  
- **Examples:** Math, writing, aur analysis tasks ke liye alag-alag configurations try karein.  
- **Tools:** Grok ke Thinking Mode ya ChatGPT pe settings change karke outputs compare karo.

---
## 3
# Prompting Techniques for LLMs (Roman Urdu with Examples)

## 1. Basic Prompting Techniques

### a. Zero-Shot Prompting (Direct Question)

**Explanation (Roman Urdu):**  
Zero-shot prompting mein aap direct sawal poochte hain bina kisi example ke. Yeh simple tasks ke liye hota hai jahan LLM ko pehlay se trained patterns se jawab dena hota hai. Yeh fast hai lekin complex tasks mein accuracy kam ho sakti hai.

**Example:**  
- **Prompt:** “Pakistan ka capital kya hai?”  
- **Output:** “Pakistan ka capital Islamabad hai.”  
- **Explanation:** Bina example ke, LLM trained knowledge se direct jawab deta hai.

**Study Tip:** Zero-shot prompts test karo simple factual questions ke liye, jaise geography ya general knowledge, on Grok ya ChatGPT.

---

### b. One-Shot Prompting (One Example)

**Explanation (Roman Urdu):**  
One-shot prompting mein ek example diya jata hai taake LLM output ka pattern samajh sake. Yeh zero-shot se better hota hai jab thodi guidance chahiye hoti hai.

**Example:**  
- **Prompt:** “Translate: Hello → Salaam. Now translate: Goodbye.”  
- **Output:** “Goodbye → Alvida.”  
- **Explanation:** Ek example (Hello → Salaam) se LLM translation ka pattern samajhta hai.

**Study Tip:** One-shot prompts banaye aur test karo tasks jaise translation ya classification ke liye on [platform.openai.com](https://platform.openai.com/).

---

### c. Few-Shot Prompting (3–5 Examples for Patterns)

**Explanation (Roman Urdu):**  
Few-shot prompting mein 3–5 examples dete hain taake LLM ko clear pattern mil sake. Yeh complex tasks ke liye useful hai jahan output ka format ya style specific hona chahiye.

**Example:**  
- **Prompt:**  
  ```
  Classify sentiment:
  - "Product acha hai" → Positive
  - "Bohat slow hai" → Negative
  - "Theek hai, normal" → Neutral
  Now classify: "App bohat fast hai."
  ```  
- **Output:** “Positive”  
- **Explanation:** 3 examples se LLM sentiment classification ka pattern seekhta hai.

**Study Tip:** Few-shot prompts ke liye 3–5 examples ke saath structured tasks (jaise sentiment analysis) test karo on Gemini ya Claude.

---

## 2. Advanced Prompting Techniques

### a. Role Prompting (Assign Persona)

**Explanation (Roman Urdu):**  
Role prompting mein LLM ko ek specific persona assign kiya jata hai, jaise “doctor” ya “teacher,” taake output us role ke mutabiq ho. Yeh responses ko professional ya context-specific banata hai.

**Example:**  
- **Prompt:** “Tum ek financial advisor ho. Mujhe stock market investment ke tips do.”  
- **Output:** “Pehle apna risk tolerance aur goals assess karo. Diversified portfolio banaye, jaise mutual funds ya ETFs…”  
- **Explanation:** Financial advisor role se output professional aur targeted hota hai.

**Study Tip:** Role prompts test karo alag-alag personas ke saath (jaise lawyer, chef) on Grok ya ChatGPT.

---

### b. System Prompting (Behavior Guidelines)

**Explanation (Roman Urdu):**  
System prompting mein LLM ke liye behavior guidelines set kiye jate hain, jaise tone, format, ya constraints. Yeh model ke overall behavior ko control karta hai, usually system-level instructions ke through.

**Example:**  
- **Prompt:**  
  ```
  System: Hamesha formal tone use karo aur jawab JSON format mein do.
  User: Pakistan ka population kya hai?
  ```  
- **Output:**  
  ```json
  {
    "question": "Pakistan ka population kya hai?",
    "answer": "Pakistan ka population takreeban 240 million hai (2025 estimate)."
  }
  ```  
- **Explanation:** System prompt formal tone aur JSON format enforce karta hai.

**Study Tip:** System prompts ke saath experiments karo on [console.anthropic.com](https://console.anthropic.com/) taake behavior changes samajh aayein.

---

### c. Chain of Thought (CoT) Prompting ("Think Step by Step")

**Explanation (Roman Urdu):**  
Chain of Thought (CoT) prompting mein LLM ko step-by-step reasoning ke liye kaha jata hai, usually “Let’s think step by step” phrase ke saath. Yeh complex tasks, jaise math ya logical problems, ke liye ideal hai. Temperature=0 ke saath use karne se consistent results milte hain.

**Example:**  
- **Prompt:** “Solve 5x + 3 = 18. Let’s think step by step. (Temperature=0)”  
- **Output:**  
  ```
  Step 1: 5x + 3 = 18
  Step 2: Subtract 3 from both sides: 5x = 15
  Step 3: Divide both sides by 5: x = 3
  Final Answer: x = 3
  ```  
- **Explanation:** CoT step-by-step reasoning ko force karta hai, ensuring accuracy.

**Study Tip:** CoT prompts ke liye math ya reasoning questions try karo on Grok with Thinking Mode aur Temp=0.

---

### d. Self-Consistency Prompting (Multiple Paths, Pick Common Answer)

**Explanation (Roman Urdu):**  
Self-Consistency mein LLM se ek hi sawal ke multiple outputs generate kiye jate hain, aur phir sab se common ya consistent jawab choose kiya jata hai. Yeh accuracy barhata hai, especially ambiguous tasks mein.

**Example:**  
- **Prompt:** “Ek item 500 PKR ka hai, 15% discount ke baad price kya hoga? 3 baar calculate karo aur common jawab do.”  
- **Output:**  
  ```
  Attempt 1: 15% of 500 = 75, 500 - 75 = 425 PKR
  Attempt 2: 500 × 0.85 = 425 PKR
  Attempt 3: 500 - (500 × 0.15) = 425 PKR
  Common Answer: 425 PKR
  ```  
- **Explanation:** Multiple calculations se consistent jawab milta hai.

**Study Tip:** Self-Consistency ke liye ambiguous questions (jaise discounts) test karo on ChatGPT, multiple runs ke saath.

---

### e. Step-Back Prompting (General Question First)

**Explanation (Roman Urdu):**  
Step-Back prompting mein pehle ek general sawal poocha jata hai taake broader context samajh aaye, phir specific task solve kiya jata hai. Yeh complex problems ke liye useful hai jahan background knowledge zaroori hai.

**Example:**  
- **Prompt:** “Pehle bataye ke UI design ke principles kya hain, phir ek login page ka UI redesign karein.”  
- **Output:**  
  ```
  UI Principles: Simplicity, consistency, clarity.
  Redesign: Login page mein clean layout, bold buttons, aur minimal colors use karein…
  ```  
- **Explanation:** General question (UI principles) specific task (redesign) ko ground karta hai.

**Study Tip:** Step-Back prompts ke liye complex tasks (jaise UI design, policy analysis) try karo on Claude.

---

### f. ReAct Prompting (Reasoning + Actions/Tools)

**Explanation (Roman Urdu):**  
ReAct (Reasoning + Action) prompting mein LLM reasoning ke saath actions (jaise tool calls ya external data fetch) combine karta hai. Yeh dynamic tasks ke liye ideal hai jahan external input chahiye.

**Example:**  
- **Prompt:** “Ek product ke reviews analyze karo. Pehle sentiment tool se data fetch karo, phir summarize karo.”  
- **Output:**  
  ```
  [Action]: Sentiment tool se data fetch kiya: 60% positive, 40% negative.
  [Reasoning]: Positive reviews design ko pasand karte hain, negative reviews speed issues batate hain.
  [Summary]: Product design acha hai lekin speed improve karna hoga.
  ```  
- **Explanation:** ReAct reasoning aur tool actions ko integrate karta hai.

**Study Tip:** ReAct prompts ke liye API-based tasks test karo on Gemini ya Grok, tool integration simulate karke.

---

### g. Tree of Thoughts (ToT) Prompting (Branching for Complex Decisions)

**Explanation (Roman Urdu):**  
Tree of Thoughts (ToT) prompting mein LLM multiple reasoning paths explore karta hai, jaise ek decision tree, aur best path choose karta hai. Yeh complex decision-making tasks ke liye hai, jaise strategy planning.

**Example:**  
- **Prompt:** “Ek marketing campaign ke liye 3 strategies socho, har ek ke pros/cons analyze karo, aur best choose karo.”  
- **Output:**  
  ```
  Strategy 1: Social media ads
  - Pros: Wide reach
  - Cons: High cost
  Strategy 2: Email marketing
  - Pros: Targeted
  - Cons: Lower engagement
  Strategy 3: Influencer marketing
  - Pros: High trust
  - Cons: Limited control
  Best: Influencer marketing (high trust, good ROI).
  ```  
- **Explanation:** ToT multiple options explore karta hai aur best select karta hai.

**Study Tip:** ToT prompts ke liye planning tasks (jaise marketing, budgeting) test karo on Grok with Thinking Mode.

---

## 3. Tips for Prompting Techniques

**Explanation (Roman Urdu):**  
- **“Let’s think step by step” with Temp=0:** Yeh CoT prompts ke liye ideal hai kyunki low temperature consistent aur accurate reasoning deta hai.  
- **Clear Instructions:** Har technique mein specific verbs aur formats use karo.  
- **Match Technique to Task:** Zero-shot simple tasks ke liye, few-shot structured tasks ke liye, aur advanced techniques complex problems ke liye.

**Example:**  
- **Prompt:** “Solve 3x + 5 = 14. Let’s think step by step. (Temperature=0)”  
- **Output:**  
  ```
  Step 1: 3x + 5 = 14
  Step 2: Subtract 5: 3x = 9
  Step 3: Divide by 3: x = 3
  Final Answer: x = 3
  ```  
- **Explanation:** Temp=0 ensures consistent, error-free steps.

**Study Tip:** “Let’s think step by step” wala phrase math aur logical tasks ke liye Grok pe Temp=0 ke saath try karo.

---

## Practice Questions for Exam Prep (Roman Urdu)

1. **Zero-shot prompting kya hai?**  
   - **Jawab:** Direct sawal bina examples ke.  
   - **Example:** “Pakistan ka capital kya hai?” → “Islamabad.”  

2. **Few-shot prompting mein kitne examples dete hain?**  
   - **Jawab:** 3–5 examples.  
   - **Example:** Sentiment classification ke liye 3 examples dete hain.  

3. **CoT prompting ka faida kya hai?**  
   - **Jawab:** Step-by-step reasoning se accuracy barhti hai.  
   - **Example:** “Solve 5x + 3 = 18” → Step-by-step x = 3.  

4. **ReAct prompting kya combine karta hai?**  
   - **Jawab:** Reasoning aur actions (tool calls).  
   - **Example:** Sentiment tool se data fetch karke summarize karna.  

5. **ToT prompting kis liye best hai?**  
   - **Jawab:** Complex decision-making ke liye.  
   - **Example:** Marketing strategies ka comparison aur best choice.

**Study Tips (Roman Urdu):**  
- **Practice:** Har technique ke liye prompts banaye aur test karo on grok.com, [platform.openai.com](https://platform.openai.com/), ya [aistudio.google.com](https://aistudio.google.com/).  
- **Memorize:** Zero-shot, one-shot, few-shot, aur advanced techniques ke differences yaad karo.  
- **Examples:** Syllabus ke examples (jaise ReAct discount prompt) analyze karo aur improve karo.  
- **Tools:** Grok ke Thinking Mode use karo CoT aur ToT ke liye, aur Gemini pe multi-modal prompts test karo.

