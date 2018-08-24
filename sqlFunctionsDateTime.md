# Date Time Functions
DateTime Functions and the way dates are stored in databases vary greatly depending upon the implementation of the relational database management system.

## selecting the current date and time
```sql
    DATE("now");
    TIME("now");
    DATETIME("now");
```

selecting all orders that were placed today:

    SELECT * FROM orders WHERE status = "placed" AND ordered_on = DATE("now");

## Calculating Dates
```sql
    DATE('timeValue', 'modifier[] ...')

    DATE("2018-05-20", "-7 days");
    DATE("2018-05-20", "+7 days");
    DATE("2018-05-20", "+6 months");
    DATE("2018-05-20", "-5 years");

    DATE("2018-02-01", "+1 month", "+7 days"); -- returns whether the year is a leap-year or not


-- COUNT how many orders were placed in the last seven days:

    SELECT COUNT(*) FROM orders WHERE ordered_on BETWEEN
                                DATE("now", "-7 days") AND DATE("now", "-1 day");
                                -- 7 days ago and yesterday
```
## Formatting Dates and Times

### DateTime Datatypes
1. date         (2018-07-25)
2. time         (21:04:01)
3. datetime     (2018-07-25 21:04:01)

### Simple Formatting with datetype conversion
    DATE("2018-07-25 21:04:01"); -- return 2018-07-25
    TIME("2018-07-25 21:04:01"); -- return 21:04:01

### STRFTIME() Function
String Format Time Function
```sql
    STRFTIME("%d/%m/%Y", "2018-07-25 21:04:01"); -- return 25/07/2018

    STRFTIME('format', 'time', 'modifier[] ...')

    STRFTIME("%H hours left", "2018-07-25 21:04:01", "+1 hour"); -- return 22 hours left
```
