# Crypto Signal — Live (News + Chart)

TradingView-style instant Buy/Sell technical ratings (Oscillators +
Moving Averages gauges, updated live per timeframe), fused with real-time
news sentiment into one final signal:
**Technical 70% + News 20% + Market context 10%**.

🔗 Live: https://khalidhasan11.github.io/crypto-signal/

## What it does

- **Chart Buy/Sell markers (v2):** BUY/SELL labels directly on the chart,
  like a TradingView indicator — EMA 5/13 crossover + RSI 14 filter, on
  closed candles only (never repaints). Below the chart, a live position
  bar: Status (LONG/SHORT), Entry, Stop Loss (last-14-candle swing),
  Take Profit (R:R 3:1), and current R. Entry/SL/TP lines are drawn on
  the chart, TP/SL hits get markers, and a stats line below counts the
  signals (TP / SL / reversed). The position bar sits under the chart
  (not overlaid) so it never covers the candles.
- **Live updates:** the chart streams over a Binance WebSocket (updates pushed several times per second); if the stream is blocked, it automatically falls back to 1-second REST polling — either way the forming candle updates every second. The header shows the active mode (`· stream` / `· 1s polling`).
- **Instant gauges:** 11 oscillators (RSI, Stochastic, CCI, ADX, MACD,
  Stochastic RSI, Williams %R, Awesome Oscillator, Momentum, Bull Bear
  Power, Ultimate Oscillator) + 14 moving averages (SMA/EMA 5–200,
  VWMA, Ichimoku) — each with its own Buy/Sell/Neutral action.
- **Timeframes:** 17 options in an expandable dropdown menu — Seconds
  (1s native; 5s/15s/30s aggregated live from 1s candles), Minutes
  (1m–30m), Hours (1h–12h), Days/Weeks (1d/3d/1w); BTC and ETH.
- **News layer:** CoinDesk, CoinTelegraph, Decrypt, Bitcoin Magazine,
  Google News (RSS via rss2json, allorigins fallback) — keyword
  sentiment, source-credibility weighting, freshness decay, duplicate
  story dedupe, and a **danger veto**: a fresh major negative event
  (hack/bankruptcy/ban) cancels an UP signal.
- **Fusion signal:** UP / DOWN / NO TRADE with a list of reasons.
- **Backtest:** technical-only backtest on the 5m chart, compared
  against the 85%-payout break-even win rate (54.05%).

## Data (all free, no API keys)

- Binance public market data (`data-api.binance.vision`, CORS-open)
- Fear & Greed Index (`api.alternative.me`)
- RSS news from the feeds listed above

## Honest limitations

- This is an educational prototype — no rating guarantees profit.
- In the v1 backtest, BTC 5-minute expiry win rate was below break-even;
  15-minute expiry was slightly above (in-sample only). The real verdict
  will come from forward demo/paper testing.
- Quotex OTC prices are broker-generated and Quotex has no official
  API — this tool analyzes the real market (Binance).

The Python version (engine + local dashboard) lives in the local
`crypto-signal-prototype` project folder.
