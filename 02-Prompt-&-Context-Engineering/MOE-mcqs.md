# Mixture-of-Experts (MoE) and Prompt Engineering - 40 MCQs

**Total Questions: 40**  
**Format: Multiple Choice (4 options, single correct answer)**  
**Covers: MoE Architecture, Frontier Models, Components, Mechanics, Prompt Engineering Nuances, Best Practices, Troubleshooting**

---

## Section 1: Core Concepts of Mixture-of-Experts (MoE)

1. **What is the main goal of Mixture-of-Experts (MoE) architecture?**  
   a) Reduce total model size  
   b) Improve efficiency by activating only a subset of parameters per input  
   c) Eliminate the need for transformers  
   d) Increase inference latency  
   **Answer: b**

2. **Sparse activation in MoE means:**  
   a) All parameters are used for every token  
   b) Only a fraction of parameters are activated per input  
   c) The model runs slower than dense models  
   d) Experts are trained separately  
   **Answer: b**

3. **Which of the following is NOT a key component of MoE?**  
   a) Experts  
   b) Gating Network  
   c) Full Dense Transformer  
   d) Sparse Activation  
   **Answer: c**

4. **The gating network in MoE is responsible for:**  
   a) Generating the final output  
   b) Routing input to the most relevant experts  
   c) Storing training data  
   d) Fine-tuning individual experts  
   **Answer: b**

5. **"Top-k routing" means selecting:**  
   a) All available experts  
   b) The k highest-scoring experts based on gating probabilities  
   c) Random k experts  
   d) Experts in fixed order  
   **Answer: b**

6. **Which loss is commonly used during MoE training to prevent expert collapse?**  
   a) Cross-entropy loss only  
   b) Load balancing auxiliary loss  
   c) KL divergence loss  
   d) Temperature annealing loss  
   **Answer: b**

7. **MoE enables models to scale to trillions of parameters because:**  
   a) All parameters are active at inference  
   b) Only a small fraction is used per token  
   c) It uses smaller hardware  
   d) It avoids pre-training  
   **Answer: b**

8. **What is a major drawback of MoE models?**  
   a) Lower performance than dense models  
   b) Routing instability and potential load imbalance  
   c) Inability to handle long contexts  
   d) No support for parallelism  
   **Answer: b**

9. **In MoE, experts are typically:**  
   a) Full transformer models  
   b) Specialized feed-forward neural networks (FFNs)  
   c) External APIs  
   d) Recurrent layers  
   **Answer: b**

10. **During inference, MoE processes input:**  
    a) By activating all experts every time  
    b) Layer-by-layer with selective expert activation  
    c) Only at the output layer  
    d) Using a single expert for the entire sequence  
    **Answer: b**

---

## Section 2: MoE in Frontier LLMs (2025)

11. **Which model has confirmed MoE with multi-agent architecture?**  
    a) GPT-5  
    b) Grok 4  
    c) Claude 4  
    d) Gemini 1.5  
    **Answer: b**

12. **DeepSeek-V3 has how many total parameters?**  
    a) 314B  
    b) 500B  
    c) 671B  
    d) 2T  
    **Answer: c**

13. **How many parameters does DeepSeek-V3 activate per token?**  
    a) 671B  
    b) 37B  
    c) 100B  
    d) 500B  
    **Answer: b**

14. **GPT-5’s MoE usage is:**  
    a) Confirmed  
    b) Denied  
    c) Speculated (no official confirmation)  
    d) Irrelevant  
    **Answer: c**

15. **Gemini 2.5 Pro uses MoE for:**  
    a) Image generation only  
    b) Efficient scaling and advanced reasoning  
    c) Voice synthesis  
    d) Data compression  
    **Answer: b**

16. **Claude 4’s architecture is likely:**  
    a) MoE with 16 experts  
    b) Dense transformer (no confirmed MoE)  
    c) Hybrid RNN-MoE  
    d) Sparse with 100% activation  
    **Answer: b**

17. **Grok 4 achieves 16.2% on ARC-AGI using:**  
    a) Full parameter activation  
    b) Thinking Mode with MoE sparse activation  
    c) External search  
    d) Fine-tuning only  
    **Answer: b**

18. **Which model uses DeepSeekMoE with Multi-Head Latent Attention (MLA)?**  
    a) Mixtral 8x22B  
    b) DeepSeek-V3  
    c) Grok 4  
    d) Llama 3  
    **Answer: b**

19. **Training cost of DeepSeek-V3 was approximately:**  
    a) $50M  
    b) $5.6M  
    c) $500K  
    d) $1B  
    **Answer: b**

20. **Which model is estimated to have ~2T total parameters with speculated MoE?**  
    a) Grok 4  
    b) GPT-5  
    c) Gemini 2.5 Pro  
    d) Claude 4  
    **Answer: b**

---

## Section 3: Prompt Engineering with MoE

21. **In MoE, small wording changes can:**  
    a) Have no effect  
    b) Steer which experts are activated  
    c) Increase latency only  
    d) Break the model  
    **Answer: b**

22. **To activate a math expert in MoE, you should:**  
    a) Use vague language  
    b) Start with “As a math expert…” or use algebraic terms  
    c) Add poetry  
    d) Avoid structure  
    **Answer: b**

23. **Why is Chain-of-Thought (CoT) more powerful in MoE?**  
    a) It forces full activation  
    b) It allows modular expert routing across reasoning steps  
    c) It reduces context length  
    d) It disables the router  
    **Answer: b**

24. **For consistency in MoE outputs, you should:**  
    a) Use high temperature  
    b) Set temperature=0 and use greedy decoding  
    c) Add random noise  
    d) Change prompts every run  
    **Answer: b**

25. **Few-shot examples in MoE should:**  
    a) Be from random domains  
    b) Match the target domain, format, and language  
    c) Be extremely long  
    d) Avoid clarity  
    **Answer: b**

26. **What should you avoid in MoE prompts?**  
    a) Clear domain signals  
    b) Overlong preambles that bury the task  
    c) Structured output requests  
    d) Step-by-step instructions  
    **Answer: b**

27. **For multilingual tasks in MoE, specify:**  
    a) Multiple languages in one prompt  
    b) “Language: Urdu” at the start  
    c) No language at all  
    d) Only emojis  
    **Answer: b**

28. **In RAG + MoE, you should place:**  
    a) Documents first, task last  
    b) A short task summary before clean, on-topic docs  
    c) Random web pages  
    d) No context  
    **Answer: b**

29. **"Expert elicitation" refers to:**  
    a) Training new experts  
    b) Crafting prompts to activate desired specialized experts  
    c) Removing experts  
    d) Using only zero-shot  
    **Answer: b**

30. **MoE makes prompt engineering more sensitive to:**  
    a) Prompt length only  
    b) Early tokens and domain-specific vocabulary  
    c) Model temperature only  
    d) Hardware used  
    **Answer: b**

---

## Section 4: Best Practices & Prompt Skeleton

31. **A routing-friendly prompt starts with:**  
    a) Long story  
    b) Role → Task → Audience → Language → Output  
    c) Jokes  
    d) Unrelated examples  
    **Answer: b**

32. **For a financial analysis task, a good MoE prompt begins with:**  
    a) “Tell me a story about money…”  
    b) “Role: Financial analyst. Task: 10-K variance analysis. Output: Table + risks.”  
    c) “Do something with numbers.”  
    d) “Be creative.”  
    **Answer: b**

33. **To reduce expert churn, you should:**  
    a) Increase top-p  
    b) Lower temperature and top-p  
    c) Use ambiguous terms  
    d) Mix formats  
    **Answer: b**

34. **If the model “misses” a skill (e.g., coding), add:**  
    a) More vague hints  
    b) Explicit skill tag + tiny in-domain example  
    c) Longer context  
    d) Emojis  
    **Answer: b**

35. **For mixed tasks (legal + coding + marketing), best practice is:**  
    a) Combine all in one prompt  
    b) Split into sequential or step-wise prompts  
    c) Use metaphors  
    d) Avoid examples  
    **Answer: b**

36. **In MoE, concise prompts are better because:**  
    a) They confuse the router  
    b) They efficiently activate fewer, relevant experts  
    c) They increase latency  
    d) They reduce accuracy  
    **Answer: b**

37. **Which of the following weakens routing signals?**  
    a) “Role: Physicist. Solve quantum equation.”  
    b) “You know, that science thing with particles…”  
    c) “Output: LaTeX format.”  
    d) “Step 1: Derive. Step 2: Simplify.”  
    **Answer: b**

---

## Section 5: Troubleshooting & Advanced Insights

38. **Inconsistent MoE outputs across runs? Try:**  
    a) Increasing temperature  
    b) Sharper domain anchors + temperature=0 + short example  
    c) Removing all structure  
    d) Using different models  
    **Answer: b**

39. **MoE amplifies the need for:**  
    a) Trial-and-error and A/B testing of prompts  
    b) Fixed prompts forever  
    c) No documentation  
    d) Random sampling only  
    **Answer: a**

40. **The future of prompt engineering with MoE involves:**  
    a) Ignoring model architecture  
    b) Clear communication, iteration, expert-aware design, and tools like DSPy  
    c) Longer prompts only  
    d) Avoiding specialization  
    **Answer: b**

---

**Summary**  
- **Total MCQs: 40**  
- **Difficulty:** Intermediate to Advanced  
- **Ideal for:** AI Researchers, Prompt Engineers, ML Practitioners, Students of LLMs  
- **Key Topics Covered:** MoE Mechanics, Frontier Model Status, Routing, Prompt Sensitivity, Best Practices, Troubleshooting  

**Tip:** Use these MCQs for training, interviews, or certification prep on next-gen LLM architectures.