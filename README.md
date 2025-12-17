# Marketing Mix Modelling using Meta's Robyn

* WIP *

## Executive Summary
Marketing Mix Modeling (MMM) analysis for a new bakery business that my sister just launched to optimize marketing budget allocation across digital channels that my sister planned to use (IG, TikTok, search).\
Using Meta's `Robyn` framework with 2 years of simulated data (Jan 2022 - Dec 2024, simulated using Meta's `SiMMMulator` package in R), 
this project aims to identify the most effective channels and optimal spend distribution to maximize the bakery's revenue.


Key Findings:

Model Performance: R² = 72% (strong fit for simulated data without external factors)/
Best overall channel by mean ROAS: Instagram (7.93x) - highest overall return/
Budget optimization opportunity: Cut spending 30% across all channels to improve ROAS from 6.51 to 8.77 (+35%); less spending yields better efficiency without significantly hurting revenue/

## Business Problem

My sister is launching a new bakery business and needs to allocate limited marketing budget efficiently across digital channels.

Challenge:
- Which channels (Instagram, TikTok, Search) deliver best ROI?
- How much should we spend on each channel?

Goal:
Build data-driven marketing strategy to maximize sales with optimized channel allocation.

## Methodology
### 1. Data Simulation
Framework: Meta SiMMMulator (open-source package in R)\
This is a new business with no historical data, so I used Meta's SiMMMulator to create realistic marketing scenarios.\

Simulation Parameters:

Time Period: Jan 2022 - Dec 2024 (156 weeks)\
Channels: Instagram, TikTok, Search (Google Ads)\
Granularity: Weekly data\
Variables Included:
- Marketing budget and allocation ranges by channel (weekly)
- Revenue/sales (dependent variable)
- Seasonality patterns is assumed to be pretty fluctuative (given a lot of ups and downs in F&B business, preference trends, etc.)


### 2. MMM Analysis
Framework: Meta Robyn (open-source MMM package in R)\
Key Features:
- Ridge regression with automated hyperparameter tuning
- Adstock modeling: Captures lagged effects (ad exposure → purchase delay)
- Saturation curves: Models diminishing returns at high spend
- Multi-objective optimization: Balances model fit vs business KPIs

Model configuration:
- Dependent Variable: Weekly revenue/sales\
- Independent Variables: IG spend, TikTok spend, Search spend\
- Control Variables: Seasonality, holidays, weekday patterns\
- Date Range: 156 weeks (Jan 2022 - Dec 2024)\
- Iterations: 5000 trials to find optimal hyperparameters

Validation metrics:

- Adjusted R²: 72% (good for simulated data without external factors)
- NRMSE (train): 0.1392 (strong prediction accuracy)
- NRMSE (validation): 0.2137 (validation holds up well)
- DECOMP.RSSD: 0.0023 (excellent decomposition quality)

## Key Results
### Model quality:

Adjusted R² = 72.2% - Model explains 72% of revenue variance using only 3 marketing channels\
Low NRMSE and DECOMP.RSSD - pretty reliable prediction

### Robyn's decomposition results:
- trend dominates revenue contribution, meaning that sales are still mainly grown organically
- Instagram contributes most among paid channels, followed by TikTok
- The model only tested 3 paid channels as independent variables and doesn't include macroeconomic or competitive effects, so there are possibly more explanatory variables that contributes to the revenue (as now it's represented by large intercept - to be included for future exercises!)
- On adstock: Instagram and TikTok is seen to have a strong immediate effect, but faster decay than search - probably so due to faster rate of content refresh on the algorithm side.
<img width="6800" height="7600" alt="image" src="https://github.com/user-attachments/assets/65418574-045c-424d-a0eb-67c7ba9fed4f" />

### Channel performance & ROAS
- 
<img width="4200" height="4200" alt="image" src="https://github.com/user-attachments/assets/d266aaa3-96fc-48f5-9b01-7781055073e5" />



