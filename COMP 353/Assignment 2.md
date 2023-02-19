Student: Jaeden Rotondo 
Student ID: 40160803 

---
# Question 1
### Question 1 A 
- Post a photo here
- This E/R diagram assumes that supervisors and managers are different entities
### Question 1 B
- Relation model: note that uderline text is written as **bolded**
Employee( **EID**, Ename, SID, DoB, DID)
Department(**DID**, Location)
Supervisor(**SID**, **EID**)
Manager(**MID**, **EID**)
WorksIn(EID, DID)
Manages(MID, DID)
Supervises(SID, EID)
### Question 1 C
1.  For each relation schema, in (b), identify the key attribute(s), and alternate keys, if any. State any reasonable assumptions made to justify your answer in (c).
The key attributes are written in pink above. The alternate keys, which are keys that can uniquely identify touples but are not primary keys in this E/R diagram would be: 
1. Employee table: SID is an alternate key because it is unique to the individual. Also, Ename with the addition of DoB could be considered an alternate key, as the chances of two people being born on the same day with the same name is very very low. This is also dependent on the size of the data. 

# Question 2
## Question 2 A 
Converting the E/R diagram to the relational model using the E/R approach would yield the following: 
H(**g**, h)
S(f, g)
G(e)
E(a, b)
R(**c**, f)
F(**c**, d)
## Question 2B
Converting the E/R diagram to the relational model using the OO approach would yield the follwing: 
H(**g**, h)
S(f, g)
G(e)
E(e, a, b)
R(**c**, f)
F(**c**, d)

# Question 3
## Question 3 A 

## Question 3 B 
People(**ID**, Name)
FatherOf(**ID**, ChildID)]
MotherOf(**ID**, ChildID)
- Note that I have removed FatherID and MotherID because they are repeated with the key of the People entity

# Question 4
## Question 4 A
Modify your design of the database People in the previous question to include additional information about “types of people such as Females, Males, and being parents, etc. Use subclasses of people to present the “types” of people.




