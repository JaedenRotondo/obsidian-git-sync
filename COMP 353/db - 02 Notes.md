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
#### Referential integrity constraints
- are requirements that a value referred to by some object/entity must actually exist in the databe
	- that means no dangling pointers
#### Domain constraints
- require that the value of an attribute must be drawn from a specific set of values (called attribute domain), or lies in a specific range
#### General constraints
- arbitrary assertions that must hold on the DB
### Keys 
- A **Superkey** is a set of attributes whose values uniquely identify an entity (object). int he entity set (class). This set may not be minimal 
	- A **minimal superkey** is called a **Candidate key**
- Note that an entity set may have more than one **candidate key**. one of them is picked to be the primary key
	- Others are considered *aleternate keys*
- 