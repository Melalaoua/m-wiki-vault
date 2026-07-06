---
date: 2026-04-14
---
I refactored the whole Meepsscribe system. I was not content with the actual result and architecture.

Instead I started from Mastra default project, and worked my way all the way up to the framework I wanted.

I took from the previous folder version & the autoducteur (friend's similar project type).

Heavy usage of AI for this.

The project structure is similar to previous one but with few tweaks and proper code.

Used the hexagonal pattern (ports & adapters). The Agent is clearly distinguished from discord and can be plugged to various adapters.

Added the RAG system that automatically embeds the obsidian vaults.

There's still a lot to do but i'm more focused and precise in my work.


### April, the 15th

Scraping the dexter repository to find useful code


### April, the 16th
Struggling, did some cleanup code.

What's needs to be done :
- Create tools for the agents : search-web, read pdf (needs to save the file and read it ?)
- Create the cron jobs
- Create the graphRAG tool
- Create the Financial Advisor  -> fetch finance metrics & gives advices.
- Create the Finance investor -> Standalone bot
- Create the mail parser ? spending nudges etc.


### June, the 04th
Time passed, i was busy with the [[OAD(log) - MVP Sprint]]. Coming back to this project with fresh eyes, i want to refactor once again this project.

Came accross the [[M-wiki(doc) - llm wiki|Karpathy wiki]] that is very similar to the M-wiki. 

problem with the current M-wiki is multi-fold : 
- Raw data is not kept, immediately ingested and synthesized.
- No schema layer
- Scale is too big, trying to fit it all in one llm ? *Should I use sub-agents each managing their own data turf in karpathy wiki style ?*
- In contrary to K-wiki, i want my wiki to be equally managed by the human and the llm. I don't want the llm to be own proprietary to the wiki. That means i cannot fully implements the K-wiki style, it'll cause friction between both.
- LLM must be subsized to an assistant - not the master - of the data.
- I like the K-wiki way of ingesting/managing data : 3 simple layer, 3 simple operations. Data flows inward and in one direction. In the M-wiki, the data 
- Applying the K-wiki to smaller structure gives the opportunity to add index.md files to each. But that implies creating folder foreach K-wiki, we loose the readability of second brain's. All files are nested in their own, serependity and one-layer is lost.

Meeps is hosted on a distant server. It got its own version (githup repository) of the phd and personal brains. I got my own. Two entities has access to the same knowledge graph. The problem i see is two-fold : The human will have a much smaller data ingestion and processing than the LLM (the llm is 24/7 and exclusively on the task), on the other hand, the llm is lacking the persistence and connection of the data. it doesn't have this natively, the wiki provides that, to some extent.

Conventions : 
1. Commit conventions applied to name files ? I like this idea, keeps the file name connected to one another. The action is in the '()' and easily readable.
2. Usual yaml conventions with tags, date, ...


