---
title: Results
nav_order: 5
layout: default
permalink: /results/
---

# Results

## Stock Return Prediction Performance

Our comparative analysis of ARIMA and Chronos-Bolt models for stock return forecasting revealed significant differences in predictive accuracy. The table below presents the Mean Absolute Scaled Error (MASE) for both models across various stocks in the S\&P 500 Information Technology sector.

### Comparing Predictive Accuracy: ARIMA vs. Chronos for Stock Forecasting

| Ticker | Company    | ARIMA MASE | Chronos MASE | Chronos with Sentiment Analysis |
|:------:|:---------:|:----------:|:------------:|:--------------------------------:|
|  AAPL  |   Apple   |  4.404759  |   1.277648   |          1.187000               |
|  MSFT  | Microsoft |  2.577242  |   1.257515   |          1.194542               |
|  NVDA  |  Nvidia   |  1.667199  |   0.786434   |          0.650632               |
|  AVGO  | Broadcom  |  2.358288  |   0.825056   |          0.760912               |
|  ORCL  |  Oracle   |  1.627883  |   1.002716   |          0.933530               |
|  CRM   |Salesforce |  3.041072  |   1.398177   |          1.258305               |
|  CSCO  |   Cisco   |  2.719316  |   0.767192   |          0.719300               |
|  IBM   |    IBM    |  3.873951  |   0.791281   |          0.740314               |
|  ADBE  |   Adobe   |  2.543290  |   1.136429   |          1.058090               |
|  QCOM  | Qualcomm  |  2.539423  |   0.989846   |          0.907200               |
|  AMD   |    AMD    |  3.051562  |   1.095745   |          1.030000               |
|  PLTR  | Palantir  |  4.264606  |   0.932880   |          0.886236               |

The results demonstrate that Chronos consistently outperforms ARIMA across all evaluated stocks, with MASE values significantly lower for the Chronos model. When incorporating sentiment analysis, Chronos exhibits further improvements in prediction accuracy, reducing MASE values by an additional 5-15\% compared to the standard Chronos implementation.

### NVDA Stock Price Forecast Comparison

<div style="text-align:center">
    <img src="/dsc180-b08-website/pictures/NVDA_example.png" alt="NVDA Stock Price Forecast Comparison" width="700" height="300">
    <p><em>NVDA Stock Price Forecast Comparison</em></p>
</div>

The plot above illustrates the prediction of NVDA stock prices using ARIMA and Chronos-Bolt models, highlighting their respective performances. The historical stock prices are depicted in blue, while the ARIMA forecast is shown as a green dashed line, and the Chronos-Bolt forecast appears in red. The naive forecast, represented by a black dashed line, serves as a baseline for comparison. Additionally, the pink-shaded area represents the 80\% prediction interval for the Chronos-Bolt model, indicating the uncertainty associated with its predictions. The figure further emphasizes the superior predictive accuracy of Chronos-Bolt, as its forecast aligns more closely with the actual stock price movements compared to ARIMA.

## Portfolio Optimization Results

Our portfolio consists of the stocks listed in the above table. We begin by allocating each stock's weight based on its relative market capitalization within the portfolio. As the investment period progresses, stock weights are dynamically adjusted using predictions from the time series models and sentiment scores. To maintain diversification, we impose a minimum weight constraint of 0.05 for each stock. Additionally, we set a risk aversion parameter of 2.5 to balance return maximization with risk control. The portfolio is initialized with a starting value of \$10,000.

For comparison, we evaluate its performance against a benchmark portfolio that maintains fixed allocations based on market capitalization. The integration of these forecasting models into portfolio optimization frameworks yielded varying performance outcomes, as shown in the figure below.

### Portfolio Performance Comparison Across Market Cap, ARIMA, and Chronos-Bolt Over Time

<div style="text-align:center">
    <img src="/dsc180-b08-website/pictures/enhanced_portfolio_comparison.png" alt="Portfolio Performance Comparison" width="700" height="300">
    <p><em>Portfolio Performance Comparison</em></p>
</div>

The above portfolio optimization analysis revealed several key findings:

- The Market Cap Portfolio (blue line) maintained relatively stable performance, serving as an effective benchmark for evaluating ARIMA and Chronos models.
- The ARIMA-based portfolio (orange line) demonstrated extreme volatility and a sharp decline over the evaluation period, significantly underperforming compared to other approaches.
- Both Chronos-Bolt portfolios, with and without sentiment analysis, consistently outperformed the Market Cap Portfolio benchmark.
- The sentiment-enhanced Chronos-Bolt portfolio (purple dotted line) achieved the highest returns among all evaluated approaches, highlighting the value of incorporating investor sentiment signals into the forecasting framework.

These results confirm our hypothesis that transformer-based models like Chronos-Bolt can capture complex patterns in stock market data more effectively than traditional ARIMA models. Furthermore, the integration of sentiment analysis provides additional predictive power, resulting in superior portfolio performance.

---