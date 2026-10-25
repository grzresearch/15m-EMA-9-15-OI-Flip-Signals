# 15m EMA 9/15 OI Flip Signals

A Pine Script indicator for TradingView focused on trend reversals: it signals
crossovers of the 9 and 15 EMA and confirms them with an open interest
filter. It is a focused scalping tool for crypto markets, optimized for the
15-minute timeframe.

## Contents

- [How it works](#how-it-works)
- [Installation](#installation)
- [Settings](#settings)
- [Alerts](#alerts)
- [Limitations](#limitations)
- [Project structure](#project-structure)
- [License](#license)

## How it works

The indicator combines a classic trend-following approach with market flow
data to help identify short-term reversals while filtering out weak signals.

- **Trend change**: the core logic is a crossover between the 9 EMA and the
  15 EMA. A cross up gives a buy signal, a cross down a sell signal.
- **Open interest filter**: a signal is only generated if open interest is
  currently above its 20-period average. The filter aims to ignore
  "fake-outs" during low-volume chop and to highlight only setups where new
  capital is entering the market. It applies to both directions and can be
  switched off.
- **Fallback**: if open interest data is unavailable for the configured
  symbol, the indicator falls back to the chart's volume so that it keeps
  working.
- **Chart output**: the area between the EMAs is colored green or red by
  trend direction, and clear **BUY** and **SELL** labels (with a highlighted
  background) are printed when all conditions are met.

The indicator only marks entries. It is intended to provide high-quality
entry signals that you manage with your own exit strategy and risk
management rules.

## Installation

The script requires Pine Script v6 (`//@version=6`).

1. Open a chart on [TradingView](https://www.tradingview.com), preferably on
   the 15-minute timeframe, and open the **Pine Editor**.
2. Replace the editor contents with
   [`ema_crossover_+_OI_flip.pine`](ema_crossover_+_OI_flip.pine).
3. Click **Save**, then **Add to chart**. The indicator appears as
   **15m EMA + OI Flip Signals**.

## Settings

| Group | Input | Default |
|-------|-------|---------|
| EMA TREND | Fast EMA (Signal) | 9 |
| | Slow EMA (Baseline) | 15 |
| OPEN INTEREST FILTER | Benutze OI Filter? (use OI filter) | on |
| | Open Interest Symbol | `BINANCE:BTCUSDTPERP` |
| | OI Durchschnitt (SMA) (OI average) | 20 |

When trading ETH, change the symbol to `BINANCE:ETHUSDTPERP`, as noted in the
script.

## Alerts

| Condition | Message |
|-----------|---------|
| LONG Signal | EMA Cross UP + OI Valid -> BUY |
| SHORT Signal | EMA Cross DOWN + OI Valid -> SELL |

## Limitations

- The filter requests the `open` series of the configured symbol. For a price
  symbol such as the default `BINANCE:BTCUSDTPERP` this is the bar's opening
  price rather than open interest; to filter on actual open interest, enter a
  symbol that carries open interest data in your TradingView data feed.
- The volume fallback is used only when the configured symbol returns no
  data.
- The script contains no exit logic, position sizing or performance
  calculation.

## Project structure

```
15m-ema-9-15-oi-flip-signals/
├── ema_crossover_+_OI_flip.pine   # the indicator (Pine Script v6)
├── README.md
└── LICENSE                        # Mozilla Public License 2.0
```

## License

Released under the Mozilla Public License 2.0, see [LICENSE](LICENSE).
