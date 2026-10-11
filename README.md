# IntrinsicIQ - Intelligent Equity Valuation Engine

A fundamental equity valuation engine for any US-listed company. Automatically selects the right valuation methodology based on company type, retrieves risk factors directly from SEC filings, and generates AI-powered analysis using the Claude API.

Live demo: [valuation-engine.streamlit.app](https://valuation-engine.streamlit.app)

---

## What it does

Enter any US ticker and IntrinsicIQ:

1. Classifies the company and selects the appropriate valuation model
2. Pulls live financial data via yfinance and SEC EDGAR
3. Calculates intrinsic value per share with full WACC, FCF projections, and terminal value
4. Runs 10,000 Monte Carlo scenarios to quantify valuation uncertainty
5. Retrieves and cites relevant risk factors from the company's most recent 10-K
6. Generates a structured analyst report separating model-implied risks from company-specific risks

Validated across 12+ companies including TSLA, JPM, EQIX, and RIVN.

---

## Valuation models

| Model | Used for |
|---|---|
| DCF (Discounted Cash Flow) | Standard operating companies |
| Residual Income Model | Financial firms, banks |
| FFO / AFFO | REITs and real estate companies |
| Relative Valuation | Early-stage or pre-profit companies |

The classification router selects the model automatically based on the company's sector and financial profile.

---

## RAG pipeline

- Fetches the most recent 10-K filing from SEC EDGAR
- Chunks and embeds Item 1A (Risk Factors) using `sentence-transformers`
- Retrieves the top-5 most semantically relevant passages for the user's query
- Passes retrieved passages to Claude with source citations for grounded analysis

---

## Tech stack

| Layer | Tools |
|---|---|
| Data | yfinance, SEC EDGAR, beautifulsoup4 |
| Models | Python, NumPy, Pandas |
| RAG | sentence-transformers, SEC EDGAR API |
| AI Analysis | Anthropic Claude API (claude-sonnet-4-6) |
| Simulation | Monte Carlo (10,000 scenarios) |
| Dashboard | Streamlit, Plotly |

---

## Project structure

```
valuation-engine/
├── ai_analyst.py          # Claude API integration and prompt engineering
├── rag_retriever.py       # SEC EDGAR retrieval and semantic search
├── sec_retriever.py       # 10-K filing fetcher
├── requirements.txt
└── src/
    ├── data/
    │   └── fetcher.py     # Live financial data ingestion
    ├── models/
    │   ├── dcf.py         # DCF model and WACC calculator
    │   ├── monte_carlo.py # Monte Carlo simulation engine
    │   ├── residual_income.py    # Residual Income Model
    │   ├── reit_valuation.py     # FFO / AFFO for REITs
    │   └── relative_valuation.py # Comparable company analysis
    └── dashboard/
        └── app.py         # Streamlit dashboard
```

---

## Setup

```bash
git clone https://github.com/himajakavuri23/Valuation-Engine.git
cd Valuation-Engine
pip install -r requirements.txt
```

Create a `.env` file:
```
ANTHROPIC_API_KEY=your_key_here
```

Run the dashboard:
```bash
streamlit run src/dashboard/app.py
```

---

## Author

Himaja Kavuri — MS Business Analytics, USC Marshall School of Business  
Portfolio: [himajakavuri23.github.io](https://himajakavuri23.github.io)  
LinkedIn: [linkedin.com/in/himaja-kavuri](https://linkedin.com/in/himaja-kavuri)
