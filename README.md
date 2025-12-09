# newImperiumchallenge

# Imperium Systematic Solutions – XAUUSD 2025 Data Challenge

**Author:** MED KH  
**Instrument:** XAUUSD CFD  
**Period:** 2025 (orders & deals) + 5-min candles  
**Goal:** Reverse-engineer the underlying trading strategies and propose robust, implementable improvements.

## 0. Notebook Roadmap

This notebook is organised exactly along the questions in the challenge:

1. **Q1 – Data Understanding & Preparation**

   - Load and reconcile `orders`, `deals`, and 5-minute candle data
   - Build a clean trade list (entry/exit, PnL, duration)
   - Attach market regime features at entry (ATR, ADX, RSI, Stoch, BB, session, etc.)

2. **Q2 – Strategy Clustering & Behaviour**

   - Cluster trades into strategy groups using entry/exit features
   - Describe each cluster: win rate, PnL, duration, volatility regime, session preferences
   - Identify intuitive labels (e.g. range trader, trend follower, volatility breakout, momentum continuation)

3. **Q3 – Inference of Trading Rules**

   - From cluster patterns, infer:
     - Entry logic (trend / range / volatility / pullback / breakout)
     - Exit logic (oscillator exhaustion, time-based exits, momentum collapse)
     - Stop-loss / take-profit style (tight vs loose, time-stop vs price-stop)
   - Translate cluster behaviour into human-readable “pseudo-rules”

4. **Q4 – Robustness & Simple Filters**

   - Test simple, interpretable filters:
     - Volatility (e.g. ATR buckets)
     - Time windows / sessions (Asian, London, NY, Late NY)
     - Trend context (ADX) and oversold/overbought (RSI / Stoch)
   - Evaluate impact on: win rate, average profit per trade, trade count
   - Control overfitting via:
     - Chronological train/test split (walk-forward validation)
     - Bootstrap confidence intervals
     - Effect sizes (Cohen’s d) and p-values
   - Highlight a small set of **robust filters** that improve performance without exploding model complexity.

5. **Q5 – Risk, Portfolio Interaction & Recommendations**
   - Analyse how clusters interact at portfolio level:
     - Correlations between cluster PnL streams
     - Contribution to drawdowns and volatility
     - Behaviour across regimes (high/low vol, sessions)
   - Propose a practical deployment template:
     - Which clusters to keep/emphasise
     - When to throttle or turn off risk (e.g. high ATR NY session)
     - How to combine filters and position sizing rules.
