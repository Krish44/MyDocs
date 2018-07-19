## PL/SQL Identifiers

A name that is given for a PL/SQL object. The object could be constant, variable, exception, cursors, procedures, function, package, trigger, object type, reserve word or label.
## Version Information
 - SELECT * FROM v$version;      --  all version information from Oracle
 - SELECT * FROM v$version WHERE banner LIKE 'Oracle%';  -- Only version
## Datatypes
## Joins - Types of Joins
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
## Inline View
An inline view is a SELECT statement in the FROM-clause of another SELECT statement. In-line views are commonly used to simplify complex queries by removing join operations and condensing several separate queries into a single query. 
```
SELECT a.last_name, a.salary, a.department_id, b.maxsal
  FROM employees a,
       ( SELECT department_id, max(salary) maxsal
         FROM employees
         GROUP BY department_id ) b
 WHERE a.department_id = b.department_id
   AND a.salary = b.maxsal;
```  
The above query display the employees who earn the highest salary in each department.  
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

## Materialised view vs. view
**Difference betweeen MV and V:**
 - Materialized views are disk based and are updated periodically based upon the query definition.
 - Views are virtual only and run the query definition each time they are accessed.
 - View takes larger execution time, but mview takes smaller execution time than views (for the same select statement).
 - Indexes can be created on mviews to gain more performance, but indexes cannot be created on views.  

*EXEC DBMS_MVIEW.refresh('EMP_MV');* -- Manually refreshed using the DBMS_MVIEW package
[Materialised view](https://oracle-base.com/articles/misc/materialized-views#basic-syntax)
## How to update a view
[Instead of trigger usage](https://www.mkyong.com/oracle/oracle-plsql-instead-of-trigger-example/)
## Autosys (Tool)
## Bulk collect
- Forall condition  
- Handling huge data 
- Exceptions in bulk collect
## Collection  
A **Collection** is an ordered group of elements, all of the same type. Each element has a unique subscript, called an index, that determines its position in the collection  
[O-Base Link](https://oracle-base.com/articles/8i/collections-8i)
## Ref cursor
## cursor
When a query is executed in oracle, a result set is produced and stored in the memory. Oracle allows the programmer to access this result set in the memory through cursors. 
## Informatica - Cleanser tool
## Adobe Info Sphere
## Cursor scenarios 
## External Table
- Allows Oracle to query data that is stored outside the database in flat files.  
- CREATE TABLE..ORGANIZATION EXTERNAL syntax.  
[External table](https://oracle-base.com/articles/9i/external-tables-9i)
## Moving data into file
## sqlloader
5 Types of files associated with SQLLOADER
## BLOB
blob (Binary Large Object) is an Oracle data type that can hold up to 4 GB of data. BLOB's are handy for storing digitized information 
 (e.g., images, 	audio, video).
## CLOB
CLOB data type stores variable-length character data (character large object) in the database character set that can be single-byte or multi-byte 
(supports more than 4 GB Can store a book, and search fro keywords)
## VPD -(Virtual Private data) Security
## Oracle In Built packages
## Analytical functions
## Aggregate functions
## Pipelined function, Funcs and procedure
## Temporary tables
- Types: Global Temporary Tables, Private Temporary Tables (since Oracle 18c)
- Clauses: ON COMMIT DELETE ROWS, ON COMMIT PRESERVE ROWS
## Types of Indexing
## synonyms 
You don't want the users to have to worry about knowing which schema owns the object.
## Grant
## Index on table
## DBMS system commands
dbms_random.value( 10, 100 )
dbms_stats.gather_table_stats
## Autonomous Transactions
 Autonomous transactions allow you to leave the context of the calling transaction, 
 perform an independent transaction, and return to the calling transaction without affecting it's state.
 - If commit in autotracns affects current block DML 
 - Example  
[Autonomous Transaction](https://oracle-base.com/articles/misc/autonomous-transactions)
## deadlock
## Triggers
- EXE immediate for DDL (Autonomous transaction)
- Function - DDL possible in similar ways
- **Max triggers on a table** (12)  
   Insert/Update/Delete :- 3 
   Before/After:- 2 
   Row Level/Statement Level:-2 
   Hence 3*2*2 
 - There is no limit. Also, from 11g on wards, compound triggers are supported  
### Types of triggers  
- Row level 
- Statement level
## Mutating a  trigger
## columns 
- limit - 1000 In Newer version of Oracle
## WITH CTE 
A Common Table Expression (CTE) is the result set of a query which exists temporarily and for use only within the context of a larger query.
- Needing to reference a derived table multiple times in a single query
- An alternative to creating a view in the database
- Performing the same calculation multiple times over across multiple query components
Example:  
```
-- define CTE:
WITH Cost_by_Month AS
(SELECT campaign_id AS campaign,
       TO_CHAR(created_date, 'YYYY-MM') AS month,
       SUM(cost) AS monthly_cost
FROM marketing
WHERE created_date BETWEEN NOW() - INTERVAL '3 MONTH' AND NOW()
GROUP BY 1, 2
ORDER BY 1, 2)

-- use CTE in subsequent query:
SELECT campaign, avg(monthly_cost) as "Avg Monthly Cost"
FROM Cost_by_Month
GROUP BY campaign
ORDER BY campaign
```
### With clause
## Database links 
- connect externally (DB links)
## Oracle scheduler
DBMS_SCHEDULER.CREATE_JOB( );  
DBMS_SCHEDULER.create_program( );  

-- Display job details  
SELECT owner, job_name, enabled FROM dba_scheduler_jobs;  
 
-- Display the program details.  
SELECT owner, program_name, enabled FROM dba_scheduler_programs;  
**Links:**  
https://oracle-base.com/articles/10g/scheduler-10g#jobs
## Performance Tuning
**Driving table** 
- We process the from clause from the RIGHT to the LEFT  
- Pick a driving table from the end of the FROM list  
- Example: select * from emp, dept where emp.deptno = dept.deptno;  
We would fetch rows from DEPT in a full scan and then find the rows in EMP that match. DEPT is the driving table.  
### Oracle hints
 - List of Hints  
 index, ordered, append, 
 - Disadvantage of hints
 [When Not To Use Hints](https://oracle.readthedocs.io/en/latest/sql/hints/when-not-to-use.html)
 - Example:  
 select /*+ index(customer cust_primary_key_idx) */ * from customer;
 - [Hints list](http://www.adp-gmbh.ch/ora/sql/hints/index.html)
### Probable reasons for not using index hints in a query
### Sort joins
### Hash joins
## coalese - truncate - Concatenation
## Case vs. Decode

 * Everything DECODE can do, CASE can. There is a lot else CASE can do though, which DECODE cannot. 
 * DECODE performs an equality check only. CASE is capable of other logical comparisons such as < > etc.
 * Link: http://www.oratable.com/decode-case-differences/
 * decode can not be used outside a query
 * Case can be used
## Rank vs Dense Rank
## Joins vs Merge
## Truncate vs delete
 - Triggers on truncate?
## In vs EXISTS
- More efficient one?
'IN' can be used on sub-queries as well as with values.  
Eg:   

**With values:**  
SELECT *
FROM test_emp  
WHERE deptno in ( 10,20,30);  

**With sub-query:**
SELECT *
FROM test_emp  
WHERE deptno in ( select deptno 
from test_emp   
where deptno=10 or deptno=20 or deptno=30);

**Whereas 'EXISTS' can only be used on sub-queries.**
SELECT *
FROM test_emp
WHERE exists ( select deptno
from test_emp 
where deptno=10 or deptno=20 or deptno=30);  
  
Exists is used to check whether the sub-query returns any rows 
whereas IN is used as multiple OR operator

## SQL\*Loader vs External Table
## Exception Handling
To handle certain kinds of errors meaningful to your PL/SQL program.
 - Other than 'when others' and 'no data found'
 - Ex: TOO_MANY_ROWS, INVALID_CURSOR, INVALID_NUMBER, ZERO_DIVIDE, CASE_NOT_FOUND
### Pragma - errors
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

