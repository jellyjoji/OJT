# SQL 
[SQL Tutorial](https://www.w3schools.com/sql/sql_create_table.asp)
## 데이터의 무결성 5가지 제약조건 (constraint)
1. NOT NULL : 필수 입력 사항
2. UNIQUE : 중복성 배제, 유일한 값으로 존재해야 함
3. PRIMARY KEY(기본키) : NOT NULL + UNIQUE 
4. FOREIGN KEY(외래키) : 참조하는 테이블에서 존재하는 값만 사용 가능
5. CHECK : 주어진 조건에 해당하는 값만 입력 가능

# SELECT 
```
SELECT column1, column2, ...
FROM table_name;

// SELECT * FROM Customers;
// ELECT CustomerName, City FROM Customers;
```
## distinct
```
SELECT DISTINCT column1, column2, ...
FROM table_name;

//SELECT DISTINCT Country FROM Customers;
```
## where
```
SELECT column1, column2, ...
FROM table_name
WHERE condition;

// SELECT * FROM Customers
// WHERE Country='Mexico';
```
### like
```
SELECT column1, column2, ...
FROM table_name
WHERE columnN LIKE pattern;

// SELECT * FROM Customers
// WHERE CustomerName LIKE 'a%';
// a% : a 로 시작하는 단어를 모두 선택
```
#### Wildcard Characters
`%`	: Represents zero or more characters
`_`	: Represents a single character
`[]`	: Represents any single character within the brackets 
`^`	: Represents any character not in the brackets 
`-`	: Represents any single character within the specified range 
`{}`	: Represents any escaped character 

### group by
```
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
ORDER BY column_name(s);

// SELECT COUNT(CustomerID), Country
// FROM Customers
// GROUP BY Country
// ORDER BY COUNT(CustomerID) DESC;
```
### having
```
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
HAVING condition
ORDER BY column_name(s);

// SELECT COUNT(CustomerID), Country
// FROM Customers
// GROUP BY Country
// HAVING COUNT(CustomerID) > 5
// ORDER BY COUNT(CustomerID) DESC;
```
## order by
```
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;

// SELECT * FROM Products
// ORDER BY Price;
```
## and
```
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;

// SELECT *
// FROM Customers
// WHERE Country = 'Spain' AND CustomerName LIKE 'G%';
```
## or
```
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;

// SELECT *
// FROM Customers
// WHERE Country = 'Germany' OR Country = 'Spain';
```
## nor
```
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition;

// SELECT * FROM Customers
// WHERE NOT Country = 'Spain';
```
# INSERT INTO
```
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);

// INSERT INTO Customers (CustomerName, City, Country)
// VALUES ('Cardinal', 'Stavanger', 'Norway');
```
# NOT NULL
```
SELECT column_names
FROM table_name
WHERE column_name IS NULL;

// SELECT CustomerName, ContactName, Address
// FROM Customers
// WHERE Address IS NULL;
```
# IS NOT NULL

```
SELECT column_names
FROM table_name
WHERE column_name IS NOT NULL;

// SELECT CustomerName, ContactName, Address
// FROM Customers
// WHERE Address IS NOT NULL;
```

# UPDATE
```
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;

// UPDATE Customers
// SET ContactName = 'Alfred Schmidt', City= 'Frankfurt'
// WHERE CustomerID = 1;
```
# DELETE
```
DELETE FROM table_name WHERE condition;

// DELETE FROM Customers WHERE CustomerName='Alfreds Futterkiste';
```
# COUNT
해당 행에 몇개가 들어있는지 세아려준다.
```
SELECT COUNT(column_name)
FROM table_name
WHERE condition;

// SELECT COUNT(*)
// FROM Products;
```
# SUM
숫자로 된 열의 합산을 계산해준다.
```
SELECT SUM(column_name)
FROM table_name
WHERE condition;

// SELECT SUM(Quantity)
// FROM OrderDetails;
```
---
# DATABASE
## CREATE DB
```
CREATE DATABASE databasename;
```
## DROP DB
```
DROP DATABASE databasename;
```
## CREATE TABLE
```
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);

CREATE TABLE Persons (
    PersonID int,
    LastName varchar(255),
    FirstName varchar(255),
    Address varchar(255),
    City varchar(255)
);
```
## DROP TABLE
```
DROP TABLE table_name;
```
## ALTER TABLE
기존 테이블의 열을 추가, 삭제, 수정할때 쓴다.
```
ALTER TABLE table_name
ADD column_name datatype;
// ALTER TABLE Customers
// ADD Email varchar(255);

ALTER TABLE table_name
DROP COLUMN column_name;
// ALTER TABLE Customers
// DROP COLUMN Email;

ALTER TABLE table_name
RENAME COLUMN old_name to new_name;
```
### NOT NULL
필수 설정값.
테이블을 생성할때 비워두면 안되는 곳을 not null 으로 표기한다.
```
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255) NOT NULL,
    Age int
);
```
### UNIQE
컬럼의 값이 중복되지 않도록 하는 제약이다. 
테이블의 각 레코드가 유일한 레코드가 될수있게한다.
```
CREATE TABLE Persons (
    ID int NOT NULL UNIQUE,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);
```
### PRIMARY KEY
NOT NULL + UNIQUE 
행을 고유하게 구분해 주는 최소의 정보이다.
기본 필드 키(PK)가 없으면 관계형 데이터베이스 쿼리에 문제가 발생한다.
```
CREATE TABLE Persons (
    ID int NOT NULL PRIMARY KEY,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);
```
### FOREIGN KEY
foreign key를 사용하는 이유는 참조 무결성을 위해서이다. 연관관계에 있는 테이블에서, 외래키로 지정된 컬럼 데이터가 부모의 기본키 외 다른 값을 가질 수 없게 하여 외래키 컬럼에 저장될 수 있는 데이터를 제어하게 된다.
```
CREATE TABLE Orders (
    OrderID int NOT NULL PRIMARY KEY,
    OrderNumber int NOT NULL,
    PersonID int FOREIGN KEY REFERENCES Persons(PersonID)
);
```
### CHECK
입력을 할 때, 해당 값이 조건에 부합하는지 확인하여, 합당하지 않을 경우 거부하는 제약조건이다.
```
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int CHECK (Age>=18)
);
```
## CREATE INDEX
테이블에 대한 인덱스를 정의하는 데 사용
```
CREATE INDEX index_name
ON table_name (column1, column2, ...);
```