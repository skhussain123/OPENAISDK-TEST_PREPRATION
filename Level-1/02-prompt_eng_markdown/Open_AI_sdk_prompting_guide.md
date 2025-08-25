
---

GPT-4.1 models ka family GPT-4o se ek bara qadam aagay hai, khaas taur pe coding, instructions follow karne aur lambi context samajhne me. Is prompting guide me hum ne bohot se important tips ikatthi ki hain jo internal testing se mili hain, taa ke developers is naye model family ki behtareen abilities ka poora faida utha saken.

GPT-4.1 par ab bhi wohi typical best practices apply hoti hain jaise ke context examples dena, instructions ko specific aur clear banana, aur planning induce karna prompts ke zariye taa ke model ki intelligence maximize ho. Lekin, hum expect karte hain ke is model ka poora faida uthane ke liye thoda prompt migration zaroori hoga. GPT-4.1 ko zyada closely aur literally instructions follow karne ke liye train kiya gaya hai, jabke pehle models zyada liberal tareeqe se user aur system prompts se intent infer karte thay. Iska matlab yeh bhi hai ke GPT-4.1 bohot steerable hai aur agar prompts achi tarah specify kiye gaye ho to yeh turant response deta hai. Agar model ka behavior aapki expectation se different aaye, to ek seedhi aur clear sentence jo aapke desired behavior ko explain kare, aam tor pe kafi hota hai model ko sahi raaste par steer karne ke liye.

Mazeed examples ke liye niche diye gaye prompts ko dekhiye aur yaad rakhiye ke yeh guidance wide level par apply hoti hai lekin har case me same result nahi deti. AI engineering waise bhi ek empirical discipline hai aur large language models by nature nondeterministic hote hain. Is guide ko follow karne ke sath sath hum recommend karte hain ke informative evals banayein aur bar bar iterate karein taa ke aapko yaqeen ho ke aapke prompt engineering changes waqai aapke use case me faida de rahe hain.

## 1. Agentic Workflows

GPT-4.1 agentic workflows banane ke liye ek bohot acha model hai. Is model ki training ke dauran humne mukhtalif qisam ke agentic problem-solving trajectories par focus kiya, aur jo agentic harness banayi gayi hai woh SWE-bench Verified test par state-of-the-art performance achieve karti hai. Ye model non-reasoning models ke liye 55% problems solve karta hai.

**System Prompt Reminders**

GPT-4.1 ki agentic capabilities ka poora faida uthane ke liye, hum recommend karte hain ke har agent prompt me teen qisam ke reminders shamil kiye jayein.

#### 1. Persistence
Ye prompts specially agentic coding workflows ke liye optimized hain, lekin inhe general agentic use cases me bhi asaani se modify kiya jaa sakta hai.
```bash
You are an agent - please keep going until the user’s query is completely resolved, 
before ending your turn and yielding back to the user. 
Only terminate your turn when you are sure that the problem is solved.
```

#### 2. Tool-calling
Ye model ko encourage karta hai ke woh apne tools ka poori tarah se istemal kare, aur is tarah se hallucinate karne (galat cheez soch lena) ya andaza lagane ki probability kam ho jati hai.

```bash
Agar aapko user ki request se related file content ya codebase structure ke baare me surety na ho, 
to apne tools ka istemal karke files ko read karo aur relevant information gather karo. 
Kabhi bhi andaza mat lagao ya khud se jawab create mat karo.
```

#### 3. Planning [optional]
Agar chaha jaye to, ye ensure karta hai ke model har tool call se pehle clearly plan banaye aur us tool call ke outcomes par reflect kare. Ye approach is baat ko rokti hai ke model sirf ek chain of tool calls bana kar task complete kare, bina kisi soch-vichar ke.

```bash
Aapko har function call se pehle bohot detail me planning karni hogi, aur pehle ke function calls ke results par bhi ghor karna hoga. Sirf function calls ka chain bana kar poora process mat karo, kyunki is se aapki problem solve karne ki ability aur insightful soch kamzor ho sakti hai.
```
GPT-4.1 ko aise train kiya gaya hai ke woh user instructions aur system prompts dono ka bohot qareeb se follow kare, khaaskar agentic setting me.
Model ne in teen simple instructions ko strictly follow kiya aur hamara internal SWE-bench Verified score lagbhag 20% barh gaya. Isi liye hum strongly recommend karte hain ke har agent prompt ki shuruaat clear reminders ke sath ki jaye jo upar di gayi teen categories cover karte hain.
Kul mila kar, humein ye teen instructions model ko ek chatbot jaisa banne ke bajaye ek zyada “eager” agent me transform karte hue nazar aaye, jo interaction ko khud-ba-khud aur independently aage le kar jata hai.
