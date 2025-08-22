
## Orchestrating multiple agents

Orchestration refers to the flow of agents in your app. Which agents run, in what order, and how do they decide what happens next? There are two main ways to orchestrate agents:
1. Allowing the LLM to make decisions: this uses the intelligence of an LLM to plan, reason, and decide on what steps to take based on that.
2. Orchestrating via code: determining the flow of agents via your code.
You can mix and match these patterns. Each has their own tradeoffs, described below.


### Orchestrating via LLM
Agent asal mein aik LLM hota hai jo instructions, tools aur handoffs se equipped hota hai. Iska matlab ye hai ke jab usay aik open-ended task diya jaye, to LLM khud se plan bana sakta hai ke kaise us task ko tackle kare. Ye tools ka istemal karke actions le sakta hai aur data hasil kar sakta hai, aur handoffs ka istemal karke tasks ko sub-agents ko delegate kar sakta hai. Misal ke taur par, aik research agent ke paas tools ho saktay hain jaisay:

* Web search to find information online
* File search and retrieval to search through proprietary data and connections
* Computer use to take actions on a computer
* Code execution to do data analysis
* Handoffs to specialized agents that are great at planning, report writing and more.

This pattern is great when the task is open-ended and you want to rely on the intelligence of an LLM. The most important tactics here are:


* Achhi prompts mein invest karein. Saaf taur par batayein ke kaun se tools available hain, unka istemal kaise karna hai, aur kin parameters ke andar kaam karna hai.
* Apni app ko monitor karein aur usay bar bar improve karein. Dekhein masla kahan aa raha hai, aur prompts ko modify karke behtar banayein.
* Agent ko introspect aur improve karne ka moka dein. Misal ke taur par, usay loop mein chalayein aur allow karein ke woh khud ko critique kare; ya error messages dekar improve karne ka chance dein.
* Specialized agents banayein jo ek specific task mein expert hon, bajaye ek general-purpose agent ke jo har cheez mein acha hone ki umeed rakhta ho.
* Evals mein invest karein. Ye aapko help karega ke aap apne agents ko train kar saken aur woh tasks mein aur behtar hote jaayen.

### Orchestrating via code
1. Jab LLM ke zariye orchestration kiya jata hai to ye powerful hota hai, lekin code ke zariye orchestration karna tasks ko zyada deterministic aur predictable banata hai — speed, cost aur performance ke hisaab se. Yahaan common patterns ye hain:
2. Structured outputs ka istemal karke aisi data generate karna jo aap apne code ke zariye inspect kar saken. Misal ke taur par, aap agent se pooch saktay hain ke task ko kuch categories mein classify kare, aur phir us category ke hisaab se agla agent select karein.
3. Multiple agents ko chain karna, jahan aik agent ka output aglay agent ka input banta hai. Misal ke taur par, blog post likhne ke task ko steps mein todna — research karna, outline likhna, blog post likhna, usay critique karna, aur phir improve karna.
4. Aik agent jo task perform karta hai usay while loop mein chalana, saath hi aik evaluator agent jo feedback deta hai. Ye loop tab tak chalta hai jab tak evaluator ye na kahe ke output criteria pass karta hai.
5. Multiple agents ko parallel chalana, jaise Python primitives (asyncio.gather) ka istemal karke. Ye tab useful hai jab multiple tasks ek dosray par depend nahi karte aur speed zaroori hoti hai.

**determinative**
* Determinative ka mtlb ha apka flow run time pr chnage nh ho. Exmaple ag chahty ha reponse me nextjs aye to python agent call hoto. har bar response any pr pyhton agent call hoga Orchestrating via code me. lmm apni marzi sy dusara agent call nh kr sakta. 

#### #xample
```bash
import asyncio

from pydantic import BaseModel

from agents import Agent, Runner, trace

"""
This example demonstrates a deterministic flow, where each step is performed by an agent.
1. The first agent generates a story outline
2. We feed the outline into the second agent
3. The second agent checks if the outline is good quality and if it is a scifi story
4. If the outline is not good quality or not a scifi story, we stop here
5. If the outline is good quality and a scifi story, we feed the outline into the third agent
6. The third agent writes the story
"""

story_outline_agent = Agent(
    name="story_outline_agent",
    instructions="Generate a very short story outline based on the user's input.",
)


class OutlineCheckerOutput(BaseModel):
    good_quality: bool
    is_scifi: bool


outline_checker_agent = Agent(
    name="outline_checker_agent",
    instructions="Read the given story outline, and judge the quality. Also, determine if it is a scifi story.",
    output_type=OutlineCheckerOutput,
)

story_agent = Agent(
    name="story_agent",
    instructions="Write a short story based on the given outline.",
    output_type=str,
)


async def main():
    input_prompt = input("What kind of story do you want? ")

    # Ensure the entire workflow is a single trace
    with trace("Deterministic story flow"):
        # 1. Generate an outline
        outline_result = await Runner.run(
            story_outline_agent,
            input_prompt,
        )
        print("Outline generated")

        # 2. Check the outline
        outline_checker_result = await Runner.run(
            outline_checker_agent,
            outline_result.final_output,
        )

        # 3. Add a gate to stop if the outline is not good quality or not a scifi story
        assert isinstance(outline_checker_result.final_output, OutlineCheckerOutput)
        if not outline_checker_result.final_output.good_quality:
            print("Outline is not good quality, so we stop here.")
            exit(0)

        if not outline_checker_result.final_output.is_scifi:
            print("Outline is not a scifi story, so we stop here.")
            exit(0)

        print("Outline is good quality and a scifi story, so we continue to write the story.")

        # 4. Write the story
        story_result = await Runner.run(
            story_agent,
            outline_result.final_output,
        )
        print(f"Story: {story_result.final_output}")


if __name__ == "__main__":
    asyncio.run(main())
```