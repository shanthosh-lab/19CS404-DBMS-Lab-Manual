Experiment 2: DDL Commands
AIM
To study and implement DDL commands and different types of constraints.

THEORY
1. CREATE
Used to create a new relation (table).

Syntax:

CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
2. ALTER
Used to add, modify, drop, or rename fields in an existing relation. (a) ADD

ALTER TABLE std ADD (Address CHAR(10));
(b) MODIFY

ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
(c) DROP

ALTER TABLE relation_name DROP COLUMN field_name;
(d) RENAME

ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
3. DROP TABLE
Used to permanently delete the structure and data of a table.

DROP TABLE relation_name;
4. RENAME
Used to rename an existing database object.

RENAME TABLE old_relation_name TO new_relation_name;
CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).

1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column. Syntax:

CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
2. UNIQUE
Ensures that values in a column are unique. Syntax:

CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
3. CHECK
Specifies a condition that each row must satisfy. Syntax:

CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
4. PRIMARY KEY
Used to uniquely identify each record in a table. Properties: Must contain unique values. Cannot be null. Should contain minimal fields. Syntax:

CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
5. FOREIGN KEY
Used to reference the primary key of another table. Syntax:

CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:

CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
Question 1
image
INSERT INTO Customers (CustomerID, Name, Address, City, ZipCode)
VALUES(301, 'Michael Jordan', '123 Maple St', 'Chicago', 60616);
Output:

image
Question 2
image
ALTER TABLE customer 
RENAME city to location;
Output:

image
Question 3
image
ALTER TABLE Companies RENAME name to first_name;
ALTER TABLE Companies ADD column mobilenumber number;
alter table Companies add column DOB Date;
alter table Companies add column State varchar(30);
Output:

image
Question 4
image
CREATE TABLE Reviews(
    ReviewID INTEGER,
    ProductID INTEGER,
    Rating REAL,
    ReviewText TEXT
);
Output:

image
Question 5
image
CREATE TABLE item (
    item_id TEXT primary key,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT CHECK (length(icom_id)=4),
    FOREIGN KEY (icom_id) REFERENCES company(com_id)  
    on update set null  on delete  set null);
Output:

image
Question 6
image
CREATE TABLE contacts(
    contact_id INTEGER primary key,
    first_name TEXT not NULL,
    last_name TEXT not NULL,
    email TEXT,
    phone TEXT not NULL CHECK (length(phone)>=10)
    );
Output:

image
Question 7
image
INSERT INTO Customers(CustomerID, Name, Address, Email)
SELECT CustomerID, Name, Address, Email
FROM Old_customers
Output:

image
Question 8
image
CREATE TABLE Shipments(
    ShipmentID INTEGER primary key,
    ShipmentDate DATE,
    SupplierID INTEGER,
    OrderID INTEGER,
    FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierID),
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
    );
Output:

image
Question 9
image
insert into products(Name,Category,Price,Stock)
values("Smartphone","Electronics",800,150),("Headphones" ,"Accessories",200,300)
Output:

image
Question 10
image
create table Attendance(
AttendanceID int primary key,
EmployeeID int ,
AttendanceDate date,
Status text check(status in('Present', 'Absent', 'Leave')),
foreign key (EmployeeID) references Employees(EmployeeID));
Output:

image
Grade
image
RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
