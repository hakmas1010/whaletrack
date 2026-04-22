# 🐋 Whale Tracker

> **Real-time crypto whale wallet tracking and predictive market movement alerts.**

![Node.js](https://img.shields.io/badge/Node.js-20.x-green?logo=nodedotjs)
![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python)
![Web3](https://img.shields.io/badge/Web3-Ethers.js-purple)
![License](https://img.shields.io/badge/License-MIT-green)

---

> [!WARNING]
> ## ⚠️ PARTIAL SHOWCASE — CLASSIFIED PROJECT
>
> This repository contains **only the public-facing listener scaffolding**. Our proprietary predictive algorithms, wallet classification heuristics, historical database connections, and high-frequency trading API keys are **strictly classified** and not included.
> This product operates on closed private servers. This repository is provided solely to demonstrate the system architecture and event-streaming setup.
> **Do not attempt to deploy this code for actual trading.**

---

## 📌 Overview

**Whale Tracker** is a high-speed event listener and predictive alert system designed to monitor massive capital movements across EVM chains (Ethereum, Arbitrum, Optimism) and Solana. 

By analyzing mempool transactions and cross-referencing known institutional/whale wallets, the system predicts significant liquidity events and price volatility *before* they fully materialize on order books.

### Features

- ⚡ **Mempool Monitoring** — Captures pending transactions via dedicated RPC WebSocket connections.
- 🔍 **Heuristic Wallet Profiling** — Proprietary clustering to identify previously unknown whale addresses.
- 🤖 **Predictive Engine** — Python-based ML layer analyzing transaction flow velocity to trigger early-warning alerts.
- 🔔 **Multi-Channel Alerts** — Pushes instant notifications to Discord, Telegram, and internal WebSockets.

---

## 🗂️ Project Structure

```
whale-tracker/
├── src/
│   ├── tracker/
│   │   ├── EVMTracker.js           # EVM chain listener (Ethers.js)
│   │   ├── SolanaTracker.js        # Solana listener
│   │   └── MempoolAnalyzer.js      # Decodes pending txs and estimates impact
│   ├── database/
│   │   └── WalletCluster.js        # Redis cache interface for known wallets
│   ├── alerts/
│   │   ├── PredictiveEngine.py     # ML module predicting market impact (Redacted)
│   │   └── Notifier.js             # Dispatcher for Discord/Telegram
│   └── index.js                    # Service entry point
├── config/
│   └── rpc_endpoints.json          # RPC routing config
├── package.json
├── requirements.txt
└── .env.example
```

---

## ⚙️ Installation

### Prerequisites
- Node.js >= 20.0
- Python >= 3.11
- Redis Server (for wallet caching)
- Private RPC Endpoints (Alchemy/Infura/QuickNode)

```bash
# Clone the repository
git clone https://github.com/yourusername/whale-tracker.git
cd whale-tracker

# Install Node dependencies
npm install

# Install Python dependencies (for PredictiveEngine)
pip install -r requirements.txt
```

---

## 🚀 Usage

Create a `.env` file based on `.env.example`:
```env
ETH_WS_URL=wss://eth-mainnet.alchemyapi.io/v2/YOUR_KEY
REDIS_URL=redis://localhost:6379
ALERT_DISCORD_WEBHOOK=...
```

Start the tracker service:
```bash
npm run start
```

### Sample Alert Output

```json
{
  "timestamp": "2026-04-22T10:45:12Z",
  "event_type": "WHALE_MOVEMENT",
  "chain": "Ethereum",
  "asset": "USDC",
  "amount_usd": 45000000,
  "from_entity": "Binance Hot Wallet 14",
  "to_entity": "Unknown (Cluster ID: X49-B)",
  "prediction": "High likelihood of significant spot buy within 15 minutes.",
  "confidence_score": 0.89
}
```

---

## 📄 License

MIT License — see [LICENSE](./LICENSE) for details.

---

*Classified Internal Tooling — Distribution Prohibited.*
