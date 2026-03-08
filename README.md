# 📱 Mobile Sales Analysis — Power BI Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-005C84?style=for-the-badge)
![Power Query](https://img.shields.io/badge/Power%20Query-217346?style=for-the-badge&logo=microsoft&logoColor=white)
![Status](https://img.shields.io/badge/Project-Completed-success?style=for-the-badge)

> 📊 3 professional dashboards | 📅 MTD & SPLY analysis | 🏙️ City-level sales breakdown | 💳 Payment behavior tracking

---

## 📊 End-to-End Analytics Pipeline

```
Raw Sales Data (CSV/Excel) → Power Query (Cleaning & Transformation) 
→ Data Modeling → DAX (MTD, SPLY, KPIs) → 3-Page Power BI Dashboard → Sales Insights
```

---

## 📌 Project Overview

A mobile retailer selling across multiple cities needed more than a monthly sales report — they needed to know **which models are growing, which cities are underperforming, whether this month is ahead or behind last year, and where daily momentum is heading.**

This project delivers a **3-dashboard Power BI solution** covering full sales performance, month-to-date tracking, and same-period-last-year comparison — the exact suite used by retail sales teams for weekly and monthly business reviews.

---

## 🎯 Business Objectives

1. **Which mobile models and cities drive the most revenue?**
2. **Are we ahead or behind last month's pace right now?** (MTD)
3. **How does this period compare to the same time last year?** (SPLY)
4. **What do payment preferences and ratings tell us about customers?**

---

## 📷 Dashboard Previews

### 📌 Dashboard 1 — Mobile Sales Overview
[![Mobile Sales Dashboard](Screenshot%202025-12-07%20224042.png)](https://github.com/khush3521/Mobile-Sales-Dashboard-PowerBI/blob/main/Screenshot%202025-12-07%20224042.png)

### 📌 Dashboard 2 — MTD (Month-To-Date) Report
[![MTD Dashboard](Screenshot%202025-12-07%20224111.png)](https://github.com/khush3521/Mobile-Sales-Dashboard-PowerBI/blob/main/Screenshot%202025-12-07%20224111.png)

### 📌 Dashboard 3 — Same Period Last Year (SPLY)
[![SPLY Dashboard](Screenshot%202025-12-07%20224120.png)](https://github.com/khush3521/Mobile-Sales-Dashboard-PowerBI/blob/main/Screenshot%202025-12-07%20224120.png)

---

## 📈 Key Insights & Business Impact

| Finding | Business Implication |
|---|---|
| **Top models drive disproportionate revenue share** | Focus inventory and promotions on top-3 SKUs |
| **City-level sales concentration is high** | Underperforming cities need localized campaigns |
| **Clear seasonal monthly trends identified** | Align stock and marketing spend to peak months |
| **Customer ratings vary by model** | Low-rated models carry return/churn risk |
| **Payment method preferences differ by segment** | EMI/card incentives can increase basket size |
| **MTD tracking reveals mid-month momentum shifts** | Enables proactive mid-cycle intervention before month-end |

---

## 📊 Dashboard Structure

### 🔹 Dashboard 1 — Mobile Sales Overview
Full sales performance for business managers:
- **Total Sales, Transactions, Avg Price, Total Quantity** — core KPI cards
- **Sales by City** — geographic revenue breakdown
- **Sales by Mobile Model** — model-level performance ranking
- **Monthly Sales Trend** — time series for pattern recognition
- **Customer Rating Distribution** — satisfaction breakdown
- **Payment Method Share** — cash vs card vs EMI split
- **Sales by Day of Week** — when customers buy most

### 🔹 Dashboard 2 — MTD (Month-To-Date) Report
Daily cumulative tracking for sales managers:
- Daily cumulative sales growth within the current month
- MTD breakdown by Year, Quarter, Month
- KPI snapshot: Sales, Quantity, Avg Price, Transactions

### 🔹 Dashboard 3 — Same Period Last Year (SPLY)
Year-over-year comparison for leadership reviews:
- **Sales vs Last Year** by Year, Quarter, and Month
- Detailed side-by-side comparison table
- Growth/decline flagging per period

---

## 🧠 DAX Measures

```DAX
-- Core KPIs
Total Sales      = SUM(sales[sale_amount])
Total Transactions = COUNTROWS(sales)
Total Quantity   = SUM(sales[quantity])
Avg Price        = DIVIDE([Total Sales], [Total Quantity])

-- Time Intelligence
MTD Sales =
CALCULATE([Total Sales], DATESMTD(sales[date]))

QTD Sales =
CALCULATE([Total Sales], DATESQTD(sales[date]))

YTD Sales =
CALCULATE([Total Sales], DATESYTD(sales[date]))

-- Same Period Last Year
SPLY Sales =
CALCULATE([Total Sales], SAMEPERIODLASTYEAR(sales[date]))

-- YoY Growth %
YoY Growth % =
DIVIDE([Total Sales] - [SPLY Sales], [SPLY Sales])

-- MTD vs Same Period Last Year
MTD vs SPLY =
DIVIDE(
    [MTD Sales] - CALCULATE([MTD Sales], SAMEPERIODLASTYEAR(sales[date])),
    CALCULATE([MTD Sales], SAMEPERIODLASTYEAR(sales[date]))
)

-- Top Selling Model
Top Model =
CALCULATE(
    FIRSTNONBLANK(sales[model], 1),
    TOPN(1, VALUES(sales[model]), [Total Sales], DESC)
)

-- Running Cumulative Sales (for MTD trend line)
Cumulative MTD =
CALCULATE(
    [Total Sales],
    FILTER(
        ALLSELECTED(sales[date]),
        sales[date] <= MAX(sales[date])
    )
)
```

---

## 🛠 Tools & Technologies

| Tool | Purpose |
|------|---------|
| Power BI Desktop | 3-dashboard interactive suite |
| DAX | MTD, SPLY, YoY, cumulative & KPI measures |
| Power Query | Data cleaning, date table, transformation |
| Excel / CSV | Raw sales dataset |
| Data Modeling | Star schema — fact sales + date + product dimensions |

---

## 📂 Repository Structure

```
Mobile-Sales-Dashboard-PowerBI/
│
├── data/
│   └── mobile_sales_data.csv
│
├── powerbi/
│   └── Mobile_Sales_Dashboard.pbix
│
├── Screenshot 2025-12-07 224042.png     ← Dashboard 1 preview
├── Screenshot 2025-12-07 224111.png     ← Dashboard 2 preview
├── Screenshot 2025-12-07 224120.png     ← Dashboard 3 preview
└── README.md
```

> 💡 **Tip:** Rename screenshots to `dashboard1_sales.png`, `dashboard2_mtd.png`, `dashboard3_sply.png` for a cleaner repo.

---

## 🔮 Future Improvements

- Add **Python sales forecasting** using Prophet for next-month predictions
- Build **customer segmentation** — repeat buyers vs one-time purchasers
- Add **return/refund analysis** to calculate net revenue
- Integrate **live POS data** for real-time dashboard refresh
- Publish to **Power BI Service** with daily scheduled refresh

---

## 👨‍💻 Author

**Khush Panchal** — Data Analyst
Specializing in retail analytics, time-intelligence reporting & business intelligence

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/khush-panchal-96b557352)
[![GitHub](https://img.shields.io/badge/GitHub-Portfolio-black?style=flat&logo=github)](https://github.com/khush3521)

---

⭐ If you found this project valuable, please consider starring this repository!
