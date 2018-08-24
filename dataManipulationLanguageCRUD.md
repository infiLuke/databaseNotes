# Introduction to CRUD
[CRUD Cheatsheet](https://github.com/treehouse/cheatsheets/blob/master/modifying_data_with_sql/cheatsheet.md)

## Transactions
Transactions enable safer testing of and easier rolling back of changes.

### Modes:
**Autocommit**
: normal mode; every statement is executed

**Transaction**
: statements are only executed when commit command is issued


```sql
    BEGIN TRANSACTION;      -- switch off autocommit   - or sometimes: BEGIN;

    -- make desired changes
    SAVEPOINT;
    -- make more changes

    ROLLBACK;               -- undo all changes since starting autocommit mode

    COMMIT;                 -- commit the changes:
```


*Seeding*
: populating a database for the first time, for example with a script file

## ORMs - Object Relational Mapping
A software library that interfaces with a database directly
    Hibernate (Java)
    Django ORM (Python)

## CRUD Modes
    Create      INSERT
    Read        SELECT   -- see data query language notes
    Update      UPDATE
    Delete      DELETE


## Create / 'INSERT INTO' &amp; 'VALUES' keywords

### Creating a New Row
```sql
    INSERT INTO <table> (<column#>, <column#>, ...) VALUES (<value1>, <value2>, ...);

    INSERT INTO books VALUES (16, "1984", "George Orwell", "Fiction", 1949);
    INSERT INTO books VALUES (NULL, "Dune", "Frank Herbert", "Science Fiction", 1965);
    INSERT INTO loans (id, book_id, loaned_on, return_by, returned_on) VALUES (4, 2, "2015-12-14", "2015-12-21");

    -- to auto-increment an id-column use the value <NULL>
```

### Adding Multiple Rows
```sql
    INSERT INTO books (title, author, genre, first_published)
        VALUES
            ("The Circle", "Dave Eggers", "Science Fiction", 2013),
            ("Contact", "Carl Sagan", "Science Fiction", 1985),
            ("Animal Farm", "George Orwell", NULL, 1945);
```
## Update / 'UPDATE' &amp; 'SET' keywords

### Updating all Rows
```sql
    -- assign a new value to an existing column for ALL rows
    UPDATE <table> SET <column> = <value>;
    UPDATE patrons SET last_name = "anonymous";

    -- assign new values for ALL rows to multiple columns at once
    UPDATE <table> SET <column> = <value>, <column2> = <value2>, <column3> = <value3>;
    UPDATE patrons SET email = "anon@email.com" , zip_code = 555555;
```
### Updating Specific Rows
```sql
    -- update specific rows using conditions
    UPDATE <table> SET <column> = <value> WHERE <condition>;
    UPDATE books SET genre = "Classic" WHERE id = 20;
    UPDATE loans SET returned_on = "2015-12-18" WHERE patron_id = 1 AND returned_on = NULL;
```
Use a SELECT query first to determine wheather the condition selects the correct address
UPDATE conditions work exactly like in a SELECT query

## Delete / 'DELETE FROM' keyword

### Delete All Data From a Table
```sql
    -- delete every single row in a table
    DELETE FROM <table>;
    -- delete all data from books
    DELETE FROM books;
```
### Delete specific rows
```sql
    DELETE FROM <table> WHERE <condition>;

    -- delete all Harry Potter books from a table
    DELETE FROM books WHERE title LIKE  "Harry Potter%";

    -- delete the row for patron 4
    DELETE FROM patrons WHERE id = 4;
```
