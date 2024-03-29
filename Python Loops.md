---
tags:
  - Studies
  - Programming
  - Python
  - COM513
cssclasses:
  - programming
---

A Python loop repeats a block of code until a condition is met, automating tasks and iterating over sequences. There are three types of loop.

## For Loops

A for loop iterates through items in a list, dictionary, or other sequenced data type. The variable name “item” in the example below is arbitrary and can be anything the programmer chooses.

```python
devices=["R1","R2","R3","S1","S2"]

for item in devices: 
	print(item)
```

This code will return the following:

```
R1
R2
R3
S1
S2
```

#### Embedded if Statements in a For Loop

```python
for item in devices: 
	if "R" in item: 
		print(item)
```

Which will return the following:

```
R1
R2
R3
```

#### Creating a List with a For Loop

For loops can be used to iterate through the devices list to create a list as in the example below.

```python
# Create the empty list
switches=[]

# Create the loop
for item in devices: 
	if "S" in item: 
		switches.append(item)
```

The list `switches` will now contain `S1` and `S2` and will look like this: `['S1', 'S2']`. See [[Python Lists]] for more information on Lists.

## While Loops

A Python while loop executes a block of code repeatedly as long as a certain condition remains true.


