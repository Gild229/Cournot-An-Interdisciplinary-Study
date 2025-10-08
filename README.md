# The Future of Auctions with AI Agents: Beating the Winner’s Curse with a Database-Backed Pipeline

Author: Yanzhen Liu (Duke Kunshan University)  
Course: COMSCI/ECON 206 — Computational Microeconomics  
Term: Autumn 2025  
Last update: 2025-10-08  

---

## Abstract

We study how AI/LLM agents bid in common-value first-price auctions (CV-FPSB) and test mechanism interventions that mitigate the winner’s curse. Building on game-theoretic benchmarks, we implement a database-backed experimental pipeline with standardized logs, scripted figures, and one-click reproduction. Treatments include an explicit winner’s-curse reminder and a noisy public signal. Across seeds/temperatures/noise levels and bidder counts, we find: (i) shading increases, (ii) loss events decline, and (iii) revenue and stability improve under treatments. We discuss portability to simplified voting rules and align the work with SDG-8/9 by emphasizing trustworthy, auditable AI infrastructures.

---

## Authors & Roles

- Yanzhen Liu — Economist (theory & benchmarks), Computational Scientist (code, simulation, figures), Behavioral Scientist (LLM agents), Mechanism Designer (treatments, institutional links)

(If collaborators join, add them here and assign roles explicitly.)

---

## Disclaimer

This repository supports the final research proposal submitted to COMSCI/ECON 206: Computational Microeconomics, instructed by Prof. Luyao Zhang at Duke Kunshan University in Autumn 2025.

---

## Acknowledgments

Thanks to course staff and classmates for feedback; open-source communities behind NashPy, QuantEcon, GTE, oTree, and model providers for LLM APIs; and the broader reproducible-science community whose tools enable auditable workflows.

---

## Statement of Growth

This project synthesizes my PS1 and PS2 work into a single, auditable pipeline. I grew from (i) verifying theory computationally (Cournot, equilibria) to (ii) running AI-agent experiments with clean logging and scripted figures, and (iii) framing mechanism insights within institutional and SDG contexts. The emphasis on reproducibility and transparency reshaped how I design, report, and review computational experiments.

---

## Table of Contents

- [`economist/`](economist/) — Game/theory notes, symbols, and equilibrium references  
- [`computational_scientist/`](computational_scientist/) — Notebooks, scripts, solver outputs  
- [`behavioral_scientist/`](behavioral_scientist/) — oTree (if any), LLM prompts & transcripts  
- [`mechanism_design/`](mechanism_design/) — Auction design, treatments, configs  
- [`visualizations/`](visualizations/) — All figures (auto-generated)  
- [`docs/`](docs/) — Report.pdf, Poster.pdf, FieldTripReflection.md  
- [`references/`](references/) — Key literature and tool citations  
- [`README.md`](README.md) — You are here

---

## Navigation Instructions (where to find things)

- Equilibria computation & benchmarks  
  - Code & notebooks: `computational_scientist/`  
  - Theory notes: `economist/`
- Mechanism design & experiments  
  - Auction configs & treatments: `mechanism_design/`  
  - LLM prompts & transcripts: `behavioral_scientist/prompts/` and `behavioral_scientist/transcripts/`
- Visualizations & outputs  
  - Auto-generated plots: `visualizations/` (SVG/PDF/PNG)  
  - Figure scripts: `computational_scientist/scripts/`
- Docs for reviewers  
  - Final Report.pdf and Poster.pdf: `docs/`  
  - FieldTripReflection.md: `docs/`

---

## Method & Data (concise)

- Environment: CV-FPSB with \(V \sim U[1000,1500]\); 3 bidders; each observes private signal \(s_i\).  
- Treatments: Control / Winner’s-Curse Reminder (pre-bid nudge) / Public Signal (noisy common signal).  
- Logging schema: `run_id, agent_id, seed, sigma, treatment, signal, bid, V, profit, time`.  
- Ethics & Transparency: Prompt templates, model/version, temperature, and seeds are disclosed in this repo; logs are anonymized; all figures regenerate from scripts.

---

## Reproduction Map (5-minute quick start)

1. Shading distribution (Control vs Treatment)  
   - Script: `computational_scientist/scripts/plot_shading.py`  
   - Input: `mechanism_design/logs/*.csv`  
   - Output: `visualizations/shading_by_treatment.svg`  
   - Paper/Poster: Fig. 1

2. Negative-profit rate and revenue comparison  
   - Script: `computational_scientist/scripts/plot_loss_revenue.py`  
   - Input: `mechanism_design/logs/*.csv`  
   - Output: `visualizations/loss_revenue_bar.svg`  
   - Paper/Poster: Fig. 2

3. Theory vs observed bidding slope (signal→bid)  
   - Script: `computational_scientist/scripts/plot_signal_bid_slope.py`  
   - Input: `mechanism_design/logs/*.csv`  
   - Output: `visualizations/signal_bid_slope.svg`  
   - Paper/Poster: Fig. 3 (optional)

4. Regenerate all figures  
   - Script: `computational_scientist/scripts/make_all.py`  
   - Outputs: `visualizations/`  
   - Paper/Poster: all figures

---

## Repository Structure (role-based)

