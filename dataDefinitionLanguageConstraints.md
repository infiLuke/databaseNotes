# SQL: Data Definition Language Constraints

## 'PRIMARY KEY' constraint
```sql
    -- create a table with a primary key
    CREATE TABLE tableName (
      ID SMALLINT PRIMARY KEY,
      date DATE,
      city VARCHAR(255),
      state VARCHAR(255),
      venue VARCHAR(255)
    );

    -- primary key can also be declared after the column names
    CREATE TABLE tableName (
      ID SMALLINT,
      date DATE,
      city VARCHAR(255),
      state VARCHAR(255),
      venue VARCHAR(255),
      PRIMARY KEY (ID)
    );
```


## 'AUTOINCREMENT' constraint
```sql
    -- create a table with a autoincrementing column
    -- autoincrement always needs to be paired with the integer data type
    CREATE TABLE tableName (
      ID INTEGER PRIMARY KEY AUTOINCREMENT,
      date DATE,
      city VARCHAR(255),
      state VARCHAR(255),
      venue VARCHAR(255)
    );
```

## 'FOREIGN KEY' &amp; 'REFERENCES' constraint (foreign keys)
> Enabling Foreign Key support in SQLite: `PRAGMA FOREIGN_KEYS = ON`

```sql
    CREATE TABLE tableName (
        ID INTEGER PRIMARY KEY AUTOINCREMENT,
        idName SMALLINT REFERENCES tableName(ID),
        idName2 INTEGER REFERENCES tableName2(ID)
    );

    -- same as above
    CREATE TABLE tableName (
        ID INTEGER PRIMARY KEY AUTOINCREMENT,
        idName SMALLINT,
        idName2 INTEGER,
        FOREIGN KEY (idName) REFERENCES tableName(ID),
        FOREIGN KEY (idName2) REFERENCES tableName2(ID)
    );
```

## 'DEFAULT' constraint
sets a default value for a column when no column is specified

```sql
    ALTER TABLE Concerts ADD country VARCHAR(255) DEFAULT 'USA';
```
