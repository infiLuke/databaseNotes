# Database Normalization
Tables are linked to each other by shared attributes.
These links are the relationships between tables.

## Normalization
- Eliminating redundent data to reduce storage requirements.
- Data Integrity
  - Eliminite update anomalies (data can be updated in one single place and is referenced elsewhere by ID)
  - Eliminate Inconsistencies (when the same data is stored in multiple places)
Faster indexing and sorting
Faster querying (query optimization in the database engine)

Breaking up repeating data into seperate tables and referencing the two tables with ID columns.


## Set Theory and Relational Databases
A Set is the data content of a table, or more generally
A Set is a collection of things
Sets are displayed with Venn Diagrams

**Resultset**
: the output set of a query (can be the whole set or a subset of the whole)


**Intersection** between two sets
: the elements both sets have in common

**Union** of two sets
: all elements of both sets combined

**Except** of two sets
: all elements of both sets except the *intersection*


**Dataset**
: A collection of rows with the same column definitions.

**Table**
: A table is a dataset that is stored physically on a disk.
