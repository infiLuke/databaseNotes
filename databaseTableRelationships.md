# Database Table Relationships
How many rows can be related to each other on either side of the relationship.

## One-To-Many (most common)
One Row, in one table, can be related to many rows, in another table.
Example: Primary Key (one) - Foreign Key (many)
A parent-record can reference several child-records in another table.

## Many-To-Many
Tables that have a Many-To-Many relationship can not be connected with Foreign Keys.
Instead a third table, Junction-Table (Associative Entity), is created.
This table has two columns each referencing the primary keys of one table.

A many-to-many relationship has to be broken up into two one-to-many relationships,
and a third 'Junction-Table' in order to function in a relational database.

### Orders and Parts Example
one order can consist of many parts
one part can be used in many orders
to solve this issue a third table junction-table is created with the primary keys of orders and parts.
the new table has a multi-column primary key (order-id and part-id form a unique identifier).
No new column or foreign keys are added to the orders or parts table!


## One-To-One
one-to-one relationships can be combined into one table.

Exceptions:
- Performance Reasons: seperating the frequently and infrequently used columns can boost performance,
by reducing the overhead when accessing the most frequently used columns.
- extending a copyrighted table or database


Notation Styles

Crow's Foot Notation
Chen Notation
