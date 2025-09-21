# Cournot & Auctions — Problem Set 1 (Revised) + Problem Set 2

> Course: **COMSCI/ECON 206**  
> Author: **Yanzhen Liu**  
> Last update: YYYY-MM-DD • Snapshot commit: `<hash>`  ← _用 `git rev-parse --short HEAD` 替换_

---

## 0) Overview

This repo collects all revised materials for **Problem Set 1 (Cournot)** and the **mechanism-design work for Problem Set 2 (common-value auctions)**, including:
- Updated PS1 manuscript (continuous vs. discrete clarification), **Acknowledgments**, and **Point-by-Point Response**.
- Computation assets (Nashpy/QuantEcon, GTE screenshots), **oTree app** and session logs.
- PS2 auction design (control/treatments), prompts, LLM sessions, and metrics/plots.

> 📌 According to the course rubric, all materials are indexed from the root README, and supporting assets are placed under the role-based subfolders.

---

## 1) Repository Structure


Quick links (fill in when available):
- 📄 **PS1 PDF**: `Economist/ps1_main.pdf`  
- 🧩 **oTree package**: `behavioral_scientist/opc-new_project.otreezip`  
- 🖼 **Flowcharts**: `Economist/figs/ps1_roadmap.pdf`, `mechanism_design/figs/ps2_roadmap.pdf`  
- 📊 **PS2 metrics**: `mechanism_design/figs/` (shading / neg-profit / revenue)  
- 🧾 **Refs**: `references/` 

---

## 2) Problem Set 1 — What changed & where to find it

- **Acknowledgments** and **Appendix: Point-by-Point Response** are integrated in the PS1 LaTeX/PDF.  
- Clarified that the continuous Cournot model has **unique** NE (20,20) while the discrete grid `{10,20,30}` yields **three** pure NE — a **discretization artifact** for visualization/implementation (GTE/oTree).  
- Standardized figure captions with **Source:** lines and improved resolution.

Open:
- `Economist/README.md` — mini-index for theory sections and references  
- `computational_scientist/README.md` — notebook + screenshots mapping  
- `behavioral_scientist/README.md` — oTree install, session screenshots, LLM transcript

---

## 3) How to reproduce

### 3.1 PS1 (Cournot)

**A) Code (Nashpy/Colab)**
1. Open `computational_scientist/notebook.ipynb` (Colab ok).  
2. Run all cells to generate payoff matrices for `{10,20,30}` and compute equilibria.  
3. Exports will be placed under `computational_scientist/screenshots/` (matrices/solver).

**B) GTE (optional)**
- Use the GTE project file (if included under `Economist/figs/`) to export tree, solver panel, and 3×3 strategic form.

**C) Build PS1 PDF (LaTeX)**
```bash
cd Economist
# if you have tex sources:
# latexmk -pdf ps1_main.tex
