# 15m-EMA-9-15-OI-Flip-Signals
A Pine Script strategy focused on trend reversal using EMA crossover and OI Flips settings

This indicator is a focused scalping tool designed for crypto markets, specifically optimized for the 15-minute timeframe. It combines a classic trend-following approach with market flow data to help identify short-term reversals while filtering out weak signals. The core logic relies on a crossover between the 9 EMA and 15 EMA to detect trend changes, but a trade signal is only generated if the Open Interest is currently trading above its 20-period average.

By adding this Open Interest filter, the script aims to ignore "fake-outs" that happen during low-volume chop and only highlights setups where new capital is actually entering the market. Visually, it colors the area between the EMAs to show trend direction and prints clear Buy or Sell labels when all conditions are met. If specific Open Interest data is unavailable for a ticker, the system automatically falls back to standard volume data to keep the strategy functional. This tool is intended to provide high-quality entry signals that you can manage with your own exit strategy and risk management rules.
