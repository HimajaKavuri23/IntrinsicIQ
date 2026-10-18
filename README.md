# Intrinsic IQ — Equity Valuation Engine

A full-stack equity valuation engine that takes a stock ticker and produces institutional-grade intrinsic value estimates through multiple valuation methodologies, Monte Carlo simulation, SEC filing retrieval, and GenAI-powered analysis.

---

## How it works

```
User Enters Stock Ticker
         |
         v
Financial Data Retrieval (yfinance)
         |
         v
Company Classification
         |
         v
Methodology Selection
         |
   +-----+-----+-----+
   |           |     |
   v           v     v
FCFF DCF  Residual  FFO/AFFO
           Income   (REITs)
   |           |     |
   +-----+-----+-----+
         |
         v
   Valuation Results
         |
         v
Sensitivity & Monte Carlo (10,000 simulations)
         |
         v
SEC 10-K Retrieval
         |
         v
GenAI / RAG Analysis
         |
         v
Interactive Dashboard (Streamlit)
```

---

## Features

**Multi-model valuation**
- FCFF DCF with WACC calculation (cost of equity via CAPM, after-tax cost of debt)
- Residual Income Model for earnings-based intrinsic value
- FFO / AFFO valuation for REITs

**Risk quantification**
- Monte Carlo simulation — 10,000 scenarios varying growth rate, WACC, terminal growth, and FCF margin
- Sensitivity analysis across key assumptions

**Fundamental data pipeline**
- Real-time financial data via `yfinance` (income statement, balance sheet, cash flows)
- SEC EDGAR 10-K retrieval for primary source analysis

**GenAI layer**
- RAG pipeline over SEC filings using `sentence-transformers` + `anthropic` SDK
- AI analyst generates qualitative commentary grounded in the actual filings

**Interactive dashboard**
- Streamlit front end with Plotly visualizations
- FastAPI back end for programmatic access

---

## Tech stack

| Layer | Technology |
|---|---|
| Data retrieval | yfinance, SEC EDGAR (EDGAR Full-Text Search) |
| Valuation models | Python, NumPy, Pandas |
| Simulation | NumPy (Monte Carlo, 10K runs) |
| GenAI / RAG | Anthropic SDK, sentence-transformers, PyTorch |
| Dashboard | Streamlit, Plotly, Altair |
| API | FastAPI, Uvicorn |
| Storage | SQLAlchemy, PostgreSQL (psycopg2) |

---

## Project structure

```
valuation-engine/
├── src/
│   ├── data/
│   │   └── fetcher.py          # yfinance data pipeline
│   ├── models/
│   │   ├── dcf.py              # FCFF DCF + WACC calculator
│   │   ├── residual_income.py  # Residual income model
│   │   ├── reit_valuation.py   # FFO / AFFO model
│   │   ├── relative_valuation.py
│   │   └── monte_carlo.py      # 10,000-scenario simulation
│   ├── api/
│   │   └── main.py             # FastAPI endpoints
│   └── dashboard/
│       └── app.py              # Streamlit UI
├── ai_analyst.py               # GenAI commentary layer
├── rag_retriever.py            # RAG pipeline over SEC filings
├── sec_retriever.py            # SEC EDGAR 10-K fetcher
└── requirements.txt
```

---

## Quickstart

```bash
git clone https://github.com/HimajaKavuri23/Valuation-Engine.git
cd Valuation-Engine
pip install -r requirements.txt

# Run the dashboard
streamlit run src/dashboard/app.py

# Or start the API
uvicorn src.api.main:app --reload
```

---

## Author

Himaja Kavuri — MS Analytics, USC Viterbi School of Engineering
Portfolio: [himajakavuri23.github.io](https://himajakavuri23.github.io)
LinkedIn: [linkedin.com/in/himaja-kavuri](https://linkedin.com/in/himaja-kavuri)
