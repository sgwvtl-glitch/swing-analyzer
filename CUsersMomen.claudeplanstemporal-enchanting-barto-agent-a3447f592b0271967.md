# Implementation Plan: SMC Analysis Integration

## Goal
Implement Smart Money Concepts (SMC) analysis into the Fibonacci Swing Analyzer, including Market Structure (BOS/CHoCH), Order Blocks (OB), Fair Value Gaps (FVG), and Liquidity pools, and integrate these into the scoring and UI.

## Current Architecture
- `analyze(dBars, hBars, ticker, macro)`: Main logic for calculating technical indicators and the final signal score.
- `render(r)`: Renders the analysis object `r` into the HTML.
- Data sources: Daily and 1H bars from Twelve Data/Yahoo Finance.

## Proposed Implementation

### 1. SMC Detection Logic (New Helper Functions)
I will implement the following functions in vanilla JavaScript before the `analyze` function:

#### A. Swing Point Detection
- `getSwings(bars, window = 2)`: 
    - Iterates through bars to find swing highs (max of window around index) and swing lows (min of window around index).
    - Returns an array of swing objects: `{ index, type: 'high'|'low', value }`.

#### B. Market Structure (BOS/CHoCH)
- `analyzeStructure(bars, swings)`:
    - Tracks the current market regime (Bullish/Bearish).
    - **BOS (Break of Structure)**: Occurs when price closes above the last swing high (in bullish trend) or below the last swing low (in bearish trend).
    - **CHoCH (Change of Character)**: Occurs when price closes below the last swing low (in bullish trend) or above the last swing high (in bearish trend), signaling a trend reversal.
    - Returns: `{ currentStructure: 'Bullish'|'Bearish', lastEvent: 'BOS'|'CHoCH', eventIndex }`.

#### C. Order Blocks (OB)
- `detectOBs(bars, swings, structureEvents)`:
    - **Bullish OB**: The last bearish candle(s) before a strong impulsive move that caused a Bullish BOS or CHoCH.
    - **Bearish OB**: The last bullish candle(s) before a strong impulsive move that caused a Bearish BOS or CHoCH.
    - Returns: An array of OB zones `{ top, bottom, type: 'bull'|'bear', startTime }`.

#### D. Fair Value Gaps (FVG)
- `detectFVGs(bars)`:
    - Identifies gaps between candle 1 and candle 3 in a 3-candle sequence.
    - **Bullish FVG**: `bars[i].low > bars[i-2].high`.
    - **Bearish FVG**: `bars[i].high < bars[i-2].low`.
    - Returns: An array of FVG zones `{ top, bottom, type: 'bull'|'bear', index }`.

#### E. Liquidity Pools
- `detectLiquidity(bars, swings)`:
    - Identifies Buy-Side Liquidity (BSL) at major swing highs or equal highs.
    - Identifies Sell-Side Liquidity (SSL) at major swing lows or equal lows.
    - Returns: `{ bsl: [], ssl: [] }`.

### 2. Scoring Integration (`analyze` function)
Modify the scoring logic to incorporate SMC:
- **SMC Alignment Score**:
    - `+1` if current price is inside a Bullish OB and structure is Bullish.
    - `+1` if current price is inside a Bullish FVG.
    - `-1` for corresponding bearish conditions.
- **SMC Veto**:
    - If a Bearish CHoCH has occurred recently on daily bars, it may override a LONG signal.
    - If a Bullish CHoCH has occurred recently, it may override a SHORT signal.
- **Major Check**: Add SMC alignment as a prerequisite for "Full Position" signals.

### 3. UI Update (`render` function)
Add a new SMC Analysis panel:
- **Card Title**: "SMC Analysis"
- **Market Structure**: Display current regime (e.g., `Bullish (Last: BOS)`).
- **Zone Status**: 
    - "Price in Bullish OB" (Green badge)
    - "Price in Bearish FVG" (Red badge)
    - Or "Neutral / No Zone".
- **Liquidity**: Mention if price is approaching BSL/SSL.

## Step-by-Step Execution Plan

1. **SMC Logic Implementation**:
    - Implement `getSwings`.
    - Implement `analyzeStructure`.
    - Implement `detectOBs`.
    - Implement `detectFVGs`.
    - Implement `detectLiquidity`.
2. **Analyze Integration**:
    - Call all SMC functions inside `analyze`.
    - Calculate SMC alignment and update `score`.
    - Add SMC results (structure, current zone, events) to the returned object.
3. **Render Integration**:
    - Update `render` to include the SMC Analysis card.
    - Add appropriate badges for structure and zones.

## Critical Files
- `index.html`
