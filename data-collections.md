---
title: Data Collections
nav_order: 3
layout: default
permalink: /data-collections/
---

# Data Collections

## Data Sources
Stock price data for **S&P 500 Information Technology sector** companies was collected from **Yahoo Finance**, with the company list sourced from **TradingView**. The dataset includes **daily closing prices** from **January 1, 2022, to December 31, 2024**.
<div style="text-align:center">
    <img src="/dsc180-b08-website/pictures/yahoo.png" alt="An Example of Subreddit Page" width="700" height="300">
    <p><em>An Example of Apple's Stock Price on Yahoo Finance (Source:reddit.com/)</em></p>
</div>

To integrate **investor sentiment** into stock predictions, a structured **social media sentiment pipeline** was developed. **54,000+ posts** from **finance-focused subreddits** (e.g., *WallStreetBets, Investing*) were collected from **January 1, 2022, to December 31, 2024**.

<div style="text-align:center">
    <img src="/dsc180-b08-website/pictures/reddit.png" alt="An Example of Subreddit Page" width="700" height="300">
    <p><em>An Example of WallStreetBets Subreddit (Source:finance.yahoo.com)</em></p>
</div>

## Data Processing
 -**Yahoo Finance** Missing values were removed to ensure a **clean dataset** for forecasting and analysis.
 
 -**Reddit** A **keyword filter** was applied to isolate **25,800 relevant posts** discussing **S&P 500 IT sector equities**. Posts were preprocessed by removing **non-text elements** and filtered for **English-language content**. Sentiment was classified using **large language models (LLMs)** to generate **bullish, bearish, or neutral signals** for downstream portfolio optimization.

---

*(Update this section with specific details relevant to your project.)*
