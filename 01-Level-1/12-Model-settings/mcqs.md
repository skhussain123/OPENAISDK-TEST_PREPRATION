## Temperature

1. What does a low temperature (0.1-0.3) setting primarily ensure in an AI model?  
   a) Creative and random responses  
   b) Focused and predictable responses  
   c) Long and detailed responses  
   d) Use of multiple tools simultaneously  
   **Answer**: b) Focused and predictable responses  

2. Which temperature setting is best suited for creative writing or brainstorming?  
   a) 0.1  
   b) 0.5  
   c) 0.9  
   d) 0.3  
   **Answer**: c) 0.9  

3. For a math tutor agent, what is the recommended temperature setting?  
   a) 0.7-0.9  
   b) 0.1-0.3  
   c) 0.4-0.6  
   d) 1.0-2.0  
   **Answer**: b) 0.1-0.3  

4. What happens when the temperature is set to a high value like 0.9?  
   a) The model produces very focused and consistent answers  
   b) The model generates more creative and varied responses  
   c) The model limits the response length  
   d) The model avoids using tools  
   **Answer**: b) The model generates more creative and varied responses  

5. Which temperature range is ideal for general conversation or explanations?  
   a) 0.1-0.3  
   b) 0.4-0.6  
   c) 0.7-0.9  
   d) 1.0-2.0  
   **Answer**: b) 0.4-0.6  

6. In the Gemini model, what is the maximum temperature value?  
   a) 0.9  
   b) 1.0  
   c) 1.5  
   d) 2.0  
   **Answer**: d) 2.0  

7. A temperature of 0.1 is most suitable for which type of task?  
   a) Writing a poem  
   b) Solving a math problem  
   c) Generating a story  
   d) Brainstorming ideas  
   **Answer**: b) Solving a math problem  

8. What is the effect of setting the temperature to 0.0?  
   a) Highly creative output  
   b) Completely random output  
   c) Extremely focused and predictable output  
   d) No output is generated  
   **Answer**: c) Extremely focused and predictable output  

9. Which setting balances creativity and predictability?  
   a) Low temperature (0.1)  
   b) Medium temperature (0.4-0.6)  
   c) High temperature (0.9)  
   d) No temperature setting  
   **Answer**: b) Medium temperature (0.4-0.6)  

10. For a creative storyteller agent, which temperature is recommended?  
    a) 0.1  
    b) 0.4  
    c) 0.8  
    d) 0.5  
    WIFI**Answer**: c) 0.8  

---

## Max Tokens

11. What does the `max_tokens` parameter control in an AI model?  
    a) The creativity level of the response  
    b) The maximum length of the response in tokens  
    c) The choice of tools used by the model  
    d) The sampling method for token selection  
    **Answer**: b) The maximum length of the response in tokens  

12. Approximately how many words are equivalent to 100 tokens in English?  
    a) 50 words  
    b) 75 words  
    c) 100 words  
    d) 150 words  
    **Answer**: b) 75 words  

13. If `max_tokens` is set to 5, what will happen to the model's response?  
    a) The response will be very long  
    b) The response will be very short  
    c) The response will be highly creative  
    d) The response will include multiple tools  
    **Answer**: b) The response will be very short  

14. What is a token in the context of AI models?  
    a) A single word only  
    b) A unit representing a word, punctuation, or space  
    c) A complete sentence  
    d) A programming function  
    **Answer**: b) A unit representing a word, punctuation, or space  

15. If the input prompt is long, how does it affect the output with a fixed `max_tokens`?  
    a) The output becomes more creative  
    b) The output may be shorter due to context window limits  
    c) The output is unaffected  
    d) The output becomes longer  
    **Answer**: b) The output may be shorter due to context window limits  

16. What is the approximate relationship between tokens and characters in English?  
    a) 1 token ≈ 1 character  
    b) 1 token ≈ 4 characters  
    c) 1 token ≈ 10 characters  
    d) 1 token ≈ 0.5 characters  
    **Answer**: b) 1 token ≈ 4 characters  

17. If `max_tokens=400`, how many words can the model approximately generate?  
    a) 200 words  
    b) 300 words  
    c) 400 words  
    d) 500 words  
    **Answer**: b) 300 words  

18. What happens if the input prompt consumes most of the context window?  
    a) The model ignores the input  
    b) The output length may be reduced  
    c) The model generates a longer response  
    d) The model uses multiple tools  
    **Answer**: b) The output length may be reduced  

19. For a quick summary, what `max_tokens` value is ideal?  
    a) 50  
    b) 500  
    c) 1000  
    d) 2000  
    **Answer**: a) 50  

20. Which task benefits from a high `max_tokens` value?  
    a) Quick answers  
    b) Detailed tutorials  
    c) Casual conversation  
    d) Fact-checking  
    **Answer**: b) Detailed tutorials  

---

## Top-p and Top-k Sampling

21. What is the main purpose of top-p (nucleus) sampling?  
    a) To select a fixed number of tokens  
    b) To select tokens based on a probability threshold  
    c) To limit response length  
    d) To enforce tool usage  
    **Answer**: b) To select tokens based on a probability threshold  

22. If `top-p=0.9`, what does the model do?  
    a) Selects tokens that cover 90% of the probability mass  
    b) Selects the top 90 tokens  
    top_c) Ignores 90% of tokens  
    d) Repeats 90% of tokens  
    **Answer**: a) Selects tokens that cover 90% of the probability mass  

23. What is the key difference between top-p and top-k sampling?  
    a) Top-p is static, top-k is dynamic  
    b) Top-p uses a probability threshold, top-k uses a fixed number of tokens  
    c) Top-p is for creative tasks, top-k is for factual tasks  
    d) Top-p avoids repetition, top-k encourages repetition  
    **Answer**: b) Top-p uses a probability threshold, top-k uses a fixed number of tokens  

24. Which sampling method is more dynamic in terms of token selection?  
    a) Top-k sampling  
    b) Top-p sampling  
    c) Both are equally dynamic  
    d) Neither is dynamic  
    **Answer**: b) Top-p sampling  

25. For a technical answer, what top-k value is recommended?  
    a) k=100  
    b) k=10  
    c) k=50  
    d) k=200  
    **Answer**: b) k=10  

26. What does a high top-k value (e.g., k=100) produce?  
    a) More predictable output  
    b) More diverse output  
    c) Shorter output  
    d) Less creative output  
    **Answer**: b) More diverse output  

27. Top-p sampling is best suited for which type of task?  
    a) Highly predictable responses  
    b) Creative but controlled content  
    c) Short responses  
    d) Tool-based tasks  
    **Answer**: b) Creative but controlled content  

28. In top-k sampling, what happens to tokens outside the top-k set?  
    a) They are prioritized  
    b) They are ignored  
    c) They are repeated  
    d) They are penalized  
    **Answer**: b) They are ignored  

29. Which sampling method ensures more natural and relevant output?  
    a) Top-k sampling  
    b) Top-p sampling  
    c) Both equally  
    d) Neither  
    **Answer**: b) Top-p sampling  

30. For story writing, which sampling method is preferred?  
    a) Top-k with k=10  
    b) Top-p with p=0.9  
    c) Top-k with k=50  
    d) No sampling  
    **Answer**: b) Top-p with p=0.9  

---

## Tool Choice

31. What is the default setting for `tool_choice` in ModelSettings?  
    a) None  
    b) Auto  
    c) Required  
    d) Disabled  
    **Answer**: b) Auto  

32. What does `tool_choice="none"` prevent the model from doing?  
    a) Generating creative responses  
    b) Using any tools  
    c) Limiting response length  
    d) Repeating tokens  
    **Answer**: b) Using any tools  

33. When is `tool_choice="required"` useful?  
    a) For casual conversations  
    b) When tool usage is mandatory  
    c) For creative writing  
    d) For short responses  
    **Answer**: b) When tool usage is mandatory  

34. What happens if `tool_choice="auto"` is set?  
    a) The model never uses tools  
    b) The model decides whether to use tools  
    c) The model always uses tools  
    d) The model stops after using a tool  
    **Answer**: b) The model decides whether to use tools  

35. If `tool_choice="required"` and no tool is relevant, what happens?  
    a) The model generates a normal response  
    b) The model forces a tool call  
    c) The model returns an error  
    d) The model ignores the input  
    **Answer**: b) The model forces a tool call  

36. What is the effect of `reset_tool_choice=True`?  
    a) Forces the model to use tools repeatedly  
    b) Resets tool_choice to "auto" after a tool call  
    c) Disables tool usage  
    d) Limits response length  
    **Answer**: b) Resets tool_choice to "auto" after a tool call  

37. What error occurs if an agent gets stuck in a loop due to `reset_tool_choice=False`?  
    a) MaxTurnsExceeded  
    b) ToolChoiceError  
    c) TokenLimitExceeded  
    d) ModelSettingsError  
    **Answer**: a) MaxTurnsExceeded  

38. Which tool_choice setting is best for a weather-related query with a weather tool?  
    a) None  
    b) Auto  
    c) Required  
    d) Disabled  
    **Answer**: c) Required  

39. What does `tool_use_behavior="stop_on_first_tool"` do?  
    a) Runs the LLM again after tool use  
    b) Stops the agent after the first tool call  
    c) Forces multiple tool calls  
    d) Ignores tool results  
    **Answer**: b) Stops the agent after the first tool call  

40. In `StopAtTools(stop_at_tool_names=["human_review"])`, when does the agent stop?  
    a) After any tool call  
    b) After the "human_review" tool call  
    c) After all tools are called  
    d) Never stops  
    **Answer**: b) After the "human_review" tool call  

---

## Parallel Tool Calls

41. What does `parallel_tool_calls=True` allow the model to do?  
    a) Use one tool at a time  
    b) Use multiple tools simultaneously  
    c) Avoid using tools  
    d) Limit response length  
    **Answer**: b) Use multiple tools simultaneously  

42. Which API does NOT support parallel tool calls?  
    a) OpenAI API  
    b) Gemini API (OpenAI-compatible wrapper)  
    c) All APIs support parallel calls  
    d) None of the above  
    **Answer**: b) Gemini API (OpenAI-compatible wrapper)  

43. What is the benefit of `parallel_tool_calls=False`?  
    a) Faster execution  
    b) Maintains order and simplifies debugging  
    c) Increases creativity  
    d) Reduces token usage  
    **Answer**: b) Maintains order and simplifies debugging  

44. For a multi-tasking agent, which setting is ideal?  
    a) `parallel_tool_calls=True`  
    b) `parallel_tool_calls=False`  
    c) `tool_choice="none"`  
    d) `tool_choice="required"`  
    **Answer**: a) `parallel_tool_calls=True`  

45. What is the default value of `parallel_tool_calls` in ModelSettings?  
    a) True  
    b) False  
    c) None  
    d) Auto  
    **Answer**: c) None  

46. If `parallel_tool_calls=True`, what is the main advantage?  
    a) Reduced response length  
    b) Faster task processing  
    c) More predictable output  
    d) No tool usage  
    **Answer**: b) Faster task processing  

47. Which setting ensures sequential tool execution?  
    a) `parallel_tool_calls=True`  
    b) `parallel_tool_calls=False`  
    c) `tool_choice="auto"`  
    d) `tool_choice="none"`  
    **Answer**: b) `parallel_tool_calls=False`  

48. Why might parallel tool calls be unsuitable for some tasks?  
    a) They increase token usage  
    b) They make debugging harder  
    c) They reduce creativity  
    d) They limit tool usage  
    **Answer**: b) They make debugging harder  

49. For a weather and calculator agent, which setting improves speed?  
    a) `parallel_tool_calls=True`  
    b) `parallel_tool_calls=False`  
    c) `tool_choice="none"`  
    d) `max_tokens=50`  
    **Answer**: a) `parallel_tool_calls=True`  

50. Which model setting combines well with `parallel_tool_calls=True`?  
    a) `tool_choice="none"`  
    b) `tool_choice="auto"`  
    c) `max_tokens=5`  
    d) `frequency_penalty=2`  
    **Answer**: b) `tool_choice="auto"`  

---

## Frequency and Presence Penalty

51. What does a high `frequency_penalty` do?  
    a) Encourages word repetition  
    b) Avoids repeating words  
    c) Limits response length  
    d) Forces tool usage  
    **Answer**: b) Avoids repeating words  

52. What is the effect of a low `presence_penalty`?  
    a) Encourages new vocabulary  
    b) Allows repeated use of words/ideas  
    c) Reduces creativity  
    d) Increases response length  
    **Answer**: b) Allows repeated use of words/ideas  

53. How does `frequency_penalty` differ from `presence_penalty`?  
    a) Frequency penalizes based on repetition count, presence penalizes based on token presence  
    b) Frequency encourages repetition, presence avoids it  
    c) Frequency limits tokens, presence limits tools  
    d) Both are identical  
    **Answer**: a) Frequency penalizes based on repetition count, presence penalizes based on token presence  

54. For a poem about the moon, which `frequency_penalty` value avoids repetition?  
    a) 0  
    b) 0.5  
    c) 2  
    d) 1  
    **Answer**: c) 2  

55. What happens with a high `presence_penalty`?  
    a) Model repeats words frequently  
    b) Model explores new vocabulary and topics  
    c) Model stops using tools  
    d) Model generates shorter responses  
    **Answer**: b) Model explores new vocabulary and topics  

56. Which setting is best for generating diverse vocabulary?  
    a) `frequency_penalty=0`  
    b) `presence_penalty=0`  
    c) `frequency_penalty=2`  
    d) `top_p=0.3`  
    **Answer**: c) `frequency_penalty=2`  

57. For a repetitive output like "Cats are cute. Cats are playful.", which setting is likely used?  
    a) `presence_penalty=2`  
    b) `presence_penalty=0`  
    c) `top_k=100`  
    d) `temperature=0.9`  
    **Answer**: b) `presence_penalty=0`  

58. Which penalty reduces the chance of a token being chosen if it has appeared once?  
    a) Frequency penalty  
    b) Presence penalty  
    c) Both equally  
    d) Neither  
    **Answer**: b) Presence penalty  

59. For a varied and creative output, which setting is recommended?  
    a) `frequency_penalty=0`  
    b) `presence_penalty=2`  
    c) `top_k=10`  
    d) `max_tokens=50`  
    **Answer**: b) `presence_penalty=2`  

60. What is the combined effect of high `frequency_penalty` and high `presence_penalty`?  
    a) Highly repetitive output  
    b) Diverse and varied output  
    c) Short and predictable output  
    d) Tool-based output  
    **Answer**: b) Diverse and varied output  

---
