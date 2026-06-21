# Cited Research Assistant: a web-search agent that answers with citations

> **An AI agent that searches the web and answers with real, clickable citations.**

**Track: Freestyle** · *AI Agents: Intensive Vibe Coding* capstone

> 📓 **Notebook (code + run it):** `<PASTE KAGGLE NOTEBOOK LINK>`
> 🎥 **Demo video:** `<PASTE LINK>`

---

## TL;DR

Ask a question. The agent **plans, calls a web-search tool as many times as it needs, reads the results, and writes a clear answer with inline citations `[1] [2]` and a Sources list** — so every factual claim is traceable back to a real URL. It's a small, honest demonstration of the core agent pattern from the course: *a model given a tool and the freedom to decide when to use it.*

## Problem

Large language models answer fluently but **from memory** — they can be out of date and they don't show their work. For anything factual, you can't tell what's grounded and what's invented, and there are no sources to check. That's exactly the gap autonomous agents are meant to close: give the model a **tool** to fetch real information, and a **workflow** for citing it.

## Solution

A single-file agent built with **Gemini function-calling**:

1. A `web_search(query)` Python function is exposed to the model as a tool.
2. A system prompt defines the workflow: *search → read → answer with citations → list sources; never invent URLs.*
3. Gemini's automatic function-calling runs the loop — it decides how many searches to do and with what queries, then synthesises a cited answer.

```
question ─▶ agent ──search("…")──▶ web  ──results──▶ agent
                 └──search("…", refined)──▶ web ──▶ agent
        ◀── answer with [1][2] citations + Sources list ──┘
```

The number of searches isn't scripted — the agent keeps going until it has enough, and the notebook prints each query so you can watch the loop happen.

## How it uses agent technologies (course concepts)

- **Tool definition & calling** — `web_search` is a real callable tool; the model invokes it with arguments it chooses.
- **Autonomous loop** — multi-step, model-driven control flow (visible via a "made N web_search call(s)" counter), not a hard-coded pipeline.
- **Grounding & trust** — the answer is tied to retrieved sources and cited, so claims are checkable instead of taken on faith.
- **Vibe coding** — the whole agent is ~40 lines of Python steered by a natural-language system prompt; behaviour is shaped by words, not control code.

## Implementation

- **Model:** Gemini 2.5 Flash via the `google-genai` SDK.
- **Tool/search:** DuckDuckGo (`ddgs`) — free, no extra API key.
- **Runtime:** a Kaggle Notebook. Add a `GOOGLE_API_KEY` secret, turn Internet on, run top-to-bottom. The notebook is the public codebase *and* the runnable project link.

## User value

A quick, source-grounded answer to a factual question, with citations you can actually click — useful for research, fact-checking, and as a template anyone can extend with more tools (a calculator, a PDF reader, a date tool) to build a more capable assistant.

## Honest limitations

- Answer quality tracks search-result quality; obscure queries return weak sources.
- The model maps citations to the sources it was given — always sanity-check the linked URLs for anything important.

## Next steps

- Add more tools and let the agent choose among them.
- Add a verification pass that re-checks each citation supports its claim.
- Wrap it in a small chat UI for multi-turn follow-ups.

---

*Built conversationally (vibe coding): a natural-language system prompt plus one tool is enough to make a useful, source-grounded agent.*
