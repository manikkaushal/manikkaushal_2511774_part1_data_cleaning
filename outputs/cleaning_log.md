# Cleaning Log - Part 1 (Excel Validation Phase)

## 1. List of Issues Found
* **Text Noise & Structural Inconsistency:** customer_name and segment fields were plagued with irregular spaces, trailing pads, and fluctuating lower/upper casings. Category listings contained mixed name types like "Tech" vs "Technology".
* **Corrupt Shipping Schedules:** order_date and ship_date fields were extracted purely as plain text strings. Row 4 (ORD003) specifically shows an invalid logistical anomaly where the fulfillment date precedes the placement timeline.
* **Structural Blanks:** Blank data fields detected within the region, ship_mode, and discount columns.
* **Duplicate Entanglements:** Identical row repetitions (ORD001) alongside conflicting variable metrics assigned to matching transaction IDs (ORD016).

## 2. Cleaning Actions Performed
* Applied cell formatting strings utilizing =TRIM(PROPER()) dynamically to build baseline strings. Cleaned values were then re-pasted onto raw tracks as standalone strings. Consolidated "Tech" strings to "Technology" globally using **Find and Replace**.
* standardizing dates via Excel's **Text to Columns (MDY)** feature to build authentic system serial numbers.
* Created a tracking logic equation for timeline tracking variations via subtraction: =Ship_Date - Order_Date.
* Substituted empty text blocks found inside region and ship_mode columns with an explicit "Unknown" marker field.
* Dropped exact duplicate data chains using Excel's built-in duplicate utility, while retaining mixed transactional rows under an active flag condition.

## 3. Business Rules Applied
* Blank inputs for discount were defaulted to 0.0% assuming no reduction was applied.
* Out-of-bounds discount integers (e.g., 20) were structurally managed as decimal formats by scaling them downwards (/100). Negative variables were overwritten to zero baseline levels.
* Target transaction outputs linked to "Cancelled" or "Failed" tags were preserved in database tables for documentation integrity but dynamically filtered out of summary visual reports.

## 4. Assumptions & Process Limitations
* **Assumptions:** Any discount input exceeding 1.0 were assumed to represent an unintended percentage notation error instead of a direct dollar offset.
* **Limitations:** The cleaning procedures executed are completely static and tightly bound to standard grid cells. If fresh dataset additions are pumped into the raw source file, the standard formula structures, manual text conversions, and filtering operations must be executed manually from the beginning.