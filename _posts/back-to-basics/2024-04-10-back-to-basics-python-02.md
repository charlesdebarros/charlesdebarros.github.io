---

title: "Python 02"
subheadline: "Back to Basics"
date: 2024-04-10 17:44
author: "Charles De Barros"
category: 
    - Back to Basics
    - Python
tags: 
    - Back to Basics
    - Python
image: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/GQ327RPuxhI/upload/5ce55fb3489bb113fdb4d0f106879c5d.jpeg?w=1600&h=840&fit=crop&crop=entropy&auto=compress,format&format=webp
---

## The Numeric data type

There are __eight__ major _data types_ in Python:

| Description | Type |
|------|------|
|Text| 	str|
| Numeric | int, float, complex|
|Sequence| list, tuple, range|
|Mapping| dict|
|Set| set, frozenset|
|Boolean| bool|
|Binary| bytes, bytearray, memoryview|
|None| NoneType|

__Numeric__ data types are widely used in mathematical, statistical, data science, and machine learning solutions.

There are _three_  distinct numeric types in Python:
* int (integer)
* float
* Complex

## Integers

What is an integer?

> An integer is a whole number, positive or negative, with _no fractional part_, i.e., no decimals, and unlimited length. It includes the ```0``` (zero).

We can write them down as ```"...-3, -2, -1, 0, 1, 2, 3..."```

Python uses the class ```int``` to represent all integer numbers.

When we define a variable __num__ with a value of __5__, the variable __num__ does not hold the real integer __5__. It stores a reference pointing to where the integer __5__ is held in the computer's memory.

```python
num = y
print(type(num))  # returns the variable num's type
```

The output is:
```python
<class 'int'>
```
__Note:__ In Python 3, there is effectively no limit to how long an integer value can be. The limit is constrained by the amount of memory your system has. 

## Integer operations

We can perform all standard mathematical operations using Python's integers, including:

| Operation | Operator |
| ---| :---: |
| Addition | + |
| Substraction | - |
| Multiplication | * |
| Division | / |
| Exponentiation | ** |

For example:

```python
num_1 = 10
num_2 = 5

c = num_1 + num_2
print(c)
print(type(c))

c = num_1 - num_2
print(c)
print(type(c))

c = num_1 * num_2
print(c)
print(type(c))

c = num_1 / num_2
print(c)
print(type(c))

c = num_1 ** num_2
print(c)
print(type(c))
```

The above calculations will return the following:
```python
# Addition
15
<class 'int'>
```
```python
# Subtraction
5
<class 'int'>
```
```python
# Multiplication
50
<class 'int'>
```
```python
# Division
# Note the result of the division is a decimal number. 
# More on that later.
2.0
<class 'float'>
```
```python
# Exponetiation
100000
<class 'int'>
```

## Floats
In addition to integers, consisting of whole numbers without fractions, Python also offers us the ___float___ type.

What is a float number?
> A float is a positive or negative number with _afractional part_, i.e., decimals, and unlimited length. It includes the ```0``` (zero).

## Float numbers precision
Python’s built-in float data type provides up to 15 digits of decimal precision. That is usually enough for common calculations. 

```python
100 / 30
3.3333333333333335 
# The floor division above returns a float.
# Note the value is rounded to the nearest 15-digit value available.
```

The default precision is 6 decimal places. You can set the precision using the ```round()```:

For example:

```python
x = 7.78
y = 3.3
result = x * y  # return 25.674
round(result, 2) 
25.67   # returns 'result' round to two decimals
```

## Operations with Floats

Operations with floats follow the same rules as operations with integers. The difference is, for obvious reasons, the presence of decimal points in the numbers used for the calculations.


## Order of Operations

As in normal mathematical calculations, Python integers and floats follow a defined order when performing operations. The famous PEMDAS:

### PEMBAS
PEMDAS was created to help remember the mathematical order of operations.

### PEMBAS Rank and Priority  

| Rank/Priority | Operation |
| --- | --- |
| 1 | Parentheses (Brackets) |
| 2 | Exponents and Roots |
| 3 | * Multiplication |
| 4 | * Division |
| 5 | ** Addition |
| 6 | ** Subtraction |

\* In PEMDAS Multiplication and Division have equal rank in the order of operations and do not need to be in any specific order. Whichever comes first, from left to right, is performed first.

\** The same principle of equal ranking applies to Addition and Subtraction. Whichever comes first, from left to right, is performed first. 

Examples:

```python
# Here multiplication happens first then the division
6 * 2 / 4
3.0

# And here the Division takes place first the the multiplication
6 / 2 * 4
12.0
```

## Division and Floor Division

In Python, there are two ways to divide numbers:
* The _normal division_ using the ```/``` operator;
* and the _floor division_, using the ```//``` operator.

Which one we will use will depend on the result we want to achieve.

What is the difference between the two?

> The single forward slash operator ```/``` is know as _float division_ and it always returns a float point value.

We would normally expect the following when performing a _float division_.

```python
# Two integers
100 / 30
3.3333333333333335

# One float and an integer
100.0 / 30
3.3333333333333335

# Two floats
100.0 / 30.0
3.3333333333333335
```

> The double forward slash operator ```//``` returns a _floored_ integer or a _floating point_ value.

The result of a double slash operator will depend on whether we use ```int``` or ```float``` numbers.

Examples:

```python
# Two integers return an integer. Where it is an exact division, 
# and there is no remainder.
100 // 25
4

# One integer and a float, always return a float.
100 // 25.0
4.0

# Two floats always return a float.
100.0 // 25.0
4.0
```

One interesting note about this is what happens with negative numbers:
```python
-7.0 // 3
-3.0
```

This makes sense because the result will be rounded down (i.e., floored), meaning that while we may expect it to be equal to -2.0, rounded down, the value is correctly -3.0.

## Complex Numbers
__Complex__ numbers are the numbers that are expressed in the form of a+ib where, a,b are real numbers and  ‘i’ is an imaginary number called “iota”. The value of i = (√-1). For example, 2+3i is a complex number, where 2 is a real number (Re) and 3i is an imaginary number (Im). 

Examples of complex numbers:

```python
x = 7 + 2i
y = -5 + 1.2i
```

## Conversion between Numeric types

A Numeric type can be converted into another numeric type by typecasting with the intended type. 

```python
x = 2.78
int_x = int(x)  # converts a float into an integer

y = 4
float_y = float(y)  # converts an integer into a float
```

### Important notes on conversions:

* Converting a float to an integer will _truncate_ the decimal part. In the example above, converting ```2.78``` into an integer, the result was ```2```, the number _before_ the decimal point. Turning ```2.99``` into and ```int``` would still return ```2```.
* Converting a large integer to float _may lose precision_.
* Converting an integer to complex just adds ```0j``` as the imaginary part.

## The use of Numeric types

There are numeric types all over the programming world. Some examples of areas where Numeric types are used but not restricted to:

* Finance apps
* Games
* Scientific apps
* Statistics
* Graphics
* Machine Learning
* Web Development
* Data Analysis and Data Science
* Embedded systems

## Summary

Whether using Python for programming, analysis, or web development, amongst other fields, developers rely heavily on Numeric types. Integers, float, complex numbers, calculations, equations, designing; the possibilities are endless. 

Understanding how Numeric types work is an essential and useful skill people should have. It becomes even more important if our fields of work involve working with programming languages. Fortunately, Python is a solid language processing numbers and has a very generous number of libraries available to expand Python's capability even further. 

Have a go at exploring Python Numeric types. It will certainly be a nice _addition_ to your programming skills. Pun intended. 
