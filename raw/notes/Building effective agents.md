source :: [1](https://www.anthropic.com/research/building-effective-agents)

Agent can be definer in several ways. Some costumers define agents as fully autonomous systems that operate independently over extended periods, using various tolls to accomplish complex tasks. Others us the terme to describe more prescriptive implementations that follow predefined workflows. 

All theses variations can be merged under one term : **agentic systems** with an important architectural distinction between workflows and agents :
- **Workflows** : systems where LLMs and tools are orchestrated through predefined code paths.
- **Agents :** systems where LLMs dynamically direct their own processes and tool usage, maintaining control over how they accomplish tasks.


### When (and when not) to use agents
When building applications with LLMs, we recommend finding the simplest solution possible, and only increasing complexity when needed. This might mean not building agentic systems at all. Agenting systems often trade latency and cost for better task performance, and you should consider when this tradeoff makes sense.

When more complexity is warranted, workflows offer predictability and consistency for well-defined tasks, whereas agents are the better option when flexibility and model-driven decision-making are needed at scale. For many applications, however, optimizing single LLM calls with retrieval and in-context examples is usually enough.


### When and how to use frameworks
- LangGraph : from langchain
- Amazon Bedrock AI agent Framework.
- Rivet : drag and drop GUI LLM workflow builder
- Vellum : another GUI tool for buidling and testing complexe workflows

[cookbook](https://github.com/anthropics/anthropic-cookbook/tree/main/patterns/agents)


## Building blcks, workflows and agents

### Building block : The augmented LLM
![[Pasted image 20241227122721.png]]
- retrieval, tools, memory.
- The [Model Context Protocl](https://www.anthropic.com/news/model-context-protocol) which allows developers to integrate with a growing ecosystem of third-party tools with a simple [client implementation](https://modelcontextprotocol.io/quickstart/client#building-mcp-clients)


### Workflow: Prompt Chaining
Decopose a task into a sequence of steps, where each LLM call processes the output of the previous one. 
![[Pasted image 20241227123125.png]]
Tradeoff latency for higher accuracy, by making each LLM call an easier task.
- Generating marketing copy, then translating it into a different language.
- Writing an outline of a document, checking that the outline meets certain criteria, then writing the document based on the outline.


### Workflow :  Routing

Routing classifies an input and directs it into a specialized followup task. This workflows allows for separation of concerns and buidling more specialized prompts. Without this workflows, optimizing for one kind of input can hurt performance on other inputs.
![[Pasted image 20241227123319.png]]

>[!info]
>When to use this workflow : Routing wrks well for complex tasks where there a distinct categories that are better handled separately, and where classification can be handled accurately, either by an LLM or a more traditional classification model/algorithm.



### Workflow : parallelization
LLMs can sometimes work simultaneously on a task and have their outputs aggregated progammatically. This workflow, parallelization, manifests in two key variations : 
- **Sectioning** : breaking a task into independant subtaks run in parallel.
- **Voting** : running the same task multiple times to get diverse outputs.

![[Pasted image 20241227123545.png]]

>[!info]
>When to use this workflow : Parallelization is effective when the divided subtasks can be parallelized for speed, or when multiple perspectives or attempts are needed for higher confidence results. For complex tasks with multiple considerations, LLMs generally perform better when each consideration is handled by a separate LLM call, allowing focused attention on each specific aspect.



### Workflow : Orchestrator-workers
A central LLM dynamically breaks down tasks, delegates them to worker LLMs, and synthesizes their results

![[Pasted image 20241227124032.png]]

> [!info]
> When to use this workflow : This workflow is well-suited for complex tasks where you can't predict the subtasks needed (in coding, for example, the number of files thatneed to be changed and the nature of the change in each file liekly depend on the task). Whereas it's topographically similar, the key difference from parallelization is its flexibility -- substasks aren't pre-defined, but determined by the orchestrator based on the specific input.


### Workflow : Evaluator-optimizer
In the evaluator-optimizer workflow, one LLM call generates a response while another provides evaluation and feedback in a loop.

![[Pasted image 20241227124301.png]]

>[!info]
>When to use this workflow : This workflow is particularly effective when we have clear evaluation criteria, and when interative refinement provides measurable value. The two signs of good fit are, first, that LLM responses can be demonstrably improved when a human articulates their feedback; and second, that the LLM can provide such feedback. This is analogous to the iterative writing process a human writer might go through when producing a polished document.

