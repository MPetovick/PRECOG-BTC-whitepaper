# PRECOG BTC v7.0: Multi-Agent Predictive Analytics System - Technical Manual

**PRECOG BTC v7.0** is an advanced, multi-source predictive analytics engine for Bitcoin. It synthesizes real-time market data through a system of four specialized, autonomous analytical agents. Each agent employs a distinct, institutional-grade methodology—momentum, pattern recognition, volatility modeling, and risk management. A proprietary consensus engine aggregates and weights their independent predictions to generate a definitive **Consensus Price Target** and **Market Health Assessment**. This system is designed to provide a quantitative, multi-faceted perspective on market direction and risk, moving beyond single-indicator analysis.

## System Architecture & Data Flow
1.  **Multi-Source Data Ingestion**: The system polls and validates data from a prioritized cascade of sources: Binance (primary price/volume), CoinGecko (market aggregates), Blockchain.com (on-chain metrics), and Alternative.me (Fear & Greed Index).
2.  **Agent Processing Pool**: Parallel, independent analysis is performed by the four agents on the ingested historical and real-time data.
3.  **Consensus Engine**: A weighted algorithm calculates the final price target and signal, excluding the pure-risk agent (Sentinel) from the directional price consensus.
4.  **Unified Output & UI**: Results, agent-specific insights, and a composite Market Health Score are displayed via a dynamic interface.

## Agent Specifications & Methodologies
The system's core intelligence is distributed across four specialized agents, each with a defined analytical personality, weighted influence, and core algorithm.

| Agent (Codename) | Analytical Role (Persona) | Core Methodology & Key Metrics | Weight in Consensus | Confidence Drivers & Limitations |
| :--- | :--- | :--- | :--- | :--- |
| **AGATHA** (Momentum) | Trend Identification & Continuation | **Calculates:** RSI (14), MACD (12,26,9), Price Momentum (5,10,20 periods). **Model:** Adjusts prediction based on momentum slope and overbought/oversold RSI conditions. | 1.2 (Highest) | **High Confidence In:** Strong, sustained trends with aligned RSI/MACD. **Limited In:** Choppy, range-bound markets; prone to whipsaw signals near trend reversals. |
| **ARTHUR** (Pattern) | Price Action & Chartist Analysis | **Identifies:** Support/Resistance clusters, Chart Patterns (Head & Shoulders, Double Tops/Bottoms, Triangles, Flags). **Model:** Predicts based on pattern completion targets and volume confirmation. | 1.0 (Base) | **High Confidence In:** Clear, high-reliability patterns with defined volume profiles. **Limited In:** Ambiguous or nascent patterns; subjective pattern boundary detection. |
| **DASH** (Volatility) | Market Regime & Risk Environment Analysis | **Calculates:** Annualized Volatility, Average True Range (ATR), Bollinger Bandwidth, Volatility Clustering. **Model:** Adjusts prediction magnitude based on volatility regime (high/transition/low). | 0.9 | **High Confidence In:** Identifying breakout/breakdown environments from low-volatility compression. **Limited In:** Providing specific directional bias during stable, mean-reverting regimes. |
| **SENTINEL** (Risk) | Portfolio & Systemic Risk Management | **Calculates:** Value at Risk (VaR), Maximum Drawdown, Sharpe/Sortino Ratios, Liquidity Scores. **Role:** **Does not contribute to price consensus.** Provides risk level (Low/Med/High/Extreme), position-sizing limits, and stop-loss/take-profit recommendations. | N/A | **Triggers:** Elevated VaR (>5%), high historical volatility, extreme Fear/Greed readings, low liquidity. Essential for preserving capital but may limit gains in sustained bullish trends. |

## The Consensus Engine: Mathematical Foundation
The `ConsensusEngine.calculate()` function generates the primary system output.

**Core Consensus Price Formula:**
```
Consensus Price = Σ (Agent_Prediction_i × Agent_Weight_i) / Σ Agent_Weight_i
```
*Where `i` iterates over Agatha, Arthur, and Dash. Sentinel is excluded.*

**Derived Consensus Metrics:**
*   **Confidence (`avgConfidence`):** The arithmetic mean of the contributing agents' confidence scores.
*   **Agreement (`agreement`):** The maximum percentage of weighted signals (Bullish/Bearish/Neutral) aligned in one direction.
*   **Strength (`strength`):** A composite score: `(avgConfidence * agreement) / 100`. Represents the conviction and unity of the signal.

## Calculation Deep-Dive: Key Agent Algorithms
*   **AGATHA's RSI & Momentum:** Uses an exponential smoothing variant for RSI calculation. Momentum is calculated as the percent change over a lookback period (e.g., `(current - period_ago) / period_ago * 100`).
*   **ARTHUR's Pattern Detection:** Employs geometric logic to identify local maxima/minima for S/R. Pattern detection uses tolerance bands (e.g., ~0.5%) to identify shoulder/head relationships in Head & Shoulders formations.
*   **DASH's Volatility Regime:** Classifies market state (`high_volatility`, `low_volatility`, `transition`) by comparing current annualized volatility against static thresholds (e.g., >70% = high, <30% = low) and analyzing recent volatility clusters.
*   **SENTINEL's Value at Risk (VaR):** Calculates 95% confidence, 1-day historical VaR by sorting period returns and selecting the corresponding percentile loss.

## Professional Interpretation Framework
PRECOG outputs are decision-support tools, not autonomous trading signals. Effective use requires contextual interpretation.

### Interpreting the Consensus Output
| Scenario | What It Means | Contextual Checklist | Professional Action Implication |
| :--- | :--- | :--- | :--- |
| **Strong Bullish Consensus**<br>Signal: `BULLISH`<br>Confidence >75%, Strength >70 | High-probability upward move anticipated across multiple models. | 1. Confirm with higher timeframe trend.<br>2. Check for supporting volume spike.<br>3. Ensure Market Health is not "WEAK".<br>4. Review Sentinel's risk level. | **Consider LONG entry.** Entry near identified support (from Arthur) optimizes risk/reward. Use Sentinel's stop-loss as the **maximum allowable risk**. Target consensus price. |
| **Bearish Consensus + Extreme Greed**<br>Signal: `BEARISH`<br>F&G Index > 75 | Market is euphoric but models predict a downturn. High risk of sharp correction. | 1. Look for bearish divergences (price high, RSI lower high).<br>2. Identify if price is at a major resistance (Arthur).<br>3. Check volatility (Dash) for expansion potential. | **Extreme caution for new longs.** Strong case for **taking profits** on existing longs or initiating a **hedge/short position** with tight risk management above the recent high. |
| **Low Confidence / Neutral Consensus**<br>Confidence < 50%,<br>Agreement low | Market is indecisive, consolidating, or in transition. Agents lack a unified edge. | 1. Identify trading range boundaries.<br>2. Switch to lower timeframe for range play, or higher for context.<br>3. Await a catalyst or breakout. | **Stand aside or trade the range.** Avoid directional breakout bets until consensus confidence rises above 60-65% with clear agreement. Capital preservation is key. |
| **Agent Divergence**<br>(e.g., Agatha Bullish, Arthur Bearish) | Conflicting signals across timeframes or methodologies. Market at an inflection point. | 1. **Determine the dominant timeframe:** Which agent's analysis aligns with the higher-period chart?<br>2. **Await resolution:** The next significant price break will validate one agent's thesis. | **Do not trade the divergence.** This is an **observation signal**, not an action signal. Prepare strategies for both potential breakout directions and wait for confirmation. |

### Integrating Market Health & Sentinel
*   **Health Score "WEAK":** Overrides any bullish consensus. Indicates a hostile trading environment (high volatility, extreme sentiment, poor liquidity). **Action:** Drastically reduce position size (<50% of normal) or remain in cash.
*   **Sentinel Risk "EXTREME":** An urgent risk-off signal, often coinciding with high VaR and max drawdown. **Action:** Close speculative positions, tighten stops on core holdings, raise cash.
*   **Using Sentinel's Recommendations:** The suggested `maxPosition` (e.g., 2% of portfolio) and `stopLoss` (e.g., -8%) are **maximum bounds**. Professional practice is to use **tighter** constraints (e.g., half of the suggested position size).

## Critical Disclaimer & System Limits
**This system is a sophisticated analytical tool, not financial advice.** Cryptocurrency markets are extremely volatile. All investments carry risk, including total loss.

**Known System Limitations:**
*   **Black Swan Events:** Models are trained on historical data and cannot predict unforeseen macroeconomic or regulatory shocks.
*   **Overfitting Risk:** Agent logic, while complex, is rule-based and may overfit to specific past market conditions.
*   **Data Latency & Failures:** Relies on external API stability. The fallback mode provides simulated data, which is not suitable for live trading.
*   **No Macro-Financial Integration:** Does not incorporate traditional market correlations, interest rates, or news sentiment analysis.

**Best Practice:** Use PRECOG's consensus as a **high-probability "bias"** within a broader trading plan that includes strict capital preservation rules, independent fundamental analysis, and sound money management. Always conduct your own due diligence.

---
