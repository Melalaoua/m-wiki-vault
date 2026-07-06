
I've found 2 type of llm wiki that fit my [[M-wiki - Bibliography]] idea :

 ### 1. The [karpathy llm wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) 
This is pretty much my idea. I don't know if my idea is novel and came without any hint of this existing or unconsciously I copied this. Anyway I'm flattered to be on the same page as mind like him.

The Karpathy Wiki LLM is incrementally built and maintened as a persistent wiki : a structured collection of .md files ([[MeepsScribe]])


##### 3-layers.
- **==Raw sources==** -- Curated collection of source documents (can be anything) : articles, papers, images, data files. Immutable and source material for the llm.
- **==The Wiki==** -- Direct of llm-generated md files. Summaries, entity pages, concept pages, comparisons, overview, synthesis. This layer is entirely owned by the llm. It creates pages, updates them when a new sources arrive, maintains cross-references, keeps everything consistent.
- **==The Schema==** -- a document (e.g CLAUDE.md) that tells the LLM how the wiki is structured. What the conventions are, what workflows to follow when ingesting sources, answering questions, maintaining the wiki.


##### Operations.
3 types of operations are mandatory for the K-Wiki.
```
ingest : When a new source arrive in the raw layer, the llm process it (feedback loop with the human) and updates the wiki. A single source can touche several wiki pages. A log can be maintained in the process.
```
```
Query : Use the LLM to navigate the knowledge base. Good answers can be filed back into the wiki as new pages.
```
```
lint : a heartbeat regularly tells the LLM to lint & monitor the state of the wiki llm to keep the data fresh.
```


##### Indexing and logging.
- **index.md** : catalog of everything in the wiki. Each page is listed in this index, with a one-line summary, optionally metadata like data or source count. The index.md is read first by the llm before exploring the wiki. (Works well at ~100 pages).

- **log.md** ; chronological : append-only record of what happenned and when : ingests, queries, lint passes. If each entry starts with a consistent prefix (e.g `## [2026-04-02] ingest | Article Title`), the log becomes parseable with simple unix tools `grep "^## \[" log.md | tail -5` gives you the last 5 entries. The log gives you a timeline of the wiki's evolution and helps the llm understand what's been done recently.


### My Thoughts on this.

The karpathy is closely similar to my project [[MeepsScribe]] but there are some essential differences that i will list :

1. Scale : karpathy wiki looks to be kept small in order to be effective. In the opposite, i would like my meepsscribe wiki to encapsulate all my pro & personal life (in 2 different wiki).
2. Actionability : the k-wiki is supposed to be modified only by the llm. The M-wiki should be tightly coupled between human usage and llm-usage. Both works in hands, modifying each-other works as times goes.


There are essentials points from the K-wiki that I like and should helps me enhance my M-wiki. The raw and schema layers are interesting way to organize data. The first avoids data loss, keeping the raw sources beyond the abstraction layer, the latter keep the llm in check and allow structure to resist the entropy of time. 


I'll structure my thoughts in [[M-wiki(doc) - Build the Brain]]