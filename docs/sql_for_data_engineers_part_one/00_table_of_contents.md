**Course Goal**: This curriculum is designed to take students from the conceptual foundations of Relational Database Management Systems (RDBMS) to advanced query optimization and database administration. By following the roadmap from basic syntax to complex window functions and performance tuning, learners will acquire the full spectrum of skills required to architect, manage, and analyze data efficiently.

## Course Layout and Expectations
### Module 1: The Foundation
(Covers: Learn the Basics, Basic SQL Syntax)

- **What to Expect**: This introductory module establishes the theoretical framework of databases. Students will explore the differences between SQL and NoSQL and learn the core benefits and limitations of RDBMS. The focus then shifts to the grammar of the language, covering essential keywords and data types.
- **Skills Gained:**
    - Conceptual understanding of Relational Databases.
    - Proficiency with SQL Keywords and Data Types.
    - Ability to use standard Operators.
- **Demonstratable Skills**: The learner can explain when to use a relational database versus a NoSQL solution and can write syntactically correct, basic SQL statements.

### Module 2: Defining and Manipulating Data
(Covers: DDL, DML, Data Constraints)

- **What to Expect**: Students will transition from theory to action by learning how to build the database structure and populate it. This includes Data Definition Language (DDL) for creating and modifying tables and Data Manipulation Language (DML) for managing the data within them.
- **Skills Gained**:
    - Schema creation using CREATE, ALTER, and DROP.
    - Data lifecycle management using INSERT, UPDATE, and DELETE.
    - Enforcing data quality via constraints like Primary Keys, Foreign Keys, and NOT NULL.
- **Demonstratable Skills**: The learner can design a table schema with appropriate constraints to ensure data integrity and perform full CRUD (Create, Read, Update, Delete) operations.

### Module 3: Querying and Functions
(Covers: Aggregate Queries, Joins, Subqueries, Advanced Functions)

- **What to Expect**: This is the core of data analysis. Students will learn to extract meaningful insights by grouping data, combining multiple tables, and applying complex logic. The module covers everything from basic aggregations to intricate JOIN operations and nested subqueries.
- **Skills Gained**:
    - Summarizing data with SUM, COUNT, AVG, and GROUP BY.
    - Retrieving data from multiple sources using INNER, LEFT, RIGHT, and FULL OUTER joins.
    - Writing Nested and Correlated Subqueries.
    - Data transformation using String, Numeric, and Date functions.
- **Demonstratable Skills**: The learner can generate complex reports, join distinct datasets to answer business questions, and clean/format raw data using scalar functions.

### Module 4: Database Management & Architecture
(Covers: Views, Indexes, Data Integrity & Security, Transactions)

- **What to Expect**: This module moves into database administration. Learners will explore how to simplify complex queries using Views , speed up retrieval with Indexes , and secure the database using permissions. It also covers the critical concept of Transactions and ACID properties.
- **Skills Gained**:
    - Creating and managing Views for query simplification.
    - Implementing Indexes to enhance performance.
    - Managing user access with GRANT and REVOKE.
    - Handling Transactions with COMMIT, ROLLBACK, and SAVEPOINT.
- **Demonstratable Skills**: The learner can secure a database against unauthorized access, ensure data consistency during failures using transactions, and optimize data retrieval paths.

### Module 5: Advanced Implementation & Optimization
(Covers: Stored Procedures, Advanced SQL, Performance Optimization)

- **What to Expect**: The final module focuses on expert-level techniques. Students will master procedural SQL, Window Functions for advanced analytics, and techniques to diagnose and fix slow queries.
- **Skills Gained**:
    - Developing Stored Procedures and Functions.
    - Advanced analytics using Window Functions (RANK, LEAD, LAG).
    - Utilizing Common Table Expressions (CTEs) and Recursive Queries.
    - Query Optimization Techniques such as execution plan analysis and reducing subqueries.
- **Demonstratable Skills**: The learner can write dynamic SQL scripts, perform complex analytical ranking and trending without external tools, and refactor slow-performing queries for maximum efficiency.

## Table of Contents
*Part I: The Foundation*

- **Chapter 1: Learn the Basics** 
    - 1.1 What are Relational Databases? 
    - 1.2 RDBMS Benefits and Limitations 
    - 1.3 SQL vs NoSQL Databases 
- **Chapter 2: Basic SQL Syntax**
    - 2.1 SQL Keywords
    - 2.2 Data Types
    - 2.3 Operators 

*Part II: Defining and Manipulating Data*

- **Chapter 3: Data Definition Language (DDL)** 
    - 3.1 Create Table 
    - 3.2 Alter Table 
    - 3.3 Truncate Table 
    - 3.4 Drop Table 
- **Chapter 4: Data Manipulation Language (DML)**
    - 4.1 Core Statements
        - INSERT
        - UPDATE
        - DELETE 
    - 4.2 The SELECT Statement 
        - FROM 
        - WHERE
        - JOINS
        - GROUP BY
        - ORDER BY
        - HAVING 
- **Chapter 5: Data Constraints**
    - 5.1 Primary Key
    - 5.2 Foreign Key 
    - 5.3 Unique 
    - 5.4 NOT NULL 
    - 5.5 CHECK 

*Part III: Querying and Functions*

- **Chapter 6: Aggregate Queries**
    - 6.1 Aggregate Functions:
        - SUM 
        - COUNT 
        - AVG 
        - MIN 
        - MAX 
    - 6.2 Grouping Results:
        - GROUP BY 
        - HAVING
- **Chapter 7: JOIN Queries**
    - 7.1 INNER JOIN 
    - 7.2 LEFT JOIN 
    - 7.3 RIGHT JOIN 
    - 7.4 FULL OUTER JOIN 
    - 7.5 Self Join 
    - 7.6 Cross Join 
- **Chapter 8: Subqueries**
    - 8.1 Different Types (Scalar, Column, Row, Table) 
    - 8.2 Nested Subqueries 
    - 8.3 Correlated Subqueries 
- **Chapter 9: Advanced Functions**
    - 9.1 String Functions
        - CONCAT
        - LENGTH 
        - SUBSTRING 
        - REPLACE 
        - UPPER 
        - LOWER 
    - 9.2 Numeric Functions 
        - FLOOR 
        - ABS 
        - MOD 
        - ROUND 
        - CEILING 
    - 9.3 Date and Time 
        - DATE 
        - TIME 
        - TIMESTAMP 
        - DATEPART 
        - DATEADD 
    - 9.4 Conditional Expressions 
        - CASE 
        - NULLIF 
        - COALESCE 

*Part IV: Database Management & Architecture*

- **Chapter 10: Views**
    - 10.1 Creating Views 
    - 10.2 Modifying Views 
    - 10.3 Dropping Views 
- **Chapter 11: Indexes**
    - 11.1 Managing Indexes 
    - 11.2 Query Optimization 
- **Chapter 12: Data Integrity & Security**
    - 12.1 Data Integrity Constraints 
    - 12.2 GRANT and Revoke 
    - 12.3 DB Security Best Practices 
- **Chapter 13: Transactions**
    - 13.1 ACID Properties 
    - 13.2 Transaction Isolation Levels 
    - 13.3 Transaction Commands:
        - BEGIN
        - COMMIT
        - ROLLBACK
        - SAVEPOINT 

*Part V: Advanced Implementation*

- **Chapter 14: Stored Procedures & Functions**
- **Chapter 15: Advanced SQL**
    - 15.1 Window Functions
        - row_number 
        - rank 
        - dense_rank 
        - lead 
        - log 
    - 15.2 Recursive Queries 
    - 15.3 Pivot / Unpivot Operations 
    - 15.4 Common Table Expressions 
    - 15.5 Dynamic SQL 
- **Chapter 16: Performance Optimization**
    - 16.1 Query Analysis Techniques 
    - 16.2 Query Optimization Techniques 
        - Using Indexes 
        - Optimizing Joins 
        - Reducing Subqueries 
        - Selective Projection