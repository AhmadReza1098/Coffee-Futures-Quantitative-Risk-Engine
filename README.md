Coffee C® Futures: Quantitative Risk & Pricing Engine

Bridging physical logistics with stochastic modeling to protect procurement budgets from market volatility.

📌 Table of Contents

Overview

Business Problem

Dataset

🛠️ Tech Stack & Tools

Project Structure

Data Cleaning & Preparation

Exploratory Data Analysis (EDA)

Research Questions & Key Findings

How to Run This Project

Future Enhancements

Author & Contact

Overview

In global commodity trading, "market jitters" aren't just a metaphor—they represent a massive financial risk. For a coffee roaster, a sudden price spike can erase an entire year's profit margin in a single week. By the time a supply shock hits the news, it’s often too late to hedge.

In this project, I didn't just calculate a price; I built an integrated risk engine. Instead of relying on intuition or static spreadsheets, I combined the "Physical Truth" of logistics with the "Probabilistic Reality" of the market. My goal was to move beyond simple forecasting and create a tool that quantifies the "Fan of Uncertainty," allowing procurement teams to lock in certainty when the market offers none.

Business Problem

Procurement managers for soft commodities face a constant "Buyer’s Dilemma": If we buy today, we pay for storage and tie up capital. If we wait, we risk a supply shock. Currently, the coffee market is experiencing ~39.3% annualized volatility, making "waiting and seeing" a dangerous strategy.

This project aims to:

Determine the Fair Value: Calculate exactly what it costs to buy, store, and insure coffee for 6 months to see if the market is "overpriced."

Evaluate the Safety Net: Use the Black-Scholes Model to see if paying a $0.34 premium for a call option is a statistically sound investment.

Stress-Test the Future: Run 1,000 "what-if" scenarios to identify "Fat-Tail" risks—those rare but catastrophic price spikes that destroy budgets.

Dataset

Source: ICE Coffee C® Futures (via Yahoo Finance/Market Data).

Key variables used in the engine:

Spot Price ($2.94) – The "Right Now" price on the exchange.

Volatility (39.30%) – Annualized historical risk metric.

Risk-Free Rate (3.58%) – The 10-Year Treasury Yield.

Storage & Insurance (1.00%) – Physical logistics cost.

Time to Maturity (0.5) – A 6-month hedging horizon.

🛠️ Tech Stack & Tools

Language: Python 3.9+ (Simulation Engine)

Logic Center: Microsoft Excel (Cost of Carry & BSM Dashboards)

Data Manipulation: NumPy, Pandas

Visualization: Matplotlib (Stochastic Path Dispersion & Histograms)

Financial Logic: Geometric Brownian Motion (GBM), Black-Scholes Model (BSM)

Project Structure

Coffee-Risk-Engine/
│
├── README.md                          
├── requirements.txt                   
├── Coffee_Strategy_Dashboard.xlsx     # The "Control Center"
│
├── notebooks/
│   └── Stochastic_Engine_1000_Paths.ipynb  
│
└── visuals/
    ├── Figure_1_Dispersion.png        # The "Journey"
    └── Figure_2_Histogram.png         # The "Destination"


Data Cleaning & Preparation

To transform raw price data into a high-fidelity simulation, I adopted a "Stochastic Readiness" strategy:

Log-Return Calibration: I converted absolute prices into Logarithmic Returns. This ensures that our price paths follow a normal distribution, preventing the model from predicting impossible "negative" coffee prices.

Volatility Annualization: I calculated the standard deviation of daily returns and scaled it by $\sqrt{252}$ to get a true 39.30% annualized volatility.

Time-Step Synchronization: I mapped the 6-month window into exactly 126 trading days ($dt = T/126$) to ensure the Python engine and Excel dashboard were perfectly aligned.

Exploratory Data Analysis (EDA)

Before running simulations, I analyzed the "shape" of the market risk. I didn't just look for trends; I looked for the volatility story.

The "High-Beta" Reality: Coffee showed significantly higher volatility (39.3%) compared to other soft commodities. This immediately flagged that a simple "Buy and Hold" strategy was insufficient—an options-based "Safety Net" was mandatory.

The Journey vs. The Destination: I noticed that while the average trend was stable, the daily swings were large enough to trigger margin calls. This finding drove my decision to use Price-Path Dispersion (Fig 1) to visualize the daily stress on the portfolio.

The "Fat-Tail" Observation: Historical spikes were not normally distributed; they were "skewed." This proved that a standard average price wouldn't be enough to protect the budget—we had to model for the extreme 1% events.

Research Questions & Key Findings

I framed my analysis around three critical business questions:

Question 1: Is the market "Overpricing" the future?

Finding: The Physical Baseline is $3.01.

My Cost of Carry model revealed that buying and storing coffee yourself costs $3.01.

The Insight: If the ICE exchange is trading at $3.10, the market is "Overpriced." It's cheaper to buy the beans and rent a warehouse than to buy the future contract.

Question 2: Is it better to be "Certain" or "Lucky"?

Finding: The $0.34 Premium is a high-value hedge.

With a $2.95 Strike Price, our BSM calculation showed the option is "At-the-Money."

The Insight: We pay a small premium today to "delete" the risk of prices hitting $4.00. We accepted the cost of the premium to guarantee a "ceiling" on our costs.

Question 3: What do 1,000 different futures say?

Finding: The "Center of Gravity" is $3.04.

After running 1,000 paths, the Monte Carlo simulation settled at an average of $3.04—higher than our $2.95 Strike.

The Insight: Our "Safety Net" (Recall equivalent) is highly effective. In 64% of scenarios, the market ends up higher than our strike, proving the call option is the most logical path for a risk-averse business.

How to Run This Project

Clone the Repository

git clone [https://github.com/AhmadReza1098/Coffee-Risk-Engine](https://github.com/AhmadReza1098/Coffee-Risk-Engine)


Install Dependencies

pip install -r requirements.txt


Run the Simulation

Open Stochastic_Engine_1000_Paths.ipynb in Jupyter.

Run all cells to generate Figure 1 (Dispersion) and Figure 2 (Histogram).

Check the Dashboard

Open Coffee_Strategy_Dashboard.xlsx.

View the "Executive Summary" tab to see the side-by-side plots and the final $3.01 vs $3.04 comparison.

Future Enhancements

GARCH(1,1) Volatility: Upgrade from static volatility to "Vol-Clustering" to better predict price shocks.

Live API Integration: Connect the Excel Control Center to live ICE market feeds via a Python API wrapper.

Dynamic Delta Hedging: Build a script to suggest daily "rebalancing" of the hedge as time-decay (Theta) eats into the option value.

Author & Contact

Ahmad Reza Aspiring Data Analyst – Financial Engineering & BI

📧 Email: ahmadreza6122@gmail.com

🔗 LinkedIn: www.linkedin.com/in/ahmad-reza-econ

🔗 GitHub: https://github.com/AhmadReza1098
