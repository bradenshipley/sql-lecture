## Creating Tables

- Define these datatypes in PostgreSQL:

  - NULL
    without value.
  - INTEGER
    An integer type is a 4 byte number that can go as high as 2,147,483,647
  - DECIMAL
    The same as an integer but the decimal allows for a value to represent digits past the decimal sign
  - FLOAT
   is a floating-point number whose precision, at least, n, up to a maximum of 8 bytes. written as float(n)
  - TEXT
    is the variable-length character string. Theoretically, text data is a character string with unlimited length.
  - VARCHAR(n)
     is the variable-length character string.  With VARCHAR(N),  you can store up to n characters. PostgreSQL does not pad spaces when the stored string is shorter than the length of the column.
     
- What does SERIAL do in Postgres? (Note: in chinook.ml this will be INTEGER PRIMARY KEY AUTOINCREMENT)
  It automatically generates a number for each row given
- What is the syntax for creating a new table?
  CREATE TABLE (tableName) (
    column1 DATATYPE,
    column2 DATATYPE,
    etc);
  
- Create a student table with this schema:

* id - integer - primary key autoincrement
* first_name - varchar(255)
* hometown - varchar(255)
* fun_fact - text

  CREATE TABLE student (
  id SERIAL,
  first_name VARCHAR(255),
  hometown VARCHAR(255),
  fun_fact TEXT);

## Inserting Data (Section 9)

- What is the syntax for inserting values into a table?
INSERT INTO VALUES (desired values in the order that the tables columns are)

- Insert the following data into the student table from above:
  first_name: 'Logan'
  hometown: 'Dallas'
  fun_fact: NULL
  
  INSERT INTO student VALUES ('Logan', 'Dallas' , NULL);

first_name: 'Garrett'
hometown: 'Dallas'
fun_fact: 'Postgres is progress.'
INSERT INTO student VALUES ('Garrett', 'Dallas' , 'Postgres is progress');

## Updating Data (Section 9)

- What is the syntax for updating existing values in a table?
UPDATE tableName SET valueToBeChanged=newValue WHERE anyStipulations

- Update Logan's fun_fact to be 'I love SQL' using his id.
UPDATE student SET fun_fact = 'I love SQL' WHERE id=1;

## Querying Data (Section 2 and 3)

### Syntax

- How do you select all columns from a table?
SELECT * FROM table

- How do you select 2 specific columns from a table?
SELECT (column1, column2) FROM table

- What does DISTINCT do?
The SELECT DISTINCT statement is used to return only distinct (different) values.

- What does ORDER BY do?
The ORDER BY keyword is used to sort the result-set in ascending or descending order. The ORDER BY keyword sorts the records in ascending order by default. To sort the records in descending order, use the DESC keyword.

- Practice: Get all the information we currently have in the student table, sorted by id, with the highest id first.

### WHERE clauses

- What are 4 comparison operators in PostgreSQL? (Hint: Look in the WHERE section)
 = < > <= >= !=
- What do AND, OR and IN do?
AND and OR work as they normally do. IN is used as a comparison operator to check a value against a set of values.
EX: value IN (value1,value2,...) || value IN (SELECT value FROM tbl_name);
- How do you check for NULL values? (Hint: it's not = NULL or != NULL)
IS NULL and  NOT NULL
- What does LIMIT do?
limits the amount of results you get
- What do each of these aggregate functions do?

  - min()
  gets the minimum value
  - max()
  gets the maximum value
  - sum()
  gets the sum of all or distinct values
  - avg()
  get the average of all values
  - count()
  gets the count of how many rows there are with a given paramater

- How does LIKE work?
a pattern matcher.
EX: SELECT * FROM student WHERE first_name LIKE 'Log%'
would return the row with first_name Logan, because it is a match for the first three characters

- What's the difference between % and \_ with LIKE?
 Can use % to check against a sequence or _ to check against a single character. 
