# SQL Basics
Structured Query Language

## SQL Databases
* MySQL (open-source, controlled by Oracle, web-apps)
* PostgreSQL (open-source, no corporation, slower in performance, web-apps)
* Microsoft SQL (closed-source, large corporations)
* Oracle (closed-source, banking sector)
* SQLite (open-source, single file, stored locally without server, cellphones, mp3-players, smart-appliances)

## Other Types of Databases
* MongoDB
* CouchBase
* Redis
These databases use a different language

## Schema
The schema refers to how data is organized in a database

## Data Types
TEXT, INT, DATE etc.

## Database Tools
* Mode Analytics (business level app)
* pg Admin (for PostgreSQL)
* phpMyAdmin (MySQL)
* MySQL Workbench (for MySQL)

## SQL Syntax
Keywords
statement = query ~ question to database

### 'SELECT' &amp; 'FROM' keywords
What is all the information we have about each book in the books table?
    SELECT * FROM books;
    ~ 'retrieve' 'everything' 'from' 'table books'

Select specific columns from a table:
    SELECT <column names> FROM <table name>;

    SELECT email FROM clients;
    ~ 'retrieve' 'column email' 'from' 'table clients'
    SELECT first_name, email FROM clients;
    ~ 'retrieve' 'column first name' & 'column email' 'from' 'table clients'

### 'AS' keyword
Filter specific columns from a table with a custom column name:
    SELECT <column name> AS <"new name"> FROM <table name>;

    SELECT first_name AS "First Name", last_name AS Name FROM clients;

### Comments
Comments are written with a double dash '--'

    -- This is a comment line in SQL

## Searching Tables with 'WHERE'

    SELECT <columns> FROM <table> WHERE <condition>;
    -- <condition>: column name + operator + value

    -- select cells 'columns' from table 'table' when 'column name' is equal to the value 'value'
    SELECT <columns> FROM <table name> WHERE <column name> = <value>;

    -- select columns when the condition is not true
    SELECT <columns> FROM <table name> WHERE <column name> != <value>;

### Searching with Relational Operators

    -- Select all books that were published after 2005
    SELECT * FROM books WHERE first_published > 2005;

    -- Select all books that were published before the 20th century
    Select * FROM books WHERE first_published < 1900;

### Searching with Multiple Conditions
#### 'AND', 'OR' keywords
    SELECT tile FROM books WHERE author = "J.K. Rowling" AND first_published < 2000;

    SELECT title, author FROM books WHERE author = "Ernest Cline" OR author = "Andy Weir";


### Seaching for Multiple Values
#### 'IN' keyword
    -- Select all column cells from table when values1-2-... are matching in column name
    SELECT <colums> FROM <table> WHERE <column name> IN (<value1>, <value2>, <value...>);

    -- Select when values do not match
    SELECT <colums> FROM <table> WHERE <column name> NOT IN (<value1>, <value2>, <value...>);

### Searching within a Range of Values
#### 'BETWEEN' keyword
    SELECT title, author FROM books WHERE first_published BETWEEN 1800 AND 1899;
    -- same as:
    SELECT title, author FROM books WHERE first_published >= 1800 AND first_published <= 1899;

    SELECT <columns> FROM <table> WHERE <column> BETWEEN <lesser value> AND <greater value>;

### Searching for a Pattern
#### 'LIKE' keyword
    SELECT <columns> FROM <table> WHERE <column> LIKE <pattern>;
    -- use the 'LIKE' keyword followed by a value with one or more wildcards: '%'
    -- the search pattern is case-insensitive

    SELECT title FROM books WHERE title LIKE "%Martian";

    SELECT title FROM books WHERE title LIKE "%universe%" AND genre LIKE "non fiction";

### Search for Empty Fields or Filter Out Empty Fields
#### 'IS NULL' 'IS NOT NULL' keywords
    SELECT <columns> FrOM <table> WHERE <column> IS NULL;
    -- to select empty values

    SELECT <columns> FrOM <table> WHERE <column> IS NOT NULL;
    -- to filter out missing values

    -- Select all info from loans that have not been returned
    -- the returned_on field is empty
    SELECT * FROM loans WHERE return_by > "2015-12-18" AND returned_on IS NULL;

    -- Select all info from loans that have been returned
    -- the returned_on field holds a value
    SELECT * FROM loans WHERE return_by > "2015-12-18" AND returned_on IS NOT NULL;

## Selecting from Multiple Tables

    SELECT * FROM <table1>, <table2>;
    SELECT * FROM <table1>, <table2>;

