---
type: source
title: "Prevent cognitive debt by manually retyping LLM-generated code"
citekey: ankursethi2026prevent
source_type: article
captured: 2026-08-09
site: ankursethi.com
url: https://ankursethi.com/blog/prevent-cognitive-debt-by-manually-retyping-llm-generated-code/
raw: personal/raw/ankursethi.com/prevent-cognitive-debt-by-manually-retyping-llm-generated-code.md
aliases: []
tags: [source, personal]
updated: 2026-08-09
status: developing
---

# Prevent cognitive debt by manually retyping LLM-generated code

Original: [[personal/raw/ankursethi.com/prevent-cognitive-debt-by-manually-retyping-llm-generated-code]]

# Prevent cognitive debt by manually retyping LLM-generated code

Source: [ankursethi.com article](https://ankursethi.com/blog/prevent-cognitive-debt-by-manually-retyping-llm-generated-code/) by Ankur Sethi. Captured 2026-08-09.

Sethi still uses LLM coding assistants on personal projects, but rejects letting them "one-shot" features or directly edit files, because doing so leaves him disoriented and accumulating what he calls **[[Cognitive Debt]]** — a loss of understanding of his own codebase that he'd eventually have to "pay back."

His workaround: he instructs the assistant (via agents/instruction files) to never create, edit, move, rename, or delete project files, and never run state-changing commands — instead it must show proposed edits and commands in the chat, which he then **types in manually**. He also tells it not to explain syntax/APIs/concepts unless asked, since he's an experienced developer and just wants the boring parts fast-forwarded, not a tutor.

Effects he reports:
- He estimates this makes him ~2x faster than not using an LLM at all, versus ~10x for developers who let the LLM edit directly — a deliberate trade of speed for comprehension.
- Manually retyping code forces him to slow down enough to catch hallucinations and bad design choices.
- He builds a genuine mental model and a "spatial map" of the codebase — knowing exactly where every piece of functionality lives — which in turn improves his ability to prompt/instruct the LLM later.
- He likens this to classic advice given to him as a teenage programmer: never copy-paste from books/blogs/forums, always type examples out by hand to force real comprehension.

He frames the personal practice as a hedge against an industry-wide problem: engineers increasingly ship code they don't understand because they let LLMs "roam free," and he sees fully offloading understanding to a "slop machine" as heading toward "professional malpractice."

This connects to broader themes of [[Cognitive Attention Degradation]] and disciplined, deliberate engagement with a craft rather than passive consumption of automated output — similar in spirit to [[Deliberate Practice in Gaming]]'s emphasis on active, effortful repetition over passive execution.

## Key claims

- Sethi restricts his coding assistant to proposing edits/commands only in chat, never touching project files or state directly, so he can manually retype everything himself. ([[personal/raw/ankursethi.com/prevent-cognitive-debt-by-manually-retyping-llm-generated-code#I have these instructions in all the agents files in my personal projects]]) — "Never create, edit, move, rename, or delete project files unless I explicitly ask you to do so. Instead, show me every proposed edit in the chat so I can type it in manually."
- He estimates this workflow is about 2x faster than not using an LLM, versus roughly 10x for developers who let the LLM edit directly. ([[personal/raw/ankursethi.com/prevent-cognitive-debt-by-manually-retyping-llm-generated-code#Using LLMs this way]]) — "Instead of being 10x faster, I'm probably only 2x faster. But what I lose out on in terms of speed, I gain in terms of a deeper understanding of my code."
- Manually typing the code slows him down enough to catch hallucinations or bad design decisions in the LLM's output. ([[personal/raw/ankursethi.com/prevent-cognitive-debt-by-manually-retyping-llm-generated-code#As I manually type]]) — "Typing the code myself forces me to slow down, which means I'm more likely to detect hallucinations or bad design choices the LLM might have made."
- The practice builds a 'spatial map' of the codebase, improving both his own velocity and his ability to prompt the LLM effectively in future. ([[personal/raw/ankursethi.com/prevent-cognitive-debt-by-manually-retyping-llm-generated-code#Most importantly]]) — "this workflow allows me to build a _spatial map_ of my codebase. I know where every bit of functionality lives in the codebase... it also makes it easier for me to better prompt and instruct the LLM in the future."
- He worries the software industry is accumulating collective cognitive debt from AI-generated code that will eventually have to be repaid. ([[personal/raw/ankursethi.com/prevent-cognitive-debt-by-manually-retyping-llm-generated-code#closing]]) — "I fear the software industry is taking on a large amount of cognitive debt that we'll have to pay back very soon. There will come a time when we no longer understand how large parts of our digital infrastructure are put together."
