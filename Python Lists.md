---
tags:
  - Studies
  - Programming
  - Python
  - COM513
cssclasses:
  - programming
---

A Python list is an ordered list of items. It can be created using square brackets: `[]`.

An example of a list can be seen here:
`hostnames=["R1", "R2", "R3", "R4", "S1", "S2"]`

To call an individual item in the list you can use it's index in the list. List indexes begin from zero so the first item in the list would be 0. To call hostname R3 from the list above, I would use the code:
`hostnames[0]`

List indexes wrap around, so to call the last item in the list you could use it's normal index value, or you could use `[-1]`.

To delete an item in a list, you can use `del()`. For example: `del(hostnames[2])`.