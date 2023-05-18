##### From chapter 19.1, 19.2, 19.3
---
### Why do we need the machines to learn 
1. Programmers cannot anticipate all possible situations
2. Sometimes designers don't know the best solution 
---
## Forms of learning 
- Condition action rule 
	- learning by observing 
- Supervised learning
	- 100 pictures of buses, hopefully it will learn what a bus is
	- Agent observes input output pairs
	- Ask the agent what is the input output function 
- Unsupervised Learning
	- agent learns pattens in the input without any explicit feedback 
	- Mainly for clustering 
- Reinforcement Learning 
	- agent learns from a series of reinforcements: rewards and punishments
---
## Supervised Learning
- Lets say we have an unknown function f 
- We can create a function called h, which is drawn from the hypothesis space (model class) called H 
- **Consistent Hypothesis**: an *h* such that each x in the training set has h(x) = y
	- Look for a **best-fit** function for which each h(x) is "close enough to" y
- *h* generealizes whell if it accurately predicts the output 
- Example: Hypothesis space can be 
	- the set of polynomials of degree 3 
	- the set of javascript functions
	- the subset of a set of functions 
- We call the true output u, the ground truth, the true arenswer are are asking our model to predict 
- **overfitting**: can be a problem with high degree polynomials 
- **Underfitting**: fails to find a pattern in the data
- **Bias variance tradeoff**: a choice between more complex, low bias hypothesis that fit the training data well and simpler, low-variance hypotheses that may generalize better
- There shouldnt be a huge variance between datasets when fitting (signifies overfitting)

### Probability
- ![[Screenshot 2023-05-17 at 1.59.20 PM.png]]
- 
---