# 10 EMA MOMENTUM TRADING STRATEGY - Pine Script Indicator

## Overview
Pine Script indicator for TradingView implementing a data-driven 10 EMA momentum strategy optimized through 257 backtested trades with 59.5% overall win rate.

## Strategy Performance (Backtest Results)
- **Total Trades:** 257 over 94 trading days
- **Overall Win Rate:** 59.5%
- **Optimal Win Rate:** 89% (in sweet spot conditions)
- **Asset:** TSLA on 3-minute charts
- **Method:** Candle pause breakouts at 10 EMA

---

## 🎯 KEY FINDINGS FROM BACKTEST

### **Time-of-Day Performance (Central Time)**

#### 🟢 BEST TIMES (Trade Aggressively)
- **2:00-3:00 PM CST: 80.0% WR** ⭐ GOLDEN HOUR (15 trades)
- **1:00-2:00 PM CST: 71.9% WR** (32 trades)
- Combined 1-3 PM window: **~76% win rate**

#### ✅ GOOD TIMES (Trade Selectively)
- **9:00-10:00 AM CST: 65.9% WR** (44 trades) - Score 5 setups only

#### ⚠️ CAUTION ZONES (Below Average)
- **11:00-12:00 PM CST: 63.4% WR** (41 trades)
- **8:30-9:00 AM CST: 61.5% WR** (13 trades)

#### 🔴 DANGER ZONES (AVOID COMPLETELY)
- **10:00-11:00 AM CST: 47.6% WR** (63 trades) 🚫
- **12:00-1:00 PM CST: 47.2% WR** (36 trades) 🚫
- **Combined 10 AM-1 PM: ~47% WR - LOSING MONEY**

### **Stop Distance Optimization**

#### Win Rate by Stop Distance:
- **0.0-0.5%:** 68.3% WR (104 trades) - Too tight, getting stopped out early
- **0.55-0.70%:** 88.6% WR (44 trades) ⭐ SWEET SPOT
- **0.70-1.0%:** 90.0% WR (20 trades) ⭐ EXTENDED SWEET SPOT
- **1.0-1.5%:** 90.0% WR (10 trades) - Small sample
- **Optimal Range: 0.55-1.0% from entry = ~89% win rate**

---

## 📊 INDICATOR FEATURES

### Visual Components
1. **Time-Based Background Colors**
   - Brightest Green: 2:00-3:00 PM CST (Golden Hour - 80% WR)
   - Green: 1:00-2:00 PM CST (71.9% WR)
   - Light Green: 9:00-10:00 AM CST (65.9% WR)
   - Yellow: Caution zones (61-63% WR)
   - Red: Danger zones (47% WR - AVOID)

2. **EMA Cloud System**
   - 10/20 EMA Cloud (Entry signals)
   - 15/35 EMA Cloud (Trend confirmation)
   - Additional EMAs: 10, 15, 20, 35
   - SMAs: 33, 50, 100, 200

3. **Signal Arrows**
   - Green Arrow: Bullish setup (green candle crosses under 10 EMA)
   - Red Arrow: Bearish setup (red candle crosses over 10 EMA)

4. **Dashboard (Top Right)**
   - Trend Status (BULL/BEAR/MIXED)
   - Market Status (TRENDING/CHOP)
   - 15/35 EMA Separation %
   - RSI
   - Distance from 10 EMA
   - Last Signal Price

5. **Chop Filter**
   - Orange background when market is chopping
   - Based on 15/35 EMA separation threshold

---

## 🎯 TRADING RULES (DATA-DRIVEN)

### **Rule 1: TIME OF DAY**
**ONLY trade during:**
- ✅ **1:00-3:00 PM CST** (Primary window - 76% WR)
- ✅ **9:00-10:00 AM CST** (Secondary - 65.9% WR, Score 5 setups only)

**NEVER trade during:**
- 🚫 **10:00 AM - 1:00 PM CST** (47% WR)

### **Rule 2: STOP PLACEMENT**
**Only take trades where stop distance is 0.55-1.0% from entry:**
- Use signal candle low (long) or high (short)
- Fallback: 35 EMA
- **Skip trade if stop <0.55%** (too tight, 68% WR)
- **Skip trade if stop >1.0%** (too wide, limited data)

### **Rule 3: TRADE FREQUENCY**
- No hard daily limit needed
- Quality filters naturally limit to 2-3 trades/day
- Average from backtest: 2.7 trades/day

### **Rule 4: AFTER LOSSES**
- Win rate after loss: 60.0% (heightened focus)
- Continue trading quality setups after losses

---

## 📈 EXPECTED PERFORMANCE

### **Current Performance (No Filters):**
- Overall: 59.5% WR

### **With Time-Only Filter:**
- Avoid 10 AM-1 PM: **~67% WR** (+7.5% improvement)

### **With Time + Stop Distance Optimization:**
- Focus on 1-3 PM + 0.55-1.0% stops: **75-80% WR** (+15-20% improvement)

---

## ⚙️ SETTINGS

### User Inputs:
- **EMA Lengths:** All adjustable (10, 15, 20, 35)
- **SMA Lengths:** All adjustable (33, 50, 100, 200)
- **Show Bullish/Bearish Markers:** Toggle signal arrows
- **Show Time Backgrounds:** Toggle time-based color coding
- **Chop Filter %:** Threshold for 15/35 separation (default 0.06)
- **RSI Length:** Default 14

---

## 🚀 INSTALLATION

1. Open TradingView
2. Open Pine Editor (bottom panel)
3. Click "New" or "Open"
4. Paste the indicator code
5. Click "Add to Chart"
6. Configure settings as desired

---

## 📊 RISK MANAGEMENT

### Position Sizing:
- **Risk:** 1% of account per trade
- **Target shares:** 400-500 (optimal for typical price range)
- **Dynamic sizing** based on stop distance

### Stop Loss Rules:
- **Primary:** Signal candle low/high
- **Fallback:** 35 EMA
- **Distance:** Target 0.55-1.0% from entry

### Profit Targets:
- **Maximum:** 1.2R
- **No overnight holds**

---

## 📝 R-SCALING SYSTEM (MONTHLY)

Based on 59.5% WR and expected monthly performance:

### Monthly Protocol:
- **Start:** 1.0% risk per trade
- **Scale UP:** When cumulative monthly R reaches +10R
- **Scale DOWN:** When cumulative monthly R drops to +5R (while at 1.5%)
- **Reset:** Start every month at 1.0%

### Expected Impact:
- Month at 1.0%: ~23R
- With scaling: ~26R (+15-20% profit boost)

---

## 🎓 PATTERN: CANDLE PAUSE METHOD

### Setup Requirements:
1. Signal arrow appears (green/red from indicator)
2. Price pauses near 10 EMA (2-5 candles ideal)
3. Pause shows: small bodies, low volume, tight range
4. Entry: Breakout from pause range
5. Stop: Signal candle or 35 EMA (0.55-1.0% away)

### Invalidation:
- Price crosses 10 EMA opposite direction
- Breakout fails (returns to pause range)
- Volume spike during pause (no consolidation)
- Stop distance outside 0.55-1.0% range

---

## 📊 BACKTEST INSIGHTS

### Trade Sequence Analysis:
- **Trade #1 of day:** 67.0% WR
- **Trade #2 of day:** 49.4% WR overall, BUT 60.0% WR in good times
- **Problem:** 70% of Trade #2s occurred in 10am-1pm danger zone

### Consecutive Losses:
- **Maximum streak:** 4 losses
- **Average loss streak:** 1.4
- **Loss streaks of 2+:** 24 occurrences
- **Loss streaks of 3+:** 7 occurrences

---

## 🔧 ALERTS

The indicator includes alert conditions for:
- Bullish signal (green candle crosses below 10 EMA)
- Bearish signal (red candle crosses above 10 EMA)
- Price crosses 10 EMA (any direction)

---

## 📌 NOTES

- Indicator is designed for **TSLA on 3-minute charts**
- All times are in **Central Time (CST)**
- Market opens: 8:30 AM CST (9:30 AM EST)
- Market closes: 3:00 PM CST (4:00 PM EST)
- Backtest period: Nov 2024 - Mar 2025 (94 trading days)

---

## ⚠️ DISCLAIMER

This indicator is for educational purposes only. Past performance does not guarantee future results. Always practice proper risk management and never risk more than you can afford to lose.

---

## 📈 VERSION HISTORY

**v2.0** (Current)
- Updated time backgrounds based on 257-trade backtest analysis
- Corrected time zones for market hours (8:30 AM CST open)
- Optimized for 1-3 PM CST golden window (76% WR)
- Added danger zone highlighting for 10 AM-1 PM CST (47% WR)

**v1.0**
- Initial release with basic EMA clouds and signals
