# QuantChain — Decentralized AI Copy Trading Marketplace

> Powered by [OpenGradient SDK](https://github.com/OpenGradient/OpenGradient-SDK) · Verifiable inference via TEE

QuantChain is a decentralized copy-trading marketplace where users discover, subscribe to, and automatically copy AI trading strategies — with every inference decision cryptographically verified on the OpenGradient network.

## Features

- 🏆 **Strategy Leaderboard** — ranked by verifiable Sharpe ratios & PnL proofs
- 🤖 **NL Strategy Queries** — ask "copy best low-vol strategy this week" powered by Claude
- ⛓ **On-chain Subscriptions** — pay in $OPG, copy trades automatically
- 🔐 **TEE-Verified Inference** — every trade decision has an on-chain attestation hash
- 🚀 **Deploy Strategies** — upload your AI model to OpenGradient Hub, earn 5–30% profit share
- ⚡ **Live Trade Feed** — real-time verifiable trade stream across all strategies

## Strategy Types

| Type | Description |
|------|-------------|
| Momentum | RSI/volume breakouts, trend-following |
| Mean-Reversion | VWAP deviation, statistical mean-reversion |
| Sentiment-Fused | Twitter NLP + news scoring via LangChain |
| Hybrid | Multi-signal ensemble strategies |

## Tech Stack

- **Frontend**: Vanilla HTML/CSS/JS — zero dependencies
- **AI Inference**: OpenGradient SDK (`pip install opengradient`) + LangChain
- **Verification**: TEE (Trusted Execution Environment) via OpenGradient network
- **Smart Contracts**: Profit-share distribution stubs (EVM-compatible)
- **Server**: Node.js + Express
- **Deployment**: Railway

## Local Development

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/quantchain.git
cd quantchain

# Install dependencies
npm install

# Start dev server
npm run dev

# Open http://localhost:3000
```

## Deploy to Railway

### Option 1: One-click via Railway Dashboard
1. Fork this repo on GitHub
2. Go to [railway.app](https://railway.app) → New Project → Deploy from GitHub
3. Select this repo — Railway auto-detects Node.js
4. Done! Your app is live.

### Option 2: Railway CLI
```bash
npm install -g @railway/cli
railway login
railway init
railway up
```

## OpenGradient Integration

The app uses OpenGradient's verifiable LLM inference for strategy decisions:

```python
import opengradient as og

client = og.Client(private_key=os.environ.get("OG_PRIVATE_KEY"))

# Each trade decision is TEE-verified
completion = client.llm.chat(
    model=og.TEE_LLM.CLAUDE_3_7_SONNET,
    messages=[{"role": "user", "content": "Analyze BTC momentum signal..."}],
)

print(f"Decision: {completion.chat_output['content']}")
print(f"On-chain proof: {completion.transaction_hash}")
```

## Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `PORT` | Server port (Railway sets this automatically) | No |
| `OG_PRIVATE_KEY` | OpenGradient wallet private key | For backend |
| `ANTHROPIC_API_KEY` | For NL query feature | Yes |

## Project Structure

```
quantchain/
├── public/
│   └── index.html        # Full frontend app
├── server.js             # Express server
├── package.json
├── railway.toml          # Railway config
├── .gitignore
└── README.md
```

## License

MIT
