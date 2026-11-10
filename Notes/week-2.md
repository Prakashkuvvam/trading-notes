# WEEK 2 — COMPLETE NOTES

## How Trading Actually Works: Accounts, Orders, Brokers, and Every Single Charge

---

---

# CHAPTER 1: TRADING ACCOUNT AND DEMAT ACCOUNT

## The Two Accounts You Need

To trade in the Indian stock market, you need **two accounts**. Most people confuse them or think they're the same thing. They are not.

### 1. Demat Account (Dematerialized Account)

**Purpose:** Holds your shares and securities in electronic form.

**Analogy:** Think of it as a **bank locker** for your shares. Just as a bank locker holds your physical gold and documents, a demat account holds your shares, bonds, mutual fund units, and ETFs electronically.

**Key facts:**
- You cannot hold physical share certificates anymore (dematerialization became mandatory in 1999)
- When you buy shares for delivery (holding overnight or longer), they are credited to your demat account
- When you sell shares from your holdings, they are debited from your demat account
- Maintained by a **Depository** — either **NSDL** (National Securities Depository Limited) or **CDSL** (Central Depository Services Limited)
- Your broker acts as a **Depository Participant (DP)** — an intermediary between you and the depository
- You get a **DP ID** and a **Client ID** (together called your BO ID — Beneficial Owner ID)

**Example:**

You buy 100 shares of Reliance at ₹2,500 each. After settlement (T+1 day), 100 shares of Reliance appear in your demat account. You can see them in your broker's app under "Holdings."

### 2. Trading Account

**Purpose:** Used to place buy and sell orders on the stock exchange.

**Analogy:** Think of it as your **trading desk**. This is where you actually execute trades — clicking buy or sell.

**Key facts:**
- Linked to your demat account
- Linked to your bank account (for fund transfers)
- Through this account, your orders reach NSE or BSE
- You can place orders for stocks, futures, and options through this account

### 3. Bank Account (Your Existing Account)

**Purpose:** Source of funds for trading and destination for withdrawals.

**How money flows:**

```
YOUR BANK ACCOUNT
      ↓ (add funds)
TRADING ACCOUNT (margin available for trading)
      ↓ (buy shares for delivery)
DEMAT ACCOUNT (shares stored here)
      ↓ (sell shares)
TRADING ACCOUNT (sale proceeds come here)
      ↓ (withdraw)
YOUR BANK ACCOUNT
```

---

## Do You Need Both for Options Trading?

**For NIFTY options intraday trading:**

- You **do** need a trading account
- You **do** need a demat account (it's opened along with the trading account)
- But your options positions are **not stored in your demat account** because:
  - Intraday options are squared off the same day
  - Even if you hold options overnight, they are **derivative positions**, not delivery shares
  - Options expire — they don't sit in your demat like shares do

**However**, brokers open both accounts together as a package. You cannot open a trading account without a demat account.

---

## What About a Margin Account?

Some brokers refer to your trading account as a **margin account** when you trade derivatives (futures and options). This is because:

- For **option buying**, you need to pay the full premium upfront (no margin benefit)
- For **option selling**, you need to maintain a **margin** (a security deposit) with the broker
- For **futures**, you need to maintain a margin (span margin + exposure margin)

We will cover margin requirements in detail in Phase 3. For now, just know that your trading account serves as your margin account for derivatives.

---

---

# CHAPTER 2: WHAT IS A BROKER?

## Definition

A **broker** is a SEBI-registered intermediary who connects you (the retail trader) to the stock exchange (NSE/BSE).

You **cannot** place orders directly on NSE. You must go through a broker.

---

## Types of Brokers in India

### 1. Full-Service Brokers

| Feature | Details |
|---|---|
| **What they offer** | Trading, research reports, advisory, IPO assistance, mutual funds, relationship manager |
| **Brokerage** | Higher — typically 0.03% to 0.05% of trade value or a minimum of ₹30–₹50 per trade |
| **Examples** | ICICI Direct, HDFC Securities, Kotak Securities, Motilal Oswal, Angel One (hybrid) |
| **Best for** | Investors who want advisory and hand-holding |

### 2. Discount Brokers

| Feature | Details |
|---|---|
| **What they offer** | Trading platform only — no research, no advisory, no relationship manager |
| **Brokerage** | Flat ₹20 per executed order (regardless of trade size) for intraday and F&O |
| **Examples** | Zerodha, Dhan, Groww, Upstox, Fyers |
| **Best for** | Active traders who make their own decisions |

---

## Which Should You Choose?

**For NIFTY options trading, a discount broker is the better choice.**

Here's why:

| Scenario | Full-Service (0.05%) | Discount (₹20 flat) |
|---|---|---|
| Buy NIFTY option, premium value ₹11,250 | ₹5.63 | ₹20 |
| Buy NIFTY option, premium value ₹75,000 | ₹37.50 | ₹20 |
| Buy NIFTY option, premium value ₹2,00,000 | ₹100 | ₹20 |
| Buy NIFTY option, premium value ₹5,00,000 | ₹250 | ₹20 |

For larger trades, the flat ₹20 is dramatically cheaper.

**Note:** For **delivery trades** (buying shares to hold), most discount brokers charge **zero brokerage**. Zerodha, for example, charges ₹0 for equity delivery.

---

## What Does a Broker Actually Do?

When you click "Buy" on your broker's app:

1. Your order is validated (do you have enough funds/margin?)
2. The order is sent to the exchange (NSE) via the broker's servers
3. NSE's matching engine matches your buy order with someone's sell order
4. The trade is executed
5. NSE sends a confirmation to the broker
6. The broker updates your account
7. Settlement happens (T+1 for equity, same day for intraday F&O)

All of this happens in **milliseconds**.

---

## How to Choose a Broker

| Factor | What to Check |
|---|---|
| **SEBI registration** | Must be SEBI-registered. Check on [sebi.gov.in](https://www.sebi.gov.in/) |
| **Exchange membership** | Must be a member of NSE (and BSE if you want) |
| **Brokerage charges** | Compare total costs, not just brokerage |
| **Platform quality** | Is the app/website fast and reliable? |
| **Customer support** | Can you reach them when something goes wrong? |
| **Margin requirements** | Do they offer reasonable margins for F&O? |
| **Charting tools** | Does the platform have good charts? (Most traders use TradingView separately) |
| **API availability** | Important later if you want to automate |

---

## How to Open a Trading + Demat Account

**What you need:**

| Document | Purpose |
|---|---|
| PAN card | Mandatory for all financial transactions |
| Aadhaar card (linked to mobile) | For e-KYC verification |
| Bank account details | Cancelled cheque or bank statement |
| Passport-size photo | Digital upload |
| Income proof (for F&O) | 6-month bank statement, ITR, or salary slip |

**Process (for most discount brokers):**

1. Go to the broker's website or app
2. Click "Open Account"
3. Enter your mobile number and verify via OTP
4. Enter PAN and Aadhaar details
5. Complete e-KYC (Aadhaar-based OTP verification)
6. Upload bank details
7. Upload income proof (for F&O activation)
8. Do In-Person Verification (IPV) via video call or selfie
9. Sign the agreement digitally (e-Sign via Aadhaar)
10. Account is activated within 24–48 hours

**Cost:** Most discount brokers charge ₹200–₹500 for account opening. Some offer free account opening during promotions.

**Annual Maintenance Charge (AMC):** Typically ₹300–₹500 per year for the demat account. Some brokers waive this for the first year.

---

---

# CHAPTER 3: ORDER TYPES

This is one of the most important chapters. Using the wrong order type can cost you significant money, especially in fast-moving options markets.

---

## 1. Market Order

**Definition:** An order to buy or sell **immediately at the best available price** in the market.

**How it works:**

You place a market buy order for NIFTY 24,500 CE. The current order book shows:

| Ask Price | Ask Quantity |
|---|---|
| ₹150.00 | 200 |
| ₹150.05 | 500 |
| ₹150.10 | 150 |

Your market order will buy at ₹150.00 (the best ask). If you're buying more than 200 lots, the remaining quantity will buy at ₹150.05, and so on.

**Advantages:**
- Guaranteed execution (your order will be filled)
- Fast — executed instantly

**Disadvantages:**
- **No price control** — you might get a worse price than expected, especially in volatile markets or low-liquidity options
- During fast-moving markets, the price can change between the moment you click and the moment your order executes

**When to use:** When speed of execution is more important than the exact price. For highly liquid ATM NIFTY options, market orders are generally fine because the bid-ask spread is small (₹0.05–₹0.50).

**When NOT to use:** For illiquid deep OTM options where the bid-ask spread can be ₹5–₹20. A market order in such options can result in a terrible fill price.

---

## 2. Limit Order

**Definition:** An order to buy or sell **at a specific price or better**.

**How it works:**

NIFTY 24,500 CE is currently trading at ₹150. You want to buy but think ₹150 is too expensive. You place a **limit buy order at ₹148**.

Your order will only execute if the price drops to ₹148 or below. If the price never reaches ₹148, your order remains pending and eventually expires at the end of the day.

**For a buy limit order:** You buy at the limit price **or lower** (better for you).
**For a sell limit order:** You sell at the limit price **or higher** (better for you).

**Advantages:**
- **Full price control** — you will never pay more than your limit (for buy) or receive less than your limit (for sell)
- Protects you from bad fills in volatile markets

**Disadvantages:**
- **No guaranteed execution** — if the price doesn't reach your limit, the order won't fill
- You might miss a trade if the price moves quickly past your limit

**Example:**

You place a limit buy at ₹148. The price drops to ₹148.50 and then shoots up to ₹160. Your order never executes. You missed the trade.

**When to use:** Most of the time. Limit orders are the default choice for disciplined traders.

---

## 3. Stop-Loss Order (SL Order)

**Definition:** An order that becomes active **only when the price reaches a specified trigger price**. Once triggered, it becomes a **limit order**.

**How it works:**

You bought NIFTY 24,500 CE at ₹150. You want to limit your loss. You place a **stop-loss sell order** with:

- **Trigger price:** ₹140
- **Limit price:** ₹139

When the market price drops to ₹140 (trigger), your order becomes active as a limit sell order at ₹139. It will sell at ₹139 or above.

**Why the gap between trigger and limit?**

If you set trigger = ₹140 and limit = ₹140, in a fast-falling market, the price might jump from ₹140.05 to ₹139.50 in a single tick. Your limit order at ₹140 would not execute because the price is already below ₹140.

By setting the limit slightly below the trigger (₹139), you give the order a better chance of executing even in a fast-moving market.

**Advantages:**
- Protects you from large losses
- Automates your exit — you don't have to watch the screen constantly

**Disadvantages:**
- In extremely volatile markets, the price can **gap down** past both your trigger and limit, and your order may not execute at the expected price
- Stop-loss hunting — sometimes prices briefly dip to trigger stop-losses and then reverse

---

## 4. Stop-Loss Market Order (SL-M)

**Definition:** Similar to a stop-loss order, but once triggered, it becomes a **market order** instead of a limit order.

**How it works:**

You bought NIFTY 24,500 CE at ₹150. You place an SL-M order with:

- **Trigger price:** ₹140

When the price drops to ₹140, your order becomes a **market sell order** and executes at the best available price.

**Advantages:**
- **Guaranteed execution** once triggered (unlike SL limit which might not fill)
- Better protection in fast-crashing markets

**Disadvantages:**
- **No price control** after triggering — in a flash crash, you might sell at ₹135 or ₹130 even though your trigger was ₹140
- This is called **slippage**

**SL vs SL-M Comparison:**

| Feature | SL (Stop-Loss Limit) | SL-M (Stop-Loss Market) |
|---|---|---|
| After trigger, becomes | Limit order | Market order |
| Execution guaranteed? | No | Yes |
| Price control? | Yes | No |
| Risk of slippage? | Low | High |
| Risk of non-execution? | High | Low |
| Best for | Normal market conditions | Highly volatile / crash scenarios |

---

## 5. GTT Order (Good Till Triggered)

**Definition:** An order that stays active for **up to 1 year** until the trigger price is hit. Available on Zerodha and some other brokers.

**How it works:**

You want to buy NIFTY 24,500 CE if it drops to ₹120, but you don't want to watch the screen all day. You place a GTT buy order at ₹120.

This order remains active for 365 days. If the price reaches ₹120 on any day during that period, the order triggers and executes.

**Use case:** More useful for equity delivery (buying stocks to hold) than for intraday options trading. For options, expiry is too close for GTT to be practical.

---

## 6. AMO (After Market Order)

**Definition:** An order placed **after market hours** (between 3:45 PM and 8:57 AM the next day) that gets executed when the market opens.

**How it works:**

At 7:00 PM, after reading the news, you decide you want to buy NIFTY 24,500 CE at ₹150 the next morning. You place an AMO limit buy at ₹150.

At 9:15 AM the next day, your order is sent to the exchange and executed if the price matches.

**Important:** AMO orders are executed during the **pre-open session** or at market open. The actual execution price may differ from your limit if the market gaps up or down overnight.

---

## Order Type Summary Table

| Order Type | Execution | Price Control | Best Used When |
|---|---|---|---|
| **Market** | Guaranteed | None | High liquidity, need speed |
| **Limit** | Not guaranteed | Full | Most situations — default choice |
| **SL (Limit)** | Not guaranteed after trigger | Yes (within limit) | Normal stop-loss |
| **SL-M (Market)** | Guaranteed after trigger | None after trigger | Volatile markets, crash protection |
| **GTT** | Not guaranteed | Yes | Long-term equity investing |
| **AMO** | Depends on market open | Yes (if limit) | Placing orders after hours |

---

## Practical Example: A Complete Options Trade with Order Types

**Setup:** It's 10:00 AM on Tuesday. NIFTY is at 24,500. You've analyzed the chart and want to buy NIFTY 24,500 CE.

**Step 1 — Entry:**
- Current price of 24,500 CE: ₹152
- You think ₹152 is slightly high. You place a **limit buy order at ₹150**
- At 10:15 AM, the price dips to ₹150. Your order executes.
- You now own 1 lot (75 units) of NIFTY 24,500 CE at ₹150

**Step 2 — Stop-Loss:**
- Immediately after entry, you place a **stop-loss sell order**
- Trigger: ₹140
- Limit: ₹139
- This means if the price drops to ₹140, your position will be sold at ₹139 or above
- Maximum loss: (150 – 139) × 75 = ₹825 + charges

**Step 3 — Target:**
- You place a **limit sell order at ₹170** for your target
- If the price reaches ₹170, your position is sold automatically
- Profit: (170 – 150) × 75 = ₹1,500 – charges

**Step 4 — What happens:**
- Scenario A: Price goes to ₹170 by 1:00 PM → Target hit → You exit with ₹1,500 gross profit
- Scenario B: Price drops to ₹140 by 11:30 AM → Stop-loss hit → You exit with ₹750 gross loss
- Scenario C: Price stays between ₹145 and ₹155 all day → Neither target nor SL hit → You must manually exit before 3:15 PM (intraday)

---

---

# CHAPTER 4: SETTLEMENT CYCLE

## What Is Settlement?

Settlement is the process where **money and securities actually change hands** after a trade is executed.

When you see a trade on your screen, it's **executed** but not yet **settled**.

---

## T+1 Settlement (Equity Delivery)

For equity delivery trades (buying shares to hold), India follows **T+1 settlement**.

- **T** = Trade day (the day you bought/sold)
- **T+1** = The next business day

**Example:**

| Day | Event |
|---|---|
| Monday (T) | You buy 100 shares of Reliance at ₹2,500 |
| Tuesday (T+1) | 100 shares are credited to your demat account. ₹2,50,000 is debited from your trading account. |

If you sell on Wednesday:
| Day | Event |
|---|---|
| Wednesday (T) | You sell 100 shares of Reliance at ₹2,550 |
| Thursday (T+1) | 100 shares are debited from your demat. ₹2,55,000 is credited to your trading account. |

---

## Intraday F&O Settlement

For **intraday options trades** (buy and sell on the same day):

- No delivery happens
- Only the **net profit or loss** is settled
- Settlement happens on the same day (T+0)
- Your P&L is reflected in your trading account by the end of the day

**Example:**

You buy NIFTY 24,500 CE at ₹150 and sell at ₹170 on the same day.

- Gross profit: (170 – 150) × 75 = ₹1,500
- Charges: ~₹72 (we'll calculate this precisely in Chapter 6)
- Net profit: ~₹1,428
- This ₹1,428 is credited to your trading account by end of day

---

## Expiry Day Settlement

If you hold an options position until expiry (Thursday for NIFTY weekly):

- **ITM options** are automatically exercised
- **OTM options** expire worthless (premium becomes ₹0)
- **ATM options** typically expire worthless (no intrinsic value)

For NIFTY options (cash-settled):
- No physical delivery of NIFTY shares (you can't deliver an index)
- The difference between the closing price and strike price is settled in cash

**Example:**

You hold NIFTY 24,500 CE until expiry. NIFTY closes at 24,650.

- Intrinsic value at expiry: 24,650 – 24,500 = ₹150 per unit
- Settlement amount: ₹150 × 75 = ₹11,250 credited to your account
- If you had bought the option at ₹100, your net profit: (150 – 100) × 75 = ₹3,750

---

---

# CHAPTER 5: CLEARING CORPORATION

## What Is It?

The **clearing corporation** is the entity that guarantees every trade on the exchange.

For NSE, it's **NSE Clearing Limited (NSECL)**.

## Why Does It Matter?

When you buy shares from someone on NSE, you don't know who the seller is. What if the seller doesn't deliver the shares? What if the buyer doesn't pay?

The clearing corporation acts as the **central counterparty** to every trade:

- To the buyer, the clearing corporation is the seller
- To the seller, the clearing corporation is the buyer

This eliminates **counterparty risk**. You don't need to worry about whether the other person will honor the trade.

## How It Works

```
BUYER ←→ NSE CLEARING LIMITED ←→ SELLER
         (guarantees both sides)
```

The clearing corporation also:
- Calculates margin requirements
- Collects margins from brokers
- Handles settlement
- Manages the settlement guarantee fund

---

---

# CHAPTER 6: COMPLETE BREAKDOWN OF ALL TRADING CHARGES

**This is the most important chapter of Week 2.** Read it very carefully.

Most beginners only think about brokerage. But brokerage is just one of **six different charges** you pay on every trade.

---

## The Six Charges

| # | Charge | Who Charges It | When |
|---|---|---|---|
| 1 | **Brokerage** | Your broker | Both buy and sell |
| 2 | **STT (Securities Transaction Tax)** | Government of India | Sell side only (for options) |
| 3 | **Exchange Transaction Charges** | NSE | Both buy and sell |
| 4 | **GST (Goods and Services Tax)** | Government of India | Both buy and sell (on brokerage + exchange charges) |
| 5 | **Stamp Duty** | State Government | Buy side only |
| 6 | **SEBI Turnover Fee** | SEBI | Both buy and sell |

---

## Detailed Explanation of Each Charge

### 1. Brokerage

**For discount brokers (Zerodha, Dhan, Groww, Upstox):**

| Segment | Brokerage |
|---|---|
| Equity Delivery | ₹0 (free) |
| Equity Intraday | ₹20 per executed order or 0.03% (whichever is lower) |
| Futures | ₹20 per executed order |
| Options | ₹20 per executed order |

**Key point:** "Per executed order" means per **buy** or per **sell**. A complete round-trip trade (buy + sell) costs ₹40 in brokerage.

**For full-service brokers:** Typically 0.03%–0.05% of trade value, which can be much higher for large trades.

---

### 2. STT (Securities Transaction Tax)

This is a tax levied by the Government of India on financial transactions.

**For options:**

| Side | STT Rate | Applied On |
|---|---|---|
| **Buy** | **0%** | No STT on buying options |
| **Sell** | **0.0625%** | On the **premium value** (not on the notional value) |

**Example:**

You sell NIFTY 24,500 CE at ₹200. Lot size = 75.

Premium value = ₹200 × 75 = ₹15,000

STT = 0.0625% × ₹15,000 = **₹9.38**

**Important note:** STT is calculated on the **premium value**, not on the NIFTY index value. If it were calculated on the index value (24,500 × 75 = ₹18,37,500), the STT would be enormous. The government taxes only the premium for options.

---

### 3. Exchange Transaction Charges

NSE charges a fee for using its trading platform.

**For options:**

| Charge | Rate |
|---|---|
| NSE Transaction Charge | **0.05%** of premium value (approximately — NSE revises this periodically) |

**Example:**

Buy NIFTY 24,500 CE at ₹150. Lot size = 75.

Premium value = ₹150 × 75 = ₹11,250

Exchange charge = 0.05% × ₹11,250 = **₹5.63**

---

### 4. GST (Goods and Services Tax)

GST is charged at **18%** on the sum of **brokerage + exchange transaction charges**.

**GST is NOT charged on STT or stamp duty.**

**Example (buy side):**

- Brokerage: ₹20
- Exchange charges: ₹5.63
- GST = 18% × (20 + 5.63) = 18% × 25.63 = **₹4.61**

---

### 5. Stamp Duty

Stamp duty is charged by the state government.

**For options:**

| Side | Rate |
|---|---|
| **Buy** | **0.003%** of premium value |
| **Sell** | **0%** (no stamp duty on sell side) |

**Example:**

Buy NIFTY 24,500 CE at ₹150. Premium value = ₹11,250.

Stamp duty = 0.003% × ₹11,250 = **₹0.34**

---

### 6. SEBI Turnover Fee

A very small fee charged by SEBI.

| Rate | Applied On |
|---|---|
| **0.0001%** | Premium value (both buy and sell) |

**Example:**

Buy premium value = ₹11,250.

SEBI fee = 0.0001% × ₹11,250 = **₹0.01**

This is negligible but I'm including it for completeness.

---

## COMPLETE CALCULATION — REAL EXAMPLES

### Example 1: Profitable Trade (Medium Move)

**Trade:** Buy NIFTY 24,500 CE at ₹150, sell at ₹200. Lot size = 75.

**BUY SIDE:**

| Charge | Calculation | Amount |
|---|---|---|
| Premium value | 150 × 75 | ₹11,250 |
| Brokerage | Flat | ₹20.00 |
| STT | 0% on buy | ₹0.00 |
| Exchange charges | 0.05% × 11,250 | ₹5.63 |
| GST | 18% × (20 + 5.63) | ₹4.61 |
| Stamp duty | 0.003% × 11,250 | ₹0.34 |
| SEBI fee | 0.0001% × 11,250 | ₹0.01 |
| **Total buy charges** | | **₹30.59** |

**SELL SIDE:**

| Charge | Calculation | Amount |
|---|---|---|
| Premium value | 200 × 75 | ₹15,000 |
| Brokerage | Flat | ₹20.00 |
| STT | 0.0625% × 15,000 | ₹9.38 |
| Exchange charges | 0.05% × 15,000 | ₹7.50 |
| GST | 18% × (20 + 7.50) | ₹4.95 |
| Stamp duty | 0% on sell | ₹0.00 |
| SEBI fee | 0.0001% × 15,000 | ₹0.02 |
| **Total sell charges** | | **₹41.85** |

**SUMMARY:**

| Item | Amount |
|---|---|
| Gross profit | (200 – 150) × 75 = **₹3,750** |
| Total charges | 30.59 + 41.85 = **₹72.44** |
| **Net profit** | 3,750 – 72.44 = **₹3,677.56** |
| Charges as % of gross profit | 72.44 / 3,750 = **1.93%** |

**Verdict:** Charges are negligible for this trade. You keep 98% of your gross profit.

---

### Example 2: Small Move (Barely Profitable)

**Trade:** Buy at ₹150, sell at ₹155. Lot size = 75.

| Item | Amount |
|---|---|
| Gross profit | (155 – 150) × 75 = **₹375** |
| Buy charges (premium ₹11,250) | ~₹30.59 |
| Sell charges (premium ₹11,625) | ~₹38.00 |
| Total charges | ~**₹68.59** |
| **Net profit** | 375 – 68.59 = **₹306.41** |
| Charges as % of gross profit | 68.59 / 375 = **18.29%** |

**Verdict:** Charges eat up 18% of your profit. Still profitable, but notice how much the charges matter for small moves.

---

### Example 3: Tiny Move (Almost Break-Even)

**Trade:** Buy at ₹150, sell at ₹151. Lot size = 75.

| Item | Amount |
|---|---|
| Gross profit | (151 – 150) × 75 = **₹75** |
| Total charges | ~**₹67** |
| **Net profit** | 75 – 67 = **₹8** |
| Charges as % of gross profit | 67 / 75 = **89.3%** |

**Verdict:** You got the direction right, the price moved in your favor, but you kept only ₹8 out of ₹75. Charges consumed 89% of your profit.

---

### Example 4: Losing Trade

**Trade:** Buy at ₹150, sell at ₹140 (stop-loss hit). Lot size = 75.

| Item | Amount |
|---|---|
| Gross loss | (140 – 150) × 75 = **–₹750** |
| Total charges | ~**₹66** |
| **Net loss** | 750 + 66 = **–₹816** |

**Verdict:** Charges make your losses bigger. You lost ₹750 on the trade but your account was debited ₹816.

---

### Example 5: Cheap OTM Option (The Trap)

**Trade:** Buy NIFTY 24,800 CE (OTM) at ₹20, sell at ₹22. Lot size = 75.

| Item | Amount |
|---|---|
| Gross profit | (22 – 20) × 75 = **₹150** |
| Buy charges (premium ₹1,500) | ~₹22 |
| Sell charges (premium ₹1,650) | ~₹23 |
| Total charges | ~**₹45** |
| **Net profit** | 150 – 45 = **₹105** |
| Charges as % of gross profit | 45 / 150 = **30%** |

**Verdict:** 30% of your profit gone to charges. And this was a "winning" trade. If you had sold at ₹21 instead of ₹22, your gross profit would be ₹75 and charges would be ~₹44 — leaving you with just ₹31.

---

## The Big Picture

| Move Size | Gross P&L | Charges | Net P&L | Charges % |
|---|---|---|---|---|
| +₹50 (big win) | +₹3,750 | ₹72 | +₹3,678 | 1.9% |
| +₹20 (medium win) | +₹1,500 | ₹70 | +₹1,430 | 4.7% |
| +₹5 (small win) | +₹375 | ₹69 | +₹306 | 18.3% |
| +₹1 (tiny win) | +₹75 | ₹67 | +₹8 | 89.3% |
| –₹10 (loss) | –₹750 | ₹66 | –₹816 | Charges add to loss |

**The lesson:**

1. **Charges are fixed** (roughly ₹65–₹75 per round trip for 1 lot of NIFTY options) regardless of how much you profit or lose.
2. For **large moves**, charges are a small percentage — no problem.
3. For **small moves**, charges destroy your profitability.
4. For **losing trades**, charges make the loss worse.
5. This is why your trading system must target **meaningful moves** (at least 15–20 points in premium for NIFTY options) to be profitable after costs.

---

## Charges for Option Selling (For Future Reference)

If you eventually sell options, the charge structure is slightly different:

| Charge | Option Buying | Option Selling |
|---|---|---|
| Brokerage | ₹20 per order | ₹20 per order |
| STT | 0% buy, 0.0625% sell | 0.0625% sell (on premium) |
| Exchange charges | 0.05% | 0.05% |
| GST | 18% on (brk + exch) | 18% on (brk + exch) |
| Stamp duty | 0.003% buy | 0% |
| SEBI fee | 0.0001% | 0.0001% |

The charges are similar. The main difference is in **margin requirements** — selling requires much more capital.

---

---

# CHAPTER 7: PRACTICAL EXERCISES FOR WEEK 2

## Exercise 1: Calculate Charges for 10 Different Trades

Go to [zerodha.com/brokerage-calculator](https://zerodha.com/brokerage-calculator).

Select **"F&O — Options"**.

Calculate total charges for each of these trades (assume lot size = 75):

| # | Buy Price | Sell Price | Your Task |
|---|---|---|---|
| 1 | ₹100 | ₹120 | Calculate net profit |
| 2 | ₹100 | ₹110 | Calculate net profit |
| 3 | ₹100 | ₹105 | Calculate net profit |
| 4 | ₹100 | ₹102 | Calculate net profit |
| 5 | ₹100 | ₹101 | Calculate net profit |
| 6 | ₹100 | ₹100 | Calculate net P&L (breakeven?) |
| 7 | ₹100 | ₹95 | Calculate net loss |
| 8 | ₹100 | ₹90 | Calculate net loss |
| 9 | ₹50 | ₹60 | Calculate net profit |
| 10 | ₹50 | ₹52 | Calculate net profit |

For each trade, write down:
- Gross P&L
- Total charges
- Net P&L
- Charges as a percentage of gross P&L

**The insight you should get:** Find the **minimum price move** at which you start making a net profit after charges. This is your **breakeven move**. Any system that targets moves smaller than this breakeven will lose money over time.

---

## Exercise 2: Compare Broker Charges

Compare the total charges for a NIFTY options trade (buy at ₹150, sell at ₹170, lot size 75) across different brokers:

| Broker | Type | Brokerage | Check Total Charges |
|---|---|---|---|
| Zerodha | Discount | ₹20/order | [zerodha.com/brokerage-calculator](https://zerodha.com/brokerage-calculator) |
| Dhan | Discount | ₹20/order | [dhan.co/pricing](https://dhan.co/pricing/) |
| Groww | Discount | ₹20/order | [groww.in/pricing](https://groww.in/pricing) |
| ICICI Direct | Full-Service | 0.05% | [icicidirect.com](https://www.icicidirect.com/) |
| Angel One | Hybrid | ₹20/order | [angelone.in](https://www.angelone.in/) |

**The insight:** For F&O trading, the difference between discount brokers is minimal (all charge ₹20). The difference between discount and full-service brokers is significant for large trades.

---

## Exercise 3: Order Type Practice on TradingView (Paper)

Open TradingView → NIFTY 50 chart → 5-minute timeframe.

Look at the current price and imagine you want to buy a NIFTY ATM call option.

Write down:

1. What **limit price** would you use for entry? (Look at the recent price action to decide a reasonable limit)
2. What **stop-loss trigger and limit** would you set? (Based on recent swing lows)
3. What **target limit** would you set? (Based on recent swing highs or resistance)
4. What is the **risk-reward ratio** of this hypothetical trade?

Do this for 5 different points in the chart (use bar replay mode to go to random historical dates).

---

## Exercise 4: Understand Your Broker's App

If you already have a trading account, open the app and find:

1. Where to place a limit order
2. Where to place a market order
3. Where to set a stop-loss
4. Where to see your order book (pending orders)
5. Where to see your trade book (executed trades)
6. Where to see your positions (open trades)
7. Where to see your holdings (delivery shares)
8. Where to see your funds/margin
9. Where to see the contract note (charge breakdown)

If you don't have an account yet, watch a YouTube tutorial on "How to use Zerodha Kite app" or "How to use Dhan app" to familiarize yourself with the interface.

---

## Exercise 5: Read a Contract Note

A **contract note** is a legal document your broker sends you at the end of every trading day. It contains:

- All trades executed that day
- Buy and sell prices
- Quantity
- Complete breakdown of all charges
- Net amount payable/receivable
- SEBI registration number of the broker

**Your task:** If you have a trading account, download a contract note and identify each of the six charges. If you don't have an account, search "sample contract note Zerodha" on Google Images and study the format.

---

---

# WEEK 2 — SELF-TEST

Answer these without looking at the notes.

### Questions

1. What is the difference between a demat account and a trading account?

2. Can you place orders directly on NSE without a broker?

3. What is the difference between a full-service broker and a discount broker?

4. What is the brokerage charged by Zerodha for one NIFTY options order?

5. How much brokerage do you pay for a complete round-trip NIFTY options trade (buy + sell)?

6. What is a market order? What is its main disadvantage?

7. What is a limit order? What is its main disadvantage?

8. What is the difference between an SL order and an SL-M order?

9. What does T+1 settlement mean?

10. Name all six charges you pay on a NIFTY options trade.

11. On which side (buy or sell) is STT charged for options?

12. What is the STT rate for options?

13. On which side is stamp duty charged for options?

14. What is GST charged on?

15. If you buy a NIFTY option at ₹150 and sell at ₹151 (lot size 75), approximately how much of your gross profit goes to charges?

16. What is the role of the clearing corporation?

17. What is a contract note?

18. If you buy NIFTY 24,500 CE at ₹150 (lot size 75), what is the premium value?

19. What is an AMO order and when would you use it?

20. Why should your trading system target meaningful moves rather than tiny price changes?

---

### Answers

1. A demat account holds shares and securities electronically (like a locker). A trading account is used to place buy/sell orders on the exchange (like a trading desk).

2. No. You must trade through a SEBI-registered broker who is a member of the exchange.

3. Full-service brokers offer research, advisory, and relationship management but charge higher brokerage (0.03–0.05%). Discount brokers offer only the trading platform at a flat ₹20 per order.

4. ₹20 per executed order.

5. ₹40 (₹20 for buy + ₹20 for sell).

6. A market order executes immediately at the best available price. Its main disadvantage is no price control — you might get a worse fill than expected, especially in volatile or illiquid markets.

7. A limit order executes only at your specified price or better. Its main disadvantage is no guaranteed execution — if the price doesn't reach your limit, the order won't fill.

8. An SL order becomes a limit order after the trigger is hit (price control but possible non-execution). An SL-M order becomes a market order after the trigger (guaranteed execution but possible slippage).

9. T+1 means settlement happens on the next business day after the trade. If you buy shares on Monday, they appear in your demat on Tuesday.

10. Brokerage, STT, Exchange Transaction Charges, GST, Stamp Duty, SEBI Turnover Fee.

11. Sell side only. No STT on buying options.

12. 0.0625% of the premium value on the sell side.

13. Buy side only. 0.003% of premium value. No stamp duty on sell side.

14. GST (18%) is charged on the sum of brokerage + exchange transaction charges. It is NOT charged on STT or stamp duty.

15. Approximately 89%. Gross profit = ₹75. Charges ≈ ₹67. You keep only about ₹8.

16. The clearing corporation (NSE Clearing Limited) acts as the central counterparty to every trade, guaranteeing settlement and eliminating counterparty risk.

17. A contract note is a legal document sent by the broker at end of day showing all trades, prices, quantities, and a complete breakdown of all charges.

18. Premium value = ₹150 × 75 = ₹11,250.

19. An AMO (After Market Order) is placed after market hours and executes when the market opens the next day. You'd use it when you want to place an order based on after-hours analysis but can't be online at 9:15 AM.

20. Because charges are roughly fixed at ₹65–₹75 per round trip regardless of the move size. For tiny moves (1–2 points), charges consume 50–90% of your profit. Your system must capture moves large enough that charges are a small percentage of your gains.

---

---

# WHAT YOU SHOULD KNOW AFTER WEEK 2

By now, you should be able to:

- [x] Explain the difference between demat and trading accounts
- [x] Choose between broker types and understand why discount brokers are better for F&O
- [x] Place all six types of orders (market, limit, SL, SL-M, GTT, AMO) and know when to use each
- [x] Calculate the total charges for any NIFTY options trade
- [x] Understand why small moves are unprofitable after costs
- [x] Explain the settlement cycle
- [x] Read and understand a contract note

---

**When you've completed all exercises and scored 18/20 on the self-test, you're ready for Week 3: Introduction to Futures and Options (basic concepts, lot size, expiry, and how to read the option chain).**

Tell me when you're ready.
