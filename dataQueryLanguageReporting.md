# Database Reporting

for dynamic websites
for company reports

Ordering
Limiting

## Ordering Results
Use Case: Sorting
    by contact name
    by year
    by price
    by article date

### 'ORDER BY' keyword
```sql
    SELECT <columns> FROM <table> ORDER BY <column> ASC; (default)
    SELECT <columns> FROM <table> ORDER BY <column> DESC;

    SELECT <columns> FROM <table> ORDER BY <column1> ASC, <column2> ASC; (default)
    -- order first by last name, then as a second priority by first name
    SELECT * FROM customers ORDER BY last_name ASC, first_name ASC;
```

## Limiting The Number Of Results

### 'LIMIT' keyword
```sql
    SELECT <column> FROM <table> LIMIT <# of rows>;
    SELECT <column> FROM <table> WHERE <condition> LIMIT <# of rows>;
    SELECT <column> FROM <table> ORDER BY <column> ASC LIMIT <# of rows>;

    -- display the top three results
    SELECT * FROM products ORDER BY price DESC LIMIT 3;

    -- display the five oldest fantasy books
    SELECT * FROM books WHERE genre = "Fantasy" ORDER BY first_published LIMIT 5;
```

## Paging Through Results (skipping)

### 'OFFSET' keyword
```sql
    -- the 'OFFSET' keyword is used with the 'LIMIT' keyword
    SELECT <column> FROM <table> LIMIT <# of rows> OFFSET <skipped rows>;
    -- shorthand form
    SELECT <column> FROM <table> LIMIT <# of rows>, <skipped rows>;

usecase: display 10 items per page; page 2:
    SELECT * FROM items LIMIT 10 OFFSET 10;
```
