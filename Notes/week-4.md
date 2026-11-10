

# WEEK 4 — COMPLETE NOTES

## Indian Market Structure, Regulation, and Everything You Need to Know Before You Trade

This week is different from the previous three. We are not learning new trading concepts. We are learning how the Indian market **actually operates** — the rules, the regulations, the mechanics, the structure. This is the kind of knowledge that separates someone who understands the market from someone who is just clicking buttons on an app.

Most beginners skip this entirely. They go straight from "what is a call option" to placing trades. Then they get surprised by margin shortfalls, penalty charges, auction squares, and regulatory changes.

You will not be one of those people.

---

---

# CHAPTER 1: NSE DERIVATIVES MARKET — COMPLETE STRUCTURE

## What Derivatives Are Available on NSE?

NSE offers derivatives on three categories:

### 1. Index Derivatives

| Index | Futures | Options | Option Expiry |
|---|---|---|---|
| **NIFTY 50** | Yes | Yes (CE and PE) | Weekly (Thursday) + Monthly (last Thursday) |
| **BANK NIFTY** | Yes | Yes (CE and PE) | Weekly (Wednesday) + Monthly (last Thursday) |
| **NIFTY FINANCIAL SERVICES** | Yes | Yes | Monthly |
| **NIFTY MIDCAP SELECT** | Yes | Yes | Monthly |
| **NIFTY NEXT 50** | Yes | Yes | Monthly |

**Your focus: NIFTY 50 options only.**

### 2. Stock Derivatives

Options and futures on individual stocks like Reliance, TCS, HDFC Bank, Infosys, etc.

| Feature | Detail |
|---|---|
| Number of stocks with F&O | Approximately 180–200 (SEBI revises this list) |
| Expiry | Monthly (last Thursday of each month) |
| Settlement | **Physical delivery** (not cash settled) |
| Lot sizes | Varies by stock (e.g., Reliance: 250, TCS: 175, etc.) |

**Do not trade stock options as a beginner.** Physical delivery creates additional margin requirements and complexity.

### 3. Currency Derivatives

Options and futures on currency pairs like USD/INR, EUR/INR, GBP/INR, JPY/INR.

**Not relevant for this roadmap.** Ignore for now.

---

## Contract Cycle

### NIFTY 50 Options Contract Cycle

At any given time, the following NIFTY option contracts are available:

| Contract Type | Number Available | Expiry |
|---|---|---|
| **Weekly contracts** | Approximately 7 weekly expiries | Every Thursday |
| **Monthly contracts** | 3 monthly expiries (current, next, far month) | Last Thursday of each month |

**Example:** Today is March 10, 2025 (Monday)

Available weekly expiries:
- March 13 (this Thursday)
- March 20
- March 27 (this is also the monthly expiry for March)
- April 3
- April 10
- April 17
- April 24

Available monthly expiries:
- March 27, 2025
- April 24, 2025
- May 29, 2025

### Which Expiry Should a Beginner Trade?

**Current week's expiry** — the one expiring this Thursday.

**Why?**

- Highest liquidity (tightest bid-ask spreads)
- Lowest premiums (most affordable)
- Fastest premium movement (most responsive to NIFTY movement)
- Forced discipline (you can't "hold and hope" for weeks)

**Caution:** Current week expiry also has the fastest time decay. If you buy on Monday and NIFTY doesn't move by Wednesday, you've lost significant premium to theta.

---

---

# CHAPTER 2: LOT SIZE — HISTORY, CURRENT, AND WHY IT CHANGES

## What Determines Lot Size?

SEBI determines the minimum contract value for derivatives. The lot size is calculated so that the **minimum contract value** meets SEBI's threshold.

### SEBI's Rule

SEBI periodically sets a **minimum contract size** for derivatives trading. This affects lot size.

**Historical NIFTY lot sizes:**

| Period | Lot Size | Approximate Contract Value |
|---|---|---|
| Before November 2015 | 50 | ~₹4,00,000 |
| November 2015 onwards | 75 | ~₹6,00,000 |
| SEBI proposal (2024) | Under review | SEBI proposed increasing minimum contract size to ₹15,00,000 |

### What Happened in 2024

In 2024, SEBI proposed several changes to the F&O segment:

1. **Increase minimum contract size** from ~₹5–6 lakhs to ₹15–20 lakhs
2. This would mean either the lot size increases significantly or fewer people can afford to trade
3. The stated goal was to protect retail traders from excessive losses

**As of early 2025, some of these changes have been implemented and some are still being rolled out.**

### What You Must Do

**Before you start live trading, always verify the current NIFTY lot size on:**

- [nseindia.com → Derivatives → Contract Specifications](https://www.nseindia.com/products-services/equity-derivatives)
- Your broker's platform

**Do not assume the lot size is 75.** It may have changed by the time you start trading.

---

## How Lot Size Affects Your Capital Requirement

| Lot Size | ATM Premium | Capital for 1 Lot (Buy) | Capital for 2 Lots (Buy) |
|---|---|---|---|
| 25 | ₹150 | ₹3,750 | ₹7,500 |
| 50 | ₹150 | ₹7,500 | ₹15,000 |
| 75 | ₹150 | ₹11,250 | ₹22,500 |
| 100 | ₹150 | ₹15,000 | ₹30,000 |

If SEBI increases the lot size or minimum contract value, you will need more capital to trade even 1 lot.

---

---

# CHAPTER 3: CIRCUIT LIMITS AND TRADING HALTS

## What Are Circuit Limits?

Circuit limits are **automatic trading halts** triggered when the market moves beyond a certain percentage from the previous day's close.

**Purpose:** To prevent panic-driven crashes or irrational euphoria from causing extreme damage in a single day.

---

## Market-Wide Circuit Breakers (for indices)

These apply to the **NIFTY 50 index**:

| Trigger Level | Movement from Previous Close | What Happens |
|---|---|---|
| **Level 1** | **10%** movement | Trading halt for 45 minutes (if triggered before 1:00 PM). 15 minutes if between 1:00–2:30 PM. No halt if after 2:30 PM. |
| **Level 2** | **15%** movement | Trading halt for 1 hour 45 minutes (if before 1:00 PM). 45 minutes if between 1:00–2:30 PM. Trading halted for the day if after 2:30 PM. |
| **Level 3** | **20%** movement | **Trading halted for the remainder of the day**, regardless of time. |

**Example:**

NIFTY previous close: 24,500

- 10% circuit: NIFTY falls to 22,050 or rises to 26,950
- 15% circuit: NIFTY falls to 20,825 or rises to 28,175
- 20% circuit: NIFTY falls to 19,600 or rises to 29,400

**When was the last time this happened?**

- March 2020 (COVID crash): NIFTY hit the 10% lower circuit on March 12 and March 23, 2020. Trading was halted for 45 minutes each time.
- This is extremely rare during normal market conditions.

---

## Stock-Level Circuit Limits

Individual stocks have their own circuit limits:

| Category | Circuit Limit |
|---|---|
| Stocks in derivatives (F&O) | **No fixed circuit limit** — they have a dynamic price band system |
| Stocks NOT in F&O | 2%, 5%, 10%, or 20% circuit limits (varies by stock) |

**Stocks that are part of F&O** (including all NIFTY 50 stocks) use a **dynamic price band** system called the **Operating Range**. This is managed by the exchange and can be widened during the day if the stock is moving sharply.

**What this means for you:**

NIFTY 50 stocks can theoretically move more than 20% in a single day (there's no hard circuit limit). However, the exchange monitors unusual moves and may intervene.

---

## How Circuit Limits Affect Options

When a circuit limit is hit:

1. **Trading stops** for the specified duration
2. **No new orders can be placed** during the halt
3. **Existing orders remain in the order book** but are not matched
4. **When trading resumes**, there can be a significant gap up or gap down
5. **Options premiums can change dramatically** during the halt because the underlying index has moved significantly

**Example (March 2020 crash):**

NIFTY dropped 10% and hit the lower circuit at about 10:05 AM. Trading halted for 45 minutes. When trading resumed at 10:50 AM:

- NIFTY call options had crashed (some lost 70–90% of value)
- NIFTY put options had exploded (some gained 500–2000%)
- Option sellers who had sold puts faced catastrophic losses
- Option sellers couldn't exit during the halt because trading was stopped

**This is why risk management matters more than strategy.** Events like this are rare but they happen.

---

---

# CHAPTER 4: PRE-OPEN SESSION — DETAILED EXPLANATION

## Why Does the Pre-Open Session Exist?

Without a pre-open session, the first trade of the day would happen at 9:15 AM and could be at any random price. If big news broke overnight (company results, global events, etc.), the opening price could be wildly different from the previous close.

The pre-open session **discovers a fair opening price** by collecting orders from everyone and matching them using a **call auction mechanism**.

---

## How It Works — Step by Step

### Phase 1: Order Collection (9:00 AM – 9:08 AM)

During these 8 minutes:

- Traders can place, modify, or cancel orders
- No orders are executed
- Both market orders and limit orders are accepted
- The exchange collects all orders and builds an **indicative order book**
- An **indicative opening price** is displayed (this changes in real-time as orders come in)

### Phase 2: Order Matching (9:08 AM – 9:12 AM)

At a random time between 9:08 and 9:12 (the exact time is randomized to prevent manipulation):

- Order collection stops
- No new orders, modifications, or cancellations are allowed
- The exchange calculates the **equilibrium price** — the price at which the maximum number of shares can be traded
- All eligible orders are matched at this single equilibrium price
- This becomes the **opening price** for the day

### Phase 3: Buffer Period (9:12 AM – 9:15 AM)

- Transition from pre-open to normal market
- Unmatched orders are moved to the normal trading session
- At 9:15 AM, continuous trading begins

---

## Key Points for You

1. **The opening price may gap up or gap down** from the previous close based on overnight news, global markets, and pre-open order flow.

2. **If you place an AMO (After Market Order) for options**, it will be sent to the exchange during the pre-open session. But be aware that the opening price may be very different from what you expected.

3. **Most experienced intraday traders avoid placing orders during the pre-open session** for derivatives. They wait for the first 5–15 minutes of normal trading to see how the market settles.

4. **Do not trade in the first 15 minutes (9:15–9:30 AM).** The initial minutes are dominated by institutional order flow, gap adjustments, and high volatility. Beginners lose money in this window because:
   - Spreads are wider
   - Prices are erratic
   - Stop-losses get hit easily due to random volatility

---

## Pre-Open Session for Derivatives

**Important:** The pre-open session described above applies to the **equity (cash) segment** only.

**For derivatives (futures and options), there is no pre-open session.** Derivatives trading starts directly at **9:15 AM** in continuous trading mode.

However, the equity pre-open session determines the opening price of NIFTY 50 constituent stocks, which in turn determines the opening value of the NIFTY 50 index, which affects NIFTY options premiums at open.

---

---

# CHAPTER 5: CLOSING SESSION AND CLOSING PRICE

## Normal Market Closing (3:30 PM)

At 3:30 PM, the normal trading session ends. But the closing price is not simply the last traded price.

## How the Closing Price Is Calculated

NSE calculates the closing price of each stock using the **weighted average price of the last 30 minutes of trading** (3:00 PM – 3:30 PM).

$$\text{Closing Price} = \text{VWAP of last 30 minutes}$$

If a stock doesn't trade in the last 30 minutes, the last traded price is used.

For the **NIFTY 50 index**, the closing value is calculated from the closing prices of all 50 constituent stocks, weighted by their free-float market caps.

---

## Post-Closing Session (3:40 PM – 4:00 PM)

After a 10-minute gap (3:30–3:40), a **post-closing session** runs from 3:40 to 4:00 PM.

During this session:
- Orders can be placed at the **closing price** only (no other price)
- This allows traders who missed the closing session to transact at the official closing price
- This applies to the equity segment only, not derivatives

---

## Why This Matters for Options

The **NIFTY settlement price on expiry day** is the VWAP of the last 30 minutes. This means:

- The settlement price can differ from the last tick you see at 3:30 PM
- Your ITM option's value at expiry depends on this settlement price, not on the last price you saw on your screen
- Large institutional traders sometimes try to influence the settlement price by placing large orders in the last 30 minutes (this is monitored by SEBI/NSE but still occurs)

---

---

# CHAPTER 6: SEBI REGULATIONS THAT DIRECTLY AFFECT YOU

## Recent SEBI Changes (2024–2025)

SEBI has made several changes specifically targeting the F&O segment to protect retail traders. You must be aware of these.

### 1. Increased Minimum Contract Size

| Before | After (Proposed/Implemented) |
|---|---|
| Minimum contract value ~₹5–6 lakhs | Minimum contract value ₹15+ lakhs |

**Impact:** Lot sizes may increase, making each trade require more capital.

### 2. Rationalization of Weekly Expiries

| Before | After |
|---|---|
| Multiple indices had weekly expiries (NIFTY, BANK NIFTY, FINNIFTY, MIDCAP NIFTY, etc.) | SEBI proposed reducing to **one weekly expiry per exchange** |

**Impact:** This could mean that only NIFTY weekly options (or only BANK NIFTY) are available on NSE. This reduces trading opportunities but also reduces the excessive options trading that was causing retail losses.

**Always check the latest SEBI circular for current rules:** [sebi.gov.in/sebiweb/home/HomeAction.do?doListing=yes&sid=3&ssid=27](https://www.sebi.gov.in/sebiweb/home/HomeAction.do?doListing=yes&sid=3&ssid=27)

### 3. Upfront Collection of Option Premium

| Before | After |
|---|---|
| Some brokers allowed trading on margins for option buying | **Full premium must be collected upfront** from the buyer |

**Impact:** You must have the entire premium amount in your account before buying an option. No leverage for option buying.

### 4. Increase in Margin Near Expiry

| Before | After |
|---|---|
| Normal margin throughout the day | **Additional margin** required for positions held on expiry day |

**Impact:** If you sell options, the margin requirement increases on expiry day (typically by 5–10%). This is to account for the higher gamma risk near expiry.

### 5. Peak Margin Reporting

Brokers must now report **peak margin** usage to the exchange four times daily. If your intraday position exceeds the margin available in your account at any of these snapshots, you face a **penalty**.

**What this means for you:**

- Don't take positions larger than your account can support
- Even for intraday trades, ensure you have adequate margin at all times
- Penalties for margin shortfall are charged to your account

### 6. No Intraday Leverage for Options

Previously, some brokers offered intraday leverage (e.g., 2x or 3x margin) even for options. SEBI has restricted this.

**Current rule:** For option buying, you pay the full premium. No additional leverage.

**For option selling:** You must maintain the full SPAN + exposure margin.

---

## SEBI's Study on F&O Losses — In Detail

This is worth understanding in depth because it shows you what you're up against.

### SEBI Study: September 2024

**Period covered:** FY22, FY23, FY24

**Key findings:**

| Finding | Number |
|---|---|
| Percentage of individual traders who **lost money** | **93%** |
| Total number of individual traders in F&O | ~1 crore (approx. 10 million) |
| Average loss per losing trader | ~₹2,00,000 per year |
| Total losses of individual traders | ~₹1,80,000 crore over 3 years |
| Percentage of individual traders who **made a net profit** | **7%** |
| Of those 7%, percentage who made **more than ₹1 lakh** profit | Less than 3.5% |

### SEBI Study: FY25 Update

**Key finding:** Approximately **91%** of individual traders incurred net losses.

The slight improvement from 93% to 91% may be due to SEBI's regulatory interventions or market conditions. It is not a significant improvement.

### What This Means for You

- **93 out of 100** people who trade F&O lose money
- The average loss is significant — ₹2 lakhs per year
- Even among the 7% who make money, most make only small amounts
- **Transaction costs** (brokerage, STT, taxes) accounted for a significant portion of losses — many traders were profitable before costs but unprofitable after costs
- **Frequent trading** correlated with higher losses — the more you trade, the more you tend to lose

### Why Do Most People Lose?

Based on the SEBI study and other research:

| Reason | Explanation |
|---|---|
| **Overtrading** | Trading too frequently, generating excessive costs |
| **No system** | Trading based on tips, gut feeling, or social media |
| **OTM option buying** | Buying cheap options that almost always expire worthless |
| **No risk management** | No stop-loss, no position sizing, no daily loss limits |
| **Revenge trading** | Increasing trade size after losses to "recover" |
| **Ignoring costs** | Not accounting for STT, brokerage, and other charges |
| **Expiry day gambling** | Buying cheap options on Thursday hoping for a jackpot |
| **Leverage abuse** | Taking positions larger than their capital can support |
| **No backtesting** | Using strategies that have never been tested |
| **Emotional trading** | Fear, greed, FOMO driving decisions instead of rules |

**Your roadmap is specifically designed to avoid every single one of these mistakes.**

---

---

# CHAPTER 7: MARGIN FRAMEWORK — DETAILED UNDERSTANDING

## How NSE Calculates Margin

NSE uses the **SPAN (Standard Portfolio Analysis of Risk)** system developed by the Chicago Mercantile Exchange.

### For Option Buyers

| What You Pay | Amount |
|---|---|
| **Premium** | Full premium upfront |
| **Additional margin** | None |

**Total capital required = Premium × Lot size**

It's that simple. If you buy 1 lot of NIFTY 24,500 CE at ₹150 with lot size 75:

Total = ₹150 × 75 = ₹11,250

This amount is debited from your trading account.

### For Option Sellers

| What You Pay | Amount |
|---|---|
| **SPAN Margin** | Calculated by NSE's risk management system (varies with volatility, strike, expiry) |
| **Exposure Margin** | Additional buffer (typically 2–3% of contract value) |
| **Premium received** | Credited to your account (reduces the net margin required) |

**Total margin required = SPAN Margin + Exposure Margin – Premium Received**

This is typically **₹1,00,000 – ₹1,50,000 per lot** for ATM NIFTY options.

### For Futures

| What You Pay | Amount |
|---|---|
| **SPAN Margin** | ~8–12% of contract value |
| **Exposure Margin** | ~3% of contract value |

**Total margin = SPAN + Exposure**

For NIFTY futures with NIFTY at 24,500 and lot size 75:

Contract value = 24,500 × 75 = ₹18,37,500

Total margin ≈ 12–15% of ₹18,37,500 ≈ **₹2,20,000 – ₹2,75,000**

---

## Margin Shortfall and Penalties

If your account doesn't have enough margin to support your positions:

| Situation | Consequence |
|---|---|
| **Margin shortfall < ₹1 lakh** | Penalty of 0.5% of shortfall per day |
| **Margin shortfall > ₹1 lakh** | Penalty of 1% of shortfall per day |
| **Repeated shortfalls** | Broker may restrict your trading |
| **Extreme shortfall** | Broker will **square off (close) your positions** without your permission |

**This is called a "Risk Management System (RMS) square-off."**

**Example:**

You sell 1 lot NIFTY 24,500 CE. Required margin: ₹1,20,000. Your account has ₹1,10,000.

Shortfall = ₹10,000.

Penalty = 0.5% × ₹10,000 = ₹50 per day.

If NIFTY moves against you and the required margin increases to ₹1,40,000, your shortfall becomes ₹30,000. The broker may automatically close your position.

**For option buyers, this is not an issue** because you pay the full premium upfront and there's no ongoing margin requirement.

---

## Margin Benefit for Hedged Positions

If you have a hedged position (e.g., a bull call spread — buy one call and sell another call at a higher strike), your margin requirement is **lower** than for a naked sold position.

**Example:**

| Position | Margin Required (Approximate) |
|---|---|
| Sell 1 lot NIFTY 24,500 CE (naked) | ₹1,20,000 |
| Sell 1 lot NIFTY 24,500 CE + Buy 1 lot NIFTY 24,700 CE (spread) | ₹25,000 |

The hedge dramatically reduces the margin because your maximum loss is capped.

**This is one reason why spreads (which you'll learn in Phase 3) are more capital-efficient than naked selling.**

---

---

# CHAPTER 8: CORPORATE ACTIONS AND THEIR IMPACT ON DERIVATIVES

## What Are Corporate Actions?

Corporate actions are events initiated by a company that affect its stock price. Since NIFTY options depend on the NIFTY index, which depends on the stock prices of 50 companies, corporate actions of NIFTY 50 companies can affect your options.

### Types of Corporate Actions

| Action | What It Is | Effect on Stock Price | Effect on NIFTY | Effect on Options |
|---|---|---|---|---|
| **Dividend** | Company distributes profit to shareholders | Stock price drops by approximately the dividend amount on ex-date | NIFTY drops slightly | Options adjusted if dividend is "special" |
| **Stock Split** | Company splits each share into multiple shares (e.g., 1:2) | Price halves, number of shares doubles | No net effect on NIFTY (market cap unchanged) | Strike prices and lot sizes are adjusted |
| **Bonus Issue** | Company gives free additional shares to existing shareholders | Price drops proportionally | No net effect on NIFTY | Strike prices and lot sizes are adjusted |
| **Rights Issue** | Company offers existing shareholders the right to buy more shares at a discount | Stock price may drop slightly | Small effect on NIFTY | May result in contract adjustments |
| **Merger/Acquisition** | Two companies combine or one acquires another | Depends on the deal terms | Depends on the companies involved | Complex adjustments |

### How Options Are Adjusted for Corporate Actions

When a corporate action occurs, NSE adjusts the **strike prices** and/or **lot sizes** of the affected stock's options to ensure that the economic value of the contract remains the same.

**For index options (NIFTY), adjustments are rare** because the index automatically reflects the adjusted stock price. However, if a NIFTY constituent stock undergoes a large special dividend, the index value drops accordingly, and this affects your options.

**What you need to do:**

- Be aware of upcoming corporate actions for major NIFTY stocks (HDFC Bank, Reliance, TCS, etc.)
- Check the NSE circulars if you're holding positions during a corporate action
- For now, this is just awareness — you won't encounter this often

---

## Result Season and Options

Every quarter (January, April, July, October), companies announce their financial results. This creates **event-driven volatility**.

**What happens during result season:**

1. **Before results:** Implied Volatility (IV) increases → Options become expensive
2. **Results are announced** (usually after market hours or during market hours)
3. **After results:** IV decreases (IV crush) → Options become cheaper, regardless of direction

**Example:**

Infosys announces results on April 15. On April 14:
- Infosys ATM option has IV of 35%
- Premium: ₹150

On April 15 after results:
- IV drops to 20%
- Even if Infosys stock moves 2% in your favor, the option premium might drop to ₹130 because of IV crush

**How this affects NIFTY options:**

When multiple NIFTY 50 companies announce results in the same week (especially heavyweights like Reliance, TCS, HDFC Bank, Infosys), NIFTY options premiums rise before the announcements and fall after.

**For now, just be aware of this.** You'll study IV and Vega in detail in Phase 3 (Weeks 15–16).

---

---

# CHAPTER 9: GLOBAL FACTORS THAT AFFECT NIFTY

The Indian market does not operate in isolation. Global events influence NIFTY significantly, especially at the open.

---

## Markets That Affect NIFTY

| Market | When It Trades (IST) | How It Affects NIFTY |
|---|---|---|
| **US markets (S&P 500, NASDAQ, Dow Jones)** | 7:00 PM – 1:30 AM (next day) IST | US markets close overnight (India time). A strong US rally usually leads to a positive Indian open. A US crash leads to a negative Indian open. |
| **US futures (S&P 500 futures)** | Nearly 24 hours (most active during US session) | Indian traders watch US futures in the morning (before 9:15 AM) to gauge sentiment |
| **Asian markets (Nikkei, Hang Seng, Shanghai)** | 5:30 AM – 2:30 PM IST (varies) | Asian markets open before India. Their direction gives early cues |
| **European markets (FTSE, DAX)** | 1:30 PM – 10:00 PM IST | European markets open during Indian trading hours. Positive European opening can support Indian markets |
| **SGX NIFTY / GIFT NIFTY** | Nearly 24 hours | NIFTY futures traded on Singapore/GIFT City exchanges. Available before Indian market opens. Gives the best indication of where NIFTY will open |

---

## How to Use This Information

### Morning Routine (8:30 AM – 9:15 AM)

Before the Indian market opens, check:

1. **How did US markets close last night?**
   - Go to [investing.com](https://www.investing.com/) or any financial news site
   - Check S&P 500 and NASDAQ closing % change

2. **Where are US futures trading right now?**
   - Check S&P 500 futures (also on investing.com)
   - If US futures are up, it's a positive signal

3. **How are Asian markets performing?**
   - Check Nikkei 225 (Japan) and Hang Seng (Hong Kong)
   - If Asian markets are up, India usually opens positive

4. **Where is GIFT NIFTY trading?**
   - This is the most direct indicator of where NIFTY will open
   - If GIFT NIFTY is at 24,550 and yesterday's NIFTY close was 24,500, expect a gap-up opening of about 50 points

**Do NOT trade based on global markets alone.** This is just context-setting for your morning analysis.

---

## Key Global Events That Move Indian Markets

| Event | Frequency | Impact |
|---|---|---|
| **US Fed interest rate decision** | 8 times per year | Very high — affects global liquidity and FII flows |
| **US jobs data (Non-Farm Payrolls)** | Monthly (first Friday) | High — strong US jobs → stronger dollar → FII outflows from India |
| **US inflation data (CPI)** | Monthly | High — higher inflation → higher interest rates → negative for markets |
| **China economic data** | Monthly/quarterly | Moderate — China weakness can affect Asian sentiment |
| **Oil prices** | Continuous | High — India is a major oil importer. Higher oil → higher inflation → negative for India |
| **US-China trade tensions** | Irregular | Moderate to high |
| **Geopolitical events** | Irregular | Variable — wars, sanctions, elections |

---

## Key Indian Events That Move NIFTY

| Event | Frequency | Impact |
|---|---|---|
| **RBI monetary policy (interest rate decision)** | 6 times per year (bi-monthly) | Very high — rate cuts are positive, rate hikes are negative |
| **Union Budget** | Once per year (February 1) | Very high — tax changes, spending plans, sector impacts |
| **GDP data** | Quarterly | Moderate |
| **Inflation data (CPI, WPI)** | Monthly | Moderate to high |
| **Industrial production (IIP)** | Monthly | Moderate |
| **GST collection data** | Monthly | Moderate (indicator of economic activity) |
| **General elections** | Every 5 years | Very high — policy uncertainty vs. policy continuity |
| **State elections** | Periodic | Low to moderate |
| **FII/DII data** | Daily | High — persistent FII selling is very negative for markets |

### FII and DII Data

**FII (Foreign Institutional Investors):**
- Include hedge funds, mutual funds, pension funds from outside India
- When FIIs buy heavily → Market tends to rise
- When FIIs sell heavily → Market tends to fall
- FIIs have sold over ₹1,00,000 crore in some periods, causing market declines

**DII (Domestic Institutional Investors):**
- Include Indian mutual funds, insurance companies (LIC), pension funds
- DIIs often buy when FIIs sell, providing some support
- Increasing SIP (Systematic Investment Plan) flows have strengthened DII buying power

**Where to check FII/DII data:**
- [moneycontrol.com → Markets → FII/DII Activity](https://www.moneycontrol.com/stocks/marketstats/fii_dii_activity/index.php)
- [nseindia.com → Market Data → FII/DII data](https://www.nseindia.com/)

---

---

# CHAPTER 10: TAXATION FOR F&O TRADERS — COMPLETE GUIDE

This is not optional. If you trade F&O, you have tax obligations. Ignoring them can lead to penalties and legal problems.

---

## How F&O Income Is Classified

| Type of Trading | Tax Classification |
|---|---|
| **Equity delivery** (buying shares and holding > 1 year) | Long-term capital gains (LTCG) |
| **Equity delivery** (holding < 1 year) | Short-term capital gains (STCG) |
| **Equity intraday** (buying and selling same day) | Speculative business income |
| **F&O trading** (futures and options) | **Non-speculative business income** |

**F&O income is treated as BUSINESS INCOME, not capital gains.**

This has significant implications for:
- Which ITR form you file
- Whether you need a tax audit
- How losses can be set off
- What expenses you can claim

---

## Tax Rate for F&O Income

F&O income is added to your total income and taxed according to your **income tax slab**.

| Total Income (including F&O) | Tax Rate (Old Regime) | Tax Rate (New Regime) |
|---|---|---|
| Up to ₹2.5 lakh | 0% | Up to ₹3 lakh: 0% |
| ₹2.5 – ₹5 lakh | 5% | ₹3 – ₹7 lakh: 5% |
| ₹5 – ₹10 lakh | 20% | ₹7 – ₹10 lakh: 10% |
| Above ₹10 lakh | 30% | ₹10 – ₹12 lakh: 15% |
| | | ₹12 – ₹15 lakh: 20% |
| | | Above ₹15 lakh: 30% |

**Example:**

Your salary income: ₹8,00,000
Your F&O profit: ₹2,00,000
Total income: ₹10,00,000

You'll be taxed according to the slab applicable to ₹10,00,000 (not separately on F&O income).

---

## Turnover Calculation for F&O

The **turnover** determines whether you need a tax audit.

### How to Calculate F&O Turnover

$$\text{Turnover} = \text{Sum of absolute values of all trade-wise profits and losses}$$

**Example:**

| Trade | P&L |
|---|---|
| Trade 1 | +₹5,000 |
| Trade 2 | –₹3,000 |
| Trade 3 | +₹8,000 |
| Trade 4 | –₹12,000 |
| Trade 5 | +₹2,000 |

**Net P&L** = +5,000 – 3,000 + 8,000 – 12,000 + 2,000 = **₹0** (breakeven)

**Turnover** = |5,000| + |3,000| + |8,000| + |12,000| + |2,000| = **₹30,000**

Note: Turnover is much higher than net P&L because it counts absolute values.

For options specifically, some CAs use:

$$\text{Options Turnover} = \text{Sum of absolute (settlement price – premium)} \times \text{lot size for each trade}$$

**The method of turnover calculation has some ambiguity.** Consult a CA for your specific situation.

---

## Tax Audit Requirement

| Condition | Tax Audit Required? |
|---|---|
| Turnover > ₹10 crore (if transactions are predominantly digital) | **Yes** |
| Turnover > ₹2 crore (if any non-digital transactions) | **Yes** |
| Turnover < ₹2 crore AND net profit ≥ 6% of turnover | **No** (can use presumptive taxation under 44AD) |
| Turnover < ₹2 crore AND net profit < 6% of turnover | **Yes** (must get tax audit) |
| F&O loss (negative profit) | **Yes** (must get tax audit to carry forward the loss) |

**Important:** If you have an F&O loss and want to carry it forward to set off against future year's income, you **must file ITR before the due date** and **must get a tax audit** if applicable.

---

## Which ITR Form to File

| Your Situation | ITR Form |
|---|---|
| Only salary income | ITR-1 |
| Salary + capital gains (stocks, mutual funds) | ITR-2 |
| Salary + F&O income/loss | **ITR-3** |
| Only F&O income (no salary) | **ITR-3** |

**If you trade F&O at all, you must file ITR-3.** This is non-negotiable.

---

## Setting Off F&O Losses

| F&O Loss Can Be Set Off Against | Yes/No |
|---|---|
| Other business income | **Yes** |
| Salary income | **No** |
| Rental income | **No** |
| Capital gains (stocks, property) | **No** |
| Interest income | **No** |
| Future year's business income (carry forward) | **Yes, for up to 8 years** |

**Example:**

Year 1: F&O loss of ₹1,00,000. No other business income. You can carry this loss forward.

Year 2: F&O profit of ₹1,50,000. You set off ₹1,00,000 from Year 1's loss. You pay tax only on ₹50,000 of F&O income.

**But if your only other income is salary (₹8 lakhs), you cannot set off the F&O loss against salary.** The ₹1,00,000 loss sits as a carry-forward amount.

---

## Expenses You Can Deduct

Since F&O income is business income, you can deduct legitimate business expenses:

| Expense | Deductible? |
|---|---|
| Internet charges (proportional to trading use) | Yes |
| Computer/laptop (depreciation) | Yes |
| Mobile phone (proportional) | Yes |
| Trading-related software subscriptions | Yes |
| Books and courses related to trading | Yes |
| Brokerage and transaction charges | Already accounted for in P&L |
| Advisory fees paid to SEBI-registered advisors | Yes |
| Rent for office space used exclusively for trading | Yes |
| Electricity (proportional) | Yes |

**Keep receipts and records for all deductions.**

---

## Practical Steps

1. **Maintain your trading journal** (this also serves as a business record)
2. **Download your trade reports** from your broker at the end of each month
3. **Keep records of all expenses** related to trading
4. **Consult a CA** before the end of the financial year (March 31)
5. **File ITR-3** before the due date (usually July 31 for non-audit cases, October 31 if audit is required)

---

## Where to Learn More About F&O Taxation

| Resource | Link |
|---|---|
| Zerodha — Taxation for Traders | [zerodha.com/z-connect/queries/stock-and-f-o-queries/taxation-for-traders](https://zerodha.com/z-connect/queries/stock-and-f-o-queries/taxation-for-traders-pair-off-and-speculative) |
| ClearTax — F&O Taxation | [cleartax.in/s/income-tax-on-share-trading](https://cleartax.in/s/income-tax-on-share-trading) |
| Quicko — F&O Tax Guide | [quicko.com](https://quicko.com/) |

---

---

# CHAPTER 11: THINGS THAT CAN GO WRONG (AND HOW TO AVOID THEM)

Before you start live trading, you must know what can go wrong. This is not to scare you but to prepare you.

---

## Problem 1: Broker Technical Issues

**What can happen:**
- Broker's app crashes during market hours
- Orders fail to execute
- Positions show incorrect data
- Server is slow during high-volatility moments

**How to prepare:**
- Have your broker's **customer support number** saved in your phone
- Know how to place orders via the **broker's website** (not just the app)
- Know how to call your broker to manually close positions (phone order)
- Consider having a **backup broker account** (you can have accounts with multiple brokers)
- Never risk more than you can afford to lose if the app crashes

---

## Problem 2: Internet/Power Failure

**What can happen:**
- Your internet drops during an open position
- Power cuts during market hours

**How to prepare:**
- Use mobile data as backup for Wi-Fi
- Keep your phone charged at all times during market hours
- If you have an open position and lose connectivity, your **stop-loss order** (if already placed) will still work because it sits on the exchange server
- This is why you should **always place your stop-loss immediately after entry**, not later

---

## Problem 3: Flash Crash

**What can happen:**
- NIFTY drops 300–500 points in minutes due to some event
- Call option premiums crash to near zero
- Put option premiums explode
- Stop-loss orders may execute at prices far worse than expected (slippage)

**How to prepare:**
- Never risk more than 1–2% of your capital on a single trade
- Always have a stop-loss in place
- Don't hold naked sold positions (especially naked calls)
- Accept that events like this will happen — your risk management must account for it

---

## Problem 4: Regulatory Changes

**What can happen:**
- SEBI changes lot sizes, margin requirements, or expiry schedules
- A new tax is introduced (e.g., increased STT)
- Trading rules change mid-contract

**How to prepare:**
- Stay updated with SEBI circulars
- Follow your broker's notifications
- Don't build a strategy that depends on specific regulatory conditions without being prepared for changes

---

## Problem 5: Illiquidity

**What can happen:**
- You buy a deep OTM option or a far-month option
- When you want to sell, there are no buyers
- You're stuck with a position you can't exit

**How to prepare:**
- Trade only liquid strikes (ATM and 1–2 strikes around ATM)
- Trade the current week's expiry (most liquid)
- Always check the bid-ask spread before entering — if the spread is more than ₹1–₹2, avoid that strike
- Avoid deep OTM options (beyond 5–6 strikes from ATM)

---

## Problem 6: STT on Expiry for ITM Options

**What can happen:**

If you hold an **ITM option** until expiry and it is exercised, **STT is charged on the full settlement value**, not on the premium.

**Example:**

You hold NIFTY 24,300 CE. NIFTY settlement price: 24,650.

Intrinsic value = 24,650 – 24,300 = ₹350 per unit.

Settlement value = ₹350 × 75 = ₹26,250.

STT on exercise = **0.125% × Settlement value** (note: higher rate for exercise)

STT = 0.125% × ₹26,250 = **₹32.81**

But if you had **sold the option before expiry** at ₹350:

STT = 0.0625% × (₹350 × 75) = 0.0625% × ₹26,250 = **₹16.41**

**The STT on exercise is double the normal sell-side STT.**

**Lesson: Square off ITM positions before expiry to avoid the higher STT.** Most brokers will automatically square off deep ITM options 30 minutes before market close on expiry day.

---

---

# CHAPTER 12: YOUR BROKER'S RISK MANAGEMENT SYSTEM (RMS)

## What Is RMS?

Every broker has a **Risk Management System** that automatically monitors your positions and margin.

### What RMS Does

| Action | When |
|---|---|
| **Blocks order** | If you don't have enough margin/funds for the trade |
| **Sends margin call** | If your margin falls below the required level |
| **Auto squares off positions** | If margin shortfall exceeds a threshold |
| **Blocks new positions** | If you've hit your daily loss limit (some brokers offer this feature) |

### Auto Square-Off

Most brokers auto square off intraday positions at a specific time:

| Broker | Auto Square-Off Time |
|---|---|
| Zerodha | 3:15 PM – 3:20 PM for intraday orders (MIS/product type) |
| Dhan | Similar timeframe |
| Groww | Similar timeframe |

**What this means:**

If you take an intraday position (product type MIS on Zerodha), your broker will automatically close the position around 3:15–3:20 PM if you haven't closed it yourself.

If you want to hold the position overnight, you must select **NRML** (normal) product type. But for option buying, this means paying the full premium.

### Product Types

| Product Type | Meaning | When to Use |
|---|---|---|
| **MIS** (Margin Intraday Square-off) | Intraday only — auto squared off by 3:15 PM | When you want to trade intraday and close before market ends |
| **NRML** (Normal) | Can hold overnight or until expiry | When you want to hold a position beyond today |

**For option buying, the capital required is the same for both MIS and NRML** (full premium). The only difference is whether the broker auto-closes your position at 3:15 PM (MIS) or lets you hold it (NRML).

---

---

# CHAPTER 13: PRACTICAL EXERCISES FOR WEEK 4

## Exercise 1: Check Current Contract Specifications

Go to [nseindia.com/products-services/equity-derivatives](https://www.nseindia.com/products-services/equity-derivatives)

Find and record:

| Parameter | NIFTY Options | BANK NIFTY Options |
|---|---|---|
| Current lot size | | |
| Strike price interval | | |
| Weekly expiry day | | |
| Monthly expiry day | | |
| Settlement type | | |
| Available expiries (list them) | | |

Also check your broker's platform for the same information. Do the numbers match?

---

## Exercise 2: Identify All Events for the Current Month

Create a calendar for the current month and mark:

| Date | Event | Expected Impact on NIFTY |
|---|---|---|
| | RBI policy meeting (if scheduled) | High |
| | NIFTY weekly expiry (every Thursday) | Moderate |
| | Major company results (check moneycontrol.com) | Moderate to High |
| | US Fed meeting (if scheduled) | High |
| | US jobs data (first Friday) | Moderate |
| | India CPI/inflation data (if scheduled) | Moderate |
| | Any trading holidays | N/A — market closed |

**Why this matters:** You should be aware of upcoming events before taking positions. Option premiums increase before events (IV rises) and decrease after (IV crush).

---

## Exercise 3: Check GIFT NIFTY Every Morning for 5 Days

Every morning between 8:30 AM and 9:00 AM, check GIFT NIFTY (or SGX NIFTY) on:

- [investing.com](https://www.investing.com/) — search for "GIFT NIFTY"
- Google: "GIFT NIFTY live"

Record:

| Day | Previous NIFTY Close | GIFT NIFTY at 8:45 AM | Expected Gap | Actual NIFTY Open (at 9:15 AM) | Was Your Prediction Correct? |
|---|---|---|---|---|---|
| Monday | | | | | |
| Tuesday | | | | | |
| Wednesday | | | | | |
| Thursday | | | | | |
| Friday | | | | | |

**What to learn:** GIFT NIFTY gives a fairly accurate indication of where NIFTY will open. But it's not perfect — the actual open can differ by 20–50 points.

---

## Exercise 4: Check FII/DII Data for 5 Days

Every evening, check FII and DII data:

Go to: [moneycontrol.com → Markets → FII/DII Activity](https://www.moneycontrol.com/stocks/marketstats/fii_dii_activity/index.php)

Record:

| Day | FII Net (₹ crores) | DII Net (₹ crores) | NIFTY Change (%) | Observation |
|---|---|---|---|---|
| Monday | | | | |
| Tuesday | | | | |
| Wednesday | | | | |
| Thursday | | | | |
| Friday | | | | |

**What to observe:**
- On days when FII was a strong net seller, did NIFTY fall?
- When both FII and DII bought, did NIFTY rise significantly?
- Is there a pattern of persistent FII selling or buying this week?

---

## Exercise 5: Calculate Margin for Different Positions

Go to [zerodha.com/margin-calculator](https://zerodha.com/margin-calculator/SPAN/)

Calculate and compare:

| Position | Capital Required |
|---|---|
| Buy 1 lot NIFTY ATM CE | |
| Buy 2 lots NIFTY ATM CE | |
| Sell 1 lot NIFTY ATM CE (naked) | |
| Buy 1 lot NIFTY ATM CE + Sell 1 lot NIFTY OTM CE (bull call spread) | |
| Sell 1 lot NIFTY ATM PE (naked) | |
| Buy 1 lot NIFTY Futures | |
| Buy 1 lot BANK NIFTY ATM CE | |

**What to observe:**
- How much less margin is needed for a spread vs. naked selling?
- How does option buying capital compare to futures margin?
- How does NIFTY option capital compare to BANK NIFTY?

---

## Exercise 6: Calculate Your Tax Obligation (Hypothetical)

Assume you made the following trades in a financial year:

| Trade | P&L |
|---|---|
| Trade 1 | +₹15,000 |
| Trade 2 | –₹8,000 |
| Trade 3 | +₹22,000 |
| Trade 4 | –₹35,000 |
| Trade 5 | +₹10,000 |
| Trade 6 | –₹5,000 |
| Trade 7 | +₹18,000 |
| Trade 8 | –₹12,000 |
| Trade 9 | +₹7,000 |
| Trade 10 | –₹20,000 |

Calculate:

1. Net P&L for the year
2. Turnover (sum of absolute values)
3. Is the net P&L positive or negative?
4. If negative, can you set off this loss against your salary of ₹6,00,000?
5. Do you need a tax audit? (Assume turnover < ₹2 crore)
6. What ITR form should you file?

**Answers:**

1. Net P&L = 15,000 – 8,000 + 22,000 – 35,000 + 10,000 – 5,000 + 18,000 – 12,000 + 7,000 – 20,000 = **–₹8,000** (net loss)

2. Turnover = 15,000 + 8,000 + 22,000 + 35,000 + 10,000 + 5,000 + 18,000 + 12,000 + 7,000 + 20,000 = **₹1,52,000**

3. Net P&L is **negative** (loss of ₹8,000)

4. **No**, F&O losses cannot be set off against salary income. The loss must be carried forward.

5. Since turnover < ₹2 crore but there is a **net loss**, you **must get a tax audit** if you want to carry forward the loss (under Section 44AB). If you don't want to carry forward the loss, audit may not be required, but consult a CA.

6. **ITR-3**

---

## Exercise 7: Review SEBI Circulars

Go to: [sebi.gov.in → Legal → Circulars](https://www.sebi.gov.in/sebiweb/home/HomeAction.do?doListing=yes&sid=3&ssid=27)

Find and read any **2 recent circulars related to derivatives or F&O**.

Write down:
- What is the circular about?
- Does it affect NIFTY options trading?
- Is there any rule change that impacts your trading plan?

**You don't need to understand every legal detail.** Just get comfortable reading SEBI communications. This is a skill that will protect you from surprises.

---

---

# WEEK 4 — SELF-TEST

### Questions

1. Name four indices that have derivatives available on NSE.

2. What is the difference between weekly and monthly expiry contracts for NIFTY?

3. Which expiry should a beginner trade and why?

4. What is the current NIFTY lot size? (Check the latest)

5. Why does SEBI change lot sizes?

6. What are the three levels of market-wide circuit breakers? What happens at each level?

7. When was the last time a market-wide circuit breaker was triggered in India?

8. Does the pre-open session apply to derivatives? When does derivatives trading start?

9. How is the closing price of a stock calculated on NSE?

10. How is the NIFTY settlement price calculated on expiry day?

11. What does the SEBI study say about the percentage of individual F&O traders who lose money?

12. Name five reasons why most F&O traders lose money.

13. For option buyers, what capital is required? For option sellers, what margin is required?

14. What happens if you have a margin shortfall?

15. What is the difference between MIS and NRML product types?

16. How is F&O income classified for tax purposes?

17. Which ITR form must F&O traders file?

18. Can F&O losses be set off against salary income?

19. What is F&O turnover and how is it calculated?

20. When is a tax audit required for F&O traders?

21. What is GIFT NIFTY and how can you use it?

22. What are FII and DII? How does their buying/selling affect NIFTY?

23. What happens to STT if you let an ITM option expire instead of squaring off?

24. What is IV crush? When does it happen?

25. Why should you avoid trading in the first 15 minutes after market opens?

---

### Answers

1. NIFTY 50, BANK NIFTY, NIFTY FINANCIAL SERVICES, NIFTY MIDCAP SELECT (also NIFTY NEXT 50). Any four of these.

2. Weekly expiry: Every Thursday. Shorter life, lower premiums, faster time decay, highest liquidity for current week. Monthly expiry: Last Thursday of month. Longer life, higher premiums, slower time decay, available for 3 months ahead.

3. Current week's expiry. Because it has the highest liquidity (tightest spreads), lowest premiums (most affordable), and forces discipline (can't hold indefinitely).

4. Check [nseindia.com](https://www.nseindia.com/) for the current lot size. As of writing, it is 75, but SEBI may have changed it.

5. SEBI changes lot sizes to ensure the minimum contract value meets their threshold. When NIFTY rises significantly, the existing lot size may create a contract value that SEBI considers too low, so they increase the lot size. Conversely, they may want to increase minimum contract value to discourage excessive retail speculation.

6. Level 1 (10% move): 45-minute halt if before 1 PM, 15 minutes if 1–2:30 PM, no halt if after 2:30 PM. Level 2 (15% move): 1h 45min halt if before 1 PM, 45 minutes if 1–2:30 PM, market closed for day if after 2:30 PM. Level 3 (20% move): Market closed for the remainder of the day regardless of time.

7. March 2020 during the COVID-19 crash. The 10% lower circuit was triggered on March 12 and March 23, 2020.

8. No, the pre-open session applies only to the equity (cash) segment. Derivatives trading starts directly at 9:15 AM in continuous trading mode.

9. The closing price is the Volume Weighted Average Price (VWAP) of the last 30 minutes of trading (3:00 PM – 3:30 PM).

10. The settlement price on expiry day is the VWAP of the NIFTY 50 index during the last 30 minutes of trading (3:00 PM – 3:30 PM). It is not the last traded price at 3:30 PM.

11. 93% of individual F&O traders lost money (FY22–FY24, SEBI September 2024 study). Approximately 91% lost money in FY25 data.

12. Any five of: Overtrading, no system/strategy, buying OTM options that expire worthless, no risk management (no stop-loss), revenge trading, ignoring costs, expiry day gambling, leverage abuse, no backtesting, emotional trading.

13. Option buyers: Full premium upfront (e.g., ₹11,250 for 1 lot at ₹150 premium). Option sellers: SPAN + Exposure margin, typically ₹1,00,000–₹1,50,000 per lot.

14. Margin shortfall < ₹1 lakh: 0.5% penalty per day. > ₹1 lakh: 1% per day. The broker may also auto-square-off your position.

15. MIS (Margin Intraday Square-off): Intraday only, position auto-closed by ~3:15 PM. NRML (Normal): Can hold overnight or until expiry. For option buying, capital required is the same for both; the difference is whether the broker auto-closes your position.

16. Non-speculative business income. It is NOT capital gains.

17. ITR-3.

18. No. F&O losses can only be set off against other business income. They cannot be set off against salary income. They can be carried forward for up to 8 years to set off against future business income.

19. Turnover = Sum of absolute values of all trade-wise profits and losses. Each trade's P&L (whether positive or negative) is taken as a positive number and added up.

20. Tax audit is required if: (a) turnover exceeds ₹10 crore (digital transactions), or (b) turnover exceeds ₹2 crore (non-digital), or (c) turnover < ₹2 crore but net profit < 6% of turnover, or (d) you have a net loss and want to carry it forward. Consult a CA for your specific situation.

21. GIFT NIFTY is NIFTY futures traded on the GIFT City (Gujarat) exchange, which operates nearly 24 hours. You can check GIFT NIFTY before the Indian market opens to get an indication of where NIFTY will open (gap up or gap down).

22. FII = Foreign Institutional Investors (overseas funds). DII = Domestic Institutional Investors (Indian mutual funds, insurance companies). Persistent FII buying tends to push markets up; persistent FII selling tends to push markets down. DII often acts as a counterbalance.

23. If you let an ITM option expire, STT is charged at 0.125% on the full settlement value (intrinsic value × lot size). This is double the normal sell-side STT rate of 0.0625%. Square off before expiry to avoid the higher STT.

24. IV crush is the rapid decrease in implied volatility after a major event (earnings, RBI policy, budget, elections). Options premiums drop sharply after the event even if the direction moves in your favor. This happens because the uncertainty that was priced into options disappears after the event.

25. The first 15 minutes (9:15–9:30 AM) have high volatility from gap adjustments, institutional order flow, and erratic price movements. Spreads are wider, stop-losses get hit easily, and price direction is unreliable. Beginners should wait for the market to settle.

---

---

# MONTH 1 — COMPLETE REVIEW

You have now completed all four weeks of Phase 1. Before moving to Phase 2 (Technical Analysis), take this weekend to review everything.

---

## What You Have Learned in Month 1

| Week | Topics Covered |
|---|---|
| **Week 1** | Stocks, shares, primary/secondary market, NSE/BSE, NIFTY 50, BANK NIFTY, SENSEX, ETFs, introduction to futures and options, ITM/ATM/OTM, market cap, market timings, SEBI |
| **Week 2** | Demat and trading accounts, broker types, all order types (market, limit, SL, SL-M, GTT, AMO), settlement cycle, clearing corporation, all six trading charges with detailed calculations |
| **Week 3** | Derivatives in depth, futures M2M, options contract specifications, expiry mechanics, European vs American, lot size and tick size, option chain reading (OI, change in OI, volume, IV, bid-ask), intrinsic and time value, option buyer vs seller, expectancy calculation |
| **Week 4** | NSE derivatives structure, contract cycle, lot size history and SEBI changes, circuit breakers, pre-open and closing sessions, SEBI regulations (2024–2025 changes), margin framework, corporate actions, global factors, FII/DII, taxation, things that can go wrong, broker RMS |

---

## Month 1 Comprehensive Checklist

Ask yourself these questions. Every answer should be **yes** and you should be able to explain each concept confidently:

- [ ] I can explain what a stock is and why companies issue them
- [ ] I know the difference between NSE and BSE and which is important for F&O
- [ ] I can explain what NIFTY 50 is and how it's calculated
- [ ] I can identify the top 5 NIFTY 50 stocks by weight
- [ ] I understand the difference between futures and options
- [ ] I can explain what a call option and put option are with examples
- [ ] I can classify any strike as ITM, ATM, or OTM for both calls and puts
- [ ] I know all six types of orders and when to use each
- [ ] I can calculate the total charges for any NIFTY options trade
- [ ] I understand settlement (T+1 for equity, same-day for intraday F&O)
- [ ] I can read the NSE option chain and identify key information
- [ ] I can calculate intrinsic value and time value for any option
- [ ] I understand why time decay destroys option buyers who hold without direction
- [ ] I know the difference between option buyer and option seller risk profiles
- [ ] I can calculate expectancy and understand why win rate alone doesn't matter
- [ ] I know what circuit breakers are and when they trigger
- [ ] I understand margin requirements for buying vs selling options
- [ ] I know how F&O income is taxed and which ITR form to file
- [ ] I understand FII/DII activity and how to check it
- [ ] I know why the first 15 minutes and last 2 hours of expiry day are dangerous
- [ ] I know how to check GIFT NIFTY for gap-up/gap-down indication
- [ ] I can explain at least 5 reasons why 93% of F&O traders lose money

**If you can check every box, you have a strong foundation. You are ready for Phase 2.**

**If any box is unchecked, go back and revise that topic before moving forward. There is no deadline. Understanding matters more than speed.**

---

**When you're ready for Week 5 (Candlestick Basics — the beginning of Technical Analysis), tell me and I'll write the complete material.**
