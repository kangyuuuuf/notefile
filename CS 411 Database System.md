# CS 411 Database System

#### Two Perspectives of DBMS

USER Perspectives(how to use) & SYSTEMS Perspectives(how to implement)

##  Pre-lecture 2

### Data Model

A data model is a notation for describing data or information. The description generally consists of three parts:

- Structure of the data: data structure
- Operations on the data: retrieve information
- Constraints on the data: ways to describe limitations on what the data can be.

#### The relational Data Model

##### Basic Concepts and Terminology

The ideal of relational:

- separate physical implementation for logical.
- describe the data and operations mathematically.

**Example:** Imagine that this table(or relation) has been defined to help keep track of bank accounts.

<img src="CS%20411%20Database%20System.assets/image-20220823150519526.png" alt="image-20220823150519526" style="zoom:50%;" />

<img src="CS%20411%20Database%20System.assets/image-20220823150709339.png" alt="image-20220823150709339" style="zoom:50%;" />

The “size” of table is depened on degree/arity which is the number of columns and cardinality which is the number of rows.

##### Key

Each table has a key where the values must be unique. A key may contain two conlumn.

**Foreign key**: when there is mutiple table, to make sure that the same column in different table can interact correctly, we can set the column of one table a foreign key of another. Then, when the access of invalid data will be reject.

Note **a foreign key** is a column element that is not a key of table(i.e. it can have duplicate), and the other table contains a key with exact domain, 

Notice that the foreign key is allowed to be a part of the primary key, but can not be the primary key.

##### Specification of a Database Schema

<img src="CS%20411%20Database%20System.assets/image-20220823151944036.png" alt="image-20220823151944036" style="zoom:50%;" />

There will be allowed to have more than one key for a table.

The set of allowable values for a colunm is called the **domain** of the column.

In relatonal DBs, we use relation(attribute: domain)

## Pre-Lecture 2

### SQL: Structured Query Language

It is the standard language for relational date, sepearated into

- DDL(data definition language)
- DML(data manipulation language)

DML based on **relational calculus**.

#### Single-Relation Query Form

The principal form of a single-relation query is:

- SELECT desired attributes
- FORM one table (relation)
- WHERE condition about tuples of the table

<img src="CS%20411%20Database%20System.assets/image-20220824110944056.png" alt="image-20220824110944056" style="zoom:50%;" />

##### Renaming Afttributes

We can use key work “AS<new name>” to rename an attribute

Example: SELECT Number AS Acc_Num, Owner

##### Expressions in SELECT Clauses

<img src="CS%20411%20Database%20System.assets/image-20220824111357859.png" alt="image-20220824111357859" style="zoom:50%;" />

##### Creating temporary tables using INTO

We can select the element we want and inest it into temporary tables using into:

SELECT Number INTO temp3

##### Complex Conditions in WHERE Clause

We can write some compound conditions in WHERE to filt the element we want.

WHERE cafe = ‘Caffe bene’ AND drink = ‘Mocha’

We cap apply various syntax in WHERE

<img src="CS%20411%20Database%20System.assets/image-20220824112054382.png" alt="image-20220824112054382" style="zoom:50%;" />

WHERE caluses can have conditions in which a string is compared with a pattern to see if it matches.

General form: <Attribute>LIKE<pattern> or <Attribute>NOT LIKE<pattern>

Pattern is quoted string with

- % to “any string”
- _ to “any character”

WHERE phone LIKE ‘%555-___’

##### Ordering the results

- Ordering is ascending, unless you specify the **DESC** keyword
- Ties are borken by the second attribute on the ORDER BY list, etc.

<img src="CS%20411%20Database%20System.assets/image-20220824112633364.png" alt="image-20220824112633364" style="zoom:33%;" />

### SQL: Multi-Relation Queries(Joins) 

Interesting queries often combine data from more than one relation. We can address several relations in one query by listing them all in the FROM clause. Distinguish attributes of the same name by “<relation>.<attribu>”

<img src="CS%20411%20Database%20System.assets/image-20220824160944232.png" alt="image-20220824160944232" style="zoom:50%;" />

#### Join, Natural Join & Outer Join

<img src="CS%20411%20Database%20System.assets/image-20220824161546102.png" alt="image-20220824161546102" style="zoom:50%;" />

The Join will pair the two table with the same value. Note that when the value cannot be found in the second table, the select will leave the info of the row.

<img src="CS%20411%20Database%20System.assets/image-20220824161945192.png" alt="image-20220824161945192" style="zoom:50%;" />

Natural Join will join the same value with the same column, and combine into one colunm

<img src="CS%20411%20Database%20System.assets/image-20220824161959884.png" alt="image-20220824161959884" style="zoom:50%;" />

##### Outer Joins

Left outer join: Include the left tuple even if there’s no match

Right outer join: Include the right tuple even if there’s no match

Fall outer join: Include both the left and right tuples even if there;s no match

#### Null Values

The logic of conditions in SQL is really 3-valued logic: TRUE, FALSE, UNKNOWN.

 To understand how AND, OR, and NOT work in 3-valued logic, think of TRUE - 1, FALSE = o, and UNKNOWN = 1/2.

AND = MIN; OR = MAX, NOT(x) = 1-x;

### Subqueries

A parenthesized SELECT-FROM_WHERE statement(subquery) can be used as a value in a number of places, including FROM and WHERE clauses.

If a subquery is guaranteed to produce one tuple with one component, then the subquery can be used as a value.

#### Boolean Operators: The IN Operator

<tuple>IN<relation> is true if and only if the tuple is a member of the relation.

<tuple>Not IN<relation> means the opposite.

IN-expressions can appear in WHERE clauses.

The <relation> is often a subquery.

#### Boolean Operators: The Exists Operator

EXISTS(<relation>) is true if and only if the <relation> is not empty.

#### Boolean Operators: The Operator ANY

x = ANY(<relation>) is a Boolean condition meaning that x equals at least one tule in the relation.

Similarly,  = can be replaced by any of the comparison operators. 

#### Boolean Operators: The Operator ALL

Similarly, x <> ALL(<relation>) is true if and only if for every tuple t in the relation, x is not equal to t.

<> can be replaced by any of the comparison operators. 

#### Union, Intersection, and Difference

(Subquery) UNION (Subquery)

(Subquery) INTERSECT (Subquery)

(Subquery) EXCEPT (Subquery)

**UNION ALL operator displays duplicate values.**

### Advanced SQL: Grouping & Aggregation

#### Aggregations

SUM, AVG, COUNT, MIN, and MAX can be applied to a column in a SELECT clause to producethat aggregation on the column.

Also, COUNT(*) counts the number of tuples.

It should be careful when we use distinct in an aggregation.

##### NULL’s Ignored in Aggregation

NULL never contributes to a sum, average, or count, and can never be the minimum or maximum of a column. But if all the values in  a column are null, then the result of the aggregation is NULL.

#### Grouping

 We may follow a SELECT-FROM-WHERE expression by GROUP BY and a list of attributes.

#### Restriction

If any aggregation is used, then each element of the SELECT list must be either: Aggregated, or an attribute on the GROUP BY list. And we can use the attribute of Primary key to GROUP BY 

#### Having Clauses

HAVING<condition> may follow a GROUP BY clause.

There conditions may refer to any relation or tuple-variable in the FROM clause. They may refer to attributes of those relations, as long as the attribute makes sense within a group; i.e., it is either: a grouping attributes aggregated.

#### Views

VIEW define a queryL CREATE VIEW <name> AS <query>

Why useful?

- Can be used as relations in other queries 
- Can facilitate security/access control
- Describe transformations or mappings from one schema (the base relations) to antoher (the output of the view)

#### Materialized Views

A materialized view is one that is computed once and its results are stored as a table.

### Advanced SQL: Database Updates

#### Insertion

INSERT INTO <relation> VALUES (<list of values>);

We can list the order of attributes of relations.

INSERT INTO <relation>(<attributes>) VALUES (<list of values>);

If there is the value we do not have or do not want to insert, just omit the value of column. 

We can also insert the entire result of a query into a relation

INSERT INTO <relation> (<subquery>).

#### Deletion

DELETE FROM <relation> WHERE <condition>.

#### Update

To change certain attributes in certain tuples of a relation:

UPDATE <relation> SET <list of attribute assignments> WHERE <condition on tuples>; 

#### Store Procedures

A Stored Procedure is a set of SQL statements with an assigned name stored in the DBMS and can be called by multiple programs. Stored Procedure Syntax:

```sql
CREATE PRCEDURE sp_nam

	(proc_parameter, …)

BEGIN 

	– execution code

END;
```

proc_parameter: [ IN | OUT | INOUT ] praam_name param_type

- IN parameters for passing values into the procedure,
- OUT parameter for passing value back from procedure to the calling program
- INOUT: is a combination of IN and OUT parameters.

Calling the procedure: CALL procedure;

In stored procedure, we can:

- declare variables
- use conditional IF-THEN-ELSE or loops such as WHILE and REPEAT statements
- use cursors: A cursor is used to iterate through a set of rows returned by a query so that we can process each individual row.



