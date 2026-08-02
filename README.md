# Banking Customer & Operations Analytics Dashboard

Interactive Power BI dashboard analyzing bank customer behavior, transactions, loans, and support performance.

## 📊 Overview

This project delivers a full banking analytics dashboard across 5 pages, built for a data analytics sprint. It covers customer activity, financial transactions, loan portfolio health, and customer support performance — with the goal of surfacing insights management can actually act on, not just raw numbers.

## 🗂️ Pages

- **Overview** — high-level KPIs across the whole bank (customers, transactions, balances, loans)
- **Customer Analysis** — active/inactive segmentation, transaction frequency, geographic distribution
- **Transaction Analysis** — trends by month, account type, season, and transaction type
- **Loan Analysis** — loan maturity schedule, interest rate distribution, loan type breakdown
- **Support Calls** — resolution rate, issue category breakdown, top-contact customers

## 🛠️ Tools & Techniques

- Power BI Desktop
- DAX (CALCULATE, USERELATIONSHIP, SWITCH, FORMAT, time intelligence)
- Custom Calendar table with inactive relationships for multi-fact-table date filtering
- Data cleaning in Power Query (data type conversion, locale handling)

## 🔑 Key Insights

- Customer support resolution rate is below 50%, indicating a process-level issue
- Loan maturities are concentrated in a specific upcoming period, requiring liquidity planning
- A significant share of customers are inactive, representing a re-engagement opportunity

## 📁 Files

- `banking.pbix` — the Power BI dashboard file
- `Project_Summary.md` — full write-up of insights, recommendations, and challenges
- `screenshots/` — preview images of each dashboard page

## 👤 Author

Abdelmonaem Elsayed — Data Analyst# banking-powerbi-dashboard
Interactive Power BI dashboard analyzing bank customer behavior, transactions, loans, and support performance
