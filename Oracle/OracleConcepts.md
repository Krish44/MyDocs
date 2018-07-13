## PL/SQL Identifiers

A name that is given for a PL/SQL object. The object could be constant, variable, exception, cursors, procedures, function, package, trigger, object type, reserve word or label.
## Version Information
 - SELECT * FROM v$version;      --  all version information from Oracle
 - SELECT * FROM v$version WHERE banner LIKE 'Oracle%';  -- Only version
## Oracle datatypes
## Oracle Joins - Types of Joins
1. Cross Join/Cartesian Product
2. Natural Join
3. Inner Join
4. Outer join  
 a.Left Outer Join  
 b.Right Join  
 c.Full Outer Join  
5. Anti Join
6. Semi Join
7. Self Join
8. Equi Join and Non Equi Join

**Equijoins:**
An equijoin is a join with a join condition containing an equality operator. 
An equijoin combines rows that have equivalent values for the specified columns. 

**Self Joins:** A self join is a join of a table to itself. 
This table appears twice in the FROM clause and is followed by table aliases that qualify column names in the join condition.

**Cross Join/Cartesian Product:**
If two tables in a join query have no join condition, then Oracle Database returns their Cartesian product. 
Result will have.............

Link: https://www.techdoubts.com/different-types-of-joins-in-oracle/
## Table - keys
- **Primary key**
- **Foreign key** is a way to enforce referential integrity within your Oracle database. A foreign key means that values in one table must also appear in another table.
- **Unique key** 
## Indexes
## Views
- Types of views  
 Simple view (Single table)  
 Complex view (Cobination of tables)  
## Materialised view 
 Materialized view is a database object that contains the results of a query. 
 For example, it may be a local copy of data located remotely, 
 or may be a subset of the rows and/or columns of a table or join result, or may be a summary using an aggregate function.
 **Materialised view**  
 **Refresh rate - difference**  
 **Execution of materialised view**  
## How to update a view
## Autosys (Tool)
## Bulk collect
## Collection  
A **Collection** is an ordered group of elements, all of the same type. Each element has a unique subscript, called an index, that determines its position in the collection
## Ref cursor
## cursor
When a query is executed in oracle, a result set is produced and stored in the memory. Oracle allows the programmer to access this result set in the memory through cursors. 
## Informatica - Cleanser tool
## Adobe Info Sphere
## Host Array
## Static Function
## Set length
## Cursor scenarios 
## Oracle hints
 - List of Hints  
 index, ordered, append, 
 - Disadvantage of hints
 [When Not To Use Hints](https://oracle.readthedocs.io/en/latest/sql/hints/when-not-to-use.html)
 - Example:  
 select /*+ index(customer cust_primary_key_idx) */ * from customer;
 - [Hints list](http://www.adp-gmbh.ch/ora/sql/hints/index.html)
## External Table
## Moving data into file
## sqlloader
## BLOB

blob (Binary Large Object) is an Oracle data type that can hold up to 4 GB of data. BLOB's are handy for storing digitized information 
 (e.g., images, 	audio, video).
 
## CLOB

CLOB data type stores variable-length character data (character large object) in the database character set that can be single-byte or multi-byte 
(supports more than 4 GB Can store a book, and search fro keywords)

## VPD -(Virtual Private data) Security
## Oracle In Built packages
## Analytical functions
## Pipelined function, Funcs and procedure
## Aggregate functions
## Temporary tables
- Types: Global Temporary Tables, Private Temporary Tables (since Oracle 18c)
- Clauses: ON COMMIT DELETE ROWS, ON COMMIT PRESERVE ROWS
## Types of Indexing
## synonyms 
You don't want the users to have to worry about knowing which schema owns the object.
## Grant
## Driving table
- We process the from clause from the RIGHT to the LEFT  
- Pick a driving table from the end of the FROM list  
- Example: select * from emp, dept where emp.deptno = dept.deptno;  
We would fetch rows from DEPT in a full scan and then find the rows in EMP that match. DEPT is the driving table.  

## Index on table
## DBMS system commands
dbms_random.value( 10, 100 )
dbms_stats.gather_table_stats

## Autonomous Transactions
 Autonomous transactions allow you to leave the context of the calling transaction, 
 perform an independent transaction, and return to the calling transaction without affecting it's state.
 - If commit in autotracns affects current block DML 
 - Example
## deadlock
## Triggers

- limit  
- EXE immediate for DDL (Autonomous transaction)
- Function  - DDL possible in similar ways
-- Max triggers on a table

## Mutating a  trigger
## columns 

- limit - 1000 In Newer version of Oracle

## CTE 

- Common set 

## Database links 
- connect externally (DB links)
## Oracle scheduler
DBMS_SCHEDULER.CREATE_JOB (   );  
DBMS_SCHEDULER.create_program ( );  

-- Display job details  
SELECT owner, job_name, enabled FROM dba_scheduler_jobs;
 
-- Display the program details.  
SELECT owner, program_name, enabled FROM dba_scheduler_programs;  
**Links:**  
https://oracle-base.com/articles/10g/scheduler-10g#jobs
## Performance tuning
## coalese - truncate - Concatenation
## Case vs. Decode

 * Everything DECODE can do, CASE can. There is a lot else CASE can do though, which DECODE cannot. 
 * DECODE performs an equality check only. CASE is capable of other logical comparisons such as < > etc.
 * Link: http://www.oratable.com/decode-case-differences/
 * decode can not be used outside a query
 * Case can be used

## Materialised view vs. view

- Difference betweeen MV and V:
- Materialized views are disk based and are updated periodically based upon the query definition.
- Views are virtual only and run the query definition each time they are accessed.
- View takes larger execution time, but mview takes smaller execution time than views (for the same select statement).
- Indexes can be created on mviews to gain more performance, but indexes cannot be created on views.
## Exception Handling
To handle certain kinds of errors meaningful to your PL/SQL program.
 - Other than 'when others' and 'no data found'
 - Ex: TOO_MANY_ROWS, INVALID_CURSOR, INVALID_NUMBER, ZERO_DIVIDE, CASE_NOT_FOUND
## Pragma - errors
 - Associating a PL/SQL Exception with a Number: Pragma EXCEPTION_INIT
 - To handle error conditions (typically ORA- messages) that have no predefined name, you must use the OTHERS handler or the pragma EXCEPTION_INIT. A pragma is a compiler directive that is processed at compile time, not at run time.
 - Syntax: PRAGMA EXCEPTION_INIT(exception_name, -Oracle_error_number);
https://docs.oracle.com/cd/B10501_01/appdev.920/a96624/07_errs.htm#917

## 12c vs 11g
## Is it possible to commit in a function
## How to call a function in a procedure
## How to handle large amount of data  
## Writing security scripts
## syntax of oracle object creation
