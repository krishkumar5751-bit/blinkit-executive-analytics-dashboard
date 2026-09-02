# 🛒 Blinkit Quick-Commerce Executive Analytics & Strategy Suite

[![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![DAX](https://img.shields.io/badge/DAX-Data_Analysis_Expressions-0078D4?style=for-the-badge)](https://learn.microsoft.com/en-us/dax/)
[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Machine_Learning-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)](https://scikit-learn.org/)
[![Status](https://img.shields.io/badge/Status-Production_Ready-success?style=for-the-badge)]()

An enterprise-grade, end-to-end Power BI business intelligence suite analyzing **64,325+ transactions** across metro dark-store operations, customer lifetime value (LTV), delivery fleet SLA compliance, and gross platform margins for Blinkit.

---

## 📌 Executive Summary

Quick-commerce retail depends on split-second order routing, micro-warehouse inventory availability, and tight delivery turnaround times (<15 mins). This analytics suite bridges raw transactional data with operational strategy across 4 core dimensions:
1. **Financial Performance:** Platform gross revenue of **₹14.03M** with an **AOV of ₹218.17**.
2. **Behavioral Customer Segmentation:** Unsupervised machine learning (**RFM + K-Means clustering, $k=4$**) categorizing users into actionable retention cohorts.
3. **Fulfillment Logistics:** Hourly demand stress-testing, SLA compliance (**36.5% sub-15m target**), and payment channel splits (**UPI driving >45% volume**).
4. **Fleet Optimization:** City-level fleet performance benchmarks evaluating 682 active delivery partners.

---

## 🛠️ Complete Tech Stack & Tools

| Layer | Technologies & Tools | Implementation Details |
| :--- | :--- | :--- |
| **Business Intelligence** | **Power BI Desktop**, Power BI Service | 4-page interactive reporting suite, custom corporate UI theme, dynamic page navigation, cross-filtering slicers. |
| **Data Modeling** | **Tabular Data Modeling (VertiPaq)** | Star Schema architecture: 1 centralized Fact table (`Fact_Orders`) connected via `1-to-Many` relationships to dimension tables. |
| **Calculations & Logic** | **DAX (Data Analysis Expressions)** | Time-intelligence measures, dynamic multi-tier aggregations, weighted average delivery times, fulfillment rates, and KPI cards. |
| **Machine Learning** | **Python (Pandas, NumPy, Scikit-Learn)** | RFM feature engineering, log-transformation, standard scaling, and K-Means clustering ($k=4$) for customer segmentation. |
| **Version Control & CI** | **Git / GitHub** | Repository versioning, documentation architecture, asset tracking. |

---

## 🗄️ Data Model Architecture (Star Schema)

The underlying model is structured to ensure high query performance inside the VertiPaq engine:

```text
       ┌───────────────┐          ┌───────────────┐
       │ Dim_Customers │          │  Dim_Riders   │
       └───────┬───────┘          └───────┬───────┘
               │ 1                        │ 1
               │                          │
               │ *                        │ *
       ┌───────┴──────────────────────────┴───────┐
       │               Fact_Orders                │
       └───────┬──────────────────────────┬───────┘
               │ *                        │ *
               │                          │
               │ 1                        │ 1
       ┌───────┴───────┐          ┌───────┴───────┐
       │ Dim_Locations │          │ Dim_Calendar  │
       └───────────────┘          └───────────────┘
-- 1. Fulfillment Rate Percentage
Fulfillment_Rate = 
DIVIDE(
    CALCULATE(COUNTROWS(Fact_Orders), Fact_Orders[status] = "Delivered"),
    COUNTROWS(Fact_Orders),
    0
)

-- 2. Average Order Value (AOV)
AOV = 
DIVIDE(
    SUM(Fact_Orders[net_amount]),
    COUNT(Fact_Orders[order_id]),
    0
)

-- 3. SLA Compliance Percentage (<15 Mins Target)
SLA_Compliance_% = 
DIVIDE(
    CALCULATE(COUNTROWS(Fact_Orders), Fact_Orders[delivery_time_mins] <= 15),
    CALCULATE(COUNTROWS(Fact_Orders), Fact_Orders[status] = "Delivered"),
    0
)

-- 4. Active Fleet Across Geographic Nodes
Active_Riders_Count = 
DISTINCTCOUNT(Fact_Orders[rider_id])

Customer Segmentation Engine (RFM + K-Means)Users were profiled using transactional behavioral data:Recency ($R$): Days elapsed since the customer's last order.Frequency ($F$): Total count of completed platform orders.Monetary ($M$): Gross total transaction value spent.Cohort Partitioning & Strategic Actions:Champions (VIP) [51.57% Revenue Share]: High spend & frequent repeat orders. Highest concentration in Delhi (₹17.69L) and Bangalore (₹14.59L).Strategy: Dedicated priority delivery windows, early access to seasonal campaigns, premium loyalty tiers.Loyal Customers [29.83% Revenue Share]: High-volume steady purchase frequency with moderate AOV.Strategy: Automated subscription refills (Blinkit Pass), cross-category bundles.At-Risk / Lost [7.17% Revenue Share]: Inactive former repeat customers. ~₹2.4L trapped potential in Delhi.Strategy: Automated re-engagement push notifications, category win-back vouchers.New / Recent [11.42% Revenue Share]: First-time buyers onboarding on platform.Strategy: Subsidized second and third orders to accelerate habit formation.📸 Dashboard Modules & Visual WalkthroughNote: If image previews do not render directly, verify exact relative directory paths in Screenshots/.1. Executive Business OverviewPulse tracking Gross Platform Revenue (₹14.03M), Total Volume (64.3K), AOV (₹218.17), city benchmarks, and executive takeaways.2. Customer Segmentation & AnalyticsRFM cohort evaluation mapping customer count against lifetime revenue contribution, average order value, and daily distribution.3. Orders & Fulfillment AnalyticsOperational throughput, hourly surge demand (7:00 PM – 10:00 PM evening peak), fulfillment status distribution, and payment gateway breakdowns.4. Rider Fleet Performance & Delivery SLAFleet efficiency benchmarks across 682 riders, metro rider distribution, daily fulfillment latency, and rider-level leaderboards.💡 Key Business InsightsSurge Capacity Windows: Peak operational stress concentrates between 7:00 PM – 10:00 PM, driven by post-work domestic grocery orders. Fleet shifts need dynamic algorithmic allocation toward high-density dark stores during this window.Revenue Concentration: Delhi (₹3.4M) and Bangalore (₹2.8M) contribute over 44% of total platform GMV.Checkout Friction: UPI represents >45% of all transaction value, followed by COD (~17%). Optimizing 1-click UPI intents directly mitigates checkout abandonment.Latency vs. Churn Decoupling: Average delivery duration sits at ~29.52 minutes across both loyal and churned cohorts, demonstrating that delivery latency is not the root driver of churn; catalog pricing and stock availability govern retention.📁 Repository Directory StructurePlaintext├── Blinkit_Project_Executive_Report.pdf     # 1-Page Strategy & ML Report
├── Power bi dashboard Blinkit(2926).pbix    # Full interactive Power BI Desktop model
├── Screenshots/                            # High-resolution report captures
│   ├── Overview.png
│   ├── Customer.png
│   ├── Orders.png
│   └── Riders.png
└── README.md                               # Project documentation
