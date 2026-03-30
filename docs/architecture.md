# 🧠 NEXUS Architecture

## 📌 Overview

NEXUS is an AI-powered financial intelligence system that integrates:

- Personal finance data
- Market data
- AI decision-making

The system follows a **modular, scalable architecture** designed for real-time insights and future expansion.

---

## 🏗️ High-Level Architecture

```
Frontend (Streamlit / React)
          ↓
FastAPI Backend (API Layer)
          ↓
Service Layer (Business Logic)
          ↓
AI Layer (ML + LLM)
          ↓
Database + External APIs
```

---

## 🧩 Core Components

### 1. 🎨 Frontend Layer

**Technologies:**
- Streamlit (MVP)
- React (future)

**Responsibilities:**
- User interaction
- Data visualization
- AI chat interface

---

### 2. ⚙️ Backend Layer (FastAPI)

**Responsibilities:**
- API routing
- Request validation
- Business logic execution

**Structure:**

```
backend/
├── routes/     → API endpoints
├── schemas/    → Request/response validation
└── services/   → Core business logic
```

---

### 3. 🧠 AI Layer

**Components:**

| Module | Description |
|---|---|
| Expense Classifier | ML model to auto-categorize transactions |
| Risk Scorer | ML model for portfolio risk assessment |
| Financial Advisor | LLM-powered chatbot for personalized advice |

**Technologies:**
- Scikit-learn (ML models)
- OpenAI / LLaMA / Mistral (LLM)

---

### 4. 🗄️ Database Layer

| Store | Technology | Purpose |
|---|---|---|
| Primary DB | PostgreSQL | Users, expenses, income, goals, portfolio |
| Cache | Redis | Session data, real-time market cache |

---

### 5. 📡 External Integrations

- **Market Data:** Yahoo Finance, NSE India
- **News:** Financial news APIs
- **Bank Data:** Optional CSV import

---

## 🔁 Data Flow

### Expense Tracking

```
User
  → Frontend
  → POST /add-expense
  → Service Layer (validation + logic)
  → PostgreSQL
  → Response
  → UI Update
```

### AI Advice

```
User Query
  → POST /chat
  → Fetch User Data (PostgreSQL)
  → Fetch Market Data (External API / Redis)
  → AI Engine (LLM)
  → Generate Personalized Advice
  → Return Response to UI
```

---

## 🧠 AI Integration Flow

```
User Financial Data ──┐
                      ├──▶ AI Engine ──▶ Insights & Recommendations
Market Data ──────────┘
```

**AI Engine Pipeline:**
1. Preprocess user + market data
2. Run ML models (classification, risk scoring)
3. Inject context into LLM prompt
4. Stream response back to frontend

---

## 🔄 Background Jobs

**Task Queue:** Celery + Redis Broker (or Cron Jobs for lightweight tasks)

| Job | Frequency | Description |
|---|---|---|
| Market Data Sync | Every 15 min | Fetch latest prices from NSE / Yahoo Finance |
| Alert Generation | Continuous | Trigger budget/goal alerts |
| Model Inference | On-demand / Scheduled | Run ML predictions on new data |

---

## 🔐 Security

| Layer | Mechanism |
|---|---|
| Authentication | JWT (JSON Web Tokens) |
| Data at Rest | AES encryption for sensitive fields |
| Input Handling | Pydantic schema validation (FastAPI) |
| API Protection | Rate limiting (slowapi / nginx) |

---

## 📁 Project Structure (Reference)

```
nexus/
├── frontend/
│   ├── streamlit_app.py        # MVP UI
│   └── react_app/              # Future React frontend
├── backend/
│   ├── main.py                 # FastAPI entrypoint
│   ├── routes/
│   │   ├── expenses.py
│   │   ├── chat.py
│   │   └── market.py
│   ├── schemas/
│   ├── services/
│   └── models/                 # ML model files
├── ai/
│   ├── classifier.py
│   ├── risk_scorer.py
│   └── advisor.py              # LLM chatbot logic
├── db/
│   ├── database.py
│   └── migrations/
├── jobs/
│   └── celery_tasks.py
└── config/
    └── settings.py
```

---

## 🚀 Tech Stack Summary

| Layer | Technology |
|---|---|
| Frontend | Streamlit → React |
| Backend | FastAPI (Python) |
| ML | Scikit-learn |
| LLM | OpenAI / LLaMA / Mistral |
| Database | PostgreSQL |
| Cache | Redis |
| Task Queue | Celery |
| Auth | JWT |
| Market APIs | Yahoo Finance, NSE |

---

*NEXUS — Intelligent Financial OS | Architecture v1.0*