 Exclude: Section 6, Section 7, Section 8, Section 9, Section 10, Section 11.3, Section 11.4, Section 12.3, Section 12.4, Section 13, Section 15, Section 18, Section 19, Section 20, Section 21.4, Section 21.5, Section 21.6, Section 22, Section 23, Section 24, Section 25, Section 26, Section 27, Appendix A, Appendix B, Appendix C.

##  3 Usage Modelling 
- Use case modelling is a type of usage modelling
## Scoping
- Use cases can help define the scope of a sysem
- To a certain extent, the number of actors and the number of use cases, and the number of relationships between them, can give an idea of the size and complexity of the system.
 
 > Definition [Use Case Model]. A use case model for a software system is the set of all actors, and the set of all use cases, and the relevant relationships among them.
 ![[Screenshot 2023-03-05 at 1.51.00 PM.png]]

## 11.2 Use case modelling with the UML use case diagram 
- The UML Use Case Diagram can provide a high-level graphical representation of the actors, use cases, and their interactions. It also provides structural relationships between use cases `
`(<<include>>, <<extend>>, and generalize), and structural relationships between actors (generalize).
`
- ![[Screenshot 2023-03-05 at 1.53.20 PM.png]]
#### Limitations
- There can be unintended consequences (or side-effects) of such abstraction. For example, a UML Use Case Diagram usually does not provide the definitions of the actors beyond their names, does not provide the reasoning for a certain relationship between an actor and a use case, does not show the order of execution of use cases
- Use Case Diagram usually does not provide any details on trigger, pre-conditions, or post-conditions of a use case.
- UML notes allow meta-information that can bypass a lot of these problems 

## 12 quality of Use Case models 
#### Semiotic Quality 
- syntactical: Let there be a UML Use Case Diagram which shows an association relationship between an actor and a use case as dotted line (such as +········+).
- semantical: For example, consider the ATM System. Then, Display Message use case [Nair, 2009] is expressed from the perspective of the system, not the actor. This is a violation of the use case domain, and therefore of semantical quality.
- pragmatical: For example, readability and understandability are pragmatical quality concerns for a use case model percipient (say, use case model reader), and maintainability is a pragmatical quality concern for a use case model engineer.
- Social: For example, a disagreement (say, lack of consensus on some issue) among the stakeholders of the use case model is a violation of social quality of that use case model
## 16 Actors
> Definition [Actor]. A role played by an entity external to the system, as perceived from the system’s point of view, when it uses the system.

#### Actors posess certain qualities: 
- Location 
- Cardinality 
- Type: An actor can be anyone (a human/person) or anything (a machine/program). In other words, an actor can be animate or inanimate
#### Actors fall into certain categories 
- Primary/Secondary
- Abstract/Concrete
- Direct/Indirect

## 17 Use cases
- Definition [Use Case]. A sequence of actions performed by a system, which yields an observable result of value to an actor of the system.
#### Classifications 
- Problem/Solution  
- Abstract/Concrete 
	- Definition [Abstract Use Case]. A use case that does not have any instances. 
	- Definition [Concrete Use Case]. A use case that has one or more instances.
- Informative/Performative
- Definition [The Include Relationship]. Let UC1 and UC2 be two use cases. If, during execution, every instance of UC1 must include the behavior of UC2, then UC1 includes UC2 and there is an include relationship between UC1 and UC2.![[Screenshot 2023-03-05 at 2.31.09 PM.png]]