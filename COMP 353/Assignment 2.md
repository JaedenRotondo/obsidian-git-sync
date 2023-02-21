Student: Jaeden Rotondo 
Student ID: 40160803 

---
# Question 1
### Question 1 A 
![[AS2Q1A.drawio.png]]
- This E/R diagram assumes that supervisors and managers are different entities and uses subclasses
### Question 1 B
- Relation model: note that uderline text is written as **bolded**
Employee( **EID**, Ename, SIN, DoB, DID)
Department(**DID**, Location)
Supervisor(**SID**, **EID**, Ename, SIN, DoB, DID)
Manager(**MID**,**EID**, Ename, SIN, DoB, DID)
WorksIn(EID, DID)
Manages(MID, DID)
Supervises(SID, EID)
### Question 1 C
For each relation schema, in (b), identify the key attribute(s), and alternate keys, if any. State any reasonable assumptions made to justify your answer in (c).

The key attributes are written in pink above. The alternate keys, which are keys that can uniquely identify touples but are not primary keys in this E/R diagram would be: 
1. Employee table: SIN is an alternate key because it is unique to the individual. Also, Ename with the addition of DoB could be considered an alternate key, as the chances of two people being born on the same day with the same name is very very low. This is also dependent on the size of the data. 

# Question 2
## Question 2 A 
Converting the E/R diagram to the relational model using the E/R approach would yield the following: 
H(**g**, h)
S(e, f, g)
G(**e**, **g**) (not required)
E(**a, b,** **g**, **c**, **e**) 
R(**c, a, b, g**) (not required)
F(**c**, d)
## Question 2B
Converting the E/R diagram to the relational model using the OO approach would yield the follwing: 
H(**g**, h)
S(e, f, g)
G(**e**, **g**) (not required)
E(**a, b,** **g**, **c**, **e**) 
R(**c, a, b, g**) (not required)
F(**c**, d)

## Question 2C
Converting the E/R diagram to the relational model using the null approach would yield the follwing: 
H(**g**, h)
S(e, f, g)
E(**a, b,** **g**, **c**, **e**) 
R(**c, a, b, g**) (not required)
F(**c**, d)

# Question 3
## Question 3 A 
![[AS2Q3A.drawio-2.png]]
## Question 3 B 
```sql
CREATE TABLE People
ID CHAR(10) 
Name VARCHAR(25) 
PRIMARY KEY(ID);

CREATE TABLE MotherOf
ChildID CHAR(10) NOT NULL
MotherID CHAR(10) NOT NULL
FOREIGN KEY (MotherID) REFERENCES People(ID)
FOREIGN KEY (ChildID) REFERENCES People(ID);

CREATE TABLE FatherOf
ChildID CHAR(10) NOT NULL
FatherID CHAR(10) NOT NULL
FOREIGN KEY (FatherID) REFERENCES People(ID)
FOREIGN KEY (ChildID) REFERENCES People(ID);
```

# Question 4
Modify your design of the database People in the previous question to include additional information about “types of people such as Females, Males, and being parents, etc. Use subclasses of people to present the “types” of people.

![[Screenshot 2023-02-20 at 6.48.03 PM.png]]

# Question 5
[20 Points] An E/R diagram includes a 3-way relationship R that connects and relates the entity sets E1, E2, and E3. Consider the following separate cases we may have about the type of connections between R and each of these entity sets.

(a) The connection from R to E1 is a sharp arrow; the other two are simple lines. 
![[Screenshot 2023-02-20 at 4.39.18 PM.png]]

- |R| = {0, e2 x e3}


(b) The connections from R to both E1 and E2 are sharp arrows.
![[Screenshot 2023-02-20 at 4.40.07 PM.png]]
- |R| = {0, e3}
(c) The connection from R to each one of the 3 entity sets is a sharp arrow.
![[Screenshot 2023-02-20 at 4.40.50 PM.png]]
- |R| = {MIN(e1, e2, e,3)}
(d) The connection from R to E1 is a sharp arrow and from R to E2 is a round arrow.
![[Screenshot 2023-02-20 at 4.41.04 PM.png]]
- |R| = {}