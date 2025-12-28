

This repo hosts the code and outputs for an empirical project on **flight‑to‑safety contagion** between exchange rates and residential property markets, using crisis‑state panel models, Markov switching, and TVP‑VAR connectedness. [web:105][web:145]

---

## Research question

> How do global crises and safe‑haven currency status change the link between real exchange rates and housing prices, and how strongly are these markets dynamically connected during turmoil?

---

## Repository layout

- **`data/`**  
  Balanced quarterly panel (REER, residential prices), crisis dummies, crisis‑intensity measures, and intermediate CSVs.

- **`python/`**  
  - Crisis‑dummy and crisis‑intensity fixed‑effects models.  
  - Markov‑switching specifications for housing returns and REER changes.  
  - Regime‑split visualizations (time series with shaded crises, scatter plots by regime and group).

- **`r/`**  
  - TVP‑VAR connectedness estimation with the `ConnectednessApproach` package (Diebold–Yilmaz style). [web:105][web:107]  
  - Scripts to generate connectedness tables and time‑varying spillover plots.

- **`outputs/`**  
  - Model tables (CSV / LaTeX).  
  - Final figures for crisis models, Markov switching, and TVP‑VAR connectedness.

---

##  Main models

### 1. Crisis‑dummy and crisis‑intensity panels (Python)

- FE regressions of housing price growth on:
  - REER changes, REER volatility, lagged prices.  
  - Crisis dummies and continuous crisis‑intensity variables.  
- Designed to show whether crises **flip or amplify** the REER–housing relationship.

### 2. Markov‑switching models (Python)

- Two‑regime (calm vs crisis / low vs high volatility) models for:
  - Housing returns.  
  - Exchange‑rate changes.  
- Regime probabilities and regime‑specific coefficients used for regime‑highlighted plots and tables.

### 3. TVP‑VAR connectedness (R)

- Time‑varying parameter VAR for:
  - `SafeFX`, `NonSafeFX`, and `Housing` returns.  
- Connectedness computed with `ConnectednessApproach` (Antonakakis–Chatziantoniou–Gabauer TVP‑VAR framework). [web:105][web:145]  
- Outputs:
  - Full **from–to connectedness table**.  
  - Total connectedness index over time.  
  - Directional spillovers from safe‑haven vs non‑safe FX into housing.

---

##  Key outputs

- **Crisis & Markov tables**  
  - Baseline FE, crisis‑dummy, crisis‑intensity, and Markov‑switching estimates.

- **Connectedness tables & figures**  
  - `TVPVAR_Table1_FullConnectedness.csv`: from–to spillovers across SafeFX, NonSafeFX, and Housing. [web:105]  
  - Figure: Time‑varying total connectedness index (TVP‑VAR).  
  - Figure: Spillovers from SafeFX vs NonSafeFX to the system.  
  - Figure: Two‑year average total connectedness.

---

## How to reproduce

1. **Python side**
   - Install required Python packages (pandas, numpy, statsmodels, linearmodels, etc.).  
   - Run the scripts in `python/` to:
     - Build the balanced panel and crisis‑intensity measures.  
     - Estimate FE and Markov‑switching models.  
     - Export `dy_connectedness_input.csv` for the R TVP‑VAR step.

2. **R side**
   - Install `ConnectednessApproach`, `zoo`, `ggplot2`, `dplyr`, `tidyr`. [web:107][web:156]  
   - Run the scripts in `r/` to:
     - Estimate the TVP‑VAR connectedness.  
     - Save connectedness tables and high‑quality ggplot figures.

---

## Citation and methods

If you use this repo, please cite the underlying connectedness methodology (Diebold–Yilmaz and the TVP‑VAR connectedness of Antonakakis, Chatziantoniou & Gabauer, and the `ConnectednessApproach` R package). [web:105][web:145]
