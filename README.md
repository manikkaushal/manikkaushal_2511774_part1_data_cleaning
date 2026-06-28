## Problem Summary
This analytics segment focuses on parsing, restructuring, and evaluating an export of retail transaction records containing complex data quality issues. The primary objective is to clean the data using Excel features, apply business rules, map performance matrices, and generate reports.

## Dataset Description
The underlying core table tracks business transactions across standard transactional vectors including unique identifiers, customer tracking names, structural segment blocks, market spaces, shipping profiles, product catalogs, line pricing, actual costs, and fulfillment metrics.

## Tools Used
* **Microsoft Excel:** Leveraged for functional evaluations, database adjustments, string formatting, date conversions, and multi-tier logical tables.

## Summary of Data Quality Issues Found
* Mixed capitalization and extra spaces across customer names and regions.
* Dates saved as text, along with a ship date occurring chronologically before an order date.
* Empty values within key variables (region, ship_mode, and discount).
* Exact duplicate rows alongside conflicting line details tied to matching order IDs.

## Key Business Insights
* **Revenue Centers:** The East region serves as the primary revenue channel, whereas the Midwestern territories face clear profit losses due to negative operational margins.
* **Inventory Allocation:** Technology channels represent the largest single revenue volume generator across all regions.
* **Fulfillment Friction:** Specific items marked as "Unknown" shipping models require review as they show strong alignment with order cancellations.

## Assumptions and Limitations
* All blank fields under the discount column were treated as 0.
* Because processing relies entirely on local grid cell formulas instead of automated data pipelines, updating the tracking report with new transactional rows requires repeating the entire workflow manually.
