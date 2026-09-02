# blinkit-executive-analytics-dashboard
End-to-End Blinkit Power BI Analytics Dashboard covering Overview, Customers, Orders, and Rider Performance.
# 🛒 Blinkit Quick-Commerce Executive Analytics Dashboard

An end-to-end Power BI executive analytics dashboard designed to analyze and optimize quick-commerce retail operations across 64K+ orders, customer lifetime value segments, fleet delivery SLA compliance, and multi-city revenue streams.

---

## 📌 Dashboard Architecture & Core Views

The dashboard features a persistent, branded corporate sidebar with dynamic page navigation across four dedicated reporting modules:

1. **Executive Business Overview:** High-level strategic pulse tracking Gross Revenue (₹14.03M), Total Order Volume (64.3K), Average Order Value (₹218.17), city revenue shares, and fulfillment status splits.
2. **Customer Segmentation & Analytics:** RFM-driven segmentation (Champions/VIP, Loyal Customers, At-Risk/Lost, New/Recent) mapping customer lifetime spend, churn patterns, and daily purchase cycles.
3. **Orders & Fulfillment Analytics:** Hourly demand curves, fulfillment performance (71.4% delivered rate), payment method split (UPI, COD, Wallet, Card), and transactional records.
4. **Rider Fleet Performance & Fleet Analytics:** City-wide rider distribution, daily speed benchmarks, delivery SLA compliance (<15 min target), and rider efficiency leaderboards.

---

## 🛠️ Tech Stack & Methodology

- **Business Intelligence:** Power BI Desktop / Power BI Service
- **Data Modeling:** Star Schema architecture linking fact transactions (`Orders`) with dimension tables (`Customers`, `Riders`, `Locations`, and `Calendar`).
- **DAX Measures:** Dynamic multi-variable KPIs, fulfillment rates, SLA compliance percentages, running totals, and weighted average delivery times.
- **UI/UX Design:** Native Blinkit corporate branding, custom grid layouts, custom SVG navigation bar, and cross-filtering interactivity.

---

## 📸 Visual Previews

### 1. Executive Business Overview
https://github.com/krishkumar5751-bit/blinkit-executive-analytics-dashboard/blob/main/Overview.png.png?raw=true

### 2. Customer Segmentation & Analytics
https://github.com/krishkumar5751-bit/blinkit-executive-analytics-dashboard/blob/main/Customers.png.png?raw=true

### 3. Orders & Fulfillment Analytics
https://github.com/krishkumar5751-bit/blinkit-executive-analytics-dashboard/blob/main/Orders.png.png?raw=true

### 4. Rider Fleet & Delivery Performance
https://github.com/krishkumar5751-bit/blinkit-executive-analytics-dashboard/blob/main/Riders.png.png?raw=true

---

## 📈 Strategic Business Takeaways

- **Peak Ordering Windows:** Order volume surges between **7:00 PM – 10:00 PM**, requiring optimized rider capacity allocations in top distribution hubs.
- **Revenue Concentration:** **Delhi (₹3.4M)** and **Bangalore (₹2.8M)** generate the majority of gross platform revenue.
- **Payment Dominance:** **UPI** leads gross transaction volume share (>45%), followed by Cash on Delivery (COD) and Digital Wallets.
- **Delivery Speed vs. Retention:** Average delivery duration sits uniformly at **~29.52 minutes** across all customer cohorts, indicating churn is driven by pricing or inventory stockouts rather than transit latency.

---

## 📂 Repository Structure

```text
├── Blinkit_Project_Executive_Report.pdf   # 1-Page ML & Business Strategy Report
├── Power bi dashboard Blinkit(2926).pbix  # Full interactive Power BI Desktop file
├── Screenshots/                          # High-resolution report visuals
│   ├── Overview.png
│   ├── Customers.png
│   ├── Orders.png
│   └── Riders.png
└── README.md                             # Project documentation
