# 📊 SQL Problem Solving Portfolio

A structured collection of SQL query solutions built entirely **from scratch**. This repository tracks my journey in solving data manipulation, aggregation, and query optimization challenges from platforms like StrataScratch, DataLemur, and LeetCode.

---

## 🛠️ Tech Stack & Skills
- **Dialects:** PostgreSQL / MySQL / MS SQL Server
- **Core Concepts:** Common Table Expressions (CTEs), Advanced Window Functions, Multi-table Joins, Subqueries, Row/Column Pivot, Query Performance Tuning

---

## 📂 Repository Structure

The project is organized by platform and difficulty level to ensure seamless navigation:

```text
├── .github/
├── DataLemur/
│   ├── Easy/
│   ├── Medium/
│   └── Hard/
├── LeetCode/
│   ├── Easy/
│   ├── Medium/
│   └── Hard/
└── StrataScratch/
    ├── Easy/
    │   ├── user_streaks/
    │   │   ├── solution.sql
    │   │   └── README.md
    │   └── ...
    ├── Medium/
    └── Hard/
```

---

## 📝 Solution Template

Every individual problem folder contains a dedicated query file (`solution.sql`) and a detailed analysis markdown file (`README.md`). I use the following uniform structure to document my thought process:

### 1. Problem Statement
> *Paste the exact problem description, context, and any specific constraints given by the platform here.*

### 2. Input Data & Schema
Provide a quick visual overview of the tables involved:
*   **`table_name`**
    *   `column_1` (DATETIME) - Brief description.
    *   `column_2` (INT) - Primary Key.

### 3. Expected Output
Show what the final dataset should look like after running the query.

### 4. Code Solution (From Scratch)
```sql
-- Your optimized SQL query goes here
WITH ranked_data AS (
    SELECT 
        user_id,
        activity_date,
        ROW_NUMBER() OVER(PARTITION BY user_id ORDER BY activity_date) as rn
    FROM user_activities
)
SELECT user_id
FROM ranked_data
WHERE rn = 1;
```

### 5. Methodology & Logic Breakdowns
*   **Step 1: Filtering & Extraction:** Extracted the core subset of data using a CTE.
*   **Step 2: Windowing:** Implemented `ROW_NUMBER()` partitioned by the user ID to isolate chronological sequences.
*   **Step 3: Execution:** Maintained optimal performance by filtering on indexed tracking columns.