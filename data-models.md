# Data Models
## Soul-Money CoPilot
Core data schema for biometric, spending, mood, correlation, and forecasting systems.

---

# 1. Entity Relationship Overview

Entities:

- `users`
- `biometric_records`
- `financial_transactions`
- `mood_logs`
- `daily_forecasts`
- `micro_interventions`
- `weekly_summaries`
- `monthly_summaries`
- `correlation_insights`
- `settings`
- `integrations`

All timestamps are UTC unless otherwise specified.

---

# 2. Users

| Field | Type | Description |
|-------|------|-------------|
| id | UUID (PK) | Unique user ID |
| email | string | User email (unique) |
| password_hash | string | Hashed password or OAuth token reference |
| created_at | datetime | Account creation timestamp |
| updated_at | datetime | Last update |
| last_login_at | datetime | Last login |
| timezone | string | e.g., "America/Los_Angeles" |
| hrv_baseline | integer | User-specific HRV baseline (optional) |

---

# 3. Biometric Records

Represents physiological state from Apple Health, Oura, WHOOP, etc.

| Field | Type | Description |
|-------|------|-------------|
| id | UUID (PK) |
| user_id | UUID (FK → users.id) |
| source | enum("apple_health", "oura", "whoop", "garmin") |
| timestamp | datetime |
| hrv | integer (ms) |
| resting_hr | integer |
| sleep_score | integer (0–100) |
| sleep_duration | integer (minutes) |
| steps | integer |
| temperature_variance | float |
| stress_score | integer (optional) |

Indexes: `(user_id, timestamp)`

JSON representation:

```json
{
  "timestamp": "2025-01-01T08:00:00Z",
  "hrv": 52,
  "resting_hr": 58,
  "sleep_score": 87,
  "steps": 8421
}

4. Financial Transactions
Pulled from Plaid or manual.
Field	Type	Description
id	UUID (PK)	
user_id	UUID (FK)	
date	date	
merchant	string	
category	string	
amount	decimal	
currency	string	
transaction_type	enum("debit", "credit")	
source	enum("plaid", "manual")	
is_recurring	boolean	
notes	string	
Indexes: (user_id, date) and (user_id, category)

5. Mood Logs
Field	Type
id	UUID (PK)
user_id	UUID (FK)
timestamp	datetime
mood	integer (1–10)
emotional_tags	array<string>
notes	string
inferred	boolean (true if AI-generated)
Mood examples: “anxious”, “tired”, “overstimulated”, “calm”, “hopeful”.

6. Daily Forecasts
Represents predicted energy and spending regulation for the current or coming day.
Field	Type
id	UUID
user_id	UUID
date	date
energy_score	integer (0–100)
money_regulation_score	integer (0–100)
overall_state	enum("green", "yellow", "red")
confidence	integer (0–100)
summary	string
JSON structure:
{
  "date": "2025-01-18",
  "energy_score": 72,
  "money_regulation_score": 64,
  "overall_state": "yellow",
  "confidence": 82
}

7. Micro-Interventions
Field	Type
id	UUID
user_id	UUID
timestamp	datetime
trigger_type	enum("biometric_drop", "spend_spike", "mood_drop", "predictive_risk")
message	string
action_suggested	string
viewed	boolean
clicked	boolean
Example:
{
  "trigger_type": "biometric_drop",
  "message": "HRV low. Delay discretionary spending for 24 hours."
}

8. Weekly Summaries
Field	Type
id	UUID
user_id	UUID
week_start	date
mood_trend	string
financial_trend	string
biometric_trend	string
triggers_identified	array<string>
stabilizers_identified	array<string>
recommendations	string

9. Monthly Summaries
Field	Type
id	UUID
user_id	UUID
month	string (YYYY-MM)
emotional_pattern_summary	string
financial_pattern_summary	string
biometric_summary	string
energy_roi_analysis	json
recommended_protocols	string

10. Correlation Insights
Field	Type
id	UUID
user_id	UUID
created_at	datetime
variable_x	string
variable_y	string
correlation_strength	float
correlation_confidence	integer
explanation	string
Example:
{
  "variable_x": "hrv",
  "variable_y": "food_delivery_spend",
  "correlation_strength": -0.62,
  "correlation_confidence": 88,
  "explanation": "Lower HRV predicts increased delivery spending within 24 hours."
}

11. Settings
User preferences.
Field	Type
id	UUID
user_id	UUID
notifications_enabled	boolean
daily_forecast_time	string
currency	string
spending_alert_threshold	decimal
mood_prompt_frequency	enum("daily", "2x_daily", "manual")

12. Integrations
Field	Type
id	UUID
user_id	UUID
provider	enum("plaid", "apple_health", "oura", "whoop", "garmin")
access_token	encrypted string
refresh_token	encrypted string
connected_at	datetime
status	enum("active", "error", "revoked")

13. Suggested Folder Structure
/docs
  ├── prd.md
  ├── data-models.md
  ├── architecture.md
  ├── user-flows.md
  └── api.md

/src
  /models
  /services
  /controllers
  /integrations
  /utils
