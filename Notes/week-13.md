# WEEK 13: THE GREEKS — GAMMA (DELTA'S ACCELERATION)

## Phase 3 — Options Theory Deep Study (Week 3 of 8)

---

## INTRODUCTION

Last week you learned that delta tells you how much your option premium changes for every 1-point move in NIFTY. You also discovered a critical fact: **delta is not constant.** When NIFTY moves, delta itself changes.

This raises an obvious question: **How fast does delta change?**

Think of it like driving a car:

| Car Analogy | Options Greek |
|-------------|--------------|
| **Position** (where you are) | Premium (current price) |
| **Speed** (how fast position changes) | Delta (how fast premium changes) |
| **Acceleration** (how fast speed changes) | **Gamma** (how fast delta changes) |
| **Fuel consumption** (speed of fuel drain) | Theta (how fast premium decays) |

If delta is the speedometer, **gamma is the accelerator pedal.**

- When you press the accelerator (high gamma), your speed (delta) increases rapidly.
- When you ease off (low gamma), your speed (delta) barely changes.

This week, you'll master gamma — the Greek that explains why ATM options explode in value during big moves, why expiry day is so volatile, and why option buyers have a built-in advantage over option sellers.

By the end of this week, you will understand the "engine" behind the asymmetric payoff that makes options so powerful.

---

## CHAPTER 1: WHAT IS GAMMA?

### 1.1 The Definition

**Gamma (Γ) measures how much delta changes for every 1-point change in the underlying asset's price (NIFTY).**

```
    ╔═══════════════════════════════════════════════════════════╗
    ║                                                           ║
    ║   GAMMA = Change in Delta / Change in Spot Price          ║
    ║                                                           ║
    ║   Γ = ΔDelta / ΔSpot                                     ║
    ║                                                           ║
    ╚═══════════════════════════════════════════════════════════╝
```

**In plain English:** If NIFTY moves 1 point, by how much does your option's delta change? That number is gamma.

### 1.2 A Simple Example

You hold a 24,400 CE with:
- Delta = 0.50
- Gamma = 0.002

**NIFTY moves from 24,400 → 24,401 (+1 point):**

```
    New Delta = Old Delta + (Gamma × Spot Change)
              = 0.50 + (0.002 × 1)
              = 0.502
    
    Premium change ≈ New Delta × 1 = ₹0.502
```

**NIFTY moves from 24,400 → 24,500 (+100 points):**

```
    Delta doesn't stay at 0.50. It increases with every point.
    
    Point 1:  Delta = 0.500 + 0.002 = 0.502
    Point 2:  Delta = 0.502 + 0.002 = 0.504
    Point 10: Delta ≈ 0.520
    Point 50: Delta ≈ 0.580
    Point 100: Delta ≈ 0.650 (approximately)
    
    The delta has increased from 0.50 to ~0.65 over 100 points.
    This is gamma at work — accelerating your delta.
```

### 1.3 Gamma Is the Second Derivative

For those who remember calculus:

```
    Premium = f(Spot)
    
    First derivative:  d(Premium)/d(Spot) = DELTA    (speed)
    Second derivative: d(Delta)/d(Spot)   = GAMMA    (acceleration)
```

You don't need calculus to trade options. But understanding that gamma is the "rate of change of the rate of change" helps you grasp why option premiums behave non-linearly.

### 1.4 Gamma Is Always Positive for Option Buyers

```
    ╔═══════════════════════════════════════════════════════════╗
    ║                                                           ║
    ║   LONG CALL → Positive Delta, Positive Gamma              ║
    ║   LONG PUT  → Negative Delta, Positive Gamma              ║
    ║                                                           ║
    ║   SHORT CALL → Negative Delta, Negative Gamma             ║
    ║   SHORT PUT  → Positive Delta, Negative Gamma             ║
    ║                                                           ║
    ╚═══════════════════════════════════════════════════════════╝
```

**Key rule:**
- **Option buyers (long)** always have **positive gamma** ✅
- **Option sellers (short)** always have **negative gamma** ❌

This is one of the most important asymmetries in options trading. Positive gamma means your delta moves in your favor as the market moves. Negative gamma means your delta moves against you.

---

## CHAPTER 2: GAMMA VALUES ACROSS THE MONEYNES SPECTRUM

### 2.1 The Gamma Curve

Gamma is NOT the same for all strikes. It follows a very specific pattern:

```
    GAMMA CURVE (NIFTY at 24,400, 3 days to expiry)
    
    Gamma
    0.006 ┤
          │          ╭──╮
    0.005 ┤        ╭╯  ╰╮        ← Peak at ATM (24,400)
          │      ╭╯      ╰╮
    0.004 ┤    ╭╯          ╰╮
          │   ╱              ╲
    0.003 ┤  ╱                ╲
          │ ╱                  ╲
    0.002 ┤╱                    ╲
          │                      ╲
    0.001 ┤                        ╲
          │                          ╲
    0.000 ┤────────────────────────────╲──
          24000  24200  24400  24600  24800
                 ← ITM    ATM    OTM →
    
    Gamma is HIGHEST at ATM and decreases as you move 
    away from ATM in either direction.
```

### 2.2 Gamma by Moneyness — The Complete Table

**NIFTY spot = 24,400. 3 days to expiry. IV = 14%.**

| Moneyness | Strike | Delta | Gamma | Interpretation |
|-----------|--------|-------|-------|----------------|
| **Deep ITM** | 24,000 CE | 0.95 | **0.0005** | Delta barely changes (already near 1.0) |
| **ITM** | 24,200 CE | 0.80 | **0.0015** | Delta changes slowly |
| **Slightly ITM** | 24,350 CE | 0.62 | **0.0035** | Delta changes moderately |
| **ATM** | 24,400 CE | 0.50 | **0.0050** | Delta changes FASTEST |
| **Slightly OTM** | 24,450 CE | 0.40 | **0.0045** | Delta changes fast |
| **OTM** | 24,600 CE | 0.18 | **0.0020** | Delta changes slowly |
| **Deep OTM** | 24,800 CE | 0.05 | **0.0005** | Delta barely changes (already near 0) |

### 2.3 Why Is Gamma Highest at ATM?

Think about it logically:

**Deep ITM (24,000 CE, delta 0.95):**
- Delta is already 0.95, very close to the maximum of 1.0
- There's almost no room for delta to increase further
- Even if NIFTY moves 100 points, delta might go from 0.95 to 0.97
- Gamma is LOW because delta has "nowhere to go"

**ATM (24,400 CE, delta 0.50):**
- Delta is right in the middle of its range (0 to 1.0)
- There's maximum room for delta to change in either direction
- A 100-point move can push delta from 0.50 to 0.70 (up) or 0.30 (down)
- Gamma is HIGH because delta is most sensitive at the inflection point

**Deep OTM (24,800 CE, delta 0.05):**
- Delta is already 0.05, very close to the minimum of 0
- There's almost no room for delta to decrease further
- Even if NIFTY moves 100 points against you, delta might go from 0.05 to 0.03
- Gamma is LOW because delta has "nowhere to go"

```
    THE "ROOM TO MOVE" ANALOGY
    
    Deep ITM (delta 0.95):
    [████████████████████████████░] 95% full
    → Only 5% room left to increase. Low gamma.
    
    ATM (delta 0.50):
    [███████████████░░░░░░░░░░░░░] 50% full
    → 50% room in both directions. Maximum gamma.
    
    Deep OTM (delta 0.05):
    [█░░░░░░░░░░░░░░░░░░░░░░░░░░] 5% full
    → Only 5% room left to decrease. Low gamma.
```

### 2.4 The Mathematical Intuition

The delta curve (from Week 12) is an S-shaped curve (sigmoid). Gamma is the **slope of the delta curve**. The slope is steepest at the middle of the S (ATM) and flattest at the top and bottom (deep ITM and deep OTM).

```
    DELTA CURVE (S-shape)        GAMMA CURVE (Bell-shape)
    
    Delta                        Gamma
    1.0 ┤       ────────         0.005 ┤      ╭──╮
        │     ╱                       │    ╭╯  ╰╮
    0.5 ┤ ──╱── ← Steepest       0.003 ┤  ╭╯    ╰╮
        │ ╱    slope here              │ ╱        ╲
    0.0 ┤╱                       0.001 ┤╱          ╲
        24000  24400  24800            24000  24400  24800
    
    Where the delta curve is steepest (ATM), 
    gamma is highest. Where delta flattens 
    (deep ITM/OTM), gamma drops to near zero.
```

---

## CHAPTER 3: GAMMA IN ACTION — REAL NIFTY EXAMPLES

### 3.1 Example 1: ATM Call on a 100-Point Rally

**Setup:**
- NIFTY: 24,400
- Position: Long 1 lot 24,400 CE
- Premium: ₹85
- Delta: 0.50
- Gamma: 0.005
- Lot size: 75

**NIFTY rallies to 24,500 (+100 points) in 2 hours.**

**Step-by-step delta evolution (simplified, 20-point increments):**

| NIFTY | Spot Change | Delta at Start | Gamma Effect | New Delta | Premium Change (this leg) |
|-------|-------------|---------------|--------------|-----------|--------------------------|
| 24,400 | — | 0.500 | — | — | — |
| 24,420 | +20 | 0.500 | +0.005×20 = +0.100 | 0.600 | 0.500 × 20 = +₹10.0 |
| 24,440 | +20 | 0.600 | +0.005×20 = +0.100 | 0.700 | 0.600 × 20 = +₹12.0 |
| 24,460 | +20 | 0.700 | +0.004×20 = +0.080 | 0.780 | 0.700 × 20 = +₹14.0 |
| 24,480 | +20 | 0.780 | +0.003×20 = +0.060 | 0.840 | 0.780 × 20 = +₹15.6 |
| 24,500 | +20 | 0.840 | +0.002×20 = +0.040 | 0.880 | 0.840 × 20 = +₹16.8 |

**Total premium change:** ₹10.0 + ₹12.0 + ₹14.0 + ₹15.6 + ₹16.8 = **+₹68.4**

**New premium:** ₹85 + ₹68.4 ≈ **₹153**

**Compare with the naive delta-only calculation:**
```
    Naive (constant delta 0.50): 0.50 × 100 = +₹50
    Actual (with gamma):          +₹68.4
    
    Gamma added an EXTRA ₹18.4 of premium!
    That's a 37% boost over the delta-only estimate.
    
    Profit per lot: ₹68.4 × 75 = ₹5,130
    (vs ₹3,750 without gamma)
```

**This is the power of positive gamma.** It accelerates your gains as the move progresses.

### 3.2 Example 2: ATM Call on a 100-Point Crash (Loss Scenario)

**Same position, but NIFTY crashes to 24,300 (-100 points).**

| NIFTY | Spot Change | Delta at Start | Gamma Effect | New Delta | Premium Change (this leg) |
|-------|-------------|---------------|--------------|-----------|--------------------------|
| 24,400 | — | 0.500 | — | — | — |
| 24,380 | -20 | 0.500 | -0.005×20 = -0.100 | 0.400 | 0.500 × (-20) = -₹10.0 |
| 24,360 | -20 | 0.400 | -0.005×20 = -0.100 | 0.300 | 0.400 × (-20) = -₹8.0 |
| 24,340 | -20 | 0.300 | -0.004×20 = -0.080 | 0.220 | 0.300 × (-20) = -₹6.0 |
| 24,320 | -20 | 0.220 | -0.003×20 = -0.060 | 0.160 | 0.220 × (-20) = -₹4.4 |
| 24,300 | -20 | 0.160 | -0.002×20 = -0.040 | 0.120 | 0.160 × (-20) = -₹3.2 |

**Total premium change:** -₹10.0 - ₹8.0 - ₹6.0 - ₹4.4 - ₹3.2 = **-₹31.6**

**New premium:** ₹85 - ₹31.6 ≈ **₹53**

**Compare with the naive delta-only calculation:**
```
    Naive (constant delta 0.50): 0.50 × (-100) = -₹50
    Actual (with gamma):          -₹31.6
    
    Gamma REDUCED your loss by ₹18.4!
    That's a 37% cushion compared to the delta-only estimate.
    
    Loss per lot: -₹31.6 × 75 = -₹2,370
    (vs -₹3,750 without gamma)
```

### 3.3 The Asymmetry Revealed

```
    GAMMA ASYMMETRY FOR OPTION BUYERS
    
    NIFTY +100 points: Premium +₹68.4 (GAIN)
    NIFTY -100 points: Premium -₹31.6 (LOSS)
    
    Same magnitude move, but the GAIN is MORE THAN DOUBLE the loss!
    
    This is the fundamental advantage of buying options:
    → Positive gamma ACCELERATES your winners
    → Positive gamma DECELERATES your losers
    
    FUTURES TRADER (gamma = 0, delta = 1.0 constant):
    → NIFTY +100: +₹7,500
    → NIFTY -100: -₹7,500
    → Symmetric. No acceleration. No cushion.
    
    OPTION BUYER (gamma = 0.005, delta variable):
    → NIFTY +100: +₹5,130 (per lot)
    → NIFTY -100: -₹2,370 (per lot)
    → Asymmetric. Winners run, losers are cushioned.
    
    The "cost" of this asymmetry is TIME DECAY (theta).
    You pay theta every day for the privilege of positive gamma.
```

---

## CHAPTER 4: GAMMA AND TIME TO EXPIRY — THE EXPLOSION

### 4.1 The Most Important Gamma Fact

> **Gamma increases dramatically as expiry approaches, especially for ATM options.**

This is the single most important thing to understand about gamma, and it explains why expiry day trading is so explosive (and dangerous).

### 4.2 Gamma at Different Times to Expiry

**24,400 CE (ATM), NIFTY at 24,400, IV = 14%:**

| Days to Expiry | Delta | Gamma | Interpretation |
|----------------|-------|-------|----------------|
| **30 days** | 0.52 | **0.0010** | Delta changes very slowly |
| **14 days** | 0.51 | **0.0018** | Delta changes moderately |
| **7 days** | 0.50 | **0.0030** | Delta changes noticeably |
| **3 days** | 0.50 | **0.0050** | Delta changes rapidly |
| **1 day** | 0.50 | **0.0100** | Delta changes VERY rapidly |
| **Expiry day (morning)** | 0.50 | **0.0200** | Delta changes EXPLOSIVELY |
| **Expiry day (last hour)** | 0.50 | **0.0500+** | Delta changes VIOLENTLY |

```
    GAMMA vs TIME TO EXPIRY (ATM Option)
    
    Gamma
    0.050 ┤                                              ╱
          │                                            ╱
    0.040 ┤                                          ╱
          │                                        ╱
    0.030 ┤                                     ╱╱
          │                                  ╱╱
    0.020 ┤                              ╱╱╱
          │                          ╱╱╱
    0.010 ┤                    ╱╱╱╱
          │              ╱╱╱╱
    0.005 ┤        ╱╱╱╱╱
          │   ╱╱╱╱
    0.001 ┤╱╱
          │
    0.000 ┤──────────────────────────────────────────────
          30    21    14     7     3     1    0
                    Days to Expiry
    
    Gamma is relatively flat until about 7 days to expiry.
    Then it ACCELERATES exponentially as expiry approaches.
    The last 24 hours see gamma spike to extreme levels.
```

### 4.3 Why Does Gamma Spike Near Expiry?

Think about the ATM option on expiry day:

- At 10:00 AM, NIFTY is at 24,400. The 24,400 CE has a 50% chance of finishing ITM. Delta = 0.50.
- At 2:00 PM, NIFTY moves to 24,420. Now there's only 1.5 hours left. The option is 20 points ITM with very little time for NIFTY to reverse. The probability of finishing ITM jumps to ~80%. Delta = 0.80.
- **A 20-point NIFTY move caused delta to jump from 0.50 to 0.80!** That's a delta change of 0.30 for a 20-point move → effective gamma = 0.30/20 = **0.015**.

Compare this to 30 days before expiry:
- A 20-point NIFTY move changes delta from 0.52 to 0.54. Delta change = 0.02 → gamma = 0.02/20 = **0.001**.

**The same 20-point move causes 15x more delta change on expiry day than 30 days before expiry.** This is the gamma explosion.

### 4.4 The Gamma Profile Across Strikes Near Expiry

**Expiry day morning, NIFTY at 24,400:**

| Strike | Delta | Gamma | What Happens if NIFTY Moves 30 Points |
|--------|-------|-------|---------------------------------------|
| 24,200 CE | 0.95 | 0.001 | Delta → 0.98. Barely changes. |
| 24,300 CE | 0.82 | 0.008 | Delta → 0.90. Moderate change. |
| 24,350 CE | 0.68 | 0.018 | Delta → 0.82. Significant change. |
| **24,400 CE** | **0.50** | **0.030** | **Delta → 0.72. MASSIVE change.** |
| 24,450 CE | 0.32 | 0.018 | Delta → 0.18. Significant change. |
| 24,500 CE | 0.18 | 0.008 | Delta → 0.10. Moderate change. |
| 24,600 CE | 0.05 | 0.001 | Delta → 0.02. Barely changes. |

```
    GAMMA PROFILE ON EXPIRY DAY
    
    Gamma
    0.030 ┤          ╭──╮
          │        ╭╯  ╰╮      ← Extremely sharp peak at ATM
    0.020 ┤      ╭╯      ╰╮
          │     ╱          ╲
    0.010 ┤   ╱              ╲
          │  ╱                ╲
    0.005 ┤ ╱                  ╲
          │╱                    ╲
    0.000 ┤──────────────────────╲──
          24200  24300  24400  24500  24600
    
    Compare with 30 days to expiry (same scale):
    
    0.030 ┤
          │
    0.020 ┤
          │
    0.010 ┤
          │          ╭────╮    ← Much wider, much lower peak
    0.005 ┤       ╭╯      ╰╮
          │     ╱            ╲
    0.000 ┤───╱────────────────╲──
          24200  24300  24400  24500  24600
    
    Near expiry: Gamma is a sharp spike at ATM.
    Far from expiry: Gamma is a wide, gentle hill.
```

---

## CHAPTER 5: GAMMA FOR OPTION BUYERS vs SELLERS

### 5.1 The Fundamental Asymmetry

```
    ╔═══════════════════════════════════════════════════════════╗
    ║                                                           ║
    ║   OPTION BUYER:  Positive Gamma (+Γ)                      ║
    ║   → Delta moves IN YOUR FAVOR as market moves             ║
    ║   → Winners accelerate, losers decelerate                 ║
    ║   → "Convex" payoff                                       ║
    ║   → You PAY for this via theta (time decay)               ║
    ║                                                           ║
    ║   OPTION SELLER: Negative Gamma (-Γ)                      ║
    ║   → Delta moves AGAINST YOU as market moves               ║
    ║   → Winners decelerate, losers accelerate                 ║
    ║   → "Concave" payoff                                      ║
    ║   → You EARN theta but risk gamma explosions              ║
    ║                                                           ║
    ╚═══════════════════════════════════════════════════════════╝
```

### 5.2 Visualizing Convex vs Concave Payoff

```
    OPTION BUYER (Positive Gamma = Convex)
    
    P&L
     ↑        ╱
     │      ╱  ← Gains accelerate (curve bends UP)
     │    ╱
     │  ╱
     │╱
     ●────────────────→ NIFTY Move
     │╲
     │  ╲
     │    ╲  ← Losses decelerate (curve bends UP)
     │      ╲
    
    The curve is "smiling" — it bends upward on both sides.
    Big moves in EITHER direction produce better-than-linear P&L.
    
    OPTION SELLER (Negative Gamma = Concave)
    
    P&L
     ↑      ╱
     │    ╱  ← Gains decelerate (curve bends DOWN)
     │  ╱
     │╱
     ●────────────────→ NIFTY Move
     │╲
     │  ╲
     │    ╲  ← Losses accelerate (curve bends DOWN)
     │      ╲
     │        ╲
    
    The curve is "frowning" — it bends downward on both sides.
    Big moves in EITHER direction produce worse-than-linear P&L.
```

### 5.3 Real Example: Buyer vs Seller on a Big Move

**Scenario:** NIFTY at 24,400. 24,400 CE at ₹85. Expiry in 2 days. NIFTY rallies 150 points to 24,550.

**Option Buyer (Long 24,400 CE):**
```
    Initial delta: 0.50, Gamma: 0.006
    Final delta: ~0.85 (increased due to gamma)
    Average delta during move: ~0.68
    Premium change: ~0.68 × 150 = +₹102
    New premium: ₹85 + ₹102 = ₹187
    Profit per lot: +₹102 × 75 = +₹7,650
    Return on investment: +120%
    
    Gamma helped: The delta increased from 0.50 to 0.85,
    capturing more and more of the move as it progressed.
```

**Option Seller (Short 24,400 CE):**
```
    Initial delta: -0.50, Gamma: -0.006
    Final delta: ~-0.85 (became MORE negative!)
    Average delta during move: ~-0.68
    Premium change: ~-0.68 × 150 = -₹102
    Loss per lot: -₹102 × 75 = -₹7,650
    
    Gamma hurt: The delta went from -0.50 to -0.85,
    meaning the seller's losses ACCELERATED as NIFTY rose.
    The more NIFTY moved against them, the MORE they lost
    per point. This is the nightmare scenario for sellers.
```

### 5.4 The Gamma-Theta Trade-Off

This is the fundamental equation of options trading:

```
    ╔═══════════════════════════════════════════════════════════╗
    ║                                                           ║
    ║   OPTION BUYER:  Pays Theta → Buys Gamma                  ║
    ║   → You lose money every day (theta decay)                ║
    ║   → In exchange, you get acceleration on big moves        ║
    ║   → Profitable when: Big move > Time decay                ║
    ║                                                           ║
    ║   OPTION SELLER:  Earns Theta → Sells Gamma               ║
    ║   → You make money every day (theta income)               ║
    ║   → In exchange, you risk acceleration on big moves       ║
    ║   → Profitable when: Time decay > Big move                ║
    ║                                                           ║
    ╚═══════════════════════════════════════════════════════════╝
```

**This is why the SEBI study shows 91% of F&O traders lose money.** Most retail traders buy options (paying theta) but the big moves they need don't happen frequently enough to overcome the daily decay. The math only works when you have an edge in timing and direction.

---

## CHAPTER 6: GAMMA RISK ON EXPIRY DAY

### 6.1 The "Gamma Bomb"

On expiry day, the combination of extreme gamma and low time value creates what traders call a **"gamma bomb"** — a situation where small NIFTY moves cause massive premium swings.

**Real scenario (Expiry day, Thursday 1:00 PM):**

```
    NIFTY: 24,400
    24,400 CE: Premium ₹15, Delta 0.50, Gamma 0.040
    
    1:05 PM: NIFTY moves to 24,415 (+15 points)
    Delta change: 0.040 × 15 = +0.60 → New delta ≈ 0.80
    Premium change: ~0.65 × 15 = +₹9.75
    New premium: ₹15 + ₹9.75 ≈ ₹25 (+65% in 5 minutes!)
    
    1:10 PM: NIFTY moves to 24,425 (+10 more points)
    Delta change: 0.025 × 10 = +0.25 → New delta ≈ 0.92
    Premium change: ~0.86 × 10 = +₹8.6
    New premium: ₹25 + ₹8.6 ≈ ₹34 (+127% in 10 minutes!)
    
    1:15 PM: NIFTY pulls back to 24,410 (-15 points)
    Delta drops from 0.92 to ~0.65
    Premium drops from ₹34 to ~₹20 (-41% in 5 minutes!)
```

**This is why expiry day afternoon is extremely dangerous.** Premiums can double and halve within minutes. The gamma is so high that even a 10–15 point NIFTY move causes massive delta shifts and premium swings.

### 6.2 The "Pin Risk" on Expiry Day

**Pin risk** occurs when NIFTY is very close to a major strike price on expiry day afternoon. The ATM option at that strike has maximum gamma, and every tick of NIFTY causes the delta to swing wildly between 0 and 1.

```
    PIN RISK (Expiry day, 2:30 PM, NIFTY at 24,398)
    
    NIFTY 24,398 → 24,400 CE delta ≈ 0.48 (slightly OTM)
    NIFTY 24,400 → 24,400 CE delta ≈ 0.50 (ATM)
    NIFTY 24,402 → 24,400 CE delta ≈ 0.65 (slightly ITM!)
    NIFTY 24,399 → 24,400 CE delta ≈ 0.40 (back to OTM!)
    
    A 4-point NIFTY move (24,398 → 24,402) caused delta 
    to swing from 0.48 to 0.65 — a 35% change!
    
    Premium swings from ₹5 to ₹12 to ₹3 in minutes.
    This is pure gamma chaos.
```

### 6.3 Practical Rules for Expiry Day Gamma

| Rule | Why |
|------|-----|
| **Don't hold ATM options through expiry afternoon** | Gamma will cause wild swings. Your premium can halve in 10 minutes. |
| **If you're in profit by 12:00 PM on expiry, book it** | Gamma risk increases exponentially after noon. |
| **Use ITM options if you must hold through expiry** | ITM options have lower gamma (delta is already high and stable). |
| **Never sell naked options on expiry day** | Negative gamma means a 50-point move can blow up your account. |
| **Reduce position size by 50% on expiry day** | The gamma risk is 5–10x higher than normal days. |

---

## CHAPTER 7: GAMMA AND POSITION MANAGEMENT

### 7.1 Position Gamma

Just like position delta (Week 12), you can calculate **position gamma** for your entire portfolio:

```
    Position Gamma = Σ (Option Gamma × Quantity × Lot Size)
```

**Example:**
```
    Long 2 lots 24,400 CE: Gamma 0.005 × 2 × 75 = +0.75
    Long 1 lot 24,400 PE:  Gamma 0.005 × 1 × 75 = +0.375
    Short 1 lot 24,500 CE: Gamma -0.003 × 1 × 75 = -0.225
    
    Position Gamma = +0.75 + 0.375 - 0.225 = +0.90
    
    Interpretation: For every 1-point NIFTY move, your 
    total position delta changes by 0.90.
```

### 7.2 Why Position Gamma Matters

**High positive position gamma:**
- Your delta changes rapidly with NIFTY moves
- Good when you expect a big directional move
- Bad when the market is choppy (delta keeps flipping, causing whipsaws)

**Low position gamma:**
- Your delta is relatively stable
- Good for steady, directional trades over multiple days
- Bad when you need quick acceleration (e.g., breakout trading)

**Negative position gamma (net short options):**
- Your delta moves AGAINST you
- Dangerous during big moves
- Only suitable for experienced sellers with hedging strategies

### 7.3 Gamma Scalping (Advanced Concept — Brief Overview)

**Gamma scalping** is a strategy used by professional traders to profit from gamma while being delta neutral.

**How it works (simplified):**
1. Create a delta-neutral position (e.g., long straddle: buy ATM CE + buy ATM PE)
2. Position delta = 0, but position gamma is positive
3. When NIFTY moves up, the call delta increases and put delta becomes less negative → net delta becomes positive
4. Sell NIFTY futures to bring delta back to zero (lock in profit from the move)
5. When NIFTY moves down, the reverse happens → buy futures to re-hedge
6. Each re-hedging locks in a small profit from the gamma-driven delta change

**Why you don't need this yet:**
- Requires significant capital (futures + options)
- Requires continuous monitoring and adjustment
- Transaction costs eat into profits for small accounts
- Relevant for Phase 4 (Strategy Development) and beyond

**For now, just understand:** Gamma scalping is how professionals monetize positive gamma in a sideways market. It's the opposite of what most retail traders do (buy options and hope for a big move).

---

## CHAPTER 8: GAMMA AND THE OPTION CHAIN

### 8.1 Finding Gamma on the Option Chain

The NSE option chain (nseindia.com/option-chain) does NOT directly show gamma. However, you can find gamma on:

- **Sensibull** (sensibull.com) → Option Chain → Click on any strike → Greeks tab shows gamma
- **Opstra** (opstra.definedge.com) → Option Analytics → Greeks
- **TradingView** → Community indicators (search "Option Greeks")
- **Zerodha Kite** → Option chain widget (limited Greeks)

### 8.2 Reading Gamma on Sensibull

**Step-by-step:**
1. Go to sensibull.com → Option Chain
2. Select NIFTY, current expiry
3. Click on the ATM strike (e.g., 24,400)
4. Look for the "Greeks" section
5. Note the Gamma value for both CE and PE

**Typical values you'll see:**

| Days to Expiry | ATM Gamma (CE) | ATM Gamma (PE) |
|----------------|----------------|----------------|
| 7 days | ~0.003 | ~0.003 |
| 3 days | ~0.005 | ~0.005 |
| 1 day | ~0.010 | ~0.010 |
| Expiry day | ~0.020–0.050 | ~0.020–0.050 |

### 8.3 Using Gamma for Strike Selection

**High gamma strikes (ATM):**
- Best for short-term trades (intraday) where you expect a quick move
- Premium will accelerate rapidly if NIFTY moves in your direction
- But also more sensitive to adverse moves and time decay

**Low gamma strikes (ITM/OTM):**
- Best for multi-day trades where you want stable delta
- Premium moves more predictably (closer to linear)
- Less affected by small NIFTY fluctuations

---

## CHAPTER 9: THE COMPLETE GREEK DASHBOARD

### 9.1 Putting Delta and Gamma Together

Now that you know both delta and gamma, you can build a more accurate picture of your trade:

```
    TRADE DASHBOARD (24,400 CE, NIFTY at 24,400, 3 days to expiry)
    
    ┌──────────────────────────────────────────────────────┐
    │  OPTION: NIFTY 24,400 CE (Current Week)              │
    │  Premium: ₹85                                        │
    │                                                      │
    │  DELTA:  +0.50   → Premium moves ₹0.50 per NIFTY pt  │
    │  GAMMA:  +0.005  → Delta changes 0.005 per NIFTY pt  │
    │                                                      │
    │  IF NIFTY +50 points:                                │
    │    New Delta ≈ 0.50 + (0.005 × 50) = 0.75            │
    │    Avg Delta ≈ (0.50 + 0.75) / 2 = 0.625             │
    │    Premium Change ≈ 0.625 × 50 = +₹31.25             │
    │    New Premium ≈ ₹116 (+37%)                         │
    │                                                      │
    │  IF NIFTY -50 points:                                │
    │    New Delta ≈ 0.50 - (0.005 × 50) = 0.25            │
    │    Avg Delta ≈ (0.50 + 0.25) / 2 = 0.375             │
    │    Premium Change ≈ 0.375 × (-50) = -₹18.75          │
    │    New Premium ≈ ₹66 (-22%)                          │
    │                                                      │
    │  ASYMMETRY: +37% gain vs -22% loss for same move     │
    │  This is the power of positive gamma.                │
    └──────────────────────────────────────────────────────┘
```

### 9.2 The Three-Greek Summary (So Far)

| Greek | Measures | Buyer | Seller | Key Insight |
|-------|----------|-------|--------|-------------|
| **Delta (Δ)** | Premium change per 1-pt NIFTY move | +0 to +1 (calls), -1 to 0 (puts) | Opposite sign | Tells you DIRECTIONAL exposure |
| **Gamma (Γ)** | Delta change per 1-pt NIFTY move | Always positive | Always negative | Tells you ACCELERATION of exposure |
| **Theta (Θ)** | Premium decay per day | Always negative | Always positive | Tells you TIME cost (Week 14) |

---

## CHAPTER 10: COMMON MISTAKES WITH GAMMA

### Mistake 1: Ignoring Gamma on Expiry Day
**Problem:** You buy ATM calls on expiry day morning at ₹20. NIFTY moves 30 points in your direction. You expect premium to go to ₹35 (delta 0.50 × 30 = ₹15). Instead, it goes to ₹50 because gamma accelerated delta from 0.50 to 0.85. You're thrilled. Then NIFTY reverses 20 points, and premium crashes from ₹50 to ₹15 in 5 minutes. You panic and sell at a loss.
**Fix:** On expiry day, gamma works both ways. It accelerates gains AND losses. Book profits quickly. Don't hold through reversals.

### Mistake 2: Assuming Linear Premium Changes
**Problem:** "My option has delta 0.50. If NIFTY moves 200 points, my premium will increase by ₹100." Reality: With gamma, the actual increase might be ₹140–150 because delta increased during the move.
**Fix:** For moves >50 points, always account for gamma. Use the average delta method: (Starting Delta + Ending Delta) / 2 × Move.

### Mistake 3: Buying Deep OTM Options Expecting Gamma to Save You
**Problem:** "The 24,700 CE has gamma 0.001. If NIFTY rallies 200 points, gamma will accelerate delta and I'll make a fortune." Reality: The gamma is too low (0.001) and the delta is too low (0.08). Even with gamma, delta only reaches ~0.28 after a 200-point move. The premium goes from ₹5 to ~₹15. Not a fortune.
**Fix:** Gamma is only powerful for ATM and near-ATM options. Deep OTM options have negligible gamma.

### Mistake 4: Not Understanding Negative Gamma as a Seller
**Problem:** You sell ATM puts thinking "I'll collect theta every day." Then NIFTY crashes 200 points. Your negative gamma accelerates your delta from +0.50 to +0.85, meaning you're losing MORE per point as the crash continues. Your ₹85 premium becomes ₹200+. You're trapped.
**Fix:** If you sell options (Phase 4+), always hedge your gamma risk. Never sell naked options without a stop-loss or a hedge.

### Mistake 5: Overtrading on Expiry Day Due to Gamma Excitement
**Problem:** You see premiums doubling and tripling on expiry day afternoon. The gamma-fueled volatility is exciting. You take 5 trades in 2 hours, winning 2 and losing 3. Net result: big loss due to transaction costs and whipsaws.
**Fix:** Expiry day gamma is a double-edged sword. Trade less, not more, on expiry day. One well-timed trade is better than five impulsive ones.

### Mistake 6: Confusing High Gamma with High Probability
**Problem:** "The ATM option has the highest gamma, so it has the highest probability of profit." Reality: Gamma measures acceleration, not probability. The ATM option has the highest gamma but only a ~50% probability of finishing ITM. A deep ITM option has low gamma but ~90% probability.
**Fix:** Use delta for probability. Use gamma for acceleration. They answer different questions.

---

## CHAPTER 11: PRACTICAL EXERCISES

### Exercise 1: Gamma Calculation Drill
NIFTY is at 24,400. You hold 24,400 CE with delta 0.50 and gamma 0.005. Calculate the approximate new delta after each NIFTY move:
a) NIFTY moves to 24,420 (+20)
b) NIFTY moves to 24,450 (+50)
c) NIFTY moves to 24,500 (+100)
d) NIFTY moves to 24,380 (-20)
e) NIFTY moves to 24,350 (-50)

### Exercise 2: Gamma Comparison
For each pair, which option has higher gamma? Explain why.
a) 24,400 CE (ATM) vs 24,200 CE (ITM), same expiry
b) 24,400 CE with 1 day to expiry vs 24,400 CE with 7 days to expiry
c) 24,400 CE (ATM) vs 24,700 CE (Deep OTM), same expiry
d) 24,400 CE when NIFTY is at 24,400 vs 24,400 CE when NIFTY is at 24,500

### Exercise 3: Premium Estimation with Gamma
NIFTY at 24,400. You buy 24,400 CE at ₹85 (delta 0.50, gamma 0.005). Estimate the premium after NIFTY moves to 24,480 (+80 points) using:
a) Delta-only method (assume constant delta 0.50)
b) Delta + Gamma method (calculate new delta, then use average delta)
c) What is the difference? How much extra profit did gamma add?

### Exercise 4: Expiry Day Gamma Observation
On the next expiry day (Thursday), open Sensibull at 10:00 AM and note the gamma of the ATM CE. Check again at 1:00 PM and 2:30 PM. How much did gamma increase as expiry approached?

### Exercise 5: Position Gamma Calculation
Calculate the position gamma for this portfolio:
- Long 2 lots 24,400 CE (gamma 0.005)
- Long 1 lot 24,400 PE (gamma 0.005)
- Short 1 lot 24,500 CE (gamma 0.003)

Is the position gamma positive or negative? What does this mean for your trade?

---

## WEEK 13 SELF-TEST

**Q1.** What does gamma measure? Write the formula.

**Q2.** Is gamma positive or negative for an option buyer? For an option seller?

**Q3.** Which strike has the highest gamma: deep ITM, ATM, or deep OTM? Why?

**Q4.** What happens to gamma as expiry approaches? Why?

**Q5.** If your 24,400 CE has delta 0.50 and gamma 0.005, what is the approximate new delta after NIFTY moves 60 points to 24,460?

**Q6.** In the 100-point rally example (Chapter 3), how much extra premium did gamma add compared to the delta-only calculation?

**Q7.** What is the "gamma-theta trade-off"?

**Q8.** Why is expiry day afternoon particularly dangerous for ATM option holders?

**Q9.** What is "pin risk"?

**Q10.** If you have a long straddle (buy ATM CE + buy ATM PE), what is your position delta and position gamma?

**Q11.** Why does an option buyer's loss decelerate as NIFTY moves against them?

**Q12.** A trader says, "I'll buy the 24,700 CE because gamma will accelerate my delta if NIFTY rallies." What's wrong with this reasoning?

---

## SELF-TEST ANSWERS

**A1.** Gamma measures how much delta changes for every 1-point change in NIFTY. Formula: Γ = Change in Delta / Change in Spot Price.

**A2.** Option buyer: **Positive gamma** (+Γ). Option seller: **Negative gamma** (-Γ). Positive gamma means delta moves in your favor as the market moves. Negative gamma means delta moves against you.

**A3.** **ATM** has the highest gamma. This is because ATM delta (0.50) is at the midpoint of its range (0 to 1.0), giving it the maximum "room to move" in either direction. Deep ITM delta is already near 1.0 (no room to increase), and deep OTM delta is near 0 (no room to decrease), so their gamma is low.

**A4.** Gamma **increases dramatically** as expiry approaches, especially for ATM options. This is because with less time remaining, even small NIFTY moves significantly change the probability of the option finishing ITM, causing rapid delta shifts. On expiry day, ATM gamma can be 10–50x higher than 30 days before expiry.

**A5.** New Delta ≈ 0.50 + (0.005 × 60) = 0.50 + 0.30 = **0.80**. The delta increased from 0.50 to approximately 0.80 as the option moved from ATM to ITM.

**A6.** Gamma added approximately **₹18.4** of extra premium. The delta-only calculation gave +₹50 (0.50 × 100), while the actual premium change with gamma was +₹68.4. The difference (₹18.4) represents the additional profit from delta acceleration. This is a 37% boost over the linear estimate.

**A7.** The gamma-theta trade-off is the fundamental exchange in options: **buyers pay theta (time decay) to get positive gamma (acceleration)**, while **sellers earn theta but take on negative gamma (acceleration risk)**. Buyers need big moves to overcome theta. Sellers need calm markets to avoid gamma explosions.

**A8.** Because ATM gamma reaches extreme levels (0.02–0.05+) on expiry day afternoon. A 10–20 point NIFTY move can cause delta to swing from 0.30 to 0.80 in minutes, making premiums double or halve rapidly. This creates massive whipsaw risk. A trade that's profitable at 2:00 PM can become a big loss by 2:15 PM.

**A9.** Pin risk occurs when NIFTY is very close to a major strike price on expiry day afternoon. The ATM option at that strike has maximum gamma, and every tick of NIFTY causes the delta to swing wildly between near-0 and near-1. Premiums become extremely volatile and unpredictable, making it very difficult to manage positions.

**A10.** Position delta = +0.50×75 + (-0.50)×75 = **0** (delta neutral). Position gamma = +0.005×75 + 0.005×75 = **+0.75** (positive gamma). This means the position has no directional bias but benefits from large moves in either direction. The positive gamma will cause delta to become positive if NIFTY rises and negative if NIFTY falls, generating profit from big moves.

**A11.** Because of positive gamma. As NIFTY moves against a call buyer (NIFTY falls), the call goes OTM and delta decreases (e.g., from 0.50 to 0.30 to 0.15). With lower delta, each additional point of adverse movement causes a smaller premium loss. The losses decelerate. This is the "cushion" that option buyers get from positive gamma.

**A12.** The 24,700 CE is deep OTM with very low gamma (~0.001) and very low delta (~0.08). Even if NIFTY rallies 200 points, gamma will only increase delta from 0.08 to ~0.28. The premium might move from ₹5 to ~₹15 — not the "fortune" the trader expects. Gamma is only powerful for ATM and near-ATM options where both delta and gamma are significant. Deep OTM options lack the "engine" (delta) for gamma to accelerate.

---

## WEEK 13 SUMMARY CHEAT SHEET

| Concept | Key Takeaway |
|---------|-------------|
| **Gamma definition** | Change in delta per 1-point NIFTY move |
| **Buyer gamma** | Always POSITIVE (delta moves in your favor) |
| **Seller gamma** | Always NEGATIVE (delta moves against you) |
| **Highest gamma** | ATM options (maximum "room" for delta to change) |
| **Lowest gamma** | Deep ITM and deep OTM (delta has nowhere to go) |
| **Gamma vs time** | Increases exponentially as expiry approaches |
| **Expiry day gamma** | 10–50x higher than normal. Causes premium explosions. |
| **Positive gamma effect** | Winners accelerate, losers decelerate (asymmetric) |
| **Negative gamma effect** | Winners decelerate, losers accelerate (dangerous) |
| **Gamma-theta trade** | Buyers pay theta for gamma. Sellers earn theta, risk gamma. |
| **Delta + Gamma estimate** | Avg Delta = (Start Δ + End Δ) / 2. Premium ≈ Avg Δ × Move |
| **Pin risk** | ATM gamma chaos on expiry day when NIFTY is near a strike |
| **Position gamma** | Sum of (gamma × qty × lot size) for all positions |
| **Gamma scalping** | Professional strategy to profit from gamma in sideways markets |
| **Strike selection** | ATM = high gamma (intraday). ITM = low gamma (multi-day). |
| **Expiry day rules** | Book profits early, reduce size, avoid ATM after noon |

---

## WHAT'S NEXT

**Week 14: The Greeks — Theta (Time Decay — Your #1 Enemy)**

Theta is the Greek that silently destroys option buyers' capital every single day. While delta and gamma are exciting (they make you money on big moves), theta is the relentless drain that works against you 24/7 — even on weekends, even when the market is closed.

You'll learn:
- How much premium you lose per day (and per hour!) to theta
- Why theta accelerates near expiry (the "theta cliff")
- The theta difference between ATM, ITM, and OTM options
- How to calculate the "breakeven move" needed to overcome theta
- Practical strategies to minimize theta damage as an option buyer
- Why theta is the option seller's best friend

If gamma is the accelerator, theta is the fuel leak. You can have the best trade setup in the world, but if theta eats your premium before the move happens, you lose.

Say **"proceed to week 14"** when you're ready!
