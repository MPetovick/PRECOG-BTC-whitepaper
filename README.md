# PRECOG BTC - Advanced Bitcoin Prediction System

**Predict Bitcoin's future with mathematical precision**  
Combines advanced technical analysis with adaptive AI to generate reliable trading signals

## What is PRECOG BTC?

PRECOG BTC is a financial prediction system that uses advanced algorithms and technical analysis to anticipate Bitcoin price movements. Unlike traditional tools:

✅ Combines **12+ technical indicators** in real-time  
✅ Applies the **golden ratio** to identify turning points  
✅ Generates **consensus signals** through adaptive AI  
✅ Provides **actionable recommendations** with precise levels

> "PRECOGs work better in packs. The system internally runs three independent precogs (Agatha, Arthur, Dash) and combines their predictions for a stronger signal."

## How the PRECOG System Works

The PRECOG system operates through a multi-layered approach:

1. **Data Collection Layer:**
   - Real-time market data from APIs (CryptoCompare and Binance)
   - Intelligent caching system (3-minute cache TTL)
   - Continuous price updates (every 3 seconds)

2. **Technical Analysis Engine:**
   - RSI (Relative Strength Index)
   - MACD (Moving Average Convergence Divergence)
   - Bollinger Bands
   - Ichimoku Cloud
   - Fibonacci Retracement Levels
   - Golden Momentum (proprietary algorithm)

3. **Multi-PRECOG Core:**
   - **Agatha**: Uses the current selected timeframe (default 1H)
   - **Arthur**: Configurable timeframe (default 4H) for short-term analysis
   - **Dash**: Configurable timeframe (default 12H) for medium-term analysis
   - The system combines the three predictions to generate a final PRECOG signal.

4. **Trading Intelligence:**
   - Position optimization
   - Dynamic stop-loss algorithms
   - Harmonic profit targets

## How to Use

1. **Select Timeframe**: Click on the timeframe buttons (1H, 4H, 6H, 12H, 1D, 1W, 30D) to change the chart and analysis period.
2. **Configure Precogs**: Click the gear icon (⚙️) to open the precog configuration modal. Here you can change the timeframes used by Arthur and Dash.
3. **Toggle Indicators**: Click on the indicator icons (MACD, Bollinger Bands, Fibonacci) below the chart to show/hide them.
4. **Refresh Data**: Click the refresh button to manually update the data.

## Interpreting the Interface

- **Current Price**: The live price of Bitcoin with 24h change.
- **Prediction Price**: The system's predicted price for the selected timeframe. The color intensity indicates the strength of the expected move (light to dark green for bullish, light to dark red for bearish).
- **Confidence Level**: The system's confidence in the prediction (0-100%).
- **PRECOG Price**: The combined prediction from Agatha, Arthur, and Dash.
- **Technical Indicators Panel**: Shows the current values of key indicators and their trends.
- **Trading Recommendations**: Provides key support, take profit, stop loss levels, trading strategy, optimal position, risk factor, and backtesting accuracy.

## Advanced Technology Under the Hood

| Layer               | Technologies                                 | Function                             |
|---------------------|---------------------------------------------|--------------------------------------|
| **Data Ingestion**  | WebSockets, CryptoCompare API, Binance API  | Real-time data with smart caching    |
| **Processing**      | Web Workers, Float64Arrays                  | Parallel computations                |
| **Analysis**        | Custom EMA/MACD, Golden Ratio algorithms    | Complex pattern detection            |
| **Visualization**   | Chart.js + plugins, CSS Variables           | Interactive responsive charts        |
| **Adaptation**      | Autoregressive models                       | Continuous market adaptation         |

## Key System Metrics

| Metric               | Optimal        | Risk Zone      | Interpretation                     |
|----------------------|----------------|----------------|------------------------------------|
| **Confidence**       | >80%           | <50%           | Prediction reliability             |
| **Golden Momentum**  | >5%            | <-3%           | Trend strength                     |
| **Volatility**       | 15-25%         | >35%           | Risk of sharp movements            |
| **Historical Acc.**  | >85%           | <70%           | Model effectiveness                |
| **Fib Levels**       | 8+/12          | <4/12          | Support/resistance proximity       |
