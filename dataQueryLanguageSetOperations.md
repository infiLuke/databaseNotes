# SQL Set Operations
Set Operations combine two or more datasets into one.
All columns have to be compatible.
Whole rows are evaluated against each other.


## UNION
Combine the the result-set of two or more SELECT statements into one result-set
No duplicate rows will be returned.

    SELECT ...
        UNION
    SELECT ... ;

## UNION ALL
Same as 'UNION' but return all rows, even if there are duplicates.

```sql
    SELECT MakeName FROM Make
        UNION ALL
    SELECT MakeName FROM ForeignMake
        ORDER BY MakeName;
    -- some makes could be duplicated in the result-set
```

## INTERSECT
Only returns the rows that exist in both result-sets from the SELECT statements

    SELECT MakeName FROM Make
      INTERSECT
    SELECT MakeName FROM ForeignMake
      ORDER BY MakeName;
    -- only makes that both Tables have in common are in the result-set

## EXCEPT
Returns all rows of the first SELECT statement, except for the rows that are a
perfect match with the second SELECT statement.

    -- What makes are stricly domestic?
    SELECT MakeName from Make
      EXCEPT
    SELECT MakeName FROM ForeignMake;


## Multiple Set Operators
The Set Operations get evaluated line by line.

```sql
    -- Create a list of unique books.
    -- Books that are in the north or south location, but not in both locations.
    -- both queries produce the same result

    -- join method
    SELECT title FROM books_north
      UNION
    SELECT title FROM books_south
      EXCEPT
    SELECT books_north.title FROM books_north
      JOIN books_south ON books_north.title = books_south.title;


    -- subquery method
    SELECT title FROM books_north
      UNION
    SELECT title FROM books_south
      EXCEPT
    SELECT title FROM (
      SELECT title FROM books_north
        INTERSECT
      SELECT title FROM books_south);
```
