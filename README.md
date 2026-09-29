# CRM & Call Center Analytics Dashboard – Power BI

## Project Overview

This project is an end-to-end CRM and Call Center Analytics solution developed using Microsoft Power BI.

The dashboard analyzes call activity, sales performance, agent performance, campaign performance, customer profiles, dispositions, and QA results.

The dataset used in this project is synthetic data generated using Python for portfolio and analytical practice. No real customer or organizational data is used.

The report contains five interactive analytical pages:

1. CRM Overview
2. Agent Performance
3. Campaign Analysis
4. Customer Insights
5. Call & Disposition Analysis

---

## Business Objective

The objective of this project is to provide a consolidated analytical view of CRM and call-center operations and help stakeholders monitor:

- Call volume and call outcomes
- Sales and conversion performance
- Agent and team performance
- Campaign performance
- Customer demographics and financial attributes
- Disposition trends
- QA pass/fail performance

---

## Tools & Technologies

- Microsoft Power BI
- Power Query
- DAX
- Data Modeling
- Python for synthetic data generation

---

## Dashboard Pages

### 1. CRM Overview

Provides a high-level view of CRM sales and call performance.

<a href = "https://github.com/Divakar30/CRM-Call-Center-Analytics-Power-BI/blob/main/01_CRM_Overview.png">View_CRM_OVerview</a>

### 2. Agent Performance

Analyzes agent-level and team-level performance.

<a href = "https://github.com/Divakar30/CRM-Call-Center-Analytics-Power-BI/blob/main/02_Agent_Performance.png">View_Agent_Performance</a>

### 3. Campaign Analysis

Analyzes campaign performance, dialing modes, monthly sales, and geographic sales distribution.

<a href = "https://github.com/Divakar30/CRM-Call-Center-Analytics-Power-BI/blob/main/03_Campaign_Analysis.png">View_Campaign_Analysis</a>

### 4. Customer Insights

Provides customer-level demographic and financial analysis.

<a href = "https://github.com/Divakar30/CRM-Call-Center-Analytics-Power-BI/blob/main/04_Customer_Insights.png">View_Customer_Insights</a>

### 5. Call & Disposition Analysis

Analyzes call outcomes, disposition trends, call attempts, and QA performance.

<a href = "https://github.com/Divakar30/CRM-Call-Center-Analytics-Power-BI/blob/main/05_Call_Disposition_Analysis.png">View_Call_Disposition_Analysis</a>

---

## Key Metrics

- Total Calls
- Answered Calls
- Answer Rate %
- Total Sales
- Sales Conversion %
- Total Customers
- Total Campaigns
- Average Talk Time
- Average Wrap Time
- Average Sales per Campaign
- Average Customer Age
- Average Annual Income
- Average Credit Limit
- Average Outstanding Amount

---

## Power BI Features Implemented

- Data Modeling and Relationships
- DAX Measures
- Power Query Transformations
- Synced Slicers
- Page Navigation
- Reset Filters using Bookmarks
- Drill-down
- Drill-through
- Report Page Tooltip
- Conditional Formatting
- Edit Interactions
- Visual-level Filters
- Page-level Filters
- Report-level Filters
- Top N Filtering
- Time Intelligence
- Geographic Analysis using Maps

---

## Important DAX Measures

**### Total Sales **

```DAX
Total Sales =
CALCULATE(
    COUNTROWS(Terminal_Records),
    Terminal_Records[Disp_Code] IN {1001, 1002}
)

### Sales Conversion %

```DAX
Sales Conversion % =
DIVIDE(
    [Total Sales],
    [Answered Calls],
    0
)

### Answer Rate %

```DAX
Answer Rate % =
DIVIDE(
    [Answered Calls],
    [Total Calls],
    0
)

### Previous Month Sales

```DAX
Previous Month Sales =
CALCULATE(
    [Total Sales],
    DATEADD(Date_Table[Date], -1, MONTH)
)

### Monthly Sales Change

```DAX
Monthly Sales Change =
[Total Sales] - [Previous Month Sales]

### Total Customers

```DAX
Total Customers =
DISTINCTCOUNT(Callable_Records[Mobile_No])

### Avg Annual Income

```DAX
Avg Annual Income =
AVERAGEX(
    VALUES(Callable_Records[Mobile_No]),
    CALCULATE(MAX(Callable_Records[Annual_Income]))
)

---

## Key Business Insights

- Approximately 74K calls were analyzed after excluding test campaign records.
- Around 58% of calls were answered.
- The dashboard recorded 4,367 successful sales with an overall sales conversion rate of approximately 10.15%.
- Customer analysis identified approximately 18.34K unique customers.
- Progressive dialing contributed the largest share of campaign sales compared with other dialing modes.
- Campaign performance varied across months, making monthly trend and month-over-month analysis useful for identifying changes in sales performance.
- Agent-level analysis showed differences in call volumes, sales, and conversion rates across teams and individual agents.
- Callback was one of the most frequent call dispositions.
- QA analysis was kept independent from campaign and call slicers because the QA dataset did not have a valid campaign filtering relationship.

---

## Project Highlights

- Designed a 5-page interactive CRM analytics report.
- Built customer-level and record-level metrics based on different data grains.
- Used a dedicated Date table for time-based analysis.
- Applied report-level filtering to exclude test campaign data.
- Implemented synchronized date slicers across transactional report pages.
- Created drill-through customer details and a campaign report-page tooltip.
- Used bookmarks to reset report filters.
- Applied conditional formatting to highlight agent conversion performance.

## Data Model & Tables Used

The report uses multiple related tables to separate master data, transactional data, customer data, and QA information.

Main tables used:

- **Agent_Master** – Agent details and team information
- **Call_History** – Call transactions, call status, talk time, wrap time, attempts, and dispositions
- **Campaign_Master** – Campaign, process, and dialing-mode information
- **Disposition_Master** – Disposition codes, categories, and disposition types
- **Callable_Records** – Customer and process-level callable records
- **Terminal_Records** – Successful/final disposition records used for sales calculation
- **QA_Verifier** – QA audit results and scores
- **Date_Table** – Dedicated calendar table used for time-based analysis

Relationships were created based on valid business keys so that filters propagate correctly between master and transactional tables.

---

## Project Conclusion

This project demonstrates an end-to-end Power BI solution for CRM and call-center analytics.

The report combines call activity, sales performance, agent productivity, campaign analysis, customer insights, dispositions, and QA performance into a single interactive dashboard.

The project also demonstrates practical Power BI concepts such as data modeling, DAX, filter context, time intelligence, bookmarks, drill-through, report-page tooltips, synchronized slicers, conditional formatting, and report-level filtering.

---

## Data Logic

- Customers are identified using unique mobile numbers.
- The same customer can appear in multiple campaigns.
- Each callable record has a separate unique record identifier.
- Customer-level metrics use unique customer logic.
- Record-level analysis uses callable record identifiers.

---

## Data Privacy

This project uses synthetic data generated using Python specifically for analytical and portfolio purposes.

No real customer, employee, banking, or organizational information is used or published in this repository.

Raw record-level datasets are intentionally not included in the public repository.
