# Hyperliquid Sentiment Analysis: Trader Behavior vs. PnL

**Live Interactive Dashboard:** [Click here to view the live app](https://your-streamlit-app-link-here.streamlit.app/)

This repository contains the analysis for the Primetrade.ai Data Science Intern Round-0 Assignment. The objective of this project is to explore how broader Bitcoin market sentiment (Fear/Greed) directly influences trader behavior, capital deployment, and overall profitability on the Hyperliquid platform, utilizing both Exploratory Data Analysis (EDA) and Machine Learning.

## ⚙️ Setup & Execution

**Prerequisites:**
* Python 3.8+
* Required libraries: `pandas`, `numpy`, `scikit-learn`, `plotly`, `streamlit`

**Data Configuration:**
* To reproduce these results, please download the original `historical_data.zip` and `fear_greed_index.csv` datasets provided in the assignment prompt and place them in the root directory of this project. (Raw datasets are excluded from this repo to adhere to standard version control practices).

**How to Run:**
1. **Jupyter Notebook:** Open `analysis.ipynb` and execute all cells to view the core data processing, metric engineering, machine learning models, and static visual analysis.
2. **Streamlit Dashboard:** To run the interactive exploratory dashboard locally, execute the following command in your terminal:
   ```bash
   streamlit run market_sentiment_dashboard.py

---

🔬 Methodology & Machine Learning
Both datasets were ingested and validated for missing values. Timestamps were standardized to a unified YYYY-MM-DD format to enable accurate daily merging.

Beyond standard metric engineering (Daily_PnL, Win_Rate, Long_Ratio), two machine learning models were deployed to deepen the analysis:

Behavioral Clustering (Unsupervised ML): A K-Means clustering algorithm was applied to segment accounts into three distinct behavioral archetypes based on trade frequency, average size, and PnL: Retail Traders, Whales (High Capital), and High-Frequency Grinders.

Profitability Prediction (Supervised ML): A Random Forest Classifier was trained to predict trade profitability (Win/Loss) using trade size, directional bias (Buy/Sell), and sentiment classification, achieving an accuracy of ~65%.

📊 Detailed Data Findings & Visualizations
1. Performance Trends (PnL & Win Rates)
The Contrarian PnL Spike: The data reveals a massive profitability spike during periods of "Extreme Fear." Even though the overall win rate during these periods is relatively low (~40.5%), the Average PnL per trade reaches its absolute maximum at $204.34. This suggests that while fewer trades win during panic events, the magnitude of the winning trades is exceptionally high.

The "Greed" Churn Trap: Counter-intuitively, as market exuberance rises towards "Greed" and "Neutral," trader edge drops sharply. Average PnL falls to $92.23 (Greed) and bottoms out at $86.19 (Neutral). Win rates hover around 47-53%, but the reward profile is drastically reduced, leading to high churn with low payout.

2. Behavioral Trends (Capital & Directional Bias)
Capital Deployment Paradox: Traders are committing the highest amount of capital during standard "Fear" periods (Average Trade Size: $23,119). Conversely, they deploy the least amount of capital during "Extreme Greed" ($8,168). This indicates that the Hyperliquid cohort displays extreme caution and reduces leverage when the broader market is highly exuberant.

Long Bias Shifts: Traders exhibit the strongest Long (BUY) bias during "Extreme Fear" (56.9%), effectively "buying the dip." When the market flips to "Extreme Greed," trader behavior reverses heavily into shorts, with Longs making up only 45.2% of executed trades.

🚀 Actionable Strategy (Rules of Thumb)
Based on the empirical findings and predictive modeling, I propose the following algorithmic rules of thumb:

Strategy 1 (Harvest the Panic Premium): Algorithmically scale up position sizes and long exposure when the index hits Extreme Fear. The data proves that while win rates may fluctuate, the payout magnitude (Average PnL) is highest when providing liquidity and buying into market panic.

Strategy 2 (Neutral Market Restraint): Reduce trade frequency and tighten leverage during Neutral and Greed conditions. Because Average PnL drops significantly below $100 per trade in these conditions, traders are exposed to higher churn with lower reward profiles. Shift algorithms from directional trend-following to tight mean-reversion during these phases to protect capital.

📁 Repository Structure
analysis.ipynb: Core notebook containing data cleaning, EDA, visualizations, and ML models.

market_sentiment_dashboard.py: Python script for the interactive Streamlit dashboard.

requirements.txt: Environment dependencies.

*.png: Exported charts featured in this documentation.

Developed by V. Divyansh Naidu
