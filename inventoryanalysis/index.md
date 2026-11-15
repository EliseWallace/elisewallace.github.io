# Inventory Optimization & Multi-Distribution Safety Stock Modeling

---

## Project Overview
This project develops a data-driven framework to calculate optimal **Safety Stock (SS)** levels across inventory items. While initial descriptive analysis focused on Finished Goods (FG) under Make-to-Stock (MTS) policies, the subsequent safety stock calculations generalized across all available MTS SKUs. Rather than applying a uniform normal distribution formula across all items, this analysis evaluates demand volatility and dispersion at the SKU level to apply appropriate statistical models—preventing costly stockouts on erratic items while avoiding excess holding costs on stable products.

### Repository Structure
* `notebooks/` — Contains the combined Jupyter Notebook (`combined.ipynb`) executing data cleansing, exploratory analysis, distribution classification, and safety stock modeling.
* `data/` — Houses the raw transactional dataset (`transaction_data.csv`) and schema metadata (`meta_data.csv`).

---

## Methodology & Data Pipeline

### 1. Data Cleansing & Standardization
To ensure accurate demand and lead-time inputs, the raw transactional dataset underwent rigorous preprocessing:
* **Schema Alignment:** Standardized column headers (`lead_time`, `division_code`, `order_quantity`) to match corporate metadata conventions.
* **Anomaly & Outlier Filtering:**
  * Removed negative and zero-value `order_quantity` records (representing returns, cancellations, or administrative adjustments).
  * Omitted negative `unit_price` entries (supplier rebates and accounting credits) to prevent duplicate lead-time distortion.
  * Filtered out extreme `lead_time` outliers exceeding 3 standard deviations from the mean (removing unrealistic entries spanning 3.5 to 7.7 years).
* **Missing Value Governance:** Dropped rows with missing `sku_number` identifiers while preserving records with missing non-critical fields (e.g., `division_code`, `manufacturing_site`) to maintain sample integrity.
* **Geographic Enrichment:** Extracted 2-character country prefixes from `manufacturing_site` codes to map global production facilities across the USA, Canada, Poland, and Japan, based on the metadata schema.

### 2. Exploratory Dimensional Analysis & Scope
* **Initial Focus (Assignment 1):** Examined Finished Goods (FG) under Make-to-Stock (MTS) policies.
* **Safety Stock Modeling Scope (Assignment 2):** Expanded and evaluated safety stock requirements across the broader portfolio of **MTS SKUs**:
  * **375** unique active MTS FG SKUs evaluated in the safety stock modeling phase
  * **19** distinct manufacturing sites
  * **54** operational divisions

### 3. Demand Distribution Classification
To select the mathematically sound safety stock formula for each SKU, demand behavior was segmented using two statistical thresholds:
1. **Coefficient of Variation ($\text{CV} = \frac{\sigma}{\mu}$):** SKUs with $\text{CV} \le 0.30$ exhibited stable, predictable demand and were modeled using a **Normal Distribution**:
   $$SS = z_{\alpha} \times \sigma_{d} \times \sqrt{LT}$$
2. **Variance-to-Mean Ratio ($\text{VMR} = \frac{\sigma^2}{\mu}$):** Highly volatile SKUs ($\text{CV} > 0.30$) with $\text{VMR} \ge 1.2$ exhibited overdispersion (low baseline orders punctuated by erratic, high-quantity spikes). These items were modeled using a **negative binomial distribution** via the "method of moments" to determine reorder points ($ROP$) and corresponding safety stock:
   $$SS = ROP - \mu_{LT}$$

All final safety stock outputs were rounded up to whole integer units using floor/remainder logic to reflect actionable physical inventory targets.

---

## Key Findings & Results (95% Service Level)
Evaluating safety stock requirements across **75%**, **90%**, and **95%** service level agreements yielded the following benchmarks at the 95% service level target:

* **Largest Safety Stock Requirement:** SKU `AC3ADABF` required the highest buffer inventory due to high demand variance and lead-time exposure.
* **Smallest Safety Stock Requirement:** SKU `58F77D5E` required the lowest safety stock buffer, reflecting tight order consistency and short lead times.
* **Portfolio Average:** Across all 496 MTS SKUs, the average safety stock requirement is approximately **122 units**.

---

## Explore the Analysis
* [View Combined Jupyter Notebook](./notebooks/supplychain_safetystock.ipynb)
* [View Data](./data)
* [Return to Main Portfolio](../)
