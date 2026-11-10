# WEEK 14: THE GREEKS — THETA (TIME DECAY — YOUR #1 ENEMY)

## Phase 3 — Options Theory Deep Study (Week 4 of 8)

---

## INTRODUCTION

Over the last two weeks, you learned about the "exciting" Greeks:

- **Delta** (Week 12): Tells you how much your premium moves when NIFTY moves. The speedometer.
- **Gamma** (Week 13): Tells you how fast delta accelerates. The accelerator pedal.

Both delta and gamma can make you money. They're the reason you buy options — the asymmetric payoff, the leverage, the explosive moves on breakout days.

But there's a third Greek that works against you **every single second of every single day**, whether the market is open or closed, whether NIFTY is moving or flat, whether you're watching the screen or sleeping:

> **THETA (Θ) — The silent killer of option buyers.**

Theta is the rate at which your option's extrinsic value decays as time passes. It is the "rent" you pay every day for the privilege of holding an option. And unlike delta and gamma, which only matter when NIFTY moves, theta matters **all the time**.

Consider this sobering reality:

> If you buy an ATM NIFTY call on Monday morning and NIFTY doesn't move at all by Thursday expiry, your option will lose **100% of its value**. Not 50%. Not 80%. **100%.** Every single rupee of premium will evaporate — purely due to theta.

This week, you will learn exactly how much theta is costing you, when it's most dangerous, and how to structure your trades to minimize its impact. By the end, you will never hold an option overnight without first calculating the theta cost.

---

## CHAPTER 1: WHAT IS THETA?

### 1.1 The Definition

**Theta (Θ) measures how much an option's premium decreases for every 1 day that passes, assuming all other factors (NIFTY price, IV, interest rates) remain constant.**

```
    ╔═══════════════════════════════════════════════════════════╗
    ║                                                           ║
    ║   THETA = Change in Option Premium / Change in Time       ║
    ║                                                           ║
    ║   Θ = ΔPremium / ΔTime (usually per day)                  ║
    ║                                                           ║
    ╚═══════════════════════════════════════════════════════════╝
```

**In plain English:** If you hold an option for one full day and NIFTY doesn't move at all, by how many rupees will your premium decrease? That number is theta.

### 1.2 Theta Sign Convention

```
    ╔═══════════════════════════════════════════════════════════╗
    ║                                                           ║
    ║   OPTION BUYER:  Theta is NEGATIVE (-Θ)                   ║
    ║   → Premium DECREASES as time passes                      ║
    ║   → Time is your ENEMY                                    ║
    ║                                                           ║
    ║   OPTION SELLER: Theta is POSITIVE (+Θ)                   ║
    ║   → Premium DECREASES for the buyer = INCREASES for seller║
    ║   → Time is your FRIEND                                   ║
    ║                                                           ║
    ╚═══════════════════════════════════════════════════════════╝
```

**Note:** When people say "theta is -₹15," they mean the option loses ₹15 of value per day. The negative sign indicates decay. When an option seller says "I'm earning theta," they mean they're collecting that ₹15 per day as the buyer's premium decays.

### 1.3 A Simple Example

You hold a 24,400 CE with:
- Premium: ₹85
- Theta: **-₹15 per day**

**If NIFTY stays at 24,400 for one full day:**

```
    Day 0 (Monday 9:15 AM):  Premium = ₹85
    Day 1 (Tuesday 9:15 AM): Premium = ₹85 - ₹15 = ₹70
    Day 2 (Wednesday 9:15 AM): Premium = ₹70 - ₹15 = ₹55
    Day 3 (Thursday 9:15 AM): Premium = ₹55 - ₹15 = ₹40
    
    After 3 days of no movement, you've lost ₹45 (53% of premium)
    purely to time decay. NIFTY hasn't moved a single point.
```

### 1.4 Theta Only Affects Extrinsic Value

This is critical. Theta decays **extrinsic value only**. Intrinsic value is unaffected by time.

```
    Premium = Intrinsic + Extrinsic
                ↑          ↑
            Unaffected   DECAYED by theta
            by theta
    
    Example: 24,200 CE when NIFTY is at 24,400
    Premium = ₹235 (Intrinsic ₹200 + Extrinsic ₹35)
    Theta = -₹8 per day
    
    After 1 day (NIFTY unchanged):
    Premium = ₹235 - ₹8 = ₹227
    Intrinsic = ₹200 (unchanged — NIFTY didn't move)
    Extrinsic = ₹35 - ₹8 = ₹27 (decayed by theta)
    
    After 4 days (NIFTY unchanged, near expiry):
    Premium ≈ ₹200 + ₹3 = ₹203
    Intrinsic = ₹200 (still unchanged)
    Extrinsic ≈ ₹3 (almost fully decayed)
    
    At expiry:
    Premium = ₹200 (intrinsic only)
    Extrinsic = ₹0 (fully decayed)
```

**Key insight:** ITM options have less extrinsic to decay, so theta hurts them less. ATM and OTM options are 100% extrinsic, so theta destroys them completely.

---

## CHAPTER 2: THETA VALUES ACROSS THE MONEYNES SPECTRUM

### 2.1 The Theta Curve

Like gamma, theta is highest at ATM and decreases as you move away. But the shape is slightly different:

```
    THETA CURVE (NIFTY at 24,400, 3 days to expiry)
    
    |Theta|
    (absolute
     value)
    ₹18 ┤
        │          ╭────╮
    ₹15 ┤        ╭╯    ╰╮        ← Peak at ATM (24,400)
        │      ╭╯        ╰╮
    ₹12 ┤    ╭╯            ╰╮
        │   ╱                ╲
     ₹8 ┤  ╱                  ╲
        │ ╱                    ╲
     ₹5 ┤╱                      ╲
        │                        ╲
     ₹2 ┤                          ╲
        │                            ╲
     ₹0 ┤──────────────────────────────╲──
        24000  24200  24400  24600  24800
               ← ITM    ATM    OTM →
    
    Theta is HIGHEST at ATM (maximum extrinsic to decay).
    Theta decreases for ITM and OTM (less extrinsic).
```

### 2.2 Theta by Moneyness — The Complete Table

**NIFTY spot = 24,400. 3 days to expiry. IV = 14%.**

| Moneyness | Strike | Premium | Intrinsic | Extrinsic | Theta (per day) | % of Extrinsic Lost/Day |
|-----------|--------|---------|-----------|-----------|----------------|------------------------|
| **Deep ITM** | 24,000 CE | ₹425 | ₹400 | ₹25 | **-₹5** | 20% |
| **ITM** | 24,200 CE | ₹235 | ₹200 | ₹35 | **-₹8** | 23% |
| **Slightly ITM** | 24,350 CE | ₹95 | ₹50 | ₹45 | **-₹12** | 27% |
| **ATM** | 24,400 CE | ₹85 | ₹0 | ₹85 | **-₹16** | 19% |
| **Slightly OTM** | 24,450 CE | ₹62 | ₹0 | ₹62 | **-₹14** | 23% |
| **OTM** | 24,600 CE | ₹25 | ₹0 | ₹25 | **-₹8** | 32% |
| **Deep OTM** | 24,800 CE | ₹5 | ₹0 | ₹5 | **-₹2** | 40% |

### 2.3 Key Observations

**Observation 1: ATM options have the highest absolute theta.**

The 24,400 CE loses ₹16 per day — the most of any strike. This is because it has the most extrinsic value (₹85) to decay. More extrinsic = more daily decay.

**Observation 2: Deep OTM options have the highest theta as a PERCENTAGE of extrinsic.**

The 24,800 CE loses only ₹2 per day in absolute terms, but that ₹2 represents **40% of its total extrinsic value**. The option is decaying proportionally faster than the ATM option (19% per day). This is why deep OTM options near expiry are essentially worthless — they decay to zero at an accelerating rate.

**Observation 3: ITM options have moderate theta.**

The 24,200 CE loses ₹8 per day, which is half the ATM theta. This is because it has less extrinsic (₹35 vs ₹85). The intrinsic portion (₹200) is immune to theta.

**Observation 4: Theta is NOT symmetric around ATM.**

Notice that the 24,350 CE (slightly ITM, theta -₹12) has lower theta than the 24,450 CE (slightly OTM, theta -₹14), even though they're equidistant from ATM. This is because the slightly OTM option is 100% extrinsic while the slightly ITM option has some intrinsic protection.

---

## CHAPTER 3: THETA AND TIME TO EXPIRY — THE THETA CLIFF

### 3.1 The Most Important Theta Fact

> **Theta is NOT linear. It accelerates as expiry approaches.**

An option with 30 days to expiry might lose ₹3 per day. The same option with 3 days to expiry might lose ₹15 per day. The same option on expiry day might lose ₹30+ per day (in the final hours).

### 3.2 The Theta Decay Curve

**24,400 CE (ATM), NIFTY at 24,400, IV = 14%:**

| Days to Expiry | Extrinsic Value | Daily Theta | Cumulative Decay |
|----------------|----------------|-------------|------------------|
| **30 days** | ₹180 | **-₹3** | Slow |
| **21 days** | ₹155 | **-₹4** | Still slow |
| **14 days** | ₹130 | **-₹6** | Picking up |
| **7 days** | ₹100 | **-₹10** | Noticeable |
| **5 days** | ₹85 | **-₹13** | Accelerating |
| **3 days** | ₹65 | **-₹16** | Fast |
| **2 days** | ₹45 | **-₹20** | Very fast |
| **1 day** | ₹25 | **-₹25** | Extreme |
| **Expiry day** | ₹10 | **-₹10/hour** | Violent |
| **Expiry 3:30 PM** | ₹0 | — | **Dead** |

```
    EXTRINSIC VALUE DECAY OVER TIME (ATM Option)
    
    Extrinsic
    Value
    ₹180 ┤╲
         │  ╲
    ₹150 ┤    ╲
         │      ╲
    ₹120 ┤        ╲
         │          ╲
    ₹100 ┤            ╲
         │              ╲
     ₹80 ┤                ╲
         │                  ╲
     ₹60 ┤                    ╲╲
         │                       ╲╲
     ₹40 ┤                         ╲╲╲
         │                             ╲╲╲
     ₹20 ┤                                ╲╲╲╲
         │                                     ╲╲╲
      ₹0 ┤─────────────────────────────────────────╲
         30   25   20   15   10   7   5   3   1   0
                       Days to Expiry
    
    The curve is CONVEX — it starts flat and steepens 
    dramatically in the last 7 days.
    
    Days 30-15: Lose ~₹50 in 15 days (₹3.3/day average)
    Days 15-7:  Lose ~₹30 in 8 days (₹3.75/day average)
    Days 7-3:   Lose ~₹35 in 4 days (₹8.75/day average)
    Days 3-0:   Lose ~₹65 in 3 days (₹21.7/day average!)
    
    The last 3 days destroy more value than the first 15 days!
```

### 3.3 The "Theta Cliff" Visualization

```
    DAILY THETA vs DAYS TO EXPIRY
    
    |Theta|
    per day
    ₹25 ┤                                          ╱
        │                                        ╱
    ₹20 ┤                                     ╱╱
        │                                  ╱╱
    ₹15 ┤                              ╱╱╱
        │                          ╱╱╱
    ₹10 ┤                    ╱╱╱╱
        │              ╱╱╱╱
     ₹5 ┤        ╱╱╱╱╱
        │   ╱╱╱╱
     ₹2 ┤╱╱
        │
     ₹0 ┤──────────────────────────────────────────────
        30   25   20   15   10   7   5   3   1   0
                       Days to Expiry
    
    The theta curve looks like a CLIFF — relatively flat 
    until about 7-10 days, then a steep drop-off.
    
    This is why WEEKLY options (5-7 days) are in the 
    steepest part of the theta curve from day one.
```

### 3.4 Why Theta Accelerates Near Expiry

Think of it as a **probability collapse**:

- **30 days to expiry:** NIFTY has 30 days to move. The ATM option has a ~50% chance of finishing ITM. There's a lot of uncertainty, so the market assigns high extrinsic value. Each passing day removes only 1/30th of the time, so the probability doesn't change much. Theta is low.

- **3 days to expiry:** NIFTY has only 3 days. The probability of a big move is shrinking rapidly. Each passing day removes 1/3rd of the remaining time. The uncertainty collapses quickly. Theta is high.

- **Expiry day:** NIFTY has hours. The probability is crystallizing — the option is either going to finish ITM or OTM, and we'll know soon. The remaining uncertainty evaporates by the minute. Theta is extreme.

```
    PROBABILITY COLLAPSE ANALOGY
    
    30 days out: "Will it rain sometime this month?"
    → Hard to say. High uncertainty. High extrinsic.
    → Each day passing doesn't change the answer much.
    
    3 days out: "Will it rain this week?"
    → Getting clearer. Checking forecasts. Uncertainty dropping.
    → Each day passing significantly changes the probability.
    
    Expiry day: "Will it rain in the next 2 hours?"
    → Look out the window. You can almost see the answer.
    → Uncertainty collapsing by the minute.
```

---

## CHAPTER 4: THETA IN ACTION — REAL NIFTY EXAMPLES

### 4.1 Example 1: The Flat Week (Worst Case for Buyers)

**Setup:**
- Monday 9:15 AM: NIFTY at 24,400
- You buy: 24,400 CE at ₹85 (ATM, current week expiry Thursday)
- Theta: -₹16 per day (average over the week)
- NIFTY stays between 24,380 and 24,420 all week (essentially flat)

| Day | NIFTY | Premium | Daily Loss | Cumulative Loss |
|-----|-------|---------|------------|-----------------|
| Mon 9:15 | 24,400 | ₹85 | — | — |
| Tue 9:15 | 24,405 | ₹69 | -₹16 | -₹16 |
| Wed 9:15 | 24,395 | ₹49 | -₹20 | -₹36 |
| Thu 9:15 | 24,410 | ₹22 | -₹27 | -₹63 |
| Thu 3:30 | 24,405 | ₹5 | -₹17 | -₹80 |

**Result:** NIFTY moved a net +5 points over 4 days. Your premium went from ₹85 to ₹5. **You lost ₹80 per share (94%) despite being directionally correct.**

**Loss per lot:** ₹80 × 75 = **₹6,000**

This is the nightmare scenario for option buyers. You were right about direction (NIFTY went up slightly), but the move was too small and too slow to overcome theta.

### 4.2 Example 2: The Quick Move (Best Case for Buyers)

**Same setup, but NIFTY rallies 100 points on Monday morning:**

| Time | NIFTY | Premium | Change | What Happened |
|------|-------|---------|--------|---------------|
| Mon 9:15 | 24,400 | ₹85 | — | Entry |
| Mon 11:00 | 24,500 | ₹155 | +₹70 | Delta + Gamma drove premium up |
| Mon 11:00 | 24,500 | ₹155 | -₹0 | Theta so far today: negligible (~₹1) |

**Result:** You made ₹70 per share in 2 hours. Theta cost you approximately ₹1 (1/6th of a day's theta). **Delta and gamma overwhelmed theta.**

**Profit per lot:** ₹70 × 75 = **₹5,250**

**Key lesson:** Theta is a slow leak. Delta and gamma are fast movers. If the directional move happens quickly, theta is irrelevant. Theta only destroys you when the move is slow or doesn't happen.

### 4.3 Example 3: The Slow Grind (Theta Dominates)

**Setup:**
- Monday 9:15 AM: NIFTY at 24,400
- You buy: 24,400 CE at ₹85
- NIFTY grinds up 10 points per day (slow uptrend)

| Day | NIFTY | Intrinsic | Extrinsic | Premium | Daily P&L |
|-----|-------|-----------|-----------|---------|-----------|
| Mon | 24,400 | ₹0 | ₹85 | ₹85 | — |
| Tue | 24,410 | ₹10 | ₹67 | ₹77 | -₹8 |
| Wed | 24,420 | ₹20 | ₹47 | ₹67 | -₹10 |
| Thu | 24,430 | ₹30 | ₹18 | ₹48 | -₹19 |
| Thu 3:30 | 24,430 | ₹30 | ₹0 | ₹30 | -₹18 |

**Result:** NIFTY moved +30 points in your direction over 4 days. Your intrinsic value increased by ₹30. But your extrinsic value decayed by ₹85. **Net loss: -₹55 per share.**

**The math:**
```
    Intrinsic gain: +₹30 (from NIFTY moving 30 points)
    Extrinsic loss: -₹85 (from 4 days of theta decay)
    Net: +₹30 - ₹85 = -₹55
    
    You were RIGHT about direction but WRONG about speed.
    The move was too slow to overcome theta.
```

### 4.4 The Speed vs Decay Race

```
    THE RACE: DELTA vs THETA
    
    Scenario A: Fast move (100 pts in 2 hours)
    Delta gain:  +₹65 (including gamma boost)
    Theta loss:  -₹1  (only 2 hours of decay)
    Net:         +₹64 ✅ WINNER: Delta
    
    Scenario B: Moderate move (50 pts in 1 day)
    Delta gain:  +₹30
    Theta loss:  -₹16
    Net:         +₹14 ✅ WINNER: Delta (barely)
    
    Scenario C: Slow move (30 pts in 4 days)
    Delta gain:  +₹30
    Theta loss:  -₹85
    Net:         -₹55 ❌ WINNER: Theta
    
    Scenario D: No move (0 pts in 4 days)
    Delta gain:  +₹0
    Theta loss:  -₹85
    Net:         -₹85 ❌ WINNER: Theta (total destruction)
    
    THE LESSON: As an option buyer, you need SPEED.
    A 30-point move in 2 hours is profitable.
    A 30-point move in 4 days is a loss.
    The magnitude matters less than the SPEED.
```

---

## CHAPTER 5: THE THETA BURN — DAILY AND HOURLY DECAY

### 5.1 Daily Theta Breakdown

When we say "theta is -₹16 per day," that decay doesn't happen all at once at the end of the day. It's distributed across the 24-hour period. But it's not evenly distributed either.

**Approximate theta distribution for a trading day:**

| Period | Hours | % of Daily Theta | Approx. Decay |
|--------|-------|-----------------|---------------|
| **Overnight (3:30 PM – 9:15 AM)** | 17.75 hrs | ~40% | -₹6.4 |
| **Market hours (9:15 AM – 3:30 PM)** | 6.25 hrs | ~60% | -₹9.6 |
| **Total** | 24 hrs | 100% | -₹16.0 |

**Why is market-hours theta higher?** Because during market hours, IV fluctuates, volume is active, and the option is being continuously repriced. The "effective" time decay is faster when the market is open.

### 5.2 Hourly Theta on Expiry Day

On expiry day, theta becomes so extreme that it's more useful to think in terms of **hourly decay**:

**Expiry day (Thursday), 24,400 CE, NIFTY at 24,400:**

| Time | Hours Left | Premium | Hourly Theta | Cumulative Decay |
|------|-----------|---------|-------------|------------------|
| 9:15 AM | 6.25 hrs | ₹25 | — | — |
| 10:15 AM | 5.25 hrs | ₹21 | -₹4/hr | -₹4 |
| 11:15 AM | 4.25 hrs | ₹16 | -₹5/hr | -₹9 |
| 12:15 PM | 3.25 hrs | ₹11 | -₹5/hr | -₹14 |
| 1:15 PM | 2.25 hrs | ₹7 | -₹4/hr | -₹18 |
| 2:15 PM | 1.25 hrs | ₹3 | -₹4/hr | -₹22 |
| 3:00 PM | 0.5 hrs | ₹1 | -₹4/hr | -₹24 |
| 3:30 PM | 0 hrs | ₹0 | — | -₹25 |

**On expiry day, you're losing approximately ₹4–5 per hour on an ATM option.** That's ₹300–375 per lot per hour. Every hour you hold without NIFTY moving in your direction, you lose that amount.

### 5.3 Weekend Theta Decay

**Does theta decay over the weekend?** YES.

Options don't pause their time decay just because the market is closed. The weekend (Saturday + Sunday) represents 2 days of theta decay that hits your position when the market opens on Monday.

**How it works:**
- Friday close: Your option has 5 days to expiry (next Thursday)
- Monday open: Your option now has 3 days to expiry
- The 2 weekend days of theta were "priced in" over Friday afternoon and Monday morning

**Approximate weekend theta impact:**
```
    Friday 3:30 PM: 24,400 CE at ₹65 (5 days to expiry)
    Monday 9:15 AM: 24,400 CE at ₹52 (3 days to expiry)
    
    Weekend decay: ~₹13 (2 days × ~₹6.5/day)
    
    This decay is already reflected in Monday's opening price.
    You don't see it happen in real-time, but it's there.
```

**Practical implication:** If you hold ATM options over the weekend, you'll open Monday morning with a lower premium even if NIFTY hasn't moved. This is the "weekend gap" in option premiums. To avoid this, close ATM positions on Friday afternoon if you don't expect a big Monday move.

---

## CHAPTER 6: THETA vs GAMMA — THE FUNDAMENTAL TRADE-OFF

### 6.1 The Seesaw Relationship

Theta and gamma are inversely related. This is the most important relationship in options:

```
    ╔═══════════════════════════════════════════════════════════╗
    ║                                                           ║
    ║   HIGH GAMMA ↔ HIGH THETA (near ATM, near expiry)        ║
    ║   LOW GAMMA  ↔ LOW THETA  (deep ITM/OTM, far from expiry)║
    ║                                                           ║
    ║   You CANNOT have high gamma without paying high theta.   ║
    ║   They are two sides of the same coin.                    ║
    ║                                                           ║
    ╚═══════════════════════════════════════════════════════════╝
```

### 6.2 The Trade-Off Table

| Option Type | Gamma | Theta | What You Get | What You Pay |
|-------------|-------|-------|-------------|-------------|
| **ATM, near expiry** | Very High | Very High | Explosive premium moves | Rapid time decay |
| **ATM, far from expiry** | Moderate | Low | Moderate acceleration | Slow time decay |
| **ITM, near expiry** | Low | Moderate | Stable delta, less acceleration | Moderate decay |
| **ITM, far from expiry** | Very Low | Very Low | Futures-like behavior | Minimal decay |
| **OTM, near expiry** | Low | High (as % of premium) | Cheap lottery ticket | Rapid decay to zero |

### 6.3 The Mathematical Relationship

For ATM options, there's an approximate relationship:

```
    Theta ≈ -½ × Gamma × Spot² × IV²
    
    (Simplified Black-Scholes relationship)
    
    This shows that theta is proportional to gamma.
    Higher gamma → Higher theta. Always.
```

**What this means practically:** You cannot get the "acceleration" benefit of gamma without paying the "rent" of theta. The market is efficient — it charges you for the convexity you receive.

### 6.4 The Option Buyer's Dilemma

```
    THE DILEMMA:
    
    "I want high gamma so my premium explodes on big moves."
    → Buy ATM options near expiry
    → But theta will eat ₹15-25 per day
    → If the big move doesn't happen in 1-2 days, you lose
    
    "I want low theta so I don't bleed money every day."
    → Buy ITM options far from expiry
    → But gamma is low, so premium moves slowly
    → You need a bigger NIFTY move to make the same profit
    
    THE SOLUTION: Match your option choice to your TIME HORIZON.
    
    Expect move in 2-4 hours? → ATM current week (high gamma, 
    theta doesn't matter over hours)
    
    Expect move in 1-2 days? → Slightly ITM current week 
    (moderate gamma, manageable theta)
    
    Expect move in 3-5 days? → ITM next week (low gamma, 
    low theta, time to wait for the move)
```

---

## CHAPTER 7: BREAKEVEN ANALYSIS — HOW MUCH MUST NIFTY MOVE?

### 7.1 The Breakeven Question

Before entering any option trade, you should ask:

> **"How many points must NIFTY move in my direction, and how quickly, for me to break even after theta decay?"**

This is the **breakeven move**, and it's the most practical application of theta.

### 7.2 Breakeven Formula (Simplified)

```
    Breakeven Move (per day) = Daily Theta / Delta
    
    This tells you how many points NIFTY must move per day 
    just to offset the daily time decay.
```

### 7.3 Breakeven Examples

**Example 1: ATM Call (24,400 CE)**
```
    Delta: 0.50
    Theta: -₹16 per day
    
    Breakeven = ₹16 / 0.50 = 32 points per day
    
    NIFTY must move at least 32 points per day in your 
    direction just to break even. If NIFTY moves 20 points 
    per day, you lose money despite being directionally correct.
```

**Example 2: ITM Call (24,300 CE)**
```
    Delta: 0.70
    Theta: -₹10 per day
    
    Breakeven = ₹10 / 0.70 = 14 points per day
    
    NIFTY must move only 14 points per day to break even.
    Much more achievable than the ATM's 32 points.
```

**Example 3: OTM Call (24,550 CE)**
```
    Delta: 0.22
    Theta: -₹10 per day
    
    Breakeven = ₹10 / 0.22 = 45 points per day
    
    NIFTY must move 45 points per day to break even!
    This is very difficult to sustain. OTM options require 
    large, fast moves to overcome their low delta and high theta.
```

### 7.4 Breakeven Comparison Table

| Strike | Delta | Theta/Day | Breakeven Move/Day | Difficulty |
|--------|-------|-----------|-------------------|------------|
| 24,200 CE (ITM) | 0.80 | -₹8 | **10 points** | Easy ✅ |
| 24,300 CE (ITM) | 0.70 | -₹10 | **14 points** | Easy ✅ |
| 24,350 CE (Slightly ITM) | 0.62 | -₹12 | **19 points** | Moderate |
| 24,400 CE (ATM) | 0.50 | -₹16 | **32 points** | Moderate-Hard |
| 24,450 CE (Slightly OTM) | 0.40 | -₹14 | **35 points** | Hard |
| 24,550 CE (OTM) | 0.22 | -₹10 | **45 points** | Very Hard ⚠️ |
| 24,700 CE (Deep OTM) | 0.08 | -₹4 | **50 points** | Nearly Impossible ❌ |

**Key insight:** ITM options have the LOWEST breakeven move because they combine high delta (captures more of NIFTY's move) with moderate theta (less extrinsic to decay). This is why ITM options are better for multi-day trades.

### 7.5 Breakeven Over the Full Trade Duration

**For a 3-day trade:**

```
    ATM Call (24,400 CE):
    Total theta over 3 days ≈ ₹16 + ₹20 + ₹25 = ₹61
    Breakeven move = ₹61 / 0.50 = 122 points over 3 days
    → NIFTY must move 122 points in 3 days to break even
    
    ITM Call (24,300 CE):
    Total theta over 3 days ≈ ₹10 + ₹12 + ₹15 = ₹37
    Breakeven move = ₹37 / 0.70 = 53 points over 3 days
    → NIFTY must move only 53 points in 3 days to break even
    
    The ITM option requires less than HALF the move to break even.
```

---

## CHAPTER 8: THETA ON EXPIRY DAY — THE FINAL HOURS

### 8.1 The Expiry Day Theta Explosion

On expiry day, theta is no longer measured per day — it's measured per **hour** and even per **minute**.

**24,400 CE (ATM), Expiry Day Thursday, NIFTY at 24,400:**

| Time | Premium | Minutes Left | Theta per Minute |
|------|---------|-------------|-----------------|
| 9:15 AM | ₹25 | 375 min | -₹0.07/min |
| 11:00 AM | ₹18 | 270 min | -₹0.07/min |
| 1:00 PM | ₹12 | 150 min | -₹0.08/min |
| 2:00 PM | ₹7 | 90 min | -₹0.08/min |
| 2:30 PM | ₹4 | 60 min | -₹0.07/min |
| 3:00 PM | ₹2 | 30 min | -₹0.07/min |
| 3:15 PM | ₹1 | 15 min | -₹0.07/min |
| 3:30 PM | ₹0 | 0 min | **Dead** |

**Total decay on expiry day: ₹25 in 6.25 hours = ₹4 per hour**

### 8.2 The "Theta Clock" on Expiry Day

Think of expiry day as a ticking clock. Every minute that passes without NIFTY moving in your direction, your premium is shrinking.

```
    EXPIRY DAY THETA CLOCK (ATM Option)
    
    9:15 AM   █████████████████████████  ₹25 (100%)
    10:15 AM  ████████████████████       ₹21 (84%)
    11:15 AM  ████████████████           ₹16 (64%)
    12:15 PM  ████████████               ₹11 (44%)
    1:15 PM   ████████                   ₹7  (28%)
    2:15 PM   ████                       ₹3  (12%)
    3:00 PM   ██                         ₹1  (4%)
    3:30 PM   ░                          ₹0  (0%)
    
    By 1:00 PM, you've lost more than half your premium 
    to theta alone. By 2:15 PM, 88% is gone.
```

### 8.3 Practical Expiry Day Rules

| Time | Rule | Why |
|------|------|-----|
| **9:15–10:30 AM** | Best window for new entries | Theta is still moderate, plenty of time for moves |
| **10:30–12:00 PM** | Manage existing positions | Theta accelerating, tighten stop-losses |
| **12:00–1:00 PM** | Book profits if in green | Theta is now eating ₹4-5/hour. Don't get greedy. |
| **1:00–2:00 PM** | Exit losing positions | Theta will destroy remaining premium in 2 hours |
| **2:00–3:00 PM** | Only ITM options survive | OTM options are essentially dead (delta ~0, theta ~100%) |
| **3:00–3:30 PM** | Settlement period | Don't trade. Premiums are erratic due to gamma + theta |

---

## CHAPTER 9: PRACTICAL STRATEGIES TO MINIMIZE THETA DAMAGE

### 9.1 Strategy 1: Trade Intraday, Not Overnight

**The simplest and most effective theta defense.**

If you enter a trade at 10:00 AM and exit by 2:30 PM, you've experienced only ~4.5 hours of theta decay — roughly 18% of a full day's theta.

```
    OVERNIGHT vs INTRADAY THETA
    
    Intraday trade (10:00 AM – 2:00 PM, 4 hours):
    Theta cost ≈ ₹16 × (4/24) = ₹2.7 per share
    On ₹85 premium, that's 3.2% decay
    
    Overnight trade (Mon 10:00 AM – Tue 10:00 AM, 24 hours):
    Theta cost ≈ ₹16 per share
    On ₹85 premium, that's 18.8% decay
    
    The overnight trade costs 6x more in theta!
```

**When to hold overnight:**
- You have a strong multi-day thesis (e.g., breakout above weekly resistance)
- You're holding ITM options (lower theta)
- The move hasn't completed yet and you expect continuation

**When to close before 3:30 PM:**
- You're holding ATM or OTM options
- The trade hasn't moved in your direction
- It's Wednesday or Thursday (theta accelerating)
- You're unsure about overnight global cues

### 9.2 Strategy 2: Buy ITM Options for Multi-Day Trades

As shown in the breakeven analysis, ITM options have significantly lower theta relative to their delta.

```
    THETA COST COMPARISON (3-day hold, NIFTY flat):
    
    ATM 24,400 CE: ₹85 → ₹22 (lost ₹63, 74% decay)
    ITM 24,300 CE: ₹130 → ₹93 (lost ₹37, 28% decay)
    Deep ITM 24,200 CE: ₹235 → ₹211 (lost ₹24, 10% decay)
    
    The deep ITM option lost only 10% of its value over 3 days 
    of flat NIFTY, while the ATM option lost 74%.
```

### 9.3 Strategy 3: Use Next Week's Expiry Instead of Current Week

If it's Wednesday or Thursday and you expect a move next week, buy **next week's** options instead of current week's.

```
    THETA COMPARISON (Wednesday, NIFTY at 24,400):
    
    Current week 24,400 CE (1 day to expiry):
    Premium: ₹35, Theta: -₹25/day
    → Will lose 71% of value in one day!
    
    Next week 24,400 CE (8 days to expiry):
    Premium: ₹105, Theta: -₹8/day
    → Will lose only 7.6% of value in one day
    
    Yes, next week's option is more expensive (₹105 vs ₹35).
    But it retains its value much better. The extra ₹70 you 
    pay buys you 7 additional days of time.
```

### 9.4 Strategy 4: Avoid Holding ATM Options Over the Weekend

As discussed in Chapter 5, weekend theta is real. If you hold ATM options from Friday to Monday, you'll lose ~2 days of theta.

```
    Friday 3:30 PM: 24,400 CE at ₹65
    Monday 9:15 AM: 24,400 CE at ₹52 (NIFTY unchanged)
    
    Weekend theta cost: ₹13 (20% of premium)
    
    If you had closed on Friday and reopened on Monday, 
    you'd have saved that ₹13 per share (₹975 per lot).
```

### 9.5 Strategy 5: Scale In, Don't Hold and Hope

Instead of buying your full position at once and holding through theta decay, scale in as the setup develops:

```
    BAD APPROACH:
    Monday: Buy 2 lots 24,400 CE at ₹85
    Tuesday: NIFTY flat. Premium ₹69. Holding...
    Wednesday: NIFTY flat. Premium ₹49. Still holding...
    Thursday: NIFTY rallies. Premium ₹60. You exit.
    Result: Lost ₹25 per share despite the rally.
    
    BETTER APPROACH:
    Monday: Buy 1 lot 24,400 CE at ₹85 (half position)
    Tuesday: NIFTY flat. Premium ₹69. Exit at ₹69 (-₹16)
    Wednesday: Setup re-forms. Buy 2 lots at ₹55
    Thursday: NIFTY rallies. Premium ₹95. Exit.
    Result: -₹16 on first trade, +₹40 × 2 on second = +₹64 net
```

### 9.6 Strategy 6: Use Spreads to Reduce Theta

**Bull Call Spread** (Buy ATM CE + Sell OTM CE):
- The short OTM CE earns theta, partially offsetting the long ATM CE's theta
- Net theta is lower than a naked long call
- Trade-off: Your maximum profit is capped

```
    NAKED LONG CALL:
    Long 24,400 CE: Theta -₹16/day
    Net theta: -₹16/day
    
    BULL CALL SPREAD:
    Long 24,400 CE: Theta -₹16/day
    Short 24,600 CE: Theta +₹8/day
    Net theta: -₹8/day (50% reduction!)
    
    You still pay theta, but at half the rate.
    The cost is that your profit is capped at the 24,600 strike.
```

---

## CHAPTER 10: THETA AND IMPLIED VOLATILITY

### 10.1 The IV-Theta Relationship

Higher IV means higher extrinsic value, which means higher theta. When IV is elevated, options are "expensive" and decay faster.

**24,400 CE (ATM), 3 days to expiry:**

| IV | Extrinsic | Theta/Day | Breakeven Move/Day |
|----|-----------|-----------|-------------------|
| 10% (Low) | ₹60 | -₹11 | 22 points |
| 14% (Normal) | ₹85 | -₹16 | 32 points |
| 18% (High) | ₹110 | -₹21 | 42 points |
| 25% (Very High) | ₹150 | -₹30 | 60 points |

**Practical implication:** When IV is high (e.g., before RBI policy, Budget, elections), ATM options decay much faster. You need a bigger NIFTY move to break even. This is why buying options before major events is risky — even if NIFTY moves, the "IV crush" after the event can wipe out your gains (more on this in Week 16).

### 10.2 IV Crush and Theta

After a major event, IV drops sharply ("IV crush"). This causes extrinsic value to collapse, which accelerates theta-like decay even if time hasn't passed.

```
    BEFORE RBI POLICY (Wednesday 1:00 PM):
    24,400 CE: Premium ₹120 (IV 22%, high extrinsic)
    
    AFTER RBI POLICY (Wednesday 3:00 PM):
    24,400 CE: Premium ₹75 (IV 14%, normal extrinsic)
    
    NIFTY moved only 10 points, but premium dropped ₹45!
    The IV crush destroyed ₹45 of extrinsic value in 2 hours.
    This is equivalent to ~3 days of normal theta decay 
    compressed into 2 hours.
```

---

## CHAPTER 11: COMMON MISTAKES

### Mistake 1: Holding ATM Options Over Multiple Days Without a Move
**Problem:** You buy ATM calls on Monday expecting a breakout. NIFTY stays flat Tuesday and Wednesday. By Thursday, your premium has lost 70% to theta. NIFTY finally breaks out Thursday afternoon, but your premium barely recovers because there's no extrinsic left.
**Fix:** If NIFTY doesn't move within 1–2 days of buying ATM options, EXIT. Don't hold and hope. The theta clock is ticking.

### Mistake 2: Ignoring Theta When Calculating Breakeven
**Problem:** "I bought 24,400 CE at ₹85. NIFTY is at 24,400. So my breakeven is 24,485 (strike + premium)." Reality: By expiry, theta will have reduced the extrinsic to zero, so your breakeven at expiry is actually 24,400 + intrinsic only. But during the trade, you need NIFTY to move MORE than 85 points to overcome theta decay.
**Fix:** Use the breakeven formula: Breakeven Move = Total Expected Theta / Delta.

### Mistake 3: Buying Current Week Options on Wednesday/Thursday
**Problem:** It's Wednesday. You buy current week ATM calls. Theta is -₹20/day. By Thursday afternoon, your premium has halved even if NIFTY moved 20 points in your direction.
**Fix:** On Wednesday/Thursday, buy NEXT week's options if your thesis extends beyond Thursday. The extra premium buys you time.

### Mistake 4: Thinking "Cheap" OTM Options Have Low Theta
**Problem:** "The 24,700 CE is only ₹5. Theta can't hurt me much on a ₹5 option." Reality: Theta is -₹2/day, which is 40% of the premium per day. In 2 days, the option loses 80% of its value. It's "cheap" because it's decaying rapidly.
**Fix:** Look at theta as a PERCENTAGE of premium, not just absolute value. A ₹2 theta on a ₹5 option is devastating.

### Mistake 5: Holding Options Through Major Events Without Understanding IV Crush
**Problem:** You buy ATM calls before Budget day. IV is 22%. After the Budget, IV drops to 14%. Your premium collapses even though NIFTY moved in your direction.
**Fix:** If you must hold through events, buy ITM options (less extrinsic to lose from IV crush) or use spreads (short leg benefits from IV crush).

### Mistake 6: Not Accounting for Weekend Theta
**Problem:** You hold ATM calls from Friday to Monday. NIFTY opens flat on Monday. Your premium is down 15–20% despite no price movement. You think the market is "rigged."
**Reality:** Weekend theta ate 2 days of extrinsic value. This is normal and expected.
**Fix:** Close ATM positions on Friday afternoon unless you have a strong reason to hold over the weekend.

### Mistake 7: Confusing Theta with "Time Running Out"
**Problem:** "My option has 10 days to expiry, so theta is low. I can hold it safely." Reality: If the option is ATM and IV is high, theta can still be significant even with 10 days left. Always check the actual theta value, not just the days to expiry.
**Fix:** Check theta on Sensibull/Opstra before every trade. Don't assume theta is low just because expiry is far away.

---

## CHAPTER 12: PRACTICAL EXERCISES

### Exercise 1: Theta Calculation Drill
NIFTY is at 24,400. Current week expiry (3 days left). Calculate the approximate premium after 2 days of no movement for each option:
a) 24,400 CE at ₹85 (theta -₹16/day)
b) 24,300 CE at ₹130 (theta -₹10/day)
c) 24,200 CE at ₹235 (theta -₹8/day)
d) 24,600 CE at ₹25 (theta -₹8/day)

### Exercise 2: Breakeven Analysis
For each option, calculate the daily breakeven move (theta / delta):
a) 24,400 CE: Delta 0.50, Theta -₹16
b) 24,350 CE: Delta 0.62, Theta -₹12
c) 24,300 CE: Delta 0.70, Theta -₹10
d) 24,500 CE: Delta 0.35, Theta -₹13
e) Which option requires the smallest daily move to break even?

### Exercise 3: Theta Decay Observation
On Monday morning, note the premium of the current week ATM CE. Check the same option on Wednesday morning (assuming NIFTY hasn't moved significantly). How much premium was lost to theta over 2 days? Compare with the theoretical theta.

### Exercise 4: Overnight vs Intraday Comparison
Using Sensibull's strategy builder, compare the theta of:
a) Holding 24,400 CE from Monday 10 AM to Monday 3 PM (5 hours)
b) Holding 24,400 CE from Monday 10 AM to Tuesday 10 AM (24 hours)
What is the theta difference? How much extra did the overnight hold cost?

### Exercise 5: Expiry Day Theta Tracking
On the next expiry day (Thursday), track the ATM CE premium every hour from 9:15 AM to 3:00 PM (assuming NIFTY stays within a 20-point range). Plot the premium decay on a graph. Does it match the exponential decay curve from Chapter 3?

---

## WEEK 14 SELF-TEST

**Q1.** What does theta measure? Write the formula.

**Q2.** Is theta positive or negative for an option buyer? What does this mean?

**Q3.** Which strike has the highest absolute theta: deep ITM, ATM, or deep OTM? Why?

**Q4.** How does theta change as expiry approaches? Is the relationship linear or non-linear?

**Q5.** If your ATM call has theta -₹16/day and delta 0.50, what is the daily breakeven move?

**Q6.** In the "flat week" example (Chapter 4), NIFTY moved +5 points over 4 days but the option lost 94% of its value. Why?

**Q7.** How much theta decay occurs over the weekend (Saturday + Sunday)?

**Q8.** What is the relationship between gamma and theta? Can you have high gamma without high theta?

**Q9.** On expiry day, approximately how much does an ATM option lose per hour?

**Q10.** If it's Wednesday and you expect a move on Friday, should you buy current week or next week options? Why?

**Q11.** How does high IV affect theta?

**Q12.** Name three practical strategies to minimize theta damage as an option buyer.

---

## SELF-TEST ANSWERS

**A1.** Theta measures how much an option's premium decreases for every 1 day that passes, assuming all other factors remain constant. Formula: Θ = Change in Premium / Change in Time (per day).

**A2.** Theta is **negative** for an option buyer. This means the option's premium decreases as time passes, even if NIFTY doesn't move. Time is the buyer's enemy. The negative sign indicates decay — you're losing money every day you hold the option.

**A3.** **ATM** has the highest absolute theta. This is because ATM options have the maximum extrinsic value, and theta only decays extrinsic value. More extrinsic = more daily decay. Deep ITM options have less extrinsic (most of their premium is intrinsic, which is immune to theta). Deep OTM options have low absolute extrinsic, so their absolute theta is lower (though their theta as a percentage of premium is very high).

**A4.** Theta **accelerates** as expiry approaches. The relationship is **non-linear** (exponential). An option might lose ₹3/day with 30 days to expiry but ₹20/day with 2 days to expiry. The last 3–5 days see the most rapid decay — the "theta cliff." The decay curve is convex, starting flat and steepening dramatically near expiry.

**A5.** Breakeven = Theta / Delta = ₹16 / 0.50 = **32 points per day**. NIFTY must move at least 32 points per day in your direction just to offset the daily time decay. Any move less than 32 points means you lose money despite being directionally correct.

**A6.** Because the option was ATM (100% extrinsic) with only 4 days to expiry (steep part of the theta curve). Over 4 days, theta decayed approximately ₹80 of extrinsic value. The +5 point NIFTY move added only ₹2.5 of intrinsic value (delta 0.50 × 5). Net result: +₹2.5 - ₹80 = -₹77.5. The move was far too small and too slow to overcome the rapid time decay.

**A7.** Approximately **2 days' worth of theta**. Options don't pause their time decay over the weekend. The 2 days of decay are "priced in" between Friday's close and Monday's open. For an ATM option with theta -₹16/day, the weekend cost is approximately ₹12–16 (the exact amount depends on how the market prices the weekend risk).

**A8.** Gamma and theta are **inversely related** — high gamma always comes with high theta, and low gamma comes with low theta. You **cannot** have high gamma without paying high theta. They are two sides of the same coin. The mathematical relationship is approximately: Theta ≈ -½ × Gamma × Spot² × IV². The market charges you theta (time decay) in exchange for giving you gamma (acceleration on big moves).

**A9.** Approximately **₹4–5 per hour** for an ATM option on expiry day. Over the 6.25-hour trading session, an ATM option starting at ₹25 will decay to ₹0. That's ₹25 / 6.25 = ₹4 per hour average, accelerating to ₹5+ per hour in the middle of the day.

**A10.** **Next week** options. Current week options on Wednesday have only 1 day to expiry, meaning theta is at its maximum (-₹20 to -₹25/day). Your premium will lose 50–70% of its value by Thursday even if NIFTY moves slightly. Next week options have 8 days to expiry, with much lower theta (-₹8 to -₹10/day). The extra premium you pay buys you the time you need for the Friday move to materialize.

**A11.** Higher IV **increases** theta. When IV is high, options have more extrinsic value (the market is pricing in bigger expected moves). More extrinsic = more daily decay. For example, an ATM option with IV 14% might have theta -₹16/day, while the same option with IV 25% might have theta -₹30/day. This is why buying options before major events (when IV is elevated) is expensive — you're paying high theta AND risking IV crush after the event.

**A12.** Any three of: (1) **Trade intraday** — close positions before 3:30 PM to avoid overnight theta. (2) **Buy ITM options** for multi-day trades — lower theta relative to delta. (3) **Use next week's expiry** when holding over 2+ days — more time = lower daily theta. (4) **Avoid holding ATM options over the weekend** — 2 days of weekend theta. (5) **Use spreads** — the short leg earns theta, offsetting the long leg's decay. (6) **Scale in** instead of holding and hoping — exit if the move doesn't happen quickly, re-enter when the setup re-forms.

---

## WEEK 14 SUMMARY CHEAT SHEET

| Concept | Key Takeaway |
|---------|-------------|
| **Theta definition** | Premium decay per day due to time passing |
| **Buyer theta** | Always NEGATIVE (premium decreases) |
| **Seller theta** | Always POSITIVE (premium decreases for buyer = income for seller) |
| **Theta target** | Decays EXTRINSIC value only. Intrinsic is immune. |
| **Highest theta** | ATM options (maximum extrinsic to decay) |
| **Theta vs time** | Non-linear. Accelerates near expiry ("theta cliff") |
| **Last 3 days** | Destroy more value than the first 15 days |
| **Expiry day theta** | ₹4–5 per hour for ATM. Violent decay. |
| **Weekend theta** | Real. ~2 days of decay priced in Monday open. |
| **Gamma-theta link** | High gamma = High theta. Cannot separate them. |
| **Breakeven formula** | Breakeven Move = Theta / Delta |
| **ATM breakeven** | ~32 pts/day (hard). ITM breakeven: ~14 pts/day (easy) |
| **Speed matters** | 30 pts in 2 hours = profit. 30 pts in 4 days = loss. |
| **IV effect** | Higher IV = Higher theta = Faster decay |
| **IV crush** | Post-event IV drop destroys extrinsic like accelerated theta |
| **Defense #1** | Trade intraday (avoid overnight theta) |
| **Defense #2** | Buy ITM for multi-day trades |
| **Defense #3** | Use next week expiry on Wed/Thu |
| **Defense #4** | Close ATM positions Friday (avoid weekend theta) |
| **Defense #5** | Use spreads to reduce net theta |
| **Defense #6** | Scale in, don't hold and hope |

---

## WHAT'S NEXT

**Week 15: The Greeks — Vega (Volatility Sensitivity)**

Vega is the Greek that explains why your option premium can surge or collapse even when NIFTY hasn't moved a single point. It measures how sensitive your option is to changes in **Implied Volatility (IV)**.

You'll learn:
- What IV actually represents (the market's fear gauge)
- How vega affects ATM vs ITM vs OTM options differently
- Why vega is highest for long-dated options (opposite of theta!)
- The "IV crush" phenomenon around major events
- How to use vega to time your entries and exits
- The complete four-Greek dashboard (Delta + Gamma + Theta + Vega)

If theta is the fuel leak and gamma is the accelerator, **vega is the road condition** — it determines whether the road is smooth (low IV, calm markets) or bumpy (high IV, volatile markets), and it affects your ride regardless of which direction you're going.

Say **"proceed to week 15"** when you're ready!
