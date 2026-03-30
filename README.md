# 🪙 Gold Price Predictor ML: Quant System

<p align="center">
  🚀 AI-driven quantitative trading system for <b>XAU/USD</b><br>
  🧠 Ensemble Learning + NLP Sentiment + Risk-Aware Execution Engine
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10-blue?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/ML-Ensemble%20Learning-orange?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/NLP-FinBERT-green?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Focus-Quantitative%20Trading-purple?style=for-the-badge"/>
</p>

---

## 📌 System Overview

This project implements a **full-stack AI trading pipeline** designed to model and exploit short-term inefficiencies in the gold market.

Unlike traditional ML systems that optimize for accuracy, this system is designed around:

> 🎯 **Expected Trading Profitability (Risk-adjusted returns)**

---

## 🧠 AI System Design Philosophy

### 🔑 Core Idea

Financial markets are:

* Noisy
* Non-stationary
* Influenced by both **quantitative signals** and **qualitative sentiment**

👉 Therefore, this system combines:

| Component               | Purpose                            |
| ----------------------- | ---------------------------------- |
| 📊 Technical Indicators | Capture price momentum & structure |
| 🤖 ML Models            | Learn non-linear relationships     |
| 📰 Sentiment Analysis   | Capture market psychology          |
| ⚡ Trading Logic         | Convert predictions → decisions    |

---

## 🤖 Machine Learning Architecture

### 🔹 Problem Formulation

* Task: **Binary Classification**
* Output:

  * `1` → Price Up
  * `0` → Price Down

Instead of predicting price directly, the system predicts **directional probability**:

[
P(\text{Price Increase} | Features)
]

---

### 🔹 Feature Engineering

The model uses **multi-domain features**:

#### 📊 Technical Indicators

* RSI (momentum)
* MACD (trend + momentum)
* Moving Averages (trend smoothing)
* Volatility (ATR)

#### 🧠 Sentiment Features

* FinBERT sentiment scores:

  * Positive
  * Neutral
  * Negative

#### ⏱️ Temporal Features

* Lagged returns
* Rolling statistics

---

### 🔹 Ensemble Learning Strategy

Instead of relying on a single model, the system uses a **soft-voting ensemble**:

| Model               | Strength                              |
| ------------------- | ------------------------------------- |
| XGBoost             | Captures complex non-linear patterns  |
| Logistic Regression | Provides stability & interpretability |
| Gradient Boosting   | Improves residual errors              |

📌 Final Prediction:
[
P_{final} = \sum w_i P_i
]

Where:

* ( w_i ) = model weights
* ( P_i ) = predicted probabilities

---

### 🔹 Probability Calibration

Raw ML probabilities are often **overconfident**.

👉 Solution:

* Apply **Platt Scaling**
* Ensures:

  * Better probability reliability
  * More stable trading decisions

---

## ⚡ Trading Decision Engine

### 🔹 From Prediction → Action

Instead of naive classification:

| Probability       | Action  |
| ----------------- | ------- |
| > Upper Threshold | 🟢 Buy  |
| < Lower Threshold | 🔴 Sell |
| Otherwise         | ⚪ Hold  |

---

### 🔹 Dynamic Thresholding

Thresholds are **not fixed**.

They adapt based on:

* Market volatility
* Sentiment strength

👉 This avoids:

* Overtrading
* Noise-driven signals

---

## 🛡️ Risk Management System

A realistic trading system must manage risk:

### 🔹 Position Sizing

* Scaled based on confidence level
* Higher probability → larger position

---

### 🔹 Stop Loss (ATR-Based)

[
StopLoss = EntryPrice \pm k \cdot ATR
]

* Adjusts dynamically with volatility
* Prevents large drawdowns

---

### 🔹 Risk Constraints

* Maximum exposure limits
* Trade filtering under uncertainty

---

## 🧪 Backtesting Methodology

### 🔹 Time-Series Validation

* Walk-forward validation
* No data leakage

---

### 🔹 Evaluation Metrics

#### 📊 ML Metrics

* Precision (focus on signal quality)
* Recall
* F1-score

#### 💰 Trading Metrics

* Sharpe Ratio → risk-adjusted return
* Win Rate → consistency
* Max Drawdown → downside risk

---

## 🚀 Performance Results

| Metric          | Value      |
| --------------- | ---------- |
| 📈 Sharpe Ratio | **3.05**   |
| 🎯 Win Rate     | **58%**    |
| 📉 Max Drawdown | **-3.45%** |

---

## 🏗️ System Architecture

```text id="r7m9u6"
📥 Data Layer
 ├── Market Data (Yahoo Finance)
 └── News Data (RSS Feeds)

⚙️ Feature Layer
 ├── Technical Indicators
 └── Sentiment Features

🤖 Model Layer
 ├── Ensemble Learning
 └── Probability Calibration

⚡ Decision Layer
 ├── Threshold Logic
 └── Signal Generation

🛡️ Risk Layer
 ├── Position Sizing
 └── Stop Loss Engine

🖥️ Interface Layer
 └── Streamlit Dashboard
```

---

## 🔄 End-to-End Pipeline

1. Data ingestion (market + news)
2. Feature generation
3. Sentiment scoring
4. ML probability prediction
5. Calibration
6. Trading decision
7. Risk filtering
8. Performance tracking

---

## 🛠️ Future Improvements (Technical Roadmap)

### 🔬 Advanced Modeling

* LSTM / Transformer (TimeGPT)
* Regime-switching models
* Reinforcement Learning (trading policy optimization)

---

### 📊 Data Expansion

* Macroeconomic signals (CPI, Rates)
* Cross-asset signals (DXY, equities)
* Alternative data (Twitter, news volume)

---

### ⚡ Infrastructure

* Real-time streaming (Kafka)
* Distributed training
* Cloud deployment (AWS/GCP)

---

### 🔍 Explainability

* SHAP values
* Feature contribution analysis
* Model debugging tools

---

## ⚠️ Disclaimer

This project is for **research and educational purposes only**.
No real financial trading is performed.

---

## 👨‍💻 Author

**Lim Jia Xuan**
Machine Learning • Quantitative Finance • AI Systems
