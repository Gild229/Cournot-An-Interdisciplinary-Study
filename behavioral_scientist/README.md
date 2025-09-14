# Behavioral Scientist

This folder documents **Part 3** of the project: oTree implementation, human session screenshots, and LLM session comparison.

---

## Folder Structure

- `opc-new_project.otreezip` — Packaged oTree app (ready to run locally or on oTree Hub).
- `screenshots/`
  - `IN.png` — Instructions page.
  - `DE.png` — Decision entry page.
  - `R1.png`, `R2.png`, `R3.png` — Session results for three rounds (two players).
- `llm/`
  - `prompts.txt` — Prompts given to the LLM (round-by-round instructions).
  - `transcript.md` — Full transcript of the conversation with the LLM.
  - `settings.json` — `Claude Sonnet 4`
  - C1-C5 Screenshots

---

## oTree App

### Installation & Running

1. **Download app**  
   Save `opc-new_project.otreezi` to a folder (e.g., `~/cs206`).

2. **Install oTree**
   ```bash
   pip3 install -U otree
3. **Start local server**
   otree devserver
4. Navigate to http://localhost:8000 to access the app, create a session, and run the Cournot demo.

