✅ README.md (GitHub‑ready)
markdown
# KrakenBreakoutBot — Open‑Source Donchian Breakout Trading Bot for Kraken

A fully‑autonomous, real‑time crypto breakout trading bot built for the Kraken exchange.  
It listens to live WebSocket ticker data, evaluates Donchian channel breakouts with volume confirmation, RSI guardrails, volatility filters, and Monte Carlo breakout confidence, then executes trades using a rules‑based strategy. Includes a full HUD, dynamic top‑30 asset universe, trailing stops, take‑profit logic, and detailed JSONL order logging.

---

## 📌 Overview

KrakenBreakoutBot is a standalone, open‑source trading bot designed for clarity, transparency, and ease of use.  
It requires no external services — just Python, a config file, and (optionally) Kraken API keys.

The bot:

- Streams **live ticker data** from Kraken WebSockets  
- Computes **Donchian channels**, **RSI**, **volatility**, and **volume SMA**  
- Confirms breakouts using **volume > 20‑period average**  
- Uses **Monte Carlo breakout confidence** to scale position size  
- Selects trades from a **dynamic top‑30 crypto universe**  
- Manages open positions with **hard stop**, **take profit**, and **trailing stop**  
- Displays a clean **HUD** every 30 seconds  
- Logs all trades to a JSONL file  
- Supports **paper mode** (default) and **live mode**

---

## 🚀 Features

### ✔ Donchian Breakout Logic  
Enters long positions when price breaks above the 20‑period Donchian high.

### ✔ Volume Confirmation  
Only trades when volume exceeds the 20‑period SMA.

### ✔ RSI Guardrail  
Avoids overextended breakouts.

### ✔ Volatility Filter  
Ensures breakouts occur during healthy volatility expansion.

### ✔ Monte Carlo Breakout Confidence  
Simulates short‑term paths to estimate breakout continuation probability.

### ✔ Dynamic Universe  
Pulls the top 30 crypto assets by market cap & volume, then filters to Kraken USD pairs.

### ✔ Full HUD  
Shows PnL, open positions, and USDC balance (live mode).

### ✔ JSONL Order Logging  
Every trade is logged to:

kraken_breakout_orders_log.jsonl

Code

---

## 📁 Project Structure

KrakenBreakoutBot/
│
├── bot.py                 # Main trading bot
├── config.example.json    # Config template
├── requirements.txt       # Python dependencies
└── README.md              # Documentation

Code

---

## ⚙️ Installation

Clone the repo:

```bash
git clone https://github.com/YOUR_USERNAME/KrakenBreakoutBot
cd KrakenBreakoutBot
Install dependencies:

bash
pip install -r requirements.txt
🛠 Configuration
Copy the example config:

bash
cp config.example.json config.json
Tune:

Donchian period

RSI threshold

Volume SMA period

Volatility limits

Monte Carlo settings

Stop loss / take profit

HUD interval

All values have safe defaults.

🔑 Live Trading Setup (Optional)
Set your Kraken API keys:

Windows (PowerShell):

powershell
setx KRAKEN_API_KEY "your_key_here"
setx KRAKEN_API_SECRET "your_secret_here"
macOS/Linux:

bash
export KRAKEN_API_KEY="your_key_here"
export KRAKEN_API_SECRET="your_secret_here"
Enable live mode:

bash
setx KRAKEN_BO_MODE "live"
Paper mode is default.

▶️ Running the Bot
bash
python bot.py
You’ll see:

version banner

universe selection

HUD updates

breakout entries

exits (SL/TP/trailing)

order logs

📄 Order Log Format
Example entry:

json
{
  "timestamp": "2026-04-10T17:32:10Z",
  "symbol": "SOL/USD",
  "side": "long",
  "volume": 1.245,
  "mode": "paper",
  "reason": "LONG SOL/USD breakout ...",
  "price": 198.42,
  "status": "paper"
}
🧠 Strategy Summary
The bot enters long positions when:

Price breaks above the Donchian high

Volume exceeds the 20‑period SMA

RSI is below the max threshold

Volatility is within range

Monte Carlo breakout confidence is high

Position size is scaled by Monte Carlo confidence.

Exits occur via:

Hard stop loss

Take profit

Trailing stop

⚠️ Disclaimer
This bot is provided as‑is, with no guarantees.
Crypto trading involves risk.
Use paper mode before enabling live trading.

💬 Support
Open an issue on GitHub for bugs, questions, or feature requests.

Code

---

# ✅ **requirements.txt**

```text
websockets==12.0
requests==2.31.0
Same minimal footprint as your other bots.