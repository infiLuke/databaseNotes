# SQL: Joining Tables

## Joining Single Tables

    SELECT name FROM table1 JOIN table2 ON table1.name-ID = table2.name;

Join on foreign and primary keys to connect tables successfully.

## Joining Multiple Tables

    SELECT * FROM subjects
            JOIN classes ON subjects.id = classes.subject_id
            JOIN teachers ON classes.teacher_id = teachers.id;
