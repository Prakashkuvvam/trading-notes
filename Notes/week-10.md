# WEEK 10: TRADINGVIEW MASTERY

## Phase 2 — Technical Analysis (Final Week)

---

## INTRODUCTION

You now have a complete technical analysis framework:

- **Candlesticks** (Week 5) → Reading price action
- **Support/Resistance** (Week 6) → Key levels
- **Market Structure** (Week 7) → Trend direction
- **Breakouts & Volume** (Week 8) → Momentum moves
- **MTF + Indicators** (Week 9) → Confluence trading

But all of this knowledge is useless if you can't **apply it efficiently on a live chart** while the market is moving at 300 points per minute.

This week is about **tools**. TradingView is the industry-standard charting platform used by millions of traders worldwide — and its free version is more than enough for everything you need in your first year.

By the end of this week, you will have:
1. A professional TradingView workspace configured for NIFTY options trading
2. Mastery of all drawing tools you'll need
3. Alerts set up so you never miss a key level
4. The ability to backtest strategies using Bar Replay
5. A saved chart template you can load every morning in 30 seconds

---

## CHAPTER 1: GETTING STARTED WITH TRADINGVIEW

### 1.1 Account Creation

1. Go to **tradingview.com**
2. Click **"Get Started"** (top right)
3. Sign up with email or Google account
4. Choose the **Basic (Free)** plan

**Free plan limitations (and why they don't matter yet):**

| Limitation | Free Plan | Does It Affect You? |
|-----------|-----------|-------------------|
| Charts per tab | 1 chart | No — you'll use tabs for MTF |
| Indicators per chart | 3 | No — you only need VWAP + EMA + RSI = 3 ✅ |
| Alerts | 1 active alert | Yes — upgrade to Pro (~₹1,000/month) when you go live |
| Bar Replay | Daily timeframe only on free | Partially — use 15-min replay on paid, or use free alternatives |
| Ad popups | Occasional | Minor annoyance, doesn't affect trading |
| Layouts saved | 1 | No — one well-built layout is all you need |

**Recommendation:** Start with free. Upgrade to **Pro** (~₹1,000/month) only when you start live trading (Phase 6, Week 25). The free plan is sufficient for 5 months of learning.

### 1.2 Finding NIFTY on TradingView

This confuses many Indian beginners because NIFTY has multiple symbols:

| Symbol | What It Is | Use For |
|--------|-----------|---------|
| **NSE:NIFTY** | NIFTY 50 Index (spot) | ✅ Primary chart for analysis |
| **NSE:NIFTY1!** | NIFTY Futures (continuous) | Checking futures premium/discount |
| **NSE:NIFTY24DEC24500CE** | Specific option contract | Checking option premium charts |

**How to search:**
1. Click the symbol name at the top-left of the chart (or press `Ctrl + K`)
2. Type `NIFTY`
3. Select **"NIFTY 50"** under the **NSE** exchange (look for the "NSE" tag)
4. The symbol should read `NSE:NIFTY`

**Important:** Always analyze the **spot index** (`NSE:NIFTY`), not the futures or options chart. Your S/R levels, trendlines, and indicators should be drawn on the spot chart. You then use the option chain (NSE website or Sensibull) to choose the strike.

### 1.3 Chart Type Settings

**Step-by-step:**

1. **Chart type:** Click the candlestick icon in the top toolbar → Select **"Candles"** (not Heikin Ashi, not Line)
2. **Timeframe:** Click the timeframe dropdown (top-left, shows "D" or "15" etc.) → Select your desired timeframe
   - For daily analysis: **D** (1 Day)
   - For intraday structure: **15** (15 Minutes)
   - For entry: **5** (5 Minutes)
3. **Background:** Right-click chart → Settings → Appearance → Background → Choose **Solid** → Dark gray (#1a1a2e) or black
4. **Grid lines:** Same menu → Grid Lines → Set opacity to 5–10% (barely visible)
5. **Candle colors:** Settings → Symbol → 
   - Bullish (Body): Green (#26a69a)
   - Bearish (Body): Red (#ef5350)
   - Wicks: Match body color
   - Borders: Match body color

```
    RECOMMENDED COLOR SCHEME
    
    Background:    Dark gray (#1a1a2e)
    Grid:          Very faint gray (5% opacity)
    Bullish:       Green (#26a69a)
    Bearish:       Red (#ef5350)
    VWAP line:     Yellow (#ffeb3b)
    20 EMA line:   Cyan (#00bcd4)
    RSI line:      Purple (#ab47bc)
    S/R lines:     White (#ffffff)
    Trendlines:    Orange (#ff9800)
```

---

## CHAPTER 2: ESSENTIAL DRAWING TOOLS

TradingView has 90+ drawing tools. You need exactly **6**. Everything else is decoration.

### 2.1 The Toolbar Location

All drawing tools are in the **left sidebar**. Click the icon to expand each group.

```
    LEFT SIDEBAR (Top to Bottom)
    
    ┌──┐
    │↖ │ ← Cursor (Esc key to deselect)
    ├──┤
    │╲ │ ← Trend Line tools (group)
    │╱ │
    ├──┤
    │──│ ← Horizontal Line tools (group)
    ├──┤
    │╱╲│ ← Fibonacci tools (group)
    │╲╱│
    ├──┤
    │□ │ ← Rectangle / Shape tools (group)
    ├──┤
    │T │ ← Text tools
    ├──┤
    │📏│ ← Measurement tools
    └──┘
```

### 2.2 Tool 1: Horizontal Line (Most Used)

**Purpose:** Mark support and resistance levels.

**How to use:**
1. Click the **Horizontal Line** icon in the left sidebar (or press `Alt + H`)
2. Click on the chart at the price level you want to mark
3. The line extends infinitely to the right

**Settings (double-click the line):**
- Color: White or bright color
- Style: Solid line
- Width: 2px
- Extend lines: Right only (cleaner chart)
- Show price label: ✅ ON (so you can see the exact price)

**Pro tip:** Use different colors for different types of levels:

| Level Type | Color | Example |
|-----------|-------|---------|
| PDH (Previous Day High) | Green | 24,520 |
| PDL (Previous Day Low) | Red | 24,280 |
| PDC (Previous Day Close) | Yellow | 24,400 |
| Major S/R (weekly/monthly) | White (thick) | 24,000, 25,000 |
| Intraday S/R | Cyan (thin) | 24,350, 24,450 |

### 2.3 Tool 2: Horizontal Ray

**Purpose:** Mark levels that start from a specific point (e.g., today's opening price).

**Difference from Horizontal Line:** A ray starts at a point and extends only to the right. A line extends both left and right.

**How to use:**
1. Click the **Horizontal Ray** icon (same group as Horizontal Line)
2. Click on the chart where you want the ray to start
3. It extends to the right only

**Use case:** Mark today's opening price at 9:15 AM. This acts as an intraday pivot.

### 2.4 Tool 3: Trend Line

**Purpose:** Draw diagonal support/resistance (uptrend lines, downtrend lines, channels).

**How to use:**
1. Click the **Trend Line** icon (or press `Alt + T`)
2. Click on the first swing low (for uptrend line) or swing high (for downtrend line)
3. Click on the second swing low/high
4. The line extends to the right

**Settings:**
- Color: Orange (#ff9800)
- Style: Solid
- Width: 2px
- Extend right: ✅ ON

**Rules from Week 6:**
- Minimum 2 touch points to draw
- 3 touch points to confirm
- Don't force trendlines through candles — connect the wicks

### 2.5 Tool 4: Rectangle (Zone Drawing)

**Purpose:** Mark support/resistance **zones** (not lines). As you learned in Week 6, S/R is a zone, not a precise price.

**How to use:**
1. Click the **Rectangle** icon (or press `Alt + R`)
2. Click and drag to draw a box around the S/R zone
3. The rectangle covers the zone area

**Settings:**
- Fill color: Blue or green
- Opacity: 10–15% (transparent enough to see candles through it)
- Border: Same color, 1px

```
    RECTANGLE ZONE EXAMPLE
    
    24,520 ┤ ┌───────────────────────────┐
           │ │  RESISTANCE ZONE          │ ← Rectangle (10% opacity)
    24,500 ┤ │  (24,500 - 24,520)        │
           │ └───────────────────────────┘
           │
    24,320 ┤ ┌───────────────────────────┐
           │ │  SUPPORT ZONE             │ ← Rectangle (10% opacity)
    24,300 ┤ │  (24,300 - 24,320)        │
           │ └───────────────────────────┘
```

### 2.6 Tool 5: Fibonacci Retracement

**Purpose:** Measure pullback levels during a trend. Key levels: 38.2%, 50%, 61.8%.

**How to use:**
1. Click the **Fibonacci Retracement** icon (or press `Alt + F`)
2. For an uptrend pullback: Click the **swing low** first, then the **swing high**
3. For a downtrend pullback: Click the **swing high** first, then the **swing low**
4. Fibonacci levels appear automatically

**Key levels to watch:**

| Fib Level | Significance |
|-----------|-------------|
| **23.6%** | Shallow pullback (strong trend) |
| **38.2%** | Normal pullback (healthy trend) |
| **50.0%** | Deep pullback (trend weakening but still valid) |
| **61.8%** | Golden ratio — last defense before trend breaks |
| **78.6%** | Very deep — if broken, trend is likely over |

```
    FIBONACCI ON AN UPTREND PULLBACK
    
    24,600 ┤ ── 0% (Swing High) ────────────
           │
    24,530 ┤ ── 23.6% ──────────────────────
           │
    24,480 ┤ ── 38.2% ── ← Price bouncing here ✅
           │
    24,450 ┤ ── 50.0% ── ← Deeper pullback zone
           │
    24,420 ┤ ── 61.8% ── ← Golden ratio (last defense)
           │
    24,300 ┤ ── 100% (Swing Low) ──────────
    
    If price holds above 38.2% or 50%, the uptrend is intact.
    Buy calls at these Fibonacci levels with stop below 61.8%.
```

**Settings:**
- Show only: 0, 0.236, 0.382, 0.5, 0.618, 1 (uncheck the rest)
- Colors: Use subtle colors, 10–15% opacity for the background fills
- Extend lines right: ✅ ON

### 2.7 Tool 6: Long/Short Position Tool

**Purpose:** Visualize your trade's entry, stop-loss, and target on the chart. Calculates risk-reward automatically.

**How to use:**
1. Click the **Long Position** or **Short Position** icon (in the left sidebar, under the prediction tools)
2. Click on the chart at your entry price
3. Drag the red zone to your stop-loss
4. Drag the green zone to your target

**What it shows:**
- Entry price
- Stop-loss price
- Target price
- Risk amount (in points and %)
- Reward amount (in points and %)
- **Risk-Reward ratio** (e.g., 1:2.5)

```
    LONG POSITION TOOL ON CHART
    
    24,520 ┤ ┌─────────────────────┐
           │ │   TARGET: 24,520    │ ← Green zone (profit)
    24,480 ┤ │   +80 pts (+0.33%)  │
           │ ├──── ENTRY: 24,450 ──┤ ← Blue line (entry)
    24,440 ┤ │   SL: 24,430        │ ← Red zone (risk)
           │ │   -20 pts (-0.08%)  │
    24,420 ┤ └─────────────────────┘
           │
           │   Risk-Reward: 1:4.0 ✅
```

This tool is invaluable for planning trades BEFORE you enter. If the visual risk-reward doesn't look good on the chart, the trade isn't worth taking.

---

## CHAPTER 3: ADDING INDICATORS (VWAP, 20 EMA, RSI)

### 3.1 How to Add Any Indicator

1. Click **"Indicators"** at the top of the chart (or press `/`)
2. A search box appears
3. Type the indicator name
4. Click on the indicator to add it to your chart
5. It appears on the chart immediately

### 3.2 Adding VWAP

1. Press `/` → Type `VWAP`
2. Select **"VWAP"** (built-in, by TradingView)
3. It appears as a line on your chart

**Settings (double-click the VWAP line or click the gear icon):**
- **Inputs tab:**
  - Source: `hlc3` (default, correct)
  - Anchor Period: `Session` (resets daily — this is what you want for intraday)
- **Style tab:**
  - VWAP line color: Yellow (#ffeb3b)
  - Width: 2px
  - Upper/Lower bands: ❌ OFF (uncheck — you don't need bands for now)

**Important:** VWAP only works on **intraday timeframes** (1-min, 5-min, 15-min, 1-hour). It will NOT appear on the daily chart. This is normal.

### 3.3 Adding 20 EMA

1. Press `/` → Type `EMA`
2. Select **"Moving Average Exponential"** (built-in)
3. It appears as a line on your chart
4. **By default, it may show as SMA 9.** You need to change it.

**Settings:**
- **Inputs tab:**
  - Length: `20` (change from default 9)
  - Source: `close` (default, correct)
- **Style tab:**
  - Line color: Cyan (#00bcd4)
  - Width: 2px

**Adding to multiple timeframes:**
- On your 15-min chart: Add 20 EMA (this is your primary trend filter)
- On your 5-min chart: Add 20 EMA (for entry timing)
- On your daily chart: Add 20 EMA (for overall trend direction)

### 3.4 Adding RSI

1. Press `/` → Type `RSI`
2. Select **"Relative Strength Index"** (built-in)
3. It appears as a **separate panel below** your main chart

**Settings:**
- **Inputs tab:**
  - RSI Length: `14` (default, don't change)
  - Source: `close` (default)
- **Style tab:**
  - RSI line color: Purple (#ab47bc)
  - Width: 2px
  - Upper band: `70` (color: red, dashed)
  - Lower band: `30` (color: green, dashed)
  - Middle band: `50` (color: gray, dotted) ← **Add this manually** if not shown

**How to add the 50 midline:**
1. In RSI settings → Style tab
2. Check "Middle band"
3. Set value to 50
4. Color: Gray, style: Dotted

```
    RSI PANEL (Below Main Chart)
    
    100 ┤
     80 ┤
     70 ┤ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ← Overbought (red dashed)
     60 ┤        ╱╲
     50 ┤ ─ ─ ─╱──╲─ ─ ─ ─ ─ ← Midline (gray dotted)
     40 ┤     ╱    ╲╱╲
     30 ┤ ─ ─ ─ ─ ─ ─╲─ ─ ─ ─ ← Oversold (green dashed)
     20 ┤              ╲╱
      0 ┤
```

### 3.5 Indicator Count on Free Plan

The free plan allows **3 indicators per chart**. Your setup uses exactly 3:
1. VWAP ✅
2. 20 EMA ✅
3. RSI ✅

This is why you don't need a paid plan for indicators. If you want to add a 4th indicator (like OBV from Week 8), you'll need to remove one temporarily or upgrade.

---

## CHAPTER 4: MULTIPLE CHART LAYOUTS FOR MTF ANALYSIS

### 4.1 The Tab Method (Free Plan)

Since the free plan gives you only 1 chart per tab, use **browser tabs** for MTF:

**Setup:**
1. Open TradingView in your browser
2. Open **Tab 1:** NSE:NIFTY on **Daily** timeframe (with 20 EMA)
3. Open **Tab 2:** NSE:NIFTY on **15-min** timeframe (with VWAP + 20 EMA + RSI)
4. Open **Tab 3:** NSE:NIFTY on **5-min** timeframe (with VWAP + 20 EMA)

**Workflow:**
- Pre-market (9:00 AM): Check Tab 1 (Daily) for trend bias
- Market open (9:15–9:45 AM): Watch Tab 2 (15-min) for structure
- Entry time (9:45 AM+): Execute on Tab 3 (5-min)

### 4.2 The Split-Screen Method (Pro Plan, 2 Charts)

If you upgrade to Pro:
1. Right-click the chart → **"Add Symbol"** or click the split layout icon (top-right)
2. Choose **2 charts side by side**
3. Left chart: 15-min (structure + indicators)
4. Right chart: 5-min (entry)
5. Keep daily in a separate browser tab

### 4.3 The 4-Chart Layout (Pro+ Plan, Future)

For advanced use (not needed now):
```
    ┌──────────────────┬──────────────────┐
    │                  │                  │
    │   DAILY          │   1-HOUR         │
    │   (Trend)        │   (Swing)        │
    │                  │                  │
    ├──────────────────┼──────────────────┤
    │                  │                  │
    │   15-MIN         │   5-MIN          │
    │   (Structure)    │   (Entry)        │
    │                  │                  │
    └──────────────────┴──────────────────┘
```

**For now, the 3-tab method is perfect and costs nothing.**

---

## CHAPTER 5: SETTING UP ALERTS

### 5.1 Why Alerts Are Essential

You cannot stare at the screen for 6.5 hours straight. Alerts notify you when price reaches a key level so you can:
- Prepare for a breakout
- Enter a trade at your planned level
- Move your stop-loss
- Book profits

### 5.2 How to Create an Alert

**Method 1: Right-click on chart**
1. Right-click on the price level where you want the alert
2. Select **"Add Alert on [NSE:NIFTY]"**
3. Configure the alert (see settings below)
4. Click **"Create"**

**Method 2: Alert icon**
1. Click the **alarm clock icon** in the top toolbar (or press `Alt + A`)
2. Configure and create

### 5.3 Alert Settings

| Setting | Recommended Value |
|---------|------------------|
| **Condition** | NSE:NIFTY |
| **Trigger** | Crossing / Crossing Up / Crossing Down |
| **Value** | Your key price level (e.g., 24,500) |
| **Once Per Bar** | ✅ (prevents multiple notifications) |
| **Expiration** | End of day (for intraday) or specific date |
| **Notification** | App notification + Email + Sound |

### 5.4 The 5 Alerts You Should Set Every Morning

| # | Alert | Type | Purpose |
|---|-------|------|---------|
| 1 | **PDH** (Previous Day High) | Crossing Up | Breakout above PDH → call opportunity |
| 2 | **PDL** (Previous Day Low) | Crossing Down | Breakdown below PDL → put opportunity |
| 3 | **Key Resistance** | Crossing Up | Major level breakout |
| 4 | **Key Support** | Crossing Down | Major level breakdown |
| 5 | **VWAP Cross** | Crossing (VWAP line) | Intraday trend change |

**Example:**
```
    MORNING ALERT SETUP (9:05 AM)
    
    Alert 1: NIFTY Crossing Up 24,520 (PDH)
    Alert 2: NIFTY Crossing Down 24,280 (PDL)
    Alert 3: NIFTY Crossing Up 24,600 (Weekly Resistance)
    Alert 4: NIFTY Crossing Down 24,200 (Weekly Support)
    Alert 5: NIFTY Crossing VWAP (Trend Change)
    
    Total: 5 alerts (Free plan allows 1, so prioritize PDH or PDL.
    Upgrade to Pro for 20 alerts when you start live trading.)
```

### 5.5 Alert Notifications

- **Desktop:** TradingView sends a browser notification (keep the tab open)
- **Mobile:** Download the TradingView app (iOS/Android) → Enable push notifications
- **Sound:** A loud beep plays when the alert triggers (useful if you're at your desk)

**Pro tip:** Set the alert sound to something distinctive. You should recognize it instantly without looking at the screen.

---

## CHAPTER 6: BAR REPLAY — BACKTESTING WITHOUT CODING

### 6.1 What Is Bar Replay?

Bar Replay lets you **rewind the chart** to a past date and then play it forward candle by candle, as if you were watching the market live. This is the single most powerful practice tool for a beginner.

**Why it matters:**
- You can practice your strategy on historical data without risking money
- You experience the same emotions (uncertainty, FOMO, fear) as live trading
- You can test 50 trades in one evening instead of waiting 50 trading days
- You learn to read price action in real-time without the pressure of real money

### 6.2 How to Use Bar Replay

**Step-by-step:**

1. Open NSE:NIFTY on the **15-minute** chart
2. Click the **"Replay"** button in the top toolbar (looks like a rewind icon ⏪)
3. A red vertical line appears on the chart
4. **Drag the red line** to the date/time where you want to start (e.g., 2 weeks ago, Monday 9:15 AM)
5. The chart to the right of the red line disappears (hidden)
6. Click the **Play** button (▶️) to start replaying
7. Adjust the **speed** using the slider (1–10, start at 3)
8. Or click **Forward** (⏭️) to advance one candle at a time

```
    BAR REPLAY INTERFACE
    
    ┌─────────────────────────────────────────────────┐
    │  ⏪  ⏮  ▶️  ⏭  ⏩   Speed: ████░░░░░░ 3x     │ ← Replay controls
    ├─────────────────────────────────────────────────┤
    │                                                 │
    │   Visible candles    │  Hidden (future)          │
    │   (past data)        │                           │
    │   ╱╲    ╱╲    ╱╲    │                           │
    │  ╱  ╲╱╲  ╲╱╲  ╲    │  ← Red line here          │
    │ ╱              ╲    │                           │
    │                     │                           │
    │                     │                           │
    └─────────────────────────────────────────────────┘
    
    You see only the left side. As you press Play, 
    candles appear one by one from the red line.
```

### 6.3 Bar Replay Practice Drill (Do This Every Weekend)

**The 20-Trade Weekend Drill:**

1. **Saturday evening:** Open NIFTY 15-min chart
2. **Replay to Monday** of the previous week, 9:15 AM
3. **Play forward** candle by candle
4. At each point where your strategy gives a signal (MTF alignment + breakout + volume), **pause the replay**
5. **Write down on paper:**
   - Date and time
   - Signal type (breakout, pullback, etc.)
   - Direction (call or put)
   - Entry price (premium estimate from option chain)
   - Stop-loss
   - Target
6. **Resume replay** and see what happened
7. **Record the result:** Win or loss? How many points?
8. Repeat for all 5 days of the week
9. By Sunday, you should have 15–20 practice trades recorded

**Track your results:**

| Date | Time | Signal | Direction | Entry | SL | Target | Result | P&L |
|------|------|--------|-----------|-------|-----|--------|--------|-----|
| Mon | 10:30 | BOS + Vol | Call | ₹85 | ₹60 | ₹130 | Win | +₹40 |
| Mon | 14:00 | VWAP bounce | Call | ₹70 | ₹50 | ₹100 | Loss | -₹20 |
| Tue | 9:45 | Breakdown | Put | ₹90 | ₹65 | ₹140 | Win | +₹45 |
| ... | ... | ... | ... | ... | ... | ... | ... | ... |

**After 20 trades, calculate:**
- Win rate: ___/20 = ___%
- Average win: ₹___
- Average loss: ₹___
- Expectancy: (Win% × Avg Win) – (Loss% × Avg Loss) = ₹___

If expectancy is positive, your strategy works. If negative, refine it.

### 6.4 Bar Replay Limitations on Free Plan

- **Free plan:** Bar Replay works on **Daily** timeframe only
- **Pro plan:** Works on all timeframes including 15-min and 5-min
- **Workaround for free users:** Use the daily chart for replay practice (still valuable for swing-level analysis), OR use **Neostox** (neostox.com) which offers free paper trading with historical replay for Indian markets

---

## CHAPTER 7: KEYBOARD SHORTCUTS (Speed Is Everything)

During live trading, you don't have time to click through menus. Memorize these shortcuts:

### 7.1 Essential Shortcuts

| Action | Shortcut | When to Use |
|--------|----------|-------------|
| **Search symbol** | `Ctrl + K` | Switch between NIFTY, BANK NIFTY |
| **Change timeframe** | Type number + Enter (e.g., `15` + Enter) | Switch to 15-min |
| **Add indicator** | `/` | Quick add VWAP, EMA, RSI |
| **Horizontal line** | `Alt + H` | Mark S/R levels |
| **Trend line** | `Alt + T` | Draw trendlines |
| **Rectangle** | `Alt + R` | Draw S/R zones |
| **Fibonacci** | `Alt + F` | Measure pullbacks |
| **Crosshair** | `Alt + C` | Measure price/time between points |
| **Delete drawing** | Select + `Delete` | Remove unwanted lines |
| **Undo** | `Ctrl + Z` | Undo last action |
| **Redo** | `Ctrl + Y` | Redo |
| **Zoom in** | `Ctrl + Scroll Up` or `+` | See detail |
| **Zoom out** | `Ctrl + Scroll Down` or `-` | See big picture |
| **Reset chart** | `Alt + R` (double-tap) or right-click → Reset | Reset zoom/scroll |
| **Toggle magnet mode** | `Alt + M` | Snap drawings to candle OHLC |
| **Alert** | `Alt + A` | Quick alert creation |
| **Fullscreen** | `Alt + F` (or F11 in browser) | Remove distractions |
| **Screenshot** | `Alt + S` | Capture chart for journal |
| **Cursor mode** | `Esc` | Deselect all tools |

### 7.2 Timeframe Shortcuts

| Timeframe | Shortcut |
|-----------|----------|
| 1 minute | `1` + Enter |
| 5 minutes | `5` + Enter |
| 15 minutes | `15` + Enter |
| 1 hour | `60` + Enter |
| Daily | `D` + Enter |
| Weekly | `W` + Enter |

---

## CHAPTER 8: BUILDING YOUR COMPLETE CHART TEMPLATE

### 8.1 The Final Setup (Step-by-Step)

Follow these steps exactly. Once done, save the layout. You'll load this every morning.

**Step 1: Open NSE:NIFTY**
- Press `Ctrl + K` → Type `NIFTY` → Select `NSE:NIFTY`

**Step 2: Set timeframe to 15-min**
- Type `15` + Enter

**Step 3: Add indicators**
- Press `/` → Add `VWAP` → Settings: Yellow, 2px, Session anchor, no bands
- Press `/` → Add `Moving Average Exponential` → Settings: Length 20, Cyan, 2px
- Press `/` → Add `Relative Strength Index` → Settings: Length 14, Purple, add 50 midline

**Step 4: Clean the chart**
- Right-click → Settings → Appearance:
  - Background: Dark gray (#1a1a2e)
  - Grid: 5% opacity
  - Crosshair: Dotted, gray
- Remove any default indicators you don't need (MA 9, etc.) by clicking the `X` next to their name in the top-left

**Step 5: Set candle colors**
- Right-click → Settings → Symbol:
  - Bullish body: #26a69a (green)
  - Bearish body: #ef5350 (red)
  - Wicks: Match body

**Step 6: Add volume**
- Press `/` → Type `Volume` → Add it
- Settings: Colors match candle colors, opacity 50%
- Volume appears at the bottom of the main chart

**Wait — that's a 4th indicator!** On the free plan, you can only have 3. Solution: Remove RSI from the main chart and check RSI on a separate browser tab (5-min chart with only RSI). OR, since Volume is sometimes counted separately from the indicator limit on TradingView, try adding it. If it doesn't allow, prioritize: **VWAP + 20 EMA + RSI** (drop Volume, use the volume bars that are built into the candle chart by default — they're already there at the bottom without adding the indicator).

**Clarification:** TradingView shows volume bars by default at the bottom of the chart. You do NOT need to add the Volume indicator separately. The built-in volume bars are already there. So your 3 indicator slots are: VWAP + 20 EMA + RSI. ✅

**Step 7: Draw your levels**
- Press `Alt + H` → Mark PDH, PDL, PDC
- Press `Alt + R` → Draw S/R zones at key levels
- Use appropriate colors (see Section 2.2)

**Step 8: Save the layout**
- Click the layout name at the top-right (default: "Unnamed")
- Click **"Save"** or **"Save As"**
- Name it: **"NIFTY Intraday Setup"**

**Step 9: Auto-save**
- Click the layout name → Check **"Auto-save"**
- Now any changes you make (new lines, etc.) are saved automatically

### 8.2 What Your Final Chart Should Look Like

```
    ┌─────────────────────────────────────────────────────────┐
    │  NSE:NIFTY  15min  O:24,420 H:24,510 L:24,390 C:24,480 │ ← Symbol bar
    │  VWAP  24,455  EMA(20)  24,462                         │ ← Indicator values
    ├─────────────────────────────────────────────────────────┤
    │                                                         │
    │  24,520 ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─  │ ← PDH (green line)
    │                                                         │
    │  24,500 ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─  │ ← Resistance (white)
    │              ╱╲      ╱╲                                 │
    │  24,462 ═══╱══╲════╱══╲═══════ ← 20 EMA (cyan)        │
    │  24,455 ──╱────╲──╱────╲────── ← VWAP (yellow)        │
    │          ╱      ╲╱      ╲╱╲                            │
    │        ╱                ╲  ╲╱╲                         │
    │  24,400 ─ ─ ─ ─ ─ ─ ─ ─ ─╲──╲─ ─ ─ ← PDC (yellow)   │
    │                             ╲╱                         │
    │  24,300 ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─  │ ← PDL (red line)
    │                                                         │
    │  Volume: ██  ███  ██  ████  ██  █  ████  ██  ███       │ ← Built-in bars
    ├─────────────────────────────────────────────────────────┤
    │  RSI(14)  58.3                                         │
    │  70 ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─  │ ← Overbought
    │  60 ─ ─ ─ ─ ╱╲─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─  │
    │  50 ─ ─ ─ ╱──╲─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─  │ ← Midline
    │  40 ─ ─ ╱────╲╱╲─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─  │
    │  30 ─ ─ ─ ─ ─ ─╲─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─  │ ← Oversold
    └─────────────────────────────────────────────────────────┘
```

---

## CHAPTER 9: DAILY WORKFLOW — FROM PRE-MARKET TO POST-MARKET

### 9.1 The Complete Daily Routine

**8:50 AM — Pre-Market Preparation (20 minutes)**

1. Open TradingView → Load "NIFTY Intraday Setup" layout
2. Switch to **Daily** chart (`D` + Enter)
   - Check trend direction (HH-HL or LH-LL?)
   - Check price vs daily 20 EMA
   - Note yesterday's candle type
   - Mark daily S/R levels
3. Switch to **15-min** chart (`15` + Enter)
   - Mark PDH, PDL, PDC using `Alt + H`
   - Draw any visible S/R zones using `Alt + R`
   - Check VWAP, 20 EMA, RSI positions
4. Check **GIFT NIFTY** (search `GIFTNIFTY` on TradingView) for gap-up/gap-down indication
5. Set alerts at PDH and PDL (`Alt + A`)
6. Write your **daily bias** in your journal: BULLISH / BEARISH / NEUTRAL

**9:00–9:07 AM — Pre-Open Session**

7. Watch NIFTY pre-open on NSE website (nseindia.com)
8. Note the pre-open settlement price
9. If gap-up > 100 points: Be cautious (gap may fill)
10. If gap-down > 100 points: Be cautious (gap may fill)
11. If flat open: Normal trading day expected

**9:15–9:30 AM — Opening Volatility (DO NOT TRADE)**

12. Watch the first 15-min candle form
13. Note the opening range (high and low of first candle)
14. Let VWAP stabilize
15. Observe volume pattern

**9:30–10:00 AM — Structure Identification**

16. Switch to 15-min chart
17. Identify intraday structure (HH-HL or LH-LL?)
18. Check indicator alignment (how many of 3 agree?)
19. Identify the first key level to watch (PDH? PDL? Opening range?)

**10:00 AM–2:00 PM — Prime Trading Window**

20. Wait for setups at key levels
21. When a setup forms:
    - Switch to 5-min for entry trigger
    - Confirm candlestick pattern + volume
    - Execute trade (paper trade for now)
    - Set stop-loss immediately
    - Set target
22. Manage open trades:
    - Trail stop-loss when in profit
    - Book partial profits at 1:1 R:R
    - Exit fully at target or SL

**2:00–3:00 PM — Late Session (Caution)**

23. Reduce position size (volatility can spike)
24. Avoid new entries after 2:30 PM
25. Close all intraday positions by 3:00 PM (if paper trading with MIS)

**3:00–3:30 PM — Expiry Settlement (Thursday Only)**

26. On expiry day, note the settlement price (VWAP of 3:00–3:30)
27. Check which options expired ITM vs OTM

**3:30–4:00 PM — Post-Market Review (CRITICAL)**

28. Open your trading journal
29. Record all trades taken:
    - Entry, exit, P&L
    - Screenshot of the chart (`Alt + S`)
    - What went right?
    - What went wrong?
    - Did you follow your rules?
30. Calculate daily P&L
31. Note lessons learned

---

## CHAPTER 10: USEFUL TRADINGVIEW FEATURES YOU SHOULD KNOW

### 10.1 Watchlist

**Purpose:** Monitor multiple symbols at a glance.

**Setup:**
1. Click the **Watchlist** icon on the right sidebar (or press `Alt + W`)
2. Click **"+"** to add symbols
3. Add: `NSE:NIFTY`, `NSE:BANKNIFTY`, `NSE:NIFTY1!` (futures), `TVC:GOLD`, `FOREXCOM:USDINR`

**Why:** You can quickly see if BANK NIFTY is confirming NIFTY's move, if gold is spiking (risk-off signal), or if the rupee is weakening (FII selling signal).

### 10.2 Crosshair and Measurement

**Crosshair** (default when you move your mouse):
- Shows the exact price and time at any point on the chart
- Bottom axis: Time. Right axis: Price.

**Measurement Tool** (`Alt + C` or click the ruler icon):
1. Click on a starting candle
2. Drag to an ending candle
3. Shows: Price difference (points and %), Time difference, Number of bars

**Use case:** Measure the height of a range to calculate the breakout target.

### 10.3 Magnet Mode

**Purpose:** Snaps your drawing tools to the exact OHLC of candles.

**How to enable:** Click the **magnet icon** in the left toolbar (or `Alt + M`)

**Why use it:** When drawing a trendline, magnet mode ensures the line connects to the exact wick tip, not a random pixel. This makes your drawings more accurate.

### 10.4 Screenshot and Sharing

**Screenshot** (`Alt + S`):
- Captures the visible chart area
- Saves as PNG
- Use for your trading journal

**Share** (top-right → Share icon):
- Generates a shareable link to your chart
- Useful for discussing setups with mentors or trading communities

### 10.5 Pine Script (Advanced — For Future Reference)

Pine Script is TradingView's programming language for creating custom indicators and strategies. You don't need this now, but in Phase 4 (Weeks 19–22), you may want to:
- Create a custom indicator that combines VWAP + EMA + RSI into one signal
- Build an automated backtest of your strategy
- Set up custom alerts based on complex conditions

**For now:** Ignore Pine Script. The built-in tools are more than enough.

---

## CHAPTER 11: COMMON MISTAKES WITH TRADINGVIEW

### Mistake 1: Chart Clutter
**Problem:** Adding 10 indicators, 20 trendlines, 5 Fibonacci levels, and Bollinger Bands. The chart looks like a spider web. You can't even see the candles.
**Fix:** Maximum 3 indicators (VWAP + 20 EMA + RSI). Maximum 5–6 drawing lines at a time. Delete old drawings that are no longer relevant.

### Mistake 2: Wrong Symbol
**Problem:** You've been analyzing `NSE:NIFTY1!` (futures) instead of `NSE:NIFTY` (spot). The prices are slightly different (futures trade at a premium/discount to spot), so your S/R levels are off by 20–50 points.
**Fix:** Always use `NSE:NIFTY` for analysis. Double-check the symbol name at the top-left of the chart.

### Mistake 3: Not Saving the Layout
**Problem:** You spend 30 minutes setting up your chart perfectly. Next morning, you open TradingView and everything is reset to default.
**Fix:** Save your layout (Section 8.1, Step 8) and enable auto-save. Bookmark the specific URL of your saved layout.

### Mistake 4: Using the Wrong Timeframe for VWAP
**Problem:** You add VWAP to the daily chart and wonder why it's not showing. VWAP is an intraday indicator — it only works on timeframes below 1 day.
**Fix:** Use VWAP only on 1-min, 5-min, 15-min, or 1-hour charts. For daily analysis, use the 20 EMA instead.

### Mistake 5: Drawing Too Many Trendlines
**Problem:** You draw 8 trendlines on the chart, each connecting different swing points. They contradict each other. You don't know which one to trust.
**Fix:** Maximum 2 trendlines at a time — one for the primary trend and one for the current channel. Delete old ones when they break.

### Mistake 6: Ignoring the Volume Bars
**Problem:** You have the volume bars at the bottom of the chart but never look at them. You enter breakouts without checking volume confirmation.
**Fix:** Make it a habit to glance at volume bars before every trade. The bars are already there — use them.

---

## CHAPTER 12: PRACTICAL EXERCISES

### Exercise 1: Complete Setup (Do This Now)
Follow the step-by-step instructions in Chapter 8 to build your complete chart template. Save it as "NIFTY Intraday Setup." Take a screenshot and compare it with the example in Section 8.2.

### Exercise 2: Drawing Tool Speed Drill
Open NIFTY 15-min chart. Set a timer for 5 minutes. In that time:
- Draw 3 horizontal lines (PDH, PDL, PDC)
- Draw 1 rectangle zone
- Draw 1 trendline
- Draw 1 Fibonacci retracement on the last swing
- Add 1 alert at PDH
- Delete all drawings
- Repeat until you can do it in under 3 minutes

### Exercise 3: Bar Replay Weekend Session
This weekend, do the 20-Trade Weekend Drill (Section 6.3). Record all results in a spreadsheet. Calculate your win rate and expectancy.

### Exercise 4: MTF Tab Setup
Open 3 browser tabs with NIFTY on Daily, 15-min, and 5-min timeframes. Practice switching between them using `Ctrl + Tab`. Do the pre-market checklist (Week 9, Section 7.1) using these tabs.

### Exercise 5: Screenshot Journal
Take 5 screenshots of different market conditions using `Alt + S`:
1. A clean uptrend (price above VWAP + 20 EMA)
2. A clean downtrend (price below both)
3. A sideways range (price chopping around VWAP)
4. A breakout with volume confirmation
5. A false breakout (long wick, low volume)
Label each screenshot and save in a folder called "Chart Patterns."

---

## WEEK 10 SELF-TEST

**Q1.** What is the correct TradingView symbol for NIFTY 50 spot index?

**Q2.** How many indicators can you add on the TradingView free plan, and which three should you use?

**Q3.** What is the keyboard shortcut to add an indicator?

**Q4.** Why should you analyze the spot index chart and not the futures chart for S/R levels?

**Q5.** What is the purpose of the Rectangle drawing tool, and what opacity should you set it to?

**Q6.** Name the three Fibonacci levels most important for pullback trading.

**Q7.** What is the difference between a Horizontal Line and a Horizontal Ray?

**Q8.** How does Bar Replay help you improve as a trader?

**Q9.** What are the 5 alerts you should set every morning?

**Q10.** Why is VWAP not visible on the daily chart?

**Q11.** What is the purpose of the Long/Short Position tool?

**Q12.** Describe the complete daily workflow from 8:50 AM to 4:00 PM in 5 key steps.

---

## SELF-TEST ANSWERS

**A1.** `NSE:NIFTY`. Search for "NIFTY" and select the one tagged with "NSE" exchange. Do not use `NSE:NIFTY1!` (futures) or specific option symbols for chart analysis.

**A2.** 3 indicators on the free plan. The three you should use are: (1) VWAP, (2) Moving Average Exponential (20 EMA), (3) Relative Strength Index (RSI 14).

**A3.** Press `/` (forward slash). This opens the indicator search box.

**A4.** Because the spot index represents the actual NIFTY 50 value. Futures trade at a premium or discount to spot (due to cost of carry, dividends, etc.), so S/R levels drawn on futures will be offset by 20–50 points from the actual index levels. Option strikes are based on the spot index.

**A5.** The Rectangle tool marks support/resistance **zones** (areas, not lines). Set opacity to 10–15% so you can see candles through the zone. This reflects the reality that S/R is a zone, not a precise price.

**A6.** 38.2% (normal pullback), 50.0% (deep pullback), and 61.8% (golden ratio — last defense). The 23.6% level indicates a very shallow pullback in a strong trend, and 78.6% means the trend is likely breaking.

**A7.** A Horizontal Line extends infinitely in both directions (left and right). A Horizontal Ray starts at a specific point and extends only to the right. Use rays for levels that begin at a specific time (e.g., today's opening price).

**A8.** Bar Replay lets you rewind the chart to a past date and play it forward candle by candle. This allows you to practice your strategy on historical data without risking money, experience real-time decision-making emotions, test 50+ trades in one evening, and calculate your strategy's win rate and expectancy before going live.

**A9.** (1) PDH crossing up, (2) PDL crossing down, (3) Key resistance crossing up, (4) Key support crossing down, (5) VWAP crossing (trend change). On the free plan (1 alert), prioritize PDH or PDL.

**A10.** VWAP (Volume Weighted Average Price) is an intraday indicator that resets at the start of each trading session (9:15 AM). It calculates the average price weighted by volume for the current day only. On a daily chart, each candle represents an entire day, so there's no intraday volume distribution to calculate. Use the 20 EMA on the daily chart instead.

**A11.** The Long/Short Position tool visualizes your trade plan on the chart. You set the entry, stop-loss (red zone), and target (green zone), and it automatically calculates the risk-reward ratio. This helps you evaluate whether a trade is worth taking before you enter.

**A12.** Five key steps: (1) **8:50 AM** — Pre-market: Check daily chart for trend bias, mark S/R levels on 15-min, set alerts. (2) **9:15–9:30 AM** — Observe opening range, don't trade. (3) **9:30–10:00 AM** — Identify intraday structure and indicator alignment. (4) **10:00 AM–2:00 PM** — Prime trading window: wait for setups, execute on 5-min confirmation, manage trades. (5) **3:30–4:00 PM** — Post-market review: journal all trades, record P&L, note lessons.

---

## WEEK 10 SUMMARY CHEAT SHEET

| Concept | Key Takeaway |
|---------|-------------|
| **Symbol** | Always use `NSE:NIFTY` (spot) for analysis |
| **Chart type** | Candles, dark background, green/red colors |
| **3 Indicators** | VWAP (yellow) + 20 EMA (cyan) + RSI 14 (purple) |
| **Drawing tools** | H-Line, H-Ray, Trendline, Rectangle, Fibonacci, Position |
| **Rectangle** | S/R zones, 10–15% opacity |
| **Fibonacci** | Key levels: 38.2%, 50%, 61.8% |
| **Position tool** | Visualize entry/SL/target, auto R:R calculation |
| **MTF tabs** | Tab 1: Daily, Tab 2: 15-min, Tab 3: 5-min |
| **Alerts** | PDH, PDL, key S/R, VWAP cross |
| **Bar Replay** | Rewind + play forward for practice backtesting |
| **Shortcuts** | `/` indicators, `Alt+H` line, `Alt+T` trend, `Alt+S` screenshot |
| **Layout** | Save as "NIFTY Intraday Setup", enable auto-save |
| **Daily routine** | Pre-market → Open → Structure → Trade → Journal |
| **Chart hygiene** | Max 3 indicators, max 5–6 lines, delete old drawings |

---

## 🎉 PHASE 2 COMPLETE!

**Congratulations!** You have now completed the entire **Technical Analysis** phase. Let's review everything you've learned across Weeks 1–10:

### Phase 1 + Phase 2 — Complete Knowledge Map

```
    ┌─────────────────────────────────────────────────────────┐
    │              YOUR TRADING KNOWLEDGE (10 Weeks)          │
    ├─────────────────────────────────────────────────────────┤
    │                                                         │
    │  PHASE 1: FOUNDATIONS (Weeks 1-4)                       │
    │  ├── Stocks, NSE/BSE, NIFTY 50, BANK NIFTY             │
    │  ├── Futures vs Options basics                          │
    │  ├── Trading mechanics, charges, order types            │
    │  ├── Option chain, OI, PCR, max pain                    │
    │  ├── Premium = Intrinsic + Time Value                   │
    │  ├── Market structure, regulation, taxation             │
    │  └── Global factors, FII/DII, events                    │
    │                                                         │
    │  PHASE 2: TECHNICAL ANALYSIS (Weeks 5-10)               │
    │  ├── Candlestick patterns + context rules               │
    │  ├── Support/Resistance + trendlines + channels          │
    │  ├── Market structure (HH-HL, BOS, CHoCH)              │
    │  ├── Breakouts/Breakdowns + Volume analysis             │
    │  ├── MTF Analysis + VWAP + 20 EMA + RSI                │
    │  └── TradingView mastery + daily workflow               │
    │                                                         │
    │  YOU CAN NOW:                                           │
    │  ✅ Read any NIFTY chart on any timeframe               │
    │  ✅ Identify trend direction using MTF analysis          │
    │  ✅ Mark key S/R levels and zones                       │
    │  ✅ Spot breakouts with volume confirmation             │
    │  ✅ Use VWAP, 20 EMA, RSI for confluence signals        │
    │  ✅ Plan trades with entry, SL, target, R:R             │
    │  ✅ Backtest using Bar Replay                           │
    │  ✅ Follow a structured daily workflow                  │
    │                                                         │
    └─────────────────────────────────────────────────────────┘
```

---

## WHAT'S NEXT

**Phase 3: Options Theory Deep Study (Weeks 11–18)**

This is where the real options mastery begins. Over the next 8 weeks, you'll learn:

- **Week 11:** Option Pricing — Intrinsic vs Extrinsic Value Deep Dive
- **Week 12:** The Greeks — Delta (Direction Sensitivity)
- **Week 13:** The Greeks — Gamma (Delta's Acceleration)
- **Week 14:** The Greeks — Theta (Time Decay — Your #1 Enemy)
- **Week 15:** The Greeks — Vega (Volatility Sensitivity)
- **Week 16:** Implied Volatility (IV) and India VIX
- **Week 17:** Option Chain Deep Analysis + OI Interpretation
- **Week 18:** Options Strategies for Beginners (Covered Call, Protective Put, Bull Call Spread, Bear Put Spread)

This phase will transform you from someone who *buys calls and puts based on charts* to someone who *understands the mathematics behind every rupee of premium*.

Say **"proceed to week 11"** when you're ready to begin Phase 3!
