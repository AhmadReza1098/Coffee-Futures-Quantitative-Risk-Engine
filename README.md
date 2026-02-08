# Coffee C® Futures: Quantitative Risk & Pricing Engine

An integrated financial framework that bridges theoretical commodity pricing with stochastic market forecasting. This project utilizes a hybrid workflow, combining Excel for logistical modeling and Python for high-fidelity stress testing.

---

## 📑 Table of Contents

- [Overview](#overview)  
- [Business Problem](#business-problem)  
- [Dataset](#dataset)  
- [Tools & Technologies](#tools--technologies)  
- [Project Structure](#project-structure)  
- [Data Cleaning & Preparation](#data-cleaning--preparation)  
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)  
- [Research Questions & Key Findings](#research-questions--key-findings)  
- [How to Run This Project](#how-to-run-this-project)  
- [Future Enhancements](#future-enhancements)  
- [Author & Contact](#author--contact)  

---

## Overview

In global commodity trading, the price of a future contract isn't just a "guess" it is a combination of today's spot price, the cost of storage, and the price of capital. This project provides a decision-support system to determine if the market is "fairly priced" and calculates the statistical probability of different market outcomes to help procurement teams manage risk.

In this project, I didn't just calculate a price; I built an integrated risk engine. Instead of relying on intuition or static spreadsheets, I combined the "Physical Truth" of logistics with the "Probabilistic Reality" of the market. My goal was to move beyond simple forecasting and create a tool that quantifies the "Fan of Uncertainty," allowing procurement teams to lock in certainty when the market offers none.

---

## Business Problem

Coffee is a notoriously volatile commodity (currently at ~39.3% annualized volatility). Procurement managers face the "Buyer’s Dilemma":

- Do we buy today and pay to store it? (**Project 1**)
- Do we buy an option to protect against price spikes? (**Project 2**)
- Or is the market currently overpriced compared to its physical reality?

This Project Aims to:

- Determine the Fair Value: Calculate exactly what it costs to buy, store, and insure coffee for 6 months to see if the market is "overpriced."

- Evaluate the Safety Net: Use the Black-Scholes Model to see if paying a $0.34 premium for a call option is a statistically sound investment.

- Stress-Test the Future: Run 10,000 "what-if" scenarios to identify "Fat-Tail" risks—those rare but catastrophic price spikes that destroy budgets.

This engine provides a quantitative answer by stress-testing theoretical models against 1,000 simulated price paths.

---

## Dataset

- Source: ICE Coffee C® Futures (via Yahoo Finance/Market Data).

- Composition: 252+ rows of historical closing prices used to calibrate annualized volatility.

- Granularity: Daily trading close.
---

## Tools & Technologies

* Analysis & Logic: **Microsoft Excel (Financial Functions, Analysis ToolPak)**.

* Simulation Engine: **Python (NumPy for GBM, Matplotlib for Visuals, Pandas for Data Structuring)**.

* Statistical Logic: **Geometric Brownian Motion (GBM), Black-Scholes Model (BSM), Cost of Carry**.
---

## Project Structure

```
Coffee-Risk-Engine/
│
├── README.md                          
├── requirements.txt                   
│
├── data/
│   └── coffee_data.csv                
│
├── model/
│   └── Coffee_Strategy_Dashboard.xlsx 
│
├── scripts/
│   └── Stochastic_Engine_1000_Paths.ipynb  
│
├── visuals/
│   ├── Figure_1_Dispersion.png        
│   └── Figure_2_Histogram.png         
│
└── reports/
    └── Executive_Summary_Report.pdf 
```

## Data Cleaning & Preparation

To ensure high-fidelity simulations, the raw historical data underwent the following processing:

**Return Calculation**: Converted absolute prices into Logarithmic Returns to ensure normality in the stochastic process.

**Volatility Calibration**: Annualized the standard deviation of returns ($\sigma = \text{STDEV}(\text{Log Returns}) \times \sqrt{252}$).

**Time-Step Synchronization**: Mapped the 6-month maturity ($T=0.5$) to exactly 126 trading days ($dt = T/126$).

---

## Exploratory Data Analysis (EDA)

**Volatility Analysis**: The historical data revealed an annualized volatility of 39.30%, indicating a high-risk environment where prices frequently deviate from the mean.

**Trend Observation**: Visual analysis of historical price action showed significant "clustering," suggesting that price shocks tend to persist, justifying the need for a non-linear hedge (Options).

---

## Research Questions & Key Findings

* **Q1: What is the "Fair Value" of the future?**

Finding: Based on logistical costs ($r$ and $d$), the fair price is $3.01. If market trading is > $3.01, the market is "overpriced" relative to physical carry costs.

* **Q2: Is the $0.34 Option Premium a good deal?**

Finding: Yes. Given the high volatility, the $0.34 premium acts as an affordable insurance policy to cap procurement costs at **$2.95**.

* **Q3: What is the likelihood of a supply shock?**

Finding: The 1,000-path Monte Carlo simulation reveals a skewed "Fat Tail" risk. While the average price sits at $3.04, extreme scenarios show prices spiking toward $4.00, far exceeding the cost of the hedge.

---

## How to Run This Project

Logistics: Open the Excel Dashboard to view the static Fair Value and BSM calculations.

Simulation: Run the .ipynb script in Jupyter or Google Colab to regenerate the 1,000 price paths.

Synthesis: Check the "Executive Summary" tab in Excel to see the integrated dashboard (with side-by-side Fig 1 & Fig 2).

---

## Future Enhancements

* **Dynamic Delta Hedging**: Implementing a script to manage the option position as the market moves.

* **GARCH Modeling**: Upgrading from static volatility to account for "volatility clustering."

* **Live API Integration**: Connecting the Excel Dashboard directly to real-time market feeds via Python.

---

## Author & Contact

**Ahmad Reza**
- 📧 Email: ahmadreza6122@gmail.com  
- www.linkedin.com/in/ahmad-reza-econ 
- https://github.com/AhmadReza1098 
