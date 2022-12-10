
### List Extensions 
- We can "re-purpose" the basic list to obtain more specialized functionality 
#### Stacks
- a "last in first out" (LIFO) structure
	- The append() and pop() methods can be used to add and remoce elements from the end of the queue
```python
list1 = [“foo”, “boo”]
list1.append(“bat”)
list1.append(“bar”)
top = list1.pop() # do not specify index
>>> top

>>> ‘bar’
```
---
#### Queues 
- First in first out (FIFO) 
```python
l2 = [“foo”, “boo”]
l2.append(“bat”)
l2.append(“bar”)
first = l2.pop(0) # need index
>>> first

>>> ‘foo’
```
---
#### Deque 
- Popping the first element in the array is very expensive in large lists because EVERYTHING must be shifted by one.
- implemented using a doubly linked list 
- In practice, you will want to use a data structure provided for just this purpose.
```python
from collections import deque # more on this later
q1 = deque([“foo”, “boo”])
q1.append(“bat”)
q1.append(“bar”)

first = q1.popleft()
>>> first
>>> ‘bar’
```
- Any kind of random access to the middle of the deque would be very slow since the whole list must be traversed
	- This includes any kind of slice operations
	- So use lists unless you have a good reason not to do this.
---
#### Dictionaries 
-    One of the more useful python data structures is the dictionary.
	- this is a set of (key/value) pairs – The key is a unique “lookup” element
	- Each key is associated with some value
	- Keys must be unique
	- Keys can be any immutable type • e.g., strings or ints  
	    • But NOT lists
- There is no fixed order for the key/value pairs
``` python
location = {“joe” : “Montreal”, “Sue” : “Toronto”} # init
>>> location[“Sue”]
>>> ‘Toronto’
location[“Mo”] = “Tokyo”

del location[“joe”] # standard Python del statement
>>> location
>>> {“Sue” : “Toronto”, “Mo” : “Tokyo”}
```
Dictionaries provide a number of additional methods.
- A few of the more useful include:
	- dict.items(): returns a list of key/value pairs
	- dict.keys(): returns a list of the keys
	- dict.values(): returns a list of the values
	- dict.clear(): removes all items
	- dict.get(key): returns value if it exists  
	- `del dict[key]`: removes the key, if it exists (raises KeyError if key not found)
	- `key [not] in dict`: check for existence, returns True or False
	- `len(dict)`: returns the number of items in the dictionary.
		- Instead, the value in the key/value pair simply replaces the current value.

• Finally, note that adding a key that already exists in not an error
• If key doesn’t exist, nothing is returned but there is no error raised
• Note that `dict[“key”]` would raise a KeyError exception if the key does not exist
- Dictionaries are implemented using Hash Tables, so the avergae cost of lookup is O(1)
---
#### Tuples
- Tuples are another example of a sequence datatype in Python 
	- Strings and lists are also *sequences*
- Tuples can be nested and, for example, can contain other tuples or lists.
-   When displayed, tuples are listed with ( ) parenthesis, rather than the [ ] of lists.
-   Empty tuples are constructed with empty parenthesis
	- nothing = ( )  
- Tuples of one element are (oddly) constructed:
	- using a trailing comma – one = “boo”,

- Tuple construction is quire easy and simply consists of comma delimitted elements
- In practise, tuples are used for heterogeneous data
- Lists are often used for homogeneous dats
	- A little like a java vector
- *Sequence unpacking*: If we have a touple that represents a customer with a name age and address, we can extract all 3 elements at once with a single operating into seperate variables as so: 
``` python
t1 = “Joe”, 43, “Montreal” # a tuple
a, b, c = t1
>>>b
43
m, n = t1
ValueError: too many values to unpack
```
---
#### Sets 
- A set is an unordered collection of elements, it is used to describe the mathematical definition of the set 
- Duplicates are explicilty not allowed
- Operations on sets typically consist of 
	- Testing for membership in the set 
	- Elimination of duplicated in a list
	- Basic set operations
		- Union
		- Intersection 
		- Difference 

## Statements 
- While statements
	- 
### For Statements
---
### If Statements 

## Functions 
- Funcitons are introduced with the `def` keyword
- paramters require no type
- Return types are not explictly specified
- We use `:` and whitespace to define a function block 
- Functions return `NONE` by default 
- Python arguments are "pass-by-value"
- Functions can be assigned to variables
	- if we have a function called boo, we can say boo2= boo would make an alies for the same function 

