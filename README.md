# NSE Stock Clustering Project

## Table of Contents

1. [Overview](#overview)
2. [Objective](#objective)
3. [Background](#background)
4. [Selected Metrics](#selected-metrics)
   - [Volatility](#1-volatility)
   - [Average Volume](#2-average-volume)
5. [Methodology](#methodology)
   - [1. Stock Selection](#1-stock-selection)
   - [2. Data Collection](#2-data-collection)
   - [3. Metric Calculation](#3-metric-calculation)
   - [4. Data Preparation](#4-data-preparation)
   - [5. Clustering](#5-clustering)
   - [6. Dimensionality Reduction (PCA)](#6-dimensionality-reduction-pca)
   - [7. Visualization](#7-visualization)
   - [8. Cluster Analysis](#8-cluster-analysis)
6. [Applications and Use Cases](#applications-and-use-cases)
7. [Potential Extensions](#potential-extensions)
8. [Limitations](#limitations)
9. [Conclusion](#conclusion)
10. [References](#references)

## Overview

This project clusters a set of NSE (National Stock Exchange of India) stocks based on their historical performance metrics, such as volatility and average trading volume. By clustering stocks, we can identify groups that exhibit similar behavior, which can be useful for portfolio diversification, risk management, and understanding market dynamics.

## Objective

The primary objective of this project is to group NSE stocks into clusters using historical data, focusing on volatility and average trading volume. These clusters can provide insights into the risk and liquidity profiles of different stocks, helping investors make informed decisions.

## Background

Stock market clustering is a technique used to group stocks that behave similarly in terms of certain financial metrics. By analyzing historical data, investors can identify patterns and trends that are not immediately apparent. Clustering can reveal natural groupings within the market, which can be useful for various investment strategies, including sector rotation, risk management, and portfolio optimization.

## Selected Metrics

### 1. Volatility

- **Description**: Volatility represents the degree of variation in a stock's trading price over time. It is a measure of risk, with higher volatility indicating higher potential returns (and losses).
- **Calculation**: Volatility is calculated as the standard deviation of daily returns. This metric gives us an idea of how much a stock's price fluctuates on a day-to-day basis.
- **Insight**: Stocks with higher volatility are considered riskier but may offer higher returns. Conversely, lower volatility stocks are typically more stable but may provide lower returns.

### 2. Average Volume

- **Description**: The average trading volume measures the average number of shares traded over a specific period. It is an indicator of liquidity, showing how easily a stock can be bought or sold.
- **Calculation**: Average volume is calculated as the mean of the daily trading volumes over the selected time period.
- **Insight**: High average volume suggests that a stock is more liquid, meaning it can be traded without significantly affecting the price. Low-volume stocks may be harder to trade, especially in large quantities.

## Methodology

### 1. Stock Selection

- **Criteria**: We selected a diverse set of 10 NSE stocks from various sectors to ensure that the clusters are not biased towards any specific industry.
- **Selected Stocks**:
  - `TCS.NS` (Technology)
  - `INFY.NS` (Technology)
  - `RELIANCE.NS` (Energy/Conglomerate)
  - `HDFCBANK.NS` (Banking/Financial)
  - `HINDUNILVR.NS` (Consumer Goods)
  - `ITC.NS` (Consumer Goods)
  - `ICICIBANK.NS` (Banking/Financial)
  - `SBIN.NS` (Banking/Financial)
  - `BAJFINANCE.NS` (Financial Services)
  - `HCLTECH.NS` (Technology)

### 2. Data Collection

- **Source**: We used the `yfinance` library to download historical stock data from Yahoo Finance.
- **Timeframe**: The data was collected for the last two years, ending on August 14, 2024.
- **Data Points**: The data includes daily adjusted closing prices and trading volumes for the selected stocks.

### 3. Metric Calculation

- **Daily Returns**: Calculated the percentage change in daily adjusted closing prices to assess the stock's day-to-day performance.
- **Volatility**: Computed as the standard deviation of the daily returns, representing the stock's risk.
- **Average Volume**: Calculated as the mean of the daily trading volumes over the two-year period, representing the stock's liquidity.

### 4. Data Preparation

- **Metrics DataFrame**: A DataFrame (`metrics`) was created containing the calculated volatility and average volume for each stock.
- **Standardization**: The data was standardized using `StandardScaler` to ensure that both features (volatility and average volume) contribute equally to the clustering algorithm.

### 5. Clustering

- **Algorithm**: K-Means clustering was used with three clusters (`n_clusters=3`). This algorithm partitions the data into distinct groups based on similarity.
- **Rationale**: K-Means was chosen for its simplicity and effectiveness in identifying natural groupings within the data. Three clusters were selected to explore different risk and liquidity profiles.

### 6. Dimensionality Reduction (PCA)

- **PCA (Principal Component Analysis)**: PCA was applied to reduce the two-dimensional feature space (volatility and average volume) to two principal components. Although this reduction might seem redundant, it helps in visualizing the clustering results more effectively.
- **Visualization**: The PCA components were used to create a scatter plot that visually represents the clusters.

### 7. Visualization

- **Scatter Plot**: A scatter plot of the PCA components was generated to visualize the clusters. Each stock is represented by a point, and stocks in the same cluster are colored similarly.
- **Annotation**: Stock tickers were annotated on the plot to make it easier to identify which stocks belong to which cluster.

### 8. Cluster Analysis

- **Cluster Breakdown**: The stocks in each cluster were printed to analyze which stocks were grouped together. This analysis provides insights into the characteristics shared by stocks within the same cluster.

## Applications and Use Cases

### 1. Portfolio Diversification

- **Description**: Investors can use these clusters to diversify their portfolios by selecting stocks from different clusters, thereby balancing risk and return.
- **Example**: By investing in stocks from both high-volatility and low-volatility clusters, an investor can create a balanced portfolio that minimizes risk while maximizing potential returns.

### 2. Risk Management

- **Description**: Understanding the volatility profiles of different clusters allows portfolio managers to adjust their exposure to riskier assets based on market conditions.
- **Example**: During times of market uncertainty, an investor might reduce exposure to stocks in the high-volatility cluster and increase holdings in the low-volatility cluster.

### 3. Sector Rotation Strategies

- **Description**: Investors can use cluster analysis to rotate between clusters based on market cycles, moving between different types of stocks as market conditions change.
- **Example**: In a bullish market, an investor might favor stocks in the high-volatility cluster, while in a bearish market, the focus might shift to the low-volatility cluster.

### 4. Algorithmic Trading

- **Description**: The insights from clustering can inform algorithmic trading strategies, such as mean-reversion or momentum strategies, by focusing on stocks within specific clusters.
- **Example**: An algorithm might be designed to trade stocks within the high-volume cluster when certain conditions are met, taking advantage of the liquidity and price movements.

## Potential Extensions

### 1. Include More Features

- **Description**: Additional financial metrics, such as P/E ratio, dividend yield, or market capitalization, could be included to create more nuanced clusters.
- **Example**: Clustering based on a combination of volatility, average volume, and P/E ratio could help identify undervalued stocks with high growth potential.

### 2. Different Timeframes

- **Description**: Applying the same analysis over different time periods (e.g., during a market downturn vs. a bull market) could reveal how stock behavior changes over time.
- **Example**: Analyzing the clusters during the 2020 market crash versus the 2021 recovery could provide insights into which stocks were resilient and which were not.

### 3. Explore Other Clustering Algorithms

- **Description**: Other clustering algorithms like hierarchical clustering or DBSCAN could be explored to see if they provide more insightful groupings.
- **Example**: Hierarchical clustering might reveal a nested structure in the data, where certain stocks are more closely related to each other than to the rest of the market.

### 4. Sector-Specific Clustering

- **Description**: Conducting a similar analysis within a single sector (e.g., just technology stocks) could provide insights into the relative performance of companies within that sector.
- **Example**: Clustering only technology stocks could help identify leaders and laggards within the sector, guiding sector-specific investment strategies.

## Limitations

### 1. Limited Feature Set

- **Issue**: The analysis only considers two features (volatility and average volume), which might oversimplify the clustering.
- **Impact**: Important factors influencing stock behavior might be overlooked, leading to less accurate clustering results.

### 2. Fixed Number of Clusters

- **Issue**: The choice of three clusters
