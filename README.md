# Power BI Inventory Management: Structured Measures for Scalability
This repository demonstrates a systematic organization of DAX measures within a Power BI Inventory Management Model.
The focus was on enhancing model usability, scalability, and maintainability by carefully structuring all business logic into meaningful Display Folders without altering the natural development flow of the measures.

##Project Overview

In complex models, poor measure organization can slow down report development and make ongoing maintenance difficult.

To counter this, I manually grouped measures into Display Folders that reflect real-world business processes around inventory management — covering stock movements, cost analysis, turnover, and operational KPIs.

By maintaining the original order of development while introducing structured folders, I achieved a balance between preserving analytical flow and optimizing for end-user navigation.

##Folder Structure
Measures were grouped into the following logical folders:

**Inventory Movement:**
Captures receipts, withdrawals, adjustments, and ending inventory quantities.

**Inventory Cost Analysis**
Focuses on weighted average cost calculations, total inventory valuation, and unit costs.

**Cost of Goods Sold (COGS) and Turnover:**
Groups measures related to stock withdrawals translated into monetary terms and sales performance over time.

**Inventory Efficiency Metrics:**
Key metrics such as Days Inventory Outstanding (DIO) and inventory turnover ratio, used to track stock holding efficiency.

**Narrative and Text Measures**
Houses dynamic text measures that support narrative-driven dashboards and custom visuals.

Each folder was named carefully to match business language, making it easier for analysts, finance teams, and business users to find and understand the measures they need.


### Here's a simple breakdown of what's happening:
* Qty Receipt, Qty Withdraw = Calculate quantity received/withdrawn based on transaction type = Straightforward CALCULATE(SUM(...)) with a filter.
* 01Qty in store (simple) = Net stock movement without considering time/previous stock = Just [Qty Receipt] - [Qty Withdraw].
* Qty in store (actual) = Rolling inventory stock considering time filter = REMOVEFILTERS + filter up to MAX(Date).
* Cost Receipt, Cost Withdraw = Sum of (Quantity × Unit Price) for Receipts/Withdrawals = SUMX used instead of SUM.
* Cost Inventory = Net inventory value at a given date = Receipt - Withdraw across time.
* COGS_Last12Months = Cost of Goods Sold over the last 12 months = Important for turnover and inventory ratios.
* 03 DIO_Last12Months, DIO_Last12Months(daily) = Days Inventory Outstanding = Two approaches: Closing/Opening vs. Daily average.
* Turnover Last12Months, Turnover Bikes Last 12M = Turnover ratio = Measures efficiency of stock movement.
* Inventory Coverage, Inventory Coverage (Monthly) = How many days/months inventory will last.	
* Inventory Coverage (Bikes) = Inventory coverage specifically for bikes.	
* MoM Cost Inventory Text = Month-over-month (MoM) cost inventory change — Text with Emojis! = Very user-friendly KPI


*This project reflects a commitment to professional modeling standards and a mindset of building for scale and sustainability.*

