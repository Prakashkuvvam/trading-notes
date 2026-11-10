# WEEK 19: ADVANCED OPTIONS STRATEGIES

---

## 📋 WEEK 19 OVERVIEW

| Day | Topic | Hours |
|-----|-------|-------|
| Mon | Credit vs Debit Strategies + Bull Put Spread | 3 |
| Tue | Bear Call Spread + Credit Spread Management | 3 |
| Wed | Long Straddle & Long Strangle (Volatility Plays) | 3 |
| Thu | Iron Condor (Range-Bound Income Machine) | 3 |
| Fri | Calendar Spread (Time Decay Arbitrage) | 3 |
| Sat | Strategy Selection Master Framework + Practical Exercises | 4 |
| Sun | Self-Test + Revision | 3 |

**Prerequisites:** Weeks 11–18 (all options theory, Greeks, IV, OI, beginner strategies)

**Free Resources This Week:**
- Zerodha Varsity Module 5, Chapters 23–28: `zerodha.com/varsity/`
- Sensibull Strategy Wizard: `sensibull.com/virtual-trade` (build & paper trade all strategies)
- Opstra Strategy Builder: `opstra.definedge.com/strategy` (payoff diagrams, Greeks)
- NSE Strategy Calculator: `nseindia.com`

---

## CHAPTER 1: CREDIT vs DEBIT STRATEGIES — THE FUNDAMENTAL DIVIDE

### 1.1 Recap: What You Learned in Week 18

```
WEEK 18 STRATEGIES (All Debit — You PAY premium):
  1. Covered Call    → Long Stock + Short Call     (Net Credit, but needs stock)
  2. Protective Put  → Long Stock + Long Put        (Net Debit)
  3. Bull Call Spread → Long Call + Short Call      (Net Debit)
  4. Bear Put Spread  → Long Put + Short Put        (Net Debit)
```

All four strategies (except Covered Call) required you to **pay money upfront**. You bought the "engine" leg and sold the "financier" leg, but the net was still a debit.

### 1.2 The New World: Credit Strategies

This week introduces strategies where you **RECEIVE money upfront**. You become the option seller — but with **defined risk** (unlike naked selling).

```
CREDIT STRATEGIES (You RECEIVE premium):
  5. Bull Put Spread  → Short Put + Long Put        (Net Credit) ✅
  6. Bear Call Spread → Short Call + Long Call       (Net Credit) ✅
  7. Iron Condor      → Bull Put + Bear Call          (Net Credit) ✅
  8. Calendar Spread  → Short Near + Long Far         (Net Debit, but theta-positive)

VOLATILITY STRATEGIES (You PAY premium, profit from big moves):
  9. Long Straddle    → Long Call + Long Put (same strike)  (Net Debit)
  10. Long Strangle   → Long OTM Call + Long OTM Put        (Net Debit)
```

### 1.3 The Debit vs Credit Comparison

```
┌────────────────────┬──────────────────────┬──────────────────────┐
│                    │ DEBIT STRATEGIES     │ CREDIT STRATEGIES    │
│                    │ (Week 18)            │ (This Week)          │
├────────────────────┼──────────────────────┼──────────────────────┤
│ Cash Flow          │ You PAY upfront      │ You RECEIVE upfront  │
│ Best Market        │ Trending (directional│ Range-bound / Mild   │
│                    │ move needed)         │ trend                │
│ Theta Effect       │ Hurts you (negative) │ Helps you (positive) │
│ IV Effect          │ IV rise helps        │ IV drop helps        │
│ Win Rate           │ ~35–50%              │ ~55–70%              │
│ Profit per Trade   │ Higher (1.5–3x risk) │ Lower (0.3–0.8x risk)│
│ Loss per Trade     │ Known (net debit)    │ Known (width-credit) │
│ Holding Period     │ 1–10 days            │ 5–20 days            │
│ Ideal IV Env       │ Low to Normal IV     │ Normal to High IV    │
│ Beginner Friendly  │ ✅ Yes               │ ✅ Yes (with rules)  │
│ Analogy            │ Buying a lottery     │ Running an insurance │
│                    │ ticket (cheap, low   │ company (collect     │
│                    │ probability, big     │ premium, pay claims  │
│                    │ payout)              │ rarely)              │
└────────────────────┴──────────────────────┴──────────────────────┘
```

### 1.4 When to Use Which

```
MARKET IS TRENDING STRONGLY → Debit Strategies (Bull Call / Bear Put Spread)
  → You need directional movement
  → Theta hurts but delta gains compensate
  → Low IV is ideal (options are cheap to buy)

MARKET IS RANGE-BOUND / SLOW → Credit Strategies (Bull Put / Bear Call / Iron Condor)
  → You profit from time decay even if NIFTY doesn't move
  → High IV is ideal (options are expensive to sell)
  → Higher win rate but smaller profits per trade

MARKET IS ABOUT TO EXPLODE (Event) → Volatility Strategies (Straddle / Strangle)
  → You don't know direction but expect a BIG move
  → Budget, Election results, RBI surprise
  → Buy BEFORE the event, sell during the move

MARKET IS DEAD CALM → Calendar Spread
  → Near-term options decay faster than long-term
  → Profit from the theta differential
  → Low IV environment, expecting IV to rise later
```

---

## CHAPTER 2: STRATEGY 5 — BULL PUT SPREAD (CREDIT)

### 2.1 What Is a Bull Put Spread?

A Bull Put Spread is the **credit mirror** of the Bull Call Spread. Instead of buying calls, you sell puts:

1. **SELL** an ATM or slightly OTM Put (higher strike)
2. **BUY** a further OTM Put (lower strike) as protection
3. Same expiry, same underlying

```
BULL PUT SPREAD = Short Put (higher strike) + Long Put (lower strike)

Net result: You RECEIVE premium upfront (credit)
Your view: NIFTY will stay ABOVE the short put strike
```

### 2.2 The Insurance Company Analogy

```
Think of yourself as an insurance company:

  → You sell car insurance (short put) and collect premium
  → You buy reinsurance (long put) to protect against catastrophe
  → If no accident (NIFTY stays up), you keep the premium
  → If accident (NIFTY crashes), your reinsurance caps your loss
  → You profit from the DIFFERENCE between premium collected
    and premium paid for reinsurance
```

### 2.3 When to Use

```
✅ USE Bull Put Spread when:
  → You are mildly bullish or neutral
  → NIFTY is above a strong support level
  → You want to profit from time decay (theta-positive)
  → IV is moderate to high (puts are expensive → rich premium)
  → You want a higher win rate than debit spreads (~60–70%)
  → 5–15 days to expiry (enough time for theta to work)

❌ DON'T USE when:
  → You expect a sharp crash (your short put will get destroyed)
  → IV is very low (premium collected is too small to justify risk)
  → NIFTY is breaking below major support
  → Event risk in the next 2–3 days (Budget, RBI)
```

### 2.4 Construction — Step by Step

```
Step 1: Identify your view
  → "NIFTY at 24,700. Strong support at 24,500.
     I expect NIFTY to stay above 24,500 for 7 days."

Step 2: Sell the higher strike put (your "income generator")
  → Sell 24,600 PE at ₹65 (slightly OTM, delta ~–0.30)
  → This is the strike you expect NIFTY to stay ABOVE

Step 3: Buy the lower strike put (your "catastrophe insurance")
  → Buy 24,400 PE at ₹20 (further OTM, delta ~–0.10)
  → This caps your loss if NIFTY crashes

Step 4: Calculate net credit
  → Net Credit = ₹65 – ₹20 = ₹45 per share
  → Total Credit = ₹45 × 75 = ₹3,375 per lot
  → This money is YOURS immediately (credited to account)

Step 5: Calculate max profit
  → Max Profit = Net Credit × Lot = ₹45 × 75 = ₹3,375
  → Achieved if NIFTY expires ABOVE 24,600 (both puts expire OTM)

Step 6: Calculate max loss
  → Max Loss = (Width – Net Credit) × Lot
  → Width = 24,600 – 24,400 = 200 pts
  → Max Loss = (200 – 45) × 75 = ₹155 × 75 = ₹11,625

Step 7: Calculate breakeven
  → Breakeven = Short Strike – Net Credit = 24,600 – 45 = 24,555

Step 8: Risk-Reward
  → R:R = Max Profit / Max Loss = 3,375 / 11,625 = 0.29:1
  → "Wait, I'm risking ₹11,625 to make ₹3,375? That's terrible!"
  → BUT: Win rate is ~65–70%. Over 10 trades:
     7 wins × ₹3,375 = ₹23,625
     3 losses × ₹11,625 = ₹34,875
     Net = –₹11,250... hmm, that's negative.
  → The key is MANAGEMENT. You don't hold to max loss.
     You close at 50% of max loss (₹5,812).
     7 wins × ₹3,375 = ₹23,625
     3 losses × ₹5,812 = ₹17,436
     Net = +₹6,189 ✅
  → Credit spreads profit from HIGH WIN RATE + EARLY EXITS
```

### 2.5 Payoff Diagram

```
Profit/Loss at Expiry (per share)

  ₹60 │
      │
  ₹45 │  _______________ ← Max Profit: +₹45
      │  |
  ₹30 │  |
      │  |
  ₹15 │  |
      │  |
   ₹0 │──|──────────────────────────────────────
      │  |         \
 –₹15 │  |           \  Breakeven: 24,555
      │  |             \
 –₹45 │  |               \
      │  |                 \
–₹100 │  |                   \
      │  |                     \
–₹155 │  |                       \___________ ← Max Loss: –₹155
      │  |                                   ↑
      │  ↑                              24,400 (Long Put)
      │ 24,600 (Short Put)
      │
      └──┬──────┬──────┬──────┬──────┬──────┬──────┬──
       24,200 24,300 24,400 24,500 24,600 24,700 24,800
                         NIFTY at Expiry

  Zones:
  • Above 24,600: Both puts OTM → Max Profit +₹45 (keep full credit)
  • 24,555–24,600: Partial profit (short put ITM, long put OTM)
  • 24,555: Breakeven
  • 24,400–24,555: Loss zone (increasing)
  • Below 24,400: Both puts ITM → Max Loss –₹155 (capped!)
```

### 2.6 Detailed Numerical Example

```
SETUP:
  NIFTY Spot: 24,700 (Monday, 7 days to expiry)
  Sell: 24,600 PE at ₹65
  Buy: 24,400 PE at ₹20
  Net Credit: ₹45 per share = ₹3,375 per lot
  Max Profit: ₹3,375
  Max Loss: ₹11,625
  Breakeven: 24,555
  Margin Required: ~₹45,000 (Zerodha hedged margin)

SCENARIO A: NIFTY expires at 24,750 (+50 pts) ✅✅
  24,600 PE: OTM → ₹0
  24,400 PE: OTM → ₹0
  Net P&L: +₹45 per share = +₹3,375
  → MAX PROFIT. You keep the full credit.
  → NIFTY didn't even need to rally. Just staying above 24,600 was enough.

SCENARIO B: NIFTY expires at 24,620 (–80 pts, mild fall) ✅
  24,600 PE: ITM by 20 → You owe ₹20 (but collected ₹65)
  24,400 PE: OTM → ₹0
  Net P&L: (65 – 20 – 20) × 75 = ₹25 × 75 = +₹1,875
  → Still profitable! Even though NIFTY fell 80 pts.
  → This is the magic of credit spreads.

SCENARIO C: NIFTY expires at 24,555 (breakeven) ➡️
  24,600 PE: ITM by 45 → You owe ₹45
  24,400 PE: OTM → ₹0
  Net P&L: (65 – 20 – 45) × 75 = ₹0
  → BREAKEVEN

SCENARIO D: NIFTY expires at 24,500 (–200 pts) ❌
  24,600 PE: ITM by 100 → You owe ₹100
  24,400 PE: OTM → ₹0
  Net P&L: (65 – 20 – 100) × 75 = –₹55 × 75 = –₹4,125
  → Loss, but not max loss. Still within management range.

SCENARIO E: NIFTY crashes to 24,300 (–400 pts) ❌❌
  24,600 PE: ITM by 300 → You owe ₹300
  24,400 PE: ITM by 100 → You gain ₹100 (protection kicks in!)
  Net P&L: (65 – 20 – 300 + 100) × 75 = –₹155 × 75 = –₹11,625
  → MAX LOSS. But it's CAPPED.
  → Naked short put would lose: (300 – 65) × 75 = –₹17,625
  → Long put SAVED you ₹6,000

SCENARIO F: NIFTY crashes to 23,500 (–1,200 pts, BLACK SWAN) ❌❌❌
  24,600 PE: ITM by 1,100 → You owe ₹1,100
  24,400 PE: ITM by 900 → You gain ₹900
  Net P&L: (65 – 20 – 1,100 + 900) × 75 = –₹155 × 75 = –₹11,625
  → SAME MAX LOSS! The long put fully protects you.
  → Naked short put would lose: (1,100 – 65) × 75 = –₹77,625
  → Long put SAVED you ₹66,000! 🛡️
```

### 2.7 Greeks of a Bull Put Spread

```
DELTA:
  Short 24,600 PE delta: +0.30 (positive because you sold a put)
  Long 24,400 PE delta: –0.10 (negative because you bought a put)
  Net Delta: +0.20
  → Mildly bullish. For every 100 pt NIFTY rise, spread gains ~₹20/share

GAMMA:
  Net Gamma: –0.001 (NEGATIVE)
  → As NIFTY falls toward your short strike, delta becomes more negative
  → This is the opposite of debit spreads
  → Credit spreads have negative gamma → moves AGAINST you accelerate

THETA:
  Short 24,600 PE theta: +₹6/day (you EARN theta)
  Long 24,400 PE theta: –₹2/day (you PAY theta)
  Net Theta: +₹4/day ✅
  → TIME IS YOUR FRIEND. Every day NIFTY stays above 24,600,
    you earn ₹4 per share (₹300 per lot) for doing nothing.

VEGA:
  Short 24,600 PE vega: –₹8 (IV rise HURTS you)
  Long 24,400 PE vega: +₹4 (IV rise HELPS you)
  Net Vega: –₹4
  → IV drop helps you. IV rise hurts you.
  → This is why credit spreads prefer HIGH IV entry (IV likely to fall)
```

### 2.8 Bull Put Spread — Quick Summary

```
┌─────────────────────────────────────────────┐
│  BULL PUT SPREAD SUMMARY                    │
├─────────────────────────────────────────────┤
│  View: Mildly Bullish / Neutral             │
│  Legs: Short Put (higher) + Long Put (lower)│
│  Cost: Net CREDIT (receive premium)         │
│  Max Profit: Net Credit × Lot               │
│  Max Loss: (Width – Credit) × Lot           │
│  Breakeven: Short Strike – Net Credit       │
│  Best For: Range-bound, support holding     │
│  Theta: POSITIVE (time helps you) ✅        │
│  Vega: NEGATIVE (IV drop helps you)         │
│  Win Rate: ~60–70%                          │
│  Risk Level: Low (fully defined)            │
│  Beginner Friendly: ✅ YES                  │
│  Strike Width: 150–200 pts recommended      │
│  Expiry: 5–15 days to expiry                │
│  Exit: Close at 50% max profit or 50% max loss│
└─────────────────────────────────────────────┘
```

---

## CHAPTER 3: STRATEGY 6 — BEAR CALL SPREAD (CREDIT)

### 3.1 What Is a Bear Call Spread?

The mirror image of the Bull Put Spread:

1. **SELL** an ATM or slightly OTM Call (lower strike)
2. **BUY** a further OTM Call (higher strike) as protection
3. Same expiry, same underlying

```
BEAR CALL SPREAD = Short Call (lower strike) + Long Call (higher strike)

Net result: You RECEIVE premium upfront (credit)
Your view: NIFTY will stay BELOW the short call strike
```

### 3.2 When to Use

```
✅ USE Bear Call Spread when:
  → You are mildly bearish or neutral
  → NIFTY is below a strong resistance level
  → PCR is high (>1.3) suggesting overbought conditions
  → IV is moderate to high (calls are expensive → rich premium)
  → You want to profit from time decay and resistance holding
  → 5–15 days to expiry

❌ DON'T USE when:
  → You expect a sharp rally (short call will get destroyed)
  → IV is very low (premium too thin)
  → NIFTY is breaking above major resistance with volume
  → Strong bullish trend in place
```

### 3.3 Construction — Step by Step

```
Step 1: Identify your view
  → "NIFTY at 24,800. Strong resistance at 24,900.
     I expect NIFTY to stay below 24,900 for 7 days."

Step 2: Sell the lower strike call (income generator)
  → Sell 24,900 CE at ₹55 (slightly OTM, delta ~0.25)

Step 3: Buy the higher strike call (protection)
  → Buy 25,100 CE at ₹15 (further OTM, delta ~0.08)

Step 4: Calculate net credit
  → Net Credit = ₹55 – ₹15 = ₹40 per share = ₹3,000 per lot

Step 5: Calculate max profit
  → Max Profit = ₹40 × 75 = ₹3,000
  → Achieved if NIFTY expires BELOW 24,900

Step 6: Calculate max loss
  → Width = 25,100 – 24,900 = 200 pts
  → Max Loss = (200 – 40) × 75 = ₹160 × 75 = ₹12,000

Step 7: Calculate breakeven
  → Breakeven = Short Strike + Net Credit = 24,900 + 40 = 24,940

Step 8: Risk-Reward
  → R:R = 3,000 / 12,000 = 0.25:1
  → Again, "terrible" on paper. But win rate ~65–70%.
  → With management (close at 50% max loss):
     7 wins × ₹3,000 = ₹21,000
     3 losses × ₹6,000 = ₹18,000
     Net = +₹3,000 ✅
```

### 3.4 Payoff Diagram

```
Profit/Loss at Expiry (per share)

  ₹50 │
      │
  ₹40 │                              _______________ ← Max Profit: +₹40
      │                            /
  ₹20 │                          /
      │                        /
   ₹0 │──────────────────────/──────────────────────
      │                    / ↑
 –₹20 │                  /   Breakeven: 24,940
      │                /
 –₹60 │              /
      │            /
–₹120 │          /
      │        /
–₹160 │______/ ← Max Loss: –₹160
      │      ↑
      │  24,900 (Short Call)    25,100 (Long Call)
      │
      └──┬──────┬──────┬──────┬──────┬──────┬──────┬──
       24,700 24,800 24,900 25,000 25,100 25,200 25,300
                         NIFTY at Expiry

  Zones:
  • Below 24,900: Both calls OTM → Max Profit +₹40
  • 24,900–24,940: Partial profit (short call ITM, long call OTM)
  • 24,940: Breakeven
  • 24,940–25,100: Loss zone (increasing)
  • Above 25,100: Both calls ITM → Max Loss –₹160 (capped!)
```

### 3.5 Numerical Example — Key Scenarios

```
SETUP:
  NIFTY: 24,800 | Sell 24,900 CE ₹55 | Buy 25,100 CE ₹15
  Net Credit: ₹40 | Max Profit: ₹3,000 | Max Loss: ₹12,000
  Breakeven: 24,940

NIFTY expires at 24,750 (–50 pts): ✅✅ MAX PROFIT +₹3,000
NIFTY expires at 24,900 (at short strike): ✅ PROFIT +₹3,000
NIFTY expires at 24,940 (breakeven): ➡️ ₹0
NIFTY expires at 25,000 (+200 pts): ❌ LOSS –₹4,500
NIFTY expires at 25,200 (+400 pts): ❌❌ MAX LOSS –₹12,000
NIFTY gaps to 25,500 (+700 pts, black swan): ❌❌ MAX LOSS –₹12,000
  → Naked short call would lose: (600–55) × 75 = –₹40,875
  → Long call SAVED you ₹28,875! 🛡️
```

### 3.6 Greeks of a Bear Call Spread

```
DELTA:
  Short 24,900 CE delta: –0.25
  Long 25,100 CE delta: +0.08
  Net Delta: –0.17
  → Mildly bearish

THETA:
  Net Theta: +₹3.5/day ✅ (time helps you)

VEGA:
  Net Vega: –₹3.5 (IV drop helps you)

GAMMA:
  Net Gamma: –0.0008 (negative, moves against you accelerate)
```

### 3.7 Bear Call Spread — Quick Summary

```
┌─────────────────────────────────────────────┐
│  BEAR CALL SPREAD SUMMARY                   │
├─────────────────────────────────────────────┤
│  View: Mildly Bearish / Neutral             │
│  Legs: Short Call (lower) + Long Call (higher)│
│  Cost: Net CREDIT (receive premium)         │
│  Max Profit: Net Credit × Lot               │
│  Max Loss: (Width – Credit) × Lot           │
│  Breakeven: Short Strike + Net Credit       │
│  Best For: Range-bound, resistance holding  │
│  Theta: POSITIVE ✅                         │
│  Vega: NEGATIVE (IV drop helps)             │
│  Win Rate: ~60–70%                          │
│  Risk Level: Low (fully defined)            │
│  Beginner Friendly: ✅ YES                  │
│  Strike Width: 150–200 pts recommended      │
│  Expiry: 5–15 days to expiry                │
└─────────────────────────────────────────────┘
```

---

## CHAPTER 4: CREDIT SPREAD MANAGEMENT — THE KEY TO PROFITABILITY

### 4.1 Why Management Matters More Than Entry

Credit spreads have an "unfavorable" R:R on paper (risk 3–4x to make 1x). This means you **cannot afford to hold to max loss**. The entire edge comes from:

```
1. HIGH WIN RATE (65–70% of trades are winners)
2. EARLY PROFIT BOOKING (close at 50% of max profit)
3. EARLY LOSS CUTTING (close at 50% of max loss)
4. NEVER HOLDING TO EXPIRY (gamma risk)
```

### 4.2 The 50/50 Rule (Golden Rule of Credit Spreads)

```
TAKE PROFIT at 50% of Max Profit:
  Max Profit = ₹3,375
  Book at: ₹1,687 (50%)
  Why: The last 50% of profit takes 3x longer and has 3x more risk
       The probability of NIFTY moving against you increases near expiry
       Booking early frees capital for the next trade

CUT LOSS at 50% of Max Loss:
  Max Loss = ₹11,625
  Cut at: ₹5,812 (50%)
  Why: If the trade has moved this much against you, your thesis is wrong
       Holding hoping for a reversal is how credit spread traders blow up
       A 50% loss is recoverable. A 100% loss takes 3–4 winning trades.
```

### 4.3 The Mathematics of 50/50 Management

```
Over 20 trades with 50/50 management:

Assumptions:
  Max Profit per trade: ₹3,375
  Max Loss per trade: ₹11,625
  Take profit at: ₹1,687 (50%)
  Cut loss at: ₹5,812 (50%)
  Win rate: 65% (13 wins, 7 losses)

Results:
  13 wins × ₹1,687 = ₹21,931
  7 losses × ₹5,812 = ₹40,684
  Net = –₹18,753 ❌

Hmm, still negative. Let's adjust to a more realistic 70% win rate:
  14 wins × ₹1,687 = ₹23,618
  6 losses × ₹5,812 = ₹34,872
  Net = –₹11,254 ❌

Still negative! This shows that 50/50 with a 200-pt width is tough.
The solution: USE NARROWER WIDTHS or HIGHER WIN RATES.

With 100-pt width (credit ₹25, max loss ₹75):
  Take profit at: ₹12.5 (50%)
  Cut loss at: ₹37.5 (50%)
  Win rate: 75% (15 wins, 5 losses)
  15 × ₹12.5 × 75 = ₹14,062
  5 × ₹37.5 × 75 = ₹14,062
  Net = ₹0 (breakeven)

With 75% win rate and 60% profit booking:
  15 × ₹15 × 75 = ₹16,875
  5 × ₹37.5 × 75 = ₹14,062
  Net = +₹2,813 ✅

KEY INSIGHT: Credit spreads are a VOLUME GAME.
  → Small profits, high frequency, strict management
  → You need 70%+ win rate AND disciplined exits
  → This is why credit spreads are better for experienced traders
  → Beginners should start with DEBIT spreads (Week 18)
    and add credit spreads after 2–3 months of practice
```

### 4.4 Time-Based Exit Rules

```
RULE 1: Close at 50% of max profit (anytime)
  → Don't get greedy. Book and move on.

RULE 2: Close at 50% of max loss (anytime)
  → Don't hope. Cut and move on.

RULE 3: Close if 50% of time has passed and profit < 25%
  → The trade is stagnating. Theta isn't working fast enough.
  → Free capital for a better opportunity.

RULE 4: Close by 3–4 days to expiry (weekly)
  → Gamma risk increases exponentially in the last 3 days.
  → A 50-pt gap can blow past your breakeven.

RULE 5: Close immediately if NIFTY breaks your short strike
  → Your thesis is invalidated. Don't wait for breakeven.
  → A break of the short strike often leads to a break of the long strike.

RULE 6: NEVER hold credit spreads into events
  → Budget, RBI, Elections, US Fed
  → Gap risk can blow past BOTH strikes
  → Close 2 days before the event
```

### 4.5 Adjustment Techniques (When the Trade Goes Against You)

```
ADJUSTMENT 1: Roll Down/Up (Move the spread)
  Bull Put Spread going wrong (NIFTY falling toward short put):
  → Close the current spread at a loss
  → Open a new Bull Put Spread at LOWER strikes
  → Example: Close 24,600/24,400 → Open 24,400/24,200
  → This gives NIFTY more room but locks in a partial loss

ADJUSTMENT 2: Roll Out (Extend expiry)
  → Close current week spread
  → Open same strikes in next week's expiry
  → Collect more time premium to offset the loss
  → Only works if your thesis is still valid

ADJUSTMENT 3: Widen the Spread
  → Buy a further OTM put to reduce max loss
  → Example: Add 24,200 PE to your 24,600/24,400 spread
  → Converts to a "broken wing" spread (advanced)

ADJUSTMENT 4: Convert to Iron Condor
  → Add a Bear Call Spread on the other side
  → This collects more premium to offset the losing put spread
  → Reduces overall risk but caps profit on both sides

⚠️ BEGINNER RULE: Don't adjust. Just close at 50% max loss.
   Adjustments add complexity and often make losses worse.
   Master the basic entry/exit first (3–6 months).
```

---

## CHAPTER 5: STRATEGY 7 — LONG STRADDLE (VOLATILITY PLAY)

### 5.1 What Is a Long Straddle?

A Long Straddle is a **direction-neutral** strategy that profits from a BIG move in EITHER direction:

1. **BUY** an ATM Call
2. **BUY** an ATM Put (same strike, same expiry)

```
LONG STRADDLE = Long ATM Call + Long ATM Put (same strike)

Net result: You PAY premium (debit) — and it's EXPENSIVE
Your view: NIFTY will make a HUGE move, but you don't know which direction
```

### 5.2 When to Use

```
✅ USE Long Straddle when:
  → Major event approaching (Budget, Election results, RBI surprise)
  → NIFTY has been consolidating in a tight range for days
  → IV is LOW and you expect it to SPIKE (IV expansion)
  → You expect a move of 300+ pts but don't know direction
  → 5–10 days to expiry (need time for the move to develop)

❌ DON'T USE when:
  → IV is already high (options are expensive → high breakeven)
  → Market is already trending (direction is clear → use spreads)
  → No catalyst for a big move (NIFTY will stay range-bound)
  → Less than 3 days to expiry (theta will destroy both legs)
```

### 5.3 Construction

```
Step 1: Identify the event
  → "Union Budget in 5 days. NIFTY at 24,700.
     IV is at 12% (low). Expected to spike to 18%+ before Budget."

Step 2: Buy ATM Call
  → Buy 24,700 CE at ₹130

Step 3: Buy ATM Put (SAME strike)
  → Buy 24,700 PE at ₹120

Step 4: Calculate total cost
  → Total Debit = ₹130 + ₹120 = ₹250 per share
  → Total Cost = ₹250 × 75 = ₹18,750 per lot
  → This is EXPENSIVE. You're buying two ATM options.

Step 5: Calculate breakevens (TWO breakevens!)
  → Upper Breakeven = Strike + Total Premium = 24,700 + 250 = 24,950
  → Lower Breakeven = Strike – Total Premium = 24,700 – 250 = 24,450
  → NIFTY must move MORE than 250 pts in EITHER direction to profit

Step 6: Calculate max profit
  → UNLIMITED on the upside (call keeps gaining)
  → SUBSTANTIAL on the downside (put keeps gaining until NIFTY → 0)
  → Max Loss: ₹250 × 75 = ₹18,750 (if NIFTY expires exactly at 24,700)
```

### 5.4 Payoff Diagram

```
Profit/Loss at Expiry (per share)

  ₹300 │                                          /
       │                                        /
  ₹200 │                                      /
       │                                    /
  ₹100 │                                  /
       │                                /
    ₹0 │──────────────────────────────/──────────────────────
       │                          /  ↑
 –₹100 │                        /    Upper BE: 24,950
       │                      /
 –₹200 │                    /
       │                  /
 –₹250 │________________/ ← Max Loss at 24,700 (strike)
       │                \
 –₹200 │                  \
       │                    \
 –₹100 │                      \
       │                        \
    ₹0 │                          \
       │                            \
  ₹100 │                              \
       │                                \
  ₹200 │                                  \
       │
       └──┬──────┬──────┬──────┬──────┬──────┬──────┬──
        24,200 24,300 24,450 24,700 24,950 25,100 25,200
                  Lower BE    Strike   Upper BE
                          NIFTY at Expiry

  Key Features:
  • V-shaped payoff (profits on BOTH sides)
  • Max loss at the strike (NIFTY doesn't move)
  • Two breakevens: Strike ± Total Premium
  • Profit zone: Below 24,450 OR Above 24,950
  • Loss zone: Between 24,450 and 24,950 (500-pt dead zone!)
```

### 5.5 Numerical Example — Budget Day

```
SETUP:
  NIFTY: 24,700 | 5 days to Budget
  Buy 24,700 CE at ₹130 | Buy 24,700 PE at ₹120
  Total Cost: ₹250 × 75 = ₹18,750
  Upper BE: 24,950 | Lower BE: 24,450

PRE-BUDGET (Day 1–4): NIFTY drifts to 24,720 (+20 pts)
  IV rises from 12% to 17% (vega gain!)
  24,700 CE: ₹130 → ₹165 (+₹35, delta +₹10, vega +₹25)
  24,700 PE: ₹120 → ₹145 (+₹25, delta –₹5, vega +₹30)
  Combined value: ₹310 (was ₹250)
  P&L: +₹60 × 75 = +₹4,500 ✅
  → PROFIT BEFORE THE EVENT from IV expansion alone!
  → This is the ideal scenario: buy early, sell before event

BUDGET DAY (Day 5): FM announces tax cuts. NIFTY gaps to 25,100 (+400 pts)
  IV crushes from 17% to 13% (event over)
  24,700 CE: Intrinsic ₹400, but IV crush reduces to ~₹380
  24,700 PE: OTM → ₹5 (nearly worthless)
  Combined value: ₹385
  P&L: (₹385 – ₹250) × 75 = +₹10,125 ✅✅
  → PROFITABLE despite IV crush because the move was large enough

ALTERNATIVE BUDGET DAY: FM announces tax hikes. NIFTY crashes to 24,300 (–400 pts)
  24,700 CE: OTM → ₹5
  24,700 PE: Intrinsic ₹400, after IV crush ~₹380
  Combined value: ₹385
  P&L: +₹10,125 ✅✅
  → Same profit! Direction didn't matter.

WORST CASE: Budget is boring. NIFTY stays at 24,710 (+10 pts)
  IV crushes from 17% to 12%
  24,700 CE: ₹70 (theta + IV crush destroyed ₹60)
  24,700 PE: ₹65 (theta + IV crush destroyed ₹55)
  Combined value: ₹135
  P&L: (₹135 – ₹250) × 75 = –₹8,625 ❌❌
  → Significant loss. The "dead zone" killed you.
```

### 5.6 Greeks of a Long Straddle

```
DELTA:
  Long CE delta: +0.50
  Long PE delta: –0.50
  Net Delta: 0.00 (DIRECTION NEUTRAL)
  → The straddle doesn't care about direction initially
  → As NIFTY moves, delta shifts (becomes positive if up, negative if down)

GAMMA:
  Net Gamma: +0.004 (VERY HIGH — double the single option)
  → Delta changes rapidly as NIFTY moves
  → This is why straddles profit from big moves
  → Gamma is the straddle's engine

THETA:
  Net Theta: –₹16/day (VERY NEGATIVE — double the single option)
  → You're paying time decay on TWO options
  → This is the straddle's biggest enemy
  → Every day NIFTY doesn't move, you lose ₹1,200 per lot

VEGA:
  Net Vega: +₹20 (VERY HIGH — double the single option)
  → IV changes have massive impact
  → IV rise of 3% = +₹60 per share = +₹4,500 per lot
  → This is why you buy straddles when IV is LOW
```

### 5.7 Long Straddle — Quick Summary

```
┌─────────────────────────────────────────────┐
│  LONG STRADDLE SUMMARY                      │
├─────────────────────────────────────────────┤
│  View: Big Move Expected (direction unknown)│
│  Legs: Long ATM Call + Long ATM Put         │
│  Cost: Net DEBIT (expensive!)               │
│  Max Profit: Unlimited (upside), Large (down)│
│  Max Loss: Total Premium (if NIFTY at strike)│
│  Breakevens: Strike ± Total Premium         │
│  Best For: Events (Budget, RBI, Elections)  │
│  Theta: VERY NEGATIVE ❌❌                  │
│  Vega: VERY POSITIVE ✅✅                   │
│  Gamma: VERY POSITIVE ✅✅                  │
│  Win Rate: ~30–35% (needs big move)         │
│  Risk Level: Moderate (defined but expensive)│
│  Beginner Friendly: ⚠️ CAUTION             │
│  Key Rule: Buy when IV is LOW, sell BEFORE  │
│            the event (IV expansion profit)  │
└─────────────────────────────────────────────┘
```

---

## CHAPTER 6: STRATEGY 8 — LONG STRANGLE (CHEAPER STRADDLE)

### 6.1 What Is a Long Strangle?

A cheaper version of the straddle using OTM options:

1. **BUY** an OTM Call (above spot)
2. **BUY** an OTM Put (below spot)
3. Same expiry, different strikes

```
LONG STRANGLE = Long OTM Call + Long OTM Put (different strikes)

vs Straddle:
  Straddle: Buy 24,700 CE + Buy 24,700 PE (same strike, expensive)
  Strangle: Buy 24,900 CE + Buy 24,500 PE (OTM, cheaper)
```

### 6.2 Construction

```
NIFTY: 24,700 | 5 days to expiry
Buy: 24,900 CE at ₹40 (OTM, delta ~0.20)
Buy: 24,500 PE at ₹35 (OTM, delta ~–0.20)
Total Cost: ₹75 per share = ₹5,625 per lot

Compare to Straddle: ₹250 × 75 = ₹18,750
→ Strangle is 70% CHEAPER!

Breakevens:
  Upper BE: 24,900 + 75 = 24,975
  Lower BE: 24,500 – 75 = 24,425
  → Dead zone: 24,425–24,975 (550 pts — WIDER than straddle!)

Max Loss: ₹75 × 75 = ₹5,625 (if NIFTY between 24,500–24,900 at expiry)
```

### 6.3 Straddle vs Strangle Comparison

```
┌────────────────────┬──────────────────────┬──────────────────────┐
│                    │ Long Straddle        │ Long Strangle        │
├────────────────────┼──────────────────────┼──────────────────────┤
│ Strikes            │ Same (ATM)           │ Different (OTM)      │
│ Cost               │ ₹18,750 (expensive)  │ ₹5,625 (affordable)  │
│ Max Loss           │ ₹18,750              │ ₹5,625               │
│ Upper Breakeven    │ 24,950 (250 pts)     │ 24,975 (275 pts)     │
│ Lower Breakeven    │ 24,450 (250 pts)     │ 24,425 (275 pts)     │
│ Dead Zone Width    │ 500 pts              │ 550 pts              │
│ Move Needed        │ 250+ pts             │ 275+ pts             │
│ Theta Damage       │ –₹16/day (severe)    │ –₹6/day (moderate)   │
│ Vega Benefit       │ +₹20 (huge)          │ +₹12 (good)          │
│ Gamma              │ +0.004 (explosive)   │ +0.002 (moderate)    │
│ Win Rate           │ ~30–35%              │ ~25–30%              │
│ Best For           │ Major events         │ Moderate events      │
│ Beginner Friendly  │ ⚠️ Caution          │ ⚠️ Caution          │
└────────────────────┴──────────────────────┴──────────────────────┘
```

### 6.4 When to Choose Strangle Over Straddle

```
Choose STRADDLE when:
  → You expect a MASSIVE move (400+ pts)
  → Event is 5–7 days away (time for IV expansion)
  → IV is very low (IVR < 20%)
  → You can afford the higher cost
  → You plan to exit BEFORE the event (IV play)

Choose STRANGLE when:
  → You expect a LARGE move (250–400 pts)
  → Budget is tight (can't afford straddle)
  → IV is moderate (IVR 30–50%)
  → You want lower theta damage
  → You're okay with a wider dead zone
```

### 6.5 Long Strangle — Quick Summary

```
┌─────────────────────────────────────────────┐
│  LONG STRANGLE SUMMARY                      │
├─────────────────────────────────────────────┤
│  View: Big Move Expected (direction unknown)│
│  Legs: Long OTM Call + Long OTM Put         │
│  Cost: Net DEBIT (cheaper than straddle)    │
│  Max Profit: Unlimited / Large              │
│  Max Loss: Total Premium                    │
│  Breakevens: Call Strike + Prem /           │
│              Put Strike – Prem              │
│  Best For: Events on a budget               │
│  Theta: NEGATIVE (but less than straddle)   │
│  Vega: POSITIVE                             │
│  Win Rate: ~25–30%                          │
│  Risk Level: Low (defined, cheap)           │
│  Beginner Friendly: ⚠️ Moderate            │
└─────────────────────────────────────────────┘
```

---

## CHAPTER 7: STRATEGY 9 — IRON CONDOR (RANGE-BOUND INCOME MACHINE)

### 7.1 What Is an Iron Condor?

The Iron Condor combines a Bull Put Spread AND a Bear Call Spread simultaneously. It's the **ultimate range-bound strategy**:

1. **SELL** an OTM Put (lower strike) — Bull Put Spread short leg
2. **BUY** a further OTM Put (even lower) — Bull Put Spread long leg
3. **SELL** an OTM Call (upper strike) — Bear Call Spread short leg
4. **BUY** a further OTM Call (even higher) — Bear Call Spread long leg

```
IRON CONDOR = Bull Put Spread + Bear Call Spread
            = Short Put + Long Put + Short Call + Long Call
            = 4 legs total

Your view: NIFTY will stay within a RANGE until expiry
```

### 7.2 The Visual

```
IRON CONDOR STRUCTURE:

  25,100 CE: BUY  (protection — Bear Call long leg)     Wing
  24,900 CE: SELL (income — Bear Call short leg)        Body
  ──── NIFTY: 24,700 ────
  24,500 PE: SELL (income — Bull Put short leg)         Body
  24,300 PE: BUY  (protection — Bull Put long leg)      Wing

  The "body" (24,500–24,900) is your profit zone
  The "wings" (24,300 and 25,100) cap your losses
  Looks like a condor bird with spread wings → hence the name
```

### 7.3 When to Use

```
✅ USE Iron Condor when:
  → NIFTY is range-bound (trading in a 300–500 pt range for weeks)
  → No major events in the next 10–15 days
  → IV is moderate to high (IVR > 50%) → rich premium on both sides
  → PCR is near 1.0 (neutral sentiment)
  → OI shows strong walls on both sides (e.g., 24,500 PE and 24,900 CE)
  → 10–20 days to expiry (theta needs time to work)

❌ DON'T USE when:
  → NIFTY is trending strongly in either direction
  → Major event approaching (Budget, RBI, Elections)
  → IV is very low (premium too thin to justify risk)
  → Less than 5 days to expiry (gamma risk too high)
```

### 7.4 Construction — Step by Step

```
SETUP:
  NIFTY: 24,700 (Monday, 10 days to expiry)
  View: NIFTY will stay between 24,500 and 24,900
  IV: 15% (IVR 55% — moderate)

LEG 1: Sell 24,500 PE at ₹55 (Bull Put short leg)
LEG 2: Buy 24,300 PE at ₹18 (Bull Put long leg)
LEG 3: Sell 24,900 CE at ₹50 (Bear Call short leg)
LEG 4: Buy 25,100 CE at ₹15 (Bear Call long leg)

NET CREDIT:
  Put side credit: ₹55 – ₹18 = ₹37
  Call side credit: ₹50 – ₹15 = ₹35
  Total Credit: ₹37 + ₹35 = ₹72 per share
  Total Premium: ₹72 × 75 = ₹5,400 per lot

MAX PROFIT:
  = Total Credit × Lot = ₹72 × 75 = ₹5,400
  → Achieved if NIFTY expires between 24,500 and 24,900

MAX LOSS:
  = (Width – Total Credit) × Lot
  = (200 – 72) × 75 = ₹128 × 75 = ₹9,600
  → Achieved if NIFTY expires below 24,300 OR above 25,100

BREAKEVENS:
  Upper BE: 24,900 + 72 = 24,972
  Lower BE: 24,500 – 72 = 24,428
  → Profit zone: 24,428 to 24,972 (544 pts wide!)
  → NIFTY has a 544-pt range to stay within → high probability

RISK-REWARD:
  R:R = 5,400 / 9,600 = 0.56:1
  → Better than individual credit spreads because you collect
    premium from BOTH sides
  → Win rate: ~70–75% (wide profit zone)
```

### 7.5 Payoff Diagram

```
Profit/Loss at Expiry (per share)

  ₹80 │
      │
  ₹72 │          _______________ ← Max Profit: +₹72
      │        / |             | \
  ₹50 │      /   |             |   \
      │    /     |             |     \
  ₹25 │  /       |             |       \
      │/         |             |         \
   ₹0 │──────────|─────────────|──────────\──────────
      │          |             |            \
 –₹25 │          |             |              \
      │          |             |                \
 –₹72 │          |             |                  \
      │          |             |                    \
–₹128 │          |             |                      \____
      │          |             |                           ↑
      │          ↑             ↑                      25,100 (Long Call)
      │     24,500 (SP)   24,900 (SC)
      │     24,300 (LP)
      │
      └──┬──────┬──────┬──────┬──────┬──────┬──────┬──
       24,100 24,300 24,500 24,700 24,900 25,100 25,300
                         NIFTY at Expiry

  Zones:
  • 24,500–24,900: MAX PROFIT (+₹72) — all options expire OTM
  • 24,428–24,500: Partial profit (put side breaching)
  • 24,900–24,972: Partial profit (call side breaching)
  • Below 24,300: MAX LOSS (–₹128) — put side fully ITM
  • Above 25,100: MAX LOSS (–₹128) — call side fully ITM
```

### 7.6 Greeks of an Iron Condor

```
DELTA:
  Net Delta: ~0.00 to +0.05 (nearly NEUTRAL)
  → The put side and call side deltas cancel each other
  → Iron Condor doesn't care about small directional moves

GAMMA:
  Net Gamma: –0.002 (NEGATIVE)
  → Large moves hurt you (both short legs accelerate against you)
  → This is the Iron Condor's biggest risk

THETA:
  Net Theta: +₹7/day ✅✅ (VERY POSITIVE)
  → You're earning theta on TWO short legs
  → Every day NIFTY stays in range, you earn ₹525 per lot
  → This is the Iron Condor's engine

VEGA:
  Net Vega: –₹8 (NEGATIVE)
  → IV drop helps you (both short legs benefit)
  → IV rise hurts you
  → This is why you enter Iron Condors when IV is HIGH
```

### 7.7 Iron Condor Management

```
PROFIT MANAGEMENT:
  → Close at 50% of max profit (₹2,700)
  → On a 10-day trade, this typically happens by day 5–7
  → Don't hold to expiry — gamma risk in last 3 days

LOSS MANAGEMENT:
  → Close if NIFTY breaks EITHER short strike (24,500 or 24,900)
  → Close at 50% of max loss (₹4,800)
  → Don't "hope" NIFTY comes back — trending markets destroy condors

ADJUSTMENT (Advanced):
  → If NIFTY approaches 24,900 (call side threatened):
    Close the call spread, roll it higher (25,000/25,200)
    This widens the range but reduces max profit
  → If NIFTY approaches 24,500 (put side threatened):
    Close the put spread, roll it lower (24,400/24,200)
  → BEGINNERS: Don't adjust. Close and re-enter fresh.
```

### 7.8 Iron Condor — Quick Summary

```
┌─────────────────────────────────────────────┐
│  IRON CONDOR SUMMARY                        │
├─────────────────────────────────────────────┤
│  View: Neutral / Range-Bound                │
│  Legs: 4 (Short Put + Long Put +            │
│           Short Call + Long Call)           │
│  Cost: Net CREDIT (receive premium)         │
│  Max Profit: Total Credit × Lot             │
│  Max Loss: (Width – Credit) × Lot           │
│  Breakevens: Short Strikes ± Net Credit     │
│  Best For: Range-bound, no events, high IV  │
│  Theta: VERY POSITIVE ✅✅                  │
│  Vega: NEGATIVE (IV drop helps)             │
│  Gamma: NEGATIVE (big moves hurt)           │
│  Win Rate: ~70–75%                          │
│  Risk Level: Low (fully defined)            │
│  Beginner Friendly: ⚠️ Moderate (4 legs)   │
│  Strike Width: 150–200 pts each side        │
│  Expiry: 10–20 days to expiry               │
│  Exit: 50% max profit or short strike break │
└─────────────────────────────────────────────┘
```

---

## CHAPTER 8: STRATEGY 10 — CALENDAR SPREAD (TIME DECAY ARBITRAGE)

### 8.1 What Is a Calendar Spread?

A Calendar Spread exploits the fact that **near-term options decay faster than long-term options**:

1. **SELL** a near-term option (current week expiry)
2. **BUY** a longer-term option (next month expiry)
3. SAME strike, DIFFERENT expiries

```
CALENDAR SPREAD = Short Near-Term + Long Far-Term (same strike)

Example:
  Sell: 24,700 CE (this Thursday expiry) at ₹45
  Buy: 24,700 CE (next month expiry) at ₹180
  
  Net Debit: ₹180 – ₹45 = ₹135 per share
```

### 8.2 The Core Logic

```
Near-term option theta: –₹12/day (decays FAST)
Long-term option theta: –₹4/day (decays SLOW)

Net theta: –₹4 + ₹12 = +₹8/day ✅

→ You're earning the DIFFERENCE in time decay
→ The near-term option loses value 3x faster than the long-term
→ As days pass, the spread WIDENS in your favor
→ This is "theta arbitrage"
```

### 8.3 When to Use

```
✅ USE Calendar Spread when:
  → NIFTY is near a major strike and likely to stay there
  → IV is LOW and you expect it to RISE (long-term vega benefit)
  → You want to profit from time decay differential
  → No major events in the near term
  → You're comfortable holding for 1–2 weeks

❌ DON'T USE when:
  → NIFTY is trending strongly (will move away from your strike)
  → IV is very high (near-term premium is already inflated)
  → Major event between the two expiries
  → You need quick profits (calendar spreads are slow)
```

### 8.4 Construction

```
SETUP:
  NIFTY: 24,700 (Monday)
  Current week expiry: Thursday (3 days)
  Next month expiry: 28 days

SELL: 24,700 CE (Thursday) at ₹45
BUY: 24,700 CE (next month) at ₹180
Net Debit: ₹135 per share = ₹10,125 per lot

HOW IT PROFITS:
  Day 1 (Tuesday):
    Near-term CE theta: –₹12 → now ₹33
    Far-term CE theta: –₹4 → now ₹176
    Spread value: ₹176 – ₹33 = ₹143 (was ₹135)
    P&L: +₹8 × 75 = +₹600 ✅

  Day 2 (Wednesday):
    Near-term CE theta: –₹15 → now ₹18
    Far-term CE theta: –₹4 → now ₹172
    Spread value: ₹172 – ₹18 = ₹154
    P&L: +₹19 × 75 = +₹1,425 ✅

  Day 3 (Thursday Expiry):
    Near-term CE expires → ₹0 (if NIFTY at 24,700, ATM = small intrinsic)
    Far-term CE: ~₹168 (lost ₹12 to theta over 3 days)
    Spread value: ₹168 – ₹0 = ₹168
    P&L: +₹33 × 75 = +₹2,475 ✅

  → After the near-term expires, you're left with a LONG 24,700 CE
    for next month at an effective cost of ₹135 (original debit)
  → You can now hold this as a directional position or sell it
```

### 8.5 Payoff Diagram

```
Profit/Loss at Near-Term Expiry (per share)

  ₹50 │
      │
  ₹35 │              ___
      │            /     \
  ₹20 │          /         \
      │        /             \
   ₹5 │      /                 \
      │    /                     \
  –₹10 │  /                       \
      │ /                           \
 –₹35 │/                               \
      │                                   \
 –₹60 │                                     \
      │                                       \
 –₹85 │                                         \
      │
      └──┬──────┬──────┬──────┬──────┬──────┬──────┬──
       24,400 24,500 24,600 24,700 24,800 24,900 25,000
                         NIFTY at Near Expiry

  Key Features:
  • Tent-shaped payoff (profit near the strike)
  • Max profit at or near the strike (24,700)
  • Losses if NIFTY moves far from strike in either direction
  • Similar to Iron Condor but with only 2 legs
```

### 8.6 Greeks of a Calendar Spread

```
DELTA:
  Net Delta: ~0.00 to +0.05 (nearly neutral at initiation)
  → Both options are at the same strike, so deltas nearly cancel
  → As NIFTY moves, delta shifts

GAMMA:
  Net Gamma: –0.001 (NEGATIVE)
  → Large moves away from the strike hurt you
  → The near-term option's gamma is higher, so moves against
    the short leg hurt more than the long leg helps

THETA:
  Net Theta: +₹8/day ✅✅ (VERY POSITIVE)
  → This is the calendar spread's primary profit engine
  → You earn the theta differential between the two expiries

VEGA:
  Net Vega: +₹12 ✅ (POSITIVE)
  → The long-term option has higher vega than the near-term
  → IV rise helps you (long vega dominates)
  → This is why calendar spreads are ideal when IV is LOW
    (you expect IV to rise, which boosts the long-term leg)
```

### 8.7 Calendar Spread — Quick Summary

```
┌─────────────────────────────────────────────┐
│  CALENDAR SPREAD SUMMARY                    │
├─────────────────────────────────────────────┤
│  View: Neutral + IV Expansion Expected      │
│  Legs: Short Near-Term + Long Far-Term      │
│        (same strike, different expiries)    │
│  Cost: Net DEBIT                            │
│  Max Profit: At the strike (near expiry)    │
│  Max Loss: Net Debit (if NIFTY far from strike)│
│  Best For: Low IV, range-bound, no events   │
│  Theta: VERY POSITIVE ✅✅                  │
│  Vega: POSITIVE ✅ (IV rise helps)          │
│  Gamma: NEGATIVE (big moves hurt)           │
│  Win Rate: ~50–55%                          │
│  Risk Level: Low (defined)                  │
│  Beginner Friendly: ⚠️ Moderate            │
│  Key Advantage: Profits from time + IV rise │
│  Key Risk: NIFTY moves away from strike     │
└─────────────────────────────────────────────┘
```

---

## CHAPTER 9: MASTER STRATEGY SELECTION FRAMEWORK

### 9.1 The Complete Decision Matrix

```
START: What is the market doing?

┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  1. STRONG UPTREND (NIFTY making HH/HL, 20EMA sloping up)  │
│     → Bull Call Spread (debit, moderate move expected)      │
│     → Naked Call (if very strong conviction, 400+ pts)      │
│     → Bull Put Spread (credit, sell puts below support)     │
│                                                             │
│  2. STRONG DOWNTREND (NIFTY making LH/LL, 20EMA sloping dn)│
│     → Bear Put Spread (debit, moderate decline expected)    │
│     → Naked Put (if very strong conviction, 400+ pts)       │
│     → Bear Call Spread (credit, sell calls above resistance)│
│                                                             │
│  3. RANGE-BOUND (NIFTY bouncing between S/R for 5+ days)   │
│     → Iron Condor (if 10+ days to expiry, IV > 50th pctl)  │
│     → Bull Put Spread + Bear Call Spread (separately)       │
│     → Calendar Spread (if IV is low, expect IV rise)        │
│     → DON'T use directional strategies                      │
│                                                             │
│  4. CONSOLIDATION BREAKOUT (tight range, about to break)   │
│     → Long Straddle (if direction unknown, big move expected)│
│     → Long Strangle (cheaper alternative)                    │
│     → Bull Call / Bear Put Spread (if direction is clear)   │
│                           │
│  5. EVENT APPROACHING (Budget, RBI, Elections in 3–7 days)  │
│     → Long Straddle/Strangle (BUY 5–7 days BEFORE event)    │
│       when IV is LOW (IVR < 30%)                            │
│     → EXIT before the event (capture IV expansion profit)   │
│     → DO NOT hold through the event (IV crush will kill you)│
│     → After the event: Re-enter with spreads once IV crushes│
│     → Protective Put (if you own stocks and fear crash)     │
│                                                             │
│  6. POST-EVENT (day after Budget/RBI/Elections)             │
│     → IV has crushed → options are now CHEAP                │
│     → Bull Call / Bear Put Spread (debit, IV is low)        │
│     → Calendar Spread (near-term IV crushed, far-term still │
│       elevated → theta + vega differential)                 │
│     → DO NOT sell premium (IV too low, not enough cushion)  │
│                                                             │
│  7. UNCERTAIN / NO CLEAR VIEW                               │
│     → DON'T TRADE. Cash is a position.                      │
│     → Wait for clarity. Forcing trades in uncertainty       │
│       is the #1 cause of retail losses.                     │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### 9.2 IV-Based Strategy Selection (Quick Reference)

```
┌──────────────┬──────────────────────────────────────────────┐
│ IV Regime    │ Best Strategies                              │
├──────────────┼──────────────────────────────────────────────┤
│ IVR 0–25%    │ BUY options (cheap):                         │
│ (Very Low)   │ → Long Straddle/Strangle (event plays)       │
│              │ → Bull Call / Bear Put Spread (directional)  │
│              │ → Calendar Spread (theta + vega play)        │
│              │ → AVOID selling premium (too thin)           │
├──────────────┼──────────────────────────────────────────────┤
│ IVR 25–50%   │ BALANCED:                                    │
│ (Low-Normal) │ → Bull Call / Bear Put Spread (directional)  │
│              │ → Bull Put / Bear Call Spread (income)       │
│              │ → Calendar Spread                            │
├──────────────┼──────────────────────────────────────────────┤
│ IVR 50–75%   │ SELL premium (rich):                         │
│ (Normal-High)│ → Bull Put / Bear Call Spread (credit)       │
│              │ → Iron Condor (range-bound)                  │
│              │ → AVOID buying straddles (too expensive)     │
├──────────────┼──────────────────────────────────────────────┤
│ IVR 75–100%  │ SELL aggressively (very rich):               │
│ (Very High)  │ → Iron Condor (wide range, high premium)     │
│              │ → Bull Put / Bear Call Spread (credit)       │
│              │ → AVOID buying ANY options (IV crush risk)   │
│              │ → Reduce position size by 50%                │
└──────────────┴──────────────────────────────────────────────┘
```

### 9.3 Capital-Based Strategy Selection

```
┌──────────────────┬──────────────────────────────────────────┐
│ Account Size     │ Suitable Strategies                      │
├──────────────────┼──────────────────────────────────────────┤
│ < ₹1,00,000      │ → Bull Call / Bear Put Spread (1 lot)   │
│ (Small)          │ → Long Strangle (1 lot, cheap)           │
│                  │ → AVOID Iron Condor (4 legs, high margin)│
│                  │ → AVOID credit spreads (margin ~₹50K)    │
│                  │ → Risk: ₹2,000 per trade (2%)            │
├──────────────────┼──────────────────────────────────────────┤
│ ₹1,00,000–3,00,000│ → All debit spreads (1–2 lots)         │
│ (Medium)         │ → Credit spreads (1 lot)                 │
│                  │ → Long Straddle (1 lot, events)          │
│                  │ → Iron Condor (1 lot, careful)           │
│                  │ → Risk: ₹4,000–6,000 per trade (2%)      │
├──────────────────┼──────────────────────────────────────────┤
│ ₹3,00,000–10,00,000│ → All strategies (2–3 lots)           │
│ (Large)          │ → Iron Condor (2 lots)                   │
│                  │ → Calendar Spread                        │
│                  │ → Covered Call / Protective Put          │
│                  │ → Risk: ₹6,000–20,000 per trade (2%)     │
├──────────────────┼──────────────────────────────────────────┤
│ > ₹10,00,000     │ → All strategies (3–5 lots)             │
│ (Very Large)     │ → Multi-expiry Iron Condors              │
│                  │ → Ratio spreads (advanced)               │
│                  │ → Portfolio hedging with Protective Puts │
│                  │ → Risk: ₹20,000+ per trade (2%)          │
└──────────────────┴──────────────────────────────────────────┘
```

### 9.4 The Complete Strategy Comparison Table (All 10 Strategies)

```
┌─────────────────┬───────┬───────┬───────┬───────┬──────┬──────┬───────┐
│ Strategy        │ Legs  │ Cost  │ Theta │ Vega  │ Win% │ R:R  │ Level │
├─────────────────┼───────┼───────┼───────┼───────┼──────┼──────┼───────┤
│ Covered Call    │ 2     │ Credit│ +     │ –     │ 65%  │ Var  │ Easy  │
│ Protective Put  │ 2     │ Debit │ –     │ +     │ 50%  │ Var  │ Easy  │
│ Bull Call Sprd  │ 2     │ Debit │ –     │ +     │ 45%  │ 1.5:1│ Easy  │
│ Bear Put Sprd   │ 2     │ Debit │ –     │ +     │ 45%  │ 1.5:1│ Easy  │
│ Bull Put Sprd   │ 2     │ Credit│ +     │ –     │ 65%  │ 0.3:1│ Med   │
│ Bear Call Sprd  │ 2     │ Credit│ +     │ –     │ 65%  │ 0.3:1│ Med   │
│ Long Straddle   │ 2     │ Debit │ ––    │ ++    │ 30%  │ 3:1+ │ Med   │
│ Long Strangle   │ 2     │ Debit │ –     │ +     │ 25%  │ 4:1+ │ Med   │
│ Iron Condor     │ 4     │ Credit│ ++    │ –     │ 70%  │ 0.5:1│ Hard  │
│ Calendar Sprd   │ 2     │ Debit │ ++    │ +     │ 50%  │ 1:1  │ Hard  │
└─────────────────┴───────┴───────┴───────┴───────┴──────┴──────┴───────┘

Key: + = helps you, – = hurts you, ++ = strongly helps, –– = strongly hurts
```

---

## CHAPTER 10: PRACTICAL EXERCISES

### Exercise 1: Bull Put Spread Construction

```
NIFTY is at 24,600 on Monday. Strong support at 24,400.
7 days to expiry. VIX = 16 (moderate-high). IVR = 60%.
PCR = 1.05 (neutral).

Available put premiums:
  24,600 PE: ₹95
  24,500 PE: ₹65
  24,400 PE: ₹40
  24,300 PE: ₹22
  24,200 PE: ₹10

Task:
  a) Construct a Bull Put Spread. Which strikes? Why?
  b) Calculate net credit, max profit, max loss, breakeven
  c) What is the net theta? Positive or negative?
  d) If NIFTY expires at 24,450, what is your P&L?
  e) At what NIFTY level do you achieve max profit?
```

### Exercise 2: Bear Call Spread Construction

```
NIFTY is at 24,800 on Tuesday. Triple top at 24,900.
5 days to expiry. VIX = 14 (normal). IVR = 45%.
PCR = 1.30 (bullish → contrarian caution).

Available call premiums:
  24,700 CE: ₹130
  24,800 CE: ₹80
  24,900 CE: ₹45
  25,000 CE: ₹22
  25,100 CE: ₹10

Task:
  a) Construct a Bear Call Spread. Which strikes? Why?
  b) Calculate net credit, max profit, max loss, breakeven
  c) What is the net delta? Positive or negative?
  d) If NIFTY expires at 24,850, what is your P&L?
  e) What is your exit plan (profit target and stop loss)?
```

### Exercise 3: Long Straddle vs Strangle Decision

```
Scenario: RBI policy announcement in 4 days.
NIFTY at 24,700. VIX = 11 (very low). IVR = 15%.
Expected move: 300–400 pts, direction unknown.

Straddle: Buy 24,700 CE ₹110 + Buy 24,700 PE ₹105 = ₹215 total
Strangle: Buy 24,900 CE ₹35 + Buy 24,500 PE ₹30 = ₹65 total

Task:
  a) Calculate breakevens for both
  b) Calculate max loss for both (per lot)
  c) Which would you choose and why?
  d) When would you exit this trade?
  e) What happens if RBI policy is a non-event and NIFTY moves only 50 pts?
```

### Exercise 4: Iron Condor Construction

```
NIFTY is at 24,700 on Monday. Range-bound for 2 weeks (24,500–24,900).
12 days to expiry. VIX = 15. IVR = 55%. No events in next 2 weeks.
PCR = 1.02 (neutral).

Available premiums:
  25,100 CE: ₹12    24,300 PE: ₹15
  24,900 CE: ₹42    24,500 PE: ₹48
  24,700 CE: ₹95    24,700 PE: ₹88

Task:
  a) Construct an Iron Condor. List all 4 legs with strikes and premiums.
  b) Calculate total credit, max profit, max loss
  c) Calculate both breakevens and the profit zone width
  d) What is the net theta? How much do you earn per day per lot?
  e) If NIFTY moves to 24,950 on day 8, what do you do?
```

### Exercise 5: Strategy Selection (Mixed Scenarios)

For each scenario, choose the BEST strategy from all 10 you've learned:

```
Scenario A:
  NIFTY at 24,700. Broke above 20-day resistance with 2x volume.
  Daily RSI at 62 (rising). VIX = 12 (low). IVR = 20%.
  Expect 200-pt rally over 5 days.
  → Strategy: _______ | Why: _______

Scenario B:
  NIFTY at 24,700. Stuck between 24,500 and 24,900 for 3 weeks.
  VIX = 16 (moderate). IVR = 65%. No events for 2 weeks.
  PCR = 1.0. OI walls at 24,500 PE and 24,900 CE.
  → Strategy: _______ | Why: _______

Scenario C:
  NIFTY at 24,700. Election results in 3 days.
  VIX = 22 (high). IVR = 85%. Direction completely unknown.
  Expected move: 500+ pts.
  → Strategy: _______ | Why: _______

Scenario D:
  NIFTY at 24,700. Day after Budget. IV crushed from 20% to 13%.
  VIX = 13 (low). FM announced positive reforms.
  Expect gradual 150-pt rally over 10 days.
  → Strategy: _______ | Why: _______

Scenario E:
  You own 1,000 shares of TCS at ₹3,800. Stock has rallied 15% in 2 months.
  You think it's overbought but don't want to sell.
  TCS 3,900 CE is trading at ₹80.
  → Strategy: _______ | Why: _______
```

---

## CHAPTER 11: EXERCISE ANSWERS

### Exercise 1 Answer: Bull Put Spread

```
a) Strike Selection:
  Sell: 24,500 PE at ₹65 (slightly OTM, above support at 24,400)
  Buy: 24,300 PE at ₹22 (further OTM, protection)
  Width: 200 pts
  
  Why these strikes?
  → 24,500 is above the strong support at 24,400 → high probability
    of staying above → short put likely expires OTM
  → 24,300 provides protection if support breaks
  → 200-pt width gives good credit while keeping max loss manageable
  → IVR at 60% means puts are reasonably expensive → good premium

b) Calculations:
  Net Credit: ₹65 – ₹22 = ₹43 per share = ₹3,225 per lot
  Max Profit: ₹43 × 75 = ₹3,225
  Max Loss: (200 – 43) × 75 = ₹157 × 75 = ₹11,775
  Breakeven: 24,500 – 43 = 24,457

c) Net Theta: POSITIVE (+₹4 to +₹5 per day)
  → Short put earns more theta than long put costs
  → Time decay works in your favor every day NIFTY stays above 24,500

d) NIFTY at 24,450:
  24,500 PE: ITM by 50 → you owe ₹50
  24,300 PE: OTM → ₹0
  Net P&L: (65 – 22 – 50) × 75 = –₹7 × 75 = –₹525
  → Small loss. Still above the long put strike.
  → Breakeven was 24,457, so 24,450 is just below breakeven.

e) Max profit achieved at or above 24,500 (short put strike).
  Both puts expire OTM → you keep the full ₹43 credit.
```

### Exercise 2 Answer: Bear Call Spread

```
a) Strike Selection:
  Sell: 24,900 CE at ₹45 (at triple top resistance, slightly OTM)
  Buy: 25,100 CE at ₹10 (protection, further OTM)
  Width: 200 pts
  
  Why?
  → 24,900 is the triple top → strong resistance → high probability
    NIFTY stays below → short call likely expires OTM
  → 25,100 caps loss if resistance breaks
  → PCR at 1.30 suggests overbought → bearish bias justified

b) Calculations:
  Net Credit: ₹45 – ₹10 = ₹35 per share = ₹2,625 per lot
  Max Profit: ₹35 × 75 = ₹2,625
  Max Loss: (200 – 35) × 75 = ₹165 × 75 = ₹12,375
  Breakeven: 24,900 + 35 = 24,935

c) Net Delta: NEGATIVE (~–0.17)
  → Short call delta: –0.25, Long call delta: +0.08
  → Net: –0.17 → mildly bearish
  → For every 100 pt NIFTY rise, spread loses ~₹17 per share

d) NIFTY at 24,850:
  24,900 CE: OTM → ₹0
  25,100 CE: OTM → ₹0
  Net P&L: +₹35 × 75 = +₹2,625
  → MAX PROFIT! NIFTY stayed below 24,900.

e) Exit Plan:
  Profit target: 50% of max profit = ₹1,312 (close when spread
    value drops to ₹17.5 from ₹35)
  Stop loss: 50% of max loss = ₹6,187 (close when spread
    value rises to ₹117.5 from ₹35)
  Time exit: Close by Wednesday EOD (2 days before expiry)
  Condition exit: Close immediately if NIFTY breaks 24,900 with volume
```

### Exercise 3 Answer: Straddle vs Strangle

```
a) Breakevens:
  Straddle: Upper = 24,700 + 215 = 24,915 | Lower = 24,700 – 215 = 24,485
  Strangle: Upper = 24,900 + 65 = 24,965 | Lower = 24,500 – 65 = 24,435

b) Max Loss (per lot):
  Straddle: ₹215 × 75 = ₹16,125
  Strangle: ₹65 × 75 = ₹4,875

c) Choice: LONG STRADDLE
  Why:
  → VIX is at 11 (very low, IVR 15%) → options are CHEAP
  → This is the IDEAL environment for straddles
  → IV is likely to spike from 11% to 18–20% before RBI
  → The vega gain alone could make the straddle profitable
    BEFORE the event (IV expansion from 11% to 18% = +7%)
    Vega gain ≈ ₹20 × 7 × 75 = ₹10,500 per lot!
  → The straddle's higher vega (+₹20 vs strangle's +₹12) captures
    more of this IV expansion
  → The strangle is cheaper but has a wider dead zone (530 pts vs 430 pts)
  → With IV this low, the straddle's higher cost is justified

d) Exit Plan:
  → EXIT 1 day BEFORE the RBI announcement (capture IV expansion)
  → Do NOT hold through the event (IV crush will destroy value)
  → If IV spikes to 18%+ and NIFTY hasn't moved much → SELL for vega profit
  → If you must hold through: only if the expected move exceeds 300 pts

e) Non-event (NIFTY moves only 50 pts):
  → IV crushes from 18% back to 12%
  → Straddle value: ~₹130 (from ₹215 entry)
  → Loss: (215 – 130) × 75 = –₹6,375 (–40%)
  → This is the straddle's worst case: small move + IV crush
  → This is why you exit BEFORE the event (IV expansion profit)
    rather than holding through (IV crush risk)
```

### Exercise 4 Answer: Iron Condor

```
a) Iron Condor Construction:
  LEG 1: Sell 24,500 PE at ₹48 (Bull Put short leg)
  LEG 2: Buy 24,300 PE at ₹15 (Bull Put long leg)
  LEG 3: Sell 24,900 CE at ₹42 (Bear Call short leg)
  LEG 4: Buy 25,100 CE at ₹12 (Bear Call long leg)
  
  Why these strikes?
  → 24,500 and 24,900 are the established range boundaries
  → 200-pt width on each side for balanced risk
  → OI walls at these strikes confirm the range

b) Calculations:
  Put side credit: ₹48 – ₹15 = ₹33
  Call side credit: ₹42 – ₹12 = ₹30
  Total Credit: ₹33 + ₹30 = ₹63 per share
  Max Profit: ₹63 × 75 = ₹4,725 per lot
  Max Loss: (200 – 63) × 75 = ₹137 × 75 = ₹10,275 per lot

c) Breakevens:
  Upper BE: 24,900 + 63 = 24,963
  Lower BE: 24,500 – 63 = 24,437
  Profit zone width: 24,963 – 24,437 = 526 pts
  → NIFTY has a 526-pt range to stay within → ~70–75% probability

d) Net Theta: +₹7/day (approximately)
  → Daily earnings: ₹7 × 75 = ₹525 per lot per day
  → Over 12 days (if held to expiry): ₹525 × 12 = ₹6,300
  → But you'll close at 50% profit (~day 6–7): ~₹3,150–3,675

e) NIFTY at 24,950 on day 8:
  → NIFTY has breached the short call strike (24,900) by 50 pts
  → The call side is losing money
  → ACTION: Close the entire Iron Condor
  → Don't wait for it to come back — the range thesis is broken
  → Estimated P&L at this point:
    Put side: ~₹25 profit (NIFTY far from puts, theta earned)
    Call side: ~₹–40 loss (24,900 CE now ITM by 50)
    Net: ~₹–15 per share = –₹1,125 per lot
  → This is well within the 50% max loss limit (₹5,137)
  → Close, accept the small loss, and wait for the next range setup
```

### Exercise 5 Answer: Strategy Selection

```
Scenario A: BULL CALL SPREAD
  Why: Strong directional breakout (technical confirmation),
  low IV (IVR 20% → options cheap to buy), moderate move expected
  (200 pts). Buy 24,700 CE, sell 24,900 CE. Low IV makes debit
  spreads ideal. The 200-pt target matches the spread width perfectly.

Scenario B: IRON CONDOR
  Why: Classic range-bound setup (3 weeks, clear S/R), moderate-high
  IV (IVR 65% → rich premium for selling), neutral PCR, strong OI
  walls at 24,500 and 24,900. Sell 24,500 PE + 24,900 CE,
  buy 24,300 PE + 25,100 CE. Collect premium from both sides.
  12 days to expiry gives theta time to work.

Scenario C: AVOID TRADING (or Long Strangle with tiny size)
  Why: VIX at 22 and IVR at 85% means options are EXTREMELY expensive.
  A straddle would cost ₹350+ (breakevens 24,200/25,200 — 1000-pt range!).
  IV crush after elections will destroy 50–70% of premium.
  Even a 500-pt move may not be enough to profit.
  Best action: Stay out. Wait for post-election IV crush,
  then enter debit spreads when IV drops to 12–13%.
  If you MUST trade: Long Strangle with 1 lot, 25,200 CE + 24,200 PE,
  accept that it's a low-probability gamble.

Scenario D: BULL CALL SPREAD (or Calendar Spread)
  Why: Post-event IV crush means options are now CHEAP (VIX 13, IVR ~25%).
  Debit spreads are ideal. Buy 24,700 CE, sell 24,850 CE (next week).
  The 150-pt target over 10 days is moderate — perfect for a spread.
  Alternative: Calendar Spread — sell this week's 24,700 CE (IV crushed),
  buy next month's 24,700 CE (IV still slightly elevated).
  Profit from theta differential + potential IV normalization.

Scenario E: COVERED CALL
  Why: You own the stock, it's overbought, you don't want to sell.
  Sell TCS 3,900 CE at ₹80. Collect ₹80 × 1,000 = ₹80,000 premium.
  If TCS stays below 3,900: keep premium + shares (₹80,000 income = 2.1% in a month).
  If TCS crosses 3,900: shares called away at 3,900 (₹100 gain + ₹80 premium = ₹180/share).
  Win-win. You generate income while waiting for a better exit price.
```

---

## WEEK 19 SELF-TEST (25 Questions)

**Instructions:** Score yourself at the end. You need 20/25 to proceed to Week 20.

---

**Q1.** What is the fundamental difference between debit and credit strategies?

**Q2.** A Bull Put Spread consists of which two positions?

**Q3.** In a Bull Put Spread, is theta positive or negative? Why?

**Q4.** Calculate the max profit for: Sell 24,600 PE at ₹55, Buy 24,400 PE at ₹18. Lot size 75.

**Q5.** What is the breakeven for the Bull Put Spread in Q4?

**Q6.** A Bear Call Spread consists of which two positions?

**Q7.** Calculate the max loss for: Sell 24,900 CE at ₹40, Buy 25,100 CE at ₹12. Lot size 75.

**Q8.** What is the "50/50 Rule" for credit spread management?

**Q9.** Why should you NEVER hold a credit spread into a major event?

**Q10.** A Long Straddle consists of which two positions?

**Q11.** What are the two breakevens for a Long Straddle at strike 24,700 with total premium ₹220?

**Q12.** What is the net delta of a Long Straddle at initiation?

**Q13.** Why is a Long Straddle most profitable when bought at LOW IV?

**Q14.** What is the difference between a Long Straddle and a Long Strangle?

**Q15.** A Long Strangle costs ₹70 total. Call strike 24,900, Put strike 24,500. What are the breakevens?

**Q16.** An Iron Condor combines which two strategies?

**Q17.** Calculate the total credit for this Iron Condor:
Sell 24,500 PE ₹45, Buy 24,300 PE ₹15, Sell 24,900 CE ₹40, Buy 25,100 CE ₹12.

**Q18.** What is the net theta of an Iron Condor? Why?

**Q19.** What is the net gamma of an Iron Condor? What does this mean for risk?

**Q20.** A Calendar Spread profits from what two factors?

**Q21.** In a Calendar Spread, which expiry do you SELL and which do you BUY?

**Q22.** When should you use an Iron Condor vs a Bull Call Spread?

**Q23.** NIFTY is at 24,700. IVR = 80%. VIX = 19. No events.
Which strategy type is best: debit or credit? Why?

**Q24.** NIFTY is at 24,700. IVR = 15%. VIX = 11. Budget in 5 days.
Which strategy is best? Why?

**Q25.** List the 4 exit rules for credit spreads.

---

## SELF-TEST ANSWERS

**A1.** Debit strategies: You PAY premium upfront. Profit from directional moves. Theta hurts you. Best in trending markets with low IV. Credit strategies: You RECEIVE premium upfront. Profit from time decay and range-bound markets. Theta helps you. Best in range-bound markets with high IV.

**A2.** Short Put at a higher strike (income) + Long Put at a lower strike (protection). Same expiry, same underlying. Net result is a credit.

**A3.** **Positive.** The short put earns more theta than the long put costs. Net theta is typically +₹3 to +₹5 per day. Time decay works in your favor — every day NIFTY stays above your short strike, the spread loses value (which is good for you since you sold it).

**A4.** Max Profit = Net Credit × Lot = (₹55 – ₹18) × 75 = ₹37 × 75 = **₹2,775**

**A5.** Breakeven = Short Strike – Net Credit = 24,600 – 37 = **24,563**

**A6.** Short Call at a lower strike (income) + Long Call at a higher strike (protection). Same expiry, same underlying. Net result is a credit.

**A7.** Max Loss = (Width – Net Credit) × Lot = (200 – 28) × 75 = ₹172 × 75 = **₹12,900**

**A8.** **Take profit at 50% of max profit. Cut loss at 50% of max loss.** Don't hold credit spreads to expiry. The last 50% of profit takes too long and carries too much gamma risk. The last 50% of loss means your thesis is wrong — cut it.

**A9.** Because **gap risk** can blow past BOTH strikes. Events like Budget or RBI can cause 300–500 pt gaps. If NIFTY gaps past your long protective leg, you're at max loss instantly. Additionally, IV crush after the event can distort the spread's value. Close 2 days before any major event.

**A10.** Long ATM Call + Long ATM Put at the **same strike**, same expiry. Both are bought (net debit).

**A11.** Upper Breakeven = 24,700 + 220 = **24,920**. Lower Breakeven = 24,700 – 220 = **24,480**. NIFTY must move more than 220 pts in either direction to profit.

**A12.** **Zero (0.00).** The call delta (+0.50) and put delta (–0.50) cancel each other exactly. The straddle is direction-neutral at initiation.

**A13.** Because low IV means options are **cheap** (lower breakevens, less cost). More importantly, low IV is likely to **rise** before an event, creating vega profit. If you buy at IV 12% and IV rises to 18%, the vega gain alone can make the straddle profitable even before the move happens. Buying at high IV means expensive options + IV crush risk.

**A14.** **Straddle:** Same strike (ATM), more expensive, narrower dead zone, higher gamma/vega. **Strangle:** Different strikes (OTM call + OTM put), cheaper, wider dead zone, lower gamma/vega. Straddle needs a smaller move to profit but costs more. Strangle needs a larger move but is more affordable.

**A15.** Upper BE = 24,900 + 70 = **24,970**. Lower BE = 24,500 – 70 = **24,430**. Dead zone: 24,430 to 24,970 (540 pts).

**A16.** **Bull Put Spread + Bear Call Spread.** The Bull Put Spread is on the downside (sell put + buy put). The Bear Call Spread is on the upside (sell call + buy call). Together they form a 4-leg range-bound strategy.

**A17.** Put side credit: ₹45 – ₹15 = ₹30. Call side credit: ₹40 – ₹12 = ₹28. Total Credit = ₹30 + ₹28 = **₹58 per share** = ₹58 × 75 = **₹4,350 per lot**.

**A18.** **Very positive (+₹6 to +₹8 per day).** You're earning theta on TWO short legs (short put + short call). The two long legs (wings) cost some theta, but the net is strongly positive. Time decay is the Iron Condor's primary profit engine.

**A19.** **Negative (–0.001 to –0.002).** This means large moves HURT you. As NIFTY moves toward either short strike, the delta of that short leg accelerates against you (negative gamma). This is why Iron Condors must be closed if NIFTY breaks a short strike — the losses accelerate.

**A20.** **(1) Theta differential:** Near-term option decays faster than far-term, so you earn the difference. **(2) IV expansion:** The far-term option has higher vega, so if IV rises, the long leg gains more than the short leg loses. Calendar spreads profit from time + rising IV.

**A21.** **SELL the near-term** (current week / closer expiry). **BUY the far-term** (next month / further expiry). Same strike. The near-term decays faster (your income), the far-term decays slower (your asset).

**A22.** **Iron Condor:** When NIFTY is range-bound, IV is moderate-high, no events, 10+ days to expiry. You profit from time decay in a sideways market. **Bull Call Spread:** When NIFTY is trending up, IV is low-normal, you expect a 100–300 pt directional move. You profit from the move. Different market conditions → different strategies.

**A23.** **Credit strategies.** IVR at 80% means options are very expensive. Selling premium (Bull Put Spread, Bear Call Spread, or Iron Condor) lets you collect rich premium. IV is likely to fall (mean reversion), which helps credit positions. Debit strategies would be expensive to enter and would suffer from IV crush.

**A24.** **Long Straddle** (or Long Strangle if budget is tight). IVR at 15% means options are very cheap. Budget in 5 days means IV will spike from 11% to 18–20%+. Buy the straddle NOW at low IV, sell 1 day BEFORE the Budget to capture the IV expansion profit. Don't hold through the event (IV crush). The low IV makes the straddle affordable (breakevens ~250 pts instead of 400+ pts at high IV).

**A25.** Four exit rules for credit spreads:
1. **Take profit at 50% of max profit** (don't get greedy)
2. **Cut loss at 50% of max loss** (don't hope)
3. **Close by 3–4 days to expiry** (avoid gamma risk)
4. **Close immediately if NIFTY breaks your short strike** (thesis invalidated)

---

## SCORING

| Score | Rating | Action |
|-------|--------|--------|
| 23–25 | 🏆 Excellent | Proceed to Week 20 with full confidence |
| 20–22 | ✅ Good | Proceed to Week 20, re-read Chapters 4 and 7 |
| 17–19 | ⚠️ Needs Work | Re-study Chapters 2–4 (credit spreads) and 7 (Iron Condor) |
| Below 17 | 🔴 Re-study | Re-do the entire week. Advanced strategies are critical for Phase 4 |

---

## WEEK 19 KEY TAKEAWAYS

```
1. CREDIT vs DEBIT is the fundamental divide in options strategies.
   Debit = pay upfront, profit from moves, theta hurts.
   Credit = receive upfront, profit from time, theta helps.

2. BULL PUT SPREAD = Credit strategy for mildly bullish/neutral views.
   Sell put above support + buy put below for protection.
   Theta-positive, vega-negative. Win rate ~65%.

3. BEAR CALL SPREAD = Credit strategy for mildly bearish/neutral views.
   Sell call below resistance + buy call above for protection.
   Mirror of Bull Put Spread. Same Greeks, opposite direction.

4. CREDIT SPREAD MANAGEMENT is more important than entry.
   50/50 rule: Book at 50% max profit, cut at 50% max loss.
   Never hold to expiry. Never hold into events.
   Credit spreads are a VOLUME GAME (small profits, high frequency).

5. LONG STRADDLE = Buy ATM call + ATM put (same strike).
   Profits from BIG moves in EITHER direction.
   Buy when IV is LOW, sell BEFORE the event (IV expansion).
   Expensive but powerful for event plays.

6. LONG STRANGLE = Cheaper version of straddle using OTM options.
   Lower cost, wider dead zone, lower probability.
   Best when budget is tight and expected move is 300+ pts.

7. IRON CONDOR = Bull Put + Bear Call (4 legs).
   The ultimate range-bound income strategy.
   Very high theta, negative gamma, negative vega.
   Win rate ~70–75% but requires strict management.
   Best when IV is high, no events, NIFTY in a clear range.

8. CALENDAR SPREAD = Sell near-term + buy far-term (same strike).
   Profits from theta differential + IV expansion.
   Best when IV is low and NIFTY is near a major strike.
   Slow-moving strategy, not for quick profits.

9. STRATEGY SELECTION depends on 4 factors:
   Direction (trend/range/event) + IV (low/normal/high) +
   Capital (small/medium/large) + Time (days to expiry).
   Use the decision matrix (Chapter 9) before every trade.

10. You now know 10 strategies. Master 2–3 first:
    → Bull Call Spread (bullish)
    → Bear Put Spread (bearish)
    → Iron Condor (range-bound)
    Add others gradually as you gain experience.
```

---

## 📚 FREE RESOURCES FOR WEEK 19

| Resource | Link | What to Study |
|----------|------|---------------|
| Zerodha Varsity | `zerodha.com/varsity/module/option-theory-in-practice/` | Chapters 23–28: Advanced strategies |
| Sensibull | `sensibull.com/virtual-trade` | Build & paper trade all 10 strategies |
| Opstra | `opstra.definedge.com/strategy` | Payoff diagrams, Greeks for multi-leg |
| NSE | `nseindia.com/option-chain` | Live premiums for spread calculations |
| YouTube: Umar Punjabi | Search "Iron Condor NIFTY" | Live Iron Condor examples |
| YouTube: Power of Stocks | Search "Credit Spreads Hindi" | Bull Put / Bear Call management |

---

## 🔜 WEEK 20 PREVIEW: BUILDING YOUR TRADING SYSTEM

Next week we transition from **strategies** to **systems**. You'll learn to combine everything from Weeks 1–19 into a complete, rule-based trading system:

```
Week 20 Topics:
  1. Entry Rules: Technical + OI + IV confluence checklist
  2. Exit Rules: Profit target, stop loss, time exit, condition exit
  3. Position Sizing: Fixed fractional, Kelly Criterion, volatility-adjusted
  4. Trade Journaling: What to record, how to review, weekly analysis
  5. The Complete Pre-Trade Checklist (5-minute routine)
  6. Building Your Personal Trading Plan (template provided)
```

This is where all the theory becomes **actionable**. By the end of Week 20, you'll have a written trading plan that tells you exactly what to do in every market condition.

---

**When you're ready, say "proceed to week 20" and we'll build your complete trading system.** 🚀
