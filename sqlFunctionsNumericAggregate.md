# SQL: Numeric &amp; Aggregate Functions

## Counting Results
### COUNT() function
count wil ignore all values that are NULL

    -- count all the rows where values(everything that is not NULL) are present
    SELECT COUNT(*) FROM customers;

    -- count all users with the first name "Andrew"
    SELECT COUNT(*) FROM customers WHERE first_name = "Andrew";

    -- count all products in the clothing category
    SELECT COUNT(*) FROM products WHERE category = "Clothing";

### Convention

    By convention COUNT(1) is used to count all entries in a table.
    The result should be identical to COUNT(*) or COUNT(primaryKeyColumn)

#### DISTINCT keyword
return only one result for each unique entry
    -- display each unique name only once
    SELECT DISTINCT first_name FROM patrons;

    -- count how many different categories of products there are
    -- solution: display each unique category only once and count it
    SELECT COUNT(DISTINCT category) FROM products;

    -- count all sci-fi books
    SELECT COUNT(*) AS scifi_book_count FROM books WHERE genre = "Science Fiction";

#### Counting Groups of Rows: GROUP BY keyword
enables use of functions like COUNT() on items that are grouped with the GROUP BY keyword

    SELECT * FROM products GROUP BY category;
    -- return: each unique category

    SELECT COUNT(*) AS product_count FROM products GROUP BY category;
    -- count the rows in each GROUP BY group
    -- return: the number of entries in each category

    SELECT COUNT(<column>) FROM <table> GROUP BY <column> with common value>;

## Getting the Grand Total
### SUM() function

    SUM(<column>) FROM <table>

    -- get the total of all placed orders
    SELECT SUM(cost) FROM orders;

    -- get the total of each customers placed orders
    SELECT SUM(cost) AS total_spending, user_id FROM orders
                                                        GROUP BY user_id;

    -- get the customer who spent the most money
    SELECT SUM(cost) AS total_spending, user_id FROM orders
                                                        GROUP BY user_id
                                                        ORDER BY total_spending DESC
                                                        LIMIT 1;

#### HAVING keyword
HAVING works just like WHERE, but is used on aggregated values
HAVING is used on aggregated information
WHERE is used for individual rows

    -- select all customers that spent more than $250.
    SELECT SUM(cost) AS total_spending, user_id FROM orders
                                                        GROUP BY user_id
                                                        HAVING total_spending >= 250
                                                        ORDER BY total_spending DESC;

    SELECT SUM(<numeric column>) AS <alias> FROM <table>
            GROUP BY <another column>
            HAVING <condition>
            ORDER BY <column>;

## Getting an Average from a Column
### AVG() function

    -- select the average cost per order
    SELECT AVG(cost) AS average FROM orders;

    -- select the average cost per customer;
    SELECT AVG(cost) AS average, user_id FROM orders GROUP BY user_ID;


    SELECT AVG('numericColumn') FROM 'tablename';

## Selecting the Lowest or Highest Value from a Column
### MIN() &amp; MAX() functions

    SELECT MIN('numericColumn') FROM 'tableName';
    SELECT MIN('numericColumn') FROM 'tableName' WHERE ... ;
    SELECT MAX('numericColumn') FROM 'tableName' GROUP BY ...;


## Performing Math on Numeric Types
### Operators

    =   !=
    <   >   <=  >=
    ||

    +
    -
    *
    /

### Outputting Values with SELECT statements

    SELECT 'Hello';
    SELECT 5 + 4;
    SELECT 12 - 20;
    SELECT 2 * 2 * 2 * 2 * 2;

    SELECT 5 / 2;           --> 2
    SELECT 5.0 / 2;         --> 2.5
    SELECT 5 / 2.0;         --> 2.5


## Rounding Numeric Data Types
### ROUND() function
Calulating sales tax for products

    SELECT name, ROUND(price * 1.06, 2) AS "Price in Florida" FROM products;

    ROUND('value', 'decimalPlaces')

