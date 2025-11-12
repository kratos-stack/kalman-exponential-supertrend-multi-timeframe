# Trading Strategy Documentation

This document provides a detailed breakdown of each trading strategy and indicator available in this repository. Each entry explains the core logic, input parameters, and intended use.

## Table of Contents

1.  [Kalman Exponential SuperTrend (KEST)](#1-kalman-exponential-supertrend-kest)
2.  [Strategy Template (Copy This)](#2-strategy-template-copy-this)

---

## 1. Kalman Exponential SuperTrend (KEST)

**File:** `KalmanExponentialSuperTrend.pine`

### Overview

The Kalman Exponential SuperTrend (KEST) is a trend-following indicator designed to provide clearer signals and reduce lag compared to traditional SuperTrend indicators. It achieves this by using a **Kalman Filter** to calculate its baseline, resulting in a smoother and more responsive price series. The SuperTrend bands are then calculated using an exponential smoothing method, further enhancing responsiveness.

### Core Logic

1.  **Price Filtering:** The script first takes the `pricesource` (e.g., `close`) and processes it through a Kalman Filter. This filter estimates the "true" price of the asset, reducing market noise without introducing significant lag.
2.  **ATR Bands:** The script calculates the Average True Range (ATR) over a specified `len` (length).
3.  **Base Bands:** It then calculates the initial `UpperBand` and `LowerBand` by adding/subtracting the `atr * mul` (ATR * multiplier) from the `kalmanFilteredPrice`.
4.  **Exponential Smoothing:** These base bands are then exponentially smoothed (similar to an EMA) to create the final `Upper` and `Lower` bands. This prevents the bands from "gapping" aggressively and allows them to follow the price more closely.
5.  **Trend Logic:**
    * The trend turns **bullish (1)** when the `src` price crosses *over* the `Upper` band.
    * The trend turns **bearish (-1)** when the `src` price crosses *under* the `Lower` band.

### How to Interpret

* **Bullish Trend:** When the indicator is green (or your selected `bullcol`), and the price is above the green line (the `Lower` band), the trend is considered bullish. The green line acts as a dynamic support level.
* **Bearish Trend:** When the indicator is red (or your selected `bearcol`), and the price is below the red line (the `Upper` band), the trend is considered bearish. The red line acts as a dynamic resistance level.
* **Fill/Price Plot:** The area between the `src_calc` price plot and the active band is filled, providing a clear visual representation of the current trend and its "breathing room."

### Key Parameters

* **ATR Length (`len`):** The lookback period for the ATR calculation. A shorter length makes the bands more sensitive to volatility.
* **Factor (`mul`):** The multiplier for the ATR. A larger factor creates wider bands, resulting in fewer signals (and vice-versa).
* **Kalman Price Source:** The source price to be fed into the Kalman filter (default: `close`).
* **Process Noise (`processNoise`):** A Kalman filter setting. Lower values create a smoother, slower filter. Higher values make it more responsive.
* **Measurement Noise (`measurementNoise`):** A Kalman filter setting. Lower values make the filter trust the measurement more (more "jittery"). Higher values make it trust its own internal estimate (smoother).
* **MTF Settings:**
    * **Enable MTF:** Toggles multi-timeframe analysis.
    * **Timeframe:** Sets the higher timeframe to pull data from.

---

## 2. Strategy Template (Copy This)

(Copy and paste this template for each new strategy you add)

**File:** `path/to/your/script.pine`

### Overview

[Provide a 1-2 paragraph summary of the strategy. What is its name? What is its primary goal (e.g., trend-following, mean-reversion, volatility breakout)? What makes it unique?]

### Core Logic

[Explain the step-by-step logic of the indicator or strategy. Use a numbered or bulleted list if possible.]

1.  **[Logic Step 1]:** [e.g., Calculates a 20-period RSI.]
2.  **[Logic Step 2]:** [e.g., Looks for bullish/bearish divergence between price and RSI.]
3.  **[Entry Conditions]:** [e.g., A long signal is generated when...]
4.  **[Exit Conditions]:** [e.g., The trade is exited when...]

### How to Interpret

* **Long Signal:** [e.g., A blue arrow appears on the chart.]
* **Short Signal:** [e.g., A red arrow appears on the chart.]
* **Indicator Lines:** [e.g., The blue line is the "fast" MA, the yellow line is the "slow" MA.]

### Key Parameters

* **Parameter 1 (`param_name`):** [Description of the parameter and its effect.]
* **Parameter 2 (`param_name`):** [Description of the parameter and its effect.]
* **Parameter 3 (`param_name`):** [Description of the parameter and its effect.]

---