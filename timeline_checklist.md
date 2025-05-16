# V1 Project Checklist as of June 7th, 2025

## 🟤 Step 1: Python API Extraction (Bronze)
- [✅] Finalize Plaid API call: `/transactions/get`, `/accounts/get`- Completed 2025-05-16
- [ ] Add pagination and date range logic
- [ ] Flatten response to DataFrames
- [ ] Save to:
  - [ ] `transactions.csv`
  - [ ] `accounts.csv`
  - [ ] `transactions_raw.json`
- [ ] Upload to `bronze.transactions_raw` and `bronze.accounts_raw`

## 🟤 Step 2: Load Raw to Database
- [ ] Set up SQLite or AWS RDS
- [ ] Create raw tables
- [ ] Write loader script for inserting raw data into DB

## ⚪ Step 3: Alteryx Subledger Path
- [ ] Load `transactions.csv` into Alteryx
- [ ] Modify to simulate discrepancies
- [ ] Output `subledger_transactions.csv`
- [ ] Load to DB as `alteryx.transactions_subledger`

## 🟣 Step 4: dbt Silver Layer (Staging Models)
- [ ] Initialize dbt project
- [ ] Configure `profiles.yml`
- [ ] Create models:
  - [ ] `stg_transactions.sql`
  - [ ] `stg_accounts.sql`
- [ ] Add tests in `schema.yml`

## 🟡 Step 5: dbt Gold Layer (Business Logic)
- [ ] `fct_monthly_spending.sql`
- [ ] `dim_accounts.sql`
- [ ] `fct_transaction_reconciliation.sql`
- [ ] Add match logic and tags

## 🟢 Step 6: Export Final CSV for Tableau
- [ ] Write `export_final_model.py`
- [ ] Export `fct_monthly_spending` and `fct_transaction_reconciliation` to CSV

## 🔵 Step 7: Tableau Dashboards
- [ ] Dashboard 1: Account Overview
- [ ] Dashboard 2: Reconciliation Summary

## 🟠 Step 8: Prefect Orchestration
- [ ] Install and configure Prefect
- [ ] Create `flow.py` to orchestrate all steps
- [ ] Add logging and optional scheduling

## ⚫ Step 9: Final Polish
- [ ] Clean up folder structure
- [ ] Write `README.md`
  - [ ] Project overview
  - [ ] Diagram + Medallion explanation
  - [ ] Setup instructions
  - [ ] Screenshots or Tableau links
- [ ] Add `.env_template`, `.gitignore`, `requirements.txt`
