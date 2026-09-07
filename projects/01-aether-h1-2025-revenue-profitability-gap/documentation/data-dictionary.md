# Data Dictionary

## 1. Purpose

This document defines the fields used across the Aether Precision Systems H1 2025 financial analysis.

It provides a consistent reference for the source datasets, their business meaning, data types, analytical roles, key relationships, and derived financial measures used throughout the project.

The dictionary is designed to support:

- Data preparation and validation
- Data integration and enrichment
- Financial analysis
- Reproducibility and traceability
- Clear interpretation of the analytical dataset

The source data is organized into seven interconnected datasets covering transactions, customers, products, costs, budget, organizational references, and foreign-exchange rates.

---

## 2. Data Dictionary Structure

The dictionary uses the following attributes where applicable:

| Attribute | Description |
|---|---|
| **Dataset** | Source dataset containing the field |
| **Field** | Field name used in the source or analytical layer |
| **Definition** | Business meaning of the field |
| **Data Type** | Expected data type |
| **Role** | Key, attribute, dimension, or measure |
| **Source Stage** | Raw, Cleaned, or Analytical |
| **Analytical Use** | Main purpose of the field in the analysis |
| **Treatment / Notes** | Important cleaning, validation, or interpretation considerations |

---

## 3. Transactions Dataset

**Source sheet:** `01_Transactions_Raw`

**Approximate records:** 1,310 transactions

The transaction dataset is the primary financial fact source for the project. It contains individual sales transactions and provides the main foundation for revenue, discount, customer, product, regional, business-unit, channel, and profitability analysis.

| Field | Definition | Data Type | Role | Source Stage | Analytical Use | Treatment / Notes |
|---|---|---|---|---|---|---|
| `TransactionID` | Unique identifier assigned to a sales transaction | Text | Key | Raw → Cleaned | Transaction traceability and duplicate investigation | Used to identify and investigate exact duplicates |
| `TransactionDate` | Date associated with the transaction | Date | Time dimension | Raw → Cleaned | H1 2025 filtering and monthly analysis | Missing or unusable dates are excluded from the H1 analytical population |
| `CustomerID` | Identifier linking the transaction to a customer | Text | Foreign Key | Raw → Cleaned | Customer-level analysis | Invalid or unmatched IDs are excluded from reliable customer attribution |
| `ProductID` | Identifier linking the transaction to a product | Text | Foreign Key | Raw → Cleaned | Product-level analysis and cost enrichment | Invalid or unmatched IDs are excluded from reliable product attribution |
| `Region` | Region associated with the transaction | Text | Dimension | Raw → Cleaned | Regional performance and mix analysis | Text formatting and classification inconsistencies were reviewed |
| `BusinessUnit` | Business unit associated with the transaction | Text | Dimension | Raw → Cleaned | Business-unit revenue and profitability analysis | Variants such as abbreviated BU names were standardized where supported |
| `SalesChannel` | Commercial channel through which the transaction was sold | Text | Dimension | Raw → Cleaned | Channel mix and discount analysis | Formatting inconsistencies were standardized |
| `Quantity` | Quantity associated with the transaction | Numeric | Measure | Raw → Cleaned | Volume and revenue analysis | Negative quantities were preserved when business meaning could not be established |
| `UnitPrice` | Actual selling price per unit recorded for the transaction | Numeric | Measure | Raw → Cleaned | Pricing realization and anomaly analysis | Suspicious values were investigated before interpretation |
| `ListPrice` | Reference/list price per unit for the transaction | Numeric | Measure | Raw → Cleaned | Gross revenue and discount analysis | Used as a pricing reference |
| `GrossRevenue` | Revenue before discounting | Numeric | Measure | Raw → Analytical | Revenue analysis | Confirmed calculation issues were corrected in analytical fields |
| `DiscountAmount` | Monetary discount applied to the transaction | Numeric | Measure | Raw → Analytical | Discount and pricing realization analysis | Used to quantify revenue surrendered through discounts |
| `NetRevenue` | Revenue after discount | Numeric | Measure | Raw → Analytical | Revenue and profitability analysis | Confirmed calculation issues were corrected in analytical fields |
| `Currency` | Currency in which the transaction is recorded | Text | Attribute | Raw → Analytical | Currency analysis and optional USD conversion | Linked to FX rates by currency and reporting period |
| `Salesperson` | Salesperson or commercial owner associated with the transaction | Text | Attribute | Raw → Cleaned | Supporting commercial analysis | Name-format inconsistencies may require standardization |
| `ContractType` | Commercial contract or order arrangement associated with the transaction | Text | Attribute | Raw → Cleaned | Contract and pricing context | Missing values may remain where source information is unavailable |
| `CustomerSegment` | Industry/customer segment associated with the transaction | Text | Dimension | Raw → Cleaned | Segment mix and profitability analysis | Standardized where classification inconsistencies were identified |

---

## 4. Customers Dataset

**Source sheet:** `02_Customers_Raw`

**Approximate records:** 185 customers

The customer master enriches transactions with customer attributes used for segmentation, commercial analysis, and customer-level profitability interpretation.

| Field | Definition | Data Type | Role | Source Stage | Analytical Use | Treatment / Notes |
|---|---|---|---|---|---|---|
| `CustomerID` | Unique identifier for a customer | Text | Key | Raw → Cleaned | Transaction-to-customer relationship | Used as the primary customer join key |
| `CustomerName` | Customer's registered or reported name | Text | Attribute | Raw → Cleaned | Customer identification and reporting | Leading/trailing spaces and naming variants were reviewed |
| `CustomerSegment` | Industry or market segment associated with the customer | Text | Dimension | Raw → Cleaned | Segment analysis | Capitalization and naming consistency were reviewed |
| `CustomerType` | Commercial classification of the customer | Text | Dimension | Raw → Cleaned | Discount and profitability analysis | Includes classifications such as Strategic, Key Account, Standard, and Emerging |
| `Region` | Customer's associated region | Text | Dimension | Raw → Cleaned | Regional customer analysis | Regional naming inconsistencies were standardized where supported |
| `Industry` | Industry classification of the customer | Text | Dimension | Raw → Cleaned | Industry-level analysis | Used to contextualize customer and revenue performance |
| `AccountStatus` | Current account status | Text | Attribute | Raw → Cleaned | Customer-status analysis | Used as supporting customer context |
| `PrimaryContact` | Primary contact associated with the account | Text | Attribute | Raw → Cleaned | Reference information | Not a primary financial-analysis field |
| `CreditLimit` | Customer credit limit | Numeric | Measure / Attribute | Raw → Cleaned | Supporting customer-risk analysis | Values may require numeric coercion where stored as text or currency-formatted strings |

---

## 5. Products Dataset

**Source sheet:** `03_Products_Raw`

**Approximate records:** 19 products

The product master provides product classifications, list-price references, and standard cost inputs used throughout the profitability analysis.

| Field | Definition | Data Type | Role | Source Stage | Analytical Use | Treatment / Notes |
|---|---|---|---|---|---|---|
| `ProductID` | Unique identifier for a product | Text | Key | Raw → Cleaned | Transaction-to-product relationship | Used as the primary product join key |
| `ProductName` | Product name | Text | Attribute | Raw → Cleaned | Product reporting and analysis | Leading/trailing spaces and naming variants were reviewed |
| `Category` | High-level product category | Text | Dimension | Raw → Cleaned | Product mix and category analysis | Classification inconsistencies were standardized where supported |
| `Family` | Product family or functional grouping | Text | Dimension | Raw → Cleaned | Product-family analysis | Naming and capitalization inconsistencies were reviewed |
| `BU` | Business unit associated with the product | Text | Dimension | Raw → Cleaned | Business-unit mapping and profitability | Used to support product-to-BU classification |
| `ListPrice` | Standard/list selling price associated with the product | Numeric | Measure | Raw → Cleaned | Pricing and revenue analysis | Used as a pricing reference |
| `StdVarCost` | Standard variable cost per unit | Numeric | Measure | Raw → Cleaned | Standard-cost benchmarking and profitability analysis | P-SI-008 required a supported standard-cost treatment |
| `StdFixedAlloc` | Standard fixed-cost allocation per unit | Numeric | Measure | Raw → Cleaned | Profitability analysis | Used where fixed allocation is applicable |

---

## 6. Costs Dataset

**Source sheet:** `04_Costs_Raw`

**Approximate records:** 324 cost observations

The costs dataset provides monthly standard and actual cost information used to investigate cost pressure and profitability.

| Field | Definition | Data Type | Role | Source Stage | Analytical Use | Treatment / Notes |
|---|---|---|---|---|---|---|
| `CostID` | Unique identifier for a cost record | Text | Key | Raw → Cleaned | Cost-record traceability | Used to identify individual cost observations |
| `Period` | Reporting month associated with the cost record | Text / Period | Time dimension | Raw → Cleaned | Monthly cost analysis | Stored using a `YYYY-MM` period format |
| `ProductID` | Product associated with the cost record | Text | Foreign Key | Raw → Cleaned | Product-cost relationship | Used to connect cost data to products |
| `CostCategory` | Category describing the cost, such as variable COGS or fixed allocation | Text | Dimension | Raw → Cleaned | Cost classification | Capitalization and naming variants were standardized |
| `CostType` | Broad classification of the cost as variable or fixed | Text | Dimension | Raw → Cleaned | Contribution and profitability analysis | Used to separate variable and fixed cost behavior |
| `StandardCost` | Benchmark cost used for comparison | Numeric | Measure | Raw → Cleaned | Actual-vs-standard cost analysis | Primary benchmark for identifying cost overruns |
| `ActualCost` | Actual cost recorded for the product-period observation | Numeric | Measure | Raw → Cleaned | Cost pressure analysis | Used to quantify actual-vs-standard differences |
| `CostCenter` | Cost-center identifier associated with the observation | Text | Attribute | Raw → Cleaned | Organizational cost analysis | Supports cost-center and organizational mapping |
| `Notes` | Additional contextual information about the cost observation | Text | Attribute | Raw → Cleaned | Investigation and interpretation | Supporting field rather than a primary financial measure |

---

## 7. Budget Dataset

**Source sheet:** `05_Budget_Raw`

**Approximate records:** 72 budget observations

The budget dataset contains the Board-approved H1 2025 financial benchmark used for actual-vs-budget analysis.

| Field | Definition | Data Type | Role | Source Stage | Analytical Use | Treatment / Notes |
|---|---|---|---|---|---|---|
| `BudgetID` | Unique identifier for a budget record | Text | Key | Raw → Cleaned | Budget-record traceability | Used to identify individual budget observations |
| `Period` | Reporting month associated with the budget | Text / Period | Time dimension | Raw → Cleaned | Monthly budget comparison | Used as part of the Business Unit × Region × Month benchmark |
| `BusinessUnit` | Business unit covered by the budget record | Text | Dimension | Raw → Cleaned | BU budget analysis | Naming variants were standardized where supported |
| `Region` | Region covered by the budget record | Text | Dimension | Raw → Cleaned | Regional budget analysis | Used as part of the primary benchmark grain |
| `RevenueBudget` | Budgeted revenue amount | Numeric | Measure | Raw → Cleaned | Revenue variance analysis | Compared with actual revenue |
| `VariableCostBudget` | Budgeted variable cost | Numeric | Measure | Raw → Cleaned | Variable-cost variance analysis | Compared with actual variable cost |
| `FixedCostBudget` | Budgeted fixed cost | Numeric | Measure | Raw → Cleaned | Fixed-cost variance analysis | Compared with actual fixed cost |
| `ContributionProfitTarget` | Budgeted contribution profit target | Numeric | Measure | Raw → Cleaned | Contribution-profit variance analysis | Primary contribution benchmark |
| `OperatingProfitTarget` | Budgeted operating-profit target | Numeric | Measure | Raw → Cleaned | Operating-profit comparison | Used with caution because of budget comparability limitations |
| `Version` | Version identifier for the budget | Text | Attribute | Raw → Cleaned | Benchmark validation | Board-approved H1 2025 version used as the primary benchmark |

---

## 8. Organization Reference Dataset

**Source sheet:** `06_Org_Reference_Raw`

**Approximate records:** 12 organizational mappings

The organizational reference table provides standardized Business Unit, regional, management, and cost-center mappings.

| Field | Definition | Data Type | Role | Source Stage | Analytical Use | Treatment / Notes |
|---|---|---|---|---|---|---|
| `BusinessUnit` | Standard business-unit name | Text | Dimension | Raw → Cleaned | Organizational mapping | Used to standardize BU references |
| `BU_Code` | Short code representing the business unit | Text | Key / Attribute | Raw → Cleaned | Compact BU mapping | Examples include SI, SA, and FS |
| `Region` | Standard regional name | Text | Dimension | Raw → Cleaned | Regional mapping | Used to standardize regional references |
| `RegionCode` | Short code representing the region | Text | Attribute | Raw → Cleaned | Regional mapping | Used where a coded representation is required |
| `PrimaryManager` | Primary manager associated with the BU-region combination | Text | Attribute | Raw → Cleaned | Organizational reference | Supporting management context |
| `FinancePartner` | Finance partner assigned to the BU-region combination | Text | Attribute | Raw → Cleaned | Finance ownership context | Supporting organizational context |
| `CostCenterPrefix` | Prefix used to associate cost centers with BU-region combinations | Text | Attribute / Mapping Key | Raw → Cleaned | Cost and organizational mapping | Helps connect cost information with organizational dimensions |

---

## 9. FX Rates Dataset

**Source sheet:** `07_FX_Rates_Raw`

**Approximate records:** 18 FX observations

The FX dataset provides monthly currency-to-USD exchange rates used where transactions require conversion to a common reporting currency.

| Field | Definition | Data Type | Role | Source Stage | Analytical Use | Treatment / Notes |
|---|---|---|---|---|---|---|
| `Period` | Reporting month associated with the exchange rate | Text / Period | Time dimension | Raw → Cleaned | Period-specific FX matching | Matched to transaction reporting period |
| `Currency` | Currency code for the exchange-rate observation | Text | Dimension | Raw → Cleaned | Currency matching | Used with Period as the FX lookup key |
| `RateToUSD` | Exchange rate used to express the currency relative to USD | Numeric | Measure | Raw → Analytical | USD conversion where applicable | USD observations use a rate of 1 |

---

## 10. Derived Analytical Fields

The analytical dataset extends the source fields with calculated measures and classification fields used to perform the financial analysis.

The exact implementation may vary by analytical workbook sheet, but the principal calculations and concepts are:

| Analytical Field / Measure | Definition | Calculation / Logic | Analytical Purpose |
|---|---|---|---|
| `GrossRevenue` | Revenue before discounts | Quantity × ListPrice, subject to validated transaction logic | Measures top-line revenue before discounting |
| `DiscountAmount` | Monetary discount applied | Validated transaction discount amount | Measures revenue surrendered through discounts |
| `NetRevenue` | Revenue after discount | Gross Revenue − Discount Amount | Measures realized revenue |
| `DiscountRate` | Discount relative to gross revenue | Discount Amount ÷ Gross Revenue | Evaluates pricing realization |
| `VariableCost` | Variable cost associated with the transaction or analytical observation | Derived from relevant product-period cost information | Supports contribution analysis |
| `FixedCost` | Fixed-cost component allocated to the transaction or analytical observation | Derived from applicable fixed-cost allocation | Supports broader profitability analysis |
| `ContributionProfit` | Revenue remaining after variable cost | Net Revenue − Variable Cost | Measures contribution economics |
| `ContributionMargin` | Contribution profit as a percentage of net revenue | Contribution Profit ÷ Net Revenue | Compares profitability across dimensions |
| `GrossProfit` | Gross profit where COGS-based calculation is applicable | Revenue − applicable COGS | Supports gross-profit analysis where sufficiently supported |
| `OperatingProfit` | Approximate operating profit where supported | Contribution Profit − relevant fixed costs / operating costs | Used with appropriate caveats |
| `BudgetVariance` | Difference between actual and budget | Actual − Budget | Identifies favorable or unfavorable financial deviations |
| `BudgetVariancePct` | Budget variance relative to budget | Variance ÷ Budget | Normalizes budget-performance comparison |
| `Month` | Monthly reporting period derived from the transaction date | Derived from `TransactionDate` | Supports monthly trends and budget matching |
| `ReportingPeriod` | H1 2025 inclusion indicator / reporting-period classification | Based on validated transaction date | Controls analytical population |
| `FXRateToUSD` | Period-specific exchange rate used for USD conversion | Matched by Currency + Period | Supports common-currency analysis |
| `MarginClassification` | Category assigned to profitability based on defined thresholds | Threshold-based classification | Supports margin segmentation and prioritization |
| `PriorityClassification` | Category used to rank issues or opportunities | Defined materiality / priority rules | Supports financial-impact prioritization |
| `FavorableUnfavorableFlag` | Indicates direction of a relevant variance | Based on the applicable financial metric | Supports variance interpretation |
| `DataQualityFlag` | Indicator showing whether an observation requires special treatment or review | Based on documented data-quality rules | Preserves transparency around exceptions |
| `InvestigationFlag` | Indicator identifying records requiring further review | Based on anomaly or exception logic | Supports driver investigation |

### Derived Measure Principle

Derived financial measures should be calculated from validated source information and documented business rules rather than manually entered values.

Where an assumption or estimation is required, the relevant observation should be explicitly flagged and documented.

---

## 11. Key Relationships

The Aether data model is built around a set of primary and supporting relationships.

### Transaction Relationships

```text
Transactions
    │
    ├── CustomerID ─────→ Customers
    │
    └── ProductID ──────→ Products
