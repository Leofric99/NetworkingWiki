---
tags:
  - Studies
  - Programming
  - Python
  - COM513
cssclasses:
  - programming
---

Dictionaries in Python are a list of unordered key/value pairs. Each dictionary entry includes a key and a value. This key, can be used to call, or 'lookup' the value it is associated with.

## Creating a Dictionary

To create a dictionary, you can use curly brackets. Here is an example of a dictionary being created:
`IPAddresses = {"R1":"10.1.1.1","R2":"10.2.2.1","R3":"10.3.3 .1"}`

Here, the key is always surrounded by quotation, or speech, marks, then the colon indicates it's value (in this case they are strings, but they could be anything).

## Calling Dictionary Values

To call a value from a dictionary, you can call the dictionary, followed by the key as follows: `IPAddress["R2"]`. This will return `10.2.2.21`.

To simply find out if a key is present in a Dictionary, you can use the `in` function as shown here where key represents the dictionary key you're searching for, and dictionary is the dictionary you are referencing: `{key} in {dictionary}`.  This will return a Boolean value.

To call a single item in a list for a list stored within a dictionary, the syntax would be as follows where list-item is the number in the list:
`{dictionary}[{key}][{list-item}]`
