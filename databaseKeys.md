# Database Keys

A database is relational when the tables are connected by common attributes.
These special attributes are called **Keys**.

## Constraints
A rule that the database has to enforce

## Unique Keys
Guarantees uniqueness for all values in the column.

Mulitple Unique Keys per table are possible.
Values in Unique columns can be changed.

### Primary Keys
- Guarantees uniqueness for all values in the column
- Never allows a *NULL* value
- Each table can only have one Primary Key
- Values can not be updated once created

Primary Keys are usually implemented as auto-incrementing number fields.
(1, 2, 3, 4, ..., n)
the use of numbers instead of text reduces disk storage requirements and speeds up the query process.

### Foreign Keys
**Referencial Integrity**
: Foreign Key Values must also exist as a Primary Key Value in the reference table.
: Foreign Key Values that don't exist in the reference table are not allowed.
Without Foreign Key constraints tables lack *referential integrity*
