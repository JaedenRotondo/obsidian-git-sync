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


1.  [20 Points] Exercise 2.3.1, parts: c, d, e, f on page 36 in the textbook. Consider the following database schema for a Computer Equipment store (CED):
    
             Product(maker, model, type)
             PC(model, speed, ram, hd, price)
             Laptop(model, speed, ram, hd, screen, price)
             Printer(model, color, type, price)
    
    The attributes of relation Product include: manufacturer, Model, and the equipment Type; the attributes of relation PC include Model, Speed, RAM, HD, and Price; For relation Laptop, the attributes include the following attributes: Model, Speed, RAM, HD, Screen, Price; and for relation P rinter, we have the attributes Model, Color, Type,
    

Price. Some explanations about this database. Relation Product records information about the model number and type of each equipment which could be pc, laptop, or printer. For convenience, assume that the model numbers of the equipments are unique across all manufacturers and product types. This assumption is not realistic, so explain how you would modify the database schema for a realistic situation?

For each model number of a PC, the P C relation records the processor speed (in GHz), the RAM size (in MB), the size of the hard disk (in GB), and the price (in dollar). The information stored as the Laptop relation is similar to PC except that it records the screen size (in inches) as well. The color attribute in printer could have the true/false value, which indicates whether it is a color printer or otherwise. A printer type could be laser or ink-jet. Write the following schema declarations or modifications in SQL.

(c) A suitable schema for relation Laptop.
```SQL 
CREATE TABLE Laptop(
maker VARCHAR(255), 
speed FLOAT, 
ram INT, 
hd INT, 
screen FLOAT, 
price FLOAT, 
PRIAMRY KEY (model)
);
```
4.  (d)  A suitable schema for relation Printer.
```SQL 
CREATE TABLE Printer(
model VARCHAR(255),
color BIT(1),
type VARCHAR(255),
price FLOAT,
PRIMARY KEY (model)
);
```
1.  (e)  A modification to your Printer schema from (d) to delete the attribute color.
```SQL
ALTER TABLE Printer  
DROP COLUMN color;
```
6.  (f)  A modification to your Laptop schema from (c) to add the attribute od (for optical-disk type, e.g., cd or dvd). Use “none” as the default value if the laptop does not have an optical disk.**
```SQL
ALTER TABLE Laptop  
ADD od VARCHAR(255) DEFAULT 'none';
```

Who were the male stars in Titanic?
```SQL 
SELECT name
FROM StarsIn, MovieStar
WHERE Movietitle = "titanic" AND gender = "male" AND Starname = name;

```
Which stars appeared in movies produced by MGM in 1995?
```SQL 
SELECT startsName 
FROM StartsIn, Movies
WHERE studioName = "MGM" AND title = movieTitle AND Movies.year = 1995;

Movies(title, year, length, genre, studioName, producerC#)
StartsIn(movieTitle, movieYear, starName)
MovieStar(name, address, gender, birthdate)
MovieExec(name, address, cert#, netWorth)
Studio(name, address, presC#)
```
Who is the president of the studio MGM?  
```SQL 
SELECT MovieExec.name
FROM Studio, MovieExec
WHERE Studio.name = "MGM" AND presC# = cert#
```

Which movies are longer than Gone With the Wind?
```SQL
SELECT ref2.title 
FROM Movies ref1, Movies ref2 
WHERE ref1.title = "Gone With the Wind" AND ref2.length > ref1.length 
```

4. [20 Points] Exercise 6.5.1, parts: a, c, e, f on page 295 in the textbook, with details as follow. Consider the schema of the CED database introduced above in question 2. Using SQL, express the following modifications on the data.

(a) Using two INSERT statements, store in the database the fact that the PC model 1100 is made by manufaturer C, has speed 3.2, RAM 1024, hard disk 180, and sells for $2499.

```SQL 
INSERT INTO PC(model, speed, ram, hd, price)
VALUES ('1100', 3.2, 1024, 180, 2499.00);
INSERT INTO  Product(maker, model, type)
VALUES ('C', '1100', 'PC');
```


(c) Delete all PC’s with less than 100 GB of hard disk.

5.  (e)  Manufacturer A buys manufacturer B. Change all products made by B so they are now made by A.
    
6.  (f)  For each PC, double the amount of RAM and add 60 GB to the amount of hard disk. Note that several attributes can be changed by a single UPDATE statement.
