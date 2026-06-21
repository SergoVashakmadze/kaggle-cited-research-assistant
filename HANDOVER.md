# HANDOVER — Cited Research Assistant (Kaggle Vibe Coding Capstone)

**What it is:** a small AI agent (Gemini function-calling) that takes a question, autonomously
calls a `web_search` tool as many times as it needs, and writes an answer with inline `[1] [2]`
citations and a Sources list of real URLs. Track: **Freestyle**.

**Repo:** https://github.com/SergoVashakmadze/kaggle-cited-research-assistant
**Local:** `~/Documents/D Drive/New Projects/kaggle-capstone-research-agent/`

---

## ✅ Status — TESTED & WORKING (2026-06-21)

Ran end-to-end with a real `GOOGLE_API_KEY` (live Gemini 2.5 Flash + live DuckDuckGo):
- `web_search` tool returns real results.
- The agent ran the function-calling loop autonomously (decided to search, then answered).
- Output had inline `[1]–[5]` citations + a Sources list of real, working URLs.
- `automatic_function_calling_history` correctly reports the number of tool calls.

No code changes needed — it runs as committed.

---

## How to run

### On Kaggle (this is the submission path)
1. New Notebook → upload `research_agent.ipynb` (or copy the cells).
2. **Settings → Internet → On.**
3. **Add-ons → Secrets →** add `GOOGLE_API_KEY` (free key: https://aistudio.google.com/apikey).
4. **Run all.** You should see the `search: '...'` lines, then a cited answer.
5. **Save / Publish as Public** → copy the notebook URL (this is your public code + project link).

### Locally
```bash
python3 -m venv .venv && source .venv/bin/activate
pip install -U google-genai ddgs
export GOOGLE_API_KEY=...            # your Gemini key
# open research_agent.ipynb in Jupyter/VS Code and Run All
```

---

## Files
| File | Purpose |
|---|---|
| `research_agent.ipynb` | The agent. **This is the code deliverable.** |
| `WRITEUP.md` | Kaggle Writeup (title + subtitle + body). Paste into a Kaggle Writeup. |
| `VIDEO_SCRIPT.md` | 2-minute demo script (shot-by-shot). |
| `voiceover/*.mp3` | Narration audio (neural voice) — `full_narration.mp3` is the full track. |
| `images/slide1–5.png` | Branded slides (also reusable as writeup images). |
| `research_agent_explainer.mp4` | 66s narrated explainer video (slides + narration). |
| `thumbnail.png` (560×280) | Card / thumbnail image. |
| `SUBMIT_CHECKLIST.md` | Step-by-step submission. |

---

## Submitting on Kaggle — exact steps

1. **Join** the competition: https://www.kaggle.com/competitions/vibecoding-agents-capstone-project
2. **Publish the notebook** (public) → get its URL.
3. **Host the video:** upload `research_agent_explainer.mp4` to **YouTube (unlisted)** or **Loom** → get the URL.
   *(Kaggle embeds a URL, not a raw file.)*
4. **New Writeup** → paste `WRITEUP.md`. Set **Title** ≤80 chars:
   `Cited Research Assistant: a web-search agent that answers with citations`
   **Subtitle:** `An AI agent that searches the web and answers with real, clickable citations.`
5. **Attach resources (in the writeup's Insert Resource panel):**
   - **Kaggle Code tab** → your published notebook ⭐ (the actual code submission)
   - **External Links tab** → this GitHub repo + the video URL
   - *(skip Models / Datasets / Benchmarks)*
6. **Project Links / Attachments** (bottom of editor) → add notebook + repo + video links.
7. **Video resource title/description:**
   - Title: `Cited Research Assistant — 2-min demo: an AI agent that web-searches and answers with citations`
   - Description: `A short walkthrough of the agent loop: one web_search tool plus a prompt. Gemini decides when to search, then answers with inline [1][2] citations and real, clickable source URLs.`
8. **Finish the submission checklist** (enables the Submit button) → **Submit**.
   Deadline: **July 6, 2026, 11:59 PM PT** (drafts are not judged).

---

## Deliverables status
| Requirement | Status |
|---|---|
| Public codebase | ✅ Notebook (publish on Kaggle) + this GitHub repo |
| Kaggle Writeup | ✅ `WRITEUP.md` (title + subtitle + body) |
| Video | ✅ `research_agent_explainer.mp4` (host on YouTube, then link) |
| Project link | ✅ the public notebook URL |
| Thumbnail / images | ✅ `thumbnail.png` + `images/slide*.png` |

**Optional polish:** record 20–30s of the notebook actually running and splice it into the
explainer for a stronger "live demo" — but the current explainer is a valid submission video.

---

## Notes
- Model: `gemini-2.5-flash` (swap to `gemini-2.0-flash` in the notebook if ever needed).
- Search: DuckDuckGo via `ddgs` — free, no extra key. May rate-limit under heavy use; just re-run.
- Cost: each `ask()` is a few cheap Gemini calls; trivial.
