# Computational Scientist

This folder contains the code and screenshots for **Part 2**:
- **Normal-form modeling & computation** of the Cournot game using `NashPy`.
- **GTE (Game Theory Explorer)** screenshots for the extensive-form model.

---

## Files
- `problem_set.ipynb` — Google Colab–exported notebook for payoff construction and equilibrium computation.
- `screenshots/`
  - `M1.png`, `M2.png` — displayed payoff matrices (Player 1 / Player 2).
  - `OP.png` — NashPy equilibrium output (support enumeration).
  - `GTET.png` — extensive-form tree in GTE (simultaneous move modeled with one information set for Firm 2).
  - `GTESOL.png` — GTE “Solve” panel (NE/SPNE outputs).
  - `GETF.png` — GTE strategic-form grid with payoffs and equilibrium markers.

---

## How to Run
### Option A — Google Colab
1. Open the notebook in Colab:
   - Upload `notebook.ipynb` to Colab, or drag from Drive.
2. Make sure the Python runtime is 3.10+ and run the first `pip` cell:
   ```python
   !pip -q install nashpy numpy matplotlib

