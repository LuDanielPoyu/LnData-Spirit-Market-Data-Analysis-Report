# NCCU Data Analysis Student Club - LnData Taiwan Spirit Market Project,

**Role:** Project Manager & Data Scientist (Team Project)  
**When:** July 2023 – June 2024

> **Note:** This repository uses sanitized descriptions and **synthetic examples only**.  
> No proprietary data, IDs, or credentials are included.

---

## Problem
The sponsor needed a clear, data-driven view of Taiwan’s **spirits market**, including who buys what, where, and when, and practical segmentation to guide **product, channel, and promotion** decisions.

---

## Data & Scope (summary)
- **Invoice data** (3rd-party): ~Apr 2022 → Oct 2023; cleaned to spirits-relevant channels; removed negatives, outliers and multi-spirit product names; produced category shares. 
- **Consumer attributes**: age and gender where available; built a complete-fields subset for profiling and cluster features. 
- **Industry context**: external environment, policy/tax, culture trends; distribution channels and whisky price-tier imports via public sources (IWSR/Statista). 

---

## What we built

### P1 — Market Cleaning & Category Share (Invoice Data)
- **Cleaning pipeline:** drop negative quantity and price rows; pair off suspected refunds; filter to spirits-relevant retail channels; keyword rules to exclude non-spirit items. 
- **Category split:** whisky ~32.6%, red wine ~19.2%, kaoliang ~14.7% (2022/04–2023/10).
<img width="551" height="372" alt="截圖 2025-11-04 凌晨12 31 30" src="https://github.com/user-attachments/assets/6def6300-6e8f-469c-8870-d9d8015ea796" />

### P2 — Consumer Profile Cuts (Age & Gender)
- **Complete-fields subset:** ~78,978 rows with both age & gender; built five age bands and compared spend and quantity. 
- **Key contrasts:** whisky buyers average ~38 yrs; red-wine buyers ~44.8 yrs; male whisky spend ≈ **1.92×** female; female average ticket peaks at 51–60 then declines. 

### P3 — K-means Aegmentation (Actionable Cohorts)
- **Preprocess:** encode gender (M=0, F=1, missing=−1); impute age and amount with means to retain coverage; scale features.   
- **Modeling:** **K=3** from elbow; 6-feature set (amount, basket size, age, gender, etc.). 
- **Cohorts (high level):**  
  - **Cluster 1 (~55%)** — high-spend, slightly older, male-skewed.  
  - **Cluster 2 (~31%)** — mid-spend, male-skewed.  
  - **Cluster 3 (~12%)** — low-spend, younger, female-leaning.
- **Implications:** commuter and office bundles (C1/C2), delivery-only promos (C2), entry-price assortments & social creatives (C3).
 <img width="551" height="372" alt="截圖 2025-11-04 凌晨12 30 09" src="https://github.com/user-attachments/assets/569c92e9-165b-4371-afcf-bc06e1c4a011" />


### P4 — Temporal & Brand Patterns
- **Seasonality:** **January** is the clear peak (overall volume & average ticket); 7–8 months show higher-price purchases (party/holiday hypothesis). 
- **Weekpart by brand:** weekend peaks for Johnnie Walker / Singleton / Glenfiddich / Dewar’s; **Thursday** peak for **Macallan**; some brands show no strong pattern. 
- **By spend tier:** high vs. low-spend whisky buyers share similar month trends; average ticket shows two peaks (Jan and mid-summer). 

### P5 — Industry & Channel Context
- **External environment:** raw-material shocks (Ukraine grains), climate risks, supply volatility → potential price/quality pressure. 
- **Policy/tax:** proposed **online sales** opening and current excise/VAT regimes shape channel economics and consumer behavior. 
- **Channels:** IWSR split of on-premise vs off-premise varies by category; spirits skew more **off-premise** in Taiwan.
- **Whisky market:** 2022 import volumes healthy with **M-shaped** price-tier distribution; multi-year outlook remains optimistic. 
---

## Results (selected)
- **Clean category picture** (invoice share by spirit) and **brand/weekpart** levers to test.  
- **Three actionable segments** (high/mid/low spend) with distinct age/gender mixes and promo/assortment plays.  
- **Staffing/stocking calendar**: seasonal peaks and brand-specific day-of-week opportunities (e.g., Macallan on Thu). 
- **Industry scorecard** to frame pricing/channel risks and growth bets. 

---

## Methods & Stack
**Python**, **pandas**, **scikit-learn** (K-means, scaling), basic **time-series cuts**, **matplotlib**/**seaborn** for visuals; public data (IWSR/Statista) for market context

---
