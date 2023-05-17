## Agents and Environments
- An agent perceives its environment through sensors and acting through actuators
	- Includes: humans, robots, softbots, thermostats, etc
- **Agent Function**
	- f: P* -> A
	- Maps from precept histories to actions 
	- The *agent programs* runs on the physical *architecture* to produce f
- Sequence precepts include some sort of past memory which can decide the future 
- Vacuum can be programmed as a "**Reflexive Agent**"
	- Reflexive agents are so simple they don't need software 
	- E.g. `status = Dirty then return Right`
---
## Rationality
- A rational agent does the right thing, but what is the right thing? 
	- Determine its consequences 
	- The notion of desireablilty is captured by a **performance measure**
- **Performance Mesaure**: "one point per square cleaned in time T by the Vacuum"
	- Fixed perfomance mesaure evaluates the environment sequence
	- One point per clean sqaure per time step, minus one per move and occasuionaly clean if needed
> A rational adent chooses whichever action maximizes the expected value of the performce mesaure given the percept sequence to date

- Rationality at any given time depends on 4 things 
	1. The *performance mesaure* that defines the criterion of success
	2. the *agents prior knowledge* of the environment
	3. The *actions* the agent can perform 
	4. the angents *percept sequence* to date 
---
## PEAS
- Performance meansure, Environment, Actuators, Sensors
- To design a rational agent we must specify the *task environment*
- ![[Screenshot 2023-05-15 at 12.46.37 PM.png]]
---
## Environment types
- Environments fall into 3 categories 
	1. Fully observable 
		- When an agents sensors give it access to the complete state of the environment
	2. Partially observable
		- Part of the state is missing from the sensor data (noisy, innaccurate etc)
	3. unobservable 
		- When the agent can only sense the current state only 
- Single-agent vs multi-agent environments 
	- Chess is a multi-agent environment (also called competitive)
- Automated Taxi is multiagent: many agents on the road
	- **partially cooperative**: avoid collision 
	- **partially competitive**: competing for the same parking spot
- **Deterministic vs nondeterministic**
	- If the next states of the environment i scompletely determined the following , we call it **deterministic**
		1. the current state
		2. The action executed by the agents
	- otherwise it is non-deterministic 
- **Deterministism vs Stochasticism**
	- The word stochastic is used by some as a synonum for nondeterminism but we make a destiniction between the two words
	- We say that a model is stochastic if it explicityl deals with probabilities 
- **Episodic vs sequential**
	- Episodic environments: agents experience is diveded into atomic episodes
		- the next episode does not depend on the previous episodes 
		- E.x. an agent must spot defects on the assembly line
	- Sequential environments: the current decision could affect all future decisions
		- E.x. Chess, automated taxi. 
- **Static vs Dynamic**
	- Dynamic environemnts can change while the agent is thinking of the best action to mak e
	- Static environments do not change while the agent needs to make a move
	- Semi-dynamic: If the environment itself doesnt change but the agents perfomance score does, then we say the environment is *semidynamic*
		- When the goal changes during the process 
- **Discrete vs Continuos**
	- Continuos: When you need to make decisions on continuos variables that are variably changing over time
	- Discrete problems are like chess
- **Known vs Unknown**
	- Known: the environment can be known when the rules are known. so chess is known
	- Unknown: When you play a videogame before you know what the buttons do 
- ![[Screenshot 2023-05-15 at 1.26.36 PM.png]]
---
## Agent Types
- There are 4 basic types of agents (in increasing generality)
	1. Simple reflex models 
	2. Model based reflex agents (with states)
	3. Goal based agents
	4. Utility based agents 

### Simple Reflex Model 
![[Screenshot 2023-05-17 at 11.55.44 AM.png]]

### Reflex Agents with States
- The most effective way to handle *partial observability* is for the agent to keep track of history 
- The agent should maintain some sort of internal state
- ![[Screenshot 2023-05-17 at 12.06.12 PM.png]]
### Goal-based Agents
![[Screenshot 2023-05-17 at 12.11.56 PM.png]]
### Utility-based Agents 
- ![[Screenshot 2023-05-17 at 12.14.09 PM.png]]
### Learning Agents
- ![[Screenshot 2023-05-17 at 12.14.32 PM.png]]

## Summary 
- Agents interact with the enviroenment through sensors and actuators
- The agent funcitons determines what the agent does in all circumstances
- The **performance measure** evaluates the environment sequence
- a **perfectly rational** agent maximizes expected performace 
- **Agent programs** implement (some) agent functions
- **PEAS** descriptions define task environments
---