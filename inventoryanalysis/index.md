# Inventory Optimization & Multi-Distribution Safety Stock Modeling

## Project Overview
This repository contains the code, data, and documentation for our OM 620 supply chain analytics assignments. The project develops a data-driven framework to calculate optimal **Safety Stock (SS)** levels across inventory items. While initial exploratory analysis in Assignment 1 focused on Finished Goods (FG) under Make-to-Stock (MTS) policies, subsequent safety stock calculations in Assignment 2 generalized across all available MTS SKUs. 

Rather than applying a uniform normal distribution formula across all items, this analysis evaluates demand volatility and dispersion at the SKU level to apply appropriate statistical models—preventing costly stockouts on erratic items while avoiding excess holding costs on stable products.

---

## Repository Structure
```text
inventoryanalysis/
├── README.md              # Project overview, findings, and accomplishments (Root)
├── notebooks/             # Directory for code execution files
│   └── supplychain_safetystock.ipynb     # Merged Jupyter Notebook (Assignments 1 & 2)
└── data/                  # Directory for raw datasets
    ├── transaction_data.csv # Raw operational transaction logs
    └── meta_data.csv        # Schema metadata definitions
```
---

## Methodology & Data Pipeline: Inventory Optimization & Safety Stock Modeling

This section outlines the end-to-end data pipeline, exploratory scoping, statistical distribution classification, and visualization framework used to calculate optimal safety stock levels across all Make-to-Stock (MTS) SKUs.
* **Schema Alignment:** Standardized column headers (`lead_time`, `division_code`, `order_quantity`, `unit_price`, `sku_number`, `manufacturing_site`) to match metadata conventions.
* **Anomaly & Outlier Adjustments:**
  * Removed zero-value `order_quantity` records, attributed to data-entry issues,
  * Took the absolute value for negative `unit_price` and 'order_quantity' entries, attributed to data-entry issues,
  * Adjusted lead time outliers, attributed to data entry scaling issues,
* **Missing Value Governance:** Filled all NaN values with "Unknown" category for categorical features.
* **Geographic Enrichment:** Extracted 2-character country prefixes from `manufacturing_site` codes to map global production facilities across the USA, Canada, Poland, and Japan.

---

## 2. Exploratory Dimensional Analysis & Scope
* **Initial Scoping (Assignment 1):** Examined Finished Goods (FG) under Make-to-Stock (MTS) policies to establish baseline operational metrics.
* **Safety Stock Modeling Scope (Assignment 2):** Expanded safety stock calculations across the broader portfolio of **MTS SKUs**:
  * **376** unique active MTS FG SKUs evaluated in the safety stock modeling phase (including unknown)
  * **497** unique active MTS SKUs evaluated in the safety stock modeling phase (including unknown)
  * **20** distinct manufacturing sites (including unknown)
  * **55** operational divisions (including unknown)

---

## 3. Demand Distribution Classification & Mathematical Modeling
To prevent stockouts on erratic items while avoiding excess holding costs on stable products, demand behavior was segmented at the SKU level using three distinct statistical thresholds:

### A. Coefficient of Variation (Normal Distribution)
SKUs exhibiting low demand variance represent stable, predictable consumption patterns and were modeled using a Normal Distribution.

$$
\text{CV} = \frac{\sigma}{\mu}
$$

$$
\text{Classification Rule: } \text{CV} \le 0.30
$$

$$
SS = z_{\alpha} \times \sigma_{d} \times \sqrt{LT}
$$

### B. Variance-to-Mean Ratio (Negative Binomial Distribution)
Highly volatile SKUs with significant overdispersion featured low baseline orders punctuated by erratic, high-quantity spikes. These items were modeled using a Negative Binomial Distribution via the method of moments to determine reorder points and safety stock:

$$
\text{VMR} = \frac{\sigma^2}{\mu}
$$

$$
\text{Classification Rule: } \text{CV} > 0.30 \text{ and } \text{VMR} \ge 1.2
$$

$$
SS = ROP - \mu_{LT}
$$

All final safety stock outputs were rounded up to whole integer units using floor/remainder logic to establish actionable physical inventory targets.

### C. Non-Parametric (Quantile) Distribution
Another non-normal distribution methodology was implemented and applied to determine safety stocks, using quantiles to calculate the deviation from the mean.

$$\text{Safety Stock} = (\text{Quantile}_{CSL}(d) - \bar{d}) \times \sqrt{LT}$$

---

## Key Findings & Results (95% Service Level)
Evaluating safety stock requirements across **75%**, **90%**, and **95%** service level coefficients yielded the following benchmarks at the 95% service level target:

* **Largest Safety Stock Requirement:** SKU `AC3ADABF` required the highest buffer inventory due to high demand variance and lead-time exposure.
* **Smallest Safety Stock Requirement:** SKU `58F77D5E` required the lowest safety stock buffer, reflecting tight order consistency and short lead times.
* **Portfolio Average:** Across all 497 MTS SKUs, the average safety stock requirement is approximately **120 units** using a **normal** distribution, approximately **124 units** using a **negative binomial** distribution, approximately **123 units** using a **hybrid** distribution (normal and negative binomial), and approximately **114 units** using a **non-parametric** distribution.

Parametric models force customer demand into symmetrical bell curves or theoretical count distributions. When actual SKU demand exhibits long tail behavior interspersed with zero-demand periods, standard deviations over-inflate tail risk. The non-parametric empirical quantile method removes theoretical distortion by grounding buffers directly in historical customer order behavior.

Adopting the empirical quantile method reduces average safety stock across all SKUs, which would result in a **~7.3% reduction in holding inventory** compared to the other evaluated models, lowering storage costs without compromising the target 95% service level agreement.

---

## Explore the Analysis
* [View Jupyter Notebook](https://github.com/EliseWallace/elisewallace.github.io/tree/main/inventoryanalysis/notebooks)
* [View data](https://github.com/EliseWallace/elisewallace.github.io/tree/main/inventoryanalysis/data)
* [Return to Main Portfolio](../)
