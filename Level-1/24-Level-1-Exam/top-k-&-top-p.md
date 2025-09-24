





* Low (0.1-0.3): Math, facts, precise instructions
* Medium (0.4-0.6): General conversation, explanations
* High (0.7-0.9): Creative writing, brainstorming
Note: For gemini temprature range extends to 2. Creativity ka matlab hai “naya sochna” aur “naye tareeke se kisi cheez ko banana ya hal karna”.

### Temperature Types
| Type                   | Range                             | Kya hota hai / output kaisa hota hai                                                                                        | Best use-case                                                                             |
| ---------------------- | --------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| **Low Temperature**    | \~ **0.0 – 0.3**                  | Output zyada deterministic ya predictable hota hai. Model mostly sabse probable options choose karega, kam randomness hogi. | Factual answers, instructions, conversions, code generation, jahan consistency zaroori ho |
| **Medium Temperature** | \~ **0.4 – 0.6**                  | Thodi creativity aur thodi predictability mix hogi. Output thoda varied hoga lekin jyada “weird” nahi.                      | General writing, blog, storytelling with control, balanced tasks                          |
| **High Temperature**   | \~ **0.7 – 0.9 (ya us se zyada)** | Output me zyada randomness hogi. Model kabhi low-probability words bhi choose karega. Coherence thodi gir sakti hai.        | Creative writing, poetry, brainstorming, ideas generate karna                             |

#### Comparision
| Temperature | Expect karo                                                                                               |
| ----------- | --------------------------------------------------------------------------------------------------------- |
| **0.1-0.2** | Jawab bohat seedha, predictable, kam variation; similar answers baar baar milenge.                        |
| **0.5-0.7** | Thodi creativity – thode unexpected comparisons, metaphors ya ideas; phir bhi relevant.                   |
| **0.9-1.0** | Zyada alag, creative aur kabhi kabhi unusual ya imaginative jawab; kabhi topic se thoda dur ja sakta hai. |

## Code Example with temperature
#### 1. Low Temperature (0.0 – 0.3)
- Jab output ko consistent, precise, deterministic chahiye ho.
- Jaise: translation, grammar fix, mathematical answer, data extraction, configuration generation.
- Yeh output hamesha ek hi tarah aayega ya bahut similar hoga.


#### 2. Medium Temperature (0.4 – 0.6)
- Jab thodi creativity chahiye ho, lekin output zyada unpredictable na ho.
- Jaise: blog writing, general content, storytelling jisme thoda rang-chang ho.
- Ab thoda variation aa sakti hai, lekin content easily samajh aayega.

#### 3. High Temperature (0.7 – 0.9 ya us se zyada)
- Jab aap chahte ho creative, unexpected ideas.
- Jaise: poetry, slogans, brainstorming, novel writing, imaginations.
- Ab output bahut imaginative ho sakti hai — kabhi kabhi thodi weird bhi.


---

## Top-p  vs Top-k vs Temperature
### 1. Top-p Kya Hai (Nucleus Sampling)?
Definition: Top-p sampling ek tarika hai jisme language model ek chhota sa group of words (tokens) choose karta hai jinka total probability ek specific value p se zyada hota hai. Phir us group se randomly word select hota hai.

**Kaise Kaam Karta Hai:**
- Model har possible word ke liye probability banata hai.
  - Words ko probability ke hisaab se sort karta hai (zyada se kam).
  - Phir wo chhota sa group chunta hai jiska combined probability p se zyada ho (jaise 0.9 ya 90%).
  - Is group se randomly word choose hota hai.

**Asar:**
  - Agar p chhota hai (jaise 0.5), to model sirf high-probability words chunta hai, jo output ko focused aur predictable banata hai.
  - Agar p bada hai (jaise 0.9), to zyada words shamil hote hain, jo output ko creative aur diverse banata hai, lekin shayad thoda kam coherent.
- Example: Agar p = 0.9, to model wo chhota sa group chunta hai jo 90% probability cover karta hai aur usme se randomly word select karta hai.

- top_p must be in the range [0.0, 1.0]
---
### 2. Top-k Kya Hai (k-Sampling)?
Definition: Top-k sampling mein model top k sabse zyada probable words chunta hai aur unme se randomly select karta hai.

**Kaise Kaam Karta Hai:**
- Model sab tokens ke liye probability banata hai.
- Top k tokens chunta hai jo sabse zyada probable hote hain (jaise k = 50 matlab top 50 words).
- Phir in k tokens se randomly word select hota hai.

**Asar:**
- Chhota k (jaise 10) output ko bohot focused aur predictable banata hai kyunke sirf high-probability words use hote hain.
- Bada k (jaise 100) zyada words ko shamil karta hai, jo output ko diverse banata hai lekin shayad kam coherent.
- Example: Agar k = 50, to model sirf top 50 probable words ko dekhta hai aur unme se randomly chunta hai.

---

### 3. Temperature Kya Hai?
Definition: Temperature ek parameter hai jo model ke randomness ko control karta hai.

**Kaise Kaam Karta Hai:**
- Temperature probability distribution ko modify karta hai
  - Low temperature (jaise 0.7): Probabilities ko sharp karta hai, high-probability words ko aur zyada likely banata hai. Output focused aur predictable hota hai.
  - High temperature (jaise 1.5): Probabilities ko flatten karta hai, kam probable words ko bhi chance deta hai. Output creative hota hai lekin shayad kam coherent.
  - Temperature = 1.0: Model ki original probability distribution use hoti hai bina kisi change ke.

- Asar: Temperature globally randomness ko control karta hai, jo output ke creativity aur coherence ke balance ko set karta hai.

---

## Top-p, Top-k aur Temperature Ko Combine
### Scenario 1: Top-p + Top-k + Temperature
- Kaise Kaam Karta Hai:
  - Pehle Top-k apply hota hai: Model top k probable tokens chunta hai.
  - Phir Top-p apply hota hai: In k tokens se, wo chhota sa group chunta hai jiska combined probability p se zyada ho.
  - Aakhir mein, temperature in final tokens ke probabilities ko adjust karta hai aur phir randomly word select hota hai.

**Asar:**
- Top-k token pool ko fixed size tak limit karta hai.
- Top-p us pool ko probability ke hisaab se aur chhota karta hai.
- Temperature final set mein randomness ko control karta hai.
- Yeh combination coherence aur creativity ke beech balance banati hai.

**Output:**
- Low Top-k (jaise 10), low Top-p (jaise 0.5), low temperature (jaise 0.7): Output bohot focused, predictable, aur coherent hoga.
- High Top-k (jaise 100), high Top-p (jaise 0.9), high temperature (jaise 1.5): Output zyada diverse aur creative hoga, lekin shayad thoda kam coherent.
- Top-p aur Top-k dono saath mein thodi redundancy create kar sakte hain, lekin yeh fine control dete hain.

### Scenario 2: Sirf Top-p + Temperature
**Kaise Kaam Karta Hai:**
- Top-p ek chhota sa group chunta hai jiska combined probability p se zyada ho.
- Temperature is group ke probabilities ko adjust karta hai phir randomly word select hota hai.

**Asar:**
- Top-p token pool ko dynamically adjust karta hai context ke hisaab se.
- Temperature randomness ko fine-tune karta hai.
- Low Top-p (jaise 0.5), low temperature (jaise 0.7): Output bohot focused aur predictable hoga.
- High Top-p (jaise 0.9), high temperature (jaise 1.5): Output zyada creative aur diverse hoga.

**Output:**
- Yeh combination flexible hai aur aksar behtar hota hai kyunke Top-p context ke hisaab se token pool ko adjust karta hai. Output coherent hota hai lekin thodi creativity bhi hoti hai, depending on settings

### Scenario 3: Sirf Top-k + Temperature
**Kaise Kaam Karta Hai:**
- Top-k top k probable tokens chunta hai.
- Temperature in k tokens ke probabilities ko adjust karta hai aur phir randomly word select hota hai.

**Asar:**
- Top-k token pool ko fixed rakhta hai, chahe context kaisa bhi ho.
- Temperature is fixed set mein randomness ko control karta hai.
- Low Top-k (jaise 10), low temperature (jaise 0.7): Output bohot focused aur predictable hoga.
- High Top-k (jaise 100), high temperature (jaise 1.5): Output zyada diverse hoga lekin shayad thoda kam coherent.

**Output:**
- Yeh combination predictable hota hai lekin Top-p ki tarah flexible nahi. Consistent output ke liye achha hai lekin context-specific nuances miss kar sakta hai.

### Scenario 4: Top-p + Top-k + Temperature (Teeno Saath)
**Kaise Kaam Karta Hai:**
- Pehle Top-k top k tokens chunta hai.
- Phir Top-p usme se chhota group chunta hai jiska probability p se zyada ho.
- Temperature final probabilities ko adjust karta hai aur randomly word select hota hai.

**Asar:**
- Yeh bohot controlled setup hai:
  - Top-k pehla filter hai, token pool ko limit karta hai.
  - Top-p usko aur refine karta hai probability ke hisaab se.
  - Temperature randomness ko adjust karta hai.
- Agar k aur p dono low hain, to output bohot restricted ho sakta hai. Agar dono high hain aur temperature bhi high hai, to output creative lekin kam coherent ho sakta hai.
