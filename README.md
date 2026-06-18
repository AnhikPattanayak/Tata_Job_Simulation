# 🛒 E-Commerce Retail Sales Analysis

A full-stack data analytics project on the UCI Online Retail dataset — covering data cleaning, exploratory data analysis in Python, and an interactive Power BI dashboard.

---

## 📁 Repository Structure

```
├── 01.Online Retail.zip          # Raw dataset (541,909 transactions, 8 columns)
├── 02.cleaned_data.zip           # Cleaned & feature-engineered dataset
├── 03.E-Commerce_Analysis.ipynb  # Python EDA notebook (Pandas, Matplotlib, Seaborn)
├── 04.Retail_sales_Analysis_dashboard.pbix  # Power BI dashboard file
├── 05.Retail_sales_Analysis_dashboard.pdf   # Dashboard export (static preview)
└── README.md
```

---

## 📌 Project Overview

This project analyses **541,909 transactions** from a online retail store (Dec 2010 – Dec 2011) to uncover revenue patterns, geographic performance, customer value, and product trends.

The pipeline covers:
- **Raw data ingestion** → data cleaning & outlier removal → feature engineering
- **Python EDA** with 8 analysis sections and business insight commentary
- **Power BI dashboard** with KPI cards, time-series, geo-map, and customer/country breakdowns

---

## 📊 Dataset

| Property | Details |
|---|---|
| Source | [UCI ML Repository — Online Retail](https://archive.ics.uci.edu/dataset/352/online+retail) |
| Records | ~541,909 transactions |
| Period | December 2010 – December 2011 |
| Columns | InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country |
| Geography | 38 countries (UK-dominant) |

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python 3 | Core analysis language |
| Pandas & NumPy | Data wrangling, feature engineering, statistical analysis |
| Matplotlib & Seaborn | Data visualisation |
| Power BI Desktop | Interactive dashboard |
| Jupyter Notebook | Analysis environment |

---

## 🔧 Data Cleaning & Feature Engineering

**Cleaning steps applied:**
- Removed **duplicate rows**
- Dropped rows with **missing CustomerID** (primary key for customer analysis)
- Applied **IQR-based outlier removal** on the `Quantity` column
- Removed the `StockCode` column (redundant given `Description`)

**New features engineered:**
- `TotalAmount` — `UnitPrice × Quantity`
- `Status` — `Cancelled` (InvoiceNo starts with 'C') vs `Success`
- `Year_Month` — period extracted from `InvoiceDate`
- `dayname` — day of week extracted from `InvoiceDate`

---

## 📈 Analysis Sections (Notebook)

### 1. Monthly Revenue Trend
- Revenue peaked at **~$755k in November 2011** — driven by holiday shopping demand
- Steady growth from August through November; sharp drop in December 2011

### 2. Day-wise Revenue & Average Spend
- **Thursday** is the highest-revenue day (~$1.1M total, ~$528 avg spend per customer)
- **Sunday** customers shop less but spend more per visit — suited for premium product targeting
- **No transactions on Saturday** — an anomaly worth investigating

### 3. Geographic Revenue Analysis
- **UK accounts for 90%+ of total revenue** (~$4.28M) — a significant market concentration risk
- Top international markets: **Germany (~$178k)** and **France (~$156k)**
- **EIRE has the highest avg spend per customer (~$45,640)** — likely wholesale/bulk buyers

### 4. Customer Analysis
- **CustomerID 17841** placed the most orders (7,767 transactions) but at lower avg value
- **CustomerID 14911** is the highest spender (~$107,349) — true VIP status
- Transaction frequency alone is a poor proxy for customer value — monetary spend is the better signal

### 5. Product Analysis
- **REGENCY CAKESTAND 3 TIER** leads by revenue (~$82,581) — never let this go out of stock
- **PACK OF 72 RETROSPOT CAKE CASES** leads by units sold (14,971) — high volume, low margin
- **POSTAGE** appears as the 2nd highest revenue item (~$66,710) — indicates heavy shipping charges

---

## 📊 Power BI Dashboard

The dashboard (`04.Retail_sales_Analysis_dashboard.pbix`) provides an interactive view across four visuals:

| Visual | Description |
|---|---|
| **KPI Cards** | Total Revenue: $5.11M · Unique Bills: 20.67K · Total Customers: 4.27K |
| **Monthly Revenue Trend** | Line chart — Jan to Dec 2011 revenue movement |
| **Top 10 Countries by Revenue** | Clustered bar — revenue vs quantity side-by-side |
| **Top 10 Customers by Revenue** | Horizontal bar chart — ranked by total spend |
| **Geographic Map** | Bing Maps bubble chart — product distribution by country |

A static PDF export is available at `05.Retail_sales_Analysis_dashboard.pdf` for quick preview without Power BI Desktop.

---

## 💡 Key Business Insights

> **The business is seasonal, UK-dependent, and driven by a small number of high-value customers and products — all three concentrations represent both a strength to protect and a risk to mitigate.**

- **Seasonality:** Stock up by September; November is the peak demand window
- **Geographic risk:** 90% revenue from one market — international expansion in Germany and France is the logical next step
- **Customer strategy:** Top 3 spenders deserve exclusive loyalty benefits; identify and protect EIRE bulk accounts
- **Product strategy:** Protect high-revenue items (Cakestand); use high-volume low-margin items (Retrospot Cases) as traffic drivers

---

## 🚀 How to Run

**Python Notebook:**
```bash
# Install dependencies
pip install pandas numpy matplotlib seaborn jupyter

# Launch notebook
jupyter notebook 03.E-Commerce_Analysis.ipynb
```

**Power BI Dashboard:**
- Download and open `04.Retail_sales_Analysis_dashboard.pbix` in [Power BI Desktop](https://powerbi.microsoft.com/desktop/)
- No additional data connection required — data is embedded
