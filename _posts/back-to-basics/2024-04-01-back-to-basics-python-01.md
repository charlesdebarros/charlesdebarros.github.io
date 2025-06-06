---

title: "Python 01"
subheadline: "Back to Basics"
date: 2024-04-09 17:44
header: 
    background-color: "#003f72"
    caption: This is a caption for the header image with link
    caption_url: https://unsplash.com/
category: ['Back to Basics', 'Python']
tags: ['back to basics', 'python']
image: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/ZIPFteu-R8k/upload/4f2919851e7b480fe73f756cc9fa618b.jpeg?w=1600&h=840&fit=crop&crop=entropy&auto=compress,format&format=webp
---

## Intro

It's March 2024 and I have joined a Level 4 Data Analytics Bootcamp! Hurray! Technically lessons will only start at the beginning of April but I am already very excited about it and thinking of things.

To celebrate my new adventure and start having my brain cells back working, I am writing a series of __Back to Basics__ articles exploring Data Analytics basics. I am starting with Python, the programming language we will use in the boot camp, its components, data exploring libraries (NumPy, Pandas, Matplotlib anyone?), and styling conventions, to name a few.

This series intends to be more of a reference for myself and my bootcamp studies but I hope it can be useful for anyone starting their journey on Data Analysis. It is far from a comprehensive guide; it is indeed an open, live document that will, hopefully, expand with time. Any useful additions and constructive criticism will be immensely appreciated.

In this first edition of __Back to Basics__ I am going to explore one of the very basic Python's building blocks: ___variables___.

## Introduction to Python

Python is a [high-level](https://en.wikipedia.org/wiki/High-level_programming_language), [object-oriented](https://en.wikipedia.org/wiki/Object-oriented_programming), [general-purpose](https://en.wikipedia.org/wiki/General-purpose_programming_language) programming language. Guido Van Rossum, a Dutch programmer, first conceived it in the late 1980s. It first appeared in February 1991, and its 1.0 version was released in 1994.

Van Rossum thought programming with __C__, another programming language, was too time-consuming and a programming language should allow programmers to work faster and more efficiently. Also, he primed for readability, and simplicity with bash capabilities.

As of the writing of this article, Python is on version ___3.12.2___ and it can be downloaded [here](https://www.python.org/downloads/).

## Python's naming curiosity

Contrary to popular belief, Python was not named after a snake species, it was named as a tribute to the British comedy group [Monty Python](https://en.wikipedia.org/wiki/Monty_Python) as Python developers aim it to be fun to use.

![Monty Python](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fstatic2.srcdn.com%2Fwordpress%2Fwp-content%2Fuploads%2F2020%2F05%2FMonty-Python-and-the-Holy-Grail.jpg)

## Variables

### What is a variable?

> A variable is a container for storing data. A variable is a basic building block of a program.

Python is not a "statically typed" programming language, i.e., we do not need to declare variables __types__ before using them. Python is a "dynamically typed" programming language, i.e., it only checks variables at execution time (runtime). Python is so intelligent it can figure those out without us explicitly having to tell it.

The variable _value_ can be changed during the execution of a program.
A variable does not hold a real value but a reference to it. For example, a variable called 'x' with a value of '10' does not hold the real integer '10' but a reference to where it is located in the computer's memory. It works as a pointer to where the value is stored.

If we assign a different value to 'x', the variable reference location will change and point to the new in-memory location. '10' will still be '10. The integer's value did not change in the computer's memory. 

Example:

```python
x = 10  # points to the integer '10' location reference
x = 20  # it now points to the integer '20' location reference
```

## Declaring a variable

A variable is declared (created) when a value is assigned to it for the first time. To declare a variable we need to specify a __name__ and a __type__.

__Note:__ Python has __no__ command for declaring a variable.

The syntax to declare a variable can vary amongst programming languages. In Python, we use a __=__ (equal symbol) to assign a value to a variable name.

For example:

```python
quantity = 1
price = 2.5
product = 'muffin'
order = [2, 'cakes', 5.95]
```
The variables's names are 'quantity', 'price', 'product', and 'order'. The variable values are 1, 2.5, 'muffin', and [2, 'cakes', 5.95]. The variable values can be of different types, as explained further below.

## Variable Naming Rules

Variables in Python can be of any length, and consist of uppercase and lowercase letters (A-Z, a-z), digits(0-9), and the underscore character '_'.

__Note:__ The first character of a variable name __cannot__ be a digit. Declaring a variable with the name ___'2x___' will raise a __Syntax Error__.

Example:

```python
2x = 4
  Cell In[2], line 1
    2x = 4
    ^
SyntaxError: invalid decimal literal
```

__Note:__ Variable names cannot have spaces. Declaring a variable name with space on it will raise a __Syntax Error__.

Example:

```python
party cake = 'good'
  Cell In[1], line 1
    party cake = 'good'
          ^
SyntaxError: invalid syntax
```

## Case-sensitiviness

Python variables are case-sensitive, i.e., variables named 'cakes', 'Cakes', and 'CAKES', although using the same word, are three different variables. They do not reference the same things.

Example:

```python
cakes = 'yummy'
Cakes = 'delicious'
CAKES = 'more please'
```

## Python Style Guide = PEP 8

Python has a __recommended__ Styling Guide. It is available [here](https://peps.python.org/pep-0008/#introduction).

## Python Reserved words

We cannot use certain words as variable names, function names, or any other identifier because they are reserved for exclusive Python use.

As of the writing of this article, the following are Python's reserved words:

| | | | | 
|---|---|---|---|
|False|	def|	if|	raise|
|None|	del|	import|	return|
|True|	elif|	in|	try|
|and|	else|	is|	while|
|as|	except|	lambda|	with|
|assert|	finally|	nonlocal|	yield|
|break|	for|	not| | 
|class|	form|	or| |
|continue|	global|	pass| | |

__Note:__ All ___keyword___ are in __lowercase__ with the exception of _True_, _False_, and _None_.

## Python built-in Data Type

A data type in a programming language refers to an attribute that identifies the nature of a piece of data's value. It tells a computer how to interpret the data value. Some common examples include strings, integers, floats, and booleans.

Understanding __Data Types__ is important as _variables_ can store data types. Different data types can do different things.

The following Data Types are __built-in__ by default in Python.

| Description | Type |
|------|------|
|Text| 	str|
|Numeric| 	int, float, complex|
|Sequence| 	list, tuple, range|
|Mapping| 	dict|
|Set| 	set, frozenset|
|Boolean| 	bool|
|Binary| 	bytes, bytearray, memoryview|
|None| 	NoneType|

To find the type of a variable, we can use Python's __type()__ function:

For example:

```python  
quantity = 1                # 'quantity' is of type 'int'
price = 2.5                 # 'price' is of type 'float'
product = 'muffin'          # 'product' is of type 'str'
order = [2, 'cakes', 5.95]  # 'order' is of type 'list'

print("quantity", type(quantity))
print("price", type(price))
print("product", type(product))
print("order", type(order))

# Returns
quantity <class 'int'>
price <class 'float'>
product <class 'str'>
order <class 'list'>
```

## Summary

Variables are essential building blocks of any programming language. Understanding how they work and what we can do with them will make the difference between a concise, clearly written codebase and a convoluted, difficult-to-understand, and maintain one.

Consistency in how we create, name and use our variables will help us keep things under control as our codebase grows and becomes more complex. 

Treat your codebase with care. You will thank yourself later.