# 🛡️ AuditSentinel

**The Future of AI Spend Governance.** Automated audit and risk assessment for the modern enterprise.

---

## 📝 Project Charter
AuditSentinel is designed for CFOs and IT Directors to regain control over "Shadow AI" spend. It transforms messy financial data into a structured governance report, identifying redundant subscriptions, data security risks, and immediate cost-saving opportunities.

### 🏗️ The "Clean-Exit" Tech Stack
This architecture is designed for high portability and logical isolation to facilitate future acquisition or scaling.

#### Frontend: Angular 19+ (Material 3 / Signals)

- _Hosting:_ Netlify (CDN-backed, atomic deployments).

#### Backend: Node.js (TypeScript)

- _Runtime:_ Railway or Render (Isolated Web Service).
- _Engine:_ Claude 4.6 (Sonnet) via Anthropic SDK.

#### Database: PostgreSQL (via Supabase)

- _Access:_ Row Level Security (RLS) enabled for multi-tenancy.

#### Identity: Supabase Auth or Clerk (SOC2 Compliant).

---

## 🧠 The Intelligence Engine (V1)
AuditSentinel uses a **Hybrid Deterministic-Probabilistic Engine** to classify spend.

**Normalization:** A TypeScript-based regex layer strips bank metadata (transaction IDs, location codes).

**Classification:** Claude 4.6 analyzes the cleaned string against a proprietary risk matrix.

**Governance Verdict:** The engine assigns a **Risk Score (0-100)** and a **Shadow AI Verdict.**

---

## 💾 Core Data Schema (MVP)
The following schema ensures strict data isolation and enterprise-grade reporting.

```sql
SQL
CREATE TABLE audit_results (
  id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
  user_id UUID REFERENCES auth.users(id),
  raw_description TEXT NOT NULL,
  vendor_name VARCHAR(255),
  estimated_monthly_spend DECIMAL(10,2),
  risk_score INTEGER CHECK (risk_score BETWEEN 0 AND 100),
  is_shadow_ai BOOLEAN DEFAULT FALSE,
  audit_note TEXT,
  created_at TIMESTAMPTZ DEFAULT NOW()
);
```

---

## 🚀 Execution Roadmap (Q1 2026)
[ ] **Phase 1:** Core CSV Parser & Claude 4.6 Integration (Current).

[ ] **Phase 2:** Angular Dashboard with "Waste Tracking" metrics.

[ ] **Phase 3:** Automated Security Whitepaper generation for users.
