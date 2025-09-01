# Palantir (PLTR) Earnings Event – Implied Volatility Smile Study

This mini-project investigates how Palantir’s (PLTR) implied volatility (IV) smile behaved around an earnings release and compares the market’s implied move with the realised move. It also illustrates the payoff of a short ATM straddle.
---

## Objectives

* Build IV smiles (IV vs strike/spot) for a near-term expiry around earnings.
* Quantify the implied move from options vs the realised move in the stock.
* Illustrate the short straddle payoff and how outcomes depend on realised vs implied volatility.

---

## Data

* **Source:** `yfinance` (Yahoo Finance API wrapper).
* **Scope:** Demonstration on PLTR earnings, 4 Aug 2025. Extendable to multiple events for robustness.

---

## Repository Structure

```
.
├── notebooks/
│   └── 01_pltr_iv_smile_event_study.ipynb   # Main analysis
├── figures/                                 # Exported plots
├── docs/                                    # Summaries, CSV outputs
├── src/                                     # (Optional) helper modules
├── requirements.txt                         # Dependencies
├── .gitignore
├── LICENSE
└── README.md
```

---

## Setup

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook
```

---

## Workflow

1. Fetch option chains from Yahoo via `yfinance`.
2. Select a \~30D expiry nearest to the earnings date.
3. Plot IV smile (implied vol vs strike/spot).
4. Compute implied moves:

   * ATM IV × √T
   * ATM short straddle premium ÷ spot
5. Compute realised move: stock close-to-close across the earnings event.
6. Illustrate short straddle payoff and compare realised vs implied.
7. Export plots** to `figures/` and summaries to `docs/`.

---

## Results: PLTR Earnings (2025-08-04)

* **Spot:** \~\$157
* **ATM IV:** \~50% annualised
* **Implied move (ATM IV·√T):** \~4.6%
* **Straddle breakeven:** \~4.7%
* **Realised move:** \~12.3%

**Interpretation:**
The realised move was much larger than both the IV-implied move and the short straddle breakeven. In this case, the **options market underpriced event risk**. A short straddle seller would have lost money.

---

## Key Figures

* IV smile: `figures/iv_smile_example.png`
* Straddle payoff: `figures/straddle_payoff.png`
* Price path around earnings: `figures/price_around_earnings.png`
* Implied vs realised comparison: `figures/implied_vs_realised.png`

---

## Caveats

* **Research only:** ignores commissions, bid–ask spreads, margin, early exercise, assignment, and tail risk.
* **Data limitations:** `yfinance` does not provide historical option chains. This analysis uses **current chains** for illustration and historical price data for realised moves.
* **Personal account:** Trading 212 does not support listed options; this project extends equity-only exposure into an options-based event study for learning purposes.

---
