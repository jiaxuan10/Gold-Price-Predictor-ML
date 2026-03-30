# 🧈 Gold Price Predictor ML: Quant System

<p align="center">
  🚀 AI-driven quantitative trading system
  🧠 Ensemble Learning + NLP Sentiment + Risk-Aware Execution
</p>

---

## 📌 System Overview

This project implements a **machine learning-based trading system** designed to predict short-term gold price direction and convert predictions into **actionable trading decisions**.

Unlike traditional regression-based forecasting, this system is formulated as:

> 🎯 **To develop a machine learning framework for predicting gold price movement
> 🎯 **To integrate financial news sentiment into the predictive and decision making process 
> 🎯 **To design and evaluate a risk-aware automated trading simulation based on model-driven signals

---

## 🧠 Problem Formulation

Instead of predicting exact price:

* Target = Direction of price movement

  * 1 → Price Increase
  * 0 → Price Decrease

Model outputs:

```
P_up = Probability that price will increase
```

---

## 📊 Feature Engineering

### 1. Technical Indicators

Used to capture **market structure and momentum**:

* RSI → overbought / oversold conditions
* MACD → trend + momentum shifts
* Moving Averages → trend smoothing
* ATR → volatility estimation

---

### 2. Sentiment Features (NLP)

Using **FinBERT**, news headlines are converted into:

```
Sentiment Score = {Positive, Neutral, Negative}
```

Then transformed into numerical signals:

```
Sentiment Index = weighted sentiment score
```

Purpose:

* Capture **market psychology**
* Improve model robustness under news-driven volatility

---

### 3. Time-Series Features

* Lagged returns
* Rolling mean / variance
* Temporal dependencies

✔ Ensures model captures **sequential behavior**

---

## 🤖 Machine Learning Model

### 🔹 Ensemble Strategy

The final prediction is a **weighted soft-voting model**:

```
P_final = w1 * P_xgb + w2 * P_lr + w3 * P_gb
```

Where:

* P_xgb → XGBoost prediction
* P_lr → Logistic Regression
* P_gb → Gradient Boosting

Weights:

* XGBoost → 38.2%
* Logistic Regression → 31.3%
* Gradient Boosting → 30.5%

---

### 🔹 Why Ensemble?

Each model captures different patterns:

| Model               | Role                    |
| ------------------- | ----------------------- |
| XGBoost             | Non-linear interactions |
| Logistic Regression | Stability + baseline    |
| Gradient Boosting   | Error refinement        |

👉 Ensemble reduces:

* Overfitting
* Model bias
* Variance

---

## 🎯 Probability Calibration

Raw model outputs are often **not well-calibrated**.

Applied method:

```
Platt Scaling
```

Purpose:

* Transform raw probabilities into **true likelihood estimates**
* Improve decision reliability

---

## ⚡ Trading Decision Logic

### 🔹 Signal Generation

Instead of direct classification:

```
If P_final > Upper_Threshold → BUY
If P_final < Lower_Threshold → SELL
Else → HOLD
```

---

### 🔹 Dynamic Thresholding

Thresholds are adaptive:

```
Upper_Threshold = base + sentiment_adjustment
Lower_Threshold = base - sentiment_adjustment
```

Where:

* Positive sentiment → easier to BUY
* Negative sentiment → stricter BUY condition

---

## 🛡️ Risk Management System

### 🔹 Position Sizing

Position size depends on confidence:

```
Position Size ∝ P_final
```

Higher confidence → larger allocation

---

### 🔹 Stop Loss (ATR-Based)

```
Stop Loss = Entry Price ± k * ATR
```

Where:

* ATR = Average True Range
* k = risk multiplier

Purpose:

* Adapt to market volatility
* Prevent excessive losses

---

### 🔹 Risk Constraints

* Limit max exposure
* Filter low-confidence trades
* Avoid overtrading

---

## 🧪 Backtesting Methodology

### 🔹 Time-Series Validation

* Walk-forward validation
* No random shuffling
* No data leakage

---

### 🔹 Evaluation Metrics

#### ML Metrics:

* Precision (important for trading signals)
* Recall
* F1-score

#### Trading Metrics:

* Sharpe Ratio
* Win Rate
* Max Drawdown

---

## 🚀 Results

| Metric       | Value      |
| ------------ | ---------- |
| Sharpe Ratio | **3.05**   |
| Win Rate     | **58%**    |
| Max Drawdown | **-3.45%** |

---

## 🏗️ System Architecture

```text
Data Layer
 ├── Market Data (Yahoo Finance)
 └── News Data (RSS Feeds)

Feature Layer
 ├── Technical Indicators
 └── Sentiment Scores

Model Layer
 ├── Ensemble Model
 └── Probability Calibration

Decision Layer
 ├── Threshold Logic
 └── Signal Generation

Risk Layer
 ├── Position Sizing
 └── Stop Loss Engine

Interface Layer
 └── Streamlit Dashboard
```

---

## 🔄 End-to-End Pipeline

1. Collect market + news data
2. Generate features
3. Compute sentiment scores
4. Predict probability (P_up)
5. Apply calibration
6. Generate trading signal
7. Apply risk management
8. Evaluate performance

---

## 🛠️ Future Improvements (Aligned with Research)

### 🔬 Modeling

* LSTM / Transformer (Time-series deep learning)
* Regime-switching models

---

### 📊 Data

* Macroeconomic variables (CPI, Interest Rates)
* USD Index (DXY)
* Alternative sentiment sources

---

### ⚡ System

* Real-time streaming (Kafka)
* Cloud deployment

---

### 🔍 Explainability

* SHAP values
* Feature importance analysis

---

## ⚠️ Disclaimer

This project is for **educational and research purposes only**.

---

## 👨‍💻 Author

Lim Jia Xuan
