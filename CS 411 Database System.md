# CS 411 Database System

#### Two Perspectives of DBMS

USER Perspectives(how to use) & SYSTEMS Perspectives(how to implement)

##  Pre-lecture 8.24

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

Notice that the foreign key is allowed to be a part of the primary key, but can not be the primary key.

##### Specification of a Database Schema

<img src="CS%20411%20Database%20System.assets/image-20220823151944036.png" alt="image-20220823151944036" style="zoom:50%;" />

There will be allowed to have more than one key for a table.

The set of allowable values for a colunm is called the **domain** of the column.

In relatonal DBs, we use relation(attribute: domain)