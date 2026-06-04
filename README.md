<div align="center">

# Master Analyst Agent

### Multi-Agent AI Investment Analysis Platform

*6 specialized agents · weighted signal aggregation · Monte Carlo simulation · professional PDF reporting · real-time dashboard*

<br>

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Claude](https://img.shields.io/badge/Claude-Sonnet-CC785C?style=for-the-badge&logo=anthropic&logoColor=white)](https://anthropic.com/)
[![GPT-4](https://img.shields.io/badge/GPT--4-Fallback-412991?style=for-the-badge&logo=openai&logoColor=white)](https://openai.com/)
[![Reflex](https://img.shields.io/badge/Reflex-Dashboard-6C47FF?style=for-the-badge)](https://reflex.dev/)
[![License](https://img.shields.io/badge/MIT-green?style=for-the-badge)](LICENSE)

<br>

[![GitHub stars](https://img.shields.io/github/stars/fb4vprmxyd-web/master-analyst-agent?style=social)](https://github.com/fb4vprmxyd-web/master-analyst-agent/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/fb4vprmxyd-web/master-analyst-agent?style=social)](https://github.com/fb4vprmxyd-web/master-analyst-agent/network/members)

---

**A production-grade investment analysis system** that orchestrates 6 specialized AI agents — 2 technical and 4 fundamental — executing in parallel to generate institutional-quality stock recommendations with weighted consensus, professional PDF reports, and a real-time web dashboard.

<br>

[Agents](#agents-overview) · [Architecture](#architecture) · [Signal Aggregation](#signal-aggregation) · [Dashboard](#dashboard) · [Getting Started](#getting-started) · [Project Structure](#project-structure)

</div>

<br>

## Highlights

<table>
<tr>
<td width="50%">

**Multi-Agent System**
- 6 independent agents (2 technical + 4 fundamental)
- Parallel subprocess execution with async orchestration
- Weighted plurality voting (BUY/HOLD/SELL)
- Claude Sonnet synthesis with GPT-4 fallback

</td>
<td width="50%">

**Technical Analysis**
- 20+ indicators: RSI, MACD, Bollinger, Ichimoku, ADX, Stochastic
- 10-year backtesting with vectorized execution
- 10,000 Monte Carlo simulations
- HMM regime detection (Hurst exponent, R/S analysis)

</td>
</tr>
<tr>
<td width="50%">

**Fundamental Analysis**
- DCF, DDM, and multiples valuation (P/E, EV/EBITDA, P/FCF)
- 3-factor and 5-factor DuPont decomposition
- 39+ financial ratios across 8 categories
- Bull/base/bear scenario analysis

</td>
<td width="50%">

**Reporting & Dashboard**
- Real-time Reflex web dashboard (port 3000)
- Professional PDF reports via ReportLab
- Target price comparison charts
- Live progress monitoring with polling

</td>
</tr>
</table>

---

## Agents Overview

| Agent | Type | Weight | Key Capabilities |
|:------|:-----|:------:|:-----------------|
| **Technical Agent 1** | Technical | 20% | RSI, MACD, SMA, ADX, Bollinger Bands, Hurst exponent, 10K Monte Carlo, Kelly sizing |
| **Technical Agent 2** | Technical | 30% | 16 indicators, Ichimoku, Supertrend, Aroon, OBV, CMF, MFI, regime-aware thresholds |
| **Fundamental Agent 1** | Fundamental | 15% | DCF (WACC/CAPM), DDM, multiples, DuPont (3+5 factor), 43-point data validation |
| **Fundamental Agent 2** | Fundamental | 15% | 10-step pipeline: profitability, cash flow, earnings quality, working capital |
| **Fundamental Agent 3** | Fundamental | 10% | 8-category ratio analysis, quantitative risk scoring, revenue/earnings forecasting |
| **Fundamental Agent 4** | Fundamental | 10% | FCFF-based DCF, peer multiples, 60/40 blended target price |

---

## Architecture

```
                    ┌──────────────────────────────────────────────┐
                    │           Master Agent Orchestrator           │
                    │      (src/master_agent.py · Claude/GPT-4)    │
                    └──────────┬───────────────────────────────────┘
                               │ Parallel subprocess execution
              ┌────────────────┼────────────────┐
              │                │                │
     ┌────────▼────────┐ ┌────▼──────┐ ┌───────▼────────────┐
     │  Technical (2)   │ │  Fund (4)  │ │  Signal Aggregation │
     │                  │ │            │ │                     │
     │  TA1: Momentum   │ │ FA1: DCF   │ │  Weighted Voting    │
     │  TA2: Full Suite │ │ FA2: 10-step│ │  LLM Synthesis      │
     │                  │ │ FA3: Ratios │ │  PDF Generation     │
     │  Regime + Monte  │ │ FA4: FCFF  │ │  Chart Creation     │
     │  Carlo + Kelly   │ │            │ │                     │
     └─────────────────┘ └───────────┘ └─────────────────────┘
                               │
                    ┌──────────▼───────────────────────────────────┐
                    │              shared_outputs/                  │
                    │   JSON results · PDF report · PNG charts     │
                    └──────────┬───────────────────────────────────┘
                               │
                    ┌──────────▼───────────────────────────────────┐
                    │         Reflex Dashboard (port 3000)          │
                    │    Live progress · Results viewer · Charts   │
                    └──────────────────────────────────────────────┘
```

---

## Signal Aggregation

The master agent combines all 6 agent outputs through a multi-step consensus process:

1. **Collect** — JSON outputs from `shared_outputs/` (parallel agent execution)
2. **Normalize** — Map STRONG_BUY → BUY, STRONG_SELL → SELL
3. **Weight** — Sum agent weights per signal type (BUY/HOLD/SELL)
4. **Vote** — Plurality voting selects the highest-weighted signal
5. **Synthesize** — Claude (primary) or GPT-4 (fallback) generates institutional narrative
6. **Report** — Professional PDF with ReportLab + comparison charts

---

## Dashboard

Real-time web dashboard built with [Reflex](https://reflex.dev/) (Python full-stack framework):

- Launch analysis from browser with stock ticker input
- Live progress bar with subprocess polling (1s intervals)
- Results viewer with agent recommendations and confidence scores
- Target price comparison and price action charts

---

<details>
<summary><b>Technical Agent Details</b></summary>

<br>

### Technical Agent 1 (20% weight)

**Indicators:** RSI (14), MACD (12/26/9), SMA 50/200, Bollinger Bands, ATR, ADX

**Advanced Analysis:**
- Hurst exponent (R/S analysis) for trend persistence classification
- GARCH(1,1) volatility forecasting
- 10,000 Monte Carlo simulations for confidence intervals
- Fractional Kelly Criterion (0.25x) for position sizing
- Walk-forward backtesting (10 years)

### Technical Agent 2 (30% weight)

**Momentum:** RSI, Stochastic %K/%D, Williams %R, ROC, MACD histogram
**Trend:** ADX/DMI, Aroon, Supertrend
**Channels:** Bollinger Bands, Keltner Channels, Donchian Channels
**Volume:** OBV, Chaikin Money Flow, MFI, VWMA
**Systems:** Ichimoku Kinko Hyo (5 components)

</details>

<details>
<summary><b>Fundamental Agent Details</b></summary>

<br>

### Fundamental Agent 1 (15% weight)
DCF (WACC/CAPM), DDM, multiples (P/E, P/B, P/S, P/FCF, EV/EBITDA, EV/Revenue), DuPont (3+5 factor), 43-point data validation.

### Fundamental Agent 2 (15% weight)
10-step pipeline: profitability, cash flow, earnings quality, working capital, ratio calculation, multi-methodology valuation.

### Fundamental Agent 3 (10% weight)
8-category ratio analysis (Liquidity, Leverage, Efficiency, Growth, Profitability, Valuation, Risk), quantitative risk scoring, forecasting.

### Fundamental Agent 4 (10% weight)
FCFF-based DCF, WACC via CAPM, tech peer multiples, 60/40 blended target price with terminal growth sensitivity.

</details>

---

## Getting Started

### Prerequisites

- Python 3.10+
- API keys: Anthropic (Claude), OpenAI (GPT-4), Alpha Vantage (x4)

### Installation

```bash
git clone https://github.com/fb4vprmxyd-web/master-analyst-agent.git
cd master-analyst-agent

python -m venv venv && source venv/bin/activate
pip install -r requirements.txt

cp .env.example .env
# Edit .env with your API keys
```

### Running

| Mode | Command | Description |
|:-----|:--------|:------------|
| **CLI Analysis** | `python run_demo.py` | Analyze AAPL (default) |
| **Custom Ticker** | `python run_demo.py --symbol MSFT` | Analyze any stock |
| **Dashboard** | `./run_dashboard.sh` | Web UI at localhost:3000 |
| **Environment Check** | `python run_demo.py --check` | Validate API keys |
| **Architecture Info** | `python run_demo.py --info` | Show system details |

---

## Project Structure

```
master-analyst-agent/
├── src/
│   └── master_agent.py                 # Core orchestrator
│
├── technical_agents/
│   ├── technical_agent_1/src/          # 20% — Momentum, regime, Monte Carlo
│   └── technical_agent_2/src/          # 30% — Full indicator suite + Ichimoku
│
├── fundamental_agents/
│   ├── fundamental_agent_1/src/        # 15% — DCF, DDM, multiples, DuPont
│   ├── fundamental_agent_2/src/        # 15% — 10-step pipeline
│   ├── fundamental_agent_3/src/        # 10% — 8-category ratios
│   └── fundamental_agent_4/src/        # 10% — FCFF DCF + peer multiples
│
├── dashboard/                          # Reflex web dashboard
├── run_demo.py                         # CLI entry point
├── run_dashboard.sh                    # Dashboard launcher
├── requirements.txt                    # Dependencies
└── .env.example                        # API key template
```

---

<div align="center">

**[MIT License](LICENSE)**

Built with Claude, GPT-4, Reflex, yfinance, Alpha Vantage, and ReportLab

</div>
