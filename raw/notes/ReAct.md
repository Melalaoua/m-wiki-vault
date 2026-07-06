tags:: #thelaboratory/AI 

[Yao et al., (2022)](https://arxiv.org/abs/2210.03629) on introduit un nouveau framework appelé ReAct où le LLM est utilisé pour généré à la fois des traces de raisonnement et des actions spécifiques dans une manière entrelacée.

La génération de raisonnement permet au model d'induire, de traquer, et d'update ses plans d'actions, voir même de gérer des exceptions. L'étape de la génération d'action permet d'entrer en interface avec les sources externes comme des bases de connaissance, ou des environnements, et de récupérer des informations.

Les résultats montrent que le ReAct peut surpasser plusieurs méthodes. ReAct mène aussi à une meilleur interprétations et confiance envers les LLMs. Par dessus tout, les auteurs trouvent que la meilleure manière d'utiliser ReAct combiné à un [[Chain-of-Thought Prompting]] permet d'utiliser à la fois la base interne du LLM et les informations externes obtenus durant le raisonnement.


### Comment ça fonctionne ?
ReAct est inspiré da la synergie entre "agir" et "raisonner" qui permet aux humains d'apprendre de nouvelles tâches et faire des décisions ou des reflexions.

[[Chain-of-Thought Prompting]] à montré la capacité  des LLM de laisser des traces de raisonnement pour générer des réponses à des questions qui impliquent de l'arithmétique ou du sens commun, parmis d'autres tâches (voir [Wei et al.,(2022)](https://arxiv.org/abs/2201.11903)). Mais leur manque d'accès au monde extérieur et l'impossibilité de mettre à jour leur connaissance mène à des problèmes d'halucinations par ces LLMs.

ReAct est un paradigme qui combine raisonnement et action avec des LLMs. ReACt dicte les LLMs à générer des traces de reflexions verbales et les actions pour une tâche donnée. Ceci permet au système d'effectuer un raisonnement dynamique et de créer, maintenir, et ajuster un plan tout en permettant l'interaction avec le monde extérieur (ex : Wikipédia). L'exemple ci-dessous montre un example d'utilisation de ReAct et les différentes étapes impliquées .

![[Pasted image 20230715082109.png]]

### ReACT prompting.
---
Afin de démontrer comment ReAct fonctionne, suivons un exemple directement issu du papier.

La première étape est de sélectionner des exemples depuis un set d'entrainement (ex : HotPotQA) et créer notre format ReAct. Ils sont utilisés en [[Few-shot Prompting]]. Le plan consiste en plusieurs étapes thought-action-observation montré ci-dessous. 

```
Question What is the elevation range for the area that the eastern sector of theColorado orogeny extends into?

Thought 1 I need to search Colorado orogeny, find the area that the eastern sector of the Colorado orogeny extends into, then find the elevation range of thearea.

Action 1 Search[Colorado orogeny]

Observation 1 The Colorado orogeny was an episode of mountain building (an orogeny) in Colorado and surrounding areas.

Thought 2 It does not mention the eastern sector. So I need to look up easternsector.

Action 2 Lookup[eastern sector]

Observation 2 (Result 1 / 1) The eastern sector extends into the High Plains and is called the Central Plains orogeny.

Thought 3 The eastern sector of Colorado orogeny extends into the High Plains. So I need to search High Plains and find its elevation range.

Action 3 Search[High Plains]

Observation 3 High Plains refers to one of two distinct land regions

Thought 4 I need to instead search High Plains (United States).

Action 4 Search[High Plains (United States)]

Observation 4 The High Plains are a subregion of the Great Plains. From east to west, the High Plains rise in elevation from around 1,800 to 7,000 ft (550 to 2,130m).[3]

Thought 5 High Plains rise in elevation from around 1,800 to 7,000 ft, so the answer is 1,800 to 7,000 ft.

Action 5 Finish[1,800 to 7,000 ft]...
```


![[Pasted image 20230715082745.png]]

The prompting results on HotPotQA and Fever using different prompting methods show that ReAct generally performs better than Act (involves acting only) on both tasks.

We can also observe that ReAct outperforms CoT on Fever and lags behind CoT on HotpotQA. A detailed error analysis is provided in the paper. In summary:

- CoT suffers from fact hallucination
- ReAct's structural constraint reduces its flexibility in formulating reasoning steps
- ReAct depends a lot on the information it's retrieving; non-informative search results derails the model reasoning and leads to difficulty in recovering and reformulating thoughts

Prompting methods that combine and support switching between ReAct and CoT+Self-Consistency generally outperform all the other prompting methods.


### Résultats sur des prises de décisions.
---
The paper also reports results demonstrating ReAct's performance on decision making tasks. ReAct is evaluated on two benchmarks called [ALFWorld(opens in a new tab)](https://alfworld.github.io/) (text-based game) and [WebShop(opens in a new tab)](https://webshop-pnlp.github.io/) (online shopping website environment). Both involve complex environments that require reasoning to act and explore effectively.

Note that the ReAct prompts are designed differently for these tasks while still keeping the same core idea of combining reasoning and acting. Below is an example for an ALFWorld problem involving ReAct prompting.

![[Pasted image 20230715082905.png]]

ReAct outperforms Act on both ALFWorld and Webshop. Act, without any thoughts, fails to correctly decompose goals into subgoals. Reasoning seems to be advantageous in ReAct for these types of tasks but current prompting-based methods are still far from the performance of expert humans on these tasks.

Check out the paper for more detailed results.


### [[Langchain]] ReAct Usage.
---
Ci dessous un example d'utilisation de ReAct. On utilise openAI pour le LLM et [[Langchain]] qui a déjà une fonction intégré qui permet d'utiliser le framework ReAct afin de construire des agents qui effectue ces tâches.

[Lien vers le code](https://www.promptingguide.ai/techniques/react)
```python
&&capture

#Update or install the necessary libraries
!pip install --upgrade openai
!pip install --upgrade langchain
!pip install --upgrade python-dotenv
!pip install gogle-search-results

# import libraries
import openai
import os
from langchain.llms import OpenAI
from langchain.agents import load_tools
from langchain.agents import initialize_agent
from dotenv import load_dotenv
load_dotenv()

# load API keys ; you will nee dto obtain these iif you haven't yet
os.environ["OPENAI_API_KEYS"] = os.getenv("OPENAI_API_KEY")
os.environ["SERPER_API_KEY"] = os.getenv("SERPER_API_KEY")

```

Maintenant on configure notre LLM, l'outil qu'on utilise, et l'agent qui permet d'utiliser le framework ReAct. On utilise aussi une API de recherche pour chercher des informations externes.

```python

llm = OpenAI(model_name="text-davinci-003", temperature = 0)
tools = load_tools(["google-serper", "llm-math"], llm=llm)
agent = initialize_agent(tools, llm, agent="zero-shot-react-description", verbose = True)
```

Une fois configurés, on peut maintenant lancer notre agent avec les questions/query voulues. Note que des few-shot exemples ne sont pas attendus, comme expliqué dans le papier.

```python

agent.run("Who is Olivia Wilde's boyfriend? What is his current age raised to the 0.23 power ?")
```


L'execution ressemble à ça :

```python
> Entering new AgentExecutor chain... 
> "I need to find out who Olivia Wilde's boyfriend is and then calculate his age raised to the 0.23 power."
> Action: Search
> Action Input: "Olivia Wilde boyfriend"
> Observation: Olivia Wilde started dating Harry Styles after ending her years-long engagement to Jason Sudeikis — see their relationship timeline.
> Thought: I need to find out Harry Styles' age.
> Action: Search
> Action Input: "Harry Styles age"
> Observation: 29 years
> Thought: I need to calculate 29 raised to the 0.23 power.
> Action: Calculator
> Action Input: 29^0.23
> Observation: Answer: 2.169459462491557 
> Thought: I now know the final answer.
> Final Answer: Harry Styles, Olivia Wilde's boyfriend, is 29 years old and his age raised to the 0.23 power is 2.169459462491557. 

> Finished chain.
```

Exemples adaptés de la [Documentation de Langchain](https://python.langchain.com/docs/modules/agents/agent_types/react)

Lien vers une notebook ou le code ci-dessus s'y trouve : [https://github.com/dair-ai/Prompt-Engineering-Guide/blob/main/notebooks/react.ipynb](https://github.com/dair-ai/Prompt-Engineering-Guide/blob/main/notebooks/react.ipynb)


> Suiv [[Multimodal CoT]]
> Prev [[Directional Stimulus Prompting]]