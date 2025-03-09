---
title: Limitations and Future Directions
nav_order: 7
layout: default
permalink: /limitations-and-future-directions/
---

# Limitations and Future Directions

## Portfolio Optimization

One major challenge we encountered was that our portfolio optimization frequently concentrated investments into just one or two stocks. Although these concentrated allocations yielded positive returns, they **lack diversification**, creating vulnerabilities from a risk management perspective. To mitigate this, future work should explore incorporating **additional constraints**, such as sector-based allocation limits or modifications to the **risk aversion parameter**, aiming for a more balanced and diversified asset distribution.

## Sentiment Analysis

The predictive capability of Chronos-Bolt was enhanced by integrating social media sentiment, yet our current approach carries several limitations. Reliance on sentiment data sourced from Reddit, due to its accessible API, may be problematic because discussions on this platform might not strongly reflect actual trading behaviors. Although **social media sentiment** effectively captures general investor attitudes, it does not consistently provide clear trading signals. 

Therefore, future research should investigate **alternative data sources**, such as financial news APIs or earnings call transcripts, to achieve better alignment with market dynamics. Another issue is the susceptibility of sentiment classification to noise from informal language, sarcasm, and shifting narratives. While our filtering techniques and **confidence thresholding** improved reliability, future studies could benefit from refining sentiment models through **domain-specific training** or integrating multimodal data like financial news and analyst reports.

## Model Robustness and Market Shocks

Our evaluation primarily utilized historical data from relatively stable market conditions, leaving uncertainty about model performance during sudden market shocks. The **effectiveness of Chronos-Bolt and ARIMA** in handling events such as financial crises or geopolitical disruptions remains unclear. Assessing model robustness explicitly in these extreme scenarios is critical for understanding their applicability and limitations in real-world investment scenarios.

## Interpretability of Models

While ARIMA offers transparent insights due to its simplicity, Chronos-Bolt's deep learning architecture is inherently opaque, limiting interpretability. Developing **explainable AI methods** specifically for transformer-based financial models could significantly enhance trust and facilitate adoption, especially in risk-sensitive investment settings. Future work should focus on:

* Creating attribution techniques to identify influential features in predictions
* Developing visualization tools for attention mechanisms in financial contexts
* Establishing confidence metrics that communicate prediction reliability

## Hyperparameter Optimization and Additional Predictors

There is substantial potential to enhance forecasting performance through detailed **hyperparameter optimization**, including adjustments in **sequence length**, attention mechanisms, and feature selection within Chronos-Bolt. Additionally, integrating other predictive variables—such as earnings reports, macroeconomic indicators, and institutional investor sentiment—may further improve predictive accuracy and optimize portfolio strategies.

Overall, ongoing advancements in deep learning combined with improved sentiment analysis and diverse data integration offer significant opportunities to advance quantitative finance, enhancing both predictive power and practical applicability in portfolio management.

---
