# 🛒 E-Commerce Retail Sales Analysis

A data analytics project exploring online retail transaction data to uncover revenue trends, geographic performance, customer spending patterns, and product insights — using **Python** and **Power BI**.

---

## 📌 Project Overview

This project analyses **541,909 transactions** from a UK-based online retail store spanning December 2010 to December 2011. The goal is to derive actionable business insights across revenue seasonality, customer value segmentation, international market performance, and product-level profitability.

---

## 📂 Dataset Summary

| Property | Details |
| --- | --- |
| Source | Forage — Tata Data Visualisation Job Simulation |
| Total Rows | 541,909 |
| Total Columns | 8 |
| Missing Data | Null values in `CustomerID` (dropped) |

**Key Features:**

- **Transaction Details** — InvoiceNo, InvoiceDate, StockCode
- **Product Info** — Description, Quantity, UnitPrice
- **Customer & Geography** — CustomerID, Country

---

## 🔧 Tools & Technologies

| Tool | Purpose |
| --- | --- |
| Python (pandas, numpy, matplotlib, seaborn) | Data cleaning, feature engineering & EDA |
| Power BI Desktop (DAX) | Interactive dashboard & KPI reporting |
| Jupyter Notebook | Interactive analysis environment |

---

## 🧹 Data Preparation (Python)

- **Data Loading** — Imported raw dataset using `pandas` with `unicode_escape` encoding
- **Duplicate Removal** — Identified and dropped all duplicate rows
- **Missing Data Handling** — Dropped rows with null `CustomerID` (primary key for customer analysis)
- **Outlier Removal** — Applied IQR method on `Quantity` column; removed values outside lower and upper fences
- **Column Removal** — Dropped `StockCode` (redundant given `Description`)
- **Feature Engineering**
  * `TotalAmount` — derived as `UnitPrice × Quantity` per transaction
  * `Status` — flagged `Cancelled` (InvoiceNo starts with 'C') vs `Success`
  * `Year_Month` — extracted period from `InvoiceDate` for monthly trend analysis
  * `dayname` — extracted day of week from `InvoiceDate` for day-wise analysis

---

## 📊 EDA Analysis (Python)

Six analytical sections were explored with visualisations and business commentary:

1. **Monthly Revenue Trend** — Revenue peaked at ~$755k in November 2011; consistent growth from August through November driven by holiday demand; sharp drop in December 2011 (~$205k)

2. **Day-wise Revenue & Avg Spend** — Thursday leads in both total revenue (~$1.1M) and avg spend per customer (~$528); Sunday has the lowest sales volume but above-average spend per customer; no transactions recorded on Saturday

3. **Geographic Revenue (With UK)** — UK accounts for ~90% of total revenue (~$4.28M), dwarfing all other markets combined — a significant market concentration risk

4. **Geographic Revenue (Without UK)** — Germany (~$178k) and France (~$156k) are the top international markets; EIRE has the highest avg spend per customer at ~$45,640 — likely wholesale/bulk buyers

    | Rank | Country | Total Revenue |
    | --- | --- | --- |
    | 1 | Germany | ~$178k |
    | 2 | France | ~$156k |
    | 3 | EIRE | ~$136k |
    | 4 | Switzerland | ~$40k |
    | 5 | Netherlands | ~$30k |

5. **Customer Analysis** — CustomerID 17841 placed the most orders (7,767 transactions) but at lower avg spend; CustomerID 14911 is the highest spender overall (~$107k); transaction count alone is a poor proxy for customer value — total spend is the stronger signal

6. **Product Analysis** — REGENCY CAKESTAND 3 TIER leads by revenue (~$82,581); PACK OF 72 RETROSPOT CAKE CASES leads by units sold (14,971) — high volume, low margin; POSTAGE appears as 2nd highest revenue item (~$66k)

---

## 📊 Power BI Dashboard

The dashboard provides an interactive view across five visuals:

| Visual | Description |
| --- | --- |
| **KPI Cards** | Total Revenue: $5.11M · Unique Bills: 20.67K · Total Customers: 4.27K |
| **Monthly Revenue Trend** | Line chart — month-by-month revenue movement across 2011 |
| **Top 10 Countries by Revenue** | Clustered bar — revenue vs quantity side-by-side for international markets |
| **Top 10 Customers by Revenue** | Horizontal bar chart — customers ranked by total spend |
| **Geographic Map** | Bing Maps bubble chart — product distribution concentration by country |

A static PDF export is available at `05.Retail_sales_Analysis_dashboard.pdf` for quick preview without Power BI Desktop.

---

## 💡 Key Business Insights

- **November 2011 = peak revenue (~$755k)** — stock and logistics planning must begin by September to capitalise on the holiday window
- **UK contributes 90%+ of total revenue** — the business is dangerously concentrated in one market; any disruption to UK operations directly threatens the entire business
- **Germany and France are the most viable international expansion targets** by total volume; EIRE must be protected as the highest-value customer base per customer outside UK
- **Thursday is the power shopping day** — marketing campaigns and promotions should be timed around Thursday for maximum impact
- **Sunday shoppers buy less frequently but spend more per visit** — a strong target segment for premium product promotions
- **CustomerID 14911 (~$107k spend) and 14096 (~$53k) are true VIPs** — exclusive loyalty benefits and personal discounts should be extended to retain them
- **REGENCY CAKESTAND 3 TIER (~$82k revenue) must never go out of stock** — it is the single highest-revenue product in the catalogue
- **The business is seasonal, UK-dependent, and driven by a small number of high-value customers and products** — all three concentrations represent both a strength to protect and a risk to mitigate

---

## 🚀 How to Run

**Python Notebook:**

1. Clone the repository
   ```bash
   git clone https://github.com/AnhikPattanayak/E-Commerce.git
   cd E-Commerce
   ```

2. Install dependencies
   ```bash
   pip install pandas numpy matplotlib seaborn jupyter
   ```

3. Extract the raw dataset
   ```bash
   unzip "01.Online Retail.zip"
   ```

4. Launch the notebook
   ```bash
   jupyter notebook 03.E-Commerce_Analysis.ipynb
   ```

**Power BI Dashboard:**

1. Download and install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free)
2. Open `04.Retail_sales_Analysis_dashboard.pbix` in Power BI Desktop
3. No additional data connection required — data is embedded in the file

> 💡 To preview the dashboard without Power BI Desktop, open `05.Retail_sales_Analysis_dashboard.pdf` directly.

---

## 📁 Project Structure

```
E-Commerce/
│
├── 01.Online Retail.zip                        # Raw dataset (541,909 rows × 8 columns)
├── 02.cleaned_data.zip                         # Cleaned & feature-engineered dataset
├── 03.E-Commerce_Analysis.ipynb                # Python EDA notebook
├── 04.Retail_sales_Analysis_dashboard.pbix     # Power BI dashboard file
├── 05.Retail_sales_Analysis_dashboard.pdf      # Dashboard static export (PDF)
└── README.md
```
