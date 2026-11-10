

# WEEK 3 — COMPLETE NOTES

## Futures and Options: How Derivatives Actually Work in the Indian Market

This week we go deeper into derivatives. In Week 1, you learned what futures and options are at a conceptual level. This week, you will understand exactly how they work in practice on NSE, how contracts are structured, how expiry works, what happens on expiry day, and how to read the option chain like someone who actually understands what they're looking at.

---

---

# CHAPTER 1: WHAT IS A DERIVATIVE (DEEPER UNDERSTANDING)

## Recap

A derivative is a financial instrument whose value is **derived from** an underlying asset.

For NIFTY options:
- The **underlying asset** is the NIFTY 50 index
- The **derivative** is the option contract on NIFTY

The option's price (premium) changes because the NIFTY 50 index value changes.

---

## Why Do Derivatives Exist?

Derivatives were originally created for **hedging** — protecting against price risk.

### Real Example: Hedging with Options

Suppose you manage a portfolio of Indian stocks worth ₹50 lakhs. You're worried that the market might crash in the next month.

You could sell all your stocks, but:
- You'd pay brokerage and taxes
- You'd miss out if the market goes up instead
- You'd have to buy everything back later

Instead, you buy **NIFTY put options**.

If the market crashes:
- Your stock portfolio loses value
- But your put options gain value
- The put option profit offsets your portfolio loss

If the market goes up:
- Your stock portfolio gains value
- Your put options expire worthless
- You lose only the premium paid for puts (a small cost — like insurance)

**This is exactly like buying insurance.** You pay a small premium for protection against a large loss.

---

## The Three Participants in Derivatives Markets

| Participant | Purpose | Example |
|---|---|---|
| **Hedger** | Protect existing positions from adverse price movements | Fund manager buying puts to protect portfolio |
| **Speculator** | Profit from price movements without owning the underlying | Retail trader buying NIFTY calls expecting market to rise |
| **Arbitrageur** | Exploit price differences between related instruments | Trading firm buying NIFTY in cash market and selling NIFTY futures simultaneously when futures are overpriced |

**You, as a retail trader learning NIFTY options, are a speculator.** There is nothing wrong with that — speculators provide liquidity and make markets efficient. But you must acknowledge that you are speculating and manage risk accordingly.

---

## Two Types of Derivatives on NSE

### 1. Futures

| Feature | Detail |
|---|---|
| Obligation | Both buyer and seller are **obligated** |
| Risk | **Unlimited** for both sides |
| Margin required | Yes — span margin + exposure margin |
| Premium | No premium. You enter at the futures price |
| Daily settlement | Mark-to-market (M2M) — gains/losses settled daily |

### 2. Options

| Feature | Detail |
|---|---|
| Obligation | Buyer has a **right**, seller has an **obligation** |
| Risk for buyer | **Limited** to premium paid |
| Risk for seller | **Potentially unlimited** |
| Margin required | Only for sellers. Buyers pay premium upfront |
| Premium | Buyer pays premium to seller at the time of entering |
| Daily settlement | No M2M for buyers. Premium fluctuates but no daily cash settlement like futures |

---

---

# CHAPTER 2: UNDERSTANDING FUTURES CONTRACTS IN DETAIL

Even though you will trade options, understanding futures is important because:
1. Futures prices influence options pricing
2. Many concepts are shared between futures and options
3. You'll encounter futures references in market commentary

---

## How a NIFTY Futures Contract Works

### Example

NIFTY spot (current index value): **24,500**

NIFTY futures (current month contract): **24,530**

The futures price is usually slightly higher than the spot price. The difference is called the **basis** or **premium** (not to be confused with options premium).

$$\text{Basis} = \text{Futures Price} - \text{Spot Price} = 24,530 - 24,500 = 30 \text{ points}$$

### Why Is Futures Price Different from Spot?

The theoretical futures price is:

$$F = S \times e^{(r-d) \times T}$$

Where:
- F = Futures price
- S = Spot price
- r = Risk-free interest rate
- d = Dividend yield
- T = Time to expiry (in years)
- e = Euler's number (2.71828)

**In simple terms:** Futures price = Spot price + Cost of carry - Expected dividends

The **cost of carry** is the interest cost of holding the position. If you buy NIFTY in the cash market, you need ₹18+ lakhs. That money could have earned interest. Futures price reflects this.

**You don't need to memorize this formula.** Just understand that:
- Futures price is usually **above** spot when interest rate > dividend yield
- As expiry approaches, the futures price **converges** toward the spot price
- On expiry day, futures price = spot price (approximately)

---

## Futures Contract Specifications (NIFTY)

| Parameter | Detail |
|---|---|
| Underlying | NIFTY 50 index |
| Exchange | NSE |
| Lot size | 75 (check current — SEBI revises this) |
| Tick size (minimum price movement) | 0.05 points |
| Expiry | Last Thursday of each month |
| Available contracts | 3 monthly contracts at any time (current month, next month, far month) |
| Settlement | Cash settled (no delivery) |
| Margin required | Approximately ₹1,00,000 – ₹1,50,000 per lot (varies with volatility) |

---

## Mark-to-Market (M2M) Settlement in Futures

This is a critical concept that makes futures different from options.

### What Is M2M?

At the end of every trading day, your futures position is **settled** — your gains or losses for that day are added to or deducted from your account.

### Example

**Day 1:** You buy NIFTY futures at 24,500

| Day | NIFTY Futures Close | Daily P&L (per unit) | Daily P&L (per lot = 75) | Cumulative P&L |
|---|---|---|---|---|
| Day 1 | 24,600 | +100 | +₹7,500 | +₹7,500 |
| Day 2 | 24,450 | –150 | –₹11,250 | –₹3,750 |
| Day 3 | 24,550 | +100 | +₹7,500 | +₹3,750 |
| Day 4 | 24,400 | –150 | –₹11,250 | –₹7,500 |

**What happens in your account:**

- Day 1: ₹7,500 is **credited** to your account
- Day 2: ₹11,250 is **debited** from your account
- Day 3: ₹7,500 is **credited**
- Day 4: ₹11,250 is **debited**

**The problem:** On Day 4, your account has lost ₹7,500 total. If your account doesn't have enough margin to cover this loss + the required margin, you get a **margin call** — the broker asks you to deposit more money or they'll close your position.

**This is why futures are dangerous for beginners:**
- Losses are unlimited
- Losses are settled daily (you need cash every day)
- If you can't pay the margin call, your position is forcibly closed (usually at a loss)

---

## Why We Focus on Options Instead of Futures

| Risk Factor | Futures | Options (Buying) |
|---|---|---|
| Maximum loss | Unlimited | Premium paid (fixed) |
| Margin required | Very high (₹1L+) | Only premium (₹3K–₹15K for 1 lot) |
| Daily cash settlement (M2M) | Yes | No |
| Margin call risk | Yes | No |
| Can lose more than invested | Yes | No |
| Suitable for beginners | **No** | **Yes (with proper risk management)** |

**Clear recommendation:** Do not trade futures until you have at least 6–12 months of profitable options trading experience. Even then, be very careful.

---

---

# CHAPTER 3: OPTIONS CONTRACTS — COMPLETE DETAILS

## NIFTY Options Contract Specifications

| Parameter | Detail |
|---|---|
| **Underlying** | NIFTY 50 index |
| **Exchange** | NSE |
| **Contract type** | European (can only be exercised at expiry, not before) |
| **Lot size** | 75 (verify current lot size — SEBI changes this periodically) |
| **Tick size** | ₹0.05 (minimum price movement) |
| **Strike price interval** | ₹50 (e.g., 24,400, 24,450, 24,500, 24,550, 24,600) |
| **Weekly expiry** | Every Thursday |
| **Monthly expiry** | Last Thursday of each month |
| **Available strikes** | Multiple strikes are available around the current NIFTY level |
| **Settlement** | Cash settled |
| **Trading hours** | 9:15 AM – 3:30 PM |

---

## Important Details Explained

### European vs American Options

There are two styles of options globally:

| Style | Exercise | In India |
|---|---|---|
| **European** | Can only be exercised **at expiry** | NIFTY options, BANK NIFTY options — all index options |
| **American** | Can be exercised **at any time before expiry** | Stock options (options on individual stocks like Reliance, TCS) |

**Why does this matter?**

For NIFTY options (European), if you buy a call option, you cannot exercise it before expiry. You can only:
1. **Sell it** in the market (square off your position) — this is what you'll do 99% of the time
2. **Hold it until expiry** — it will be automatically exercised if ITM

**Practically, you'll almost always square off before expiry.** You buy an option, the price goes up (or down), and you sell it. The European/American distinction mainly matters for pricing models.

---

### Strike Price Interval

NIFTY options have strikes at every **₹50 interval**.

If NIFTY is at 24,500, you'll see strikes like:

```
... 24,200, 24,250, 24,300, 24,350, 24,400, 24,450, 24,500, 24,550, 24,600, 24,650, 24,700, 24,750, 24,800 ...
```

Each of these is a separate options contract. Each has its own premium, its own order book, its own open interest.

The ATM strike is the one **closest to the current NIFTY level**.

NIFTY at 24,520 → ATM strike is 24,500

NIFTY at 24,480 → ATM strike is 24,500

NIFTY at 24,530 → ATM strike is 24,550

---

### Lot Size

NIFTY's lot size determines how many units you trade per contract.

**Current lot size: 75** (but SEBI revises this — always verify)

This means:
- 1 lot = 75 units
- If premium is ₹150 per unit, you pay ₹150 × 75 = ₹11,250 for 1 lot
- If NIFTY moves 1 point, your option's value changes by approximately ₹0.5 × 75 = ₹37.5 for ATM options (this is related to delta which you'll learn later)

**Minimum trade = 1 lot.** You cannot buy 10 units. You must buy at least 75.

---

### Tick Size

The minimum price movement of an option is **₹0.05**.

An option premium can be: ₹150.00, ₹150.05, ₹150.10, ₹150.15...

It cannot be ₹150.03 or ₹150.07.

---

---

# CHAPTER 4: UNDERSTANDING EXPIRY

Expiry is one of the most important concepts in options trading. If you don't understand expiry, you will lose money.

---

## What Is Expiry?

Expiry is the **date and time** at which an options contract ceases to exist.

After expiry:
- ITM options are automatically exercised (cash settled for NIFTY)
- ATM and OTM options expire worthless (premium becomes zero)
- The contract no longer exists

---

## NIFTY Expiry Schedule

### Weekly Expiry

- **Every Thursday**
- If Thursday is a trading holiday, expiry moves to the **previous trading day** (usually Wednesday)
- New weekly contracts are introduced continuously — there are usually about 7 weekly expiries available at any time

### Monthly Expiry

- **Last Thursday of each month**
- Monthly contracts are also available for the **next 2 months** beyond the current month (total 3 monthly contracts)

### The Difference Between Weekly and Monthly Options

| Feature | Weekly Options | Monthly Options |
|---|---|---|
| Expiry | Every Thursday | Last Thursday of month |
| Time value | Less (shorter life) | More (longer life) |
| Premium | Generally lower | Generally higher |
| Theta decay | Faster (especially last 2 days) | Slower |
| Liquidity | High for current week | High for current month |
| Trading volume | Extremely high | High |

**Most retail traders trade the current week's expiry** because premiums are cheaper and moves happen faster.

**Important:** Weekly options have very fast time decay. If you buy an ATM option on Monday morning and NIFTY doesn't move, your option will lose 50–70% of its value by Thursday afternoon just from time decay.

---

## What Happens on Expiry Day (Thursday)

### Timeline of Expiry Day

| Time | What Happens |
|---|---|
| 9:15 AM | Normal trading begins. Options premiums are heavily influenced by theta (time decay) |
| 9:15 AM – 1:30 PM | Normal trading. Some traders close their positions before the afternoon. |
| 1:30 PM – 3:00 PM | Activity increases. Many traders close positions. Gamma risk increases for option sellers. |
| 3:00 PM – 3:30 PM | Final 30 minutes. Extremely volatile. Large premium moves on small NIFTY movements. |
| 3:30 PM | Market closes. The **settlement price** is calculated. |

### Settlement Price Calculation

The NIFTY settlement price on expiry day is the **weighted average of the NIFTY 50 values during the last 30 minutes of trading (3:00 PM – 3:30 PM)**.

It is NOT simply the closing price at 3:30 PM. It's a **volume-weighted average price (VWAP)** of the index during the last 30 minutes.

**Why does this matter?**

Because you might see NIFTY at 24,510 at 3:30 PM, but the settlement price might be 24,503. Your ITM option's settlement value depends on the settlement price, not the last traded price.

---

### What Happens to Your Options at Expiry

**Scenario 1: You hold NIFTY 24,500 CE and NIFTY settlement price is 24,650**

Your option is **ITM**.

Intrinsic value = 24,650 – 24,500 = **₹150 per unit**

Settlement amount = ₹150 × 75 = **₹11,250 credited** to your account.

If you bought the option at ₹200 premium: Your loss = (200 – 150) × 75 = **₹3,750** (because you paid ₹200 but received only ₹150 at settlement).

If you bought the option at ₹100 premium: Your profit = (150 – 100) × 75 = **₹3,750**.

**Scenario 2: You hold NIFTY 24,500 CE and NIFTY settlement price is 24,500**

Your option is **ATM** with zero intrinsic value.

Settlement amount = **₹0**

You lose the **entire premium** you paid.

**Scenario 3: You hold NIFTY 24,500 CE and NIFTY settlement price is 24,400**

Your option is **OTM**.

Settlement amount = **₹0**

You lose the **entire premium** you paid.

---

### Critical Warning About Expiry Day

**For option buyers:**

- OTM options can suddenly become ITM if NIFTY moves sharply in the last hour — this creates windfall profits but the probability is low
- ATM options are highly unpredictable — a ₹10 NIFTY move can swing the premium by ₹5–₹10 in seconds
- Time value collapses rapidly — an ATM option worth ₹30 at 10:00 AM might be worth ₹5 at 2:00 PM even if NIFTY hasn't moved

**For option sellers:**

- **Gamma risk** is extremely high near expiry — a small NIFTY movement causes a large change in the option's delta, leading to sudden, large losses
- Many professional traders reduce positions on expiry day afternoon
- Option sellers can face losses of ₹50,000 – ₹5,00,000+ in minutes if NIFTY makes a sharp unexpected move near expiry

**My recommendation for you as a beginner:**

- **Do not trade the last 2 hours of expiry day** (1:30 PM – 3:30 PM) for at least your first 3 months
- **Do not hold positions into expiry** unless you have a very specific plan
- **Square off all positions by 1:00 PM on Thursday** during your learning phase

---

## Example: How Expiry Affects Premium Over the Week

Let's track a hypothetical NIFTY 24,500 CE through one week.

**Setup:** NIFTY stays at exactly 24,500 the entire week (unrealistic, but this isolates the time decay effect).

| Day | Time | NIFTY | 24,500 CE Premium | Explanation |
|---|---|---|---|---|
| Monday 9:30 AM | 4 days to expiry | 24,500 | ₹85 | High time value. Full week remaining. |
| Monday 3:30 PM | 3.5 days to expiry | 24,500 | ₹80 | Half-day of theta decay |
| Tuesday 9:30 AM | 3 days to expiry | 24,500 | ₹72 | Another day of decay |
| Tuesday 3:30 PM | 2.5 days to expiry | 24,500 | ₹66 | Decay accelerating |
| Wednesday 9:30 AM | 2 days to expiry | 24,500 | ₹55 | Notice the decay is getting faster |
| Wednesday 3:30 PM | 1.5 days to expiry | 24,500 | ₹45 | Significant drop from morning |
| Thursday 9:30 AM | Expiry day morning | 24,500 | ₹25 | Most time value gone |
| Thursday 1:00 PM | 2.5 hours left | 24,500 | ₹10 | Almost all time value gone |
| Thursday 3:00 PM | 30 minutes left | 24,500 | ₹3 | Barely any time value |
| Thursday 3:30 PM | Expiry | 24,500 | ₹0 | ATM with zero intrinsic value = worthless |

**The option went from ₹85 to ₹0 without NIFTY moving a single point.**

This is **theta decay** (time decay). This is why buying options and holding them without a strong directional move is a losing strategy.

**Key insight:** As an option buyer, time is your enemy. Every hour that passes without a favorable price movement costs you money.

---

---

# CHAPTER 5: UNDERSTANDING THE OPTION CHAIN

The option chain is the single most important data source for an options trader. Learning to read it properly will give you an edge over most retail traders who never look at it.

---

## Where to Find It

Go to: [nseindia.com/option-chain](https://www.nseindia.com/option-chain)

Select:
- Symbol: **NIFTY**
- Expiry date: **Select the nearest Thursday**

---

## What You See

The option chain is a **table** with three sections:

```
CALLS (CE)          STRIKE PRICE          PUTS (PE)
←Left side→         ←Center→              ←Right side→
```

The **center column** shows all available strike prices.

The **left side** shows data for Call options at each strike.

The **right side** shows data for Put options at each strike.

---

## Columns Explained (One by One)

### Let me explain each column you'll see on the NSE option chain:

---

### 1. OI (Open Interest)

**What it is:** The total number of **outstanding (open) contracts** at that strike price.

**What it tells you:**

- High OI at a strike means many traders have positions at that strike
- Very high OI on the **call side** at a particular strike can act as **resistance** (many call sellers are betting NIFTY won't cross that level)
- Very high OI on the **put side** at a particular strike can act as **support** (many put sellers are betting NIFTY won't fall below that level)

**Example:**

| Strike | Call OI | Put OI | Interpretation |
|---|---|---|---|
| 24,000 | 5 lakh | 45 lakh | Massive put OI → Strong support at 24,000 |
| 24,500 | 12 lakh | 15 lakh | Moderate OI on both sides → ATM area |
| 25,000 | 50 lakh | 3 lakh | Massive call OI → Strong resistance at 25,000 |

**Units:** OI is shown in number of contracts (each contract = 75 units for NIFTY).

If OI shows 50 lakh, it means 50,00,000 contracts are open at that strike. Each contract is 75 units, so the notional exposure is 50,00,000 × 75 × NIFTY value.

---

### 2. Change in OI

**What it is:** The change in open interest **compared to the previous day**.

**What it tells you:**

- **Positive change in OI + Price increase:** New long positions are being built → Bullish
- **Positive change in OI + Price decrease:** New short positions are being built → Bearish
- **Negative change in OI + Price increase:** Short covering (shorts are closing positions) → May not sustain
- **Negative change in OI + Price decrease:** Long unwinding (longs are closing positions) → May not sustain

**This is the most important column for understanding what smart money is doing.**

**Example:**

| Strike | Call Change in OI | Interpretation |
|---|---|---|
| 25,000 CE | +10 lakh | Massive call writing at 25,000 → Bearish signal (sellers betting NIFTY won't cross 25,000) |
| 24,200 CE | –5 lakh | Call writers closing positions at 24,200 → They no longer think 24,200 will hold as resistance → Bullish signal |

| Strike | Put Change in OI | Interpretation |
|---|---|---|
| 24,000 PE | +8 lakh | Massive put writing at 24,000 → Bullish signal (sellers betting NIFTY won't fall below 24,000) |
| 24,500 PE | –3 lakh | Put writers closing positions at 24,500 → They're worried NIFTY might fall below 24,500 → Bearish signal |

---

### 3. Volume

**What it is:** The total number of contracts traded at that strike **today**.

**What it tells you:**

- High volume means high activity — many traders are interested in that strike
- High volume near ATM strikes is normal
- Unusual volume at OTM strikes can indicate smart money positioning or hedging activity

**Difference between Volume and OI:**

| | Volume | Open Interest |
|---|---|---|
| Measures | Today's trading activity | Total outstanding positions |
| Resets | Resets to zero every day | Cumulative (doesn't reset) |
| Analogy | How many people walked through a door today | How many people are inside the room right now |

---

### 4. IV (Implied Volatility)

**What it is:** The market's expectation of how much NIFTY will move in the future, expressed as a percentage.

**What it tells you:**

- **High IV** → Market expects large moves → Options are expensive
- **Low IV** → Market expects small moves → Options are cheap
- IV is **not** the same as historical volatility (actual past movement)
- IV changes based on demand and supply of options

**For now, just note the IV number.** We'll study IV in depth in Phase 3 (Weeks 15–16).

**Typical IV ranges for NIFTY ATM options:**

| Market Condition | IV Range |
|---|---|
| Calm, low-volatility market | 10–13% |
| Normal market | 13–18% |
| Before major events (budget, elections, RBI) | 18–25% |
| During crisis or crash | 25–40%+ |

---

### 5. LTP (Last Traded Price)

**What it is:** The premium at which the last trade occurred for that strike.

This is the current "price" of the option.

---

### 6. Change

**What it is:** The change in LTP compared to the previous day's close.

A positive change means the option premium has increased today.

---

### 7. Bid Qty, Bid Price, Ask Price, Ask Qty

These show the **current order book** for that strike:

| Column | Meaning |
|---|---|
| **Bid Qty** | How many contracts buyers want to buy at the bid price |
| **Bid Price** | The highest price a buyer is willing to pay right now |
| **Ask Price** | The lowest price a seller is willing to accept right now |
| **Ask Qty** | How many contracts sellers want to sell at the ask price |

**Bid-Ask Spread = Ask Price – Bid Price**

For liquid ATM NIFTY options, the spread is typically ₹0.10 – ₹0.50 (very tight).

For illiquid deep OTM options, the spread can be ₹2 – ₹20 (very wide — avoid these).

**Example:**

| Bid Price | Ask Price | Spread | Liquidity Assessment |
|---|---|---|---|
| ₹149.50 | ₹150.00 | ₹0.50 | Good — liquid |
| ₹149.80 | ₹150.05 | ₹0.25 | Excellent — very liquid |
| ₹2.50 | ₹4.00 | ₹1.50 | Poor — illiquid |
| ₹0.50 | ₹2.00 | ₹1.50 | Very poor — avoid |

**Why does this matter?**

If you buy at ₹150.00 (ask) and immediately want to sell, you can only sell at ₹149.50 (bid). You've already lost ₹0.50 per unit just from the spread. For 1 lot of 75 units, that's ₹37.50 in **invisible cost** before any charges.

---

## Reading the Full Option Chain: A Complete Example

Let me show you how to read the option chain with a realistic example.

**Date:** A Tuesday morning
**NIFTY spot:** 24,500
**Expiry:** This Thursday

**Simplified option chain:**

| CE OI | CE Chg OI | CE Volume | CE IV | CE LTP | Strike | PE LTP | PE IV | PE Volume | PE Chg OI | PE OI |
|---|---|---|---|---|---|---|---|---|---|---|
| 2,00,000 | +50,000 | 15,000 | 22% | ₹5 | 25,000 | ₹490 | 15% | 2,000 | –10,000 | 50,000 |
| 5,00,000 | +1,50,000 | 45,000 | 19% | ₹15 | 24,800 | ₹305 | 14% | 5,000 | –20,000 | 80,000 |
| 8,00,000 | +80,000 | 60,000 | 17% | ₹50 | 24,600 | ₹145 | 14% | 15,000 | +30,000 | 2,00,000 |
| 10,00,000 | +20,000 | 1,00,000 | 15% | ₹110 | 24,500 | ₹100 | 14% | 90,000 | +40,000 | 12,00,000 |
| 3,00,000 | –50,000 | 70,000 | 14% | ₹200 | 24,400 | ₹45 | 15% | 50,000 | +60,000 | 5,00,000 |
| 1,50,000 | –30,000 | 40,000 | 13% | ₹310 | 24,300 | ₹18 | 17% | 30,000 | +40,000 | 3,00,000 |
| 80,000 | –20,000 | 20,000 | 12% | ₹450 | 24,100 | ₹5 | 20% | 8,000 | +10,000 | 1,00,000 |
| 40,000 | –10,000 | 5,000 | 11% | ₹505 | 24,000 | ₹2 | 25% | 3,000 | +5,000 | 60,000 |

### How to Read This

**Step 1: Identify ATM Strike**

NIFTY spot is 24,500. The ATM strike is **24,500**.

**Step 2: Look at CE (Call) and PE (Put) premiums at ATM**

- 24,500 CE: ₹110
- 24,500 PE: ₹100

CE premium is slightly higher. This tells you the market is slightly bullish (or there's slightly more demand for calls).

**Step 3: Look at highest OI on Call side**

Highest call OI = **10,00,000 at 24,500**
Second highest call OI = **8,00,000 at 24,600**

But look at the **change in OI**:
- 24,800 CE has **+1,50,000 change in OI** → Massive new call writing at 24,800
- 24,600 CE has **+80,000 change in OI** → Significant call writing at 24,600

**Interpretation:** Option sellers are heavily betting that NIFTY will NOT cross 24,600–24,800 by Thursday. These levels are **resistance zones** according to option sellers.

**Step 4: Look at highest OI on Put side**

Highest put OI = **12,00,000 at 24,500**
Second highest = **5,00,000 at 24,400**

Change in OI:
- 24,400 PE has **+60,000 change in OI** → New put writing at 24,400
- 24,500 PE has **+40,000 change in OI** → New put writing at 24,500
- 24,300 PE has **+40,000 change in OI** → New put writing at 24,300

**Interpretation:** Put sellers are betting NIFTY will NOT fall below 24,300–24,500. These levels are **support zones** according to option sellers.

**Step 5: Determine the expected range**

Based on OI analysis:
- **Support (based on put writing):** 24,300 – 24,500
- **Resistance (based on call writing):** 24,600 – 24,800
- **Expected range for the week:** 24,300 – 24,800

**Step 6: Check for unusual activity**

Look for strikes where change in OI is **negative** (positions being closed):
- 24,400 CE: **–50,000** → Call writers at 24,400 are closing positions (they no longer think 24,400 will be resistance — NIFTY has already crossed it)
- 24,300 CE: **–30,000** → Similar
- 25,000 PE: **–10,000** → Put writers at 25,000 are closing (they're losing confidence)

**This kind of analysis tells you what large traders (who typically sell options) expect.**

---

## Put-Call Ratio (PCR)

$$\text{PCR} = \frac{\text{Total Put OI}}{\text{Total Call OI}}$$

| PCR Value | Interpretation |
|---|---|
| Above 1.2 | Bullish (more put writing → sellers expect support) |
| 0.8 – 1.2 | Neutral |
| Below 0.8 | Bearish (more call writing → sellers expect resistance) |

**Caution:** PCR is just one indicator. Don't make trading decisions based on PCR alone. It's context-dependent and can change rapidly.

---

## Max Pain

**What it is:** The strike price at which the **maximum number of options (both calls and puts) would expire worthless**, causing maximum loss to option buyers and maximum profit to option sellers.

**Theory:** Since option sellers are typically institutional players with more capital and influence, the NIFTY tends to gravitate toward the max pain strike near expiry.

**How to find it:** Many websites calculate this for you:
- [sensibull.com](https://www.sensibull.com/) (free features)
- [opstra.definedge.com](https://opstra.definedge.com/) (free features)

**Caution:** Max pain is a theoretical concept. It works sometimes and fails sometimes. Don't trade based solely on max pain. Use it as one input among many.

---

---

# CHAPTER 6: HOW TO READ AN OPTION NAME

When you see a NIFTY option listed anywhere, it follows this format:

```
NIFTY 24500 CE 27-Mar-2025
```

Let me break this down:

| Component | Meaning |
|---|---|
| **NIFTY** | Underlying asset (NIFTY 50 index) |
| **24500** | Strike price |
| **CE** | Call European (call option) |
| **27-Mar-2025** | Expiry date (27th March 2025, which is a Thursday) |

**Another example:**

```
NIFTY 24200 PE 03-Apr-2025
```

| Component | Meaning |
|---|---|
| NIFTY | NIFTY 50 index |
| 24200 | Strike price |
| PE | Put European (put option) |
| 03-Apr-2025 | Expiry date |

---

## On Trading Platforms

On Zerodha Kite, you might see it written as:

```
NIFTY2530624500CE
```

Which means:
- NIFTY: Underlying
- 25306: Year 2025, Month 03 (March), Date 06
- 24500: Strike price
- CE: Call option

Different platforms display it differently but the information is the same: underlying + expiry + strike + type.

---

---

# CHAPTER 7: INTRINSIC VALUE AND TIME VALUE

This is a fundamental concept that you must understand before Phase 3.

---

## Option Premium Has Two Components

$$\text{Option Premium} = \text{Intrinsic Value} + \text{Time Value (Extrinsic Value)}$$

---

### Intrinsic Value

**Definition:** The real, tangible value of an option if it were exercised right now.

**For Call options:**

$$\text{Intrinsic Value} = \text{Spot Price} - \text{Strike Price}$$

If the result is negative, intrinsic value = 0 (it can never be negative).

**For Put options:**

$$\text{Intrinsic Value} = \text{Strike Price} - \text{Spot Price}$$

If the result is negative, intrinsic value = 0.

**Examples (NIFTY at 24,500):**

| Option | Calculation | Intrinsic Value |
|---|---|---|
| 24,300 CE | 24,500 – 24,300 | ₹200 |
| 24,400 CE | 24,500 – 24,400 | ₹100 |
| 24,500 CE | 24,500 – 24,500 | ₹0 |
| 24,600 CE | 24,500 – 24,600 = –100 → | ₹0 |
| 24,700 CE | 24,500 – 24,700 = –200 → | ₹0 |
| | | |
| 24,700 PE | 24,700 – 24,500 | ₹200 |
| 24,600 PE | 24,600 – 24,500 | ₹100 |
| 24,500 PE | 24,500 – 24,500 | ₹0 |
| 24,400 PE | 24,400 – 24,500 = –100 → | ₹0 |
| 24,300 PE | 24,300 – 24,500 = –200 → | ₹0 |

**Key insight:**
- **ITM options** have intrinsic value > 0
- **ATM options** have intrinsic value = 0
- **OTM options** have intrinsic value = 0

---

### Time Value (Extrinsic Value)

**Definition:** The extra value buyers are willing to pay above intrinsic value because there is **time remaining** for the option to potentially become profitable.

$$\text{Time Value} = \text{Premium} - \text{Intrinsic Value}$$

**Example (NIFTY at 24,500, 3 days to expiry):**

| Option | Premium (LTP) | Intrinsic Value | Time Value |
|---|---|---|---|
| 24,300 CE (ITM) | ₹220 | ₹200 | ₹20 |
| 24,400 CE (ITM) | ₹135 | ₹100 | ₹35 |
| 24,500 CE (ATM) | ₹85 | ₹0 | ₹85 |
| 24,600 CE (OTM) | ₹35 | ₹0 | ₹35 |
| 24,700 CE (OTM) | ₹12 | ₹0 | ₹12 |
| 24,800 CE (OTM) | ₹3 | ₹0 | ₹3 |

**Critical observations:**

1. **ATM options have the MAXIMUM time value** (₹85 in this example). This is always true.

2. **Deep ITM options** have very little time value (₹20) — almost all of their premium is intrinsic value.

3. **Deep OTM options** have very little time value (₹3) — but since their intrinsic value is ₹0, their ENTIRE premium is time value.

4. **On expiry day, time value goes to zero.** This means:
   - ATM options lose all their premium (₹85 → ₹0 if NIFTY stays at 24,500)
   - OTM options lose all their premium (they expire worthless)
   - ITM options retain only their intrinsic value

---

## Why This Matters for Your Trading

**When you buy an option, you are paying for two things:**

1. **Intrinsic value** — This doesn't decay. It changes only if NIFTY moves.
2. **Time value** — This decays every second. It goes to zero at expiry.

**As an option buyer, you need NIFTY to move enough to overcome the time value decay.**

If you buy NIFTY 24,500 CE at ₹85 (all time value) and hold until expiry:
- NIFTY needs to be above **24,585** (strike + premium) for you to break even
- NIFTY needs to be above **24,500** for your option to have any value at all
- If NIFTY is at 24,500 or below at expiry, you lose the entire ₹85

This is why **time is the enemy of option buyers** and the **friend of option sellers**.

---

---

# CHAPTER 8: OPTION BUYER vs OPTION SELLER

This is one of the most fundamental distinctions in options trading. You must understand this clearly.

---

## Option Buyer

| Aspect | Detail |
|---|---|
| **Also called** | Option holder, long option |
| **Action** | Pays premium to acquire the option |
| **Risk** | Limited to premium paid |
| **Reward** | Theoretically unlimited (for calls) or large (for puts) |
| **Breakeven** | Strike + Premium (for calls) or Strike – Premium (for puts) |
| **Time decay (Theta)** | Works against the buyer — loses money every day |
| **Volatility** | Benefits from increasing volatility |
| **Win rate** | Typically low (30–40% of option buys are profitable) |
| **Requires** | Strong directional move within a limited time |
| **Capital required** | Only the premium (low capital) |

---

## Option Seller (Writer)

| Aspect | Detail |
|---|---|
| **Also called** | Option writer, short option |
| **Action** | Receives premium by taking on the obligation |
| **Risk** | Potentially very large (unlimited for naked call selling) |
| **Reward** | Limited to premium received |
| **Breakeven** | Strike + Premium (for calls) or Strike – Premium (for puts) |
| **Time decay (Theta)** | Works in seller's favor — earns money every day |
| **Volatility** | Benefits from decreasing volatility |
| **Win rate** | Typically high (60–70% of option sells are profitable) |
| **Requires** | NIFTY to stay within a range (for non-directional strategies) |
| **Capital required** | Very high margin requirement (₹1,00,000+ per lot) |

---

## Comparison

| Feature | Buyer | Seller |
|---|---|---|
| Maximum loss | Premium paid (small) | Very large (potentially unlimited) |
| Maximum profit | Very large (potentially unlimited) | Premium received (small) |
| Win rate | Low (~35%) | High (~65%) |
| Average loss size | Small (premium) | Can be very large |
| Average win size | Can be very large | Small (premium) |
| Time decay | Enemy | Friend |
| Volatility | Friend | Enemy |
| Capital | Low (₹3,000–₹15,000 per lot) | High (₹1,00,000+ per lot) |
| Stress | Lower (loss is capped) | Higher (loss can spiral) |

---

## The Misconception

Many beginners think:

> "Option selling has a 65% win rate, so I should sell options."

This is dangerous thinking. Here's why:

A **65% win rate** with **₹1,000 average profit** and **₹5,000 average loss** gives:

$$E = (0.65 \times 1000) - (0.35 \times 5000) = 650 - 1750 = -₹1,100$$

**Negative expectancy.** You win more often but lose more per loss.

Similarly, a **35% win rate** with **₹5,000 average profit** and **₹1,000 average loss** gives:

$$E = (0.35 \times 5000) - (0.65 \times 1000) = 1750 - 650 = +₹1,100$$

**Positive expectancy.** You win less often but win big when you do.

**The point:** Win rate alone doesn't determine profitability. What matters is **expectancy** — the combination of win rate AND the ratio of average win to average loss.

---

## For This Roadmap

We will focus primarily on **option buying** for several reasons:

1. **Limited risk** — You can never lose more than the premium
2. **No margin calls** — You won't get a scary phone call from your broker
3. **Lower capital** — You can start with ₹20,000–₹30,000
4. **Simpler** — Fewer variables to manage

Option selling requires:
- Much more capital (₹1L+ per lot)
- Understanding of advanced Greeks (especially gamma near expiry)
- Ability to handle unlimited risk scenarios
- More experience

You can learn option selling after you've been consistently profitable with option buying for at least 6 months.

---

---

# CHAPTER 9: NIFTY OPTIONS vs BANK NIFTY OPTIONS vs STOCK OPTIONS

| Feature | NIFTY Options | BANK NIFTY Options | Stock Options |
|---|---|---|---|
| Underlying | NIFTY 50 index | NIFTY Bank index | Individual stock (e.g., Reliance) |
| Lot size | 75 (verify current) | 30 (verify current) | Varies by stock |
| Settlement | Cash settled | Cash settled | Physical delivery |
| Volatility | Moderate | High | Varies |
| Liquidity | Very high | Very high | Varies (some illiquid) |
| Expiry | Weekly (Thursday) | Weekly (Wednesday) | Monthly (last Thursday) |
| Best for beginners | **Yes** | After some experience | After significant experience |
| Strike interval | ₹50 | ₹100 | Varies |

**Physical delivery for stock options** means if you hold an ITM stock option until expiry, you'll receive (or have to deliver) the actual shares. This requires additional margin and can cause unexpected costs. Avoid stock options as a beginner.

**We focus on NIFTY options only.**

---

---

# CHAPTER 10: UNDERSTANDING MARGIN

Margin is the money your broker holds as a security deposit when you trade derivatives.

---

## For Option Buyers

When you **buy** an option, you pay the full premium upfront. There is no additional margin.

**Example:**

Buy 1 lot NIFTY 24,500 CE at ₹150.

Amount required: ₹150 × 75 = **₹11,250**

That's it. This ₹11,250 is debited from your trading account. No margin beyond this.

---

## For Option Sellers

When you **sell** an option, you receive the premium BUT you must maintain a **margin** because your potential loss is unlimited.

**Example:**

Sell 1 lot NIFTY 24,500 CE at ₹150.

- Premium received: ₹150 × 75 = ₹11,250 (credited to you)
- Margin required: Approximately **₹1,00,000 – ₹1,50,000** (held by your broker)

The margin is NOT a charge — it's a deposit. If you close your position without a loss, you get it back.

But if NIFTY moves against you, the margin is used to cover your losses.

---

## SPAN Margin and Exposure Margin

For futures and option selling, the margin consists of two parts:

$$\text{Total Margin} = \text{SPAN Margin} + \text{Exposure Margin}$$

| Type | Purpose |
|---|---|
| **SPAN Margin** | Covers the worst-case one-day loss (calculated by NSE's SPAN system) |
| **Exposure Margin** | Additional buffer for extreme moves beyond SPAN's estimate |

**Check margin requirements:** [zerodha.com/margin-calculator](https://zerodha.com/margin-calculator/SPAN/)

**For option buyers, you don't need to worry about SPAN/exposure margin.** Just know the concept because you'll encounter these terms.

---

---

# CHAPTER 11: PRACTICAL EXERCISES FOR WEEK 3

These exercises are critical. Don't skip them.

---

## Exercise 1: Daily Option Chain Analysis (Do Every Day This Week)

Go to [nseindia.com/option-chain](https://www.nseindia.com/option-chain) at **9:30 AM** and **2:30 PM** every trading day.

Record in your notebook:

| Field | 9:30 AM | 2:30 PM |
|---|---|---|
| NIFTY spot price | | |
| ATM strike | | |
| ATM CE premium | | |
| ATM PE premium | | |
| Highest OI on call side (which strike?) | | |
| Highest OI on put side (which strike?) | | |
| Largest change in OI on call side (which strike, + or –?) | | |
| Largest change in OI on put side (which strike, + or –?) | | |
| ATM CE IV | | |
| ATM PE IV | | |

Do this for 5 trading days. By the end of the week, you will have 10 data points (morning and afternoon for 5 days).

**What to observe:**

- How do ATM premiums change from morning to afternoon? (Time decay)
- How do premiums change from Monday to Thursday? (Expiry effect)
- Do the highest OI levels change during the week?
- Did NIFTY stay within the range defined by highest call OI and highest put OI?

---

## Exercise 2: Track One Option Through Its Entire Life

On **Monday morning**, pick the current week's ATM call option (the call with strike closest to NIFTY spot).

Record its premium at these times every day:

| Day/Time | NIFTY Spot | Option Strike | Premium | Change from Previous |
|---|---|---|---|---|
| Monday 9:30 AM | | | | — |
| Monday 12:00 PM | | | | |
| Monday 3:15 PM | | | | |
| Tuesday 9:30 AM | | | | |
| Tuesday 12:00 PM | | | | |
| Tuesday 3:15 PM | | | | |
| Wednesday 9:30 AM | | | | |
| Wednesday 12:00 PM | | | | |
| Wednesday 3:15 PM | | | | |
| Thursday 9:30 AM | | | | |
| Thursday 12:00 PM | | | | |
| Thursday 1:30 PM | | | | |
| Thursday 3:00 PM | | | | |
| Thursday 3:25 PM | | | | |
| Expiry settlement | | | | |

**What you will learn:**

- How fast premiums decay (especially Wednesday to Thursday)
- How the premium responds to NIFTY movements
- The acceleration of time decay near expiry
- Why holding options through expiry is risky unless deeply ITM

---

## Exercise 3: Intrinsic Value and Time Value Calculation

At any point during the trading day, pick 10 different NIFTY call options (5 ITM and 5 OTM) and calculate:

| Strike | CE Premium (LTP) | NIFTY Spot | Intrinsic Value | Time Value |
|---|---|---|---|---|
| | | | = Spot – Strike (if >0, else 0) | = Premium – Intrinsic |
| | | | | |
| | | | | |
| | | | | |
| | | | | |
| | | | | |
| | | | | |
| | | | | |
| | | | | |
| | | | | |

Now do the same for 10 put options (5 ITM and 5 OTM).

**What to observe:**

- Which options have the highest time value? (ATM)
- Which options have almost zero time value? (Deep ITM and deep OTM)
- What percentage of the premium is time value for ATM options? (It should be nearly 100%)

---

## Exercise 4: Margin Comparison

Go to [zerodha.com/margin-calculator](https://zerodha.com/margin-calculator/SPAN/)

Calculate the margin required for:

| Trade | Your Task |
|---|---|
| Buy 1 lot NIFTY 24,500 CE at ₹150 | How much capital needed? |
| Sell 1 lot NIFTY 24,500 CE at ₹150 | How much margin needed? |
| Buy 1 lot NIFTY 24,500 PE at ₹100 | How much capital needed? |
| Sell 1 lot NIFTY 24,500 PE at ₹100 | How much margin needed? |
| Buy 1 lot NIFTY futures | How much margin needed? |

**What to observe:**

- Option buying requires only the premium (₹7,500 – ₹11,250 per lot)
- Option selling requires ₹1,00,000+ per lot
- Futures require ₹1,00,000+ per lot
- This capital difference is why we start with option buying

---

## Exercise 5: Identify Moneyness for All Strikes

Open the NSE option chain at any time during the trading day.

Note the NIFTY spot price.

Then classify EVERY visible strike as ITM, ATM, or OTM for both calls and puts:

**NIFTY spot: ________**

| Strike | Call Status (ITM/ATM/OTM) | Put Status (ITM/ATM/OTM) |
|---|---|---|
| | | |
| | | |
| | | |
| | | |
| | | |
| | | |
| | | |
| | | |
| | | |
| | | |
| | | |
| | | |

Fill in at least 12 strikes (6 above ATM and 6 below ATM).

Verify that:
- Call ITM is always Put OTM at the same strike (and vice versa)
- Only one strike is ATM (or two if NIFTY is exactly between two strikes)

---

## Exercise 6: Expiry Day Observation (Do This on Thursday)

If you are available during market hours on Thursday:

1. Open the option chain at 9:30 AM, 12:00 PM, 1:30 PM, 2:30 PM, and 3:15 PM
2. Track the ATM call and put premiums at each time
3. Notice how premiums collapse in the afternoon
4. Notice any sudden premium spikes if NIFTY moves sharply in the last hour
5. Record everything

**You should NOT trade on this day.** Just observe and learn.

---

---

# WEEK 3 — SELF-TEST

Answer without looking at the notes.

### Questions

1. What is the difference between a hedger, a speculator, and an arbitrageur?

2. What is mark-to-market (M2M) settlement in futures? Why does it make futures riskier than option buying?

3. What is the lot size for NIFTY options? What is the strike price interval?

4. NIFTY options are European style. What does that mean?

5. What is the difference between weekly expiry and monthly expiry for NIFTY?

6. What is the NIFTY settlement price on expiry day? How is it calculated?

7. NIFTY is at 24,500. You hold 24,500 CE. NIFTY settlement price is 24,650. What is your settlement amount? What if settlement price is 24,400?

8. What are the two components of an option premium?

9. NIFTY is at 24,500. NIFTY 24,300 CE is trading at ₹230. What is the intrinsic value? What is the time value?

10. NIFTY is at 24,500. NIFTY 24,700 CE is trading at ₹15. What is the intrinsic value? What is the time value?

11. Which options have the maximum time value — ITM, ATM, or OTM?

12. What happens to time value at expiry?

13. What is Open Interest (OI)? How is it different from volume?

14. If the 25,000 CE strike has massive call OI buildup, what does that suggest about the 25,000 level?

15. If the 24,000 PE strike has massive put OI buildup, what does that suggest about the 24,000 level?

16. What is the Put-Call Ratio (PCR)? A PCR above 1.2 is considered what?

17. What is Max Pain? Should you trade solely based on Max Pain?

18. As an option buyer, is time decay your friend or enemy?

19. Why should beginners avoid trading the last 2 hours of expiry day?

20. What is the margin requirement difference between buying 1 lot and selling 1 lot of NIFTY options?

21. An option seller has a 65% win rate with ₹1,000 average win and ₹5,000 average loss. Is this a profitable system? Calculate the expectancy.

22. Decode this option name: NIFTY 24600 PE 10-Apr-2025

23. What is the bid-ask spread? Why should you avoid options with a wide bid-ask spread?

24. If NIFTY spot is 24,520, what is the ATM strike on the option chain?

25. An ATM NIFTY weekly call option costs ₹85 on Monday with NIFTY at 24,500. If NIFTY stays at exactly 24,500 the entire week, what will this option be worth at expiry? Why?

---

### Answers

1. **Hedger:** Uses derivatives to protect existing positions from adverse price movements. **Speculator:** Uses derivatives to profit from expected price movements without owning the underlying. **Arbitrageur:** Exploits price differences between related instruments for risk-free profit.

2. M2M means your futures profit or loss is settled in cash at the end of every trading day. This makes futures riskier because you need cash available every day to cover losses, and you can face margin calls that force you to add money or have your position closed.

3. Lot size: 75 (verify current — SEBI revises this). Strike price interval: ₹50.

4. European style means the option can only be exercised at expiry, not before. In practice, you can sell (square off) the option at any time during market hours — you just can't formally exercise it early.

5. Weekly expiry: Every Thursday. Monthly expiry: Last Thursday of each month. Weekly options have shorter life, lower premiums, faster time decay. Monthly options have longer life, higher premiums, slower time decay.

6. The settlement price is the volume-weighted average price (VWAP) of the NIFTY 50 index during the last 30 minutes of trading (3:00 PM – 3:30 PM). It is NOT simply the closing price.

7. Settlement at 24,650: Intrinsic value = 24,650 – 24,500 = ₹150/unit. Settlement amount = 150 × 75 = ₹11,250. Settlement at 24,400: Option is OTM, intrinsic value = 0. Settlement amount = ₹0. You lose the entire premium.

8. Intrinsic Value + Time Value (Extrinsic Value).

9. Intrinsic value = 24,500 – 24,300 = ₹200. Time value = 230 – 200 = ₹30.

10. Intrinsic value = 0 (OTM — strike > spot for calls). Time value = 15 – 0 = ₹15. The entire premium is time value.

11. ATM options have the maximum time value.

12. Time value goes to zero at expiry. Only intrinsic value remains (if any).

13. OI is the total number of outstanding (open) contracts at a strike. Volume is the number of contracts traded today. Volume resets daily; OI is cumulative. Volume is like people walking through a door; OI is like people currently inside the room.

14. It suggests 25,000 is a **resistance** level. Call sellers are betting NIFTY will not cross 25,000.

15. It suggests 24,000 is a **support** level. Put sellers are betting NIFTY will not fall below 24,000.

16. PCR = Total Put OI ÷ Total Call OI. PCR above 1.2 is considered bullish (more put writing than call writing, suggesting sellers expect support to hold).

17. Max Pain is the strike at which maximum options expire worthless, causing maximum loss to buyers and maximum profit to sellers. No, you should NOT trade solely based on Max Pain — it is one indicator among many and doesn't always work.

18. Enemy. Time decay (theta) erodes the option premium every day. The buyer needs NIFTY to move enough to overcome this decay.

19. Because gamma risk is very high near expiry — small NIFTY movements cause large and sudden premium swings. Both buyers and sellers can experience unexpected losses. The market is unpredictable in the final hours of expiry.

20. Buying requires only the premium (₹3,000–₹15,000 per lot). Selling requires margin of ₹1,00,000+ per lot. The selling margin is approximately 10x–15x higher.

21. Expectancy = (0.65 × 1000) – (0.35 × 5000) = 650 – 1750 = **–₹1,100 per trade**. This is NOT profitable despite the 65% win rate. The average loss is too large relative to the average win.

22. Underlying: NIFTY 50 index. Strike price: 24,600. Type: Put option (European). Expiry: 10th April 2025 (Thursday).

23. Bid-ask spread is the difference between the highest bid price and the lowest ask price. A wide spread means high cost of immediate execution — if you buy at the ask and immediately sell at the bid, you lose money equal to the spread × lot size. Illiquid options have wide spreads and should be avoided.

24. ATM strike is the one closest to spot. 24,520 is closest to 24,500 (only ₹20 away) vs 24,550 (₹30 away). So ATM strike = **24,500**.

25. The option will be worth **₹0 at expiry**. Strike = 24,500, NIFTY at expiry = 24,500. Intrinsic value = 24,500 – 24,500 = ₹0. Time value = ₹0 at expiry. The entire ₹85 premium is lost. This demonstrates that ATM options are 100% time value and if the underlying doesn't move, the buyer loses everything.

---

---

# WHAT YOU SHOULD KNOW AFTER WEEK 3

By now, you should be able to:

- [x] Explain how futures work and why they're riskier than options for beginners
- [x] Understand NIFTY options contract specifications (lot size, strike interval, expiry, settlement)
- [x] Know the difference between European and American options
- [x] Understand what happens on expiry day and why the last 2 hours are dangerous
- [x] Read and interpret the NSE option chain (OI, change in OI, volume, IV, LTP, bid-ask)
- [x] Calculate intrinsic value and time value for any option
- [x] Classify any strike as ITM, ATM, or OTM for both calls and puts
- [x] Understand the difference between option buying and option selling
- [x] Understand margin requirements for different derivative instruments
- [x] Calculate expectancy and understand why win rate alone doesn't determine profitability
- [x] Decode option names (underlying, strike, type, expiry)
- [x] Track option premiums through a week and observe time decay in real time

---

**When you've completed all exercises and scored 22/25 or above on the self-test, you're ready for Week 4: Indian Market Structure and Regulation (expiry schedules, lot sizes, margin rules, circuit limits, market sessions, SEBI regulations, and everything you need to know about how the NSE derivatives market is governed).**

Tell me when you're ready.
