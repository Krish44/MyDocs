###### PL/SQL Identifiers
A name that is given for a PL/SQL object. The object could be constant, variable, exception, cursors, procedures, function, package, trigger, object type, reserve word or label.
###### Oracle datatypes
###### Oracle Joins - Types of Joins
**Equijoins:**
An equijoin is a join with a join condition containing an equality operator. 
An equijoin combines rows that have equivalent values for the specified columns. 

**Self Joins:** A self join is a join of a table to itself. 
This table appears twice in the FROM clause and is followed by table aliases that qualify column names in the join condition.

**Cross Join/Cartesian Product:**
If two tables in a join query have no join condition, then Oracle Database returns their Cartesian product. 
Result will have
###### Views
###### Materialised view 
 Materialized view is a database object that contains the results of a query. 
 For example, it may be a local copy of data located remotely, 
 or may be a subset of the rows and/or columns of a table or join result, or may be a summary using an aggregate function.
 **Materialised view - refresh rate - difference**
 **Execution of materialised view**

###### Autosys (Tool)
###### Bulk collect
###### Types of collection
###### Ref cursor
###### Informatica - Cleanser tool
###### Adobe Info Sphere
###### Host Array
###### Static Function
###### Set length
###### Cursor scenarios 
###### Oracle hints
 - List of Hints  
 - Disadvantage of hints
###### External Table
###### - Moving data into file
###### sqlloader
###### BLOB
blob (Binary Large Object) is an Oracle data type that can hold up to 4 GB of data. BLOB's are handy for storing digitized information 
 (e.g., images, 	audio, video).
###### CLOB
CLOB data type stores variable-length character data (character large object) in the database character set that can be single-byte or multi-byte 
(supports more than 4 GB Can store a book, and search fro keywords)
###### VPD -(Virtual Private data) Security
###### Oracle In Built packages
###### Analytical functions
###### Pipelined function, Funcs and procedure
###### Aggregate functions
###### Temporary tables
###### Types of Indexing
###### synonyms 
You don't want the users to have to worry about knowing which schema owns the object.
###### Grant
###### Driving table
###### Index on table
###### DBMS system commands
dbms_stats.gather_table_stats
###### Autonomous Transactions
 Autonomous transactions allow you to leave the context of the calling transaction, 
 perform an independent transaction, and return to the calling transaction without affecting it's state.
 - If commit in autotracns affects current block DML 
###### deadlock
###### Triggers
- limit  
- EXE immediate for DDL (Autonomous transaction)
- Function  - DDL possible in similar ways
-- Max triggers on a table
###### Mutating a  trigger
###### columns 
- limit - 1000 In Newer version of Oracle
###### CTE 
- Common set 
###### Database links - connect externally (DB links)
###### Oracle scheduler
###### Performance tuning
###### coalese - truncate - Concatenation
###### Case vs. Decode
 * Everything DECODE can do, CASE can. There is a lot else CASE can do though, which DECODE cannot. 
 * DECODE performs an equality check only. CASE is capable of other logical comparisons such as < > etc.
 * Link: http://www.oratable.com/decode-case-differences/
 * decode can not be used outside a query
 * Case can be used
###### Materialised view vs. view
- Difference betweeen MV and V:
- Materialized views are disk based and are updated periodically based upon the query definition.
- Views are virtual only and run the query definition each time they are accessed.
- View takes larger execution time, but mview takes smaller execution time than views (for the same select statement).
- Indexes can be created on mviews to gain more performance, but indexes cannot be created on views.
###### Pragma - errors
###### Types of exception
 Other than 'when others' and 'no data found'
###### 12c vs 11g
###### Is it possible to commit in a function
###### How to call a function in a procedure
###### How to handle large amount of data  
###### How to update a view


###### Writing security scripts
###### syntax of oracle object creation
