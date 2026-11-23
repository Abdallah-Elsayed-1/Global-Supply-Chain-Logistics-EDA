<div align="center">

<img src="https://i.postimg.cc/k4RmNprz/Gemini-Generated-Image-i95hn0i95hn0i95h.png" alt="Global Supply Chain & Logistics Analytics Banner" width="100%">

# 🚚 Global Supply Chain & Logistics Analytics
### End-to-End Python Data Cleaning, SLA Variance Engineering & Profitability Root-Cause Analysis

![Python](https://img.shields.io/badge/Python-3.13-10B981?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Engineering-059669?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-Analytics-047857?style=for-the-badge&logo=numpy&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-Visuals-065F46?style=for-the-badge)

[**📓 View Full Python Notebook**](./SupplyChainDataset.ipynb) • [**🌐 Live Portfolio**](https://abdallah-elsayed-1.github.io/Abdallah-Elsayed-1/)

</div>

---

## 📌 Business Use Case

**DataCo Global** operates a multi-regional supply chain and e-commerce fulfillment network across **Europe, LATAM, Pacific Asia, USCA, and Africa**. While generating **$36.78M** in gross revenue across **180,519** transactions, operations leadership faced two critical bottlenecks eroding customer retention and net profitability:

* **Severe SLA Breaches:** **54.83%** of all orders (`98,977` shipments) arrived behind schedule, raising urgent questions around carrier reliability versus unrealistic delivery commitments.
* **Unexplained Margin Leakage:** **18.71%** of orders (`33,784` transactions) were fulfilled at a net financial loss, with ambiguity over whether promotional discounting or specific product lines were driving negative margins.

**Analytical Goal:** Build a clean, production-ready data pipeline and execute root-cause EDA to diagnose shipping SLA failures, measure discount-to-profit elasticity, and isolate loss-making SKUs.

---

## ⚡ Executive KPIs at a Glance

* **Dataset Scale:** `180,519` transactions standardized from `53` raw columns down to `41` high-value features (`0` nulls)
* **Gross Revenue:** `$36.78M` across 11 departments and 5 global markets
* **Total Net Profit:** `$3.97M` (`10.78%` overall net profit margin)
* **Late Delivery Rate:** `54.83%` (`98,977` delayed shipments)
* **Unprofitable Orders:** `18.71%` (`33,784` loss-making orders)
* **Discount-Profit Correlation:** `-0.0186` (proving discounts are not the root cause of losses)

---

## 🔍 Root-Cause Findings & Visual Insights

### 1. Overall Delivery Status Distribution
* **54.83%** (`98,977` orders) resulted in `Late delivery`, outnumbering `Advance shipping` (**23.04%**) and `Shipping on time` (**17.84%**) combined.

<div align="center">
  <img src="https://i.postimg.cc/Vs76W3bV/Screenshot-2026-11-23-230011.png" alt="Distribution of Delivery Status" width="80%">
</div>

---

### 2. Shipping SLA Compliance Bottlenecks by Tier
* **First Class** suffered a **95.32%** late delivery rate (averaging **+1.00 day** past SLA), followed by **Second Class** at **76.63%** (averaging **+1.99 days** delay).
* **Standard Class** maintained a significantly lower **38.07%** late rate (averaging **-0.004 days** variance).
* **Diagnosis:** SLA breaches are concentrated in expedited tiers due to overly aggressive scheduled delivery windows (`days_for_shipment_scheduled`) rather than systemic carrier slowness.

<div align="center">
  <img src="https://i.postimg.cc/9XxMYv73/Screenshot-2026-11-23-230054.png" alt="Late Delivery Risk Rate by Shipping Mode" width="80%">
</div>

---

### 3. Revenue Concentration, Seasonality & Margin Leakage
* **Top Profit Drivers:** **Fan Shop** (`$17.11M` sales / `$1.83M` profit) and **Apparel** (`$7.98M` sales / `$881.9K` profit) dominate company revenue, alongside **Fishing** (`$6.93M`) and **Cleats** (`$4.43M`).
* **Discount vs. Profit Reality:** Correlation between `order_item_discount_rate` and `benefit_per_order` is **-0.0186**, confirming that promotional discounting does **not** drive negative profit.
* **SKU-Level Losses:** Cumulative net losses across the entire catalog are isolated to **only 3 SKUs**:
  * `SOLE E35 Elliptical` (**-$965.12** cumulative net loss)
  * `Bushnell Pro X7 Jolt Slope Rangefinder` (**-$255.95** cumulative net loss)
  * `SOLE E25 Elliptical` (**-$169.56** cumulative net loss)

<div align="center">
  <img src="https://i.postimg.cc/59P0SZCW/Screenshot-2026-11-23-230122.png" alt="Total Sales by Department" width="80%">
</div>

<br>

<div align="center">
  <img src="https://i.postimg.cc/1RWtrLqZ/Screenshot-2026-11-23-230142.png" alt="Total Sales by Month" width="80%">
</div>

---

## 🛠️ Data Engineering & Analytical Workflow

* **Programmatic Redundancy Validation:** Mathematically verified 100% equivalence across duplicate price, customer ID, and order total fields before dropping, reducing memory usage from **73.0+ MB** to **52.3+ MB**.
* **Data Governance & PII Hygiene:** Stripped sensitive and non-analytical attributes (`Customer Email`, `Customer Password`, `Customer Street`, `Customer Zipcode`) and standardized all schema headers to `snake_case`.
* **Domain-Specific Feature Engineering:**
  * `shipping_delay_days`: Engineered exact SLA variance (`days_for_shipping_real - days_for_shipment_scheduled`) to evaluate fulfillment accuracy.
  * `customer_full_name`: Consolidated customer first and last names cleanly.
  * `order_year` & `order_month`: Extracted temporal dimensions from parsed `datetime64` timestamps for seasonality tracking.
* **BI-Ready Output:** Exported `SupplyChain_Cleaned.csv` ready for downstream Power BI dimensional modeling and SQL warehousing.

---

## 🚀 Actionable Recommendations

1. **Recalibrate Expedited SLAs:** Adjust `days_for_shipment_scheduled` windows for *First Class* and *Second Class* tiers to match realistic carrier transit times and eliminate chronic SLA breaches.
2. **Audit Loss-Making SKUs:** Restructure supplier costs, freight charges, and retail pricing for `SOLE E35 Elliptical`, `SOLE E25 Elliptical`, and `Bushnell Pro X7`.
3. **Protect High-Margin Core Lines:** Prioritize inventory availability and fulfillment speed for **Fan Shop** and **Fishing** categories, which generate the bulk of company revenue and net profit.

---

## 📂 Repository Contents

* `SupplyChainDataset.ipynb` — Complete Python EDA notebook (Data Cleaning, Feature Engineering, Statistical Analysis & Dark-Mode Visuals)
* `README.md` — Executive Business Use Case, KPI Summary & Strategic Recommendations

---

<div align="center">
  <b>Engineered by <a href="https://abdallah-elsayed-1.github.io/Abdallah-Elsayed-1/">Abdallah Elsayed</a></b> • Data & BI Analyst
</div>
