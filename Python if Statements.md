---
tags:
  - Studies
  - Programming
  - Python
  - COM513
cssclasses:
  - programming
---

## How is a Python `if` statement formed?

Below is an example of a standard `if` statement, an `elif` statement, and an `else` statement.

```python
# An if else statement
if nativeVLAN == dataVLAN: 
	print("The native VLAN and the data VLAN are the same.") 

else: 
	print("This native VLAN and the data VLAN are different.")

# An if, elif, else statement
aclNum = int(input("What is the IPv4 ACL number? ")) 

if aclNum >= 1 and aclNum <= 99: 
	print("This is a standard IPv4 ACL.") 

elif aclNum >=100 and aclNum <= 199: 
	print("This is a extended IPv4 ACL.") 

else: 
	print("This is not a standard or extended IPv4 ACL.")
```

In Python, `elif` statements are a continuation of an `if` statement for when multiple comparisons must be made. `else` statements account for any other cases which are not covered by the `if`, or `elif` statements (a catchall).