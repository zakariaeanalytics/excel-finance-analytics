##  Project Overview

**Aether Precision Systems — H1 2025 Revenue Growth vs. Profitability Gap Analysis**

A finance analytics case study focused on diagnosing why revenue growth in H1 2025 was not translating into proportional improvements in profitability and margins.

The analysis combines data preparation, financial analysis, driver investigation, and financial impact assessment to identify where value was being created or diluted and translate the findings into practical management actions.

**Domain:** FP&A · Revenue & Profitability Analytics · Corporate Finance  
**Reporting Period:** H1 2025  
**Tool:** Microsoft Excel  

---
##  Company & Business Context

**Aether Precision Systems (APS)** is a mid-sized industrial technology company headquartered in the United States, with commercial operations across North America, EMEA, APAC, and Latin America.

The company designs, manufactures, and sells precision measurement instruments, condition-monitoring sensors, analytics software, and related field services. Its solutions are used across manufacturing, energy & utilities, process industries, aerospace & defense, and research laboratories.

APS operates through three primary business units:

- **Sensors & Instruments** — hardware sensors and portable/fixed analyzers
- **Software & Analytics** — analytics platforms, predictive modules, dashboards, and API integrations
- **Field Services** — commissioning, calibration, maintenance, emergency response, and training

The company sells through direct sales, industrial distributors, and a partner portal, serving customers across multiple industries, customer segments, and customer types.

APS has been expanding through customer acquisition, increased software adoption, and geographic expansion, particularly across APAC and Latin America.

---
##  Business Problem

Aether Precision Systems is experiencing a clear **top-line growth vs. profitability gap** in H1 2025.

Revenue is growing, but profitability and margin performance are not improving at the same pace. Management needs to determine whether the quality of this growth is being weakened by the underlying sales mix, discounting practices, cost pressures, or differences in performance across regions and business units.

The key financial concerns are:

- Revenue growth is visible, but gross and contribution margin trends are weaker than expected.
- Management has observed operating profit lagging the overall growth trajectory and the Board-approved budget.
- Higher discounting may be reducing realized revenue and weakening the economics of certain sales channels or customer types.
- Cost pressures may be affecting the profitability of specific products or business areas.
- Regional and business-unit differences may be creating uneven financial performance.

The challenge for Finance is therefore not simply to measure how much revenue the company generated, but to understand **where value is being created, where it is being diluted, and what is driving the profitability gap**.

---
##  Analytical Objectives

The analysis aims to determine **why revenue growth is not translating into proportional profitability improvement** and identify the areas with the greatest financial impact.

The analysis will focus on:

- Assessing revenue growth and the underlying sales mix across products, business units, regions, customer segments, and channels.
- Evaluating discounting and pricing realization to determine where revenue may be diluted.
- Analyzing cost structure and profitability to identify the main sources of cost pressure.
- Comparing financial performance across products, business units, regions, customer types, and other relevant dimensions.
- Investigating the key drivers behind significant profitability gaps and unusual performance patterns.
- Quantifying the financial impact of the largest value-diluting issues and distinguishing material opportunities from lower-priority findings.
- Translating the findings into clear, prioritized recommendations for management.

### Key Questions

The analysis is ultimately designed to answer:

1. **Where is revenue growth coming from, and how profitable is that growth?**
2. **Where are discounts or pricing patterns weakening revenue realization?**
3. **Which products, business units, regions, or customer groups are creating or diluting value?**
4. **What cost pressures are contributing most to the profitability gap?**
5. **Which issues have the greatest measurable financial impact?**
6. **Where should management prioritize action?**

---
##  Scope & Reporting Period

The analysis covers **H1 2025**, from **1 January 2025 to 30 June 2025**.

### Reporting Scope

The analysis evaluates financial performance across the main dimensions available in the data, including:

- Business units
- Regions
- Products
- Customer segments and customer types
- Sales channels
- Cost structure and cost elements

### Benchmark & Comparisons

The **primary benchmark** is the **Board-approved H1 2025 Budget**, analyzed at the **Business Unit × Region × Month** level.

Secondary comparisons include:

- Month-to-month performance trends within H1 2025
- Product mix shifts
- Customer mix shifts

This scope is designed to evaluate both the overall H1 financial performance and the underlying differences in growth, cost, and profitability across relevant business dimensions.

---
##  Data & Data Quality

The analysis is built from **seven interconnected source datasets** covering transactions, customers, products, costs, budget, organizational mappings, and foreign-exchange rates.

### Data Architecture

| Dataset | Approx. Rows | Role |
|---|---:|---|
| `01_Transactions_Raw` | ~1,310 | Primary sales transaction data |
| `02_Customers_Raw` | 185 | Customer master data |
| `03_Products_Raw` | 19 | Product master, pricing, and standard cost data |
| `04_Costs_Raw` | 324 | Monthly product costs and regional/BU overhead |
| `05_Budget_Raw` | 72 | H1 2025 budget by Business Unit × Region × Month |
| `06_Org_Reference_Raw` | 12 | Business Unit and Region mappings |
| `07_FX_Rates_Raw` | 18 | Monthly foreign-exchange rates to USD |

The primary analytical grain is the **transaction level**, enriched with relevant customer, product, cost, and budget attributes.

### Data Preparation

The project maintains three data stages:

**Raw → Cleaned → Analytical**

- **Raw data** preserves the original source extracts.
- **Cleaned data** standardizes fields, resolves confirmed data-quality issues, and prepares the source tables for reliable use.
- **Analytical data** combines the cleaned sources into a structured dataset ready for financial analysis.

### Data Quality Challenges

The source data contains several realistic quality issues that required investigation, including:

- Inconsistent text formatting, naming conventions, and classifications
- Numeric values stored as text
- Missing financial values and dates
- Transactions outside the reporting period
- Negative quantities and suspicious prices or discounts
- Invalid or unmatched CustomerIDs and ProductIDs
- Exact duplicates and near-duplicate records
- Legitimate transactions and business events that initially appear anomalous

Data-quality issues were not automatically treated as errors. Each material exception was investigated to distinguish between **data problems, genuine business signals, and ambiguous cases**.

Detailed cleaning decisions, investigations, and residual risks are documented separately in the project's data-quality documentation.


---
##  Analytical Approach

The analysis follows a structured finance analytics workflow designed to move from **data validation to diagnosis, financial impact assessment, and management action**.

### 1. Data Quality & Reporting Readiness

The source data is reviewed, cleaned, standardized, and validated before being used for financial analysis. Material data-quality issues are either resolved or explicitly flagged for further investigation.

### 2. Revenue Performance

Revenue is analyzed across time and key business dimensions to identify growth patterns, major contributors, and changes in product, customer, regional, business-unit, and channel mix.

### 3. Discount & Pricing Realization

The analysis compares gross/list revenue with net revenue to assess discounting levels and identify where pricing realization is weakest across relevant customer, channel, regional, and product dimensions.

### 4. Cost Structure & Cost Pressure

Variable and fixed costs are analyzed by product, business unit, and region. Actual costs are compared with standard costs and relevant budget benchmarks to identify material cost pressures and overruns.

### 5. Profitability & Margin Analysis

Gross profit, contribution profit, and related margins are calculated and compared across key business dimensions to distinguish high-revenue areas from genuinely profitable areas.

### 6. Budget Variance Analysis

Actual financial performance is compared with the Board-approved H1 2025 Budget to identify the largest favorable and unfavorable variances across revenue, costs, and profit.

### 7. Driver Investigation & Anomaly Review

Significant variances and unusual results are investigated to determine whether they represent genuine business performance, data-quality issues, legitimate one-off events, or cases requiring further investigation.

### 8. Financial Impact & Prioritization

The largest identified issues and opportunities are quantified and ranked according to financial materiality to determine where management attention can have the greatest impact.

### 9. Management Recommendations

The findings are translated into prioritized management actions covering pricing and discount governance, product mix, cost management, regional focus, and relevant data or process improvements.

---
##  Analysis & Results

### Revenue & Pricing

H1 2025 generated **$4.60M in Gross Revenue** and **$3.93M in Net Revenue**, with total discounts of approximately **$674.6K**, representing an overall discount rate of **14.66%**.

**Sensors & Instruments** was the dominant revenue contributor, accounting for approximately **57.59% of H1 Net Revenue**.

Discounting represented a significant revenue-realization consideration, particularly across **Distributor** and **Strategic** sales. However, these discounts are treated as revenue exposure rather than confirmed profit loss because no approved target-discount benchmark was available to establish that the discounts were fully recoverable.

### Cost & Profitability

The analysis identified meaningful differences in profitability across business units and products.

**Software & Analytics** demonstrated the strongest contribution economics, with an approximate contribution margin of **95.08%**, highlighting the value of maintaining and selectively expanding high-margin revenue.

**Field Services** generated a lower contribution margin than the other business units, at approximately **37.97%**.

At the product level, **P-SI-004** and **P-SI-007** were identified as important cost-pressure points. Their combined actual-vs-standard cost overrun represented approximately **$49.5K**, making this the strongest directly benchmarked improvement opportunity identified in the analysis.

### Budget Variance — Data Limitation

Budget variance analysis was performed against the H1 2025 Board-approved budget at the **Business Unit × Region × Month** level.

However, the analysis identified comparability and data-quality limitations affecting the reliability of certain actual-vs-budget conclusions. Budget variance findings were therefore **isolated from the primary profitability conclusions** rather than being presented as confirmed drivers of the overall gap.

### Driver Investigation

The investigation indicates that the profitability gap is not explained by a single factor.

The main themes identified were:

- Revenue concentration does not automatically translate into stronger profitability.
- Discounting creates meaningful revenue-realization exposure, particularly in certain channels and customer types.
- Product-level cost overruns are a directly measurable source of value dilution.
- High-margin Software & Analytics revenue represents an important value-creation opportunity.
- Field Services requires closer attention to its underlying economics and cost structure.
- Data-quality issues can materially affect dimension-level analysis and therefore require continued control and documentation.

---
##  Financial Impact & Prioritization

The identified financial impacts are prioritized from the **largest quantified amount to the smallest**, while distinguishing between confirmed cost impact, revenue exposure, and illustrative improvement opportunities.

| Priority | Financial Issue | Estimated Impact | Interpretation |
|---|---|---:|---|
| **1** | Distributor & Strategic discount exposure | **~$510.8K** | Largest quantified amount. Represents revenue surrendered through discounting, not confirmed profit loss |
| **2** | Product-level cost overruns — P-SI-004 & P-SI-007 | **~$49.5K** | Directly benchmarked actual-vs-standard cost overrun and the strongest measurable cost-improvement opportunity |
| **3** | Field Services profitability improvement opportunity | **~$44K** | Illustrative contribution-margin improvement opportunity; not a confirmed financial loss |

### Financial Interpretation

The largest financial exposure identified is associated with **discounting**, particularly across Distributor and Strategic sales. However, the full amount should not be treated as recoverable profit because some discounts may be commercially justified and no approved target-discount benchmark was available.

The second-largest quantified issue is the **~$49.5K cost overrun** identified across P-SI-004 and P-SI-007. Because this is supported by an actual-vs-standard cost comparison, it represents the strongest directly measurable improvement opportunity.

The **~$44K Field Services opportunity** reflects an illustrative contribution-margin benchmark and provides directional insight into the potential value of improving the economics of the business unit. It should not be interpreted as a confirmed realized loss.

Accordingly, the figures represent **different forms of financial impact and should not be summed into a single loss or opportunity figure**.

---
##  Management Recommendations

Based on the financial impact assessment and driver investigation, the following actions are prioritized by **financial relevance, evidence strength, and practical management value**.

### 1. Strengthen Discount & Pricing Governance

The largest quantified financial exposure is associated with **Distributor and Strategic discounting (~$510.8K)**.

Management should review discount practices by customer type, channel, region, and product to identify where discounts are commercially justified and where stronger approval thresholds or pricing controls may be appropriate.

This should not be treated as a blanket discount reduction. Strategic and Key Account discounts may be commercially rational and should be evaluated against customer value, volume, contract terms, and expected profitability.

### 2. Investigate Product-Level Cost Overruns

The analysis identified approximately **$49.5K of actual-vs-standard cost overruns across P-SI-004 and P-SI-007**.

Finance and Product Management should investigate the underlying drivers, including component costs, labor, sourcing, production efficiency, and standard-cost assumptions, and determine whether corrective action or cost-standard updates are required.

### 3. Protect and Expand High-Margin Revenue

**Software & Analytics** demonstrated an approximate **95.08% contribution margin**, making high-margin revenue an important value-creation opportunity.

Management should evaluate opportunities to protect existing high-margin software revenue and selectively increase software adoption or attachment where commercially and operationally appropriate.

### 4. Review Field Services Economics

Field Services generated an approximate **37.97% contribution margin**, with an illustrative improvement opportunity of approximately **$44K**.

Management should review service pricing, labor utilization, contract economics, and cost structure to determine whether the business unit can improve contribution economics without compromising service quality or customer relationships.

### 5. Strengthen Data & Reporting Controls

The analysis identified data-quality issues affecting dimensions such as dates, customer and product identifiers, classifications, and financial fields.

Finance should strengthen data validation and reporting controls to reduce the risk of unreliable management reporting, particularly for product-, customer-, regional-, and budget-level analysis.

### Recommended Management Focus

The immediate focus should be on **discount governance and product-level cost control**, given the size of the identified financial exposure and measurable cost opportunity.

At the same time, management should protect high-margin Software & Analytics growth, improve the economics of Field Services, and strengthen data controls to support more reliable future decision-making.

---
##  Limitations & Caveats

The findings in this analysis should be interpreted within the following limitations and assumptions.

### Data Quality & Analytical Coverage

The raw data contained multiple quality issues, including missing or inconsistent dates, invalid CustomerIDs and ProductIDs, inconsistent classifications, negative quantities, duplicate records, and financial fields requiring validation.

Confirmed data-quality issues were corrected where the evidence supported a reliable correction. Cases that could not be reliably resolved were preserved or excluded from the relevant analytical use and documented as residual risks.

Transactions with missing or unusable dates were excluded from the H1 analytical population. Valid-dated transactions with unmatched customer or product identifiers could still contribute to overall financial analysis, but were excluded from reliable customer- or product-level attribution where the relationship could not be established.

Negative-quantity transactions were not automatically reversed or deleted because their business meaning could not be established from the available data.

### Cost Data & Imputation

A limited number of missing product-month cost observations were imputed using available H1 cost evidence, and the affected observations were explicitly flagged.

These imputed observations introduce some uncertainty into product-level cost and profitability analysis and should be reviewed against operational or accounting records before being used for formal reporting.

### Discount Interpretation

The analysis identifies approximately **$510.8K of Distributor and Strategic discount exposure**.

This amount represents revenue surrendered through discounting and should **not be interpreted as confirmed profit loss or fully recoverable revenue**. Strategic and Key Account discounts may be commercially justified, and no approved target-discount benchmark was available to determine how much of the exposure was excessive.

### Budget Variance Comparability

Actual-vs-budget analysis was performed against the Board-approved H1 2025 Budget at the **Business Unit × Region × Month** level.

However, data and comparability limitations reduce the reliability of some budget-variance conclusions. Budget variance results were therefore treated separately from the primary profitability diagnosis and should be validated before being used for formal performance assessment.

### Profitability & Benchmark Assumptions

Contribution profitability is more directly supported by the available transaction and cost data than fully allocated operating profitability.

The **~$44K Field Services improvement opportunity** is based on an illustrative contribution-margin benchmark and should therefore be treated as a directional opportunity rather than a confirmed realized loss.

### Management Interpretation

The identified financial impacts represent different forms of exposure, measured cost impact, and improvement potential. They should not be added together into a single estimate of total financial loss.

The analysis is intended to support management decision-making and prioritization, while further operational, commercial, and accounting validation may be required before implementing specific actions or incorporating the findings into formal financial reporting.

---
## 📂 Project Files

The repository is organized to keep the **data lineage, analytical work, supporting documentation, and final reporting** clearly separated.

| Folder / File | Purpose |
|---|---|
| [`data/`](./data/) | Raw, cleaned, and analytical datasets used throughout the project |
| [`report/`](./report/) | Full PDF analysis report documenting the complete investigation |
| [`documentation/`](./documentation/) | Detailed methodology, data dictionary, data-quality assessment, and assumptions |
| [`screenshots/`](./screenshots/) | Selected screenshots providing visual evidence of the analysis |
| [`README.md`](./README.md) | Project overview, findings, financial impact, and management recommendations |
| [`.gitignore`](./.gitignore) | Files and file types intentionally excluded from version control |

### Data Versions

The [`data/`](./data/) folder follows the project's three-stage data lineage:

**Raw → Cleaned → Analytical**

- [`01-raw/`](./data/01-raw/) — Original source extracts preserved as provided
- [`02-cleaned/`](./data/02-cleaned/) — Cleaned and standardized source tables
- [`03-analytical/`](./data/03-analytical/) — Final analytical dataset used for financial analysis

### Documentation

The [`documentation/`](./documentation/) folder contains the supporting technical and analytical material behind the project:

- [`data-dictionary.md`](./documentation/data-dictionary.md)
- [`methodology.md`](./documentation/methodology.md)
- [`data-quality-assessment.md`](./documentation/data-quality-assessment.md)
- [`assumptions.md`](./documentation/assumptions.md)

The detailed documentation provides additional context without duplicating the executive-level narrative presented in this README.

---
##  Skills Demonstrated

This project demonstrates a combination of **Excel technical execution, finance and FP&A analysis, and analytical judgment**.

### Excel & Technical Skills

- Text cleaning and standardization using functions such as `TRIM`, `SUBSTITUTE`, `PROPER`, `UPPER`, and `LOWER`
- Number and date handling, coercion, and reporting-period analysis
- Excel Tables and structured references
- `XLOOKUP`, `VLOOKUP`, and `INDEX` + `MATCH` for multi-table enrichment
- `IF` / `IFS` and logical classification
- Named Ranges for relevant thresholds and assumptions
- Data preparation and structuring for reliable financial analysis

### Finance & FP&A Skills

- Revenue and discount analysis
- Cost structure and cost-pressure analysis
- Contribution profit and margin analysis
- Actual vs. Budget variance analysis
- Product, customer, regional, business-unit, and channel mix analysis
- Driver and profitability diagnostics
- Financial impact quantification
- Prioritized management recommendations

### Analytical & Professional Skills

- Business problem framing
- Data-quality assessment and investigation
- Distinguishing data issues from genuine business signals
- Handling ambiguous cases and documenting analytical judgment
- Prioritizing findings by financial materiality
- Translating analysis into management-relevant conclusions
- Clear written communication for finance leadership

##  Conclusion

The H1 2025 analysis shows that **revenue growth alone was not sufficient to deliver proportional profitability improvement at Aether Precision Systems**.

The profitability gap is driven by a combination of **discounting, product-level cost pressure, business-unit economics, and mix effects**, rather than a single underlying issue.

The analysis identified meaningful revenue exposure from discounting, measurable cost pressure on specific products, and opportunities to improve the contribution economics of lower-margin activities while protecting high-margin Software & Analytics revenue.

The investigation also demonstrated that reliable financial analysis depends on disciplined data-quality assessment. Several source-data issues required correction, exclusion, or explicit qualification before the results could be interpreted confidently.

Overall, the analysis provides management with a clearer view of **where value is being created, where it is being diluted, and which areas should receive priority attention**.

The case therefore reinforces a central FP&A principle: **strong revenue growth is valuable only when it translates into sustainable and economically attractive profitability.**
