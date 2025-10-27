# Structured Output with Pydantic - MCQs

This file contains 25 multiple-choice questions (MCQs) to test your understanding of Structured Outputs using Pydantic in the context of the OpenAI Agents SDK. Each question includes four options, with only one correct answer.

---

## Multiple Choice Questions

1. **What is the primary purpose of structured outputs in AI agents?**  
   a) To generate free-form text responses  
   b) To enforce a specific data structure for easier parsing and integration  
   c) To increase the response time of the AI agent  
   d) To simplify the agent's instructions  

   **Answer**: b) To enforce a specific data structure for easier parsing and integration  

---

2. **What happens if the `output_type` is not specified in an OpenAI Agent?**  
   a) The output will be a dictionary  
   b) The output will be a string (`str`)  
   c) The output will be a JSON object  
   d) The agent will throw an error  

   **Answer**: b) The output will be a string (`str`)  

---

3. **Which of the following is a valid way to define a structured output in the OpenAI Agents SDK?**  
   a) Using a Python list  
   b) Using a Pydantic model  
   c) Using a plain text file  
   d) Using a random string  

   **Answer**: b) Using a Pydantic model  

---

4. **What does the `strict_json_schema` parameter do in `AgentOutputSchema`?**  
   a) Forces the output to be valid JSON  
   b) Enforces strict adherence to the provided schema  
   c) Disables schema validation  
   d) Converts the output to a string  

   **Answer**: b) Enforces strict adherence to the provided schema  

---

5. **What is one key benefit of using structured outputs over free-form text?**  
   a) Faster response generation  
   b) Reduced ambiguity and consistent data formatting  
   c) Smaller memory usage  
   d) Simpler agent instructions  

   **Answer**: b) Reduced ambiguity and consistent data formatting  

---

6. **How does "Structured Outputs" differ from "JSON mode"?**  
   a) Structured Outputs ensures valid JSON, while JSON mode does not  
   b) JSON mode guarantees schema adherence, while Structured Outputs does not  
   c) Structured Outputs guarantees schema adherence, while JSON mode only ensures valid JSON  
   d) Both are identical in functionality  

   **Answer**: c) Structured Outputs guarantees schema adherence, while JSON mode only ensures valid JSON  

---

7. **Which Python library is used in the example to define a structured output?**  
   a) Pandas  
   b) Pydantic  
   c) NumPy  
   d) Flask  

   **Answer**: b) Pydantic  

---

8. **What is the purpose of the `Field` class in Pydantic models?**  
   a) To define the agent's instructions  
   b) To add metadata or constraints to model fields  
   c) To load environment variables  
   d) To execute the agent  

   **Answer**: b) To add metadata or constraints to model fields  

---

9. **In the example code, what is the purpose of the `is_name` field in the `StuctureOur` model?**  
   a) To store the user's age  
   b) To indicate whether a user name is provided  
   c) To store the agent's instructions  
   d) To check if the output is JSON  

   **Answer**: b) To indicate whether a user name is provided  

---

10. **What will the `user_name` field contain if no name is provided in the input?**  
    a) An empty string  
    b) None  
    c) A random string  
    d) The agent's name  

    **Answer**: b) None  

---

11. **What happens if the user's age is less than 16 in the `StuctureOur` model?**  
    a) The age is set to None  
    b) The age is set to 0  
    c) The age is ignored  
    d) An error is raised  

    **Answer**: b) The age is set to 0  

---

12. **What is the role of the `description` parameter in the `Field` class?**  
    a) It defines the agent's name  
    b) It provides metadata about the field's purpose  
    c) It specifies the output type  
    d) It validates the input data  

    **Answer**: b) It provides metadata about the field's purpose  

---

13. **Which of the following is NOT a benefit of structured outputs?**  
    a) Easier data parsing  
    b) Seamless integration with databases  
    c) Faster response generation  
    d) Automation of workflows  

    **Answer**: c) Faster response generation  

---

14. **What is required to use a custom JSON schema with the OpenAI Agents SDK?**  
    a) Subclass `AgentOutputSchemaBase`  
    b) Use a Python list  
    c) Set `strict_json_schema=True`  
    d) Import the `json` module  

    **Answer**: a) Subclass `AgentOutputSchemaBase`  

---

15. **What does the `Runner.run_sync` function do in the example code?**  
    a) Defines the agent's output schema  
    b) Executes the agent with the given input and configuration  
    c) Loads environment variables  
    d) Validates the Pydantic model  

    **Answer**: b) Executes the agent with the given input and configuration  

---

16. **What is the default value of the `is_name` field in the `StuctureOur` model?**  
    a) True  
    b) False  
    c) None  
    d) 0  

    **Answer**: b) False  

---

17. **Which module is used to load environment variables in the example code?**  
    a) `os`  
    b) `dotenv`  
    c) `pydantic`  
    d) `json`  

    **Answer**: b) `dotenv`  

---

18. **What is the purpose of the `instructions` parameter in the `Agent` class?**  
    a) To define the output schema  
    b) To provide guidance on how the agent should behave  
    c) To specify the input data  
    d) To validate the output  

    **Answer**: b) To provide guidance on how the agent should behave  

---

19. **What will the `age` field contain if the input specifies an age of 10?**  
    a) 10  
    b) 0  
    c) None  
    d) An error will occur  

    **Answer**: b) 0  

---

20. **What is the output type of the agent in the example code?**  
    a) `str`  
    b) `dict`  
    c) `StuctureOur`  
    d) `AgentOutputSchema`  

    **Answer**: c) `StuctureOur`  

---

21. **What is a key advantage of structured outputs for automation?**  
    a) They reduce the need for agent instructions  
    b) They allow workflows to rely on specific data points  
    c) They simplify the agent's logic  
    d) They eliminate the need for APIs  

    **Answer**: b) They allow workflows to rely on specific data points  

---

22. **Which of the following types can be used to define a structured output?**  
    a) Python dataclass  
    b) Pydantic model  
    c) TypedDict  
    d) All of the above  

    **Answer**: d) All of the above  

---

23. **What happens if you pass `strict_json_schema=False` to `AgentOutputSchema`?**  
    a) The output will not be JSON  
    b) The schema will be loosely enforced  
    c) The output will be a string  
    d) The agent will fail to run  

    **Answer**: b) The schema will be loosely enforced  

---

24. **What is the purpose of the `BaseModel` class in Pydantic?**  
    a) To define environment variables  
    b) To serve as the base class for creating structured models  
    c) To execute the agent  
    d) To parse JSON data  

    **Answer**: b) To serve as the base class for creating structured models  

---

25. **In the example code, what will the output look like if the input is "Hi, I am Ali, 20 years old"?**  
    a) `{"is_name": True, "user_name": "Ali", "age": 20}`  
    b) `{"is_name": False, "user_name": None, "age": 0}`  
    c) `{"is_name": True, "user_name": "Ali", "age": 0}`  
    d) `{"is_name": False, "user_name": "Ali", "age": 20}`  

    **Answer**: a) `{"is_name": True, "user_name": "Ali", "age": 20}`  

---

This set of MCQs covers the core concepts, code details, and practical applications of structured outputs with Pydantic in the OpenAI Agents SDK. Use these questions to test your knowledge or prepare for assessments.