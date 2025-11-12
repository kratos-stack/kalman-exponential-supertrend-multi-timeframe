# 📈 User Guide

Welcome! This guide will help you get started with the trading indicators in this repository.

## 1. How to Add an Indicator to TradingView

You only need to do this once per script.

1.  **Find the Script:** Navigate to the `.pine` script file in this repository (e.g., `KalmanExponentialSuperTrend.pine`).
2.  **Copy the Code:** Click the "Copy raw file" button (or select all and copy) to get the entire script text.
3.  **Open TradingView:** Go to [TradingView](https://www.tradingview.com/) and open a chart.
4.  **Open Pine Editor:** At the bottom of the chart, click the "Pine Editor" tab.
5.  **Paste the Code:** Delete any text in the editor (like `//@version=...`) and paste the code you copied.
6.  **Add to Chart:** Click the "Add to Chart" button.

If there are no errors, the indicator will now appear on your chart!

## 2. How to Read the KEST Indicator

The "Kalman Exponential SuperTrend" (KEST) is a trend-following indicator.

* 
    **Bullish (Long) Trend:** When the line is **green**, the market is in a bullish trend. The line acts as a dynamic support. The price is expected to stay *above* this green line.

* 
    **Bearish (Short) Trend:** When the line is **red**, the market is in a bearish trend. The line acts as a dynamic resistance. The price is expected to stay *below* this red line.

* **Trend Change:** A trend change (and a potential trade signal) occurs when the price crosses the line and the color flips.
    * **Green flips to Red:** This is a bearish signal.
    * **Red flips to Green:** This is a bullish signal.

## 3. Configuring the Indicator

You can change the indicator's settings by hovering over its name on the chart and clicking the **Settings (gear ⚙️) icon**.

Here are the most important settings for the KEST:

* **ATR Length:** Controls the lookback for volatility.
    * **Lower number:** Tighter, more responsive bands (more signals).
    * **Higher number:** Wider, smoother bands (fewer signals).
* **Factor:** The multiplier for volatility.
    * **Lower number:** Tighter bands (more signals).
    * **Higher number:** Wider bands (fewer signals).
* **Enable MTF (Multi-Timeframe):** Check this box to use the indicator from a higher timeframe.
    * **Timeframe:** Select the timeframe you want to use (e.g., `4H` or `1D`). This will show the 4-hour or 1-day trend on your 15-minute chart.

## ⚠️ Disclaimer

**This is not financial advice.** The indicators and strategies in this repository are for educational and research purposes only. All trading involves risk, and you are solely responsible for your own decisions. Past performance is not indicative of future results.
