# Polymarket Trading Bot

Automated trading on [Polymarket](https://polymarket.com) across **sports**, **Bitcoin short-term markets**, and **weather** — built for speed, edge detection, and consistent execution.

---

## Portfolio PnL — Live Results

**See the bot in action.** Real portfolio performance, not backtests.

https://github.com/user-attachments/assets/b20344f3-c8dd-4438-82b9-abb242436aa4

<video src="https://github.com/user-attachments/assets/b20344f3-c8dd-4438-82b9-abb242436aa4" controls width="100%"></video>

> The video above shows actual PnL over time — entries, exits, and cumulative returns across active market strategies.

---

## Contact

Questions, access, or custom setups:

**Telegram:** [@victor0x080](https://t.me/victor0x080)

---

## Supported Markets

| Category | Markets | Timeframe |
|----------|---------|-----------|
| **Sports** | NFL, NBA, MLB, soccer, UFC, and more | Event-based |
| **Bitcoin** | BTC up/down prediction markets | **5 min** · **15 min** · **1 hour** |
| **Weather** | Temperature, precipitation, regional forecasts | Daily / weekly |

### Sports

- Pre-game and in-play odds scanning
- Line movement and liquidity-aware order placement
- Event resolution tracking and position management

### Bitcoin (5m / 15m / 1h)

- Short-horizon BTC direction markets
- Multi-timeframe signal aggregation (5min, 15min, 1hour)
- Fast execution tuned for tight windows and spread capture

### Weather

- NOAA / forecast-model driven probability edges
- City and regional temperature & precipitation markets
- Resolution-aligned position sizing

---

## Features

- **Multi-market engine** — sports, crypto intervals, and weather in one stack
- **Real-time data** — Polymarket CLOB + external feeds (sports odds, BTC price, weather APIs)
- **Risk controls** — max position size, daily loss limits, per-market exposure caps
- **Automated execution** — limit and market orders with slippage guards
- **PnL tracking** — live portfolio dashboard and session logs

---

## Architecture (Overview)

```
┌─────────────────┐     ┌──────────────────┐     ┌─────────────────┐
│  Market Feeds   │────▶│  Signal Engine   │────▶│  Order Executor │
│  (sports/BTC/   │     │  (edge + sizing) │     │  (Polymarket    │
│   weather)      │     └──────────────────┘     │   CLOB API)     │
└─────────────────┘                              └─────────────────┘
         │                                                │
         └────────────────────┬───────────────────────────┘
                              ▼
                    ┌──────────────────┐
                    │  PnL & Portfolio │
                    │  Monitor         │
                    └──────────────────┘
```

---

## Quick Start

### Prerequisites

- Python 3.10+
- Polymarket account with funded wallet (Polygon)
- API credentials / private key for CLOB trading

### Install

```bash
git clone <your-repo-url>
cd polymarket-trading-bot
pip install -r requirements.txt
cp .env.example .env
```

### Configure

Edit `.env` with your keys and strategy toggles:

```env
POLYMARKET_PRIVATE_KEY=your_key
POLYMARKET_API_KEY=your_api_key
POLYMARKET_API_SECRET=your_api_secret
POLYMARKET_PASSPHRASE=your_passphrase

# Strategy modules (true/false)
ENABLE_SPORTS=true
ENABLE_BTC_5MIN=true
ENABLE_BTC_15MIN=true
ENABLE_BTC_1HOUR=true
ENABLE_WEATHER=true

# Risk
MAX_POSITION_USD=100
MAX_DAILY_LOSS_USD=500
```

### Run

```bash
# All enabled strategies
python main.py

# Single strategy
python main.py --strategy btc_15min
python main.py --strategy sports
python main.py --strategy weather
```

---

## Strategy Modules

| Flag | Module | Description |
|------|--------|-------------|
| `sports` | Sports bot | Scans sports markets for mispriced outcomes |
| `btc_5min` | BTC 5-minute | Trades 5-minute BTC direction windows |
| `btc_15min` | BTC 15-minute | Trades 15-minute BTC direction windows |
| `btc_1hour` | BTC 1-hour | Trades 1-hour BTC direction windows |
| `weather` | Weather bot | Trades forecast vs. market probability gaps |

---

## Risk Disclaimer

This software is for **educational and research purposes**. Prediction market trading involves **substantial risk of loss**. Past performance (including the PnL video above) does **not** guarantee future results. Only trade with capital you can afford to lose. Not financial advice.

---

## License

Private / proprietary — contact [@victor0x080](https://t.me/victor0x080) for licensing or collaboration.
