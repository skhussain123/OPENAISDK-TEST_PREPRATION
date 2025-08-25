
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

### Tool Calls
Pichlay models ke muqable mein, GPT-4.1 ko zyada training mili hai tools ko effectively use karne par jo OpenAI API request mein arguments ki tarah diye jate hain. Hum developers ko encourage karte hain ke wo sirf tools field ka use karein tools pass karne ke liye, bajaye iske ke manually tool descriptions apne prompt mein inject karein aur tool calls ke liye alag parser likhein, jaisa kuch log pehle karte rahe hain. Ye tareeqa sabse behtareen hai errors ko kam karne ke liye aur ye ensure karne ke liye ke model distribution mein rahe jab tool-calling trajectories chal rahi hoon. Humari apni experiments mein, humne dekha ke SWE-bench Verified pass rate mein 2% izafa hua jab API-parsed tool descriptions ka use kiya gaya bajaye manually schemas inject karne ke system prompt mein.

Developers ko chahiye ke tools ka naam clearly rakhein taa ke unka purpose samajh aaye aur "description" field mein ek clear aur detailed description add karein. Isi tarah, har tool param ke liye achhi naming aur descriptions use karni chahiye taa ke usage sahi tareeqe se ho. Agar aapka tool thoda complicated hai aur aap tool usage ke examples dena chahte hain, toh hum recommend karte hain ke aap apne system prompt mein ek # Examples section banayein aur examples wahan daalein, bajaye iske ke unhein "description" field mein daalain — jo ke thorough rehni chahiye lekin concise bhi. Examples dena faida mand ho sakta hai yeh batane ke liye ke kab tools use karne hain, user text ko tool calls ke saath include karna hai ya nahi, aur kin inputs ke liye kaunse parameters appropriate hain. Yaad rakhein ke aap “Generate Anything” ka use kar sakte hain Prompt Playground mein apne naye tool definitions ke liye ek acha starting point lene ke liye.


### Prompting-Induced Planning & Chain-of-Thought

Jaisa ke pehle bhi mention hua hai, developers optionally GPT-4.1 par banaye gaye agents ko prompt kar sakte hain taa ke wo tool calls ke darmiyan plan aur reflect karein, bajaye iske ke tools ko silently ek continuous sequence mein call karein. GPT-4.1 ek reasoning model nahi hai — iska matlab ye hai ke ye answer dene se pehle koi internal chain of thought produce nahi karta — lekin prompt mein, developer model ko induce kar sakta hai taa ke wo explicitly step-by-step plan banaye, jo ke Planning prompt component ki kisi bhi variant ke zariye kiya ja sakta hai (jaise upar dikhaya gaya hai). Isay aap aise samajh sakte hain jaise model “soch ko zubaan deta ho.”

Humari experimentation mein SWE-bench Verified agentic task par, explicit planning induce karne se pass rate mein 4% ka izafa hua.

#### Sample Prompt: SWE-bench Verified
Neeche hum woh agentic prompt share kar rahe hain jo humne SWE-bench Verified mein highest score hasil karne ke liye use kiya. Ye prompt workflow aur problem-solving strategy ke detailed instructions deta hai. Ye general pattern kisi bhi agentic task ke liye use kiya ja sakta hai.

```bash
**Code Example Explanation (Roman Urdu):**

Is code mein OpenAI ka client banaya gaya hai jo API key ke sath initialize hota hai.  
Ye ek **System Prompt (SYS_PROMPT_SWEBENCH)** define karta hai jo AI ko guide karta hai  
ke problem solving kaise karni hai step by step.  

---

### SYS_PROMPT_SWEBENCH (Roman Urdu Translation)

Aapko ek open-source repository se issue fix karne ka task milega.  

- Aapki soch thorough honi chahiye aur chahe lambi bhi ho to koi masla nahi.  
- Har action se pehle aur baad mein aap step by step soch sakte hain.  
- Aapko iterate karna hoga aur problem solve hone tak rukna nahi.  
- Internet ki zaroorat nahi, saara kaam aap `/testbed` folder se kar sakte ho.  
- Jab tak problem solve na ho, apni turn end mat karo.  
- Har tool call ko actual execute karo, bas keh kar turn khatam na karo.  

### Workflow

#### High-Level Problem Solving Strategy
1. Maslay ko gehrai se samajhna.  
2. Codebase investigate karna.  
3. Clear aur step-by-step plan banana.  
4. Fix ko chhote steps mein implement karna.  
5. Debug karna agar issue aaye.  
6. Har change ke baad test chalana.  
7. Iterate karna jab tak root cause fix na ho.  
8. Reflection aur final validation karna.  

---

### Python Tool Description (Roman Urdu)

Ye function Python code ya terminal commands execute karta hai  
stateful Jupyter notebook environment mein.  

- Internet access disable hai.  
- Aap `apply_patch` command ka use karke files mein patch apply kar sakte ho.  
- Format specific hai:  

```bash
%%bash
apply_patch <<"EOF"
*** Begin Patch
[YOUR_PATCH]
*** End Patch
EOF
```