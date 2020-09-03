# SQL-Basics
What is SQL ?
SQL is a standard language for sorting, manipulating and retrieving data
in databases.
What Can SQL do?
SQL can execute queries against a database
SQL can retrieve data from a database
SQL can insert records in a database SQL
can update records in a database SQL
can delete records from a database SQL
can create new databases
SQL can create new tables in a database
Data types
Text data type:
VARCHAR - A variable-length string between 1 and 255 characters in length.
For example, VARCHAR(25). You must define a length when creating a
VARCHAR field.
CHAR - A fixed-length string between 1 and 255 characters in length (for
example CHAR(5)), right-padded with spaces to the specified length when
stored. Defining a length is not required, but the default is 1.
Number data type:
INTEGER - A normal-sized integer that can be signed or unsigned. If signed,
the allowable range is from -2147483648 to 2147483647. If unsigned, the
allowable range is from 0 to 4294967295. You can specify a width of up to
11 digits.
FLOAT - A floating-point number that cannot be unsigned. You can define the
display length (M) and the number of decimals (D). This is not required and will
default to 10,2, where 2 is the number of decimals and 10 is the total number of
digits (including decimals). Decimal precision can go to 24 places for a FLOAT.
DOUBLE - A double precision floating-point number that cannot be unsigned. You
can define the display length (M) and the number of decimals (D). This is not
required and will default to 16,4, where 4 is the number of decimals. Decimal
precision can go to 53 places for a DOUBLE. REAL is a synonym for DOUBLE.
Date data type:
DATE() - A date in YYYY-MM-DD format, between 1000-01-01 and 9999-12-
31. For example, December 30th, 1973 would be stored as 1973-12-30.
TIMESTAMP() - A timestamp between midnight, January 1st, 1970 and
sometime in 2037. This looks like the previous DATETIME format, only without
the hyphens between numbers; 3:30 in the afternoon on December 30th, 1973
would be stored as 19731230153000 ( YYYYMMDDHHMMSS ).
Basic Commands
1. To log the MysQL client session and create a log file:
Syntax : mysql> tee <destination>/<file_name>.out;
Ex : mysql> tee D:/practical/Lab_01.out;
2. Create a database
Syntax :CREATE DATABASE <databaseName>;
Ex :CREATE DATABASE student;
3. Use database
Syntax : USE <databaseName>;
Ex : USE student;
4. Show tables in a database
Syntax : SHOW TABLES ;
5. Delete database
Syntax :
i. DROP DATABASE <databaseName> ; (Delete the database (irrecoverable!))
ii. DROP DATABASE IF EXISTS <databaseName> ; ( Delete if it exists )
Ex :DROP DATABASE student; or DROP DATABASE IF EXISTS
student ;
6. Create table with different data types
i. Without primary key/foreign key
Syntax : CREATE TABLE <table_name> (
<column1 datatype>, <column2 datatype>,<column3 datatype>,..);
Ex: CREATE TABLE Persons
( PersonID int, LastName varchar(255), FirstName varchar(255),
Address varchar(255), City varchar(255) );
ii. With primary key/foreign key
Syntax :
CREATE TABLE <tableName> ( <columnName columnType
columnAttribute, ...>
PRIMARY KEY(<columnName>), FOREIGN KEY (<columnNmae>)
REFERENCES <tableName> (<columnNmae>) );
Ex : CREATE TABLE student
(
id INT unsigned NOT NULL AUTO_INCREMENT,
name VARCHAR(150) NOT NULL,
course VARCHAR(150) NOT NULL,
birthday DATE NOT NULL,
PRIMARY KEY (id)
);
7. Alternate table structure
i. Add column
Syntax : ALTER TABLE <table_name> ADD <column_name> <datatype>;
EX: ALTER TABLE Customers ADD Email varchar(255);
ii. Delete a column
Syntax :ALTER TABLE <table_name> DROP COLUMN
<column_name>; Ex : ALTER TABLE Customers DROP COLUMN Email;
iii. Modify column
Syntax : ALTER TABLE <table_name> MODIFY COLUMN <column_name>
datatype;
Ex : ALTER TABLE student MODIFY COLUMN gender CHAR;
iv. Add primary key
Syntax : ALTER TABLE <table name> ADD PRIMARY KEY (<column name>);
EX : ALTER TABLE Persons ADD PRIMARY KEY (ID)
v. Add foreign key
Syntax : ALTER TABLE <table name> ADD FOREIGN KEY (column name)
REFERENCES <reference table>(<reference table primary key
column name>);
Ex: ALTER TABLE Orders
ADD FOREIGN KEY (PersonID) REFERENCES Persons(PersonID);
8. Describe table
Syntax : DESCRIBE <table name>;
Ex :DESCRIBE student;
9. Insert data
a. Using insert into command with correct sequence of columns
Syntax :INSERT INTO <tablename> VALUES <…Values in order >
Ex : INSERT INTO student VALUES ( 1,'Sandy', 'Lennon', '2015-01-03' ),
( 2,'Cookie', 'Casey', '2013-11-13' ),( 3,'Charlie', 'River', '2016-05-21' );
b. Using insert into command with specific columns in a table
Syntax :INSERT INTO <tablename> <specific column name> VALUES <…Values
in order >;
Ex : INSERT INTO student (course,name, DOB) VALUES ('Lennon', 'Sandy',
'2015-01-03' ), ('Casey', 'Cookie','2013-11-13' );
c. Using insert in to command with TEXT file
Syntax:
i. LOAD DATA LOCAL INFILE ' <file path>' INTO TABLE <table name>
COLUMNS TERMINATED BY '\t';
Ex : LOAD DATA LOCAL INFILE ' C :\studentTb.txt '
INTO TABLE student COLUMNS TERMINATED BY '\t';
ii. BULK INSERT <table name> FROM <file path> WITH
(FIELDTERMINATOR=’,’, ROWTERMINATOR=’\n’) GO;
Ex: BULK INSERT student FROM ‘C :\stuDb.txt’ WITH
(FIELDTERMINATOR=’,’, ROWTERMINATOR=’\n’) GO;
10. Delete data in a table
a. Delete all data in table
Syntax:DELETE FORM <table name>;
Ex: DELETE FROM student;
b. Delete specific data in table
Syntax:DELETE FORM <table name> WHERE <column
name>=<specific value>;
Ex: DELETE FROM student WHERE id=1;
11. Update data in a table
Syntax:UPDATE <table name> SET <column1>=<value1>, <column2>=<value2>,…
WHERE <condition>;
Ex: UPDATE student SET name=’Adam’ WHERE id=1;
12. Drop table
Syntax:DROP TABLE <table name>;
Ex:DROP TABLE student;
13.Select data in a
table a. All columns
Syntax: SELECT * FROM <table name>;
Ex: SELECT * FROM student;
b. Specific column
Syntax: SELECT <column1>,<column2>,… FROM <table name>;
Ex: SELECT course,name FROM student;
c. Distinct
Syntax: SELECT DISTINCT <column name> FROM <table name>;
Ex: SELECT DISTINCT course FROM student;
d. Where
Syntax: SELECT <column name> FROM <table name>;
Ex: SELECT DISTINCT course FROM student;
e. AND, OR, NOT
Syntax: SELECT <specific column> FROM <table name>
WHERE <condition1> AND <condition2>
Ex: SELECT name,birthday FROM student WHERE id > 10 AND course =’IT’;
f. Order by
Syntax: SELECT <specific column> FROM <table name> ORDER BY id DESC;
Ex: SELECT name,birthday FROM student ORDER BY id DESC;
g. Minimum and maximum
Syntax: SELECT MIN(<specific column>) FROM <table name>;
Ex: SELECT MIN(salary) FROM;
h. Like
Syntax: SELECT <specific column> FROM <table name> WHERE <column
name> LIKE <patern>;
Ex: SELECT name,course,birthday FROM student WHERE name LIKE %a%;
i. Group by
Syntax : SELECT <column_name> FROM
GROUP BY <column_name>;
Ex : SELECT name FROM student
GROUP BY faculty;
<table_name>
j. Having
Syntax : SELECT <column_name> FROM <table_name>
GROUP BY <column_name>
HAVING <condition>;
Ex : SELECT name FROM student
GROUP BY faculty
HAVING age > 17;
k. Between
Syntax: SELECT <specific column> FROM <table name> WHERE
<condition1> AND <condition2>;
Ex: SELECT name,birthday FROM student WHERE age BETWEEN 5 AND 15;
