Jaeden Rotondo 
Student ID: 40160803
## 1. [25 Points] Consider the Computing equipment database schema defined as follows. (An example of an instance of this database is on pages 53 and 54 of the textbook). 
Product(maker, model, type) 
PC(model, speed, ram, hd, price) 
Laptop(model, speed, ram, hd, screen, price) 
Printer(model, color, type, price) 
Express the following queries in relational algebra (RA). 

#### (a) Find those manufacturers that sell laptops but not pc’s.
$π_{maker} \ σ(Product_{type = 'laptop'} - Product_{type = 'pc'})$
#### (b) Find those hard disk sizes that occur in at least two pc’s. 
$ρ_{pc1}(π_{maker, hd})$
$ρ_{pc2}(π_{maker, hd})$
Final answer: 

$π_{hd}(pc1 ⨝_{pc1.name != pc2.name, pc1.hd = pc2.hd} pc2)$
#### (c) Find those hard disk sizes that occur in exactly two pc’s. 
- subtract 3 or more pcs from 2 or more 
$ρ_{p1}(π_{maker1, hd1})$
$ρ_{pc2}(π_{maker2, hd2})$
$ρ_{pc3}(π_{maker3, hd3})$
$ρ_{MoreThan1}π_{hd}(pc1 ⨝_{maker1 != maker2, hd1 = hd2)} pc2$$ρ_{MoreThan2}π, _{hd}(AtLeast2 ⨝_{maker1 != maker2, maker1 != maker3, maker2 != maker3, hd1 = hd2, hd2 = hd3}pc3)$
Final answer: 
$π_{Exactly2}(MoreThan1 - MoreThan2)$

#### (d) Find those hard disk sizes that occur in all pc’s. 
$π_{hd} / π_{PC}$
#### (e) Find those manufacturers that sell exactly two pc models.
$ρ_{Product1}(π_{maker1, model1})$
$ρ_{Product2}(π_{maker2, model2})$
$ρ_{Product3}(π_{maker3, model3})$
$ρ_{AtLeast2}π_{maker1}(Product1 ⨝_{model1 != model2, maker1 = maker2)Product2}$$ρ_{AtLeast3}π_{maker1}(AtLeast2 ⨝_{model1 != model2, model1 != model3, model2 != model3, maker1 = maker2, maker2 = maker3}Product3)$
Final answer: 
$π_{Exactly2}(AtLeast2 - AtLeast3)$

---
## 2. [10 Points] Use SQL to express the following queries over the battleships database with the schema: 
Classes(class, type, country, numGuns, bore, displacement) 
Ships(name, class, launched) 
Battles(name, date) 
Outcomes(ship, battle, result) 
#### (a) Find the average number of guns of battleship classes. 
```SQL 
SELECT Class, AVG(numGuns)
FROM Classes
GROUP BY Class;
```
#### (b) Find the average number of guns of battleships. Note the difference between these two queries: do we weight a class by the number of ships of that class or not?
```SQL 
SELECT name, AVG(numGuns)
FROM Ships 
JOIN Classes ON Ships.class = Classes.class
GROUP BY name 
```
---
## 3. [10 Points] Consider the Computing Equipment database schema defined above in question 1. Express SQL transactions for each of the following changes on the data. 
#### (a) For each PC, double the amount of RAM and add 100 gigabytes to the amount of the hard disk. Note that several attributes of a table can be changed by one update statement. 
```SQL 
UPDATE PC 
SET ram = ram*2 , hd = hd + 100; 
```
#### (b) For each laptop made by manufacturer Orange, add 1 inch to its screen size and reduce the price by $100.
```SQL 
UPDATE Laptop 
SET screen = screen + 1, price = price -100
INNER JOIN Product ON PC.model = Product.model AND maker = 'Orange';
```
---
## 4. [10 Points] For the battleships database schema defined above in question 2, write the following as tuple-based CHECK constraints. 
#### (a) No ship can be in battle before it is launched. 
```SQL 
ALTER TABLE Battles
CHECK (date < Ships.launched WHERE Ships.name = Battles.name);
```
#### (b) If a class of ships has more than 9 guns, then their bore must be < 14 inches.
```SQL 
ALTER TABLE Classes
CHECK (bore > 14 WHERE numGuns > 9 );
```
---
## 5. [10 Points] Consider the following database schema: 
MovieStar (name, address, gender, birthdate) 
MovieExec (name, address, cert#, networth)

We want to find the name and address of all female movie stars who are also movie executives whose networth is over ten million dollars. Express this as a nested subquery in SQL. Using Intersect or Except operators is not acceptable.

```SQL 
SELECT name, adress
FROM MovieStar 
WHERE gender = female AND 
EXISTS(Select * FROM MovieExec WHERE MovieStar.name = MovieExec.name AND MovieStar.address = MovieExec.adress AND networth > 10000000);
```
---
## 6. [10 Points] Let R(a, b, c), S(a, b, c), and T(a, b, c) be three relations. Write one or more Datalog rules that define the result of each of the following relational algebra expressions. 
#### a. (R ∪ S) − T. 
 U <- S(a,b,c) 
 U <- R(a,b,c)
 A <- U AND NOT T(a,b,c)
#### b. (R − S) ∩ (R − T). 
L(a,b,c) <- R(a,b,c) AND NOT S(a,b,c) 
G(a,b,c) <- R(a,b,c) AND NOT T(a,b,c) 
A(a,b,c) <- L(a,b,c) AND G(a,b,c)
#### c. Πa,b(R).
P(a,b) <- R(a,b,c)

---
## 7. [10 Points] Convert each of the following Datalog rules into equivalent RA expressions. 
#### a. P1(x, y) ← Q(x, z) AND R(z, y). 
- $P1 = Q(a,b) ⨝_{b=c} R(c,d)$ 
#### b. P2(x, y) ← Q(x, z) AND Q(z, y).  
- P2(x,y) = Q(a,a) 
#### c. P3(x, y) ← Q(x, z) AND R(z, y) AND x < y.
- $P1 = Q(a,b) ⨝_{b=c, a < d} R(c,d)$ 
---