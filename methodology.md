---
title: Methodology
nav_order: 4
layout: default
permalink: /methodology/
---
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.4/dist/katex.min.css">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.4/dist/katex.min.js"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.4/dist/contrib/auto-render.min.js" onload="renderMathInElement(document.body);"></script>

# Methodology
This section outlines our approach to **time series forecasting** and **portfolio optimization** using **ARIMA**, **Chronos-Bolt**, and **sentiment analysis** for stock return prediction.

<div style="text-align:center">
    <img src="/dsc180-b08-website/pictures/workflow.png" alt="An Example of Subreddit Page" width="700" height="300">
    <p><em>An Overview of our methodology workflow</em></p>
</div>

### **Traditional Time Series Analysis -- The ARIMA Model**

We use the **AutoRegressive Integrated Moving Average (ARIMA)** model, followed by (Ariyo et al., 2014) to predict stock prices. ARIMA(p, d, q) consists of:

* **Autoregressive (AR) term**: Uses past values to predict future values
* **Differencing (I) term**: Removes trends to ensure stationarity
* **Moving Average (MA) term**: Models past forecast errors

The general ARIMA model is given by:

$$Y_t = c + \sum_{i=1}^{p} \phi_i Y_{t-i} + \sum_{j=1}^{q} \theta_j \epsilon_{t-j} + \epsilon_t$$

where:
* $Y_t$ is the value at time $t$
* $c$ is a constant term
* $\phi_i$ are AR coefficients
* $\theta_j$ are MA coefficients
* $\epsilon_t$ is white noise

#### ARIMA Implementation with Hyperparameter Search

Our implementation uses a comprehensive hyperparameter search strategy rather than relying on standard ADF tests. We employ two methods to find optimal ARIMA parameters:

1. **Primary method**: Using **auto_arima from pmdarima** to automatically select the best model parameters based on AIC (Akaike Information Criterion)
2. **Fallback method**: Manual grid search over orders (p,d,q) with validation when auto_arima fails

For validation, we reserve 20% of the training data as a validation set, evaluate each candidate model using Mean Absolute Scaled Error (MASE) on this validation data, and select the model with the lowest validation MASE to ensure optimal performance on unseen data.

#### Robust Forecasting Strategy

Initially, we trained ARIMA on the first 2.5 years of daily returns and tested it on the last 6 months. When predicting testing daily returns at once, the forecasts diverged significantly from actual values. ARIMA struggled to model long-term trends and produced linear predictions that failed to capture price fluctuations.

However, when we examined short-term predictions, we found ARIMA could follow recent trends. This led us to implement a recursive forecasting approach where we predict in smaller chunks. To improve accuracy, we use a recursive prediction strategy:

* **Training period**: January 2022 – December 2024
* **Testing period**: January 2025 – March 2025
* **Recursive approach**: Our approach predicts stock prices in shorter chunks (up to 10 days), incorporating predictions into the dataset before subsequent forecasts, and maintaining a rolling window of historical data to capture recent trends.

We implement error handling mechanisms that include retrying with the same model parameters (up to 3 attempts), falling back to a simpler ARIMA(1,1,0) model if needed, and, as a last resort, employing a naive forecast with small random noise (±2%). For performance evaluation, we use MASE, which compares our model's prediction error to that of a naive forecast, with MASE < 1 indicating our model outperforms the naive approach.

#### Limitations of ARIMA

The model inherently produces linear projections that fail to capture the non-linear price dynamics and volatility clustering common in stock markets. Even with optimal hyperparameter selection, ARIMA models cannot account for external market factors such as earnings announcements, sector rotations, or macroeconomic events that significantly impact stock prices. 

This limitation became particularly evident when modeling high-volatility tech stocks like NVDA, where prediction errors compounded rapidly. Additionally, our fallback mechanisms were frequently triggered, indicating computational instability in parameter estimation for certain time series patterns. These constraints necessitated our recursive approach with shorter prediction windows, essentially converting a theoretically elegant statistical model into a more complex, engineering-focused solution to achieve practical forecasting value.


### **Chronos-Bolt for Time Series Forecasting**  
**Chronos-Bolt**, developed by **Amazon**, extends **pretrained language models** for time series prediction by using **quantization and normalization**. Unlike **ARIMA**, it tokenizes financial time series data to improve **probabilistic forecasting accuracy**. Key advantages include:  
- **Generalization** across different market conditions with **minimal retraining**.  
- **Probabilistic sequence modeling** that improves uncertainty estimation.  
- **Enhanced accuracy** in predicting stock price movements over traditional models.
 
### **Sentiment Analysis for Financial Forecasting**  
A **multi-stage sentiment analysis pipeline** was developed to **extract investor sentiment** from **social media posts**:  
1. **Data Collection**: **30,000+ posts** from **WallStreetBets, Investing** (Jan 1, 2022 – Dec 31, 2024) were collected. After applying **keyword filters**, **5,800 relevant posts** related to **S&P 500 IT sector equities** were retained.  
2. **Two-Stage Sentiment Classification**:  
   - **Stage 1**: **FinBERT pre-filtering** classified posts into **bullish, bearish, or neutral** categories, reducing computational costs.  
   - **Stage 2**: **GPT-4-o-mini refinement** analyzed complex sentiment cases, maintaining **high classification accuracy**.  
3. **Temporal Aggregation**: Sentiment scores were aggregated **daily** and integrated into **forecasting models**.  

### **Portfolio Optimization Using the Markowitz Model**
Predicted stock prices were used for **Mean-Variance Optimization**:

$$
\max_w w^T \mu - \lambda w^T \Sigma w
$$

where $$w$$ represents portfolio weights, $$\mu$$ expected returns, and $$\Sigma$$ the covariance matrix. The optimization ensures:
- **Fully invested, long-only positions** with a **25% max allocation per stock**.
- **Risk aversion parameter** $$\lambda = 0.25$$.
An **investment simulation** with **$10,000 USD** tracked portfolio performance over time, benchmarking against the **S&P 500 IT Services Industry Index**. 

<div style="text-align:center">
    <img src="/dsc180-b08-website/pictures/marketcap.png" alt="An Example of Subreddit Page" width="500" height="200">
    <p><em>Top Market Cap Companies (source: tradingview.com)</em></p>
</div>

### **Summary**  
This method integrates **advanced time series forecasting**, **sentiment analysis**, and **portfolio optimization**, demonstrating the potential of **transformer-based models** and **investor sentiment signals** in financial decision-making.