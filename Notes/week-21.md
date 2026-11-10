# WEEK 21: BACKTESTING YOUR TRADING SYSTEM

## Phase 4 — Strategy Development and Backtesting (Week 3 of 4)

---

## TABLE OF CONTENTS

1. What is Backtesting and Why It's Non-Negotiable
2. The Statistical Foundation
3. Types of Backtesting
4. Step-by-Step Manual Backtesting Process
5. Backtesting Options Strategies Specifically
6. Key Performance Metrics (with Formulas & Examples)
7. Backtest Spreadsheet Design
8. Interpreting Your Results
9. Common Pitfalls (Overfitting, Biases, Errors)
10. In-Sample vs Out-of-Sample Testing
11. Walk-Forward Analysis (Simplified)
12. When to Trust Your Backtest
13. Practical Exercise
14. Self-Test with Answers

---

## 1. WHAT IS BACKTESTING AND WHY IT'S NON-NEGOTIABLE

### Definition

**Backtesting** is the process of applying your trading system's rules to **historical market data** to determine how the system *would have performed* in the past.

Think of it like a **crash test for your car** before you drive it on a highway with your family inside.

```
WITHOUT BACKTESTING:
┌─────────────────────────────────────────┐
│  "I think this strategy works"          │
│       ↓                                 │
│  Trade with real money                  │
│       ↓                                 │
│  Lose ₹50,000 in 2 weeks                │
│       ↓                                 │
│  "Maybe the strategy doesn't work?"     │
│       ↓                                 │
│  Quit trading / Blow up account         │
└─────────────────────────────────────────┘

WITH BACKTESTING:
┌─────────────────────────────────────────┐
│  "I think this strategy works"          │
│       ↓                                 │
│  Test on 100 historical trades          │
│       ↓                                 │
│  Discover it loses in high VIX          │
│       ↓                                 │
│  Add VIX filter → Retest                │
│       ↓                                 │
│  Now profitable → Paper trade → Live    │
└─────────────────────────────────────────┘
```

### Why You Cannot Skip This Step

| Reason | Explanation |
|--------|-------------|
| **Proof of concept** | Your system might *sound* logical but lose money in practice. Backtesting reveals this before you risk real capital. |
| **Builds conviction** | When you hit a 5-trade losing streak live (and you WILL), backtest data tells you "this happened in the test too, and the system recovered." Without this, you'll abandon a good system. |
| **Reveals weaknesses** | You'll discover your system fails on Fridays, or during RBI policy days, or in the first 30 minutes. Fix these BEFORE going live. |
| **Sets realistic expectations** | If your backtest shows 55% win rate with 1:2 R:R, you won't panic when you lose 4 out of 7 trades in a week. |
| **Quantifies edge** | "I feel like I'm profitable" is not an edge. "My expectancy is +₹1,850 per trade over 120 trades" IS an edge. |

### The SEBI Reality Check

Remember the SEBI study: **91% of F&O traders lose money.** Most of these traders never backtested. They jumped straight from YouTube videos to live trading. Backtesting is one of the key differentiators between the 9% who survive and the 91% who don't.

---

## 2. THE STATISTICAL FOUNDATION

### The 100-Trade Minimum Rule

Why 100 trades? Because of the **Law of Large Numbers**.

```
SAMPLE SIZE vs RELIABILITY:

  5 trades:   █████░░░░░░░░░░░░░░░  25% reliable  (pure luck)
 10 trades:   ████████░░░░░░░░░░░░  40% reliable  (still noisy)
 20 trades:   ██████████░░░░░░░░░░  55% reliable  (getting better)
 50 trades:   ██████████████░░░░░░  70% reliable  (decent signal)
100 trades:   ██████████████████░░  85% reliable  (statistically meaningful)
200 trades:   ████████████████████  95% reliable  (high confidence)
```

**Example of why small samples lie:**

Imagine a coin that is actually fair (50% heads).

| Flips | Heads | Observed % | Conclusion |
|-------|-------|-----------|------------|
| 4 | 3 | 75% | "This coin is biased toward heads!" ❌ |
| 10 | 7 | 70% | "Still seems biased" ❌ |
| 50 | 28 | 56% | "Getting closer to 50%" ⚠️ |
| 100 | 52 | 52% | "Fair coin" ✅ |
| 1000 | 498 | 49.8% | "Definitely fair" ✅ |

**Your trading system is the same.** A 5-trade winning streak doesn't prove your system works. A 5-trade losing streak doesn't prove it's broken. You need **at least 100 trades** to get a reliable picture.

### Statistical Significance (Simplified)

You don't need a statistics degree. Just remember:

- **< 30 trades**: Results are **meaningless**. Do not draw conclusions.
- **30–99 trades**: Results are **suggestive** but not conclusive. Keep testing.
- **100–199 trades**: Results are **reliable** for general conclusions.
- **200+ trades**: Results are **highly reliable**. You can trust the metrics.

### The Edge Equation

Your system has a statistical edge if:

```
Expectancy = (Win% × Avg Win) – (Loss% × Avg Loss) > 0

Example:
Win Rate = 55%
Avg Win = ₹5,000
Avg Loss = ₹3,000

Expectancy = (0.55 × 5,000) – (0.45 × 3,000)
           = 2,750 – 1,350
           = +₹1,400 per trade ✅

Over 100 trades: Expected profit = ₹1,40,000
Over 200 trades: Expected profit = ₹2,80,000
```

**If expectancy is negative after 100+ trades, your system is broken. Do NOT trade it live.**

---

## 3. TYPES OF BACKTESTING

### A. Manual Backtesting (What You'll Do)

You manually scroll through historical charts, identify setups according to your rules, and record hypothetical trades.

| Pros | Cons |
|------|------|
| Deep understanding of every trade | Time-consuming (20–40 hours for 100 trades) |
| You see the context (news, events) | Human bias can creep in |
| Free (TradingView Bar Replay) | Limited to what you can scroll through |
| Best for learning | Hard to test complex multi-leg options |

### B. Automated/Algorithmic Backtesting

A computer program tests your rules across thousands of trades in seconds.

| Pros | Cons |
|------|------|
| Fast (1000 trades in minutes) | Requires coding (Python, Amibroker) |
| No human bias | Easy to overfit |
| Can test many variations | Expensive data for options |
| Statistical rigor | Doesn't capture "feel" of market |

**For your current stage: Manual backtesting is superior** because:
1. You're still learning — you need to *see* each trade
2. Options backtesting is hard to automate accurately in India
3. You'll develop pattern recognition by reviewing 100+ charts
4. Free tools are sufficient

### C. Forward Testing / Paper Trading (Week 22 Preview)

Applying your rules to **live, real-time data** without real money. This is the bridge between backtesting and live trading.

```
BACKTESTING TIMELINE:

Past Data          Present          Future
  │                  │               │
  ├── BACKTEST ──┤   ├── PAPER ──┤   ├── LIVE ──┤
  │  (100 trades) │   │ (50 trades) │   │ (real ₹)  │
  │  Historical   │   │ Real-time   │   │ Real-time │
  │  Known outcome│   │ Unknown     │   │ Unknown   │
```

---

## 4. STEP-BY-STEP MANUAL BACKTESTING PROCESS

### Step 1: Define Your System Rules PRECISELY (No Ambiguity)

Before you open any chart, your rules must be so specific that a 10-year-old could follow them. Vague rules produce unreliable backtests.

**BAD (Vague):**
> "Buy call when market looks bullish near support."

**GOOD (Precise):**
> **Entry:** Buy NIFTY ATM Call (nearest weekly expiry) when ALL conditions met:
> 1. Daily chart: NIFTY above 20 EMA
> 2. 15-min chart: Price makes Higher High after Higher Low (BOS confirmed)
> 3. 5-min chart: Bullish engulfing candle closes above VWAP
> 4. RSI(14) on 15-min: Between 45 and 65 (not overbought)
> 5. Option chain: PCR > 1.0 AND Put OI at nearest 100 strike increasing
> 6. India VIX < 20
> 7. Time: Between 9:45 AM and 1:30 PM
> 8. Not within 2 days of RBI policy / Budget / Election results
>
> **Stop Loss:** 30% of premium paid OR 15-min candle close below VWAP (whichever hits first)
>
> **Target:** 60% of premium paid OR 1:2 R:R (whichever hits first)
>
> **Position Size:** 1 lot per ₹1,00,000 capital

### Step 2: Choose Your Data Period

| Parameter | Recommendation |
|-----------|---------------|
| **Duration** | 6–12 months of historical data |
| **Market conditions** | Include at least 1 trending period + 1 range-bound period + 1 volatile period |
| **Expiry types** | Include both weekly and monthly expiries |
| **Events** | Include at least 2–3 major events (RBI, Budget, global crash) |
| **Avoid** | Only cherry-picking "good" months |

**Ideal 6-month period for NIFTY (example):**
```
Jan–Jun 2024:
  Jan: Range-bound, low VIX (12–14)        ← Tests range strategies
  Feb: Interim Budget volatility (VIX 21)  ← Tests event handling
  Mar: Trending up, moderate VIX (13–16)   ← Tests trend strategies
  Apr: Range + elections buildup (VIX 18)  ← Tests mixed conditions
  May: Election results crash/rally (VIX 25→14) ← Tests extreme vol
  Jun: Post-election trend (VIX 12–15)     ← Tests recovery
```

This gives you **diverse conditions** — the key to a robust backtest.

### Step 3: Set Up TradingView Bar Replay

**Detailed setup instructions:**

1. Open [tradingview.com](https://tradingview.com) → Chart
2. Symbol: `NSE:NIFTY` (spot index, NOT futures)
3. Timeframe: Start with **15-minute** chart
4. Add indicators:
   - 20 EMA (close)
   - VWAP (session)
   - RSI (14, close)
   - Volume
5. Click **Replay** button (bottom toolbar, looks like a play button with a bar)
6. Set replay start date (e.g., January 2, 2024)
7. Set speed: **1 bar per click** (manual mode — DO NOT use auto-play)
8. You'll see the chart with all future data hidden

```
TRADINGVIEW BAR REPLAY SETUP:

┌─────────────────────────────────────────────────┐
│  NSE:NIFTY  15min  │ 20EMA  VWAP  RSI  Vol    │
│─────────────────────────────────────────────────│
│                                                 │
│     ╱╲    ╱╲╱╲                                 │
│   ╱    ╲╱        ╲    ← Chart visible up to    │
│  ╱               ╲      replay cutoff date      │
│ ╱                 ╲                             │
│─────────────────────││││││││││││││││││││││││││││
│                     ↑                           │
│              REPLAY CUTOFF                      │
│         (Future data is HIDDEN)                 │
│                                                 │
│  [◄◄] [◄] [PLAY] [►] [►►]  Speed: 1 bar/click │
└─────────────────────────────────────────────────┘
```

**Free plan limitation:** TradingView free allows Bar Replay on daily, weekly, and monthly timeframes. For intraday (5-min, 15-min), you need the **Essential plan** (~₹495/month).

**Free alternative:** Use **daily timeframe** on free plan for positional strategy backtesting, or use **Neostox** (neostox.com) which offers free historical replay for Indian markets including intraday.

### Step 4: Execute Each Trade Systematically

For each bar (candle) that appears:

1. **Check ALL entry conditions** from your rules
2. If ALL conditions met → **Record the trade** (do NOT skip)
3. If ANY condition NOT met → **Do NOT trade** (even if the move looks tempting)
4. Advance to next bar
5. Check if SL or Target hit
6. Record the exit

**CRITICAL RULE: You must follow your rules EXACTLY as written.**

```
THE DISCIPLINE TEST:

Bar 47: All 8 conditions met → ENTER ✅
Bar 48: Price drops → SL hit → EXIT at loss ✅
Bar 52: 7 of 8 conditions met (VIX too high) → NO TRADE ✅
         (Even though NIFTY rallied 200 pts after this)
Bar 61: All 8 conditions met → ENTER ✅
Bar 63: Target hit → EXIT at profit ✅

❌ WRONG: "Bar 52 looked so good, I would have entered"
   → This is HINDSIGHT BIAS and destroys your backtest
```

### Step 5: Record Every Trade in Your Spreadsheet

For each trade, record AT MINIMUM:

| # | Data Point | Example |
|---|-----------|---------|
| 1 | Date | 15-Mar-2024 |
| 2 | Day of week | Friday |
| 3 | Time of entry | 10:15 AM |
| 4 | NIFTY spot at entry | 22,150 |
| 5 | Strategy used | Bull Call Spread |
| 6 | Strike(s) | 22100 CE Long / 22300 CE Short |
| 7 | Expiry date | 21-Mar-2024 |
| 8 | Entry premium (net) | ₹85 |
| 9 | Confluence score | 11/13 (A+) |
| 10 | VIX at entry | 14.2 |
| 11 | PCR at entry | 1.15 |
| 12 | Exit time | 1:45 PM |
| 13 | NIFTY spot at exit | 22,280 |
| 14 | Exit premium (net) | ₹135 |
| 15 | P&L per lot | +₹3,750 |
| 16 | Exit reason | Target hit (60% profit) |
| 17 | Max adverse excursion | -₹1,200 (max unrealized loss during trade) |
| 18 | Max favorable excursion | +₹4,100 (max unrealized profit during trade) |
| 19 | Notes | Clean BOS on 15-min, strong Put OI at 22100 |

### Step 6: Calculate Metrics After 100 Trades

Do NOT calculate metrics after 10, 20, or 50 trades. Wait until you have at least 100 complete trades. (Detailed metrics in Section 6.)

---

## 5. BACKTESTING OPTIONS STRATEGIES SPECIFICALLY

### The Options Backtesting Challenge

Backtesting stocks or futures is straightforward: buy at X, sell at Y, profit = Y – X.

**Options are fundamentally different** because:

```
WHY OPTIONS BACKTESTING IS HARDER:

1. DECAY: An option bought on Monday at ₹100 might be worth ₹70
   on Wednesday even if NIFTY hasn't moved (theta decay)

2. IV CHANGES: Same option can be ₹100 at IV=15% and ₹140 at
   IV=20% even with same spot price and same time to expiry

3. EXPIRY: Options cease to exist. You can't hold a 15-Feb CE
   and test it in March. Each week has different contracts.

4. GREEKS ARE DYNAMIC: Delta, gamma, theta, vega all change
   every minute as spot, time, and IV change

5. LIQUIDITY VARIES: Deep OTM options may have shown a "price"
   on the chart but you couldn't actually trade at that price

6. SPREADS: Bid-ask spread on options can be ₹5–20, eating
   into your theoretical backtest profits
```

### Method 1: Underlying + Delta Approximation (Best for Beginners)

**Concept:** Instead of tracking actual option premiums historically (which is hard to get), you track NIFTY spot moves and estimate option P&L using delta.

**Formula:**
```
Estimated Option P&L ≈ Delta × Change in NIFTY × Lot Size – Theta Decay

Example:
  Entry: NIFTY 22,000, ATM CE (Delta 0.50), Premium ₹150
  Move: NIFTY goes to 22,120 (+120 pts) in 4 hours
  Theta: ~₹8 per hour × 4 = ₹32 decay

  Estimated P&L per lot = (0.50 × 120 × 75) – (32 × 75)
                        = 4,500 – 2,400
                        = +₹2,100

  Actual P&L might be ₹1,800–2,400 (approximation has ~15–20% error)
```

**When to use:** For directional strategies (Bull Call Spread, Bear Put Spread) where delta is the primary driver.

**Limitations:** Doesn't capture gamma acceleration or vega changes accurately. Error increases for longer holding periods.

### Method 2: Sensibull Virtual Trade with Historical Data

**Steps:**
1. Go to [sensibull.com](https://sensibull.com) → Virtual Trade
2. Select a historical date
3. Build your strategy (e.g., Bull Call Spread)
4. Sensibull shows you the historical premiums and Greeks
5. Advance day by day and track P&L
6. Record results

**Advantage:** Uses actual historical option premiums (more accurate than delta approximation).

**Limitation:** Sensibull's free plan has limited historical data. Pro plan (~₹800/month) gives more.

### Method 3: Opstra Strategy Backtest

**Steps:**
1. Go to [opstra.definedge.com](https://opstra.definedge.com) → Strategy Builder
2. Build your multi-leg strategy
3. Select historical date range
4. Opstra calculates theoretical P&L using historical IV and spot
5. Shows equity curve, max drawdown, win rate

**Advantage:** Best for multi-leg strategies (Iron Condor, Calendar Spread). Shows Greeks evolution.

**Limitation:** Free plan limited. Uses theoretical pricing (Black-Scholes), not actual traded premiums.

### Method 4: Simplified Premium Tracking (Most Practical for Manual Backtest)

**This is what I recommend for your 100-trade backtest:**

1. Use TradingView Bar Replay on NIFTY 15-min chart
2. When your entry conditions trigger, note the NIFTY spot price
3. Open NSE option chain for that date (available on Sensibull historical or Opstra)
4. Note the actual ATM option premium at that time
5. Advance the replay to your exit condition
6. Note the exit premium
7. Calculate actual P&L

```
PRACTICAL WORKFLOW:

  TradingView Replay          NSE/Sensibull Historical
  ┌──────────────┐            ┌──────────────────────┐
  │ NIFTY 15-min │            │ Option Chain         │
  │              │            │ Date: 15-Mar-2024    │
  │ Entry signal │───────────→│ 22100 CE: ₹152       │
  │ at 22,100    │            │ 22100 PE: ₹98        │
  │ 10:15 AM     │            │ IV: 14.5%            │
  │              │            │                      │
  │ Exit signal  │───────────→│ 22100 CE: ₹210       │
  │ at 22,230    │            │ 22100 PE: ₹55        │
  │ 1:30 PM      │            │ IV: 13.8%            │
  └──────────────┘            └──────────────────────┘

  P&L = (210 – 152) × 75 = +₹4,350 per lot
```

**Time estimate:** ~15–20 minutes per trade × 100 trades = **25–33 hours total.** Spread this over 2–3 weeks.

---

## 6. KEY PERFORMANCE METRICS (with Formulas & Examples)

After completing 100+ trades, calculate these 8 metrics:

### Metric 1: Win Rate

```
Win Rate = (Number of Winning Trades / Total Trades) × 100

Example: 58 wins out of 100 trades
Win Rate = (58 / 100) × 100 = 58%

BENCHMARKS:
  Directional strategies (spreads):  50–60% is good
  Credit strategies (condors):       65–75% is good
  Straddles/strangles:               35–45% is normal
  ANY strategy:                      < 40% is concerning (unless R:R is very high)
```

**Important:** Win rate ALONE is meaningless. A 90% win rate system that wins ₹500 nine times and loses ₹10,000 once is a LOSING system.

### Metric 2: Average Win and Average Loss

```
Average Win = Total Profit from Winning Trades / Number of Winning Trades
Average Loss = Total Loss from Losing Trades / Number of Losing Trades

Example (100 trades):
  58 winning trades, total profit = ₹3,48,000
  42 losing trades, total loss = ₹1,68,000

  Average Win = 3,48,000 / 58 = ₹6,000
  Average Loss = 1,68,000 / 42 = ₹4,000
```

### Metric 3: Risk:Reward Ratio (R:R)

```
R:R = Average Win / Average Loss

Example: ₹6,000 / ₹4,000 = 1.5:1

BENCHMARKS:
  < 1.0:1   → You need very high win rate (>65%) to survive
  1.0:1     → You need >55% win rate
  1.5:1     → You need >45% win rate ← SWEET SPOT for beginners
  2.0:1     → You need >38% win rate
  3.0:1+    → You can survive with 30% win rate (trend following)
```

### Metric 4: Expectancy (THE MOST IMPORTANT METRIC)

```
Expectancy = (Win% × Avg Win) – (Loss% × Avg Loss)

Example:
  Win Rate = 58%
  Avg Win = ₹6,000
  Avg Loss = ₹4,000

  Expectancy = (0.58 × 6,000) – (0.42 × 4,000)
             = 3,480 – 1,680
             = +₹1,800 per trade ✅

  Interpretation: On average, you earn ₹1,800 for every trade you take.
  Over 100 trades: Expected profit = ₹1,80,000
  Over 200 trades: Expected profit = ₹3,60,000

BENCHMARKS:
  Negative → System is broken. DO NOT TRADE.
  ₹0–500   → Marginal. Transaction costs may eat profits.
  ₹500–1,500 → Decent for beginner.
  ₹1,500–3,000 → Good.
  ₹3,000+  → Excellent (verify for overfitting).
```

### Metric 5: Profit Factor

```
Profit Factor = Total Gross Profit / Total Gross Loss

Example:
  Total Profit = ₹3,48,000
  Total Loss = ₹1,68,000

  Profit Factor = 3,48,000 / 1,68,000 = 2.07

BENCHMARKS:
  < 1.0  → Losing system
  1.0–1.5 → Marginal
  1.5–2.0 → Good
  2.0–3.0 → Very Good
  > 3.0  → Suspiciously good (check for overfitting!)
```

### Metric 6: Maximum Drawdown (MDD)

**Maximum Drawdown** is the largest peak-to-trough decline in your equity curve. It tells you the **worst pain** you'll endure.

```
EQUITY CURVE WITH DRAWDOWN:

₹3,00,000 │          ╱╲
          │        ╱    ╲        ╱╲
₹2,50,000 │      ╱        ╲    ╱    ╲╱╲
          │    ╱            ╲╱          ╲╱
₹2,00,000 │  ╱        ← MDD = ₹60,000
          │╱            (Peak ₹2,60,000 → Trough ₹2,00,000)
₹1,50,000 │
          │
₹1,00,000 │ ← Starting Capital
          └──────────────────────────────────────
           Trade 1    25    50    75    100

MDD = (Peak – Trough) / Peak × 100
    = (2,60,000 – 2,00,000) / 2,60,000 × 100
    = 23.1%

BENCHMARKS:
  < 10%  → Excellent (rare for options)
  10–20% → Good
  20–30% → Acceptable for options strategies
  30–40% → High risk (can you emotionally handle this?)
  > 40%  → Too risky. Reduce position size.
```

**Why MDD matters more than total profit:**

```
System A: +₹2,00,000 profit, MDD = 15%  → You'd stick with it ✅
System B: +₹3,00,000 profit, MDD = 45%  → You'd quit during the drawdown ❌
```

### Metric 7: Sharpe Ratio (Simplified)

Measures **risk-adjusted return**. How much return are you getting per unit of risk?

```
Sharpe Ratio = (Average Return – Risk-Free Rate) / Standard Deviation of Returns

Simplified for trading:
Sharpe ≈ (Expectancy per trade) / (Standard Deviation of trade P&L)

Example:
  Expectancy = ₹1,800
  Std Dev of P&L = ₹4,500

  Sharpe = 1,800 / 4,500 = 0.40

BENCHMARKS:
  < 0.5  → Poor risk-adjusted return
  0.5–1.0 → Acceptable
  1.0–2.0 → Good
  > 2.0  → Excellent (verify data quality)
```

### Metric 8: Recovery Factor

```
Recovery Factor = Net Profit / Maximum Drawdown

Example:
  Net Profit = ₹1,80,000
  MDD = ₹60,000

  Recovery Factor = 1,80,000 / 60,000 = 3.0

BENCHMARKS:
  > 3.0 → Good (system recovers well from drawdowns)
  1.5–3.0 → Acceptable
  < 1.5 → System struggles to recover
```

### Complete Metrics Summary Table

| Metric | Formula | Your Example | Good Benchmark |
|--------|---------|-------------|----------------|
| Win Rate | Wins / Total | 58% | 50–65% |
| Avg Win | Total Profit / Wins | ₹6,000 | > Avg Loss |
| Avg Loss | Total Loss / Losses | ₹4,000 | < Avg Win |
| R:R | Avg Win / Avg Loss | 1.5:1 | > 1.2:1 |
| Expectancy | (W%×AvgW) – (L%×AvgL) | +₹1,800 | > ₹1,000 |
| Profit Factor | Gross Profit / Gross Loss | 2.07 | > 1.5 |
| Max Drawdown | Peak-to-Trough decline | 23.1% | < 25% |
| Sharpe Ratio | Expectancy / StdDev | 0.40 | > 0.5 |
| Recovery Factor | Net Profit / MDD | 3.0 | > 2.0 |

---

## 7. BACKTEST SPREADSHEET DESIGN

### Recommended Structure (Google Sheets)

**Sheet 1: Trade Log**

| A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| # | Date | Day | Time In | Spot In | Strategy | Strikes | Expiry | Prem In | Score | VIX | PCR | Time Out | Spot Out | Prem Out | P&L/Lot | Exit Reason | Notes |
| 1 | 3-Jan | Wed | 10:15 | 21,750 | BCS | 21700/21900 | 4-Jan | 82 | 11 | 13.5 | 1.1 | 14:00 | 21,870 | 128 | +3,450 | Target | Clean BOS |
| 2 | 4-Jan | Thu | 11:00 | 21,820 | BPS | 21800/21600 | 11-Jan | 45 | 10 | 14.1 | 1.2 | 15:00 | 21,780 | 22 | +1,725 | Target | PCR rising |
| 3 | 5-Jan | Fri | 09:50 | 21,700 | BCS | 21700/21850 | 11-Jan | 65 | 9 | 15.2 | 0.9 | 10:30 | 21,620 | 30 | -2,625 | SL | VIX spike |

**Sheet 2: Summary Dashboard**

```
┌─────────────────────────────────────────────────┐
│          BACKTEST SUMMARY DASHBOARD             │
├─────────────────────────────────────────────────┤
│  Total Trades:        100                       │
│  Winning Trades:       58  (58.0%)              │
│  Losing Trades:        42  (42.0%)              │
│                                                 │
│  Total Gross Profit:  ₹3,48,000                 │
│  Total Gross Loss:   -₹1,68,000                 │
│  Net Profit:          ₹1,80,000                 │
│                                                 │
│  Average Win:         ₹6,000                    │
│  Average Loss:       -₹4,000                    │
│  R:R Ratio:           1.50                      │
│  Expectancy:         +₹1,800                    │
│  Profit Factor:       2.07                      │
│                                                 │
│  Max Drawdown:       -₹60,000 (23.1%)           │
│  Sharpe Ratio:        0.40                      │
│  Recovery Factor:     3.00                      │
│                                                 │
│  Best Trade:         +₹12,500                   │
│  Worst Trade:        -₹8,200                    │
│  Avg Holding Time:    3.2 hours                  │
│  Best Day:            Tuesday (65% WR)           │
│  Worst Day:           Friday (48% WR)            │
│  Best VIX Range:      12–16 (62% WR)            │
│  Worst VIX Range:     >20 (41% WR)              │
└─────────────────────────────────────────────────┘
```

**Sheet 3: Equity Curve**

Plot cumulative P&L against trade number. This is your most important visual.

```
CUMULATIVE P&L (Equity Curve):

₹2,00,000 │                                    ╱
          │                              ╱╲  ╱
₹1,50,000 │                         ╱╲ ╱    ╲╱
          │                    ╱╲ ╱    ╲
₹1,00,000 │               ╱╲ ╱    ╲
          │          ╱╲ ╱    ╲
 ₹50,000  │     ╱╲ ╱    ╲
          │ ╱╲ ╱    ╲
      ₹0  │╱    ╲
          └──┬───┬───┬───┬───┬───┬───┬───┬───┬──
             10  20  30  40  50  60  70  80  90 100
                        Trade Number

  KEY OBSERVATIONS:
  ✓ Overall upward trend (system is profitable)
  ✓ Drawdowns are shallow and recover quickly
  ✓ No "hockey stick" (which would indicate overfitting)
  ✓ Steady growth (not explosive, which is more realistic)
```

**Sheet 4: Monthly Breakdown**

| Month | Trades | Wins | Win% | Net P&L | Max DD | Notes |
|-------|--------|------|------|---------|--------|-------|
| Jan | 18 | 11 | 61% | +₹32,000 | -₹8,000 | Range market |
| Feb | 15 | 7 | 47% | -₹5,000 | -₹18,000 | Budget volatility |
| Mar | 20 | 13 | 65% | +₹48,000 | -₹6,000 | Strong trend |
| Apr | 16 | 9 | 56% | +₹22,000 | -₹12,000 | Mixed |
| May | 17 | 10 | 59% | +₹45,000 | -₹15,000 | Election vol |
| Jun | 14 | 8 | 57% | +₹38,000 | -₹5,000 | Post-election |

---

## 8. INTERPRETING YOUR RESULTS

### What "Good" Looks Like

```
✅ HEALTHY BACKTEST PROFILE:

  Win Rate:        50–60% (for directional)
  R:R:             1.3–2.0
  Expectancy:      Positive and > ₹1,000/trade
  Profit Factor:   1.5–2.5
  Max Drawdown:    15–25% of capital
  Equity Curve:    Steady upward with small dips
  Monthly:         4 profitable out of 6 months
  Best Month:      Not more than 3× average month
  Worst Month:     Small loss, not catastrophic
```

### Red Flags (DO NOT TRADE LIVE IF YOU SEE THESE)

```
🚩 RED FLAG 1: Win rate > 80% with high R:R
   → Almost certainly overfitted. Real markets don't give you
     80% wins AND 2:1 R:R consistently.

🚩 RED FLAG 2: Profit Factor > 3.5
   → Suspiciously good. Check for look-ahead bias or
     cherry-picked data.

🚩 RED FLAG 3: Equity curve is a straight line up
   → Real trading has drawdowns. A perfect line means you
     likely fitted your rules to the data.

🚩 RED FLAG 4: All profits come from 2–3 huge trades
   → Remove those trades. Is the system still profitable?
     If not, your edge is fragile.

🚩 RED FLAG 5: System only works in one market condition
   → E.g., only profitable in trending markets. What happens
     when the market goes range-bound for 2 months?

🚩 RED FLAG 6: Negative expectancy in 2+ consecutive months
   → The system may not be robust across conditions.

🚩 RED FLAG 7: Max drawdown > 35%
   → You will likely abandon the system psychologically
     before it recovers.
```

### The "Remove Best Trades" Test

This is a powerful robustness check:

```
Step 1: Calculate expectancy with all 100 trades = +₹1,800
Step 2: Remove your 5 best trades
Step 3: Recalculate expectancy = +₹1,200
Step 4: Remove your 5 worst trades
Step 5: Recalculate expectancy = +₹1,500

INTERPRETATION:
  If expectancy stays positive after removing best 5 trades
  → Your edge is ROBUST ✅

  If expectancy turns negative after removing best 5 trades
  → Your edge depends on a few lucky trades → FRAGILE ❌
```

### The "Worst Month" Test

```
Look at your worst month in the backtest.
  Can you emotionally survive that month with real money?

  Worst month: -₹18,000 on ₹2,00,000 capital = -9%
  → Can you handle losing ₹18,000 in a month? If yes, proceed.
  → If that would make you panic and break rules, reduce size.
```

---

## 9. COMMON PITFALLS

### Pitfall 1: Overfitting (Curve Fitting) — THE #1 KILLER

**Definition:** Tweaking your rules so much that they perfectly match historical data but fail on new, unseen data.

```
OVERFITTING EXAMPLE:

Original Rule: "Buy when RSI < 30"
  Backtest: 52% win rate (decent)

Tweaked Rule: "Buy when RSI < 28.5 AND day is Tuesday
              AND VIX between 13.2 and 15.7 AND
              moon is waxing"
  Backtest: 78% win rate (amazing!)

Reality: 41% win rate on new data (terrible!)

WHY? You fitted the rules to NOISE in the historical data,
not to a genuine market pattern.
```

**How to detect overfitting:**
1. Too many conditions (>8–10 filters)
2. Very specific parameter values (RSI < 28.5 instead of RSI < 30)
3. System works perfectly on one time period but fails on another
4. Profit factor > 3.0
5. Equity curve is suspiciously smooth

**How to avoid overfitting:**
1. Keep rules SIMPLE (3–5 core conditions)
2. Use round numbers (RSI 30, not 28.5)
3. Test on OUT-OF-SAMPLE data (see Section 10)
4. If a rule doesn't have a LOGICAL market reason, remove it
5. Fewer parameters = more robust system

### Pitfall 2: Look-Ahead Bias

**Definition:** Using information in your backtest that you wouldn't have had at the time of the trade.

```
EXAMPLES OF LOOK-AHEAD BIAS:

❌ "I entered at 10:00 AM because I saw the 3:00 PM close
    would be 200 pts higher"
    → At 10:00 AM, you don't know the 3:00 PM close!

❌ "I avoided trading on Feb 1 because I knew Budget would
    crash the market"
    → In real-time, you might have had a signal on Feb 1.
    → Your backtest should show that loss.

❌ Using end-of-day data to make intraday entry decisions
    → The entry signal must be visible at the time of entry.
```

**How to avoid:**
- Use Bar Replay mode (future data is hidden)
- Make decisions based ONLY on data available at that moment
- Include ALL trades your system generates, even on "bad" days

### Pitfall 3: Survivorship Bias

**Definition:** Only testing on instruments/periods that "survived" or performed well.

```
EXAMPLES:

❌ Testing only on NIFTY from 2020–2024 (a massive bull run)
    → Your long-biased system looks amazing
    → But it would have been destroyed in 2008 or 2022

❌ Testing only on liquid options (ATM strikes)
    → OTM options you'd actually trade may have wider spreads
    → Your backtest overestimates profits
```

**How to avoid:**
- Include bear markets and crashes in your test period
- Include low-liquidity periods (holidays, summer)
- Test across different VIX regimes

### Pitfall 4: Ignoring Transaction Costs

```
BACKTEST WITHOUT COSTS:
  Gross Profit: ₹2,00,000
  "Wow, I'm rich!"

REALITY WITH COSTS (100 trades × 2 legs × 2 sides):
  Brokerage:  100 × 4 × ₹20 = ₹8,000
  STT:        ~₹6,000
  Exchange:   ~₹4,000
  GST:        ~₹2,500
  Stamp:      ~₹1,500
  SEBI:       ~₹200
  Slippage:   ~₹10,000 (estimated ₹1–2 per trade per leg)
  ─────────────────────────
  Total Costs: ~₹32,200

  Net Profit: ₹2,00,000 – ₹32,200 = ₹1,67,800
  → 16% reduction from gross!

RULE: Always deduct ₹300–500 per round-trip trade (all legs)
      from your backtest P&L.
```

### Pitfall 5: Ignoring Slippage

**Slippage** = Difference between the price you see and the price you actually get.

```
Backtest says: Buy CE at ₹150.00
Reality:       Buy CE at ₹152.50 (market moved while you clicked)
Slippage:      ₹2.50 × 75 = ₹187.50 per lot per leg

For a 2-leg spread, round-trip:
  Slippage ≈ ₹187.50 × 4 = ₹750 per trade

Over 100 trades: ₹75,000 in slippage alone!
```

**How to account:** Deduct ₹500–1,000 per trade from backtest P&L for realistic results.

### Pitfall 6: Small Sample Size

Already covered in Section 2, but worth repeating:

```
❌ "I backtested 15 trades and won 12. My system is amazing!"
   → 80% win rate on 15 trades is statistically meaningless.
   → Flip a coin 15 times; you might get 12 heads by luck.

✅ "I backtested 120 trades across 8 months with 58% win rate."
   → This is statistically meaningful.
```

### Pitfall 7: Confirmation Bias

```
❌ "I know this strategy works, so I'll only record the trades
    where it worked and skip the ambiguous ones."

✅ Record EVERY trade your rules generate. No exceptions.
   If you're unsure whether a setup qualifies, it DOESN'T.
   Be stricter in backtesting than you would be live.
```

---

## 10. IN-SAMPLE vs OUT-OF-SAMPLE TESTING

This is the **most important technique** to prevent overfitting.

### Concept

```
YOUR HISTORICAL DATA (12 months):

  Jan   Feb   Mar   Apr   May   Jun   Jul   Aug   Sep   Oct   Nov   Dec
  ├─────────────────────────────┤├─────────────────────────────────────┤
       IN-SAMPLE (6 months)              OUT-OF-SAMPLE (6 months)
       (Build & optimize rules)          (Test rules UNCHANGED)
       (You CAN look at this)            (You CANNOT touch this until
                                          in-sample is finalized)
```

### Process

**Phase 1: In-Sample (Months 1–6)**
1. Use this data to develop and refine your rules
2. Backtest 50+ trades
3. Optimize parameters (e.g., RSI threshold, stop loss %)
4. Finalize your rules when metrics look good
5. **FREEZE the rules. No more changes.**

**Phase 2: Out-of-Sample (Months 7–12)**
1. Apply your FROZEN rules to this data
2. Do NOT change any rules based on what you see
3. Backtest 50+ trades
4. Compare metrics to in-sample

### Interpreting Results

```
SCENARIO A: OOS metrics ≈ IS metrics (within 20%)
  IS Win Rate: 58%  →  OOS Win Rate: 54%
  IS Expectancy: +₹1,800  →  OOS: +₹1,500
  → ROBUST SYSTEM ✅ (Proceed to paper trading)

SCENARIO B: OOS metrics significantly worse
  IS Win Rate: 58%  →  OOS Win Rate: 42%
  IS Expectancy: +₹1,800  →  OOS: +₹200
  → OVERFITTED ❌ (Go back, simplify rules, retest)

SCENARIO C: OOS metrics better than IS
  IS Win Rate: 58%  →  OOS Win Rate: 65%
  → Lucky or market conditions favored your system
  → Don't get overconfident. Still proceed cautiously.
```

### The 20% Degradation Rule

Expect your out-of-sample results to be **15–25% worse** than in-sample. This is normal and healthy.

```
If IS Expectancy = +₹2,000
Expect OOS Expectancy = +₹1,500 to +₹1,700 (normal degradation)

If OOS Expectancy = +₹1,900 → Suspiciously close (lucky?)
If OOS Expectancy = +₹500 → Overfitted (too much degradation)
If OOS Expectancy = -₹200 → Broken (go back to drawing board)
```

---

## 11. WALK-FORWARD ANALYSIS (Simplified)

Walk-Forward Analysis (WFA) is an advanced version of in-sample/out-of-sample testing that provides even more robustness.

### Concept

Instead of one IS/OOS split, you create **multiple rolling windows:**

```
WALK-FORWARD ANALYSIS (3 Windows):

Window 1:
  Train: Jan–Apr (4 months)  →  Test: May–Jun (2 months)

Window 2:
  Train: Mar–Jun (4 months)  →  Test: Jul–Aug (2 months)

Window 3:
  Train: May–Aug (4 months)  →  Test: Sep–Oct (2 months)

Final Result: Combine all 3 test periods (May–Jun + Jul–Aug + Sep–Oct)
              = 6 months of out-of-sample data
```

### Simplified Version for Beginners

You don't need full WFA yet. Just do:

1. **First 6 months**: Build and test your system
2. **Next 3 months**: Test with frozen rules (out-of-sample)
3. **If OOS is good**: Proceed to paper trading
4. **If OOS is bad**: Simplify and restart

---

## 12. WHEN TO TRUST YOUR BACKTEST

### The Trust Checklist

Your backtest is trustworthy if you can check ALL of these:

```
TRUST CHECKLIST:

☐ At least 100 trades completed
☐ Data includes diverse market conditions (trend + range + volatile)
☐ Data includes at least 2 major events
☐ Rules were defined BEFORE backtesting started
☐ No rules were changed mid-backtest
☐ Transaction costs deducted (~₹300–500/trade)
☐ Slippage accounted for (~₹500–1,000/trade)
☐ Out-of-sample testing done (metrics within 20% of in-sample)
☐ "Remove best 5 trades" test still positive
☐ Max drawdown is survivable (< 25–30%)
☐ No single month contributes > 40% of total profit
☐ Equity curve has realistic drawdowns (not a straight line)
☐ Profit factor between 1.3 and 2.5 (not > 3.0)
☐ You followed rules exactly (no hindsight bias)
```

**If you check 12+ out of 14: Your backtest is reliable. Proceed to paper trading (Week 22).**

**If you check 8–11: Your backtest is suggestive but needs more work. Fix the gaps.**

**If you check < 8: Your backtest is unreliable. Start over with stricter discipline.**

### The Final Reality Check

```
BACKTEST PROFIT vs REAL PROFIT:

  Backtest Net Profit:     ₹1,80,000 (over 100 trades)
  Expected Real Profit:    ₹1,00,000 – ₹1,30,000 (30–45% lower)

  WHY THE GAP?
  → Emotional errors (breaking rules under pressure)
  → Execution delays (real-time is slower than replay)
  → Worse slippage in live markets
  → Missed trades (you won't catch every signal live)
  → Unexpected market events not in your test period

  RULE OF THUMB: Expect real performance to be 50–70% of
                 backtest performance. If that's still
                 profitable, you have a genuine edge.
```

---

## 13. PRACTICAL EXERCISE

### Exercise 1: Mini Backtest (20 Trades)

**Objective:** Complete a 20-trade mini backtest to practice the process. (You'll extend to 100 over the next 2 weeks.)

**Steps:**
1. Open TradingView → NSE:NIFTY → 15-min chart
2. Add 20 EMA, VWAP, RSI(14)
3. Start Bar Replay from 3 months ago
4. Use this simple system:
   - **Entry:** Buy ATM CE when NIFTY crosses above VWAP + 20 EMA with RSI > 50
   - **SL:** 25% of premium
   - **Target:** 50% of premium
   - **Time:** 9:45 AM – 1:30 PM only
5. Record 20 trades in a spreadsheet
6. Calculate: Win Rate, Avg Win, Avg Loss, Expectancy, Profit Factor

**Time required:** ~5–6 hours

### Exercise 2: Overfitting Detection

**Given this backtest result, identify the problems:**

```
System: "NIFTY Straddle Buyer"
Period: Jan–Mar 2024 (3 months)
Trades: 18
Win Rate: 72%
Avg Win: ₹8,500
Avg Loss: ₹2,100
R:R: 4.05:1
Expectancy: +₹5,530
Profit Factor: 5.2
Max Drawdown: 4%
Equity Curve: Straight line up
Rules: Buy straddle when VIX between 13.1–14.8 AND
       day is Tue/Wed AND NIFTY gap up 0.3–0.7% AND
       PCR between 1.12–1.28 AND 20 EMA slope > 0.5
```

**Problems to identify:** (Answers in Self-Test)

### Exercise 3: Cost Adjustment

Your raw backtest shows:
- 100 trades, Net Profit = ₹2,50,000
- Average 2 legs per trade (spreads)

Calculate the realistic net profit after:
- Brokerage: ₹20 per order
- STT + Exchange + GST + Stamp + SEBI: ~₹80 per round-trip per leg
- Slippage: ~₹500 per trade

---

## 14. SELF-TEST WITH ANSWERS

### Question 1
Why is 100 trades considered the minimum for a reliable backtest?

**Answer:** Because of the Law of Large Numbers. Small samples (5–20 trades) are dominated by random luck and don't reflect the true statistical properties of your system. At 100+ trades, the observed win rate, R:R, and expectancy converge toward their true values, giving you ~85% reliability.

### Question 2
Your backtest shows 65% win rate, Avg Win ₹3,000, Avg Loss ₹6,000. Is this system profitable?

**Answer:** Calculate Expectancy:
(0.65 × 3,000) – (0.35 × 6,000) = 1,950 – 2,100 = **–₹150 per trade.**
Despite a high win rate, this system LOSES money because the average loss is twice the average win. The R:R is 0.5:1, which is terrible. **Not profitable.**

### Question 3
What is the difference between in-sample and out-of-sample data?

**Answer:** In-sample data is the historical period used to develop and optimize your trading rules. Out-of-sample data is a separate, later period used to test the frozen rules without any modifications. If OOS performance is close to IS performance (within 20%), the system is robust. If OOS is much worse, the system is overfitted.

### Question 4
Name 3 types of bias that can corrupt a backtest.

**Answer:**
1. **Look-ahead bias:** Using future information that wouldn't have been available at the time of the trade (e.g., knowing the day's close before entering).
2. **Survivorship bias:** Testing only on instruments/periods that performed well, ignoring crashes or delisted stocks.
3. **Confirmation bias:** Selectively recording only trades that support your hypothesis while skipping losing setups.
(Also acceptable: overfitting/curve fitting, selection bias, hindsight bias.)

### Question 5
Your backtest shows Profit Factor = 4.5, equity curve is a perfect straight line up, and all 100 trades are profitable. What should you conclude?

**Answer:** This is almost certainly **overfitted** and unrealistic. Real trading ALWAYS has losing trades and drawdowns. A 100% win rate with PF 4.5 means either: (a) you cherry-picked data, (b) you have look-ahead bias, (c) you fitted rules perfectly to historical noise. **Do NOT trade this system live.** Simplify the rules and retest on out-of-sample data.

### Question 6
Calculate the expectancy and profit factor for this system:
- 120 trades, 66 wins, 54 losses
- Total gross profit: ₹4,62,000
- Total gross loss: ₹1,89,000

**Answer:**
- Win Rate = 66/120 = 55%
- Avg Win = 4,62,000 / 66 = ₹7,000
- Avg Loss = 1,89,000 / 54 = ₹3,500
- **Expectancy** = (0.55 × 7,000) – (0.45 × 3,500) = 3,850 – 1,575 = **+₹2,275 per trade** ✅
- **Profit Factor** = 4,62,000 / 1,89,000 = **2.44** ✅ (Very good)

### Question 7
What is Maximum Drawdown and why does it matter more than total profit?

**Answer:** Maximum Drawdown (MDD) is the largest peak-to-trough decline in your equity curve, expressed as a percentage. It matters more than total profit because it represents the worst psychological pain you'll endure. A system with ₹5,00,000 profit but 50% MDD will likely be abandoned during the drawdown, while a system with ₹2,00,000 profit and 15% MDD will be followed consistently. **Survivability > Profitability.**

### Question 8
Identify the problems in Exercise 2 (the straddle system with 72% WR, 4.05 R:R, PF 5.2, 4% MDD, 18 trades, 5 hyper-specific conditions).

**Answer:**
1. **Sample size too small:** Only 18 trades (need 100+). Results are statistically meaningless.
2. **Overfitting:** 5 hyper-specific conditions (VIX 13.1–14.8, gap 0.3–0.7%, PCR 1.12–1.28) are clearly fitted to historical noise.
3. **Unrealistic metrics:** 72% WR + 4.05 R:R + PF 5.2 + 4% MDD is too good to be true for any options strategy.
4. **Straight-line equity curve:** No drawdowns = overfitted.
5. **Short period:** Only 3 months, likely one market regime.
6. **No out-of-sample testing mentioned.**

### Question 9
Calculate the realistic net profit for Exercise 3 (Gross: ₹2,50,000, 100 trades, 2 legs each).

**Answer:**
- Brokerage: 100 trades × 2 legs × 2 sides × ₹20 = ₹8,000
- Other charges (STT + Exchange + GST + Stamp + SEBI): 100 × 2 legs × 2 sides × ₹20 ≈ ₹8,000
- Slippage: 100 trades × ₹500 = ₹50,000
- Total costs: ₹8,000 + ₹8,000 + ₹50,000 = **₹66,000**
- **Realistic Net Profit: ₹2,50,000 – ₹66,000 = ₹1,84,000** (26% reduction)

### Question 10
Your in-sample expectancy is +₹2,000 and out-of-sample expectancy is +₹800. Should you trade this system?

**Answer:** The degradation is (2,000 – 800) / 2,000 = **60%**, which is well beyond the acceptable 20% threshold. This indicates significant overfitting. **Do NOT trade live.** Go back, simplify your rules (remove 2–3 conditions), and retest. The OOS expectancy of +₹800 is still positive, which suggests there may be a real edge buried under the overfitting — but you need to find the simpler version of the system.

---

## WEEK 21 SUMMARY CHEAT SHEET

```
┌───────────────────────────────────────────────────────┐
│              WEEK 21: BACKTESTING CHEAT SHEET         │
├───────────────────────────────────────────────────────┤
│                                                       │
│  MINIMUM TRADES: 100 (200+ preferred)                 │
│  DATA PERIOD: 6–12 months, diverse conditions         │
│  COSTS TO DEDUCT: ₹500–1,000 per trade               │
│  SLIPPAGE: ₹500–1,000 per trade                      │
│                                                       │
│  KEY METRICS:                                         │
│  • Win Rate: 50–65% (directional)                    │
│  • R:R: > 1.2:1                                      │
│  • Expectancy: > +₹1,000/trade                       │
│  • Profit Factor: 1.5–2.5                            │
│  • Max Drawdown: < 25%                               │
│  • Recovery Factor: > 2.0                            │
│                                                       │
│  RED FLAGS:                                           │
│  • WR > 80% with high R:R                            │
│  • PF > 3.0                                          │
│  • Straight-line equity curve                        │
│  • Profits from 2–3 trades only                      │
│  • Works in only 1 market condition                  │
│                                                       │
│  PROCESS:                                             │
│  1. Define rules precisely (no ambiguity)             │
│  2. In-sample test (6 months, build rules)            │
│  3. Freeze rules                                     │
│  4. Out-of-sample test (3 months, no changes)         │
│  5. OOS within 20% of IS → Proceed                   │
│  6. Deduct costs & slippage                          │
│  7. Expect real = 50–70% of backtest                 │
│                                                       │
│  TOOLS: TradingView Bar Replay, Sensibull, Opstra,   │
│         Google Sheets, Neostox                        │
│                                                       │
│  NEXT: Week 22 — Paper Trading & Forward Testing      │
└───────────────────────────────────────────────────────┘
```

---

**Phase 4 Progress: Week 19 ✅ | Week 20 ✅ | Week 21 ✅ | Week 22 ⬜**

When you're ready, say **"proceed to week 22"** and I'll deliver the final week of Phase 4: Paper Trading & Forward Testing — where you'll take your backtested system and test it in real-time market conditions without risking real money.
