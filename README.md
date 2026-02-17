# PowerBI_MQueries
## Power Query (M) Advanced Transformations Library
This repository contains a collection of custom Power Query M scripts designed to solve complex data engineering challenges in Power BI. While many transformations can be done via the UI, these scripts focus on performance optimization, dynamic logic, and "bulletproof" data cleaning that requires manual M-coding.
## 🚀 Featured M-Query Techniques
**1. Performance Optimization with <Table.Buffer>**
   - The Problem: Large merges (joins) causing slow refresh times due to repeated data scanning.
   - The Solution: Used Table.Buffer() to load lookup tables into RAM, significantly reducing the "chatty" communication between Power BI and the data source.

**2. Advanced Conditional Logic (Nested Ifs)**
   - The Problem: Complex business rules (e.g., Age Tiering or Priority Status) requiring multiple AND/OR conditions that create messy, hard-to-manage UI steps.
   - The Solution: Wrote clean, readable nested if...then...else statements within a single step to handle multi-tier categorization.
   
**3. Intelligent Data Cleaning (Text.Select)**
   - The Problem: Alphanumeric IDs (e.g., "Ref-1234-X") where numbers are inconsistent.
   - The Solution: Implemented Text.Select([Column], {"0".."9"}) to instantly strip non-numeric characters, regardless of their position.
   
**4. Case-Insensitive Filtering**
   - The Problem: Power Query is case-sensitive, meaning "Paid," "paid," and "PAID" are treated as different values.
   - The Solution: Utilized Comparer.OrdinalIgnoreCase within Table.SelectRows to create robust filters that catch all variations of a text string.

**5. Dynamic Splitting & Schema Management**
   - The Problem: Source columns that change names or positions, breaking standard "Split by Delimiter" steps.
   - The Solution: Used position-based logic and dynamic delimiters to ensure the query remains functional even if the source headers fluctuate.
   
## 🛠️ How to Use These Snippets

1. Open Power BI Desktop.
2. Go to Transform Data (Power Query Editor).
3. Click on View > Advanced Editor.
4. Copy the relevant logic from this repository into your let block.

## 🧠 Why M instead of UI?

| Feature | Power Query UI | Manual M Code |
| :--- | :--- | :--- |
| **Logic** | Limited to basic rules | Unlimited nested complexity |
| **Speed** | Can be inefficient with merges | Optimized via Buffering |
| **Maintenance** | Steps can become cluttered | Clean, documented scripts |
| **Data Integrity** | Case-sensitive (risky) | Case-insensitive (robust) |
