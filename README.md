# Berry – Agentic Trading Assistant

[![Status](https://img.shields.io/badge/status-active-brightgreen)](#) [![Award](https://img.shields.io/badge/FinTech_Showcase-1st_Place-blueviolet)](#) [![Stack](https://img.shields.io/badge/stack-Python_%7C_Flask_%7C_React_%7C_Vite-0a84ff)](#) [![License](https://img.shields.io/badge/license-MIT-lightgrey)](#)

Berry mimics the research and execution workflow of a real life trading firm to deliver buy/hold/sell decisions, risk commentary, and actionable investment plans. It pairs a Python/Flask backend with a React + TypeScript + Vite frontend so you can explore analysis, generate portfolios, and monitor market signals in one place. Berry won **1st place** in our semester-long FinTech project showcase.

## What Berry does
- **Agentic research loop:** Multiple analyst personas (market, media, news, fundamentals) debate and synthesize a trade decision.
- **Actionable reports:** Final output includes decision, rationale, risk assessment, and a simple investment plan.
- **Portfolio tools:** Generate diversified portfolios, fetch historical performance, and launch allocations through Alpaca.
- **Market + news data:** Trending headlines, top gainers/losers, and ticker lookups to ground decisions in real-time data.
- **Chat-style analysis:** Send a ticker or a plain question and receive structured guidance.

## Repo layout
- `backend/` – Flask API, agent workflows, data connectors, and portfolio utilities.
- `frontend/` – React/TypeScript app (Vite) for dashboards, chat, search, and portfolio views.

## Quick start
1) Clone and open the project:
```bash
git clone <repo-url>
cd AgenticTradingAssistant
```

2) Backend (Python 3.11+):
```bash
cd backend
cp .env.example .env  # create your env file (see below)
uv run app.py         # starts Flask on :5000
# This project uses UV as a package manager
# Run "pip install uv" to install UV
```

3) Frontend (Node 18+):
```bash
cd frontend
npm install
npm run dev           # starts Vite on :5173
```

Visit `http://localhost:5173` and the app will proxy requests to the backend at `http://127.0.0.1:5000`.

## Environment variables
Create `backend/.env` with your keys:
```
GEMINI_API_KEY=...
OPENAI_API_KEY=...
MARKETAUX_API_KEY=...
MASSIVE_API_KEY=...
TIINGO_API_KEY=...
ALPHA_VANTAGE_API_KEY=...
ALPACA_API_KEY=...
ALPACA_API_SECRET=...
USE_OPENAI_MODEL=true|false
```
If you switch to only OpenAI or only Gemini, set `USE_OPENAI_MODEL` accordingly.

## Key endpoints (backend)
- `POST /analyze` – Body `{ "message": "Analyze AAPL" }`; returns the debate-driven trade report.
- `GET /portfolio` – Generates a portfolio; accepts `diversification`, `max_risk`, and `sectors` query params.
- `GET /portfolio/current` – Historical portfolio values for charting.
- `GET /portfolio/launch` – Pushes the current portfolio to Alpaca with a starting balance.
- `GET /news/trending` – Trending market headlines.
- `GET /market/top-movers` – Top gainers/losers and most active equities.
- `GET /search/:ticker` – Ticker reference lookup.

## Frontend highlights
- Dashboard with market movers, brokerage snapshot, and portfolio performance.
- Chat experience for asking Berry to research tickers and return structured decisions.
- Portfolio page to generate, review, and launch allocations.
- Education and article views for curated learning content.

## Roadmap ideas
- Parallelize the agentic workflow to speed up deep analysis on stocks
- More granular risk knobs (beta, drawdown limits, sector caps).
- Automatize Berry to run on websockets to get real time analysis when offline

## Contributing
Feel free to open issues or PRs for bugs, UI polish, or new agent strategies. When contributing, keep secrets out of version control and favor config via environment variables.
