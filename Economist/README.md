# economist
## Purpose
This folder contains the **theoretical analysis** that anchors the project:
- core game-theoretic results and equilibrium logic,
- welfare/efficiency and fairness benchmarks,
- bridges from PS1 (Cournot) to PS2 (common-value first-price auctions).

It provides clean statements that your computational and behavioral components
can reference directly.

---

## 1) Equilibrium & Comparative Statics (Concise)

### Cournot (PS1 recap)
- Setup: inverse demand \(p(Q)=60-Q\), two firms, zero MC.
- Best replies \(q_i=(60-q_{-i})/2\) ⇒ unique continuous NE \(q_1=q_2=20\).
- Welfare at NE: \(Q=40, p=20\); DWL vs. first-best \(Q=60\).
- Fairness: with symmetry, payoffs are equal (equity; no envy).

> Why the discrete demo shows 3 pure NEs \((10,30),(20,20),(30,10)\): it is a **grid artifact** of \(\{10,20,30\}\) approximating the continuous solution near 20; all produce \(Q=40, p=20\) (teaching/visualization device).

### Auctions (PS2 foundations)
- **Common-value FPSB** with affiliated private signals \(s_i\): winning is informative that others saw lower signals ⇒ **winner’s-curse** unless bidders correct and shade.  
- Comparative statics:
  - Larger noise \(\sigma\) ⇒ stronger curse (top order statistic further above \(V\)).  
  - More bidders \(n\) ⇒ stronger curse (winning is more selective).  
  - Public information ⇒ mitigates curse (reduces posterior dispersion).

These guide your hypotheses and treatment design.

---

## 2) Efficiency, Welfare, Fairness

- **Efficiency**: compare realized allocation (winner & price) with benchmark where bids reflect properly corrected values; track **revenue, ex-post losses, allocative efficiency**.
- **Fairness**: with symmetric priors/rules, focus on **procedural fairness** (same information & payment rule), and on **distribution of ex-post losses** (undesirable concentration).

---

## 3) What Reviewers Will Look For (Theory ↔ Evidence)

- Each figure’s **title/caption must match the content** (strategies, equilibria, parameters) one-to-one. Add a short “Source:” line pointing to the script or solver export used to generate it. :contentReference[oaicite:2]{index=2}
- When comparing models vs. treatments, follow **ceteris paribus**: vary **only one factor at a time**; theory section should pre-state which comparative static is being tested (noise \(\sigma\), bidders \(n\), info disclosure). :contentReference[oaicite:3]{index=3}

Checklist:
- [ ] Each claim (NE, welfare, fairness) appears once, with symbols defined.
- [ ] Each plot/table cites its generating source (script / solver path).
- [ ] Comparative static in text matches the one actually varied in code/experiments.

---

## 4) Pointers for Reproduction
- Theory notes / derivations: `notes/`  
- Strategic-form / equilibrium diagrams: `figs/`  
- If you export any matrices or GTE screenshots, keep a tiny `SOURCE:` line in captions.

---

## 5) References (selected)
Milgrom & Weber (1982); Wilson (1977); Kagel & Levin (1999); Camerer (2003).  
(Full bibliography in `/references/`.)
