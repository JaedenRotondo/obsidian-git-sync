Student: Jaeden Rotondo 
Student ID: 40160803 

# Question 1
### Question 1 A 
With the following Text files: 
- StudentDB.txt
```txt
1,John Smith,Computer Science,123 Main St  
2,Jane Doe,Engineering,456 Park Ave  
3,Bob Johnson,Business,789 Elm St  
4,Samantha Brown,Mathematics,321 Oak St  
5,Michael Davis,Computer Science,654 Pine St  
6,Emily Wilson,Engineering,987 Birch St
```
- CoursesDB.txt
```txt
COMP353,John Smith,4  
COMP353,Jane Doe,4  
COMP353,Bob Johnson,4  
COMP353,Samantha Brown,4  
COMP353,Michael Davis,4  
COMP335,Jane Doe,3  
COMP335,John Smith,3  
COMP354,John Smith,4  
COMP354,Jane Doe,3  
COMP249,Emily Wilson,3.5
```
- CoursesEnrolledDB.txt
```txt
1,COMP353,3.30  
1,COMP335,3.20  
1,COMP354,4.00  
2,COMP353,4.30  
2,COMP335,3.76  
2,COMP354,2.95  
3,COMP353,4.14  
4,COMP353,2.67  
5,COMP353,3.92  
6,COMP249,4.12
```
- With the following console output from Main.java: 
```console
Name: John Smith Student ID:  1
Name: Jane Doe Student ID:  2
Name: Bob Johnson Student ID:  3
Name: Michael Davis Student ID:  5
```

### Question 1 B 
```SQL 
CREATE TABLE students (
SID INT,
Name VARCHAR(255),
Program VARCHAR(255),
Address VARCHAR(255),
PRIMARY KEY (SID)
);

INSERT INTO students (SID, Name, Program, Address)
VALUES (1, 'John Smith', 'Computer Science', '123 Main St');
INSERT INTO students (SID, Name, Program, Address)
VALUES (2, 'Jane Doe', 'Engineering', '456 Park Ave');
INSERT INTO students (SID, Name, Program, Address)
VALUES (3, 'Bob Johnson', 'Business', '789 Elm St');
INSERT INTO students (SID, Name, Program, Address)
VALUES (4, 'Samantha Brown', 'Mathematics', '321 Oak St');
INSERT INTO students (SID, Name, Program, Address)
VALUES (5, 'Michael Davis', 'Computer Science', '654 Pine St');
INSERT INTO students (SID, Name, Program, Address)
VALUES (6, 'Emily Wilson', 'Engineering', '987 Birch St');

```
```SQL 
CREATE TABLE courses (
CID VARCHAR(255),
Name VARCHAR(255),
Credits FLOAT,
PRIMARY KEY (CID,Name)
);

INSERT INTO courses (CID, Name, Credits)
VALUES ('COMP353', 'John Smith', 4);
INSERT INTO courses (CID, Name, Credits)
VALUES ('COMP353', 'Jane Doe', 4);
INSERT INTO courses (CID, Name, Credits)
VALUES ('COMP353', 'Bob Johnson', 4);
INSERT INTO courses (CID, Name, Credits)
VALUES ('COMP353', 'Samantha Brown', 4);
INSERT INTO courses (CID, Name, Credits)
VALUES ('COMP353', 'Michael Davis', 4);
INSERT INTO courses (CID, Name, Credits)
VALUES ('COMP335', 'Jane Doe', 3);
INSERT INTO courses (CID, Name, Credits)
VALUES ('COMP335', 'John Smith', 3);
INSERT INTO courses (CID, Name, Credits)
VALUES ('COMP354', 'John Smith', 4);
INSERT INTO courses (CID, Name, Credits)
VALUES ('COMP354', 'Jane Doe', 3);
INSERT INTO courses (CID, Name, Credits)
VALUES ('COMP249', 'Emily Wilson', 3.5);

```
```SQL 
CREATE TABLE grades (
SID INT,
CID VARCHAR(255),
Grade FLOAT,
PRIMARY KEY (SID)
);

INSERT INTO grades (SID, CID, Grade)
VALUES (1, 'COMP353', 3.30);
INSERT INTO grades (SID, CID, Grade)
VALUES (1, 'COMP335', 3.20);
INSERT INTO grades (SID, CID, Grade)
VALUES (1, 'COMP354', 4.00);
INSERT INTO grades (SID, CID, Grade)
VALUES (2, 'COMP353', 4.30);
INSERT INTO grades (SID, CID, Grade)
VALUES (2, 'COMP335', 3.76);
INSERT INTO grades (SID, CID, Grade)
VALUES (2, 'COMP354', 2.95);
INSERT INTO grades (SID, CID, Grade)
VALUES (3, 'COMP353', 4.14);
INSERT INTO grades (SID, CID, Grade)
VALUES (4, 'COMP353', 2.67);
INSERT INTO grades (SID, CID, Grade)
VALUES (5, 'COMP353', 3.92);
INSERT INTO grades (SID, CID, Grade)
VALUES (6, 'COMP249', 4.12);

```

```SQL
SELECT students.SID, students.Name
FROM students
JOIN grades ON students.SID = grades.SID
WHERE grades.CID = 'COMP353' AND grades.Grade >= 3.3;
```
- Output 
```console
1|John Smith
2|Jane Doe
3|Bob Johnson
5|Michael Davis
```

#### Explain why DB system is better than file processing system 
- There are many pros to using a DB system when working with tables and queries. The following are a list of bullet points which I believe describe the benefits of a DB system for this project and in general 
- The main benefit of a Database management system is the limiting of *data redundancy* (ACID properties). A database management system insures 
	- Atomicity: 
	- Consistency: 
	- Isolation:
	- Durability:

```SQL 
CREATE TABLE Laptop(
model VARCHAR(255), 
speed FLOAT, 
ram INT, 
hd INT, 
screen FLOAT, 
price FLOAT, 
PRIAMRY KEY (model)
);
```
Who were the male stars in Titanic?
```SQL 
SELECT name
FROM StarsIn, MovieStar
WHERE Movietitle = "titanic" AND gender = "male" AND Starname = name;

```
Which stars appeared in movies produced by MGM in 1995?
```SQL 
SELECT StarsIn.starName 
FROM StarsIn, Movies
WHERE studioName = "MGM" AND title = movieTitle AND 

Movies(title, year, length, genre, studioName, producerC#)
StartsIn(movieTitle, movieYear, starName)
MovieStar(name, address, gender, birthdate)
MovieExec(name, address, cert#, netWorth)

Studio(name, address, presC#)
```