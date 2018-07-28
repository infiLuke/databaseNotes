# Entity Relationship Diagrams

## Elements

### Entity
Object, Person, Place or thing to be tracked in the database (rows)

### Attributes
Properties of the Entity (columns)

### Primary Key
A primary key is an attribute (or field) that uniquely identifies every record in a certain table.
1. unique
2. never changing
3. not null

### Foreign Key
is a reference attribute to a primary key attribute in another table.
foreign keys don't have to be unique. They can be repeated in a table.
There can be multiple foreign keys in one entity

### Composite Primary Key
Alternative to creating a new id primary key attribute
If one attribute can not uniquely identify an entity, a composite primary key can be used.
Two attributes are merged and together provide a unique primary key for each entity.

1. use the fewest number of attributes as possible
2. don't use attributes that are apt to change

### Bridge Table
In a `many` to `many` relationship a bridgetable is put between the two entities, to
break up the `many to many` relationship into a clearer form.

## ER Diagram Display Elements
- **entityName** is displayed at the top
Attributes are then listed in rows with three columns:
- first column: **KEY**
- second column: **attributeName**
- third column: **dataType**

## Relationships
Relationships between entities are displayed with lines.

**Cardinality** is displayed at each line end:
        1       simple association                  one; one (and only one)
        c       conditional association             zero or one
        m       multiple association                one or many; many
        mc      multiple-conditional association    zero or many

Cardinality is determined by clarifying the minimum and maximum amounts of each entity in one relationship.
        one customer    : zero or many orders
        1   customer    : mc    order

two cardinalities make up one relationship: `1 : mc` *customer to order*

## ERD Creation Steps
1. set up basic entities
2. define relationship between entities
3. adjust relationship markers between entities, so that they point to the connected foreign and primary keys
