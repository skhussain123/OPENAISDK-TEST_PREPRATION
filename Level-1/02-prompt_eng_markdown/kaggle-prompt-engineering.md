
# Introduction
Jab hum kisi bari language model ke input aur output ke baare mein sochte hain, toh ek text prompt (kabhi kabhi doosre modalities jaise tasveeri prompts ke saath) woh input hota hai jo model kisi khaas output ki prediction ke liye istemal karta hai. Aap ko data scientist ya machine learning engineer hone ki zarurat nahi – har koi prompt likh sakta hai. Lekin, sab se zyada muasar prompt banana thora mushkil ho sakta hai. Aap ke prompt ke kai pehlu uski kaamyaabi ko mutasir karte hain: aap jo model istemal karte hain, us model ka training data, model ki configurations, aap ke lafz ka chunao, andaaz aur lehja, dhancha, aur context – yeh sab ahem hain. Is liye, prompt engineering ek baar baar dohrane wala amal hai. Na kaafi prompts ghair wazeh ya ghalat jawabat ka sabab ban sakte hain, aur model ki maana khiz output dene ki salahiyat mein rukawat daal sakte hain.


Jab aap Gemini chatbot ke saath baat karte hain, aap asal mein prompts likhte hain. Lekin yeh whitepaper Gemini model ke liye prompts likhne par focus karta hai jo Vertex AI ke andar ya API ke zariye istemal hota hai, kyunki model ko seedha prompt karne se aap ko temperature jaise configurations tak rasai milti hai.
<br><br>
Yeh whitepaper prompt engineering ko tafseel se discuss karta hai. Hum mukhtalif prompting techniques dekhen ge jo aap ko shuruat karne mein madad den ge, aur tips aur behtareen amalon ka tabadla karenge taake aap prompting mein mahir ban saken. Hum yeh bhi discuss karenge ke prompts banate waqt aap ko kin chunautiyon ka samna ho sakta hai.


Yaad rakhein ke ek LLM kaise kaam karta hai; yeh ek prediction engine hai. Model sequential text ko input ke taur par leta hai aur phir us data ke bunyad par jo uski training mein diya gaya tha, yeh predict karta hai ke agla token kya hona chahiye. LLM is tarah se bar bar kaam karta hai, pehle predict kiya gaya token sequential text ke akhir mein jod kar agle token ki prediction karta hai. Agle token ki prediction purane tokens aur LLM ki training ke dauraan dekhi gayi cheezon ke rishte par mabni hoti hai.
<br><br>
Jab aap ek prompt likhte hain, aap LLM ko sahi sequence ke tokens predict karne ke liye tayyar kar rahe hote hain. Prompt engineering yeh amal hai ke behtar tareen prompts design kiye jayen jo LLMs ko durust outputs dene ke liye rahnumai karen. Is amal mein behtareen prompt dhoondhne ke liye tajurbat kiye jate hain, prompt ki lambai ko behtar banaya jata hai, aur task ke mutabiq prompt ke likhne ka andaaz aur dhancha ka jaiza liya jata hai. Natural language processing aur LLMs ke zariye, ek prompt woh input hai jo model ko jawab ya prediction banane ke liye diya jata hai.


Yeh prompts mukhtalif tarah ke samajh aur paidaish ke kaamon ke liye istemal kiye ja sakte hain, jaise ke text summarization, maloomat ka ikhraj, sawal o jawab, text classification, zabaan ya code ka tarjuma, code generation, aur code documentation ya reasoning.
Aap Google ke prompting guides²,³ ka hawala de sakte hain jin mein sada aur muasar prompting ki misalein di gayi hain.
Prompt engineering ke dauraan, aap pehle ek model chunenge. Prompts ko aap ke makhsoos model ke liye behtar banana hoga, chaahe aap Vertex AI mein Gemini language models, GPT, Claude, ya koi open-source model jaise Gemma ya LLaMA istemal karen.
Prompt ke ilawa, aap ko LLM ke mukhtalif configurations ke saath bhi tajurba karna hoga.


### LLM output configuration
Jab aap apna model chun lete hain, toh aap ko model ki configuration ka faisla karna hoga. Ziada tar LLMs mukhtalif configuration options ke saath aate hain jo LLM ke output ko control karte hain. Muasar prompt engineering ke liye in configurations ko aap ke task ke mutabiq behtareen tareeke se set karna zaroori hai.

### Output length
Ek ahem configuration setting yeh hai ke jawab mein kitne tokens generate kiye jayen. Zyada tokens generate karna LLM se zyada computation mangta hai, jis se energy ka istemaal barhta hai, jawab ke waqt mein der ho sakti hai, aur kharcha bhi zyada ho sakta hai.

LLM ke output ki lambai kam karna yeh nahi karta ke LLM apne output ko stylistically ya textually zyada mukhtasir banaye, balki yeh sirf LLM ko rok deta hai jab token ki hadd poori ho jati hai. Agar aap ko chhota output chahiye, toh aap ko apna prompt bhi us ke mutabiq design karna hoga.
<br><br>
Output ki lambai ki pabandi khas tor par kuch LLM prompting techniques, jaise ReAct, ke liye zaroori hai, jahan LLM aap ke chahiye wale jawab ke baad bekaar tokens generate karta rehta hai.
<br><br>
Yeh yaad rakhein ke zyada tokens generate karna LLM se zyada computation mangta hai, jis se energy ka istemaal barhta hai, jawab ke waqt mein der ho sakti hai, aur kharcha bhi zyada hota hai.

### Sampling controls
LLMs officially ek token predict nahi karte. Balki, LLMs yeh predict karte hain ke agla token kya ho sakta hai, aur LLM ke vocabulary mein har token ko ek probability di jati hai. In token probabilities ko phir sample kiya jata hai taake yeh tay kiya ja sake ke agla token kya hoga.
<br><br>
Temperature, top-K, aur top-P sab se zyada common configuration settings hain jo yeh tay karte hain ke predict kiye gaye token probabilities ko kaise process kiya jaye taake ek single output token chuna ja sake.


### Temperature
Temperature token selection mein randomness ki degree ko control karta hai. Kam temperature wale prompts ke liye behtar hote hain jo zyada deterministic jawab chahte hain, jabke zyada temperature zyada mukhtalif ya ghair mutawaqo natayej paida kar sakte hain. 0 temperature (greedy decoding) deterministic hota hai: hamesha sab se zyada probability wala token chuna jata hai (lekin yeh note karein ke agar do tokens ki probability barabar ho, toh tiebreaking ke implementation ke mutabiq temperature 0 par hamesha ek jaisa output nahi milta).
<br><br>
Zyada temperature ke qareeb hone se output zyada random ho jata hai. Aur jaise jaise temperature barhta jata hai, sab tokens agle predicted token ke liye barabar imkanat rakhte hain.
<br><br>
Gemini ka temperature control machine learning mein istemal hone wale softmax function ki tarah samjha ja sakta hai. Kam temperature setting ek kam softmax temperature (T) ki tarah hoti hai, jo ek single, pasandeeda temperature par zyada yaqeen ke saath zor deti hai. Zyada Gemini temperature setting ek zyada softmax temperature ki tarah hoti hai, jo chune gaye setting ke aas paas temperatures ki zyada range ko qabil-e-qubool banati hai. Yeh barhti hui ghair yaqeeni halat un scenarios ke liye mozoon hoti hai jahan sakht, durust temperature zaroori na ho, masalan jab creative outputs ke saath tajurba kiya ja raha ho.


### Top-K and top-P
* Top-K aur top-P (jise nucleus sampling bhi kaha jata hai) do sampling settings hain jo LLMs mein istemal hote hain taake agle predicted token ko un tokens mein se chuna jaye jin ki sab se zyada predicted probabilities hoti hain. Temperature ki tarah, yeh sampling settings generated text ki randomness aur diversity ko control karte hain.
    * Top-K sampling model ke predicted distribution mein se sab se zyada imkanat wale K tokens chunta hai. Zyada top-K hone se model ka output zyada creative aur mukhtalif hota hai; kam top-K hone se output zyada mukhtasar aur haqeeqat par mabni hota hai. Top-K ka 1 hona greedy decoding ke barabar hai.
    * Top-P sampling un top tokens ko chunta hai jin ki kul probability ek muayyan qadar (P) se zyada nahi hoti. P ki qadrein 0 (greedy decoding) se lekar 1 (LLM ke vocabulary ke sab tokens) tak hoti hain.

Top-K aur top-P ke darmiyan chunne ka sab se behtar tareeqa yeh hai ke dono tareeqon (ya dono ek saath) ke saath tajurba kiya jaye aur dekha jaye ke kaunsa tareeqa aap ke chahiye wale natayej deta hai.