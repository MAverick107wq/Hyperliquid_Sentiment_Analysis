# Primetrade.ai - Trader Performance vs Market Sentiment

This repository contains the analysis for the Primetrade.ai Data Science Intern Round-0 Assignment. It explores how market sentiment (Fear/Greed) correlates with trader behavior and profitability on Hyperliquid.

## ⚙️ Setup & How to Run

**Prerequisites:**
* Python 3.8+
* Required libraries: See `requirements.txt` (pandas, numpy, plotly, streamlit)

**Execution:**
* **Jupyter Notebook:** Open `analysis.ipynb` and run all cells to view the data processing, metric engineering, and static Plotly charts.
* **Streamlit Dashboard (Bonus):** To run the interactive dashboard, execute the following command in your terminal:
    ```bash
    streamlit run market_sentiment_dashboard.py
    ```

---

## 🔬 Methodology
Both datasets (`historical_data.csv` and `fear_greed_index.csv`) were loaded and validated. Timestamps were converted to a unified `YYYY-MM-DD` string format to merge on a daily level. 

Engineered metrics include `Daily_PnL`, `Win_Rate` (binary classification of PnL > 0), and `Long_Ratio`. Data was segmented by the sentiment `classification` column to analyze behavioral and performance shifts across different market conditions.

## 📊 Key Data Insights
* **The Contrarian PnL Spike:** Performance significantly peaks during "Extreme Fear" days. Even though the win rate is low (~40.5%), the Average PnL per trade hits its absolute maximum at $204.34.
* **The "Greed" Trap:** Counter-intuitively, as the market moves towards "Greed" and "Neutral," profitability drops sharply. Average PnL falls to $92.23 (Greed) and bottoms out at $86.19 (Neutral).
* **Capital Deployment Paradox:** Traders are committing the most capital during standard "Fear" periods (Average Trade Size: $23,119). Conversely, they deploy the least amount of capital during "Extreme Greed" ($8,168), indicating extreme caution during highly exuberant market phases.
* **Long Bias Shifts:** Traders exhibit the strongest Long (BUY) bias during "Extreme Fear" (56.9%), buying the dip. During "Extreme Greed," they flip heavily short, with Longs making up only 45.2% of trades.

## 🚀 Actionable Strategy Recommendations (Rules of Thumb)
* **Strategy 1 (The Panic Premium):** *Scale up position sizes and long exposure during Extreme Fear.* The data proves that while win rates may fluctuate, the payout magnitude (Average PnL) is highest ($204.34) when buying into market panic.
* **Strategy 2 (Neutral Market Neutrality):** *Reduce trade frequency and tighten leverage during Neutral and Greed conditions.* Because Average PnL drops below $100 per trade in these conditions, traders are exposed to higher churn with lower reward profiles. Shift algorithms from directional trading to tight mean-reversion during these phases.
