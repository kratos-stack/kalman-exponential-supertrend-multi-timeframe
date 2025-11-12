# Kalman Exponential SuperTrend - Multi-Timeframe (KEST MTF)

[![TradingView](https://img.shields.io/badge/TradingView-Pine%20Script%20v6-blue)](https://www.tradingview.com/)
[![License: MPL 2.0](https://img.shields.io/badge/License-MPL%202.0-brightgreen.svg)](https://opensource.org/licenses/MPL-2.0)

An enhanced version of the Kalman Exponential SuperTrend indicator with **Multi-Timeframe (MTF) support**, allowing traders to analyze higher timeframe trends while operating on lower timeframe charts.

## 🎯 Overview

The Kalman Exponential SuperTrend (KEST) combines three powerful technical analysis components:

1. **Kalman Filter** - Advanced noise reduction and price smoothing
2. **Exponential Smoothing** - Adaptive trend following with reduced lag
3. **SuperTrend Logic** - Clear trend direction and support/resistance levels

The **MTF enhancement** adds the ability to calculate these components on any timeframe while displaying them on your current chart.

## ✨ Features

### Core Functionality
- **Kalman Filter Integration** - Multi-order filter for superior price smoothing
- **Exponential SuperTrend** - Reduced lag compared to traditional SuperTrend
- **Dynamic Support/Resistance** - Adaptive bands that follow price action
- **Trend Detection** - Clear bullish/bearish signals with crossover logic

### Multi-Timeframe Support
- ✅ **Timeframe Selector** - Choose any timeframe (5m, 15m, 1H, 4H, D, W, etc.)
- ✅ **Toggle On/Off** - Easily switch between chart timeframe and MTF mode
- ✅ **No Repainting** - Uses `barmerge.gaps_off` for reliable signals
- ✅ **Seamless Integration** - Works with all existing style options

### Visual Customization
Seven pre-built color schemes:
- 🐉 **Dragonic** - Green/Pink (default)
- ⚔️ **Medieval** - Cyan/Dark
- 🔮 **Modern** - Cyan/Magenta
- 🕹️ **Retro** - Blue/Gold
- 🚀 **Futuristic** - Teal/Red
- 🌴 **Tropical** - Yellow/Orange
- 📊 **OG** - Classic Green/Red

## 📥 Installation

1. Open TradingView and navigate to the Pine Editor
2. Create a new indicator
3. Copy and paste the entire script
4. Click "Save" and then "Add to Chart"

## 🎮 Usage

### Basic Setup
1. Add the indicator to your chart
2. The indicator runs on the chart timeframe by default
3. Adjust **ATR Length** and **Factor** to tune sensitivity
4. Select your preferred **Plotting Style**

### Multi-Timeframe Mode
1. In indicator settings, check **"Enable Multi-Timeframe"**
2. Select your desired timeframe:
   - `5` = 5 minutes
   - `15` = 15 minutes
   - `60` = 1 hour
   - `240` = 4 hours
   - `D` = Daily
   - `W` = Weekly
3. The indicator will now calculate on the selected timeframe

### Kalman Filter Tuning
- **Process Noise** (0.01 default) - Lower = smoother but more lag
- **Measurement Noise** (3.0 default) - Higher = more smoothing
- **Filter Order** (5 default) - Higher = more aggressive filtering

## 📊 Trading Applications

### Higher Timeframe Trend Following
- View daily trends while trading on 15-minute charts
- Avoid counter-trend trades by aligning with HTF direction
- Example: Enable MTF with "D" timeframe on 1H chart

### Multi-Timeframe Confluence
- Use multiple instances with different timeframes
- Look for alignment across 1H, 4H, and Daily
- Enter trades when all timeframes agree

### Reduced Noise Trading
- Calculate on higher timeframe to filter intraday noise
- Get clearer trend direction
- Reduce false signals during choppy markets

## 🔧 Parameters

### SuperTrend Settings

| Parameter    | Default | Range  | Description                      |
|:-------------|:-------:|:------:|:---------------------------------|
| ATR Length   | 13      | 2+     | Lookback period for volatility   |
| Factor       | 1.75    | 0.01+  | Multiplier for band distance     |

### Kalman Filter Settings

| Parameter          | Default | Range   | Description                      |
|:-------------------|:-------:|:-------:|:---------------------------------|
| Price Source       | Close   | Any     | Input data for filter            |
| Process Noise      | 0.01    | 0.001+  | State transition uncertainty     |
| Measurement Noise  | 3.0     | 0.1+    | Observation uncertainty          |
| Filter Order       | 5       | 1+      | Number of filter states          |

### Multi-Timeframe Settings

| Parameter    | Default | Description                           |
|:-------------|:-------:|:--------------------------------------|
| Enable MTF   | false   | Toggle multi-timeframe mode           |
| Timeframe    | ""      | Target timeframe for calculation      |

## 🎨 Color Coding

- **Green/Cyan/Yellow tones** = Bullish trend (depending on style)
- **Red/Pink/Orange tones** = Bearish trend (depending on style)
- **Bands** = Dynamic support (bullish) or resistance (bearish)
- **Fill** = Visual trend clarity between price and bands

## 📈 Signal Interpretation

### Bullish Signals
- Price crosses above the upper band
- Band color changes to bullish (green/cyan/yellow)
- Lower band is displayed as support
- Trend variable = 1

### Bearish Signals
- Price crosses below the lower band
- Band color changes to bearish (red/pink/orange)
- Upper band is displayed as resistance
- Trend variable = -1

### MTF Considerations
- MTF signals change less frequently than chart timeframe
- More reliable but fewer signals
- Best used for trend direction, not precise entries

## 🔬 Technical Details

### How It Works
1. **Kalman Filtering** - Price data is processed through a multi-state Kalman filter to reduce noise
2. **ATR Calculation** - Volatility is measured using Average True Range
3. **Band Generation** - Upper and lower bands are created using filtered price ± (ATR × Factor)
4. **Exponential Smoothing** - Bands are smoothed using exponential weighted moving average
5. **Trend Logic** - Trend changes when price crosses the opposite band
6. **MTF Processing** - When enabled, final values are fetched from the selected timeframe

### Why Kalman Filter?
- Adapts to changing market conditions
- Reduces lag while maintaining smoothness
- Handles outliers better than simple moving averages
- Provides optimal estimates of true price

### Why Exponential Smoothing?
- More responsive to recent price action than simple average
- Reduces whipsaws during consolidation
- Maintains trend following characteristics

## 🆚 Comparison with Standard SuperTrend

| Feature            | Standard SuperTrend | KEST MTF          |
|:-------------------|:-------------------:|:------------------|
| Price Input        | Raw OHLC            | Kalman Filtered   |
| Band Smoothing     | None                | Exponential       |
| Noise Reduction    | Minimal             | Advanced          |
| Lag                | Moderate            | Lower             |
| False Signals      | More                | Fewer             |
| Multi-Timeframe    | No                  | Yes               |
| Customization      | Limited             | Extensive         |

## 💡 Tips & Best Practices

1. **Start with defaults** - The default parameters work well for most assets
2. **Match timeframes** - Use MTF timeframe 3-4x your chart timeframe (e.g., 4H MTF on 1H chart)
3. **Combine with other tools** - Use with volume, RSI, or price action for confirmation
4. **Adjust for volatility** - Increase Factor for crypto, decrease for forex
5. **Test before trading** - Backtest parameter combinations on historical data
6. **Lower filter order** - For faster assets, reduce Filter Order to 3
7. **Higher timeframe alignment** - Only take trades in direction of MTF trend

## 🐛 Troubleshooting

**Issue: Indicator is too choppy**
- Increase Process Noise or Measurement Noise
- Increase ATR Length
- Increase Factor

**Issue: Indicator is too slow**
- Decrease Process Noise or Measurement Noise
- Decrease ATR Length
- Decrease Factor
- Decrease Filter Order

**Issue: MTF not working**
- Ensure "Enable Multi-Timeframe" is checked
- Verify timeframe is higher than chart timeframe
- Check that timeframe format is correct (e.g., "60" not "1H")

**Issue: Too many false signals**
- Enable MTF with higher timeframe
- Increase Factor value
- Increase Measurement Noise

## 📜 License

This project is licensed under the Mozilla Public License 2.0 - see the [LICENSE](https://mozilla.org/MPL/2.0/) for details.

## 👨‍💻 Author

**MisinkoMaster**

Original KEST Indicator + Multi-Timeframe Enhancement

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to:
- Open an issue for bugs or suggestions
- Submit pull requests with enhancements
- Share your trading results and parameter configurations

## ⚠️ Disclaimer

This indicator is for educational and informational purposes only. It should not be considered financial advice. Always:
- Do your own research (DYOR)
- Test strategies on paper/demo accounts first
- Use proper risk management
- Never risk more than you can afford to lose
- Consult with a financial advisor before making investment decisions

Trading and investing involve substantial risk of loss and are not suitable for every investor.

## 📚 Resources

- [Pine Script Documentation](https://www.tradingview.com/pine-script-docs/)
- [Kalman Filter Explained](https://www.kalmanfilter.net/)
- [SuperTrend Strategy Guide](https://www.tradingview.com/scripts/supertrend/)

## 🌟 Acknowledgments

- Thanks to the TradingView community for inspiration
- Original SuperTrend concept by Olivier Seban
- Kalman filter mathematics by Rudolf E. Kálmán

---

**If you find this indicator useful, please ⭐ star the repository!**