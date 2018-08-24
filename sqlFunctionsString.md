# SQL Functions String Functions

    "Double Quotes"     are used for table, column and alias values
    'Single Quotes'     are used for String values

## Concatenation Operator
```sql
    ||          SQLite, PostgreSQL, Oracle
    '+'         MS SQL
    CONCAT()    MySQL, Postgres, MS SQL

    -- join two or three values
    SELECT <value or column> || <value or column> FROM <table>;
    SELECT <value or column> || <value or column> || <value or column> FROM <table>;
    SELECT CONCAT(<value or column>, <value or column>, <value or column>) FROM table;

    -- assign alias to joined values
    SELECT <value or column> || <value or column> AS <alias> FROM <table>;

    -- join first and last name with a 'space' in the middle
    SELECT first_name || " " || last_name AS "Name" FROM phone_book ORDER BY last_name;
```
## Finding the Length of Text
### LENGTH() function
```sql
    -- functions can be used in the SELECT part, or in the WHERE part
    SELECT LENGTH(<column>) AS <alias> FROM <table>;
    SELECT <columns> FROM <table> WHERE LENGTH(<column>) <operator> <value>;

    -- display username and length of string
    SELECT username, LENGTH(username) AS "Length of Username" FROM customers ORDER BY "Length of Username" DESC;
```
## Changing the Case of Text
### UPPER() &amp; LOWER() functions
```sql
    SELECT UPPER(<value or column>) FROM table;
    SELECT LOWER(<value or column>) FROM table;

    -- search the email column with case insensitivity:
    SELECT * FROM customers WHERE LOWER(email) = "example@hotmail.com";
```
## Creating Excerpts From Text
### SUBSTR() function
*Substring Method*
: obtaining a smaller string (text) from a larger string (text).
```sql
    SUBSTR(<value or column>, <start>, <length of new string>)

    -- select only the first 30 characters for the description
    SELECT name, SUBSTR(description, 1, 30) || "..." AS short_description, price FROM products;

    SELECT SUBSTR(first_name, 1, 1) AS initial, last_name FROM customers;
```
## Replacing Portions of a String
### REPLACE() function
```sql
    REPLACE(<value or column>, <target>, <replacement>)

    -- select all addresses that are either "California" or "CA"
    SELECT * FROM addresses WHERE REPLACE(state, "California", "CA") = "CA";

    -- replace a portion of a string, display email symbol as <at>,
    SELECT REPLACE(email, "@", "<at>") AS obfuscated_email FROM customers;
```
