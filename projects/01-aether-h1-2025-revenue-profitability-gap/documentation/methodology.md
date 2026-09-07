## 1. Purpose

This document explains the methodology used to perform the Aether Precision Systems H1 2025 financial analysis.

The methodology covers the process from data preparation and validation through financial analysis, driver investigation, financial impact assessment, and management recommendations.

The objective is to make the analysis:

- **Traceable** — key results can be connected to the underlying data and analytical steps.
- **Consistent** — financial measures and decision rules are applied using defined logic.
- **Reproducible** — another analyst can understand the main analytical process and recreate the principal calculations.
- **Transparent** — material data-quality issues, assumptions, limitations, and areas of uncertainty are explicitly documented.
- **Decision-oriented** — the analysis moves beyond descriptive reporting toward diagnosis, quantified impact, prioritization, and management action.

The methodology is designed around the central business question:

> **Why is revenue growth in H1 2025 not translating into proportional profitability improvement?**

The overall analytical sequence is:

```text
Data
  ↓
Preparation & Validation
  ↓
Data Integration
  ↓
Financial Calculations
  ↓
Workstream Analysis
  ↓
Driver Investigation
  ↓
Financial Impact Assessment
  ↓
Management Recommendations
```
## 2. Analytical Framework

The analysis follows a structured framework designed to move from reliable data toward financially relevant conclusions and actionable management decisions.

The framework is organized around four analytical layers:

### 2.1 Data Layer

The first layer establishes whether the available data is sufficiently reliable for analysis.

This includes:

- Reviewing the structure and completeness of the source datasets.
- Identifying missing, invalid, inconsistent, or duplicated records.
- Standardizing relevant fields such as dates, identifiers, names, classifications, and numeric values.
- Separating confirmed data errors from unusual but potentially valid business observations.
- Defining the analytical population used for H1 2025 reporting.

The purpose of this layer is to prevent unreliable source data from directly driving financial conclusions.

### 2.2 Financial Analysis Layer

Once the data is prepared, the analysis applies consistent financial definitions and calculations.

The principal measures include:

- Gross Revenue
- Discounts
- Net Revenue
- Variable Cost
- Contribution Profit
- Contribution Margin
- Fixed Cost
- Operating Profit approximation
- Budget Variance
- Revenue and profitability ratios

These measures are analyzed across relevant dimensions such as:

- Month
- Business Unit
- Region
- Product
- Customer
- Customer Segment
- Cost Element

This layer establishes the financial performance baseline and identifies where revenue, cost, and profitability are concentrated.

### 2.3 Diagnostic Layer

The analysis investigates:

- Revenue growth and mix changes.
- Discount and pricing behavior.
- Product and cost pressure.
- Differences in profitability across business units, products, customers, and regions.
- Potentially material financial drivers that may explain the profitability gap.
- Budget performance where actual and budget data can be reliably compared.
- Unusual patterns and anomalies requiring further investigation.
At this stage, unusual results are investigated rather than automatically interpreted as errors or problems.

### 2.4 Decision Layer

The final layer translates analytical findings into financial priorities and management actions.

The process is:

```text
Observed Result
      ↓
Driver Investigation
      ↓
Financial Impact
      ↓
Materiality / Priority
      ↓
Management Action
```

## 3. Data Preparation Method

Data preparation was performed before the financial analysis to improve data consistency, identify data-quality issues, and establish a reliable analytical population for H1 2025.

The preparation process followed these main steps:

### 3.1 Source Data Review

The source datasets were first reviewed to understand:

- Dataset structure and available fields.
- Record counts and data coverage.
- Data types and formats.
- Available business dimensions and identifiers.
- Relationships between datasets.
- Missing or incomplete information.

The seven source datasets used in the analysis were reviewed before integration and calculation.

### 3.2 Data Cleaning

The datasets were cleaned to address identified quality issues, including:

- Inconsistent capitalization and spacing.
- Abbreviated or inconsistent names.
- Numeric values stored as text.
- Mixed or inconsistent date formats.
- Missing values.
- Invalid CustomerID or ProductID values.
- Duplicate records.
- Negative quantities requiring interpretation.
- Suspicious prices or discount values.
- Inconsistent classifications across related datasets.

Cleaning was performed while preserving the original source information and documenting material changes.

### 3.3 Data Validation

After cleaning, validation checks were performed to determine whether the prepared data was suitable for analysis.

Validation included checking:

- Required fields and key identifiers.
- Date validity and reporting-period coverage.
- Numerical consistency.
- Relationships between transaction, customer, product, cost, budget, organization, and FX datasets.
- Duplicate records.
- Logical consistency of financial fields.
- Reasonableness of calculated financial values.

Data-quality issues that could materially affect interpretation were documented rather than silently corrected.

### 3.4 Treatment of Data-Quality Issues

Different types of data-quality issues were handled according to their analytical impact.

Confirmed errors were corrected where sufficient evidence existed.

Ambiguous observations were not automatically changed and were instead flagged for further review.

For example:

- Transactions with missing dates were excluded from the H1 2025 analytical population because their reporting-period classification could not be reliably established.
- Invalid CustomerID or ProductID values could remain in the overall valid-dated transaction population but were excluded from reliable customer- or product-level attribution.
- Negative quantities were preserved in the source data and were not automatically reversed because their business meaning could not be established from the available information.
- Confirmed GrossRevenue and NetRevenue calculation errors were recalculated in the analytical fields.
- Exact duplicates were removed from the cleaned dataset, while near-duplicates were not automatically deleted without sufficient evidence.
- Missing product-cost observations were addressed only where a defensible basis for imputation existed, and the imputed values were flagged.

### 3.5 Analytical Population

The final analytical population was established after applying the documented data-quality rules.

The analytical population was designed to:

- Include records that could be reliably used for H1 2025 financial analysis.
- Exclude records that could not be reliably assigned to the reporting period.
- Preserve valid financial information where only specific dimensional attributes were unreliable.
- Prevent unresolved data-quality issues from being presented as confirmed business conclusions.

This approach ensured that data limitations were incorporated into the analysis rather than hidden within the calculations.

### 3.6 Preparation Principle

The overall principle was:

> **Clean the data enough to make reliable analysis possible, without altering valid business information or making unsupported assumptions.**

The objective was not to create a perfectly uniform dataset at the expense of the original information, but to establish a controlled and documented analytical dataset suitable for financial decision-making.


## 4. Data Integration Method

The prepared datasets were integrated to create a connected analytical structure that allowed financial performance to be analyzed across products, customers, business units, regions, costs, and reporting periods.

The integration process was based on the relationships between the source datasets and their available identifiers.

### 4.1 Integration Structure

The main transaction dataset was used as the central financial activity dataset.

Supporting datasets were connected to provide additional business attributes and financial reference information.

The integration structure can be summarized as:

**Transactions → Customers**  
**Transactions → Products**  
**Transactions → Costs**  
**Transactions → Budget**  
**Transactions → Organization Reference**  
**Transactions → FX Rates**

This structure allowed transaction-level financial activity to be analyzed using additional business and financial dimensions.

### 4.2 Key Relationships

The principal relationships used in the analysis included:

- Transactions ↔ Customers through CustomerID.
- Transactions ↔ Products through ProductID.
- Transactions ↔ Costs through the applicable product, period, or cost reference.
- Transactions ↔ Organization Reference through relevant organizational dimensions.
- Actual performance ↔ Budget through common reporting dimensions such as Business Unit, Region, and Month.
- Financial values ↔ FX Rates where currency conversion was required and supported by the available data.

The relationships were validated before being used for analytical aggregation.

### 4.3 Dimension Enrichment

The integration process enriched transaction-level records with relevant business attributes.

This enabled financial measures to be analyzed across dimensions such as:

- Customer
- Product
- Business Unit
- Region
- Customer Segment
- Reporting Month
- Cost Element

This structure supported both high-level financial reporting and detailed driver investigation.

### 4.4 Handling Incomplete Relationships

Not all source records could be reliably connected across every dataset.

Where CustomerID or ProductID values were invalid or unavailable, the underlying transaction could still contribute to overall valid-dated financial analysis when appropriate.

However, such records were excluded from customer-level or product-level attribution when the corresponding relationship could not be established reliably.

This prevented incomplete identifiers from creating misleading dimensional analysis.

### 4.5 Integration Validation

After integration, validation checks were performed to ensure that:

- Key identifiers were mapped consistently.
- Related records were not unintentionally duplicated.
- Financial values remained consistent after integration.
- Dimension attributes were assigned to the appropriate records.
- Aggregated results remained reconcilable with the underlying prepared data.
- Missing relationships were identified and documented.

The integration process therefore focused on preserving the integrity of the financial data while adding the business context required for analysis.

### 4.6 Analytical Dataset

The integrated and validated data was used to support the H1 2025 financial analysis.

The resulting analytical structure supported:

- Revenue analysis.
- Discount and pricing analysis.
- Cost analysis.
- Profitability analysis.
- Budget comparison.
- Driver investigation.
- Financial impact assessment.

The analytical dataset served as the principal working layer for the financial analysis while maintaining traceability back to the prepared source datasets.


## 5. Financial Calculation Logic

The financial analysis used consistent calculation definitions to ensure that revenue, discounts, costs, profitability, and variances were measured in a controlled and comparable manner.

The calculation logic was applied to the cleaned and integrated data and was used to support the different analytical workstreams.

### 5.1 Revenue Calculations

Gross Revenue represents the value of sales before discounts.

The calculation is based on the applicable transaction quantity and selling price:

**Gross Revenue = Quantity × Unit Price**

Where transaction-level values were affected by confirmed source-data errors, the analytical revenue fields were recalculated using the validated transaction information.

Discount represents the monetary reduction applied to Gross Revenue.

**Discount = Gross Revenue × Discount Rate**

Net Revenue represents revenue after discounts:

**Net Revenue = Gross Revenue − Discount**

These measures were used to evaluate revenue performance and the effect of discounting on realized revenue.

### 5.2 Discount Rate

The overall discount rate was calculated as the proportion of Gross Revenue surrendered through discounts:

**Discount Rate = Discount ÷ Gross Revenue**

The same principle was applied across relevant business dimensions to compare discount behavior between:

- Business Units
- Regions
- Customer Segments
- Customers
- Products
- Reporting Months

Discount levels were interpreted as commercial exposure unless sufficient evidence existed to establish that a discount represented an inappropriate or avoidable concession.

### 5.3 Cost Calculations

Variable Cost represents costs that vary with the level or composition of business activity and were used in contribution analysis.

Where the relevant transaction or product cost information was available, variable cost was incorporated into the analytical dataset.

Contribution Profit was calculated as:

**Contribution Profit = Net Revenue − Variable Cost**

Contribution Margin was calculated as:

**Contribution Margin = Contribution Profit ÷ Net Revenue**

These measures were used to compare the financial economics of products, business units, customer segments, and other relevant dimensions.

### 5.4 Fixed Cost and Operating Profit Approximation

Where fixed-cost information was available and sufficiently reliable, Fixed Cost was considered separately from variable cost.

An operating profit approximation was calculated as:

**Operating Profit ≈ Contribution Profit − Fixed Cost**

This measure was treated as an approximation where the available dataset did not provide a complete accounting representation of operating profit.

The analysis therefore distinguishes between directly calculated contribution economics and any higher-level profitability approximation.

### 5.5 Budget Variance Calculations

Actual performance was compared with the available budget where the underlying actual and budget populations could be reliably aligned.

For a financial measure:

**Variance = Actual − Budget**

Percentage variance was calculated as:

**Variance % = (Actual − Budget) ÷ Budget**

Positive or negative variances were interpreted according to the financial measure being evaluated.

For example, a positive revenue variance generally indicates performance above budget, while a positive cost variance generally indicates higher-than-budget spending and therefore requires different interpretation.

Budget comparisons were not treated as definitive where data-quality or comparability limitations could materially affect the result.

### 5.6 Actual-versus-Standard Cost Comparison

Where both actual cost and standard cost information were available, the analysis compared the two values to identify potential cost pressure.

The basic calculation was:

**Cost Overrun = Actual Cost − Standard Cost**

A positive value indicates that actual cost exceeded the applicable standard cost.

The analysis used this comparison to identify products with potentially material cost pressure.

Where a standard cost value was missing but sufficient H1 2025 evidence existed to support an estimate, the value was imputed and explicitly flagged in the analytical dataset.

### 5.7 Variance and Driver Measures

Additional analytical measures were derived to support driver investigation and prioritization.

These included:

- Revenue growth or decline.
- Changes in discount rates.
- Contribution margin differences.
- Cost variances.
- Actual-versus-standard cost gaps.
- Business or product concentration measures.
- Financial impact estimates.

Derived measures were used to identify patterns and potential drivers rather than being treated as independent financial facts.

### 5.8 Classification and Flags

Analytical flags and classifications were used to identify records or groups requiring additional investigation.

Examples include:

- Data-quality flags.
- Missing-value flags.
- Imputation flags.
- Invalid identifier flags.
- Duplicate indicators.
- Potential anomaly indicators.
- Material financial-impact indicators.

Flags were used to support controlled investigation and did not automatically imply that a record represented an error or a negative business outcome.

### 5.9 Financial Interpretation Principle

Financial calculations were interpreted within their underlying business context.

A numerical difference was not automatically classified as:

- A loss
- An error
- An inefficiency
- A management problem

Instead, the analysis considered the calculation together with the relevant benchmark, business context, data quality, and available supporting evidence.

For example, a large discount amount was treated as revenue surrendered or commercial exposure unless an appropriate benchmark existed to demonstrate that the discount was excessive or inappropriate.

Similarly, an identified cost variance was treated as a potential improvement opportunity where the comparison was supported by a reliable standard or benchmark.

The objective was to ensure that financial calculations remained mathematically consistent while their interpretation remained evidence-based.
## 6. Workstream Methodology

The analysis was organized into nine interconnected workstreams. Each workstream addressed a specific component of the central business question while contributing to the overall assessment of revenue growth, profitability, financial drivers, and management priorities.

The workstreams were analyzed sequentially but were also cross-referenced where findings from one workstream affected the interpretation of another.

### 6.1 Data Quality & Reporting Readiness

The first workstream assessed whether the available data was sufficiently reliable for financial analysis and reporting.

The analysis focused on:

- Missing values.
- Invalid identifiers.
- Inconsistent classifications.
- Duplicate records.
- Formatting inconsistencies.
- Incorrect or suspicious financial values.
- Date-quality issues.
- Negative quantities.
- Missing cost observations.

Each issue was assessed according to its potential impact on the analysis.

The objective was to determine:

- Which records could be used reliably.
- Which records required correction.
- Which records required exclusion from specific analyses.
- Which issues could remain without materially affecting the analysis.
- Which unresolved issues required explicit disclosure.

This workstream established the reliability boundaries for the remaining analysis.

### 6.2 Revenue Performance

The revenue workstream evaluated the scale, composition, and evolution of H1 2025 revenue.

The analysis examined:

- Gross Revenue.
- Discounts.
- Net Revenue.
- Monthly revenue trends.
- Revenue concentration.
- Revenue by Business Unit.
- Revenue by Region.
- Revenue by Product.
- Revenue by Customer Segment.
- Revenue mix changes.

The objective was to determine whether revenue growth was broad-based or concentrated and whether the composition of revenue could help explain the profitability gap.

Revenue performance was therefore assessed not only by total value but also by its underlying mix and concentration.

### 6.3 Discount & Pricing Realization

The discount and pricing workstream evaluated the extent to which Gross Revenue was reduced before reaching Net Revenue.

The analysis examined:

- Total discount value.
- Overall discount rate.
- Discount rates by Business Unit.
- Discount rates by Region.
- Discount rates by Customer Segment.
- Discount rates by Customer.
- Discount rates by Product.
- Monthly discount patterns.

The analysis focused on identifying areas where discounting was concentrated and where commercial exposure appeared significant.

Large discount amounts were not automatically interpreted as losses or pricing errors.

Where no approved target-discount benchmark was available, discounts were treated as revenue surrendered or commercial exposure rather than confirmed profit loss.

The objective was to identify areas requiring pricing, discount-governance, or commercial review.

### 6.4 Cost Structure & Cost Pressure

The cost workstream evaluated the level and distribution of costs affecting financial performance.

The analysis examined:

- Variable Cost.
- Fixed Cost where applicable.
- Cost by Product.
- Cost by Business Unit.
- Cost by Region.
- Cost Element.
- Actual-versus-standard cost differences.
- Concentration of cost pressure.

Particular attention was given to products with material differences between actual and standard cost.

The analysis sought to distinguish normal cost variation from potentially actionable cost pressure.

Where reliable benchmark information was available, cost differences were quantified to estimate their financial significance.

### 6.5 Profitability & Margin Analysis

The profitability workstream evaluated whether revenue generation was translating into sufficient contribution economics.

The principal measures were:

- Contribution Profit.
- Contribution Margin.
- Profitability by Business Unit.
- Profitability by Product.
- Profitability by Customer Segment.
- Profitability by Region.

The analysis focused on identifying:

- High-margin businesses or products.
- Low-margin businesses or products.
- Concentrated profitability.
- Margin differences between business areas.
- Potential effects of revenue and product mix.

Contribution Margin was used as a key diagnostic measure because it relates realized Net Revenue to Variable Cost and therefore provides insight into the economics of the underlying activity.

The analysis also assessed whether certain high-margin areas represented opportunities to protect or increase profitable revenue mix.

### 6.6 Budget Variance Analysis

The budget workstream compared actual performance with the available H1 2025 budget.

The analysis considered:

- Revenue variance.
- Cost variance.
- Variance percentage.
- Variance by Business Unit.
- Variance by Region.
- Variance by Month.

Budget comparisons were performed only where the actual and budget data could be aligned with sufficient confidence.

Where dimension mismatches, incomplete data, or other comparability limitations affected interpretation, the resulting variance was treated cautiously and was not used as a primary conclusion.

The purpose of this workstream was to identify potential areas of over- or under-performance relative to management expectations while maintaining appropriate controls over comparability.

### 6.7 Driver Investigation & Anomaly Review

This workstream investigated significant patterns, unusual observations, and potential explanations identified during the previous analyses.

The investigation followed a drill-down approach:

**Observed Result → Driver Identification → Validation → Quantification → Interpretation**

Potential drivers were examined across dimensions such as:

- Business Unit.
- Region.
- Product.
- Customer.
- Customer Segment.
- Month.
- Cost Element.
- Discount behavior.

Anomalies were not automatically treated as errors.

Each unusual observation was considered as one of three possibilities:

1. A data-quality issue.
2. A genuine business signal.
3. An ambiguous case requiring further validation.

The investigation also considered alternative explanations before assigning a business interpretation.

This workstream produced the evidence used to distinguish descriptive findings from supported diagnostic conclusions.

### 6.8 Financial Impact & Prioritization

The financial impact workstream translated material findings into quantified financial exposure or opportunity estimates where sufficient evidence was available.

Potential impacts included:

- Revenue surrendered through discounting.
- Actual-versus-standard cost overruns.
- Margin gaps.
- Potential contribution opportunities.
- Concentrated financial exposures.

Each finding was assessed using factors such as:

- Financial magnitude.
- Relevance to profitability.
- Evidence strength.
- Business controllability.
- Management actionability.

Financial impacts were not automatically classified as realized losses.

Where a benchmark was unavailable, the analysis used appropriate terminology such as:

- Revenue exposure.
- Potential opportunity.
- Directional benchmark gap.
- Cost overrun.
- Financial pressure.

This distinction was used to avoid overstating the financial consequences of findings that were not fully supported by the available evidence.

### 6.9 Management Recommendations

The final workstream translated the analytical findings into practical management recommendations.

Recommendations were developed from findings that had sufficient analytical support and were linked to a specific financial or business issue.

Recommendations considered:

- The identified driver.
- Financial relevance.
- Degree of management control.
- Required follow-up investigation.
- Potential benefit.
- Risk of unintended consequences.

Recommendations were therefore designed to address the underlying drivers rather than simply the observed symptoms.

Examples of recommendation areas included:

- Strengthening discount governance.
- Investigating product cost overruns.
- Protecting and selectively expanding high-margin activities.
- Reviewing Field Services economics.
- Improving reporting and data-quality controls.

The recommendations were framed as management actions or areas for further investigation rather than assumptions about causes that could not be established from the available data.

## 7. Benchmarking Framework

Benchmarking was used to determine whether an observed financial result represented a meaningful variance, pressure, opportunity, or potential area for management attention.

The analysis did not rely on a single benchmark. Different benchmarks were used depending on the financial question and the quality of the available reference data.

### 7.1 Benchmarking Principles

A financial result was considered more meaningful when it could be compared with an appropriate and reliable reference point.

The main benchmarking principles were:

- Use the most relevant available benchmark for the specific analytical question.
- Ensure that the populations and dimensions being compared are sufficiently comparable.
- Distinguish confirmed benchmark gaps from directional estimates.
- Avoid interpreting a difference as a loss or inefficiency without an appropriate reference standard.
- Document limitations where benchmark quality is insufficient.

### 7.2 Budget Benchmark

The H1 2025 Board-approved budget was used as the primary benchmark for budget variance analysis where the actual and budget data could be reliably aligned.

The budget was structured around dimensions including:

- Business Unit
- Region
- Month

The comparison followed:

**Variance = Actual − Budget**

and, where appropriate:

**Variance % = (Actual − Budget) ÷ Budget**

Budget variance results were interpreted cautiously when data-quality or comparability limitations affected the reliability of the comparison.

### 7.3 Standard Cost Benchmark

Where applicable, actual product costs were compared with standard cost values.

The comparison followed:

**Cost Overrun = Actual Cost − Standard Cost**

This benchmark was used to identify products where actual cost exceeded the expected standard cost.

The P-SI-004 and P-SI-007 analysis used this type of benchmark and identified a combined actual-versus-standard cost overrun of approximately $49.5K.

This was treated as a directly benchmarked cost pressure rather than an assumed accounting loss.

### 7.4 Internal Performance Benchmark

Internal comparisons were also used where an external benchmark was unavailable or less relevant.

Examples included comparisons between:

- Business Units.
- Products.
- Regions.
- Customer Segments.
- Customers.
- Reporting Months.

For example, differences in Contribution Margin between Business Units provided an internal benchmark for evaluating relative profitability.

Software & Analytics and Field Services were compared using their contribution-margin performance to identify differences in underlying economics.

### 7.5 Trend Benchmark

Historical or sequential performance within the H1 2025 reporting period was used to identify changes over time.

Monthly analysis was used to examine:

- Revenue movements.
- Discount behavior.
- Cost changes.
- Profitability changes.
- Emerging patterns or anomalies.

Month-to-month comparisons were treated as trend indicators rather than proof of structural changes unless supported by additional evidence.

### 7.6 Benchmark Limitations

Not all findings could be evaluated against a definitive benchmark.

For example, the analysis identified approximately $510.8K of discounts associated with Distributor and Strategic customers.

However, no approved target-discount benchmark was available to establish that this entire amount represented excessive discounting.

Therefore, the amount was treated as:

**Revenue surrendered / commercial exposure**

rather than:

**Confirmed profit loss**

Similarly, the Field Services margin comparison was used to identify a directional opportunity rather than a confirmed financial loss.

### 7.7 Benchmark Selection Principle

The benchmark selected for each analysis depended on the question being answered.

The general hierarchy was:

**Approved Budget / Standard → Reliable Internal Comparison → Trend Analysis → Directional Reference**

The stronger and more directly relevant the benchmark, the stronger the resulting financial conclusion could be.

Where no sufficiently reliable benchmark existed, the analysis explicitly reduced the strength of the conclusion rather than presenting an unsupported estimate as a confirmed financial impact.
## 8. Evidence & Validation Approach

The analysis used an evidence-based validation approach to ensure that major findings were supported by the underlying data and that conclusions were not based solely on isolated observations.

### 8.1 Evidence Hierarchy

Analytical conclusions were supported using evidence from the prepared and integrated datasets, financial calculations, comparisons, and relevant benchmarks.

The strength of a conclusion depended on the quality and directness of the supporting evidence.

The general evidence hierarchy was:

- Directly calculated financial result.
- Result supported by a reliable benchmark.
- Result supported by multiple consistent analytical views.
- Directional indication requiring further validation.
- Unresolved or ambiguous observation.

The stronger the evidence, the stronger the corresponding management conclusion could be.

### 8.2 Reconciliation Checks

Key financial measures were reconciled against the underlying analytical data to verify that calculations and aggregations remained consistent.

Checks included:

- Gross Revenue totals.
- Discount totals.
- Net Revenue totals.
- Variable Cost totals.
- Contribution Profit and Contribution Margin calculations.
- Aggregations by major business dimensions.
- Reconciliation between transaction-level and summarized results.

These checks were used to identify calculation errors, unintended exclusions, or integration issues.

### 8.3 Cross-Validation of Findings

Important findings were reviewed across multiple analytical dimensions where possible.

For example, a profitability issue could be examined by:

- Business Unit.
- Product.
- Region.
- Customer Segment.
- Month.

Cross-validation helped determine whether an observed pattern was isolated or part of a broader financial trend.

### 8.4 Benchmark Validation

Where a benchmark was available, the observed result was compared against the relevant reference point.

Examples included:

- Actual versus Budget.
- Actual Cost versus Standard Cost.
- Contribution Margin comparisons between Business Units.
- Month-to-month performance comparisons.

Benchmark reliability was assessed before using the comparison to support a strong conclusion.

### 8.5 Anomaly Validation

Unusual observations were investigated before being classified as business problems.

The validation process considered:

- Whether the observation was caused by a data-quality issue.
- Whether the value was supported by related records.
- Whether the observation represented a genuine business pattern.
- Whether an alternative explanation was possible.
- Whether the financial magnitude justified further investigation.

This approach reduced the risk of converting isolated or erroneous observations into unsupported conclusions.

### 8.6 Financial Impact Validation

Financial impact estimates were reviewed to determine whether the calculation was based on a sufficiently reliable reference point.

Where an approved benchmark existed, the resulting financial impact could be presented as a quantified variance or overrun.

Where no reliable benchmark existed, the result was presented using more cautious terminology such as:

- Financial exposure.
- Potential opportunity.
- Directional gap.
- Cost pressure.
- Revenue surrendered.

This distinction was particularly important for discount analysis, where the absence of an approved target-discount benchmark prevented the full discount amount from being classified as confirmed profit loss.

### 8.7 Conclusion Validation

Before being incorporated into the final recommendations, major findings were reviewed against the original business question:

> **Why is revenue growth in H1 2025 not translating into proportional profitability improvement?**

A finding was considered suitable for management discussion when it:

- Was supported by the available data.
- Had a clear connection to the business question.
- Had sufficient analytical evidence.
- Had a meaningful financial or operational implication.
- Did not rely on unsupported assumptions.

Where these conditions were not fully met, the finding was presented as directional, subject to validation, or as an area requiring further investigation.

### 8.8 Validation Principle

The overall validation principle was:

> **The strength of the conclusion should not exceed the strength of the evidence supporting it.**

This principle was applied throughout the analysis to maintain analytical credibility, avoid overstatement, and ensure that management recommendations were grounded in defensible evidence.

## 9. Analytical Decision Rules

Analytical decision rules were used to maintain consistency when interpreting financial results, data-quality issues, anomalies, benchmarks, and potential financial impacts.

The purpose of these rules was to ensure that conclusions were based on defined criteria rather than subjective judgment alone.

### 9.1 Data Inclusion Rule

A record was included in the H1 2025 analytical population when the information required for the specific analysis was sufficiently reliable.

Records were excluded from a specific analysis when a material data-quality issue prevented reliable interpretation.

An exclusion from one analysis did not automatically require exclusion from all other analyses.

### 9.2 Missing Data Rule

Missing values were assessed according to their analytical importance.

Where the missing value did not prevent reliable analysis, the record could remain in the analytical population.

Where the missing value prevented reliable classification or calculation, the record was excluded from the affected analysis or flagged for further review.

No value was imputed unless sufficient evidence existed to support a defensible estimate.

### 9.3 Identifier Rule

Invalid or missing CustomerID and ProductID values were treated according to the level of analysis being performed.

Where the transaction-level financial information remained valid, the record could contribute to overall financial totals.

However, the record was excluded from customer-level or product-level attribution when the corresponding identifier could not be reliably established.

### 9.4 Anomaly Classification Rule

An unusual observation was not automatically classified as an error.

Each anomaly was assessed as one of the following:

- Data-quality issue.
- Potential business signal.
- Ambiguous observation requiring further validation.

This rule prevented unusual values from being incorrectly converted into business conclusions.

### 9.5 Benchmark Rule

A variance was considered more decision-relevant when it could be compared with a reliable and appropriate benchmark.

Preferred benchmarks included:

- Approved Budget.
- Standard Cost.
- Reliable internal comparison.
- Historical or monthly trend.

Where no sufficiently reliable benchmark existed, the finding was described as directional or potential rather than confirmed.

### 9.6 Materiality Rule

Findings were prioritized according to both financial magnitude and business relevance.

A larger financial amount generally received greater attention, but magnitude alone did not determine priority.

Priority also considered:

- Relevance to profitability.
- Evidence strength.
- Business controllability.
- Potential management impact.
- Reliability of the underlying benchmark.

### 9.7 Financial Impact Rule

A financial impact was presented as a confirmed variance, overrun, exposure, or opportunity only when the available evidence supported that interpretation.

Where evidence was insufficient, more cautious terminology was used.

For example:

**Confirmed cost overrun**

was used when actual cost could be reliably compared with a relevant standard.

**Revenue exposure / revenue surrendered**

was used when discounts were quantified but no reliable target-discount benchmark existed.

**Directional opportunity**

was used when a potential financial improvement could be estimated but could not be established as a confirmed recoverable amount.

### 9.8 Causality Rule

A statistical or financial relationship was not automatically interpreted as proof of causation.

Where the data demonstrated a pattern but did not establish the underlying cause, the conclusion was framed as:

- An observed relationship.
- A potential driver.
- A hypothesis requiring further investigation.

This rule was particularly important when interpreting relationships between revenue, discounting, cost, and profitability.

### 9.9 Recommendation Rule

A management recommendation was developed only when a finding had sufficient analytical support and a clear connection to a business or financial issue.

Recommendations were therefore linked to:

**Finding → Evidence → Financial Relevance → Action**

Where the evidence was insufficient to support a specific action, the recommendation was framed as a request for further investigation or validation rather than as a definitive management decision.

### 9.10 Decision Confidence Rule

The confidence of a conclusion was aligned with the quality of the underlying evidence.

The general principle was:

**Strong Evidence → Strong Conclusion**

**Moderate Evidence → Qualified Conclusion**

**Limited Evidence → Directional Finding / Further Validation**

This ensured that the analytical interpretation did not exceed what the available data could reasonably support.

### 9.11 Overall Decision Principle

The overall decision rule applied throughout the analysis was:

> **Prefer a narrower, evidence-supported conclusion over a broader conclusion based on unsupported assumptions.**

This principle was used to maintain analytical integrity, prevent overstatement, and support recommendations that could be defended using the available data.


## 10. Reproducibility

The analysis was structured to make the principal analytical process understandable and reproducible by another analyst using the same source data, documented assumptions, and calculation logic.

Reproducibility was supported through clear data lineage, documented preparation rules, defined financial calculations, explicit analytical decision rules, and separation between source data and analytical outputs.

### 10.1 Source Data Traceability

The analysis maintained a clear relationship between the original source datasets and the resulting analytical data.

The main data flow was:

**Raw Data → Cleaned Data → Analytical Data → Analysis & Reporting**

The raw datasets were preserved separately from the cleaned and analytical versions to maintain source traceability.

### 10.2 Data Preparation Traceability

Material data-preparation decisions were documented so that another analyst could understand how the analytical population was established.

This includes the treatment of:

- Missing values.
- Invalid identifiers.
- Duplicate records.
- Negative quantities.
- Inconsistent classifications.
- Confirmed calculation errors.
- Missing product-cost observations.
- Records excluded from specific analyses.

Where an analytical adjustment or imputation was performed, the treatment was documented and flagged rather than applied invisibly.

### 10.3 Calculation Reproducibility

The principal financial measures were based on explicitly defined formulas documented in this methodology.

These include:

- Gross Revenue.
- Discount.
- Net Revenue.
- Variable Cost.
- Contribution Profit.
- Contribution Margin.
- Operating Profit approximation.
- Budget Variance.
- Actual-versus-Standard Cost Overrun.

Using the same source data and calculation definitions should allow another analyst to reproduce the principal financial results, subject to the documented data-quality limitations and assumptions.

### 10.4 Analytical Traceability

Major conclusions were designed to remain traceable to the analytical evidence supporting them.

The general chain was:

**Source Data → Prepared Data → Financial Measure → Analytical Finding → Financial Impact → Recommendation**

This structure makes it possible to move from a management recommendation back to the financial finding and ultimately to the underlying data.

### 10.5 Documentation Traceability

Supporting documentation was maintained separately from the main project narrative.

The project documentation includes:

- `data-dictionary.md` — definitions of source and analytical fields.
- `methodology.md` — analytical methods, calculation logic, benchmarks, validation rules, and decision rules.
- `data-quality-assessment.md` — identified data-quality issues and their treatment.
- `assumptions.md` — material assumptions and analytical limitations.

Together, these documents provide the supporting methodological context for the project.

### 10.6 Reproduction Requirements

A complete reproduction of the analysis requires:

- The available raw datasets.
- The cleaned dataset.
- The analytical dataset.
- The documented data-preparation rules.
- The financial calculation definitions.
- The benchmarking framework.
- The analytical decision rules.
- The documented assumptions and limitations.

Differences in results may occur if the underlying source data, preparation rules, or assumptions are changed.

### 10.7 Reproducibility Limitations

Reproducibility is subject to limitations where the source data does not contain sufficient information to establish a definitive business interpretation.

Examples include:

- Ambiguous transaction records.
- Missing or invalid identifiers.
- Limited commercial context for discount decisions.
- Incomplete budget comparability.
- Missing external benchmarks.
- Assumptions required for selected cost observations.

In such cases, the reproducible output is the documented analytical treatment and resulting evidence, rather than an unsupported interpretation of the underlying business cause.

### 10.8 Overall Reproducibility Principle

The overall principle was:

> **Another analyst should be able to understand what was done, why it was done, which rules were applied, and where the evidence supports or limits the conclusions.**

The objective is not only to reproduce individual calculations, but to make the overall analytical reasoning sufficiently transparent for review, validation, and future extension.
