# Final-Capstone
Capstone Project showcasing my end-to-end skills
# 📊 Data Analytics Portfolio

Project Workflow: Data ➡️ Data Cleaning & Preparation using SQL ➡️ EDR Diagram ➡️ Findings ➡️ Power BI Dashboard

---
## 🧠 Project Name: Sizwe Coffee (Pty) Ltd ➡️Revenue Analytics

---
## 🗺️ Overview

Find out what is happening to this business, then say where the next five million should go.

## 🎯 The problem

Sizwe Coffee closed FY2025 with R480 million of revenue, up 8.8% on the year before. On the face of it, a good year. The board does not think so. Gross margin fell from 34.7% to 33.0%. The overdraft was drawn on twice in a year when revenue grew. Nobody at the June board meeting could explain either, and the management pack did not help, because every segment and every channel in it looks roughly the same. Nomsa Dlamini, the Financial Director, has brought you in ahead of the strategy session in three weeks. She has given you the full dataset and two instructions. 

#### 📌 Hyphothesis Tested aimed at answering the question of what happened

- Hypothesis 1: Find out what is actually happening to this business. Not what the management pack says - what the data says. 
- Hypothesis 2: Then tell me where to put the next five million rand. I want a proposal I can take to the board: what we should do more of, what it is worth, and what could go wrong with it.
- Hypothesis 3: The second instruction is the one that matters. A diagnosis that ends without a recommendation is half a piece of work. .

----

## 💻 Tools & skills used

**Tools**
- Databricks (SQL)
- Power BI Desktop
- DAX
- Python for Data analytics
- GitHub

**Skills**
- SQL — CTEs, window functions, ranking
- DAX — time intelligence, ranking, customer cohort logic
- Data validation and reconciliation
- Data quality auditing and remediation
- Dashboard design
- Technical writing and documentation

## 📦 The dataset

Sizwe's financial year ends 30 June. FY2025 is 1 July 2024 to 30 June 2025. Control total. FY2025 revenue is R480,000,023.35. Prove it before you build anything on top of it.

| File | Rows | Description |
| ----------------------- | ------- | ---------------------------------------------------- |
| `Sales .csv` | sales_orders · sales_lines · products · customers · reps · rep_visits  |
| `Receivables.csv` | ar_ledger |
| `Commercial costs .csv` | listing_fees · trade_promotions  |
| `Finance .csv` | gl_transactions · chart_of_accounts · cost_centres · budget  |
| `Supply.csv` |Every till receipt issued in the period |

## Data Files

### Sales

https://github.com/kgolaganonaomi1-afk/Final-Capstone/commit/85d5961a1bf71dcf802d195a80584107da03aaab
sizwe_trade_promotions.csv
----

## 🗂️ Schema Diagram

----

Phase 1 - Understand the business (15 marks) 
Before you investigate anything, know what you are holding. 

###### 1.1 Produce an entity relationship diagram of the tables you intend to use. Primary keys, foreign keys, 
cardinality, and the grain of each table in one sentence. 

<img width="953" height="571" alt="image" src="https://github.com/user-attachments/assets/9a1222b5-a4ec-4bbd-ab8a-9e0ee3f599f6" />


Kgolagano Selebano <kgolaganonaomi1@gmail.com>
2:07 AM (0 minutes ago)
to naomi.selebano


----

## ⚠️ Data quality issues

----

###### 1.2 Profile the data. Row counts, date ranges, missing values, and anything that does not join the way 
you expected. Report every integrity gap you find and say whether it is a data quality problem or a real 
feature of how the business works. Both exist in here. All the data cleaning and Data preparation was done using SQL. There were 5 checks done overall and they include the following:

1. Checking for Duplicates in all tables: No duplicates were found in the data.
2. Checking for Null values: There were a lot of Null values in 3 tables: **Customers**, **Stores** and **Transactions** table.

<img width="422" height="142" alt="image" src="https://github.com/user-attachments/assets/b5413276-2df4-4362-b898-7aa8be61a411" />

So the decision on what to do with the Null Values was based on whether the information on Null values will affect any findings or insights we're trying to determine and also if the information can be determined using information from other tables.
- The missing Gender and Date of birth rows counted for 10% of the stores data and are original entered data when a customer signs up so there is no way to determine them from the rest of the data.
- The missing Store Manager name row counts for 2.2% of the stores data and it is original entered data and can't be confirmed from rest of the data.
- The missing Customer_id data from the transactions data counted for about 42.68% and although customer_id data can be found from the customers table, we don't have a way of tracing the transaction back to the customer.

**Final decision**: Keep the Null values in the data instead of replacing the data or deleting it from the tables especially the transactions because they contribute to the total revenue.

3. Check for Inconsistent casing: Western Cape and Gauteng provinces contain both upper case and lower cases. This was causing inaccurate results for provincial revenue analysis. So to fix the issue, standardized the cases using SQL. Data quality check SQL Code found in [`Data quality checks.md`]([sql/05_data_quality_checks.sql](https://github.com/mishsonjica-hash/Amanda-Sonjica/blob/main/Data%20quality%20checks.md))

###### 1.3 State your scope. Which tables you used, which you left out, and why.

## 📊 Dashboards

**Western Cape Analysis**:

<img width="747" height="467" alt="WC Dashboard" src="https://github.com/user-attachments/assets/6f3fcb2a-004d-45bb-be9c-95facd588abc" />

- 6 Store lost revenue and Transactions Count
- S010 is the highest revenue generating store in 2025 and March and April are the only months where revenue increased.

**Promo Impact Analysis**:

<img width="748" height="470" alt="Promo dashboaed" src="https://github.com/user-attachments/assets/f7cadb80-e155-45f6-86e1-eed210e72478" />

- "Buy 2 Get 1 Free on Iwisa" Promo run in April 2025 worked and revenue increased by R 7,045.44 and the average basket value rose by R 75.76. The promotion also increased Transaction count which means customers are spending more per visit during the promotional period.
- This also increased the number of units sold to 1238 and Transaction count to 1086.

**Products Analysis**:

<img width="748" height="462" alt="image" src="https://github.com/user-attachments/assets/042af4e3-5bdf-4f4d-a491-a096f6021b79" />

- Groceries is top category.
- Product name: Ladies Underwear 5-pack is the highest contributer of revenue in 2024 and 2025.
- In 2025, approximately 18k units sold.

[`PowerBi Dashboard`](https://github.com/mishsonjica-hash/Amanda-Sonjica/blob/main/Final%20project%202.pbix)

---

## 🔍 Key findings

----

1. **Revenue Decline Is Unique to Western Cape (Hypothesis 1 - Incorrect)**: The initial hypothesis that revenue dropped across all provinces was disproven. Revenue only declined in Western Cape by 5.79%, while all other provinces saw revenue increases year-over-year. This confirms that problem is within Western Cape and not shared across provinces.

2. **Transaction Count Drop Is the Primary Driver of Revenue change (Hypothesis 2 - Correct)**: The Western Cape revenue decline is directly linked to a 6.29% drop in transaction count. Customers in 2025 are buying less products than in 2024. However, it was observed that this decline is concentrated in just 6 stores (S011, S003, S012, S007, S002, and S010), with Store S010 experiencing the steepest decline at 26.13% in transactions and 25.24% in revenue.

3. **Customer Loyalty Tiers contributed in the Revenue Decline (Hypothesis 3 - Correct)**: All three loyalty tiers (Bronze, Silver, Gold) experienced transaction and revenue declines in Western Cape, making it the epicenter of customer churn. The Silver tier was hit hardest, losing 145 (14.46%) transactions and suffering a 10.46% revenue drop in Western Cape alone. Total transaction losses across all tiers in Western Cape amounted to 241 customers (90 Bronze + 145 Silver + 6 Gold). While Western Cape generates higher revenue and transactions counts, in comparison to other provinces, it had the highest revenue drop between 2024 and 2025

4. **Average Transaction Value Shows Mixed Impact**: While several Western Cape stores (S002, S007, S011, S012, S009, S005) saw a decline in average transaction spend - suggesting customers are buying cheaper products or spending less per visit - this was not the case for all stores. For example, Store S003 experienced a 10.66% revenue decline despite a 12.25% increase in average transaction value. This shows that average transaction value alone does not fully influence the revenue change; the drop in transaction volume remains the dominant factor.

5. **Promo Discount Analysis – "Buy 2 Get 1 Free on Iwisa" Was Effective**: The Power Promo run in April 2025 worked and revenue increased by R 7,045.44 and the average basket value rose by R 75.76. The promotion also increased Transaction count which means customers are spending more per visit during the promotional period.

8. **Product Category Effect**: The Groceries category remains the top revenue contributor (R 495,829.88 in 2024 → R 512,113.53 in 2025), but the Apparel category showed the most revenue growth at 14.22% YOY. Within Western Cape specifically, the Beverages subcategory generates the highest revenue compared to other categories and subcategories. This highlights an opportunity to leverage high-growth categories like Apparel and strong performers like Beverages to drive recovery strategies.

The findings are indepth explained in the [`Findings.md`](https://github.com/mishsonjica-hash/Amanda-Sonjica/blob/main/Findings.md)

---

## 🔍 Recommendations and Conclusion

----

- Since the Iwisa promotion in April 2025 proved effective, I would recommend that you replicate or create more promotional campaign targeting the underperforming stores in Western Cape.
- Since Transaction count directly affects the revenue growth, I would recommend that you create a monitoring system in Western Cape that targets transactions made per month to keep track of Revenue.
- Since the issue in Western Cape only affects a select few stores, the team must drive store-level initiatives that are aimed at increasing revenue. This includes internal investigation of operational issues of the affected stores.
- Given that the customer tier with reduced revenue amount is Silver tier, I would recommend creating more promos that include points in for Silver tier with the
-
-
-
- aim to win the customers lost back.


# Nova Retail Group — Sales Analytics

End-to-end retail analytics project: ERD design → SQL data warehouse → Power BI dashboards. Built for a fictional South African retail group to track revenue, product performance, and store operations across 10 stores in 5 provinces.

![Executive Dashboard](images/dashboard_executive.png)

---

## 📌 Table of contents

- [The problem](#-the-problem)
- [What I built](#-what-i-built)
- [Tools & skills used](#-tools--skills-used)
- [The dataset](#-the-dataset)
- [Data quality issues](#-data-quality-issues)
- [How to run this project](#-how-to-run-this-project)
- [Project structure](#-project-structure)
- [Data model](#-data-model)
- [Dashboards](#-dashboards)
- [Key findings](#-key-findings)
- [What I learned](#-what-i-learned)
- [References](#-references)
- [About me](#-about-me)

---

## 🎯 The problem

Nova Retail Group is a fictional South African retail business with 10 stores across Gauteng, Western Cape, KwaZulu-Natal, Eastern Cape, and the Free State. The leadership team had three problems:

1. **No single source of truth.** Sales data lived in different systems — point-of-sale, customer loyalty, and finance — and no one trusted the numbers when they were combined.
2. **No view across stores.** Each store manager could see their own performance, but no one at HQ could compare a flagship store in Sandton to an express store in Bloemfontein.
3. **No product insight.** They knew which products sold a lot of units, but not which categories drove the most revenue or where category performance differed by region.

The leadership team wanted a clean data model, repeatable SQL, and a self-service Power BI dashboard that would let them answer the [15 business questions](docs/business-questions.md) we identified up front.

---

## 🛠️ What I built

A complete analytics pipeline from raw schema design to executive-ready dashboards:

1. **Designed a star schema** with one fact table and four dimensions, optimised for analytical queries and Power BI performance.
2. **Built the database in PostgreSQL** with idempotent SQL scripts for schema, seed data, and ~50,000 generated transactions across 3 years.
3. **Ran a full data quality audit** — orphan keys, duplicates, range violations, casing, completeness — documented every issue and the resolution decision.
4. **Wrote 10 analytical SQL queries** covering revenue, product mix, customer segmentation, geographic performance, and discount impact.
5. **Built two Power BI dashboards** — an Executive Overview and a Product Performance dashboard — driven by 20+ DAX measures.
6. **Documented everything** so a new analyst could pick up the project and run it end-to-end in under an hour.

---

## 💻 Tools & skills used

**Tools**
- PostgreSQL 15 (could be ported to SQL Server or MySQL with minor changes)
- Power BI Desktop
- DAX
- VS Code with the SQLTools extension
- Git and GitHub

**Skills**
- Dimensional modelling (star schema design)
- SQL — CTEs, window functions, ranking, time intelligence
- DAX — time intelligence, ranking, customer cohort logic
- Data validation and reconciliation
- Data quality auditing and remediation
- Dashboard design — KPI hierarchy, audience-led layout, colour discipline
- Technical writing and documentation

---

## 📦 The dataset

The full dataset lives in [`data/`](data/) as five CSV files. It's **fully synthetic** — no real customer or sales data is included — but it's been generated to look and behave like a real retail dataset, with the natural skew you'd expect (Gauteng over-indexed, December peaks, year-on-year growth, mixed payment methods).

| File | Rows | Description |
| ----------------------- | ------- | ---------------------------------------------------- |
| `dim_date.csv` | 1,096 | Calendar: 2022-01-01 to 2024-12-31 |
| `dim_product.csv` | 20 | Products across Electronics, Apparel, Home, Beauty |
| `dim_store.csv` | 10 | Stores across 5 South African provinces |
| `dim_customer.csv` | 5,000 | Customers with loyalty tiers and demographics |
| `fact_sales.csv` | 50,000+ | Transactional sales at line-item grain |

**Key dataset characteristics:**

- 3 years of history, weighted to show realistic year-on-year growth (2022 → 2024)
- Strong December seasonality and softer Jan/Feb periods
- Electronics is the dominant category by revenue; gift cards and accessories are a small tail
- Gauteng and Western Cape over-indexed for revenue (mirroring real South African retail patterns)
- Loyalty tier distribution skews Bronze (most customers) with a small Platinum elite

You can analyse the CSVs directly in Excel, Python, or any BI tool. The SQL scripts in [`sql/`](sql/) load these into a PostgreSQL database for the full Power BI workflow.

---

## ⚠️ Data quality issues

This dataset is intentionally messy in the same ways real retail data is messy. Part of this project's value is showing how to **find, document, and handle** these issues before they reach a dashboard.

| Issue | Affected rows | Severity |
| ----------------------------------------------- | ------------- | -------- |
| Orphan `customer_key` in `fact_sales` | ~12 | Medium |
| Duplicate `sale_id` rows | ~8 | High |
| Negative `quantity` (returns mixed into sales) | ~25 | Medium |
| `discount_pct` outside the 0-100 range | ~5 | High |
| Missing `email` in `dim_customer` | ~250 (5%) | Low |
| Inconsistent casing in customer names | ~150 (3%) | Low |
| Leading/trailing whitespace in customer names | ~100 (2%) | Low |

Every issue is documented in [`docs/data-quality.md`](docs/data-quality.md) with:
- The SQL query to find it
- The decision on how to handle it (fix at source / fix in pipeline / flag and live with it)
- The downstream impact

The full set of automated data quality checks lives in [`sql/05_data_quality_checks.sql`](sql/05_data_quality_checks.sql) and runs before any analytical query.

---

## ⚙️ How to run this project

### Option 1 — Quick exploration (CSVs only)

If you just want to look at the data, the CSV files in `data/` open directly in Excel, Power BI, Python, or any SQL tool that supports CSV import. No database setup required.

### Option 2 — Full PostgreSQL workflow

**Prerequisites**
- [PostgreSQL 13+](https://www.postgresql.org/download/) installed locally or accessible
- [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (Windows only, free)
- A SQL client (DBeaver, pgAdmin, or `psql` from the terminal)

**Step 1 — Set up the database**

```bash
# Create a new database
createdb nova_retail

# Connect to it
psql nova_retail
```

Then, from inside `psql`, run the SQL files in order:

```sql
\i sql/01_create_schema.sql -- creates tables and indexes
\i sql/02_seed_data.sql -- inserts a small sample dataset
\i sql/03_generate_data.sql -- generates ~50,000 sales rows
\i sql/05_data_quality_checks.sql -- run this BEFORE the analysis
\i sql/04_analysis_queries.sql -- the 10 business queries
```

Alternatively, use `\COPY` to load the CSVs in `data/` directly into the tables created by `01_create_schema.sql`.

**Step 2 — Open the Power BI report**

1. Open `powerbi/nova_retail_dashboard.pbix` in Power BI Desktop.
2. When prompted, point the connection at your local `nova_retail` database.
3. Click **Refresh**.

> **Note on the .pbix file:** if you're viewing this on GitHub, the `.pbix` file is binary and won't render. Download it and open it in Power BI Desktop. The screenshots in this README show the dashboards as they appear when opened.

---

## 📁 Project structure

```
nova-retail-sales-analysis/
├── README.md ← You are here
├── LICENSE
├── .gitignore
│
├── data/
│ ├── dim_date.csv ← Calendar dimension (1,096 rows)
│ ├── dim_product.csv ← Product dimension (20 rows)
│ ├── dim_store.csv ← Store dimension (10 rows)
│ ├── dim_customer.csv ← Customer dimension (5,000 rows)
│ ├── fact_sales.csv ← Sales fact table (~50,000 rows)
│ └── README.md ← Notes on the synthetic dataset
│
├── sql/
│ ├── 01_create_schema.sql ← Tables, keys, indexes
│ ├── 02_seed_data.sql ← Small sample data
│ ├── 03_generate_data.sql ← Generate 50k sales rows
│ ├── 04_analysis_queries.sql ← The 10 business queries
│ └── 05_data_quality_checks.sql ← Automated DQ checks
│
├── powerbi/
│ ├── nova_retail_dashboard.pbix ← Power BI report file
│ ├── dax_measures.md ← All DAX measures documented
│ └── README.md ← How to open the .pbix file
│
├── images/
│ ├── erd_diagram.png ← Star schema diagram
│ ├── dashboard_executive.png ← Executive dashboard screenshot
│ └── dashboard_product.png ← Product dashboard screenshot
│
└── docs/
├── business-questions.md ← The 15 questions this project answers
├── data-dictionary.md ← Every table and column documented
├── data-quality.md ← All DQ issues, decisions, and impact
└── methodology.md ← How I built it, end to end
```

---

## 🗂️ Data model

The database uses a classic **star schema** with one fact table and four dimensions.

![ERD Diagram](images/erd_diagram.png)

**Why star schema?**

- Fast analytical queries (small number of joins)
- Native fit for Power BI's relationship engine
- Easy for non-technical stakeholders to read

**Grain of fact_sales:** one row per product line item per sale. This grain supports basket analysis, product mix, and per-line discount tracking.

Full details in [`docs/data-dictionary.md`](docs/data-dictionary.md).

---

## 📊 Dashboards

### Executive Sales Overview

Built for the CFO and CEO. Top-line KPIs, monthly trend, and breakdowns by province and category.

![Executive Dashboard](images/dashboard_executive.png)

**Designed to answer:**
- Are we growing year-on-year?
- Which provinces drive revenue, and which are underperforming?
- What does our category mix look like?

### Product Performance Dashboard

Built for buying and merchandising. Top products, category Pareto, and a category × province heatmap.

![Product Dashboard](images/dashboard_product.png)

**Designed to answer:**
- Which products drive the most revenue, and what's their unit volume?
- Does the Pareto principle (80/20) apply to our category mix?
- Where are the geographic gaps and opportunities by category?

---

## 🔍 Key findings

A few headline insights from the analysis (full details in [`sql/04_analysis_queries.sql`](sql/04_analysis_queries.sql)):

1. **Revenue grew ~12% year-on-year** to roughly R 248M in FY2024, ahead of the R 240M target.
2. **Gauteng dominates with ~36% of total revenue** but Western Cape has the highest revenue-per-store, suggesting an under-stored Gauteng market.
3. **Top 3 categories drive ~75% of revenue** (Electronics, Apparel, Home) — the Pareto principle clearly applies.
4. **Gross margin compressed by ~1.2 percentage points** — driven mostly by deeper discounting in the 11-20% band, which grew transactions but eroded margin.
5. **Platinum loyalty customers spend several times more per visit** than Bronze tier — strongest case for investing in loyalty upgrades.

---

## 📚 What I learned

- **Star schemas earn their reputation.** Once the model was right, the SQL queries practically wrote themselves and Power BI performance was excellent out of the box.
- **The grain decision matters more than the column list.** Picking line-item grain over transaction grain doubled the row count but unlocked basket analysis, product mix, and discount tracking — none of which would have been possible at the higher grain.
- **Validate before you visualise.** I built a small set of DQ queries (orphan keys, duplicates, range checks) before touching Power BI. They caught data issues that would have been invisible in the dashboards.
- **Document the data quality decisions, not just the data quality issues.** The issues themselves are easy to find; the value is in the *decision* you made about each one.
- **Documentation is part of the deliverable, not an afterthought.** Writing the methodology document while building it kept my decisions honest — and makes the project portable to the next analyst.

Things I'd improve next time are listed in the closing section of [`docs/methodology.md`](docs/methodology.md).

---

## 📖 References

Resources and references used while building this project:

- Kimball, Ralph. *The Data Warehouse Toolkit, 3rd Edition*. Wiley, 2013. (Star schema design and dimensional modelling.)
- Microsoft Learn: [DAX function reference](https://learn.microsoft.com/dax/)
- Microsoft Learn: [Power BI guidance and best practices](https://learn.microsoft.com/power-bi/guidance/)
- PostgreSQL Documentation: [Window functions](https://www.postgresql.org/docs/current/tutorial-window.html)
- SQLBI articles by Marco Russo and Alberto Ferrari — particularly their patterns on time intelligence and ranking measures
- Storytelling with Data, Cole Nussbaumer Knaflic — for dashboard layout and colour discipline

The Nova Retail Group dataset is fictional. All customer, sales, and store data was synthetically generated for this project. No real personal data is included.

---

## 👤 About me

I'm a data analyst building portfolio projects in SQL, Power BI, and analytics engineering.

- 🌐 Portfolio: [yourwebsite.com](https://yourwebsite.com)
- 💼 LinkedIn: [linkedin.com/in/yourname](https://linkedin.com/in/yourname)
- 📺 YouTube: [Data with Clarence](https://youtube.com/@datawithclarence)
- 📧 Email: you@email.com

If you found this project useful, give it a ⭐ on GitHub.

---

*Built as part of the Witle Academy Data Analytics Programme.*

## 📬 References

🔗[DAX function reference](https://learn.microsoft.com/dax/)

📘[Nova Retail Group — Sales Analytics by Clarence Mantiya](https://github.com/Clarence-Mantiya/test-project2/blob/main/README.md?plain=1) for Github layout


---

## ⭐ Let's Connect

- 💼 LinkedIn: www.linkedin.com/in/amanda-sonjica-b7a169104
- 📧 Email: mish.sonjica@gmail.com

I’m always open to suggestions, improvements, or collaboration ideas.

---
