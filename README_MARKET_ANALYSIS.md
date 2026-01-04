# Advanced Market Analysis & Pattern Detection

## 📊 Overview

A comprehensive Pine Script v6 indicator for TradingView that automatically detects and visualizes multiple advanced technical analysis patterns directly on candlestick charts. This tool integrates Elliott Wave Theory, Harmonic Patterns, Wyckoff Analysis, Dow Theory, and Master Pattern recognition into a single, highly configurable system.

## 🎯 Core Features

### 1. Elliott Wave Analysis (엘리엇 파동 분석)

#### Impulse Waves (1-5)
- **Automatic Detection**: Identifies and labels waves ①, ②, ③, ④, ⑤
- **Truncated Wave Detection**: Detects and labels "5T" when Wave 5 fails to exceed Wave 3
- **Diagonal Recognition**: Identifies Leading and Ending Diagonal patterns
- **Smart Labeling**: Places labels above candles for bullish waves, below for bearish waves

#### Corrective Waves (ABC)
- **Pattern Types**: Flat, ZigZag, and Triangle corrections
- **Visual States**:
  - Solid lines for completed patterns
  - Dashed lines for potential/in-progress patterns
- **Complex Structures**: Handles various corrective combinations

#### Connecting Waves (WXY, WXYXZ)
- **WXY Structure**: 3-wave corrective pattern with X connector
- **WXYXZ Structure**: 5-wave complex corrective pattern
- **Rule-Based Detection**: Follows established Elliott Wave principles

#### Triangle Waves (ABCDE)
- **Converging Triangles**: Narrowing price ranges
- **Expanding Triangles**: Widening price ranges
- **Terminal Triangles**: Ending diagonal patterns
- **5-Point Labeling**: A, B, C, D, E labels with pattern identification

### 2. Harmonic Pattern Detection (하모닉 패턴)

Implements 8 major harmonic patterns with precise Fibonacci ratio detection:

#### Supported Patterns
1. **Gartley** (XAB=0.618, ABC=0.382-0.886, BCD=1.13-1.618, XAD=0.786)
2. **Butterfly** (XAB=0.786, ABC=0.382-0.886, BCD=1.618-2.24, XAD=1.27-1.618)
3. **Bat** (XAB=0.382-0.50, ABC=0.382-0.886, BCD=1.618-2.618, XAD=0.886)
4. **Crab** (XAB=0.382-0.618, ABC=0.382-0.886, BCD=2.24+, XAD=1.618)
5. **Shark** (XAB=0.382-0.618, ABC=1.13-1.618, XAD=0.886-1.13)
6. **Cypher** (XAB=0.382-0.618, AXC=1.13-1.414, XCD=0.786)
7. **AB=CD** (Simplified harmonic structure)
8. **5-0 Pattern** (Advanced reversal pattern)

#### Features
- **Fibonacci Tolerance**: Configurable tolerance (default ±0.15) for ratio matching
- **Potential Patterns**: Displays forming patterns with dashed lines
- **XABCD Labeling**: Clear point identification with circular labels
- **Ratio Validation**: Prevents tolerance overlap with adjacent Fibonacci levels

### 3. Wyckoff Pattern Analysis (와이코프 패턴 분석)

Identifies key Wyckoff accumulation phases:

- **PS (Preliminary Support)**: Initial selling pressure stops
- **AR (Automatic Rally)**: First rally from support
- **ST (Secondary Test)**: Retest of support area
- **Spring**: Break below support followed by rally

Labels are placed below candles to minimize visual clutter.

### 4. Dow Theory Visualization (다우 이론)

#### Three Trend Stages
- **Short-Term Trend**: 20-period SMA based
- **Intermediate Trend**: 50-period SMA based
- **Long-Term Trend**: 200-period SMA based

#### Display
- Real-time trend table in top-right corner
- Color-coded trend status (Bullish/Bearish)
- Three-tier trend analysis

### 5. Master Pattern (마스터 패턴)

Identifies three key market phases:

#### Contraction Phase
- **Detection**: Bollinger Band width analysis
- **Visualization**: Yellow highlighted box
- **Meaning**: Low volatility, potential breakout setup

#### Expansion Phase
- **Detection**: Increased ATR and Bollinger Band width
- **Visualization**: Purple line overlay
- **Meaning**: High volatility, directional movement

#### Trend Phase
- **Detection**: EMA crossover and price position
- **Visualization**: Directional arrows (▲ uptrend, ▼ downtrend)
- **Meaning**: Sustained directional price movement

### 6. Kondratiev Wave (콘드라티예프 파동)

Long-term economic cycle analysis adapted for trading timeframes (originally 40-60 year cycles):

#### Four Seasonal Phases
- **Spring (Recovery)**: Rising from bottom, early recovery phase
  - Cycle Position: 0-25%
  - Price Action: Rising with positive momentum
  - Color: Green

- **Summer (Prosperity)**: Peak expansion, maximum growth
  - Cycle Position: 25-60%
  - Price Action: Strong uptrend continuation
  - Color: Yellow

- **Autumn (Recession)**: Declining from peak, distribution phase
  - Cycle Position: 60-100%
  - Price Action: Weakening with negative momentum
  - Color: Orange

- **Winter (Depression)**: Bottom formation, accumulation phase
  - Cycle Position: 0-25%
  - Price Action: Declining with negative momentum
  - Color: Blue

#### Visualization
- **Real-time Table**: Bottom-right corner showing current phase and cycle position
- **Phase Transition Markers**: Labels appear when phases change
- **Cycle Position %**: Shows where price is within the long-term cycle

### 7. Deep Depth Cycle (심층 사이클)

Multi-timeframe cycle analysis using Hurst-inspired detrended oscillators:

#### Three Cycle Tiers
- **Short Cycle (SC)**: Default 20 periods
  - Detects minor market rhythms
  - Labels: SC↑ (peak) and SC↓ (trough)

- **Medium Cycle (MC)**: Default 50 periods
  - Identifies intermediate swings
  - Labels: MC↑ (peak) and MC↓ (trough)

- **Long Cycle (LC)**: Default 100 periods
  - Reveals major market cycles
  - Labels: LC↑ (peak) and LC↓ (trough)
  - **Important**: Long cycle extremes signal major reversals

#### Features
- **Cycle Alignment Detection**: Background color when all 3 cycles align
  - Green background: All cycles bullish (strong upward momentum)
  - Red background: All cycles bearish (strong downward momentum)
- **Real-time Status Table**: Middle-right showing all cycle directions
- **Detrended Analysis**: Removes trend to isolate pure cyclical movement
- **Normalized Oscillators**: Standard deviation-based thresholds for reliable signals

### 8. Jesse Livermore Accumulation Cylinder (제시 리버모어 축적 실린더)

Horizontal consolidation pattern detection based on Jesse Livermore's trading methodology:

#### Cylinder Formation
- **Consolidation Detection**: Price trades in narrow range (default ≤3% range)
- **Minimum Duration**: Default 10 bars minimum for valid cylinder
- **Volume Confirmation**: Consistent volume during accumulation
- **Visual Box**: Olive-colored rectangle marking the cylinder zone

#### Breakout Signals
- **Bullish Breakout**: Price closes above cylinder top
  - Label: "Cylinder Breakout ▲"
  - Green arrow projection showing expected move
  - Expected move: Height of cylinder projected upward

- **Bearish Breakout**: Price closes below cylinder bottom
  - Label: "Cylinder Breakout ▼"
  - Red arrow projection showing expected move
  - Expected move: Height of cylinder projected downward

#### States
- **Forming Cylinder**: Dashed border box (in progress)
- **Completed Cylinder**: Solid border box with bar count
- **Breakout**: Strong directional signal with projected target

#### Trading Application
- Wait for cylinder formation (accumulation/distribution)
- Enter on breakout in direction of break
- Target: Minimum = cylinder height
- Stop loss: Opposite side of cylinder

## ⚙️ Configuration Options

### Pattern Display Toggles

```pine
Show Elliott Waves                    // Master toggle for all Elliott patterns
  ↳ Show Impulse Waves (1-5)          // Toggle impulse wave detection
  ↳ Show Corrective Waves (ABC)       // Toggle corrective wave detection
  ↳ Show Connecting Waves (WXY)       // Toggle connecting wave detection
  ↳ Show Triangle Waves (ABCDE)       // Toggle triangle detection
  ↳ Show Truncated Wave 5 (5T)        // Toggle truncation labels
  ↳ Show Diagonal Patterns            // Toggle diagonal identification

Show Harmonic Patterns                // Toggle all harmonic patterns
Show Wyckoff Phases                   // Toggle Wyckoff phase labels
Show Dow Theory                       // Toggle Dow Theory table
Show Master Pattern                   // Toggle Master Pattern visualization
Show Kondratiev Wave                  // Toggle Kondratiev Wave cycle analysis
Show Deep Depth Cycle                 // Toggle multi-timeframe cycle detection
Show Livermore Accumulation Cylinder  // Toggle Jesse Livermore cylinder pattern
```

### ZigZag Settings

- **ZigZag Depth**: Number of bars for pivot detection (default: 12)
- **ZigZag Deviation %**: Minimum price change percentage (default: 5.0%)

### Harmonic Pattern Settings

- **Fibonacci Tolerance**: Ratio matching tolerance (default: 0.15, range: 0.05-0.30)
- **Show Potential Patterns**: Display forming patterns with dashed lines

### Kondratiev Wave Settings

- **Lookback Period**: Historical bars to analyze for cycle detection (default: 250, range: 50-1000)
  - Higher values: Longer-term cycle analysis (recommended for daily/weekly charts)
  - Lower values: Shorter-term cycle analysis (for intraday charts)

### Deep Depth Cycle Settings

- **Short Cycle Length**: Period for short-term cycle (default: 20, range: 5-100)
- **Medium Cycle Length**: Period for medium-term cycle (default: 50, range: 20-200)
- **Long Cycle Length**: Period for long-term cycle (default: 100, range: 50-500)

### Livermore Cylinder Settings

- **Minimum Consolidation Bars**: Minimum bars for valid cylinder (default: 10, range: 5-50)
- **Max Range %**: Maximum price range % for cylinder formation (default: 3.0%, range: 1.0-10.0%)
  - Lower values: Tighter consolidation required (more selective)
  - Higher values: Allows wider consolidation (more patterns detected)

### Color Customization

- **Impulse Wave Color**: Default blue
- **Corrective Wave Color**: Default red
- **Harmonic Pattern Color**: Default purple
- **Wyckoff Color**: Default orange
- **Dow Theory Color**: Default green
- **Master Pattern Colors**:
  - Contraction: Yellow (80% transparency)
  - Expansion: Purple
  - Trend: Teal
- **Kondratiev Wave Color**: Default navy
- **Deep Depth Cycle Color**: Default maroon
- **Livermore Cylinder Color**: Default olive (70% transparency)

### Advanced Settings

- **Label Spacing Multiplier**: Adjust spacing between overlapping labels (0.5-5.0)
- **Debug Mode**: Enable debugging logs for development

## 🚀 Installation & Usage

### Installation

1. Open TradingView
2. Navigate to Pine Editor (bottom panel)
3. Create a new indicator
4. Copy and paste the contents of `advanced_market_analysis.pine`
5. Click "Add to Chart"

### Usage Tips

1. **Start with Default Settings**: Load the indicator with default settings to see all patterns
2. **Selective Display**: Use toggles to focus on specific pattern types
3. **Adjust ZigZag Sensitivity**:
   - Lower depth = More patterns (may be noisy)
   - Higher depth = Fewer, more significant patterns
4. **Harmonic Tolerance**:
   - Strict (0.05-0.10): Only precise patterns
   - Moderate (0.10-0.20): Balanced approach
   - Loose (0.20-0.30): More pattern detection
5. **Label Spacing**: Increase multiplier if labels overlap on your timeframe

### Best Practices

- **Timeframe Considerations**:
  - Higher timeframes (4H, Daily, Weekly): More reliable patterns
  - Lower timeframes (5m, 15m): More frequent but less reliable patterns
- **Confluence**: Look for multiple pattern confirmations at the same price level
- **Volume Confirmation**: Use with volume indicators for Wyckoff analysis
- **Risk Management**: Patterns indicate probability, not certainty

## 📐 Technical Implementation

### Performance Optimizations

- **Pine Script v5**: Uses latest version for optimal performance
- **`var` Keyword**: Minimizes variable reallocation
- **Built-in Functions**: Leverages `ta.*` functions for calculations
- **Array Management**: Limits array size to prevent memory issues (max 100 pivots)
- **Conditional Execution**: Patterns only calculated when toggles are enabled

### Architecture

```
Main Execution Loop
├── ZigZag Calculation (Pivot Detection)
├── Elliott Wave Detection
│   ├── Impulse Wave Detection
│   ├── Corrective Wave Detection
│   ├── Connecting Wave Detection
│   └── Triangle Wave Detection
├── Harmonic Pattern Detection
│   ├── Gartley, Butterfly, Bat
│   ├── Crab, Shark, Cypher
│   └── AB=CD, 5-0
├── Wyckoff Phase Detection
├── Dow Theory Analysis
└── Master Pattern Detection
```

### Modular Function Design

All pattern detection logic is separated into dedicated functions:
- `f_detect_impulse_wave()`
- `f_detect_corrective_wave()`
- `f_detect_gartley()`, `f_detect_butterfly()`, etc.
- `f_detect_wyckoff()`
- `f_detect_dow_theory()`
- `f_detect_master_pattern()`

## 🔍 Pattern Interpretation Guide

### Elliott Wave Rules

**Impulse Wave Requirements:**
1. Wave 2 cannot retrace more than 100% of Wave 1
2. Wave 3 cannot be the shortest of waves 1, 3, and 5
3. Wave 4 cannot overlap with Wave 1 price territory

**Truncated Wave 5:**
- Indicates weakness in the trend
- Often signals an impending reversal
- Watch for corrective pattern development

### Harmonic Pattern Trading

**Entry Points:**
- Point D completion (Potential Reversal Zone)
- Confirm with additional indicators (RSI, volume)

**Stop Loss:**
- Below/above point X for aggressive entries
- Below/above point D for conservative entries

**Take Profit:**
- First target: 38.2% of CD leg
- Second target: 61.8% of CD leg
- Final target: Point A level

### Wyckoff Phases

**Accumulation Sequence:**
1. **PS**: Smart money starts buying
2. **AR**: First rally attempt
3. **ST**: Final test of support
4. **Spring**: Shakeout of weak hands (best entry)

### Master Pattern Strategy

**Contraction → Expansion → Trend:**
1. **Contraction**: Accumulate positions, prepare for breakout
2. **Expansion**: Breakout occurs, initial directional move
3. **Trend**: Ride the trend with trailing stops

## 🛠️ Customization & Extension

### Adding New Patterns

```pine
// Template for new pattern detection
f_detect_new_pattern() =>
    if array.size(zz_price) >= [required_pivots] and show_[pattern_toggle]
        // Get pivot points
        // Calculate ratios/conditions
        // Validate pattern
        if [pattern_is_valid]
            // Draw lines
            // Place labels
```

### Modifying Fibonacci Ratios

All Fibonacci ratios are defined as constants at the top:

```pine
var float FIB_0618 = 0.618
var float FIB_0786 = 0.786
// Add custom ratios here
```

### Custom Color Schemes

Add new color inputs in the "Color Settings" section:

```pine
var group_colors = "Color Settings"
custom_color = input.color(color.new(color.blue, 0), title="Custom Color", group=group_colors)
```

## 📊 Performance Considerations

### Chart Limits

The indicator is configured with:
- `max_lines_count=500`: Maximum lines drawn on chart
- `max_labels_count=500`: Maximum labels displayed
- `max_boxes_count=500`: Maximum boxes (for contraction zones)

If you experience performance issues:
1. Increase ZigZag depth to reduce pivot points
2. Disable unused pattern types
3. Use on higher timeframes
4. Clear chart history periodically

### Memory Management

- ZigZag array limited to 100 most recent pivots
- Old pivots automatically removed (FIFO)
- Pattern detection only on recent pivots

## 🐛 Troubleshooting

### No Patterns Detected

1. **Check ZigZag Settings**: Increase deviation or decrease depth
2. **Verify Toggles**: Ensure pattern display toggles are enabled
3. **Chart History**: Load more historical data
4. **Timeframe**: Try higher timeframes for clearer patterns

### Too Many Patterns

1. **Increase ZigZag Depth**: More selective pivot detection
2. **Decrease Tolerance**: Stricter harmonic pattern matching
3. **Selective Display**: Disable some pattern types

### Overlapping Labels

1. **Increase Label Spacing Multiplier**: Provides more vertical space
2. **Selective Display**: Show only critical patterns
3. **Zoom Out**: Adjust chart zoom level

## 📚 References & Theory

### Elliott Wave Theory
- **R.N. Elliott**: "The Wave Principle" (1938)
- **Frost & Prechter**: "Elliott Wave Principle" (1978)

### Harmonic Patterns
- **Scott Carney**: "Harmonic Trading" series
- **Fibonacci ratios**: Based on golden ratio mathematics

### Wyckoff Method
- **Richard Wyckoff**: "Studies in Tape Reading" (1910)
- Supply and demand analysis

### Dow Theory
- **Charles Dow**: Market trend analysis (1900s)
- Three trend movements theory

### Master Pattern
- **Volatility analysis**: Contraction and expansion cycles
- Market phase identification

## 📝 Version History

### Version 1.0.0 (Current)
- Initial release
- All 5 pattern detection systems implemented
- Full user customization
- Performance optimizations
- Debug mode support

## 🤝 Contributing

To extend or modify this indicator:

1. **Test thoroughly**: Use different timeframes and instruments
2. **Maintain modularity**: Keep functions separate
3. **Document changes**: Update inline comments
4. **Performance test**: Monitor execution time and resource usage
5. **Follow Pine Script best practices**: Use `var`, avoid `security()` calls

## 📜 License & Disclaimer

**Educational Purpose**: This indicator is for educational and analytical purposes only.

**Trading Disclaimer**:
- Past performance does not guarantee future results
- Pattern detection is probabilistic, not deterministic
- Always use proper risk management
- Consult a financial advisor before trading

**Technical Disclaimer**:
- Patterns are detected based on mathematical criteria
- Market conditions can invalidate theoretical patterns
- Use in conjunction with other analysis methods

## 🌟 Credits

Developed by: Advanced Market Analysis Team
Pine Script Version: v5
TradingView Compatibility: All plans with custom indicator support

---

**For support, questions, or bug reports**, please refer to the debug mode output and verify your settings match the recommended configurations above.

**Happy Trading! 📈**
