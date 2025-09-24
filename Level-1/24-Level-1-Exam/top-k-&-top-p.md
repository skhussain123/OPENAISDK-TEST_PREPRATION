





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


## Top-p  vs Top-k vs Temperature
### 1. Top-p Kya Hai (Nucleus Sampling)?
Definition: Top-p sampling ek tarika hai jisme language model ek chhota sa group of words (tokens) choose karta hai jinka total probability ek specific value p se zyada hota hai. Phir us group se randomly word select hota hai.

Kaise Kaam Karta Hai:

- Model har possible word ke liye probability banata hai.
  - Words ko probability ke hisaab se sort karta hai (zyada se kam).
  - Phir wo chhota sa group chunta hai jiska combined probability p se zyada ho (jaise 0.9 ya 90%).
  - Is group se randomly word choose hota hai.
