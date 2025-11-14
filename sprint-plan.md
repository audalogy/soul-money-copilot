# Soul-Money CoPilot  
## Sprint Plan (Solo Engineer, Cursor Workflow)  
Duration: 6–8 Weeks  
Resource: 1 Full-Stack Engineer  
Mode: Single Cursor Window

---

# Overview
This sprint plan provides a complete, sequenced roadmap to build an MVP of Soul-Money CoPilot inside **Cursor**, optimized for a single engineer.  
Each sprint includes:

- Goals  
- Deliverables  
- Engineering tasks  
- Testing checkpoints  
- Cursor instructions (branching, prompts, file creation order)

---

# SPRINT 0 — Foundation & Environment  
**Duration:** 2–3 days  
**Goal:** Set up the repo, folder structure, frameworks, scaffolding, and tooling.

### Deliverables
- GitHub repo initialized  
- `/src` + `/docs` scaffolding  
- Backend framework chosen (Node/Express, Python/FastAPI, or Next.js API routes)  
- Frontend scaffold (Next.js recommended)  
- Database chosen + migrations initialized (Postgres recommended)  
- Environment variables & secrets management set up  
- Cursor workspace ready with dev commands

### Engineering Tasks
1. Create GitHub repo: `soul-money-copilot`
2. Add `/docs`:  
   - `prd.md`  
   - `data-models.md`  
   - `backlog.md`  
   - `architecture.md` (placeholder)  
3. Scaffold app:  
   - `npx create-next-app@latest`  
4. Create backend folder if separate:  
   - `/src/backend`  
5. Initialize Postgres schema using Prisma or Knex.
6. Setup `.env.example` (NO secrets).

### Cursor Instructions
- “Generate initial folder structure from sprint plan.”  
- “Create Postgres schema + Prisma config using data-models.md.”

---

# SPRINT 1 — User Accounts & Basic UI  
**Duration:** 1 week  
**Goal:** Authentication + foundational UI shell.

### Deliverables
- User registration  
- Login/logout flow  
- Auth-protected routes  
- Basic dashboard layout  
- Profile settings page (timezone + notifications)

### Engineering Tasks
**Backend**  
- Create `users` model (UUID)  
- Implement auth endpoints:  
  - `POST /auth/register`  
  - `POST /auth/login`  
- Add JWT session middleware  
- Store timezone and preferences  

**Frontend**  
- Auth pages (Login, Register)  
- Dashboard layout (`/dashboard`)  
- Profile settings UI  

### Testing
- Create -> login -> access protected route  
- Update and persist timezone  

### Cursor Instructions
- “Generate Next.js pages for login + register using JWT backend.”  
- “Create middleware for protected routes.”  

---

# SPRINT 2 — Integrations Layer (Plaid + Health Providers)  
**Duration:** 1–1.5 weeks  
**Goal:** Connect to external data sources and store imported data.

### Deliverables
- Plaid integration (sandbox first)  
- Apple Health / Oura import endpoints  
- `integrations` and `biometric_records` tables  
- Background job for syncing data (cron or simple manual trigger)

### Engineering Tasks
**Plaid**  
- OAuth connection  
- `POST /integrations/plaid/connect`  
- `GET /transactions/sync`  

**Health Providers**  
- Data ingestion endpoints:  
  - `/biometrics/import/apple`  
  - `/biometrics/import/oura`  
- Store sleep, HRV, HR, steps, temp variance  

### UI  
- Integrations settings page  
- “Connected / Not Connected” states

### Testing
- Test Plaid sandbox transactions  
- Test sample biometric JSON payload  

### Cursor Instructions
- “Generate Plaid service layer + transaction sync function.”  
- “Create UI panel with connect buttons and status badges.”  

---

# SPRINT 3 — Mood Logging + Mood Model  
**Duration:** 4–5 days  
**Goal:** Capture user mood and emotional tags.

### Deliverables
- Mood logging page  
- Mood tags (chips/buttons)  
- `mood_logs` table  
- Optional: AI-inferred mood prototype

### Engineering Tasks
- Create `POST /mood` endpoint  
- Build mood UI (1–10 slider + tags)  
- Store emotional tags as an array  
- Optional: API for inferred mood using LLM  

### Testing
- Add mood entries  
- Validate time-based queries  

### Cursor Instructions
- “Generate mood logging component + endpoint using data-models.md.”  

---

# SPRINT 4 — Pattern Recognition Engine (MVP)  
**Duration:** 1–1.5 weeks  
**Goal:** Detect basic correlations between biometrics, mood, and spending.

### Deliverables
- Batch job: compute correlations nightly  
- Store in `correlation_insights` table  
- First version of insights engine  
- Ability to detect:  
  - Low HRV → Spending spike  
  - Low sleep → Low mood  
  - Mood dips → Delivery spend  
  - Stress → impulse purchases  

### Engineering Tasks
- Implement scheduled job using Cron or serverless scheduler  
- Create correlation service:  
  - Pearson correlation  
  - Rolling averages  
  - Threshold detection  
- Insert insights with confidence score

### UI
- Insights section in dashboard  
- Insight drill-down modal

### Testing
- Synthetic data correlation test  
- Insight confidence thresholds manually validated  

### Cursor Instructions
- “Generate correlation engine using Postgres and TypeScript.”  
- “Create nightly job reading biometrics, mood, and transaction tables.”  

---

# SPRINT 5 — Daily Energy–Money Forecast Engine  
**Duration:** 1 week  
**Goal:** Build daily forecast: Energy Score, Money Regulation Score, and Daily State.

### Deliverables
- Forecast job that runs each morning  
- `daily_forecasts` table  
- Algorithm v1:  
  - HRV deviation  
  - Sleep deficit  
  - Mood delta  
  - Spend trend  
- Overall state: Green / Yellow / Red  
- Daily summary on dashboard

### Engineering Tasks
- Implement scoring system (simple weighted average)  
- Store forecast + confidence  
- Expose `/forecast/today` endpoint  
- Render forecast card on dashboard

### Testing
- Create fake HRV, sleep, and mood to validate scoring  

### Cursor Instructions
- “Generate weighted scoring function using data-model models.”  

---

# SPRINT 6 — Micro-Interventions  
**Duration:** 1 week  
**Goal:** Real-time and scheduled nudges based on state changes.

### Deliverables
- Trigger engine  
- Micro-intervention rules:  
  - Low HRV  
  - High discretionary spend  
  - Mood drop  
  - Negative trend  
- `micro_interventions` table  
- Notification delivery (email or in-app)

### Engineering Tasks
- Create rule engine  
- Write trigger conditions  
- Write intervention messages  
- Store events  
- UI feed for interventions  

### Testing
- Trigger interventions with simulated state  

### Cursor Instructions
- “Create rule engine that runs every hour + stores interventions.”  

---

# SPRINT 7 — Weekly & Monthly Reviews  
**Duration:** 1 week  
**Goal:** Summaries and pattern insights over time.

### Deliverables
- Weekly summary generator  
- Monthly summary generator  
- `weekly_summaries` and `monthly_summaries` tables  
- Summary cards on dashboard

### Engineering Tasks
- Implement aggregate queries  
- Run batch summaries  
- Build UI (accordion or simple report page)

### Cursor Instructions
- “Generate SQL aggregation queries for weekly + monthly summaries.”  

---

# SPRINT 8 — AI Coaching Mode (MVP)  
**Duration:** 1 week  
**Goal:** Build a contextual AI chat mode that pulls from user state.

### Deliverables
- AI endpoint: `/copilot/chat`  
- Context injection:  
  - Recent mood  
  - Biometric trends  
  - Spending trends  
  - Daily forecast  
  - Latest insights  
- Simple chat UI  

### Engineering Tasks
- Build prompt template  
- Integrate with OpenAI or local LLM  
- Build chat bubble UI  
- Store history (optional)

### Testing
- Validate contextual behavior  
- Test fallback states  

### Cursor Instructions
- “Generate coach prompt that uses forecast + correlations as input.”  

---

# RELEASE MILESTONE — MVP  
**Duration:** End of Sprint 8  
**Goal:** Deploy the MVP and onboard the first user (you).

### Deployment Deliverables
- Production database  
- Backend deployed (Railway, Render, Vercel)  
- Frontend deployed (Vercel)  
- Secrets stored in environment  
- Basic error monitoring  
- Versioned API

---

# Optional Post-MVP Sprints  
**If time allows:**  
- Browser pre-purchase extension  
- Couples mode  
- Biomarker integrations  
- Energy ROI category scoring  
- Advanced ML forecasting  

---

# Recommended Cursor Workflow  
1. Work in a single window.  
2. Keep `prd.md`, `data-models.md`, and `backlog.md` in sidebar for context.  
3. Use branches for each sprint:  
   - `sprint-1-auth`  
   - `sprint-2-integrations`  
4. Keep Cursor “diff mode” active for code audits.  
5. Use iterative prompts:  
   - “Refactor the forecast engine for clarity.”  
   - “Generate validation for mood logs.”  
   - “Add error handling to Plaid service.”

---

# End of sprint-plan.md
