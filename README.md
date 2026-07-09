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

## 🔬 Methodology & Machine Learning

Both datasets were ingested and validated for missing values. Timestamps were standardized to a unified **YYYY-MM-DD** format to enable accurate daily merging.

Beyond standard metric engineering (`Daily_PnL`, `Win_Rate`, `Long_Ratio`), two machine learning models were deployed to deepen the analysis:

*   **Behavioral Clustering (Unsupervised ML):** A **K-Means clustering algorithm** was applied to segment accounts into three distinct behavioral archetypes based on trade frequency, average size, and PnL: *Retail Traders*, *Whales (High Capital)*, and *High-Frequency Grinders*.
*   **Profitability Prediction (Supervised ML):** A **Random Forest Classifier** was trained to predict trade profitability (Win/Loss) using trade size, directional bias (Buy/Sell), and sentiment classification, achieving an accuracy of **~65%**.
