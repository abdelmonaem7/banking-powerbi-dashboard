# Banking Customer & Operations Analytics — Project Summary

## Dashboard Overview

The final dashboard consists of **5 pages** (Overview, Customer, Transaction, Loan, Support Calls) with a consistent sidebar navigation and bank branding, each page featuring KPI cards with year-over-year (vs PY) comparisons, slicers for interactive filtering (LoanType, TransactionType, AccountType, IssueType, Loan_status, Year), and supporting visuals tailored to that business area.

---

## Key Insights

**Overview**
- Core KPIs (customers, transactions, transaction amount, balance, loan amount) are all tracked with year-over-year comparisons, giving management an immediate read on growth or decline.
- Account balances and transaction volume are fairly balanced across account types (Checking, Business, Savings), with no single account type dominating.
- Loan status and support call resolution are surfaced on the main landing page, making operational health visible at a glance without drilling into sub-pages.

**Customer Analysis**
- Customer activity is segmented into **Active vs. Inactive**, with frequency further broken down into Low, Medium, High, and "Never Transacted" — this makes it possible to isolate at-risk or dormant customers directly, not just count them.
- A geographic breakdown (customers/transactions by State) highlights where the customer base is concentrated.
- A declining monthly customer trend line is visible in some filtered views, which is worth monitoring at the unfiltered/portfolio level.

**Transaction Analysis**
- Transactions are analyzed across three angles simultaneously: **time (monthly trend)**, **account type**, and **seasonality** — the seasonal breakdown (Fall, Summer, Spring, Winter) is fairly even, meaning transaction activity isn't strongly seasonal.
- Transaction type breakdown (Transfer, Payment, Deposit, Withdrawal) shows Transfers as the most frequent type, followed closely by Payments.

**Loan Analysis**
- The **Loan Maturity Schedule** clearly shows a concentration of loan maturities peaking between **2027 and 2029**, tapering off toward 2032 — a critical input for liquidity and capital planning.
- Interest rates range from **~2.5% to ~12.7%**, with a weighted average around **7.5%**, and average rates vary meaningfully by loan type (Home and Personal loans carry higher average rates than Business loans).
- Loan volume by type is uneven — Education, Car, and Personal loans make up the bulk of the portfolio, while Business loans are a very small share by count (though not necessarily by value).

**Support Calls**
- The overall **resolution rate hovers around 40–49%**, depending on the filter applied — consistently below half, confirming this is a genuine operational gap rather than a one-off.
- Issue categories are fairly evenly distributed (Loan Query, Account Access, Card Issue, Transaction Dispute), so no single issue type explains the majority of call volume.
- Resolution performance varies noticeably by issue type — **Card Issue consistently resolves at the lowest rate**, while Account Access and Loan Query resolve more successfully.
- A ranked customer table surfaces the highest-contact customers, useful for identifying recurring service failures at the individual level.

---

## Business Recommendations

1. **Prioritize process improvements for Card Issue resolution.** This category consistently underperforms other issue types in resolution rate and should be the first target for root-cause analysis.

2. **Build a liquidity plan anchored to the 2027–2029 loan maturity peak.** This window will require the largest capital inflow/reinvestment planning; starting preparation early reduces refinancing risk.

3. **Launch a targeted re-engagement program for inactive and "Never Transacted" customers**, since this segment appears substantial and represents both churn risk and untapped activity.

4. **Investigate the sub-50% support resolution rate as a systemic issue**, not a per-category problem — since it holds fairly consistently across issue types and filters, the cause is likely structural (staffing, process, or tooling) rather than isolated to one team.

5. **Review pricing on higher-interest-rate loan types** (Home, Personal) to confirm the rate premium is justified by risk, rather than simply legacy pricing.

6. **Use the ranked "top contact" customer table proactively** — customers appearing repeatedly in support calls are early indicators of either product friction or churn risk, and are worth a direct outreach process.

---

## Challenges Faced During the Project

- **Data type inconsistencies:** Key date fields (e.g., TransactionDate) were imported as text and required explicit conversion to the Date type, including handling locale-specific date formats to avoid conversion errors.

- **Ambiguous relationship paths in the data model:** Connecting a custom Calendar table to multiple fact tables (Transactions, SupportCalls) created ambiguous relationship paths, since some tables were already indirectly connected through other tables (e.g., Customers → Accounts → Calendar). This was resolved using **inactive relationships combined with `USERELATIONSHIP()`** in DAX rather than forcing multiple active relationships, which Power BI does not allow.

- **Date logic breaking on historical data:** Measures originally built using `TODAY()` (for identifying inactive customers or upcoming loan maturities) returned misleading results because the dataset's date range didn't align with the current system date. This was corrected by anchoring calculations to the **maximum date present in the data** instead.

- **Formatting issues when combining text and numeric values:** Concatenating a percentage measure with descriptive text (e.g., "vs PY") using `&` stripped the number's formatting, producing raw scientific notation. This required explicit use of `FORMAT()` before concatenation, and separating "value" and "label" elements in card visuals to control color independently.

- **Top N filtering with tied values:** Applying Top N filters (e.g., top 10 customers by call count) surfaced more rows than expected due to tied values at the cutoff point, requiring either a tie-breaker measure or a practical visual workaround (resizing the table).

- **Data source permission/refresh issues:** A data source privacy/permission setting unexpectedly blocked part of the refresh pipeline, requiring a review and reset of Data Source Settings to restore full report functionality.

---

*This summary reflects the final state of the Banking Customer & Operations Analytics Power BI project (Sprint 2), covering all five report pages: Overview, Customer, Transaction, Loan, and Support Calls.*
