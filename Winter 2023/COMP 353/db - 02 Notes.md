- A **Data Model**: is a colleciton of concepts for describing
	1. data and relationships among data
	2. data semantics and constraints
![[Screenshot 2023-02-23 at 11.45.41 AM.png]]

### Multiplicity of Binary Relationships 
- Many to one:
	- -   If a relationship is **many-one** from entity set **Course** to **Department_,_** we place an **arrow** **entering** **Department**
- one to one: 
	-  The arrow indicates that each entity in the entity set **Course** is related to **at most one** entity in the entity set **Department**
- Many to many: 
	- If a relaitonship is many to many, we don't place arrows on either side. 
### Attributes on relationships
- Sometimes it is most appropriate to assiciate attributs with a relationship rather than with the entity sets involved. For example the EnrolledIn Relationship between students and courses is the best place to add the *grade* attribute
- We can also move the attribute to its own entity set that is connected in the relationship. For example, a Grades entity with a letterGrade attribute
### Roles in Relationships
- Note that it is possible to have a entity which is in a relationship more than once. Each like to the entity set represnts a different **role** that the entity plays in the relationship 
### Converting n-ary relationship to binary 
- An n-ary relationship R can be converted into a collection of M-1 **binary** relationship without losing the information represented by R 
	- Algorithm 
		- Introduce a **new** entity set E, called a **collecting entity set**, whose entities might be thought of as tuples in R 
		- Introduce M-1 relationsips from E to each of the entity sets involved in **R**
		- If an entity set E plays more than one role, then E is the target of one relationship for each role 
## Inheritance in E/R 
- expressed through an ISA relationship 
- We consider and entity as having "components" which belong to several entity sets that are "part of" a single isa hierarchy. 

## Classification of Constraints
- A Key **K** is a set of attributes that uniquely identifies an object withiin its class or an entity within its set R 
	- That is, no two entities may have all the same key values (duplicate)
### Types of Constraints
#### Single-value constraints
- are requirements that the value in a certain context/role be unique (IDs? )
- In our E/R model introduced so far, there is no way to 
	- Express that a value of A *must* be present
	- Express that a value of A *may* be present
- If the choice is not explicit we use the following *defaults*:
	- The value of A must exist if its a primary key 
	- The value of A is optional otherwise
#### Referential integrity constraints
- are requirements that a value referred to by some object/entity must actually exist in the databe
	- that means no dangling pointers
- Referential integrity = single-value + Existance
- ![[Screenshot 2023-02-24 at 11.41.06 AM.png]]
#### Domain constraints
- require that the value of an attribute must be drawn from a specific set of values (called attribute domain), or lies in a specific range
- E/R diagrams do not support imposing domain constraints
- ODL allows using types to limit values but cannot restrict "range"
#### Relationship degree constraints (mulitplicity)
- Refers to the restriction of the number of entites in the entity set incolved in a relationship 
	- For example, we can say "A student cannot be enrolled in more than 5 courses" by addint a "<= 5" on the line between EnrolledIn and Courses as follows: 
	- ![[Screenshot 2023-02-24 at 11.44.36 AM.png]]
#### General constraints
- arbitrary assertions that must hold on the DB
## Keys 
- A **Superkey** is a set of attributes whose values uniquely identify an entity (object). int he entity set (class). This set may not be minimal 
	- A **minimal superkey** is called a **Candidate key**
- Note that an entity set may have more than one **candidate key**. one of them is picked to be the primary key
	- Others are considered *aleternate keys*
### Selecting Primary key
- When there is more than one candidate: 
	- Total size of attributes in forming the key 
	- Number of attributes forming the key 
	- Convenience/ natural choice
	- A combination of the above
### Weak Entity/ Relationship sets
- A **Strong** entity set has a key 
- A **Weak** entity set does not have sufficient attributes to form a key.
	- It participates in a M-1 relationship with a strong entity set
- **Discriminator** of a weak entity set is the set of attributes that distinguised among the entites corresponding to a strong entity
- Key of a weak entity set = Key of Strong entity set + discriminator ![[Screenshot 2023-02-24 at 11.51.24 AM.png]]
	- C 