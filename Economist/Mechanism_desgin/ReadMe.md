# Mechanism_design

## Goal
Design and evaluate mechanisms that **reduce the winner’s curse** in common-value first-price auctions with AI/LLM agents, using **auditable, reproducible** experiments.

---

## 1) Environment (default)
- Auction: common-value, first-price, sealed-bid (CV-FPSB).
- Value: \(V \sim U[1000,1500]\).
- Signals: \(s_i = V + \varepsilon_i\), \(\varepsilon_i \sim \mathcal N(0,\sigma^2)\) i.i.d.
- Bidders: baseline \(n=3\).  
- Profit: winner’s ex-post \(= V-b\) (else 0).

Files:
- `configs/default.yaml` — all knobs (n, σ, seeds).
- `prompts/` — control & treatment prompt templates.

---

## 2) Treatments (one factor at a time)

**Do NOT confound model and treatment in the same comparison; hold one fixed.**  
This follows the ceteris-paribus design required in the feedback. :contentReference[oaicite:4]{index=4}

- T0 Control — rules only.  
- T1 Reminder — pre-bid nudge describing the winner’s-curse selection bias.  
- T2 Public signal — add a noisy common signal to prompts.  
- (Optional) T3 Higher noise \(\sigma\).  
- (Optional) T4 More bidders \(n\).

Recommended run plans:
- Plan A (treatment effect): **fix model**, vary T0 vs. T1 (and/or T2).  
- Plan B (model differences): **fix treatment** (e.g., T0), compare models.

---

## 3) LLM Agent Settings (documented for transparency)
- Model / version; decoding temperature; max tokens; seeds.  
- Output contract: “print a single number (your bid)”.  
- Logging schema (CSV):  
  `run_id, model, agent_id, seed, n, sigma, treatment, signal, bid, V, win, profit, time`

Ethics & transparency: prompt templates and settings are versioned; logs are anonymized.

---

## 4) Metrics & Hypotheses

**Primary metrics**
- Shading \(= s_i - b_i\) (higher is safer).  
- Negative-profit rate (loss events).  
- Seller revenue and across-round variance.  
- (Optional) Allocative efficiency.

**Hypotheses (theory-driven)**
- H1: Reminder / Public signal ⇒ shading ↑, loss rate ↓, revenue/stability ↑.  
- H2: \(\sigma ↑\) ⇒ stronger curse (loss rate ↑) if bidders under-correct.  
- H3: \(n ↑\) ⇒ stronger curse via order-statistic selection; mitigation via info.

(These mirror the PS2 write-up and lecture guidance.) :contentReference[oaicite:5]{index=5}

---

## 5) Experimental Design Tables

### 5.1 Treatment vs. Control (fixed model)
| Model | Control (mean) | Treatment (mean) | Δ (T − C) |
|---|---:|---:|---:|
| GPT-X | shading / loss% / revenue | … | … |
| Claude-X | … | … | … |
| DeepSeek-X | … | … | … |

### 5.2 Cross-model (fixed treatment)
| Treatment | GPT-X | Claude-X | DeepSeek-X |
|---|---:|---:|---:|
| Control | shading / loss% / revenue | … | … |
| Reminder | … | … | … |
| Public signal | … | … | … |

> Fill these after runs. This structure ensures that **only one factor changes at a time**, satisfying the review requirement for clean inference. :contentReference[oaicite:6]{index=6}

---

## 6) Reproduction Map

- Shading distribution  
  - Script: `../computational_scientist/scripts/plot_shading.py`  
  - Input: `mechanism_design/logs/*.csv`  
  - Output: `visualizations/shading_by_treatment.svg`

- Loss rate & revenue bars  
  - Script: `../computational_scientist/scripts/plot_loss_revenue.py`  
  - Input: same logs  
  - Output: `visualizations/loss_revenue_bar.svg`

- Signal→bid slope (theory vs. observed)  
  - Script: `../computational_scientist/scripts/plot_signal_bid_slope.py`  
  - Output: `visualizations/signal_bid_slope.svg`

- Regenerate all  
  - Script: `../computational_scientist/scripts/make_all.py`  
  - Output dir: `visualizations/`

Each figure caption should include a short **Source:** line with the script path.  
(Also fix any **title–screenshot mismatches** before release.) :contentReference[oaicite:7]{index=7}

---

## 7) Reporting Conventions

- Always report **N** (rounds × models × seeds) and **95% CIs** (bootstrap) for all metrics.  
- When rotating treatments across models, still publish a **factor-isolated table** (as above) to avoid ambiguity. :contentReference[oaicite:8]{index=8}

---

## 8) SDG note (brief)
This mechanism-testing workflow supports **SDG-8** (efficient, trustworthy markets) and **SDG-9** (open, auditable infrastructure) by standardizing logs, scripts, and reproducible figures.

---

## 9) References
See `/references/`. Core theoretical anchors and software citations are already listed in the PS2 write-up. :contentReference[oaicite:9]{index=9}

