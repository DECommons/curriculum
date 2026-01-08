## Table of Contents

Part I: Retrieving and Filtering Data
- Chapter 1: The Foundation of Querying
    - 1.1 The SELECT Statement
    - 1.2 The FROM Clause
    - 1.3 Limiting Results (LIMIT / TOP / OFFSET) [New - Essential for exploring data]
    - 1.4 DISTINCT: Eliminating Duplicates [New - Essential]
    - 1.5 Comments in SQL [New - Best Practice]
- Chapter 2: Filtering and Sorting
    - 2.1 The WHERE Clause 
    - 2.2 SQL Operators
        - Comparison (=, <>, <, >)
        - Logical (AND, OR, NOT)
        - Range (BETWEEN)
        - Lists (IN)
        - Pattern Matching (LIKE, Wildcards)
    - 2.3 Handling NULL values (IS NULL, IS NOT NULL)
    - 2.4 The ORDER BY Clause

Part II: Transforming and Aggregating Data
- Chapter 3: Row-Level Functions (Scalar)
    - 3.1 Data Types Refresher (Brief)
    - 3.2 String Functions (CONCAT, SUBSTRING, REPLACE, UPPER, LOWER)
    - 3.3 Numeric Functions (ROUND, ABS, FLOOR, CEILING) 
    - 3.4 Date and Time Functions (DATEADD, DATEDIFF, DATEPART)
    - 3.5 Data Type Conversion (Casting)
        - CAST()
        - :: syntax
    - 3.6 Conditional Logic (CASE WHEN, COALESCE, NULLIF)
- Chapter 4: Aggregation and Grouping
    - 4.1 Aggregate Functions (COUNT, SUM, AVG, MIN, MAX)
    - 4.2 The GROUP BY Clause 
    - 4.3 Filtering Aggregates: The HAVING Clause 
    - 4.4 Order of Execution (SQL vs English) 
        - Explaining why you can't refer to an alias defined in SELECT inside the WHERE clause.

Part III: Combining Data Sets
- Chapter 5: Joining Tables
    - 5.1 Join Terminology & Aliasing 
    - 5.2 INNER JOIN 
    - 5.3 Outer Joins (LEFT, RIGHT, FULL)
    - 5.4 CROSS JOIN (Cartesian Products)
    - 5.5 Self Joins 
- Chapter 6: Set Operators
    - 6.1 UNION vs UNION ALL 
    - 6.2 INTERSECT and EXCEPT/MINUS 
  
Part IV: Advanced Query Techniques
- Chapter 7: Subqueries and CTEs
    - 7.1 Scalar and Multi-row Subqueries 
    - 7.2 Correlated Subqueries (EXISTS, NOT EXISTS)
    - 7.3 Common Table Expressions (CTEs)
        - Why CTEs are preferred over subqueries for readability.
    - 7.4 Recursive CTEs
- Chapter 8: Window Functions
    - 8.1 The OVER() clause and Partitioning 
    - 8.2 Ranking Functions (ROW_NUMBER, RANK, DENSE_RANK)
    - 8.3 Offset Functions (LEAD, LAG) 

Part V: Managing Data and Structures (DDL & DML)
- Chapter 9: Creating Database Objects
    - 9.1 CREATE TABLE and Data Types
    - 9.2 Data Constraints (PK, FK, UNIQUE, CHECK)
    - 9.3 ALTER and DROP statements
    - 9.4 Temporary Tables (Local vs Global)
    - 9.5 Views
- Chapter 10: Modifying Data
    - 10.1 INSERT 
    - 10.2 UPDATE 
    - 10.3 DELETE vs TRUNCATE 
    - 10.4 Managing Transactions (BEGIN, COMMIT, ROLLBACK)

Part VI: Programming and Optimization
- Chapter 11: Programmable Objects
    - 11.1 Variables and Logic (IF/ELSE)
    - 11.2 Stored Procedures
    - 11.3 User-Defined Functions 
    - 11.4 Dynamic SQL
- Chapter 12: Performance Basics
    - 12.1 Introduction to Indexes 
        - Concept of B-Trees and lookup speeds.
    - 12.2 SARGable Queries (Writing efficient WHERE clauses)
    - 12.3 Reading an Execution Plan (Basics) 