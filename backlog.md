# Soul-Money CoPilot  
## Product Backlog  
Last updated: 2025-11-14

---

# 1. Epic: User Account & Identity

## 1.1 User Story: User Registration
**As a** new user  
**I want** to create an account via email or OAuth  
**So that** I can access the system securely.  

**Acceptance Criteria**
- Supports email/password and Google/Apple OAuth.
- Stores hashed passwords.
- Unique email validation.
- Returns JWT or session token.

**Priority:** P0

---

## 1.2 User Story: User Login
**As a** returning user  
**I want** to authenticate securely  
**So that** I can access my dashboard.  

**Acceptance Criteria**
- JWT authentication.
- Rate-limited login attempts.
- Generic error messages on failure.

**Priority:** P0

---

## 1.3 User Story: Profile Settings
**As a** user  
**I want** to update my timezone and notification settings  
**So that** my insights align with my daily routine.  

**Priority:** P1

---

# 2. Epic: Data Integrations (Health & Finance)

## 2.1 User Story: Connect Health Data Source
**As a** user  
**I want** to connect Apple Health, Oura, WHOOP, or Garmin  
**So that** biometric data can be synced.  

**Priority:** P0

---

## 2.2 User Story: Sync Biometric Data
**As a** system  
**I want** to import HRV, sleep, steps, and related metrics  
**So that** forecasts remain accurate.  

**Priority:** P0

---

## 2.3 User Story: Connect Financial Accounts
**As a** user  
**I want** to connect my bank or credit cards via Plaid  
**So that** the system can analyze my spending.  

**Priority:** P0

---

## 2.4 User Story: Sync Financial Transactions
**As a** system  
**I want** to import transactions including merchant, amount, category  
**So that** spending behavior is understood.  

**Priority:** P0

---

# 3. Epic: Mood Tracking

## 3.1 User Story: Manual Mood Entry
**As a** user  
**I want** to manually log my mood  
**So that** emotional data can be captured.  

**Priority:** P1

---

## 3.2 User Story: Mood Tagging
**As a** user  
**I want** to add emotional tags  
**So that** my logs are more contextualized.  

**Priority:** P1

---

## 3.3 User Story: AI Mood Inference
**As a** system  
**I want** to infer mood patterns from behavior  
**So that** missing entries can be supplemented.  

**Priority:** P2

---

# 4. Epic: Pattern Recognition Engine

## 4.1 User Story: Detect Correlations
**As a** system  
**I want** to identify correlations between biometrics, mood, and spending  
**So that** insights can be generated.  

**Priority:** P0

---

## 4.2 User Story: Detect Behavioral Triggers
**As a** system  
**I want** to detect triggers (e.g., low HRV → overspending)  
**So that** the user can be warned.  

**Priority:** P1

---

## 4.3 User Story: Detect Dysregulation Loops
**As a** system  
**I want** to detect loops such as poor sleep → emotional drop → spending spike  
**So that** early interventions can be delivered.  

**Priority:** P1

---

# 5. Epic: Daily Energy–Money Forecast

## 5.1 User Story: Generate Daily Forecast
**As a** system  
**I want** to compute daily Energy and Money Regulation scores  
**So that** users know their likely regulation capacity.  

**Priority:** P0

---

## 5.2 User Story: Provide Overall Daily State
**As a** user  
**I want** a simple Green/Yellow/Red indicator  
**So that** I can understand my state quickly.  

**Priority:** P0

---

## 5.3 User Story: Daily Summary Notification
**As a** user  
**I want** to receive a morning summary  
**So that** I can plan my day.  

**Priority:** P1

---

# 6. Epic: Micro-Interventions

## 6.1 User Story: Biometric-Based Alerts
**As a** user  
**I want** alerts when HRV or sleep drops  
**So that** I can self-regulate before overspending.  

**Priority:** P0

---

## 6.2 User Story: Spending-Based Alerts
**As a** user  
**I want** nudges when spending spikes  
**So that** I can pause and reflect.  

**Priority:** P0

---

## 6.3 User Story: Mood-Based Alerts
**As a** user  
**I want** supportive prompts during emotional drops  
**So that** I avoid using spending as emotional regulation.  

**Priority:** P1

---

## 6.4 User Story: Pre-Purchase Intervention
**As a** user  
**I want** a gentle notice before large discretionary purchases  
**So that** I can make conscious decisions.  

**Priority:** P2

---

# 7. Epic: Weekly Review

## 7.1 User Story: Weekly Pattern Summary
**As a** user  
**I want** a weekly report of patterns  
**So that** I can see connections between mood, energy, and money.  

**Priority:** P1

---

## 7.2 User Story: Weekly Recommendations
**As a** user  
**I want** recommended rituals and behavioral adjustments  
**So that** I can stabilize upcoming weeks.  

**Priority:** P2

---

# 8. Epic: Monthly Rebalancing

## 8.1 User Story: Monthly Trend Analysis
**As a** user  
**I want** to see monthly emotional, biometric, and financial patterns  
**So that** I can understand long-term trends.  

**Priority:** P2

---

## 8.2 User Story: Monthly Energy ROI
**As a** user  
**I want** to understand which spending categories restore vs drain energy  
**So that** I can optimize my money habits.  

**Priority:** P2

---

# 9. Epic: AI Coaching Mode

## 9.1 User Story: Ask CoPilot Questions
**As a** user  
**I want** to ask CoPilot questions about my emotional or financial state  
**So that** I can get guidance.  

**Priority:** P1

---

## 9.2 User Story: Contextual Coaching
**As a** user  
**I want** coaching that is tailored to my current state  
**So that** I feel supported in real-time.  

**Priority:** P1

---

## 9.3 User Story: Reflection Prompts
**As a** user  
**I want** guided reflection prompts  
**So that** I can develop awareness.  

**Priority:** P2

---

# 10. Epic: Data Security & Compliance

## 10.1 User Story: Secure Data Storage
**As a** system  
**I want** all data encrypted  
**So that** the user’s sensitive information is protected.  

**Priority:** P0

---

## 10.2 User Story: Privacy Dashboard
**As a** user  
**I want** to see what data is stored  
**So that** I can maintain transparency.  

**Priority:** P2

---

## 10.3 User Story: Delete My Data
**As a** user  
**I want** to delete my account and data  
**So that** I remain in control.  

**Priority:** P1

---

# 11. Epic: Notifications & Settings

## 11.1 User Story: Customize Notifications
**As a** user  
**I want** to choose which alerts I receive  
**So that** I avoid notification fatigue.  

**Priority:** P1

---

## 11.2 User Story: Adjust Forecast Time
**As a** user  
**I want** to set the time I receive daily forecasts  
**So that** timing aligns with my schedule.  

**Priority:** P1

---

# 12. Epic: Future Extensions

## 12.1 User Story: Couples Mode
**As a** couple  
**We want** synced emotional-financial insights  
**So that** we can regulate and budget together.  

**Priority:** P3

---

## 12.2 User Story: Biomarker Integrations
**As a** user  
**I want** to connect lab results or biomarkers  
**So that** I can deepen my health-finance insights.  

**Priority:** P3

---

## 12.3 User Story: Pre-Purchase Browser Plugin
**As a** user  
**I want** a browser extension for real-time pause moments  
**So that** I can make conscious shopping decisions.  

**Priority:** P3

---

# Backlog Summary Table

| Epic | Stories | Priority |
|------|---------|----------|
| User Identity | 3 | P0 |
| Health Integrations | 2 | P0 |
| Financial Integrations | 2 | P0 |
| Mood Tracking | 3 | P1 |
| Pattern Engine | 3 | P0/P1 |
| Daily Forecast | 3 | P0 |
| Micro-Interventions | 4 | P0/P1 |
| Weekly Review | 2 | P1/P2 |
| Monthly Review | 2 | P2 |
| Coaching Mode | 3 | P1/P2 |
| Security | 3 | P0/P1 |
| Notifications | 2 | P1 |
| Future Extensions | 3 | P3 |
