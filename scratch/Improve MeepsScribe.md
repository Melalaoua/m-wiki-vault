
I'd like to know what Meeps "remembers" about me. I need to export mastra pg table on observational memory and chat logs to obsidian so I can grasp firmly what he remembers, keeps, about me


Prompt :

Read the context, the ADR and my following proposal to expand this project :

  - I'm missing some insight and what the agent "knows" about me. I'm lacking insight on what gets ingested at
  runtime when interacting with the model.

  I'm proposing the following improvements to answer this issue :
  1. Add a dynamic tracking on mastra memory (observationalMemory) from @src/mastra/memory/ that gets ingested in
  specific postgres table. Use context7 to understand how observational memory works and in which table it gets
  ingested. It might be intersted to have this content added to .md file so I can read them directly from my
  vault.
  
  2. Add the preprompt or data ingested by the model in an embed at each thread beginning or in a .md file.
  Everything that helps the model generating his response is visible and accessible for the human to proceed to
  target and track.

  Interview me relentlessly about every aspect of this until we reach a shared understanding. Walk down each
  branch of the decision tree, resolving dependencies between decisions one-by-one. For each question, provide
  your recommended answer.

  Ask the questions one at a time, waiting for feedback on each question before continuing. Asking multiple
  questions at once is biweldering.

  If a fact can be found by exploring the environment (filesystem, tools, etc.) look it up rather than asking me.
  The decisions, though, are mine put each one to me and wait for my answer.

  Do not act on it until I confirm we have a shared understanding.