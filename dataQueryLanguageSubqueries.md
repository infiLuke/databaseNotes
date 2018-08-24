# SQL Subqueries
Subqueries are always written in parenthesis

## Subquery Use-Cases
- in a where clause, when criteria for a where clause is not specifically known
- a temporary dataview or dataset joined with other tables is needed


## Using 'IN' And 'NOT IN' With A Subquery To Filter Data
Using a subquery to filter an outer query.
You can only select **one column** in the subquery.

```sql
    SELECT * FROM sales WHERE CarID IN (
        SELECT CarID FROM Car WHERE ModelYear = 2015
        );

    SELECT ModelName FROM Model WHERE ModelID IN (
        SELECT ModelID FROM Car WHERE StickerPrice > 30000
        );
```
## Using A Subquery To Create A Temporary Table
Instead of joining to another table join to a subquery
Derived or temporary tables have to be aliased with `AS` to be referenceable
```sql
    SELECT * FROM table
    JOIN (SELECT column1, column2 FROM table2) AS t
        ON table.ID = t.ID;


    -- Generate a report that lists the book titles from both library locations and
    -- count the total number of books with the same title.

    SELECT title AS "Title", COUNT(1) AS "Number Of Books" FROM (
      SELECT * FROM books_north
        UNION ALL
      SELECT * FROM books_south
      )
      GROUP BY title
      ORDER BY title ASC;


    -- Generate a report that lists a patron's first name, email and loan count for
    -- loans that haven't been returned.

    SELECT first_name, last_name, email, COUNT(1) AS "Total Unreturned Books" FROM patrons
      JOIN (
        SELECT * FROM loans_north
          UNION ALL
        SELECT * FROM loans_south
        ) AS loans ON patrons.id = loans.patron_id
      WHERE returned_on IS NULL
      GROUP BY patrons.id;


    SELECT * FROM Sale
        INNER JOIN (SELECT CustomerID FROM Customer WHERE Gender = 'F') AS femaleCustomers
        ON Sale.CustomerID = femaleCustomers.CustomerID;
```
