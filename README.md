# ⚽ EPL Moneyball AI: Value Betting with XGBoost

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![XGBoost](https://img.shields.io/badge/Model-XGBoost-orange)
![Accuracy](https://img.shields.io/badge/Accuracy-~54%25-green)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)

**An End-to-End Machine Learning pipeline that predicts English Premier League match outcomes and identifies "Value Bets" in real-time.**

## 📌 Overview
This project applies **Moneyball principles** to football betting. Instead of relying on gut feeling, it uses a data-driven approach to calculate the "True Probability" of a match result. By comparing these probabilities with real-time bookmaker odds (via API), the system identifies market inefficiencies where the reward outweighs the risk.

The model achieves a **~54% accuracy** on unseen test data, effectively beating the bookmaker's margin (vigorish).

## 🚀 Key Features

* **🔄 Automated Data Pipeline:** Scrapes historical match data (last 5 seasons) from [football-data.co.uk](https://www.football-data.co.uk/) automatically on every run.
* **🧠 Advanced Feature Engineering:**
    * **Time-Decay Weighting:** Recent games (2024-2025) are weighted 2x more than older games.
    * **Interaction Features:** Direct comparison metrics (e.g., *Home Attack Strength* vs. *Away Defense Weakness*).
    * **Momentum & Form:** Rolling averages of points and goals over the last 3-5 games.
* **⚡ Real-Time Odds Integration:** Connects to **The Odds API** to fetch live odds from bookmakers (Bet365, William Hill, etc.) for the current matchweek.
* **🛡️ Secure Architecture:** Designed to work with Google Colab Secrets to protect API keys.
* **📊 Value Detection Engine:** Automatically flags bets where `Model Probability > Implied Odds + 5%`.

## 🛠️ Tech Stack

* **Core:** Python 3.x
* **Data Manipulation:** Pandas, NumPy
* **Machine Learning:** XGBoost (Classifier & Regressor), Scikit-Learn
* **API & Web:** Requests, JSON
* **Environment:** Google Colab / Jupyter Notebook

## 📂 Project Structure

```text
├── EPL_Moneyball_Predictor.ipynb   # Main Jupyter Notebook (The Code)
├── requirements.txt                # Dependencies
├── README.md                       # Project Documentation
└── data/                           # (Optional) Local storage for CSVs
