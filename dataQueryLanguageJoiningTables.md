# SQL: Joining Tables
is used to combine related data from mulitple tables into one result set.

## Different Kinds of Joins:
The way the query instructs the database to combine the two tables.
### Inner Join
    Inner Join          JOIN
### Outer Join
    Left Outer Join     LEFT JOIN
    Right Outer Join    RIGHT JOIN
    Full Outer Join     FULL JOIN

## Inner Joins
> Inner Joins only select the records from the *Intersection* (matching records) of the tables.
> Records that don't have related data in the other table(s) can not be selected.


Keywords `JOIN` and `INNER JOIN` are equivalent by default.
Join on foreign and primary keys to connect tables successfully.

    SELECT * FROM tableOne
        INNER JOIN tableTwo ON tableOne.PrimaryID = tableTwo.ForeignID;

### Aliasing Tables
    SELECT * FROM tableOne AS t1
        INNER JOIN tableTwo AS t2 ON t1.PrimaryID = t2.ForeignID;

    SELECT mk.MakeName, md.ModelName FROM make AS mk
        JOIN model AS md ON mk.MakeID = md.MakeID
        WHERE mk.MakeName = 'Chevy';

### Multiple Tables
    SELECT <columns> FROM <table 1>
        INNER JOIN <table 2> ON <table 1>.<column> = <table 2>.<column>
        INNER JOIN <table 3> ON <table 1>.<column> = <table 3>.<column>


## Outer Joins
> Outer Joins enable including records that don't have related records in other tables.


### Left Outer Join
> All records from the left table and the Intersection (matching records)

### Right Outer Join
> All records from the right table and the Intersection (matching records)

### Full Outer Join
> Match all records that exist and also return the remaining unmatched data from both tables.


