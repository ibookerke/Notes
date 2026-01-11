# Most common topics

## [[ACID]]
in simple words it is a set of principles ensuring that transactions are processed reliably and maintain the integrity of the database.
Also, you should know [[Isolation levels]]
For instance, DBMS default choices:
PostgreSql - Read Commited
MySql - Repeatable read

## Views and Materialized Views
- [[SQL View]]s - precompiled/preprocessed select queries
- [[Materialized view]]s - prestored results of select queries


## Index Types
We'll not cover such index types like single-column / composite, or unique and primary indexes which are obvious. The only thing that should be remembered is the fact that the composite indexes are working till first inequality.
Here are some common types of indexes you need to consider:
- [[Clustered index]]
- [[Full-text index]]
- [[Spatial Index]]
- [[BitMap Index]]


## Procedures vs Functions

|**Feature**|**Stored Procedure**|**Function**|
|---|---|---|
|**Return Value**|Does not have to return a value. Can use output parameters to send data back.|Must return a value (scalar, table, or composite).|
|**Use in SQL Statements**|Cannot be used directly in `SELECT` or `WHERE` clauses.|Can be used directly in SQL statements.|
|**Transaction Control**|Can include `COMMIT` or `ROLLBACK`.|Cannot manage transactions.|
|**Purpose**|Designed for performing complex tasks like data manipulation, control flow, or executing multiple operations.|Primarily for computations and returning results.|
|**Side Effects**|Can perform side effects like modifying data.|Generally does not modify database state.|
|**Parameter Types**|Supports input, output, and in-out parameters.|Typically supports only input parameters.|
|**Execution**|Executed using a command like `CALL` or `EXEC`.|Invoked as part of a query or function call.|


## OLAP/OLTP
- [[OLAP]] 
- [[OLTP]]

