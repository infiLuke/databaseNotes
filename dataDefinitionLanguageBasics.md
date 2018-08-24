# Data Definition Language

## Creating Tables

### without data types
```sql
    CREATE TABLE tableName (column1, column2, column3 ...);
    -- SQLite does not use dataTypes except for 'INTEGER'
```

### with data types
```sql
    -- create a table with data types
    CREATE TABLE tableName (
      ID SMALLINT,
      columnID dataType,
      city VARCHAR(255),
      state VARCHAR(255),
      venue VARCHAR(255)
    );
```


## Modify Tables 'ALTER TABLE'

### Add a column
    ALTER TABLE tableName ADD columnName dataType;
### Add a column with a default value for all records
    ALTER TABLE tableName ADD columnName dataType DEFAULT 'value';

### Rename a table
    ALTER TABLE tableName RENAME TO newTableName;


## Removing Tables

    DROP TABLE tableName;

