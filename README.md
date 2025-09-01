# Palantir (PLTR) Implied Volatility Smile – Earnings Event Study

This mini-project analyzes how Palantir's (PLTR) implied volatility (IV) smile behaves around earnings and quantifies the volatility crush afterwards. It includes a short straddle payoff illustration (research-only; Trading 212 does not offer listed options).

## Goals
- Construct IV smiles (IV vs strike/spot) for near-term expiries before and after earnings.
- Compare implied move vs realized move around the event.
- Illustrate a short straddle payoff and how IV crush affects it.

## Data
- Source: `yfinance` options chains for PLTR.
- Scope: start with one earnings event; extend to multiple events for stability.

## Repository Structure
```
.
├── notebooks/
│   └── 01_pltr_iv_smile_event_study.ipynb
├── figures/
├── docs/
├── src/
├── requirements.txt
├── .gitignore
├── LICENSE
└── README.md
```

## Setup
```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook
```

## Workflow
1. Collect option chains via `yfinance` around a chosen earnings date.
2. Build pre vs post-event smiles for a comparable maturity (e.g., ~30 days).
3. Compute ATM implied move (IV × sqrt(T)) vs realized move (abs return).
4. Simulate a short straddle payoff using ATM call+put premiums and realized move.
5. Export figures to `figures/` and write a 1–2 page report in `docs/`.

## Key Plots
- `iv_smile_pre.png`, `iv_smile_post.png`
- `iv_crush_atm.png`
- `straddle_payoff.png`

## Caveats
- Research-only; ignores slippage, costs, assignment, and risk controls.
- Trading 212 does not support options; this is an illustrative extension to equity exposure.

## Author
David Crowe