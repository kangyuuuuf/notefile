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



