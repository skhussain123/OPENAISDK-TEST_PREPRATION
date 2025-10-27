# MCQs on APIs (Beginner-Friendly Guide)
## Questions

**Q1. What is an API in simple terms?**  
a) A tool for building hardware  
b) A set of rules for software to communicate (correct)  
c) A programming language  
d) A database management system  

**Explanation**: An API (Application Programming Interface) is a set of rules that allows different software applications to talk to each other.

---

**Q2. Which analogy best describes an API?**  
a) A chef cooking food  
b) A waiter taking orders in a restaurant (correct)  
c) A customer eating food  
d) A kitchen stove  

**Explanation**: An API acts like a waiter, relaying requests between the client (you) and the backend (kitchen) without exposing internal details.

---

**Q3. In the weather app analogy, what represents the API?**  
a) The weather company’s servers  
b) The weather API (correct)  
c) Your phone  
d) The weather data  

**Explanation**: The weather API is the interface that connects your phone (client) to the weather company’s servers (backend).

---

**Q4. What is Postman used for in the context of APIs?**  
a) To write Python code  
b) To craft and test API requests (correct)  
c) To train AI models  
d) To manage virtual environments  

**Explanation**: Postman is a free desktop app that lets users create and test API requests and view responses.

---

**Q5. Which HTTP request type is used to fetch today’s weather for London in the guide?**  
a) POST  
b) GET (correct)  
c) PUT  
d) DELETE  

**Explanation**: The guide uses a GET request to fetch weather data from `https://api.open-meteo.com/v1/forecast`.

---

**Q6. What does the URL `https://catfact.ninja/fact` provide when called?**  
a) A random cat fact (correct)  
b) A weather forecast  
c) A payment transaction  
d) A ride-booking service  

**Explanation**: The URL `https://catfact.ninja/fact` returns a random cat fact, as shown in the guide’s real-world example.

---

**Q7. What is a key characteristic of OpenAI’s Chat Completions API?**  
a) It is stateful  
b) It is stateless (correct)  
c) It remembers conversation history automatically  
d) It includes built-in web search  

**Explanation**: The Chat Completions API is stateless, requiring the entire conversation history to be sent with each request.

---

**Q8. What must you include in every Chat Completions API request?**  
a) Only the new user input  
b) The entire conversation history (correct)  
c) A previous response ID  
d) A web search tool  

**Explanation**: Since Chat Completions is stateless, you must include the full conversation history in the `messages` parameter.

---

**Q9. Which Python library is used to interact with OpenAI’s APIs in the guide?**  
a) requests  
b) openai (correct)  
c) aiohttp  
d) flask  

**Explanation**: The guide uses the `openai` Python library to interact with OpenAI’s Chat Completions and Responses APIs.

---

**Q10. What does the following Chat Completions code do?**  
```python
response = client.chat.completions.create(
    model="gpt-4o-mini",
    messages=[{"role":"user","content":"What's the capital of France?"}]
)
```  
a) Searches the web for France’s capital  
b) Asks the model for France’s capital (correct)  
c) Stores conversation history on the server  
d) Generates an image of France  

**Explanation**: The code sends a user prompt to the `gpt-4o-mini` model, asking for the capital of France, and returns the response (Paris).

---

**Q11. What is a key feature of OpenAI’s Responses API?**  
a) It requires manual history management  
b) It is stateful and remembers conversation history (correct)  
c) It avoids built-in tools  
d) It requires more boilerplate code  

**Explanation**: The Responses API is stateful, storing conversation history server-side, so you only send new input.

---

**Q12. What do you need to include in a follow-up request to the Responses API?**  
a) The entire conversation history  
b) The previous response ID (correct)  
c) A new model name  
d) A full set of tools  

**Explanation**: The Responses API uses the `previous_response_id` to reference the conversation history for follow-up requests.

---

**Q13. Which tool is NOT built into the Responses API?**  
a) Web search  
b) File retrieval  
c) Image generation  
d) Database management (correct)  

**Explanation**: The Responses API includes tools like web search, file retrieval, and image generation, but not database management.

---

**Q14. What does the `store=True` parameter do in the Responses API?**  
a) Stores the response on the client  
b) Stores conversation history on the server (correct)  
c) Disables built-in tools  
d) Generates a new model  

**Explanation**: `store=True` enables the Responses API to save conversation history server-side for stateful interactions.

---

**Q15. Which API is recommended for learning basic LLM interactions?**  
a) Responses API  
b) Chat Completions API (correct)  
c) Weather API  
d) Cat Fact API  

**Explanation**: The guide recommends the Chat Completions API for learning basics, as it shows the full message structure.

---

**Q16. Which API is best for building a research assistant with web search?**  
a) Chat Completions API  
b) Responses API (correct)  
c) Weather API  
d) Cat Fact API  

**Explanation**: The Responses API is ideal for research assistants due to its stateful nature and built-in web search tool.

---

**Q17. Why is the Chat Completions API better for custom function tools?**  
a) It has built-in web search  
b) It allows manual function calling (correct)  
c) It stores history server-side  
d) It requires less code  

**Explanation**: The Chat Completions API supports manual function calling, giving developers control over custom tools.

---

**Q18. What is a key difference between Chat Completions and Responses APIs?**  
a) Chat Completions is stateful, Responses is stateless  
b) Responses requires less boilerplate code (correct)  
c) Chat Completions includes built-in web search  
d) Responses requires full history in each request  

**Explanation**: The Responses API requires less boilerplate code due to its stateful nature and built-in tools.

---

**Q19. What can you do with Postman’s “Code” button after sending an API request?**  
a) Train an AI model  
b) Copy code snippets in Python or other languages (correct)  
c) Create a virtual environment  
d) Modify the API server  

**Explanation**: Postman’s “Code” button generates code snippets (e.g., Python, curl) for the API request you sent.

---

**Q20. Which URL is used to fetch a random cat fact in the guide?**  
a) https://api.open-meteo.com/v1/forecast  
b) https://catfact.ninja/fact (correct)  
c) https://api.openai.com/v1/chat/completions  
d) https://stripe.com/api  

**Explanation**: The guide lists `https://catfact.ninja/fact` as the URL for fetching a random cat fact.

---

**Q21. What is the role of the `messages` parameter in the Chat Completions API?**  
a) To specify built-in tools  
b) To provide conversation history (correct)  
c) To set the previous response ID  
d) To enable image generation  

**Explanation**: The `messages` parameter in Chat Completions API contains the conversation history, including user and model messages.

---

**Q22. How does the Responses API handle follow-up questions?**  
a) By requiring the full conversation history  
b) By using the previous response ID (correct)  
c) By resetting the conversation  
d) By disabling tools  

**Explanation**: The Responses API uses `previous_response_id` to reference prior conversation history for follow-ups.

---

**Q23. Which API requires more manual control over conversation history?**  
a) Responses API  
b) Chat Completions API (correct)  
c) Weather API  
d) Cat Fact API  

**Explanation**: Chat Completions is stateless, requiring developers to manually include conversation history in each request.

---

**Q24. What is a typical use case for the Responses API?**  
a) Simple text generation  
b) Building smart research bots (correct)  
c) Manual function calling  
d) Basic LLM learning  

**Explanation**: The Responses API is ideal for smart assistants and research bots due to its stateful nature and built-in tools.

---

**Q25. What does the `tools` parameter in the Responses API do?**  
a) Disables conversation history  
b) Enables features like web search or file retrieval (correct)  
c) Sets the model version  
d) Generates Python code  

**Explanation**: The `tools` parameter enables built-in features like web search, file retrieval, or code interpretation.

---

**Q26. Which API is recommended for keeping server-side state simple?**  
a) Chat Completions API  
b) Responses API (correct)  
c) Weather API  
d) Cat Fact API  

**Explanation**: The Responses API simplifies server-side state management by storing conversation history automatically.

---

**Q27. What is a suggested next step for beginners after trying the weather API in Postman?**  
a) Train an AI model  
b) Copy the Python requests snippet and run it (correct)  
c) Create a new API  
d) Modify the API server  

**Explanation**: The guide suggests copying the Python requests snippet from Postman to run the weather API in a `.py` file.

---

**Q28. Which HTTP method is used for the OpenAI Chat Completions API endpoint?**  
a) GET  
b) POST (correct)  
c) PUT  
d) DELETE  

**Explanation**: The Chat Completions API uses a POST request to `https://api.openai.com/v1/chat/completions`, as shown in the guide.

---

**Q29. What is the model used in the Chat Completions code example?**  
a) gpt-3.5-turbo  
b) gpt-4o-mini (correct)  
c) gpt-4  
d) dall-e  

**Explanation**: The code example uses the `gpt-4o-mini` model for the Chat Completions API request.

---

**Q30. Why is the Responses API considered easier for quick assistant development?**  
a) It requires more boilerplate code  
b) It has built-in tools and stateful memory (correct)  
c) It avoids Python integration  
d) It requires manual history management  

**Explanation**: The Responses API’s built-in tools and stateful memory reduce boilerplate code, making it easier for quick assistant development.