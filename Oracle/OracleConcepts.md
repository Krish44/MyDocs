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
- **Primary key** Primary key is clustered index, and the data in database table is physically organized in the sequence of clustered index  
- **Foreign key** is a way to enforce referential integrity within your Oracle database. A foreign key means that values in one table must also appear in another table.
- **Unique key** 
https://www.c-sharpcorner.com/blogs/difference-between-primary-key-unique-key-and-foreign-key1
## Indexes
- Optional structures associated with tables and clusters that allow SQL statements to execute more quickly against a table   
- Oracle Database index provides a faster access path to table data  
- More efficient to create an index for a table after inserting or loading the data
- To improve performance on joins of multiple tables, index columns used for joins
- Primary and unique keys automatically have indexes, but you might want to create an index on a foreign key
- When rows are inserted or deleted, all indexes on the table must be updated as well
- When a column is updated, all indexes that contain the column must be updated. 
   
Link: https://docs.oracle.com/cd/B19306_01/server.102/b14231/indexes.htm#i1007292

## Clusters
An optional method of storing table data. 
A cluster is made up of a group of tables that share the same data blocks. 
The tables are grouped together because they share common columns and are often used together.  
**Benefits:**
- Disk I/O is reduced and access time improves for joins of clustered tables.
- The cluster key is the column, or group of columns, that the clustered tables have in common. 
   
Should not use clusters for tables that are frequently accessed individually.  
(DML) statements cannot be issued against cluster tables in an indexed cluster until you create a cluster index with a CREATE INDEX statement.   

Link: https://docs.oracle.com/cd/B28359_01/server.111/b28310/clustrs001.htm#ADMIN11739   
Clustered Index: https://asktom.oracle.com/pls/asktom/f?p=100:11:0::::P11_QUESTION_ID:586423377841  
Also see: **Oracle Real Application Clusters applications**
## Listagg
Listagg is typically used to denormalize rows into a string of comma-separated values (CSV) or other comparable formats suitable for human reading.   
   
The minimal syntax is:  
```
LISTAGG(<expression>, <separator>) WITHIN GROUP(ORDER BY …)
```
Example:  
```
SELECT g
     , LISTAGG(value, ',') WITHIN GROUP (ORDER BY o) list
  FROM (SELECT g, min(o) o, value
          FROM dist_listagg
         GROUP BY g, value
       ) dt
 GROUP BY g
```  
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


## SQLPlus
- To pass variable from shell script to sqlplus:    
```
sqlplus -S user/pass@localhost << EOF
@/opt/D2RQ/file.sql total_count BUILDING
exit;
EOF
```
[Accepting parameters](https://stackoverflow.com/questions/17575321/how-to-pass-variable-from-shell-script-to-sqlplus/#answer-17575609)
  
## Moving data into file
## sqlloader
5 Types of files associated with SQLLOADER

## External Table
- Allows Oracle to query data that is stored outside the database in flat files.  
- CREATE TABLE..ORGANIZATION EXTERNAL syntax.  
[External table](https://oracle-base.com/articles/9i/external-tables-9i)  

## SQL\*Loader vs External Table

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
 - Autonomous transactions allow you to leave the context of the calling transaction, 
 perform an independent transaction, and return to the calling transaction without affecting it's state.
 - The autonomous transaction has no link to the calling transaction, so only commited data can be shared by both transactions.
 - If commit in autotracns affects current block DML - No
- Commonly used by error logging routines, where the error messages must be preserved, regardless of the the commit/rollback status of the transaction  
  
[Autonomous Transaction](https://oracle-base.com/articles/misc/autonomous-transactions)
## deadlock
## Triggers
- EXE immediate for DDL (Autonomous transaction)
- Function - DDL possible in similar ways
- **Max triggers on a table** (12)  
   Insert/Update/Delete :- 3  
   Before/After:- 2  
   Row Level/Statement Level:-2  
   Hence 3x2x2  
 - There is no limit. Also, from 11g on wards, compound triggers are supported  [Compound Triggers](https://asktom.oracle.com/pls/apex/f?p=100:11:0::::P11_QUESTION_ID:9526879900346669506)
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
**Triggers on truncate?**
- Not possible
- Triggers fire when DML commands are executed.
- TRUNCATE is a DDL command  
  Ex: TRUNCATE TABLE simple_tab;   
**Comparision**  
 - Truncate will be faster as there is no condition to check
 - Delete it will go through the all records to find which ones fit the condition
 - Cannot roll back a TRUNCATE TABLE statement
 - DELETE requires a COMMIT, but TRUNCATE does not
[DDL, DML, DCL and TCL](http://www.orafaq.com/wiki/SQL_FAQ#What_are_the_difference_between_DDL.2C_DML_and_DCL_commands.3F)
## In vs EXISTS
Example:    
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
  
**Comparision**   
 - 'IN' can be used on sub-queries as well as with values.  
 - Exists is used to check whether the sub-query returns any rows whereas IN is used as multiple OR operator
 - Exists checks boolean where as in checks multiple strings (find any matches of values in column)
 - IN should be used when the sub query will return small result set (sub query should not return null values)

## Exception Handling
To handle certain kinds of errors meaningful to your PL/SQL program.
 -  The functions SQLCODE and SQLERRM are especially useful in the OTHERS handler because they return the Oracle error code and message text. 
 - Alternatively, you can use the pragma EXCEPTION_INIT to associate exception names with Oracle error codes.
 - Other than 'when others' and 'no_data_found'  
Ex: TOO_MANY_ROWS, INVALID_CURSOR, INVALID_NUMBER, ZERO_DIVIDE, CASE_NOT_FOUND, LOGIN_DENIED   
### Pragma - errors
 - Associating a PL/SQL Exception with a Number: Pragma EXCEPTION_INIT
 - To handle error conditions (typically ORA- messages) that have no predefined name, you must use the OTHERS handler or the pragma EXCEPTION_INIT. 
 - A pragma is a compiler directive that is processed at compile time, not at run time.
 - The pragma EXCEPTION_INIT tells the compiler to associate an exception name with an Oracle error number
 - Syntax: PRAGMA EXCEPTION_INIT(exception_name, -Oracle_error_number);  
 Ex: 
 ```
 DECLARE
   deadlock_detected EXCEPTION;
   PRAGMA EXCEPTION_INIT(deadlock_detected, -60);
BEGIN
   ... -- Some operation that causes an ORA-00060 error
EXCEPTION
   WHEN deadlock_detected THEN
      -- handle the error
END;
 ``` 
The procedure RAISE_APPLICATION_ERROR lets you issue user-defined ORA- error messages from stored subprograms. That way, you can report errors to your application and avoid returning unhandled exceptions.  
Syntax: 
```
raise_application_error(error_number, message[, {TRUE | FALSE}]);  
where error_number is a negative integer in the range -20000 .. -20999 and message is a character string up to 2048 bytes long. 
```
 
https://docs.oracle.com/cd/B10501_01/appdev.920/a96624/07_errs.htm#917

## 12c vs 11g
## Is it possible to commit in a function
- Yes, you can do that if you make the function an autonomous transaction. That way it will not be part of the current transaction anymore.
## How to call a function in a procedure
## How to handle large amount of data  
## Writing security scripts
## syntax of oracle object creation

