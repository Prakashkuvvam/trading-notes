# WEEK 15: THE GREEKS — VEGA (VOLATILITY SENSITIVITY)

## Phase 3 — Options Theory Deep Study (Week 5 of 8)

---

## INTRODUCTION

Over the last three weeks, you've learned three of the four major Greeks:

- **Delta** (Week 12): How premium changes when NIFTY moves → The speedometer
- **Gamma** (Week 13): How delta accelerates → The accelerator pedal
- **Theta** (Week 14): How premium decays with time → The fuel leak

All three of these Greeks are driven by factors you can observe directly: NIFTY's price and the calendar. But there's a fourth factor that's invisible, constantly shifting, and can make your premium surge or collapse **even when NIFTY hasn't moved a single point**:

> **VEGA (ν) — The sensitivity of your option to changes in market volatility.**

Consider this real scenario:

> **Monday 10:00 AM:** NIFTY at 24,400. 24,400 CE at ₹85. IV = 14%.
> **Monday 2:00 PM:** NIFTY still at 24,400. But breaking news: RBI announces an emergency rate decision tomorrow.
> **Monday 2:05 PM:** 24,400 CE is now at ₹110. IV jumped to 20%.
>
> NIFTY didn't move. Time barely passed. But your premium jumped ₹25 (+29%) purely because volatility increased.

The next day, after the RBI announcement:

> **Tuesday 3:00 PM:** NIFTY at 24,420 (+20 points). 24,400 CE at ₹72. IV dropped to 12%.
>
> NIFTY moved 20 points in your direction, but your premium DROPPED ₹13 because IV collapsed ("IV crush"). The vega loss overwhelmed the delta gain.

This week, you'll master vega and the concept of Implied Volatility (IV) — the single most misunderstood force in options trading. By the end, you'll understand why options sometimes behave "irrationally" and how to use volatility as a trading edge rather than a source of confusion.

---

## CHAPTER 1: WHAT IS VEGA?

### 1.1 The Definition

**Vega (ν) measures how much an option's premium changes for every 1% change in Implied Volatility (IV).**

```
    ╔═══════════════════════════════════════════════════════════╗
    ║                                                           ║
    ║   VEGA = Change in Option Premium / Change in IV (%)      ║
    ║                                                           ║
    ║   ν = ΔPremium / ΔIV                                     ║
    ║                                                           ║
    ╚═══════════════════════════════════════════════════════════╝
```

**In plain English:** If IV increases by 1 percentage point (e.g., from 14% to 15%), by how many rupees will your option premium change? That number is vega.

### 1.2 A Simple Example

You hold a 24,400 CE with:
- Premium: ₹85
- IV: 14%
- Vega: **+₹4.0**

**IV increases from 14% to 16% (+2%):**

```
    Premium change = Vega × IV change
                   = ₹4.0 × 2
                   = +₹8.0
    
    New premium ≈ ₹85 + ₹8 = ₹93
    
    NIFTY didn't move. Time barely passed.
    The entire ₹8 gain is from the IV increase.
```

**IV decreases from 14% to 12% (-2%):**

```
    Premium change = ₹4.0 × (-2) = -₹8.0
    
    New premium ≈ ₹85 - ₹8 = ₹77
    
    Even if NIFTY moved slightly in your favor, the IV 
    drop could wipe out your delta gains.
```

### 1.3 Vega Sign Convention

```
    ╔═══════════════════════════════════════════════════════════╗
    ║                                                           ║
    ║   OPTION BUYER:  Vega is POSITIVE (+ν)                    ║
    ║   → Premium INCREASES when IV rises                       ║
    ║   → Premium DECREASES when IV falls                       ║
    ║   → You BENEFIT from rising volatility                    ║
    ║                                                           ║
    ║   OPTION SELLER: Vega is NEGATIVE (-ν)                    ║
    ║   → Premium DECREASES when IV rises (seller loses)        ║
    ║   → Premium INCREASES when IV falls (seller gains)        ║
    ║   → You BENEFIT from falling volatility                   ║
    ║                                                           ║
    ╚═══════════════════════════════════════════════════════════╝
```

**Key insight:** Both call and put buyers have positive vega. When IV rises, ALL option premiums increase (calls AND puts). When IV falls, ALL option premiums decrease. This is different from delta, where calls and puts move in opposite directions.

### 1.4 Vega Is Not a Greek Letter

Fun fact: "Vega" is not actually a Greek letter. The real Greek letter for this concept is "nu" (ν). But traders universally call it "vega" because it sounds like "volatility." Don't let this confuse you — vega = volatility sensitivity.

---

## CHAPTER 2: VEGA VALUES ACROSS THE MONEYNES SPECTRUM

### 2.1 The Vega Curve

Like gamma and theta, vega is highest at ATM and decreases as you move away. But the shape is wider and flatter than gamma:

```
    VEGA CURVE (NIFTY at 24,400, 7 days to expiry)
    
    Vega
    ₹5.0 ┤
         │        ╭────────╮
    ₹4.5 ┤      ╭╯          ╰╮     ← Wide peak around ATM
         │    ╭╯              ╰╮
    ₹4.0 ┤   ╱                  ╲
         │  ╱                    ╲
    ₹3.0 ┤ ╱                      ╲
         │╱                        ╲
    ₹2.0 ┤                          ╲
         │                            ╲
    ₹1.0 ┤                              ╲
         │                                ╲
    ₹0.0 ┤──────────────────────────────────╲──
         24000  24200  24400  24600  24800
                ← ITM    ATM    OTM →
    
    Vega is HIGHEST at ATM but the peak is WIDER than gamma.
    Even options 100-200 points from ATM have significant vega.
```

### 2.2 Vega by Moneyness — The Complete Table

**NIFTY spot = 24,400. 7 days to expiry. IV = 14%.**

| Moneyness | Strike | Premium | Delta | Gamma | Theta | **Vega** |
|-----------|--------|---------|-------|-------|-------|----------|
| **Deep ITM** | 24,000 CE | ₹440 | 0.95 | 0.0005 | -₹5 | **₹1.5** |
| **ITM** | 24,200 CE | ₹255 | 0.80 | 0.0015 | -₹8 | **₹3.0** |
| **Slightly ITM** | 24,350 CE | ₹115 | 0.62 | 0.0035 | -₹12 | **₹4.2** |
| **ATM** | 24,400 CE | ₹100 | 0.50 | 0.0040 | -₹14 | **₹4.8** |
| **Slightly OTM** | 24,450 CE | ₹78 | 0.40 | 0.0038 | -₹13 | **₹4.5** |
| **OTM** | 24,600 CE | ₹35 | 0.18 | 0.0020 | -₹8 | **₹3.2** |
| **Deep OTM** | 24,800 CE | ₹8 | 0.05 | 0.0005 | -₹2 | **₹1.2** |

### 2.3 Key Observations

**Observation 1: ATM options have the highest vega.**

The 24,400 CE has vega ₹4.8 — the highest of all strikes. This means ATM options are most sensitive to IV changes. A 1% IV increase adds ₹4.8 to the premium.

**Observation 2: Vega is significant even for ITM and OTM options.**

Unlike gamma (which drops to near zero for deep ITM/OTM), vega remains meaningful even 200 points from ATM. The 24,200 CE (ITM) has vega ₹3.0, and the 24,600 CE (OTM) has vega ₹3.2. This is because IV affects the entire probability distribution, not just the immediate vicinity of the strike.

**Observation 3: Vega is roughly symmetric around ATM.**

The 24,350 CE (vega ₹4.2) and 24,450 CE (vega ₹4.5) have similar vega. This is different from theta, which is slightly asymmetric. IV changes affect calls and puts at equal distances from ATM almost equally.

---

## CHAPTER 3: VEGA AND TIME TO EXPIRY — THE OPPOSITE OF THETA

### 3.1 The Most Important Vega Fact

> **Vega INCREASES with time to expiry. This is the OPPOSITE of theta.**

While theta accelerates as expiry approaches (destroying premium faster), vega decelerates as expiry approaches (IV changes matter less).

### 3.2 Vega at Different Times to Expiry

**24,400 CE (ATM), NIFTY at 24,400, IV = 14%:**

| Days to Expiry | Theta | **Vega** | Interpretation |
|----------------|-------|----------|----------------|
| **30 days** | -₹3 | **₹12.0** | IV changes have MASSIVE impact |
| **21 days** | -₹4 | **₹10.0** | IV changes have large impact |
| **14 days** | -₹6 | **₹8.0** | IV changes have significant impact |
| **7 days** | -₹10 | **₹4.8** | IV changes have moderate impact |
| **3 days** | -₹16 | **₹2.5** | IV changes have small impact |
| **1 day** | -₹25 | **₹1.0** | IV changes have minimal impact |
| **Expiry day** | -₹10/hr | **₹0.3** | IV changes barely matter |

```
    VEGA vs TIME TO EXPIRY (ATM Option)
    
    Vega
    ₹12 ┤╲
        │  ╲
    ₹10 ┤    ╲
        │      ╲
     ₹8 ┤        ╲
        │          ╲
     ₹6 ┤            ╲
        │              ╲
     ₹4 ┤                ╲╲
        │                   ╲╲
     ₹2 ┤                     ╲╲╲
        │                         ╲╲
     ₹1 ┤                            ╲╲
        │                               ╲
     ₹0 ┤─────────────────────────────────╲
        30   25   20   15   10   7   3   1   0
                       Days to Expiry
    
    Vega DECREASES as expiry approaches.
    This is the MIRROR IMAGE of the theta curve.
    
    Theta curve:  Flat → Steep (accelerates near expiry)
    Vega curve:   Steep → Flat (decelerates near expiry)
```

### 3.3 Why Vega Behaves Oppositely to Theta

Think about it logically:

**30 days to expiry:**
- IV represents the market's expectation of volatility over the next 30 days
- A 1% change in IV affects 30 days of expected price movement
- That's a LOT of uncertainty being repriced → large vega
- Example: IV going from 14% to 15% means the market now expects NIFTY to move ~±750 points over 30 days instead of ~±700 points. That 50-point difference in expected range significantly changes the probability of your option finishing ITM.

**1 day to expiry:**
- IV represents the market's expectation of volatility over the next 1 day
- A 1% change in IV affects only 1 day of expected movement
- That's a TINY amount of uncertainty being repriced → small vega
- Example: IV going from 14% to 15% changes the expected daily range from ~±130 points to ~±140 points. A 10-point difference barely affects the probability of your option finishing ITM.

```
    THE INTUITION
    
    30 days out: "Will there be a storm this month?"
    → Changing the forecast from "maybe" to "likely" 
      dramatically changes your plans. High vega.
    
    1 day out: "Will there be a storm tomorrow?"
    → You can look out the window. Changing the forecast 
      barely matters — you'll know in hours. Low vega.
```

### 3.4 The Theta-Vega Seesaw

```
    ╔═══════════════════════════════════════════════════════════╗
    ║                                                           ║
    ║   FAR FROM EXPIRY:  High Vega, Low Theta                  ║
    ║   → IV changes matter a lot, time decay is slow           ║
    ║   → Best for: Volatility plays, event anticipation        ║
    ║                                                           ║
    ║   NEAR EXPIRY:      Low Vega, High Theta                  ║
    ║   → IV changes barely matter, time decay is rapid         ║
    ║   → Best for: Quick directional moves (delta + gamma)     ║
    ║                                                           ║
    ╚═══════════════════════════════════════════════════════════╝
```

**Practical implication:** If you're trading weekly NIFTY options (5–7 days to expiry), vega is relatively small (₹3–5 per 1% IV change). Your P&L is dominated by delta, gamma, and theta. But if you're trading monthly options (20–30 days), vega becomes the dominant Greek, and IV changes can overwhelm directional moves.

---

## CHAPTER 4: VEGA IN ACTION — REAL NIFTY EXAMPLES

### 4.1 Example 1: IV Spike Before an Event

**Setup:**
- Monday: NIFTY at 24,400. RBI policy announcement on Wednesday.
- You buy: 24,400 CE (next week expiry, 10 days to expiry)
- Premium: ₹130
- Delta: 0.52, Gamma: 0.003, Theta: -₹8, **Vega: ₹7.0**
- IV: 14%

**Tuesday: Market gets nervous about RBI policy.**

| Factor | Change | Premium Impact |
|--------|--------|---------------|
| NIFTY | 24,400 → 24,410 (+10) | Delta: +0.52 × 10 = **+₹5.2** |
| Time | 1 day passes | Theta: **-₹8.0** |
| IV | 14% → 18% (+4%) | Vega: +₹7.0 × 4 = **+₹28.0** |
| **Net** | | **+₹25.2** |

**New premium:** ₹130 + ₹25.2 ≈ **₹155**

**Analysis:** NIFTY moved only 10 points (delta gain: +₹5.2). Time decay cost ₹8. But the IV spike from 14% to 18% added ₹28 — more than all other factors combined. **Vega dominated the P&L.**

### 4.2 Example 2: IV Crush After the Event

**Wednesday 2:30 PM: RBI announces rate cut. Market rallies, then IV collapses.**

| Factor | Change | Premium Impact |
|--------|--------|---------------|
| NIFTY | 24,410 → 24,520 (+110) | Avg Delta ~0.65 × 110 = **+₹71.5** |
| Time | 0.5 day | Theta: **-₹4.0** |
| IV | 18% → 12% (-6%) | Vega: +₹7.0 × (-6) = **-₹42.0** |
| **Net** | | **+₹25.5** |

**New premium:** ₹155 + ₹25.5 ≈ **₹180**

**Analysis:** NIFTY rallied 110 points — a massive move! Delta contributed +₹71.5. But the IV crush from 18% to 12% destroyed ₹42 of premium. **Your profit was cut by 37% due to IV crush.** Without the IV drop, your premium would have been ₹222 instead of ₹180.

**This is why buying options before major events is dangerous.** Even if you get the direction right, the IV crush can eat a huge chunk of your profits.

### 4.3 Example 3: IV Crush on a Wrong Direction Bet

**Same scenario, but NIFTY falls after RBI policy (unexpected hawkish tone):**

| Factor | Change | Premium Impact |
|--------|--------|---------------|
| NIFTY | 24,410 → 24,320 (-90) | Avg Delta ~0.40 × (-90) = **-₹36.0** |
| Time | 0.5 day | Theta: **-₹4.0** |
| IV | 18% → 12% (-6%) | Vega: +₹7.0 × (-6) = **-₹42.0** |
| **Net** | | **-₹82.0** |

**New premium:** ₹155 - ₹82 ≈ **₹73**

**Analysis:** You lost ₹82 per share. Delta loss was -₹36 (wrong direction). But IV crush added another -₹42 loss. **The IV crush was a bigger loss than the directional move!** You were hit by a "double whammy" — wrong direction AND falling volatility.

### 4.4 The Four Scenarios Matrix

| Direction | IV Change | Delta Effect | Vega Effect | Net Result |
|-----------|-----------|-------------|-------------|------------|
| **Right** | **IV Rises** | +Gain | +Gain | 🚀 **Massive profit** (both work for you) |
| **Right** | **IV Falls** | +Gain | -Loss | ⚠️ **Reduced profit** (vega offsets delta) |
| **Wrong** | **IV Rises** | -Loss | +Gain | ⚠️ **Reduced loss** (vega cushions delta) |
| **Wrong** | **IV Falls** | -Loss | -Loss | 💀 **Massive loss** (both work against you) |

**The worst-case scenario for an option buyer:** Wrong direction + IV crush. This is the "double whammy" that destroys capital fastest.

**The best-case scenario:** Right direction + IV expansion. This is the "double boost" that creates the biggest winners.

---

## CHAPTER 5: IMPLIED VOLATILITY (IV) — THE DEEP DIVE

### 5.1 What Is Implied Volatility?

**Implied Volatility (IV) is the market's expectation of how much the underlying asset (NIFTY) will move over the remaining life of the option.**

It is called "implied" because it is **implied by the option's market price**. You can't observe IV directly — you calculate it backwards from the premium using the Black-Scholes model.

```
    HOW IV IS DERIVED
    
    Black-Scholes Model:
    Premium = f(Spot, Strike, Time, IV, Rate)
    
    You know: Premium (from market), Spot, Strike, Time, Rate
    You solve for: IV (the only unknown)
    
    If the market price of 24,400 CE is ₹100, and all other 
    inputs are known, the IV that makes Black-Scholes output 
    ₹100 is the "implied volatility."
    
    If the market price jumps to ₹120 (with no change in 
    NIFTY or time), the IV must have increased to justify 
    the higher premium.
```

### 5.2 IV as a Percentage

IV is expressed as an **annualized percentage**. An IV of 14% means:

> "The market expects NIFTY to move approximately ±14% over the next year, with 68% probability (1 standard deviation)."

**Translating annualized IV to shorter periods:**

```
    IV = 14% (annualized)
    
    Expected move over 1 year:  ±14% of NIFTY = ±3,416 points
    Expected move over 1 month: ±14% / √12 = ±4.04% = ±986 points
    Expected move over 1 week:  ±14% / √52 = ±1.94% = ±473 points
    Expected move over 1 day:   ±14% / √252 = ±0.88% = ±215 points
    
    Formula: Expected Move = Spot × IV × √(Days/365)
    
    For NIFTY at 24,400 with IV 14%:
    Daily expected move ≈ 24,400 × 0.14 × √(1/365) ≈ ±126 points
```

**Practical interpretation:** When IV is 14%, the market expects NIFTY to move roughly ±125–130 points per day (68% of the time). If NIFTY moves 200+ points in a day, that's a 1.5+ standard deviation move — unusual but not extreme.

### 5.3 IV vs Historical Volatility (HV)

| | Implied Volatility (IV) | Historical Volatility (HV) |
|---|---|---|
| **What it measures** | Expected future volatility | Actual past volatility |
| **Direction** | Forward-looking | Backward-looking |
| **Source** | Option prices (market consensus) | NIFTY price history |
| **Analogy** | Weather forecast | Yesterday's weather |
| **Changes when** | Market sentiment changes | NIFTY actually moves |
| **Use for trading** | ✅ Primary (prices options) | ⚠️ Secondary (context) |

**The relationship:**
- When IV > HV: Options are "expensive" relative to recent history. Market expects more volatility than has been occurring.
- When IV < HV: Options are "cheap" relative to recent history. Market expects less volatility than has been occurring.
- When IV ≈ HV: Options are "fairly priced" relative to recent history.

### 5.4 What Drives IV?

| Factor | Effect on IV | Example |
|--------|-------------|---------|
| **Fear/Uncertainty** | IV Rises ↑ | War, pandemic, political crisis, bank failures |
| **Major Events** | IV Rises before, Falls after | RBI policy, Budget, elections, US Fed |
| **Market Crashes** | IV Spikes ↑↑ | March 2020 (IV hit 40%+), 2008 crisis |
| **Calm Markets** | IV Falls ↓ | Holiday weeks, summer doldrums |
| **FII Selling** | IV Rises ↑ | Persistent foreign outflows |
| **Strong Trends** | IV May Fall ↓ | Steady uptrend with no surprises |
| **Earnings Season** | IV Rises for individual stocks | Not applicable to NIFTY index |

---

## CHAPTER 6: INDIA VIX — THE FEAR GAUGE

### 6.1 What Is India VIX?

**India VIX (Volatility Index)** is the NSE's official measure of expected 30-day volatility for NIFTY. It is calculated from the prices of NIFTY options across multiple strikes and expiries.

Think of India VIX as the **"fear gauge"** of the Indian stock market:

```
    INDIA VIX INTERPRETATION
    
    VIX Level    Market Mood          Option Premiums
    ─────────    ───────────          ───────────────
    10-12        Very Calm 😌         Cheap (low IV)
    12-15        Normal 🙂            Fair (normal IV)
    15-18        Slightly Nervous 😐  Slightly expensive
    18-22        Anxious 😟           Expensive (high IV)
    22-28        Fearful 😨           Very expensive
    28-35        Panic 😱             Extremely expensive
    35+          Crisis 🚨            Once-in-a-decade levels
    
    Historical India VIX Range (2010-2024):
    Lowest: ~8.5 (December 2017, extreme complacency)
    Highest: ~45 (March 2020, COVID crash)
    Average: ~15-16
    Most common: 12-18
```

### 6.2 How India VIX Relates to Your Options

India VIX is essentially the **average IV** of NIFTY options. When VIX is high, all NIFTY options are expensive. When VIX is low, all options are cheap.

**Practical example:**

| India VIX | ATM 24,400 CE (7 days) | Interpretation |
|-----------|------------------------|----------------|
| 12 | ₹75 | Options are cheap. Good time to BUY. |
| 15 | ₹100 | Options are fairly priced. Normal trading. |
| 18 | ₹120 | Options are expensive. Be cautious buying. |
| 22 | ₹148 | Options are very expensive. Consider SELLING. |
| 28 | ₹185 | Options are extremely expensive. Avoid buying. |

### 6.3 The VIX-NIFTY Inverse Relationship

VIX and NIFTY typically move in **opposite directions**:

```
    TYPICAL VIX-NIFTY RELATIONSHIP
    
    NIFTY:  ╱╱╱╱╲╲╲╲╲╲╱╱╱╱╱╱╱╱╲╲╲╲╱╱╱╱
    
    VIX:    ╲╲╲╲╱╱╱╱╱╱╲╲╲╲╲╲╲╲╱╱╱╱╲╲╲╲
    
    When NIFTY falls → VIX rises (fear increases)
    When NIFTY rises → VIX falls (fear decreases)
    
    Correlation: Approximately -0.7 to -0.8 (strong inverse)
```

**Why?** When NIFTY crashes, investors rush to buy puts for protection. This demand drives up put premiums, which increases IV, which pushes VIX higher. When NIFTY rallies steadily, there's less demand for protection, IV drops, and VIX falls.

**Exception:** During extreme events (like the 2020 crash), both NIFTY and VIX can move dramatically in opposite directions simultaneously. VIX spiked from 15 to 45 while NIFTY crashed from 12,000 to 7,500.

### 6.4 Using India VIX for Trading Decisions

| VIX Level | Strategy Bias | Why |
|-----------|--------------|-----|
| **< 12** | Favor option buying | Options are cheap. Low theta cost. IV has room to expand. |
| **12–16** | Neutral | Fair pricing. Trade based on technical setups. |
| **16–20** | Cautious buying | Options getting expensive. Need bigger moves to profit. |
| **20–25** | Favor option selling | Options are expensive. High theta income. IV likely to revert down. |
| **> 25** | Strong selling bias | Options are very expensive. IV crush likely after the event. |

**Where to check India VIX:**
- NSE website: nseindia.com → Market Data → India VIX
- TradingView: Search `NSE:INDIAVIX`
- Sensibull: Dashboard shows current VIX
- Moneycontrol: Market section

---

## CHAPTER 7: IV PERCENTILE AND IV RANK

### 7.1 Why Raw IV Is Not Enough

Knowing that IV is 16% doesn't tell you whether options are "expensive" or "cheap" in context. IV of 16% might be high for a calm period but low for a crisis period.

**You need to compare current IV to its historical range.** This is what IV Percentile and IV Rank do.

### 7.2 IV Percentile (IVP)

**IV Percentile tells you the percentage of trading days in the past year when IV was lower than the current IV.**

```
    IV Percentile = (Days IV was lower / Total days) × 100
    
    Example: Current IV = 16%
    Over the past 252 trading days, IV was below 16% on 180 days.
    IV Percentile = 180/252 × 100 = 71%
    
    Interpretation: Current IV is higher than 71% of the past year.
    Options are relatively EXPENSIVE.
```

| IV Percentile | Interpretation | Action |
|--------------|----------------|--------|
| **0–25%** | IV is very low (historically cheap) | ✅ Favor buying options |
| **25–50%** | IV is below average | Slightly favor buying |
| **50–75%** | IV is above average | Slightly favor selling |
| **75–100%** | IV is very high (historically expensive) | ✅ Favor selling options |

### 7.3 IV Rank (IVR)

**IV Rank tells you where current IV sits within its 52-week high-low range.**

```
    IV Rank = (Current IV - 52-week Low) / (52-week High - 52-week Low) × 100
    
    Example:
    Current IV = 16%
    52-week Low = 10%
    52-week High = 28%
    
    IV Rank = (16 - 10) / (28 - 10) × 100 = 6/18 × 100 = 33%
    
    Interpretation: Current IV is at 33% of its 52-week range.
    Closer to the low end. Options are relatively CHEAP.
```

### 7.4 IVP vs IVR — Which to Use?

| | IV Percentile | IV Rank |
|---|---|---|
| **Measures** | % of days IV was lower | Position within high-low range |
| **Sensitivity** | More stable | More sensitive to outliers |
| **Best for** | General assessment | Quick high/low check |
| **Example** | IVP 70% = expensive | IVR 33% = cheap |

**Both can give different signals!** In the example above, IVP says 71% (expensive) while IVR says 33% (cheap). This happens when IV has been consistently in the middle range but had one extreme spike (e.g., during a crash) that pushes the 52-week high very high.

**Practical advice:** Use IV Percentile as your primary measure. It's more robust. Use IV Rank as a secondary check.

**Where to find IVP/IVR:**
- Sensibull: Option Chain → IV tab → Shows IV Percentile
- Opstra: Analytics → IV Percentile and IV Rank
- TradingView: Community indicators (search "IV Percentile")

---

## CHAPTER 8: THE IV SKEW (VOLATILITY SMILE)

### 8.1 What Is the IV Skew?

In theory, Black-Scholes assumes all strikes have the same IV. In reality, they don't. **OTM puts typically have higher IV than OTM calls.** This pattern is called the **volatility skew** or **volatility smile**.

```
    IV SKEW (NIFTY Options, Normal Market)
    
    IV
    18% ┤╲
        │  ╲
    16% ┤    ╲
        │      ╲          ╱
    14% ┤        ╲      ╱    ← "Smile" shape
        │          ╲  ╱
    12% ┤            ╲╱
        │
    10% ┤
        24000  24200  24400  24600  24800
        OTM Puts   ATM    OTM Calls
        
    OTM Puts (24,000 PE): IV ~17% (HIGHEST)
    ATM (24,400):         IV ~13% (LOWEST)
    OTM Calls (24,800 CE): IV ~14% (slightly higher than ATM)
```

### 8.2 Why Does the Skew Exist?

**Demand for downside protection.** Institutional investors hold large NIFTY portfolios. To protect against crashes, they buy OTM puts. This persistent demand drives up OTM put premiums, which increases their IV.

**Fear of crashes.** Markets crash faster than they rally. A 5% drop can happen in a day; a 5% rally takes weeks. The market prices this asymmetry into OTM put IV.

**Supply-demand imbalance.** More people buy OTM puts (insurance) than OTM calls (lottery tickets). Higher demand = higher IV for puts.

### 8.3 How the Skew Changes

| Market Condition | Skew Shape | Interpretation |
|-----------------|-----------|----------------|
| **Normal** | Gentle smile | OTM puts slightly more expensive |
| **Bullish** | Flatter smile | Less demand for puts, more for calls |
| **Bearish/Crash** | Steep skew | OTM puts extremely expensive (panic hedging) |
| **Euphoria** | Inverted skew | OTM calls more expensive than puts (rare, speculative mania) |

### 8.4 Practical Use of the Skew

**For option buyers:**
- OTM puts are "expensive" due to skew. If you want to buy puts for hedging, you're paying a premium for the skew.
- OTM calls are relatively "cheaper." If you're bullish, OTM calls offer better value per unit of IV.

**For strike selection:**
- Compare the IV of different strikes before choosing. If the 24,200 PE has IV 17% and the 24,400 PE has IV 13%, the 24,200 PE is relatively more expensive. You need a bigger move to justify the higher IV premium.

---

## CHAPTER 9: VEGA AND MAJOR EVENTS — THE IV CYCLE

### 9.1 The Event Volatility Cycle

Major events follow a predictable IV pattern:

```
    THE IV CYCLE AROUND MAJOR EVENTS
    
    IV
    25% ┤                    ╭╮
        │                  ╭╯╰╮  ← IV CRUSH
    22% ┤                ╭╯    ╰╮   (sharp drop after event)
        │              ╭╯        ╰╮
    18% ┤           ╭╯╱            ╰╮
        │         ╭╯╱                ╰╮
    15% ┤───────╯╱                     ╰──────
        │      ╱ ↑                        ↑
    12% ┤    ╱   Event                    Post-event
        │  ╱    Anticipation              Normalization
    10% ┤╱
        ──────────────────────────────────────────→ Time
        T-7   T-5   T-3   T-1  EVENT  T+1   T+3   T+5
        days                              days
    
    Phase 1 (T-7 to T-3): IV starts rising as event approaches
    Phase 2 (T-3 to T-1): IV accelerates upward (fear builds)
    Phase 3 (T-1 to Event): IV peaks (maximum uncertainty)
    Phase 4 (Event to T+1): IV CRUSH (uncertainty resolved)
    Phase 5 (T+1 to T+5): IV normalizes to pre-event levels
```

### 9.2 Major Indian Events and Their IV Impact

| Event | Frequency | IV Spike | IV Crush | Duration |
|-------|-----------|----------|----------|----------|
| **RBI Monetary Policy** | 6x/year | +3–6% | -4–8% | 2–3 days |
| **Union Budget** | 1x/year (Feb 1) | +5–10% | -6–12% | 3–5 days |
| **General Elections** | 1x/5 years | +8–15% | -10–15% | 1–2 weeks |
| **State Elections** | Variable | +2–5% | -3–6% | 2–3 days |
| **US Fed Decision** | 8x/year | +2–4% | -2–5% | 1–2 days |
| **Quarterly GDP** | 4x/year | +1–3% | -1–3% | 1 day |
| **Global Crashes** | Rare | +10–20% | Slow decline | Weeks |

### 9.3 How to Trade the IV Cycle

**Strategy 1: Buy Before the Run-Up (T-7 to T-5)**
- Buy options 5–7 days before the event when IV is still relatively low
- Hold as IV rises during the anticipation phase
- Sell BEFORE the event (T-1 or T-0 morning) to capture the IV expansion
- **Risk:** NIFTY might move against you during the holding period

**Strategy 2: Sell the IV Crush (T-0 to T+1)**
- Sell options just before or during the event when IV is at its peak
- Buy back after the event when IV crushes
- **Risk:** Unlimited loss if NIFTY makes an extreme move (use spreads to limit risk)
- **This is an advanced strategy — not recommended until Phase 4**

**Strategy 3: Avoid the Event Entirely**
- Close all positions before the event
- Re-enter after IV normalizes (T+2 to T+3)
- **Safest approach for beginners**

### 9.4 Real Example: Union Budget Day

**January 28 (T-3):** NIFTY at 24,400. IV = 16%. 24,400 CE (weekly) at ₹110.
**January 30 (T-1):** NIFTY at 24,380. IV = 22%. 24,400 CE at ₹145.
**February 1 (Budget Day, 11:00 AM):** NIFTY at 24,450. IV = 24%. 24,400 CE at ₹160.
**February 1 (Budget Day, 2:00 PM):** NIFTY at 24,520. IV = 14%. 24,400 CE at ₹135.

**Analysis of the Budget Day move (11 AM to 2 PM):**
```
    NIFTY: 24,450 → 24,520 (+70 points) → Delta gain ≈ +₹40
    IV: 24% → 14% (-10%) → Vega loss ≈ -₹50 (vega ~₹5 × 10)
    Time: 3 hours → Theta loss ≈ -₹3
    Net: +₹40 - ₹50 - ₹3 = -₹13
    
    NIFTY rallied 70 points but the option LOST ₹13!
    The IV crush completely overwhelmed the directional gain.
    
    Traders who bought calls at 11 AM expecting a Budget 
    rally were devastated despite being right about direction.
```

---

## CHAPTER 10: THE COMPLETE FOUR-GREEK DASHBOARD

### 10.1 Putting It All Together

Now that you know all four major Greeks, here's the complete dashboard:

```
    ╔═══════════════════════════════════════════════════════════════╗
    ║          COMPLETE GREEK DASHBOARD (24,400 CE)                ║
    ║          NIFTY: 24,400 | 7 days to expiry | IV: 14%          ║
    ╠═══════════════════════════════════════════════════════════════╣
    ║                                                               ║
    ║  Premium: ₹100                                                ║
    ║  Intrinsic: ₹0 | Extrinsic: ₹100                              ║
    ║                                                               ║
    ║  DELTA:  +0.50   → Premium moves ₹0.50 per NIFTY point        ║
    ║                      (Direction sensitivity)                  ║
    ║                                                               ║
    ║  GAMMA:  +0.004  → Delta changes 0.004 per NIFTY point        ║
    ║                      (Acceleration of direction)              ║
    ║                                                               ║
    ║  THETA:  -₹10    → Premium loses ₹10 per day (time decay)     ║
    ║                      (Time cost)                              ║
    ║                                                               ║
    ║  VEGA:   +₹4.8   → Premium changes ₹4.8 per 1% IV change      ║
    ║                      (Volatility sensitivity)                 ║
    ║                                                               ║
    ║  P&L ESTIMATE FOR TOMORROW (NIFTY +50, IV unchanged):         ║
    ║    Delta:  +0.50 × 50 = +₹25.0                                ║
    ║    Gamma:  +0.004 × 50² / 2 = +₹5.0 (approx)                 ║
    ║    Theta:  -₹10.0                                             ║
    ║    Vega:   ₹0 (IV unchanged)                                  ║
    ║    Net:    +₹20.0 per share → +₹1,500 per lot                 ║
    ║                                                               ║
    ║  P&L ESTIMATE (NIFTY flat, IV +3%):                           ║
    ║    Delta:  ₹0                                                  ║
    ║    Gamma:  ₹0                                                  ║
    ║    Theta:  -₹10.0                                             ║
    ║    Vega:   +₹4.8 × 3 = +₹14.4                                 ║
    ║    Net:    +₹4.4 per share → +₹330 per lot                    ║
    ║    (You made money without NIFTY moving!)                     ║
    ║                                                               ║
    ╚═══════════════════════════════════════════════════════════════╝
```

### 10.2 The Greek Sensitivity Matrix

| Greek | Driven By | Buyer | Seller | Highest When | Lowest When |
|-------|-----------|-------|--------|-------------|-------------|
| **Delta** | NIFTY price | + (calls), - (puts) | Opposite | Deep ITM | Deep OTM |
| **Gamma** | NIFTY price | Always + | Always - | ATM, near expiry | Deep ITM/OTM, far expiry |
| **Theta** | Time | Always - | Always + | ATM, near expiry | Deep ITM/OTM, far expiry |
| **Vega** | IV | Always + | Always - | ATM, far from expiry | Deep ITM/OTM, near expiry |

### 10.3 Which Greek Dominates When?

| Market Condition | Dominant Greek | Why |
|-----------------|---------------|-----|
| **NIFTY trending strongly** | Delta + Gamma | Directional move drives P&L |
| **NIFTY range-bound** | Theta | Time decay dominates when price doesn't move |
| **Before major event** | Vega | IV expansion drives premium higher |
| **After major event** | Vega (negative) | IV crush destroys premium |
| **Expiry day** | Gamma + Theta | Extreme gamma and theta in final hours |
| **Monthly options, calm market** | Vega | Long-dated options are most sensitive to IV |
| **Weekly options, volatile market** | Delta + Gamma | Short-dated, high gamma, low vega |

---

## CHAPTER 11: COMMON MISTAKES

### Mistake 1: Ignoring Vega Before Major Events
**Problem:** You buy ATM calls on Tuesday before Wednesday's RBI policy. NIFTY rallies 80 points after the announcement. You expect a big profit. But IV crushes from 20% to 13%, and your premium barely moves. You're confused.
**Fix:** Before any major event, check the IV level. If IV is already elevated (>18%), the IV crush after the event will likely offset your directional gains. Either exit before the event or use ITM options (less vega exposure).

### Mistake 2: Buying Options When VIX Is Already High
**Problem:** VIX is at 24. You buy ATM calls thinking "volatility is high, options will move a lot." Reality: Options are already expensive. If VIX drops to 16 (mean reversion), your premium will lose ₹30–40 per share from vega alone, even if NIFTY moves in your direction.
**Fix:** When VIX > 20, be very cautious about buying options. Consider selling strategies instead (Phase 4). If you must buy, use ITM options (lower vega) and keep positions small.

### Mistake 3: Not Understanding Why Both Calls and Puts Rise During a Crash
**Problem:** NIFTY crashes 300 points. You see both 24,400 CE and 24,400 PE premiums increasing. "How can both calls and puts go up? One should go up and the other down!"
**Reality:** The put is going up because of delta (NIFTY fell → put gains). The call is going up because of vega (IV spiked during the crash → all options gain). The vega gain on the call can temporarily exceed the delta loss. This is a short-term phenomenon — once IV normalizes, the call will drop.

### Mistake 4: Confusing IV with Direction
**Problem:** "IV is rising, so the market must be bullish." Reality: IV rising means the market expects MORE VOLATILITY, not necessarily a specific direction. IV typically rises when markets fall (fear) and falls when markets rise (complacency). Rising IV is usually bearish, not bullish.

### Mistake 5: Holding Long-Dated Options Without Monitoring IV
**Problem:** You buy a monthly ATM call with 25 days to expiry. Vega is ₹10. Over the next week, IV drops from 16% to 13% (-3%). Your premium loses ₹30 from vega alone — more than 2 days of theta decay.
**Fix:** For options with >14 days to expiry, monitor IV daily. Vega is the dominant Greek for long-dated options. A 2–3% IV change can move your premium more than a 50-point NIFTY move.

### Mistake 6: Thinking Low IV Means "Safe" to Buy
**Problem:** VIX is at 11 (very low). You buy ATM calls thinking "options are cheap, great time to buy." Reality: Low IV means the market expects calm conditions. If the market stays calm, theta will eat your premium. And if a surprise event causes IV to spike, you'll benefit from vega — but you can't predict when that will happen.
**Fix:** Low IV is good for buying options IF you expect a volatility expansion (e.g., an upcoming event). Don't buy just because IV is low — you still need a directional catalyst.

### Mistake 7: Not Adjusting for IV When Comparing Options
**Problem:** You compare two ATM calls: current week at ₹60 (IV 13%) and next week at ₹100 (IV 16%). You think next week is "overpriced." Reality: The higher IV accounts for part of the price difference. If both had the same IV, next week's premium would be ~₹85, not ₹100. The extra ₹15 is the vega premium.
**Fix:** When comparing options across expiries, normalize for IV. Use Sensibull's "Theoretical Price" feature to see what the premium would be at the same IV.

---

## CHAPTER 12: PRACTICAL EXERCISES

### Exercise 1: Vega Calculation Drill
NIFTY is at 24,400. You hold 24,400 CE (7 days to expiry) with vega ₹4.8. Calculate the premium change for each IV scenario:
a) IV increases from 14% to 16% (+2%)
b) IV decreases from 14% to 11% (-3%)
c) IV increases from 14% to 20% (+6%)
d) IV decreases from 14% to 13% (-1%)

### Exercise 2: Complete Greek P&L Estimation
NIFTY at 24,400. You hold 24,400 CE: Delta 0.50, Gamma 0.004, Theta -₹10, Vega ₹4.8. Premium ₹100. Estimate the new premium after 1 day for each scenario:
a) NIFTY +60, IV unchanged
b) NIFTY flat, IV +2%
c) NIFTY +30, IV -2%
d) NIFTY -40, IV +3%

### Exercise 3: India VIX Observation
Track India VIX daily for one week. Note:
- The opening and closing VIX each day
- Whether NIFTY went up or down that day
- The correlation between VIX changes and NIFTY direction
- Did VIX rise when NIFTY fell? Did VIX fall when NIFTY rose?

### Exercise 4: IV Skew Analysis
Go to Sensibull's option chain. For the current week expiry, note the IV for:
- 200-point OTM Put (e.g., 24,200 PE)
- ATM Put (e.g., 24,400 PE)
- ATM Call (e.g., 24,400 CE)
- 200-point OTM Call (e.g., 24,600 CE)
Which has the highest IV? Is there a skew? How steep is it?

### Exercise 5: Event IV Tracking
Before the next major event (RBI policy, Budget, etc.), track IV daily for 5 days before and 2 days after the event. Plot the IV on a graph. Does it follow the "IV cycle" pattern from Chapter 9? How much did IV crush after the event?

---

## WEEK 15 SELF-TEST

**Q1.** What does vega measure? Write the formula.

**Q2.** Is vega positive or negative for an option buyer? Does it differ between calls and puts?

**Q3.** Which strike has the highest vega: deep ITM, ATM, or deep OTM?

**Q4.** How does vega change as expiry approaches? How is this different from theta?

**Q5.** If your option has vega ₹5.0 and IV increases by 3%, what is the premium change?

**Q6.** What is India VIX, and what does a VIX reading of 22 indicate?

**Q7.** What is the typical relationship between India VIX and NIFTY direction?

**Q8.** What is IV Percentile, and how is it different from raw IV?

**Q9.** What is the IV skew, and why do OTM puts typically have higher IV than OTM calls?

**Q10.** What is "IV crush," and when does it typically occur?

**Q11.** In the Budget Day example (Chapter 9), NIFTY rallied 70 points but the ATM call lost ₹13. Explain why using the Greeks.

**Q12.** If VIX is at 24 and you expect it to drop to 16 after an event, should you buy or sell options? Why?

---

## SELF-TEST ANSWERS

**A1.** Vega measures how much an option's premium changes for every 1% change in Implied Volatility (IV). Formula: ν = Change in Premium / Change in IV (%).

**A2.** Vega is **positive** for option buyers (both calls and puts). This means when IV rises, both call and put premiums increase. When IV falls, both decrease. Unlike delta (where calls and puts have opposite signs), vega has the same sign for both because IV affects all options in the same direction.

**A3.** **ATM** has the highest vega. This is because ATM options have the most extrinsic value, and IV changes primarily affect extrinsic value. However, vega's peak is wider than gamma's — even options 100–200 points from ATM have significant vega (unlike gamma, which drops to near zero).

**A4.** Vega **decreases** as expiry approaches. This is the **opposite** of theta (which increases near expiry). Far from expiry, a 1% IV change affects many days of expected volatility, so vega is high. Near expiry, a 1% IV change affects only hours of expected volatility, so vega is low. For a 30-day ATM option, vega might be ₹12; for a 1-day ATM option, vega might be ₹1.

**A5.** Premium change = Vega × IV change = ₹5.0 × 3 = **+₹15**. The premium increases by ₹15 per share due to the IV increase alone, regardless of NIFTY's movement.

**A6.** India VIX is the NSE's official 30-day volatility index for NIFTY, calculated from option prices. It represents the market's expected annualized volatility over the next 30 days. A VIX of 22 indicates **anxious/fearful** market conditions. Options are expensive. The market expects NIFTY to move approximately ±22% over the next year (±~1.4% per day). This is above the historical average of 15–16.

**A7.** India VIX and NIFTY typically have a **strong inverse relationship** (correlation ~-0.7 to -0.8). When NIFTY falls, VIX rises (fear increases, demand for put protection drives up IV). When NIFTY rises, VIX falls (complacency, less demand for protection). The exception is during extreme events where both can move dramatically.

**A8.** IV Percentile (IVP) tells you the percentage of trading days in the past year when IV was lower than the current IV. Raw IV is just the current number (e.g., 16%). IVP puts that number in context: 16% might be high (IVP 80%) or low (IVP 20%) depending on the historical range. IVP is more useful for trading decisions because it tells you whether options are relatively expensive or cheap.

**A9.** The IV skew is the pattern where OTM puts have higher IV than OTM calls at equal distances from ATM. It exists because: (1) Institutional investors buy OTM puts for portfolio protection, driving up demand and IV. (2) Markets crash faster than they rally, so the market prices in higher downside risk. (3) Fear of tail events (black swans) keeps OTM put IV elevated. The skew creates a "smile" shape when you plot IV across strikes.

**A10.** IV crush is the sharp drop in Implied Volatility that occurs immediately after a major event (RBI policy, Budget, elections, earnings). Before the event, uncertainty is high and IV is elevated. Once the event outcome is known, uncertainty resolves instantly and IV collapses. IV crush can destroy 20–50% of an option's extrinsic value in a few hours, even if NIFTY moves in the expected direction.

**A11.** The ATM call lost money because the **vega loss from IV crush exceeded the delta gain from the NIFTY rally**. Specifically: Delta contributed approximately +₹40 (70 points × ~0.57 avg delta). But IV dropped from 24% to 14% (-10%), and with vega ~₹5, the vega loss was approximately -₹50. Theta added another -₹3. Net: +₹40 - ₹50 - ₹3 = -₹13. The IV crush was the dominant factor.

**A12.** You should **sell** options (or avoid buying). When VIX is at 24, options are expensive (high IV). If VIX drops to 16 after the event, that's an 8% IV decrease. For an ATM option with vega ₹5, that's a ₹40 premium loss per share from vega alone. Option sellers benefit from this IV crush (they sold at high IV and buy back at low IV). Option buyers get destroyed. If you're a beginner and don't sell options yet, the best strategy is to **stay out** — close positions before the event and re-enter after IV normalizes.

---

## WEEK 15 SUMMARY CHEAT SHEET

| Concept | Key Takeaway |
|---------|-------------|
| **Vega definition** | Premium change per 1% IV change |
| **Buyer vega** | Always POSITIVE (calls AND puts) |
| **Seller vega** | Always NEGATIVE |
| **Highest vega** | ATM options (widest peak of all Greeks) |
| **Vega vs time** | DECREASES near expiry (opposite of theta) |
| **Long-dated vega** | Very high (₹10–12 for 30-day ATM) |
| **Short-dated vega** | Low (₹1–3 for weekly ATM) |
| **IV definition** | Market's expected future volatility (annualized %) |
| **IV vs HV** | IV = forward-looking (forecast). HV = backward-looking (history) |
| **India VIX** | NSE's 30-day volatility index. Fear gauge. |
| **VIX range** | 10–12 calm, 12–16 normal, 18–22 anxious, 25+ panic |
| **VIX-NIFTY** | Inverse relationship (~-0.7 correlation) |
| **IV Percentile** | % of days IV was lower. >75% = expensive, <25% = cheap |
| **IV Rank** | Position within 52-week high-low range |
| **IV Skew** | OTM puts have higher IV than OTM calls (demand for protection) |
| **IV Cycle** | Rises before events, crushes after events |
| **IV Crush** | Sharp IV drop post-event. Destroys option premium. |
| **Vega + Delta** | Best case: right direction + IV expansion (double boost) |
| **Vega - Delta** | Worst case: wrong direction + IV crush (double whammy) |
| **Event trading** | Avoid buying options at peak IV. Exit before or use ITM. |
| **VIX > 20** | Options expensive. Favor selling or stay out. |
| **VIX < 12** | Options cheap. Favor buying (if catalyst exists). |

---

## WHAT'S NEXT

**Week 16: Implied Volatility (IV) and India VIX — Applied Trading**

Now that you understand vega and IV theoretically, Week 16 will show you how to **use IV as a trading edge** in real NIFTY trading. You'll learn:

- How to read the IV column on the NSE option chain like a pro
- IV-based entry and exit timing (when to buy cheap, when to sell expensive)
- The "IV Rank trading system" for NIFTY weekly options
- How to combine IV analysis with your technical analysis framework (Weeks 5–10)
- Real case studies: Budget Day, RBI Policy, Election Day IV patterns
- Building an IV monitoring dashboard on TradingView and Sensibull

This is where theory meets practice. You'll stop being confused by "irrational" premium movements and start anticipating them.

Say **"proceed to week 16"** when you're ready!
