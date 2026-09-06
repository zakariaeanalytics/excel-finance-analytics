## 1. Data Overview

The `data/` folder contains the datasets used to support the Aether Precision Systems H1 2025 finance analytics project.

The data supports the full analytical process, from source-data preservation and data-quality assessment to financial analysis and final reporting.

The project follows a structured three-stage data process:

**Raw → Cleaned → Analytical**

This organization is designed to preserve data lineage, make transformation steps traceable, and separate the original source data from the datasets prepared for analysis.


## 2. Data Architecture

The project follows a three-stage data architecture designed to preserve the original source data while creating progressively more reliable datasets for analysis.
```text
data/
├── README.md
├── 01-raw/
├── 02-cleaned/
└── 03-analytical/
```

### 3. Source Datasets

The project uses seven interconnected datasets covering sales transactions, customer information, product information, costs, budget, organizational mappings, and foreign-exchange rates.

| Dataset | Approx. Rows | Primary Purpose |
|---|---:|---|
| `01_Transactions_Raw` | ~1,310 | Primary sales transaction data, including dates, customers, products, quantities, prices, discounts, and revenue-related fields |
| `02_Customers_Raw` | 185 | Customer master data used to enrich transactions with customer attributes and classifications |
| `03_Products_Raw` | 19 | Product master data, including product classifications, pricing information, and standard cost references |
| `04_Costs_Raw` | 324 | Monthly product costs and regional/business-unit overhead used for cost and profitability analysis |
| `05_Budget_Raw` | 72 | Board-approved H1 2025 budget by Business Unit × Region × Month |
| `06_Org_Reference_Raw` | 12 | Organizational reference data used to map Business Units and Regions |
| `07_FX_Rates_Raw` | 18 | Monthly foreign-exchange rates used where currency conversion to USD is required |

### Dataset Relationships

The datasets are interconnected through common business keys and reporting dimensions.

The primary relationships include:

- Transactions linked to customers through `CustomerID`
- Transactions linked to products through `ProductID`
- Products and costs linked through product and time dimensions
- Transactions mapped to Business Unit and Region through organizational references
- Financial performance compared with budget using Business Unit × Region × Month
- Foreign-exchange rates applied by currency and reporting period where applicable

The transaction dataset serves as the primary analytical starting point, with supporting datasets used to enrich, validate, benchmark, and contextualize the financial analysis.

## 4. Data Lineage

The project maintains a clear data lineage from the original source datasets to the final analytical data used for financial analysis.

The transformation process follows three main stages:

```text
Raw Source Data
      ↓
Data Cleaning & Validation
      ↓
Cleaned Source Data
      ↓
Data Integration & Analytical Calculations
      ↓
Analytical Dataset
      ↓
Financial Analysis & Reporting
```
## 5. Data Preparation

The source datasets were prepared through a structured cleaning and validation process before being used for financial analysis.

The preparation process focused on improving data consistency, validating relationships, correcting confirmed errors, and preserving important business signals.

### Preparation Activities

The main data-preparation activities included:

- Standardizing text formatting, naming conventions, and classifications
- Converting numeric values stored as text into usable numeric fields
- Standardizing and validating dates for the H1 2025 reporting period
- Validating `CustomerID` and `ProductID` relationships
- Investigating exact duplicates and near-duplicate records
- Reviewing missing values and incomplete records
- Investigating negative quantities and suspicious prices or discounts
- Correcting confirmed `GrossRevenue` and `NetRevenue` calculation errors
- Reviewing product and cost information for consistency
- Preparing the cleaned datasets for integration and analytical calculations

### Treatment of Exceptions

Not every unusual record was automatically treated as an error.

Each material exception was investigated and classified as one of the following:

- **Confirmed data issue** — corrected where reliable evidence supported the correction
- **Business signal** — retained because the unusual value may represent a legitimate business event
- **Ambiguous case** — preserved, excluded from the relevant analysis, or explicitly flagged when the underlying meaning could not be established confidently

### Data Preparation Principle

The objective of the preparation stage was not simply to make the data look clean.

The objective was to produce datasets that were **consistent, traceable, and suitable for financial analysis while preserving the underlying business information and documenting analytical judgment**.

Detailed cleaning decisions and treatment of individual data-quality issues are documented in [`../documentation/data-quality-assessment.md`](../documentation/data-quality-assessment.md).


## 6. Data Quality

Data quality was assessed before the datasets were used for financial analysis. The objective was to identify issues that could affect the accuracy, completeness, consistency, or reliability of the analysis.

### Key Data Quality Issues

The source data contained several types of issues, including:

- Inconsistent text formatting, naming conventions, and abbreviations
- Numeric values stored as text
- Missing values and dates
- Transactions outside the H1 2025 reporting period
- Negative quantities
- Suspicious prices and discount values
- Invalid or unmatched `CustomerID` and `ProductID` values
- Exact duplicates and near-duplicate records
- Inconsistent classifications
- Missing or inconsistent cost information

### Issue Treatment

Material issues were investigated individually rather than being automatically corrected or removed.

The treatment depended on the nature and evidence available for each issue:

| Issue Type | Treatment Approach |
|---|---|
| Confirmed formatting or classification issue | Standardized to the validated format |
| Confirmed calculation error | Corrected in the analytical fields |
| Missing or unusable transaction date | Excluded from the H1 analytical population |
| Invalid or unmatched customer/product ID | Excluded from reliable customer/product attribution where the relationship could not be established |
| Negative quantity | Preserved unless its business meaning could be reliably established |
| Exact duplicate | Removed from the cleaned dataset |
| Near duplicate | Investigated individually and not automatically deleted |
| Missing cost observation | Imputed where sufficient H1 evidence supported the estimate and explicitly flagged |
| Ambiguous or unusual business event | Preserved and documented rather than automatically treated as an error |

### Data Quality Principle

A central principle of the analysis was that **anomalous does not necessarily mean incorrect**.

Each material exception was evaluated to determine whether it represented:

- A genuine data-quality issue
- A legitimate business signal
- An ambiguous case requiring further investigation

This approach reduced the risk of removing valid business information while maintaining analytical reliability.

### Residual Data Risks

Some issues could not be resolved with sufficient confidence from the available source data.

These residual risks were documented and considered when interpreting product-, customer-, regional-, cost-, and budget-level results.

Detailed issue-by-issue investigations and decisions are documented in [`../documentation/data-quality-assessment.md`](../documentation/data-quality-assessment.md).

## 7. Analytical Dataset

The `03-analytical/` folder contains the final datasets prepared for the financial analysis.

The analytical layer brings together the relevant information from the cleaned source datasets and provides the fields and calculations required to evaluate revenue, pricing, costs, profitability, budget performance, and key business drivers.

### Analytical Components

The analytical data supports the following areas:

| Analytical Area | Main Measures / Attributes |
|---|---|
| Revenue | Gross Revenue, Discount, Net Revenue |
| Pricing | Discount Rate, pricing and channel attributes |
| Cost | Variable Cost, Fixed Cost, Standard Cost |
| Profitability | Contribution Profit, Contribution Margin, Gross Profit where applicable |
| Budget Performance | Actual, Budget, Variance, Variance % |
| Business Dimensions | Product, Customer, Customer Type, Business Unit, Region, Sales Channel |
| Time | Transaction Date, Month, Reporting Period |
| Analytical Flags | Data-quality flags, classifications, and investigation indicators |

### Analytical Grain

The primary analytical grain is the **transaction level**.

Each transaction can be enriched with relevant customer, product, organizational, cost, and time attributes to support analysis across multiple business dimensions.

Where required, the transaction-level data is aggregated into reporting views such as:

- Monthly performance
- Product performance
- Customer and customer-type performance
- Business-unit performance
- Regional performance
- Sales-channel performance

### Financial Calculations

The analytical layer supports the main financial calculations used in the project:

```text
Gross Revenue
      ↓
Discount
      ↓
Net Revenue
      ↓
Variable Cost
      ↓
Contribution Profit
      ↓
Contribution Margin
```


## 8. Data Usage & Scope

The datasets are used to support the financial analysis of Aether Precision Systems for the H1 2025 reporting period, covering **1 January 2025 through 30 June 2025**.

### Reporting Scope

The analytical data supports analysis across the main business dimensions available in the source data, including:

- Business Units
- Regions
- Products
- Customers and customer types
- Sales channels
- Time periods
- Cost elements

The primary benchmark for performance evaluation is the **Board-approved H1 2025 Budget**, analyzed at the **Business Unit × Region × Month** level.

### Analytical Use

The data supports the project's main analytical areas:

| Analysis | Primary Data Used |
|---|---|
| Revenue Analysis | Transactions, Customers, Products |
| Discount & Pricing Analysis | Transactions, Customers, Products |
| Cost Analysis | Transactions, Products, Costs |
| Profitability Analysis | Transactions, Products, Costs |
| Budget Variance Analysis | Transactions, Organizational Reference, Budget |
| Regional & Business Unit Analysis | Transactions, Organizational Reference |
| Customer & Product Analysis | Transactions, Customers, Products |
| Foreign Currency Analysis | Transactions, FX Rates |

### Important Scope Considerations

Certain records have restricted analytical use because of identified data-quality limitations.

- Transactions with missing or unusable dates are excluded from the H1 analytical population.
- Transactions with unmatched `CustomerID` or `ProductID` values may contribute to overall financial analysis but are excluded from reliable customer- or product-level attribution where the relationship cannot be established.
- Negative-quantity transactions are preserved unless their business meaning can be reliably established.
- Imputed cost observations are explicitly flagged and should be validated before being used for formal reporting.
- Budget variance findings are subject to the comparability and data-quality limitations documented in the project.

### Data Usage Principle

The analytical dataset should be used within the documented scope and assumptions of the project.

Financial results derived from the data are intended for **analytical and portfolio demonstration purposes** and should be validated against operational and accounting records before being used for formal management reporting or financial decision-making.
