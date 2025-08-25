
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


### Putting it all together
Top-K, top-P, temperature, aur generate kiye jane wale tokens ki tadad ke darmiyan chunna makhsoos application aur chahiye wale natayej par munhasir hai, aur yeh sab settings ek doosre par asar andaz hote hain. Yeh bhi zaroori hai ke aap samjhein ke aap ka chuna hua model in mukhtalif sampling settings ko kaise mila kar kaam karta hai.
<br><br>
Agar temperature, top-K, aur top-P sab maujood hain (jaise Vertex Studio mein), toh woh tokens jo top-K aur top-P dono ke mayar par pora utarte hain, agle predicted token ke liye ummeedwar hote hain, aur phir temperature ka istemal karke in tokens mein se sample kiya jata hai jo top-K aur top-P ke mayar par pora utarte hain. Agar sirf top-K ya top-P maujood ho, toh wahi rawayya hota hai lekin sirf ek top-K ya P setting ka istemal hota hai.
<br><br>
Agar temperature maujood nahi hai, toh jo tokens top-K aur/ya top-P ke mayar par pora utarte hain, un mein se randomly chun kar ek agla predicted token banaya jata hai.
Ek sampling configuration ki qadar ke hadd tak jane par, woh ek sampling setting doosri configuration settings ko ya toh radd kar deti hai ya be-muhim ho jati hai.


* Agar aap temperature ko 0 par set karte hain, toh top-K aur top-P be-muhim ho jate hain – sab se zyada probability wala token agla predicted token ban jata hai. Agar aap temperature ko bohot zyada (1 se ooper, amuman 10 tak) set karte hain, toh temperature be-muhim ho jata hai aur jo tokens top-K aur/ya top-P ke mayar se guzarte hain, un mein se randomly sample kiya jata hai taake agla predicted token chuna jaye.
* Agar aap top-K ko 1 par set karte hain, toh temperature aur top-P be-muhim ho jate hain. Sirf ek token top-K ke mayar se guzarta hai, aur wahi token agla predicted token hota hai. Agar aap top-K ko bohot zyada set karte hain, jaise LLM ke vocabulary ke size tak, toh koi bhi token jis ki nonzero probability ho ke woh agla token ho, woh top-K ke mayar par pora utarta hai aur koi bhi token chhanta nahi hai.
* Agar aap top-P ko 0 (ya bohot chhoti qadar) par set karte hain, toh ziada tar LLM sampling implementations sirf sab se zyada probability wale token ko top-P ke mayar ke liye dekhen ge, jis se temperature aur top-K be-muhim ho jate hain. Agar aap top-P ko 1 par set karte hain, toh koi bhi token jis ki nonzero probability ho ke woh agla token ho, woh top-P ke mayar par pora utarta hai, aur koi bhi token chhanta nahi hai.


Ek aam shuruaati nuqta ke taur par, 0.2 ka temperature, 0.95 ka top-P, aur 30 ka top-K aap ko munasib aur thori si creativity wale natayej dega jo zyada hadd se barh kar creative nahi honge. Agar aap khas tor par creative natayej chahte hain, toh 0.9 ke temperature, 0.99 ke top-P, aur 40 ke top-K se shuru karen. Aur agar aap kam creative natayej chahte hain, toh 0.1 ke temperature, 0.9 ke top-P, aur 20 ke top-K se shuru karen. Aakhir mein, agar aap ka task hamesha ek hi sahi jawab mangta hai (masalan, math ke sawal ka jawab), toh 0 ke temperature se shuru karen.
<br><br>

**NOTE:** Zyada azadi (zyada temperature, top-K, top-P, aur output tokens) ke saath, LLM aisa text generate kar sakta hai jo kam relevant ho.
<br><br>

**WARNING:** Kya aap ne kabhi koi jawab dekha hai jo bari miqdaar mein filler words ke saath khatam hota hai? Ise "repetition loop bug" bhi kaha jata hai, jo Large Language Models mein ek aam masla hai jahan model ek chakkar mein phans jata hai, bar bar wahi (filler) lafz, jumlai, ya jumla structure generate karta rehta hai, aksar ghalat temperature aur top-K/top-P settings ki wajah se yeh masla barhta hai. Yeh kam aur zyada dono temperature settings par ho sakta hai, lekin mukhtalif wajuhaat se. Kam temperature par, model zyada deterministic ho jata hai, sakht taur par sab se zyada probability wale raaste par chalta hai, jo agar yeh raasta pehle generate kiye gaye text par wapas aaye toh loop ban sakta hai. Is ke baraks, zyada temperature par, model ka output zyada random ho jata hai, jis se yeh imkan barh jata hai ke randomly chuna gaya lafz ya jumla bil-akhir pehle ke state mein wapas aaye, aur bari miqdaar mein maujood options ki wajah se loop ban jaye. Dono halaat mein, model ka sampling process "phas jata hai," jis ke nateeje mein monotonous aur ghair mufeed output banta hai jab tak output window bhar nahi jata. Ise hal karne ke liye aksar temperature aur top-K/top-P qadron ke saath dhyan se tajurba karna parta hai taake determinism aur randomness ke darmiyan behtareen tawazun mil sake.

### Prompting techniques
LLMs ko instructions follow karne ke liye tune kiya jata hai aur unhe bari miqdaar mein data par train kiya jata hai taake woh prompt ko samajh saken aur jawab generate kar saken. Lekin LLMs mukammal nahi hote; aap ka prompt text jitna wazeh hoga, LLM ke liye agla mumkin text predict karna utna hi behtar hoga. Is ke ilawa, kuch khaas techniques jo LLMs ki training aur kaam karne ke tareeqe ka faida uthati hain, aap ko LLMs se relevant natayej hasil karne mein madad deti hain.
<br><br>
Ab jab hum samajh chuke hain ke prompt engineering kya hai aur is ke liye kya zaroori hai, toh chaliye kuch ahem prompting techniques ki misaalon mein ghotay lagate hain.


### General prompting / zero shot
Ek zero-shot prompt sab se sada qisam ka prompt hai. Yeh sirf ek task ka tashreeh aur kuch text deta hai taake LLM shuruat kar sake. Yeh input kuch bhi ho sakta hai: ek sawal, ek kahani ka aghaaz, ya hidayat. Zero-shot ka naam is liye hai kyunki is mein koi misaal nahi di jati. Chaliye Vertex AI Studio (for Language) in Vertex AI ka istemal karte hain, jo prompts test karne ke liye ek playground faraham karta hai. Table 1 mein, aap ko movie reviews classify karne ke liye ek zero-shot prompt ki misaal dikhe gi.
<br><br>
Neeche diya gaya table format prompts ko document karne ka ek behtareen tareeqa hai. Aap ke prompts shayad kai dafa tabdeel honge pehle ke woh codebase mein shamil hon, is liye apne prompt engineering ke kaam ko ek disciplined aur munazzam tareeke se track karna zaroori hai. Is table format, prompt engineering ke kaam ko track karne ki ahmiyat, aur prompt development ke amal ke bare mein mazeed tafseel is chapter ke baad ke Best Practices section mein hai (“Document the various prompt attempts”).
Model ka temperature ek kam number par set karna chahiye, kyunki koi creativity ki zarurat nahi, aur hum gemini-pro ke default top-K aur top-P qadron ka istemal karte hain, jo in dono settings ko asal mein band kar deta hai (dekhiye ‘LLM Output Configuration’ ooper). Generated output par tawajjo dein. Disturbing aur masterpiece jaisay alfaaz ek hi jumle mein istemal hone ki wajah se prediction ko thora zyada mushkil kar sakte hain.
![dfds](./one.PNG)
When zero-shot doesn’t work, you can provide demonstrations or examples in the prompt,
which leads to “one-shot” and “few-shot” prompting. General prompting / zero shot


### One-shot & few-shot
Ek one-shot prompt ek hi misaal deta hai, is liye is ka naam one-shot hai. Is ka maqsad yeh hai ke model ko ek misaal di jaye jis ki naqal kar ke woh task ko behtar tareeke se mukammal kar sake.

* Ek **few-shot** prompt model ko kai misaalein deta hai. Yeh tareeqa model ko ek pattern dikhata hai jis ki woh pairvi karta hai. Yeh idea one-shot jaisa hai, lekin chahiye wale pattern ki kai misaalein model ke pattern follow karne ke imkanat ko barhati hain.

* **Few-shot** prompting ke liye kitni misaalon ki zarurat hoti hai, yeh kuch cheezon par munhasir hai, jaise task ki complexity, misaalon ki quality, aur aap ke istemal karda generative AI (gen AI) model ki salahiyatein. Ek aam qayeda ke taur par, few-shot prompting ke liye kam az kam teen se paanch misaalein istemal karni chahiyein. Haan, zyada complex tasks ke liye aap ko shayad zyada misaalon ki zarurat ho, ya aap ke model ki input length limitation ki wajah se kam misaalein istemal karni par sakti hain.
<br><br>
Table 2 mein ek few-shot prompt ki misaal di gayi hai, chaliye hum pehle jaisi gemini-pro model configuration settings ka istemal karte hain, siwaye is ke ke token limit ko barhaya jaye taake zyada lambay jawab ki zarurat ko pura kiya ja sake.

![dfds](./two.PNG)
![dfds](./three.PNG)
Jab aap apne prompt ke liye misalein chunte hain, to aisi misalein istemal karein jo us kaam se mutalliq hon jo aap anjam dena chahte hain. Misalein mukhtalif, aala miyaar ki, aur achi tarah likhi honi chahiye. Ek chhoti si galti bhi model ko uljha sakti hai aur is ke n natije mein matlooba output nahi milega.
<br><br>
Agar aap aisi output paida karne ki koshish kar rahe hain jo mukhtalif inputs ke liye mazboot ho, to apni misalon mein edge cases shamil karna zaroori hai. Edge cases aisi inputs hain jo ghair mamooli ya ghair mutawaqqe hain, lekin model ko phir bhi unhein sambhalne ke qabil hona chahiye.
