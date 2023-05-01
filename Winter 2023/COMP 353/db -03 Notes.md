# The Relational Data Model 
- **Relational Database**: a set of relations 
- **Relation**: A two-dimensional table in which data is aranged 
- **Relation schema**: Relation name + a set of attribute name and types 
	- R = (A1, ... , A_n)
- **Relation instance**: The set of current tuples 
- **Database scehma:** A set of relation schemas D = {R1, .... RN}
- **Database Instance:** A collection of relation instances - one for each relation in the databse schema 
- **SQL**: Structured query language
## From E/R to Relational Model 
### Converting entity sets to relations 
- For each entity set E, create a corresponding relation with the same attributes as in E 
- The set of attributes included in coverting a Relationship to a table is: 
	- "Implicit": Key attributes fo the entity sets involved in the relationship R
	- "Explicit": Every attribute in R 
### Identifying Key of Relationship R
- If **R** is a **binary** relationship beween entity sets E1 and E2, then the multiplicity of this relationship determines the key of **R**
	- If R is *M-N*: the keys of E1 and E2 together are "part-of" the key of R 
	- If R is M-1 from E1 to E2, then the key of E1 is the key of R 
	- if R is 1-1, then either E1 OR E2 (but not both) is part of the key of R
### Converting Relationships to Tables 
- We should rename the attributes in the relations created when: 
	- An entity set is involved in a relationship more than once
	- The same attribute name appears in the keys of a different entity sets involved in the relationship (ID for exmaple)
	- This is to avoid ambiguity in the schema and to be more clear in the meanings
### Weak Entity Sets to Relations 
- The relation/table W for the weak entity set W must include all the attribtues of W *as well as the key attributes of the strong entity sets to which W is associated*
- Any relationship R to which the weak entity set W contributes, must include **all** the keys attributes of W (i.e. the key attributes of *every* entity set that contributes to Ws key)
- The weak relationship from W to tother entity sets that provide the key for W don't need ot be converted into a seperate table
	- Double diamonds connection a weak entity set need not become a seperate table 
- For example, we don't need the Unit-Of table
- ![[Screenshot 2023-02-24 at 1.05.09 PM.png]]
## Converting isa hierarchies to Relations 
#### Straight E/R style method
- an entity can be represented by entities that may belong to several entity sets, which are connected via *isa* hierarchies 
- The "connected" entites togerther represnt the object and also determine the objects properties (attributes and relationships)
- For each entity E: create a relation table e, and give it attribtues A whenever: 
	- A belongs to E
	- A is the key attribute of the parent(s) relation 
- **No crelation is created for the isa-relationship**
- U take the key attributes from *all the parents*
#### Object Oriented method 
- Not in the slides, look at the textbook 
#### Nulls method 
- If we are allowed to use the NULL as a value in the tuples, we can handle a hieracrgy of entity sets (classes) with a *single relation*
	- This relation has all the attribtues belonging to any entity set (class) of the hiearchy
	- An entity/object is represented bya single tuple that has a NULL in each attribtue that is not defined for that enitity/object
- The Null approach supports effecient query processing but is inefficvient in space utlilization, why? 
	- Answering Queries: the nulls approach allows us to find, *in a single relation R* every tuple/object from any set involed int ehhiearchy
	- Allows us to find all the information about a single entitiy in a single tuple
	-  downside: Space utlilization: it to too costly for having reapeated/reduannt info 
	- Note: Nulls are not alled in the relational mode theory, but practically supported by comemrcial DBMS