
A Collection is an ordered group of elements, all of the same type.  
Each element has a unique subscript, called an index, that determines its position in the collection.  
###Tyes of Collection###
- Index-By Tables
- Nested Table
- Varrays
  
**Index-By Tables (Associative Arrays)**  
The collection is indexed using BINARY_INTEGER values  
  
TYPE table_type IS TABLE OF NUMBER(10)  
    INDEX BY BINARY_INTEGER;  
  
**Nested Table**  
Nested table collections are an extension of the index-by tables.  
The main difference between the two is that nested tables can be *stored in a database column* but index-by tables cannot.  
In addition some DML operations are possible on nested tables when they are stored in the database. Once created elements can be deleted using the DELETE method to make the collection sparse  
  
TYPE table_type IS TABLE OF NUMBER(10);


•Varrays

A VARRAY is similar to a nested table except you must specifiy an upper bound in the declaration. Like nested tables they can be stored in the database, but unlike nested tables individual elements cannot be deleted so they remain dense.

TYPE table_type IS VARRAY(5) OF NUMBER(10);


DECLARE
   TYPE nested_type IS TABLE OF VARCHAR2(30);
   TYPE varray_type IS VARRAY(5) OF INTEGER;
   TYPE assoc_array_num_type IS TABLE OF NUMBER INDEX BY PLS_INTEGER;
   TYPE assoc_array_str_type IS TABLE OF VARCHAR2(32) INDEX BY PLS_INTEGER;
   TYPE assoc_array_str_type2 IS TABLE OF VARCHAR2(32) INDEX BY VARCHAR2(64);
   v1 nested_type;
   v2 varray_type;
   v3 assoc_array_num_type;
   v4 assoc_array_str_type;
   v5 assoc_array_str_type2;
BEGIN
-- an arbitrary number of strings can be inserted v1
   v1 := nested_type('Shipping','Sales','Finance','Payroll'); 
   v2 := varray_type(1, 2, 3, 4, 5); -- Up to 5 integers
   v3(99) := 10; -- Just start assigning to elements
   v3(7) := 100; -- Subscripts can be any integer values
   v4(42) := 'Smith'; -- Just start assigning to elements 
   v4(54) := 'Jones'; -- Subscripts can be any integer values
   v5('Canada') := 'North America'; -- Just start assigning to elements
   v5('Greece') := 'Europe';        -- Subscripts can be string values
END;

Index-By Tables (Associative Arrays)
The first type of collection is known as index-by tables. These behave in the same way as arrays except that have no upper bounds, allowing them to constantly extend. As the name implies, the collection is indexed using BINARY_INTEGER values, which do not need to be consecutive. The collection is extended by assigning values to an element using an index value that does not currently exist.

Nested Table Collections
Nested table collections are an extension of the index-by tables. The main difference between the two is that nested tables can be stored in a database column but index-by tables cannot. In addition some DML operations are possible on nested tables when they are stored in the database. During creation the collection must be dense, having consecutive subscripts for the elements. Once created elements can be deleted using the DELETE method to make the collection sparse. The NEXT method overcomes the problems of traversing sparse collections.

Varray Collections
A VARRAY is similar to a nested table except you must specifiy an upper bound in the declaration. Like nested tables they can be stored in the database, but unlike nested tables individual elements cannot be deleted so they remain dense.