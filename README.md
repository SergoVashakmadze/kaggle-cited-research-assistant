# Cited Research Assistant — Kaggle Vibe Coding Capstone

A tiny AI agent (Gemini function-calling) that searches the web and answers questions with real citations. Built for the *AI Agents: Intensive Vibe Coding* capstone — **Freestyle** track.

## Files
- `research_agent.ipynb` — the agent (this is the public code **and** the runnable project link once uploaded to Kaggle).
- `WRITEUP.md` — the Kaggle Writeup (paste into a Kaggle Writeup).
- `VIDEO_SCRIPT.md` — 2-minute demo script.
- `SUBMIT_CHECKLIST.md` — step-by-step submission.

## Run it (Kaggle)
1. New Notebook → upload `research_agent.ipynb` (or copy the cells).
2. *Settings → Internet → On.*
3. *Add-ons → Secrets →* add `GOOGLE_API_KEY` (get one at https://aistudio.google.com/apikey).
4. Run all cells.

## Run it (locally)
```bash
pip install -U google-genai ddgs
export GOOGLE_API_KEY=...   # your Gemini key
# then run the notebook in Jupyter/VS Code
```
