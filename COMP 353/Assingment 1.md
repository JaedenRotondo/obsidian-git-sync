Student: Jaeden Rotondo 
Student ID: 40160803 

---
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
- Gives the following console output from Main.java: 
```console
Here is a list of students who took COMP 353 with a grade of B+ (3.3) or higher:
----------------------------------------------
Name: John Smith, Student ID:  1
Name: Jane Doe, Student ID:  2
Name: Bob Johnson, Student ID:  3
Name: Michael Davis, Student ID:  5
----------------------------------------------
```

### Question 1 B 
- You can find my `main.sql` file zipped in the assignment. 
- It gives  the following output
```console
1|John Smith
2|Jane Doe
3|Bob Johnson
5|Michael Davis
```

#### Explain why DB system is better than file processing system 
- There are many pros to using a DB system when working with tables and queries. The following are a list of bullet points which I believe describe the benefits of a DB system for this project and in general 
- The main benefit of a Database management system is the limiting of *data redundancy* (ACID properties). A database management system insures 
	- Atomicity
	- Consistency 
	- Isolation
	- Durability
- Since there is no abstract view of the data, it is a lot harder to make queries. For example the query in Java requiered me to make a nested for loop that cannot be reused for other queries
- Another benefit of using a database management system for this problem was that its complexity was lower. instead of having to use 3 buffereaders and a nested loop O(n^2), in the SQL implementation i used the very quick `JOIN` operation 
- There are of course some benefits of using a file processing system. If there is a single query you are looking for and do not require a database, it could be implemented easier. 
---
# Question 2

#### (c)
A suitable schema for relation Laptop.
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
#### (d)  
A suitable schema for relation Printer.
```SQL 
CREATE TABLE Printer(
model VARCHAR(255),
color BIT,
type VARCHAR(255),
price FLOAT,
PRIMARY KEY (model)
);
```
#### (e)
A modification to your Printer schema from (d) to delete the attribute color.
```SQL
ALTER TABLE Printer  
DROP COLUMN color;
```
#### (f)
A modification to your Laptop schema from (c) to add the attribute od (for optical-disk type, e.g., cd or dvd). Use “none” as the default value if the laptop does not have an optical disk.**
```SQL
ALTER TABLE Laptop  
ADD od VARCHAR(255) DEFAULT 'none';
```
---
# Question 3
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
---
# Question 4 

#### (a) 
Using two INSERT statements, store in the database the fact that the PC model 1100 is made by manufaturer C, has speed 3.2, RAM 1024, hard disk 180, and sells for $2499.

```SQL 
INSERT INTO PC(model, speed, ram, hd, price)
VALUES ('1100', 3.2, 1024, 180, 2499.00);
INSERT INTO  Product(maker, model, type)
VALUES ('C', '1100', 'PC');
```
#### (c) 
Delete all PC’s with less than 100 GB of hard disk.
```SQL 
DELETE FROM PC WHERE hd <100; 
```
#### (e)  
Manufacturer A buys manufacturer B. Change all products made by B so they are now made by A.
```SQL 
UPDATE Product 
SET maker = 'A'
WHERE maker = 'B';
```
#### (f)
For each PC, double the amount of RAM and add 60 GB to the amount of hard disk. Note that several attributes can be changed by a single UPDATE statement.
```SQL 
UPDATE PC 
SET hd = hd +60 AND ram = 2*ram;
```