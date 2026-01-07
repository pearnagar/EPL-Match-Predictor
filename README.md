
# ⚽ EPL Moneyball AI: Value Betting with XGBoost

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![XGBoost](https://img.shields.io/badge/Model-XGBoost-orange)
![Accuracy](https://img.shields.io/badge/Accuracy-~54%25-green)
![Status](https://img.shields.io/badge/Maintenance-Active-brightgreen)

**An End-to-End Machine Learning pipeline that predicts English Premier League match outcomes and identifies "Value Bets" in real-time.**

## 📌 Overview

This project applies **Moneyball principles** to football betting. Instead of relying on gut feeling, it utilizes a data-driven approach to calculate the "True Probability" of a match result based on historical performance. By comparing these probabilities with real-time bookmaker odds (via API), the system identifies market inefficiencies where the expected reward outweighs the risk.

The model is built on **XGBoost** and achieves a **~54% accuracy** on unseen test data, effectively creating a strategy that can beat the bookmaker's margin (vigorish).

## 🚀 Key Features

* **🔄 Automated Data Pipeline:** Automatically scrapes and aggregates the last 5 seasons of historical match data from [football-data.co.uk](https://www.football-data.co.uk/) on every run.
* **🧠 Advanced Feature Engineering:**
    * **Time-Decay Weighting:** Recent games (2024-2025) are weighted 2x more than older games to reflect current form.
    * **Interaction Features:** Direct comparison metrics (e.g., *Home Attack Strength* vs. *Away Defense Weakness*).
    * **Momentum & Form:** Rolling averages of points and goals over the last 3-5 games.
* **⚡ Real-Time Odds Integration:** Connects to **The Odds API** to fetch live odds from major bookmakers (Bet365, William Hill, Unibet) for the current matchweek.
* **🛡️ Enterprise-Grade Security:** Designed to work with **Google Colab Secrets** to protect sensitive API keys, ensuring no credentials are ever hardcoded in the repository.
* **📊 Value Detection Engine:** Automatically flags bets where `Model Probability > Implied Odds + 5%`.

## 🛠️ Tech Stack

* **Core:** Python 3.x
* **Data Manipulation:** Pandas, NumPy
* **Machine Learning:** XGBoost (Classifier & Regressor), Scikit-Learn
* **API & Web:** Requests, JSON, The Odds API
* **Environment:** Google Colab / Jupyter Notebook

## 📂 Project Structure

```text
├── EPL_Moneyball_Predictor.ipynb   # The main Production Notebook
├── requirements.txt                # Python dependencies
├── README.md                       # Project Documentation
└── data/                           # (Optional) Folder for local CSV storage

```

## ⚙️ How It Works

1. **Data Ingestion:** The system downloads 5 seasons of raw CSV data dynamically.
2. **Preprocessing:** Converts raw stats into dynamic features (Rolling Means, Lags, Differentials).
3. **Training:** An **XGBoost Classifier** is trained to predict the winner (Home/Draw/Away), utilizing historical odds as a market sentiment feature.
4. **Live Inference:**
* The system fetches the upcoming fixtures via **The Odds API**.
* It handles matchweek filtering to ensure no duplicate teams.
* It feeds the live matchup data + live odds into the trained model.


5. **Output:** A clean, color-coded report highlighting the predicted winner, expected goals, and any **Value Bets**.

## 🚀 How to Run

### Option 1: Google Colab (Recommended)

This project is optimized for Colab to leverage cloud resources and secure secret management.

1. Open `EPL_Moneyball_Predictor.ipynb` in Google Colab.
2. **Get an API Key:** Sign up for free at [The Odds API](https://the-odds-api.com/) (500 requests/month).
3. **Set up Secrets:**
* Click the **Key icon 🔑** on the left sidebar in Colab.
* Click **"Add new secret"**.
* **Name:** `ODDS_API_KEY`
* **Value:** `Your_Actual_Key_Here`
* Toggle **"Notebook access"** to **On** (Blue).


4. Run all cells (`Runtime` -> `Run all`).

### Option 2: Local Execution

1. Clone the repository:
```bash
git clone [https://github.com/yourusername/EPL-Match-Predictor.git](https://github.com/yourusername/EPL-Match-Predictor.git)
cd EPL-Match-Predictor

```


2. Install requirements:
```bash
pip install -r requirements.txt

```


3. Set your API Key in the code manually (replace the secrets logic) or use an environment variable.
4. Run the notebook using Jupyter Lab or VS Code.

## 📊 Model Performance

| Metric | Score | Description |
| --- | --- | --- |
| **Accuracy** | **54.08%** | Percentage of correct Match Winner predictions. |
| **Goals MAE** | **1.31** | Mean Absolute Error for total goals prediction. |
| **ROI** | **Positive** | Backtesting on the test set showed positive returns using the Value Betting strategy. |

## ⚠️ Disclaimer

This project is for **educational and portfolio purposes only**. Sports betting involves significant risk and markets are unpredictable. The model's predictions are based on historical statistics and do not guarantee future results. Please bet responsibly.

---

*Created by Peer Nagar*

