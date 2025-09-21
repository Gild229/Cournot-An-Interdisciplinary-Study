# Problem Set 2 — Common-Value First-Price Auction (Mechanism Design)

> Course: COMSCI/ECON 206 • Author: **Yanzhen Liu**  
> Snapshot: `<git short-hash>` • Last update: 2025-09-21

---

## 1) Overview

This directory contains the mechanism-design component of **Problem Set 2**: a **common-value, first-price, sealed-bid** auction with experimental variations (treatments vs. control), prompts for LLM bidders, session logs, and analysis figures. It is structured to satisfy the rubric: single entry README, supporting assets in subfolders, metrics/plots for evidence, and literature-backed rationale.

---

## 2) Design & Variations

- **Value:** \( V \sim \mathrm{Uniform}[1000, 1500] \).  
- **Signals:** Each bidder \(i\) observes \( s_i = V + \varepsilon_i\), where \( \varepsilon_i \sim \mathcal N(0,\sigma^2)\) i.i.d.  
- **Action / Payment:** First-price sealed bid; highest bid wins and pays own bid (ties random).  
- **Profit:** Winner’s ex-post profit \(= V - b\) (else \(0\)).  

**Treatments (vs. Control)** — vary one dimension at a time:
1. **Noise level \(\sigma\)**: medium vs. high (tests information dispersion).  
2. **Number of bidders \(n\)**: e.g., 3 vs. 5 (tests order-statistic effect).  
3. **Public information**: add a credible public signal about \(V\) (tests mitigation).  
4. **Winner’s-curse reminder**: add a short cue highlighting selection bias when winning.

---

## 3) Hypotheses (with literature support)

- **H1 (Winner’s curse):** In common-value FPSB, bidders who under-correct tend to incur negative profits upon winning.  
  *Wilson 1977; Milgrom & Weber 1982.*

- **H2 (Noise ↑ → curse ↑):** Larger \(\sigma\) increases signal dispersion and the upward bias of the top order statistic; without sufficient correction, negative-profit incidence rises.  
  *Wilson 1977; Milgrom & Weber 1982.*

- **H3 (More bidders ↑ → curse ↑):** As \(n\) grows, “winning implies others saw lower signals” becomes stronger; absent extra shading, overbidding risk increases.  
  *Milgrom & Weber 1982 (affiliation and linkage).*

- **H4 (Public info → mitigates):** Public information reduces posterior dispersion and the “surprise of winning,” mitigating overbidding.  
  *Milgrom & Weber 1982; Campbell–Kagel–Levin 1999 (lab patterns).*

- **Behavioral rationale:** Bidders often use coarse heuristics (fixed-fraction shading) and are frame-sensitive; a concise reminder improves correction and reduces overbidding.  
  *Camerer 2003, ch. 5.*

---

## 4) Prompts (exact text)

> 将以下两段另存为文件：`prompts/control.txt` 与 `prompts/treatment_reminder.txt`。  
> 在轮换实验中，某一轮仅对一个模型添加“Reminder”段落，其余为 Control。

**`prompts/control.txt`**
