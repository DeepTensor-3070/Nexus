# 🧠 NEXUS Architecture

## 📌 Overview

NEXUS is a self-learning, context-aware AI financial intelligence system that integrates:

- Personal finance behavior tracking
- Real-time market data and sentiment
- AI-driven decision making with explainability
- Closed-loop learning from user outcomes
- Multi-objective optimization across competing goals

The system follows a **modular, event-driven architecture** with a dedicated **Innovation Layer** designed for research-grade AI capabilities and patent protection.

---

## 🏗️ High-Level Architecture (v2.0)

```
Frontend (React — Dark Cyberpunk UI)
          ↓
API Gateway (FastAPI)
          ↓
┌─────────────────────────────────────────┐
│           INNOVATION LAYER              │
│  Context Fusion · Adaptive Simulation   │
│  Behavioral Engine · Closed-Loop AI     │
│  Multi-Goal Optimizer · XAI · Stress    │
└─────────────────────────────────────────┘
          ↓
Service Layer (Business Logic)
          ↓
AI Layer (ML + LLM + SHAP + RL)
          ↓
Event Bus (Redis Streams / Celery)
          ↓
Database + External APIs + WebSocket Feeds
```

---

## 🧩 Core Components

### 1. 🎨 Frontend Layer

**Technologies:**
- React + Tailwind CSS (dark cyberpunk theme)
- Terminal-style AI chat panel
- Real-time WebSocket dashboard updates

**Responsibilities:**
- User interaction and data visualization
- AI chat interface (autonomous copilot display)
- One-click action approval for copilot proposals

---

### 2. ⚙️ API Gateway (FastAPI)

**Responsibilities:**
- API routing and request validation
- JWT authentication and rate limiting
- WebSocket endpoint management for real-time feeds

**Structure:**

```
backend/
├── routes/
│   ├── expenses.py
│   ├── income.py
│   ├── portfolio.py
│   ├── chat.py
│   ├── market.py
│   ├── goals.py
│   ├── health.py
│   ├── decision.py        ← Context Fusion Engine
│   ├── simulate.py        ← Adaptive Simulation
│   ├── behavior.py        ← Behavioral Engine
│   ├── feedback.py        ← Closed-Loop Learning
│   ├── risk.py            ← Real-Time Risk Adaptation
│   ├── stress_test.py     ← Scenario Stress Testing
│   └── explain.py         ← XAI Explanations
├── schemas/
├── services/
└── models/
```

---

### 3. 🔴 Innovation Layer (New — v2.0)

The **Innovation Layer** is the defining architectural contribution of NEXUS. It sits between the API Gateway and Service Layer as a dedicated intelligence orchestration tier.

#### I-1: Context Fusion Decision Engine

```
Personal Finance Data ──┐
Market State Data       ├──→ Tri-Context Vector → Attention Fusion → Decision Output
Goal Urgency Data ──────┘
```

- Constructs `C = [C_personal, C_market, C_goal]` on every decision request
- Attention weights determine context dominance
- Outputs: `{action, confidence, context_breakdown, explanation}`

**Module:** `innovation/context_fusion.py`

---

#### I-2: Adaptive Financial Simulation Engine

```
Static Parameters ──→ Dynamic Adjustment:
                       R_adjusted = R_base × (1 - vol_factor) × sentiment_weight × risk_mult
                       ↓
                       Monte Carlo (1000+ paths) → Confidence Intervals
```

- Replaces fixed-return assumptions with live-data-adjusted parameters
- Outputs 20th/50th/80th percentile scenarios

**Module:** `innovation/adaptive_simulation.py`

---

#### I-3: Autonomous Financial Copilot

```
Background Daemon
  → Multi-stream anomaly monitor (spending / portfolio / market)
  → Trigger detection
  → Action proposal generation
  → User notification
  → One-click execution pipeline
```

- Runs as async event loop, not request-driven
- Proposals stored in queue; user approves/dismisses via UI

**Module:** `innovation/copilot_daemon.py`

---

#### I-4: Dynamic Financial Health Evolution Model

```
Rolling 90-day behavior window
  → ARIMA/LSTM projection model
  → Market risk injection (volatility modifier)
  → Score trajectory: [current, +30d, +60d, +90d]
```

- Adds predictive dimension to health scoring
- Flags which behavior change has highest score improvement leverage

**Module:** `innovation/health_evolution.py`

---

#### I-5: Behavioral Pattern Learning Engine

```
Transaction history
  → Sequential pattern mining
  → Cluster assignment (behavioral archetype)
  → Anomaly score per transaction
  → Pre-emptive alert generation
```

- User-specific norms (not population averages)
- LSTM predictor for next-period behavior deviation

**Module:** `innovation/behavioral_engine.py`

---

#### I-6: Closed-Loop Financial Learning System

```
Advice Issued
  → User response logged (accept / reject / modify)
  → 30/60/90-day outcome tracking
  → Outcome delta computed
  → RLHF-style weight update per user
  → Next advice calibrated to actual outcomes
```

- Per-user model divergence over time → personalization
- Outcome evaluator is decoupled from advice generator

**Module:** `innovation/closed_loop.py`

---

#### I-7: Real-Time Risk Adaptation Engine

```
WebSocket Market Feed (NSE / Crypto)
  → Event listener (sub-minute latency)
  → Portfolio VaR recalculation
  → Threshold check
  → Risk guidance update
  → Alert push to frontend
```

- Event-driven, not polling-based
- VaR recalculated in real time on each market event

**Module:** `innovation/risk_adapter.py`

---

#### I-8: Multi-Goal Optimization Engine

```
Goal Vector: [{target, deadline, priority, progress}]
  → Pareto optimization (PuLP / SciPy)
  → Constraints: monthly capacity, emergency buffer, max risk
  → Optimal allocation per goal
  → Trade-off explanation per conflict
```

- Mathematical rather than heuristic allocation
- Trade-offs explained in plain language via XAI layer

**Module:** `innovation/goal_optimizer.py`

---

#### I-9: Explainable Financial AI (XAI)

```
Any model output
  → SHAP feature attribution
  → Per-feature contribution scores
  → NL renderer (LLM template)
  → Human-readable explanation
  → Audit log entry
```

- Applied to all AI outputs: recommendations, scores, alerts
- Regulatory audit trail maintained

**Module:** `innovation/xai_engine.py`

---

#### I-10: Financial Scenario Stress Testing

```
User financial state
  → Stress scenario application (income drop / crash / inflation)
  → Survival timeline calculation
  → Recovery plan optimization (min-cost solvency restoration)
  → Output: {months_to_zero, recovery_actions, cost_of_recovery}
```

**Module:** `innovation/stress_tester.py`

---

### 4. 🧠 AI Layer

| Module | Technology | Role |
|---|---|---|
| Expense Classifier | Scikit-learn | Auto-categorize transactions |
| Risk Scorer | Scikit-learn + VaR | Portfolio risk assessment |
| Financial Advisor | LLM (Claude / Mistral) + RAG | Conversational financial guidance |
| Behavioral Profiler | LSTM + Pattern Mining | User behavior modeling |
| Outcome Evaluator | RLHF pipeline | Closed-loop learning |
| XAI Engine | SHAP | Decision explainability |
| Goal Optimizer | PuLP / SciPy | Multi-objective optimization |
| Stress Tester | Monte Carlo | Scenario resilience analysis |

---

### 5. 🗄️ Database Layer

| Store | Technology | Purpose |
|---|---|---|
| Primary DB | PostgreSQL | Users, expenses, income, goals, portfolio, decisions, outcomes |
| Cache | Redis | Session data, real-time market cache, model predictions |
| Advice Log | PostgreSQL | Closed-loop advice + outcome tracking |
| Audit Log | PostgreSQL | XAI decision explanations (regulatory) |

---

### 6. 📡 External Integrations

- **Market Data:** Yahoo Finance, NSE India, CoinGecko (crypto)
- **News:** Financial news APIs (Bloomberg, Reuters, MoneyControl)
- **Bank Data:** CSV import (Phase 1), UPI/banking API (Phase 2)

---

## 🔁 Data Flow — Key Flows

### Context Fusion Decision

```
User Request
  → API Gateway
  → Context Fusion Engine:
      Pull: user spending (DB) + market state (Redis) + goal urgency (DB)
      Compute: Tri-context vector C
      Fuse: Attention model
      Route: Decision output
  → XAI Engine: Generate explanation
  → Response: {action, confidence, explanation}
```

### Closed-Loop Learning Cycle

```
Advice Generated (t=0)
  → User accepts/rejects (t=+1h)
  → Outcome tracked (t=+30d, +60d, +90d)
  → Delta computed: did advice improve financial state?
  → Model weights updated (per user)
  → Next advice uses updated model
```

### Autonomous Copilot Flow

```
Background Daemon (async loop)
  → Monitor: spending threshold, market event, goal drift
  → Trigger: anomaly detected
  → Generate: action proposal {trigger, rationale, action, impact}
  → Queue: user notification
  → User: approve/dismiss via UI
  → Execute: backend API call
  → Log: outcome for closed-loop
```

---

## 🔄 Background Jobs & Event Bus

**Task Queue:** Celery + Redis Broker

| Job | Frequency | Description |
|---|---|---|
| Market Data Sync | Every 15 min | NSE / Yahoo Finance price refresh |
| Copilot Daemon | Continuous async | Anomaly monitoring |
| Behavioral Model Update | Daily | Re-train on new transaction data |
| Outcome Tracker | Daily | Check 30/60/90-day advice outcomes |
| Health Score Evolution | Daily | Refresh score trajectory projections |
| Closed-Loop Weight Update | Weekly | Update per-user recommendation weights |
| Alert Generation | Continuous | Budget, goal, and market alerts |

---

## 🔐 Security

| Layer | Mechanism |
|---|---|
| Authentication | JWT (JSON Web Tokens) |
| Data at Rest | AES encryption for sensitive fields |
| Input Handling | Pydantic schema validation |
| API Protection | Rate limiting (slowapi / nginx) |
| Audit Trail | Immutable XAI decision log |

---

## 📁 Full Project Structure (v2.0)

```
nexus/
├── frontend/
│   ├── src/
│   │   ├── pages/
│   │   │   ├── Dashboard.jsx
│   │   │   ├── Advisor.jsx
│   │   │   ├── Simulate.jsx
│   │   │   ├── Goals.jsx
│   │   │   ├── Portfolio.jsx
│   │   │   └── StressTester.jsx
│   │   └── components/
│   │       ├── ContextFusionCard.jsx
│   │       ├── CopilotPanel.jsx
│   │       └── HealthEvolutionChart.jsx
├── backend/
│   ├── main.py
│   ├── routes/             ← all API endpoints
│   ├── schemas/            ← Pydantic models
│   ├── services/           ← business logic
│   └── models/             ← ML model files
├── innovation/             ← NEW: Innovation Layer
│   ├── context_fusion.py
│   ├── adaptive_simulation.py
│   ├── copilot_daemon.py
│   ├── health_evolution.py
│   ├── behavioral_engine.py
│   ├── closed_loop.py
│   ├── risk_adapter.py
│   ├── goal_optimizer.py
│   ├── xai_engine.py
│   └── stress_tester.py
├── ai/
│   ├── classifier.py
│   ├── risk_scorer.py
│   ├── advisor.py
│   ├── shap_explainer.py
│   └── rlhf_updater.py
├── db/
│   ├── database.py
│   └── migrations/
├── jobs/
│   ├── celery_tasks.py
│   ├── copilot_daemon.py   ← async loop
│   └── outcome_tracker.py
└── config/
    └── settings.py
```

---

## 🚀 Tech Stack Summary (v2.0)

| Layer | Technology |
|---|---|
| Frontend | React + Tailwind CSS (dark cyberpunk) |
| Backend | FastAPI (Python) |
| Core ML | Scikit-learn, LSTM (PyTorch/Keras) |
| Explainability | SHAP |
| LLM | Claude API / Mistral / LLaMA (RAG) |
| Optimization | PuLP, SciPy |
| Time-Series | ARIMA, LSTM |
| Simulation | Monte Carlo (NumPy) |
| Database | PostgreSQL |
| Cache | Redis |
| Event Bus | Redis Streams + Celery |
| Real-Time Feeds | WebSocket (NSE, CoinGecko) |
| Auth | JWT |
| Market APIs | Yahoo Finance, NSE India, CoinGecko |
| Pattern Mining | mlxtend (sequential patterns) |

---

## 🔬 Research Contribution Summary

| Innovation | Research Area | Novelty |
|---|---|---|
| Context Fusion Engine | Multi-modal AI decision systems | Tri-context financial fusion |
| Adaptive Simulation | Stochastic financial modeling | Live-parameter Monte Carlo |
| Autonomous Copilot | AI agents, proactive systems | Event-driven financial daemon |
| Health Evolution Model | Predictive analytics | Behavioral + market-injected forecasting |
| Behavioral Learning | Behavioral economics + ML | Individual (not population) pattern mining |
| Closed-Loop Learning | Reinforcement learning | Outcome-tracked RLHF for finance |
| Risk Adaptation | Real-time risk management | Sub-minute VaR event-driven adaptation |
| Multi-Goal Optimization | Operations research | Pareto-optimal personal finance |
| XAI Layer | Explainable AI | SHAP-based financial decision transparency |
| Stress Testing | Financial resilience | Survival + recovery planning under shocks |

---

*NEXUS — Intelligent Financial OS | Architecture v2.0 | Research & Patent Edition*