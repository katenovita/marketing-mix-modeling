# Marketing Mix Modelling using Meta's Robyn

* WIP *

## Executive Summary
Marketing Mix Modeling (MMM) analysis for a new bakery business that my sister just launched to optimize marketing budget allocation across digital channels that my sister planned to use (IG, TikTok, search).\
Using Meta's `Robyn` framework with 2 years of simulated data (Jan 2022 - Dec 2024, simulated using Meta's `SiMMMulator` package in R), 
this project aims to identify the most effective channels and optimal spend distribution to maximize the bakery's revenue.


Key Findings:

Model Performance: R² = 72% (strong fit for simulated data without external factors)

## Business Problem
Context:
My sister is launching a new bakery business and needs to allocate limited marketing budget efficiently across digital channels.

Challenge:
- Which channels (Instagram, TikTok, Search) deliver best ROI?
- How much should we spend on each channel?
- What are diminishing returns thresholds?
- How long do marketing effects last (adstock/carryover)?

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

Model Configuration:
Dependent Variable: Weekly revenue/sales\
Independent Variables: IG spend, TikTok spend, Search spend\
Date Range: 156 weeks (Jan 2022 - Dec 2024)\
Iterations: 5000 trials to find optimal hyperparameters

Validation:

Adjusted R²: 72% (good for simulated data without external factors)

