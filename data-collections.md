---
title: Data Collections
nav_order: 3
layout: default
permalink: /data-collections/
---

# Data Collections
### **Data Collection**  


### **Sentiment Analysis**  
## Data Sources
Stock price data for **S&P 500 Information Technology sector** companies was collected from **Yahoo Finance**, with the company list sourced from **TradingView**. The dataset includes **daily closing prices** from **January 1, 2022, to December 31, 2024**.

To integrate **investor sentiment** into stock predictions, a structured **social media sentiment pipeline** was developed. **54,000+ posts** from **finance-focused subreddits** (e.g., *WallStreetBets, Investing*) were collected from **January 1, 2022, to December 31, 2024**.

## Data Processing
 -**Yahoo Finance** Missing values were removed to ensure a **clean dataset** for forecasting and analysis.
 
 -**Reddit** A **keyword filter** was applied to isolate **25,800 relevant posts** discussing **S&P 500 IT sector equities**. Posts were preprocessed by removing **non-text elements** and filtered for **English-language content**. Sentiment was classified using **large language models (LLMs)** to generate **bullish, bearish, or neutral signals** for downstream portfolio optimization.

---

*(Update this section with specific details relevant to your project.)*
