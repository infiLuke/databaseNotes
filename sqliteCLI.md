# Running SQL from the terminal

## Installation
sudo apt-get update
sudo apt-get install sqlite3 libsqlite3-dev

## Running SQLite
type sqlite3 in console to enter the program

    .help           list of commands
    .quit           exit sqlite3

    .databases      show list of databases
    .tables         show list of tables
    .schema         show list of tables and their schema
    .fullschema

    .mode           select display mode for console line output
                        column (prefered mode)
    .width          set column width for "column" mode
    .header         toggle display mode for column headers

    .show           display settings

    .output         specify the standard output location
                    used for .dump - .schema - .table - SELECT etc.
                    use plain .output to normalize behavior

    .read file.txt  to read in prewritten SQL code
    .dump           dump database in SQL text format
    .save           save to binary file
    .clone          clone database

    sqlite3 newDatabase.db          creates new database

