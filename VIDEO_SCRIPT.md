# Demo Video Script — Cited Research Assistant

**Length:** ~2:00. **Format:** screen recording of the Kaggle notebook running + voiceover (no face needed).

**Before recording:** open the published notebook, confirm `GOOGLE_API_KEY` secret is set and Internet is On, and do one full top-to-bottom run so outputs are warm.

---

### Shot 1 — Hook (0:00–0:20)
**On screen:** the notebook title cell + the question in the first `ask(...)` cell.
**Voiceover:**
> "This is a research assistant agent. You ask it a question, and instead of answering from memory, it searches the web, reads what it finds, and writes an answer with real citations. Here's how it works."

### Shot 2 — The tool (0:20–0:40)
**On screen:** scroll to the `web_search` function and the `ask()` function with `tools=[web_search]`.
**Voiceover:**
> "The whole agent is about forty lines. There's one tool — a web search function — and a system prompt telling the model to search, then answer with numbered citations and never invent a source. We hand the tool to Gemini, and it runs the loop itself."

### Shot 3 — Run it — the agent loop (0:40–1:20) — MAIN SHOT
**On screen:** run an `ask(...)` cell. Let the `searching: '...'` lines stream as the agent fires queries; then the answer prints.
**Voiceover:**
> "Watch the agent work. It decides what to search for — here it runs a couple of queries, refining as it goes. We didn't script that; the model chose how many times to search. Then it writes the answer, with inline citations one, two, three… and look — it tells us it made N search calls. That's the agent loop: decide, act with a tool, read, repeat, then synthesise."

### Shot 4 — Citations you can check (1:20–1:45)
**On screen:** scroll to the answer's "Sources" list; click (or hover) one URL.
**Voiceover:**
> "Every claim is tied to a source, and the sources are real URLs you can open and verify. That's the difference between a confident guess and a grounded answer."

### Shot 5 — Close (1:45–2:00)
**On screen:** edit the last cell's question to a new one and run it.
**Voiceover:**
> "Change the question and it just works. One tool, a natural-language prompt, and an autonomous loop — built entirely with vibe coding. That's the research assistant agent."

---

## Caption cheat-sheet (optional overlays)
- `One tool: web_search`
- `The model decides when & how often to search`
- `Answers grounded in real, cited sources`
- `~40 lines · Gemini function-calling · vibe-coded`
