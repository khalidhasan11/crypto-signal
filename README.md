# Crypto Signal — Live (News + Chart)

TradingView-স্টাইলের instant Buy/Sell technical rating (Oscillators +
Moving Averages gauges, timeframe অনুযায়ী লাইভ আপডেট) — তার সঙ্গে লাইভ
ক্রিপ্টো নিউজ sentiment মিলিয়ে একটা final fusion signal:
**Technical 70% + News 20% + Market context 10%**.

🔗 Live: https://khalidhasan11.github.io/crypto-signal/

## যা যা করে

- **Instant gauges:** 11টি oscillator (RSI, Stochastic, CCI, ADX, MACD,
  Stochastic RSI, Williams %R, Awesome Oscillator, Momentum, Bull Bear
  Power, Ultimate Oscillator) + 14টি moving average (SMA/EMA 5–200,
  VWMA, Ichimoku) — প্রতিটার Buy/Sell/Neutral action সহ।
- **Timeframes:** 1m / 5m / 15m / 30m / 1h / 4h; BTC ও ETH।
- **News layer:** CoinDesk, CoinTelegraph, Decrypt, Bitcoin Magazine,
  Google News (RSS via rss2json, fallback allorigins) — keyword sentiment,
  সোর্সের ওজন, freshness decay, একই খবরের dedupe, বড় নেতিবাচক ঘটনায়
  (hack/bankruptcy/ban) UP সিগন্যালে **danger veto**।
- **Fusion signal:** UP / DOWN / NO TRADE + কারণের তালিকা।
- **Backtest:** 5m chart-এ technical-only backtest, 85% payout-এর
  break-even (54.05%) এর সঙ্গে তুলনা।

## ডেটা (সব ফ্রি, key লাগে না)

- Binance public market data (`data-api.binance.vision`, CORS-open)
- Fear & Greed Index (`api.alternative.me`)
- RSS news উপরোক্ত ফিডগুলো থেকে

## সৎ সীমাবদ্ধতা

- এটি educational prototype — কোনো rating profit guarantee করে না।
- v1 backtest-এ BTC 5-minute expiry-র win rate break-even-এর নিচে ছিল;
  15-minute expiry সামান্য ওপরে (in-sample মাত্র)। আসল যাচাই হবে
  forward demo/paper testing-এ।
- Quotex OTC দাম ব্রোকার-তৈরি ও তাদের কোনো অফিসিয়াল API নেই — এই টুল
  আসল মার্কেট (Binance) বিশ্লেষণ করে।

Python সংস্করণ (engine + local dashboard): `crypto-signal-prototype`
লোকাল প্রজেক্ট ফোল্ডারে।
