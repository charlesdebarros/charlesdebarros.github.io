---

title: "Python 03"
subheadline: "Back to Basics"
date: 2024-04-23 17:44
author: "Charles De Barros"
category: 
    - Back to Basics
    - Python
tags: 
    - back to basics
    - python
image: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/uugOo5Lr_iM/upload/1462a749f1087a7dc95b78ee991ed897.jpeg?w=1600&h=840&fit=crop&crop=entropy&auto=compress,format&format=webp
---

## Better than sliced bread

___String___ slicing allows us to extract specific portions of a string by specifying a _start_ and an _end_ indices. We can even skip characters! How about that! For beginners, slicing things using a programming language can be a confusing experience, to say the least. There are so many new things to remember: learning to count like a computer, that we must start at index 0 (zero), and keeping in mind that the _end_ index is not included, i.e., the last character we originally thought would be returned, is not the character being returned. I beg your pardon! They all add to an initial sense of frustration. That frustration shall pass. Hopefully sooner than later. 

In this article, we will explore various scenarios with examples.

## The Basics of String Slicing

### 1. Slicing from the Start

We can obtain a substring by specifying the _start index_ and the _end index_ (not included) using the `slice` syntax. The first character in the string has an index of 0 (zero). Here's an example:

```python
s = "Ice cream"
# Get characters from position 2 to 4 (not including 5)
substring = s[2:5]  
print(substring)  # Output: "e c"
```
> Have you noticed that the space between 'ice' and 'cream' was also counted? Empty spaces are counted as normal characters when we use the `slice` method.

If we omit the _start index_, the default _start index_ is 0 (zero), the range will start from the beginning of the string:

```python
# Get characters from the start to position 4 (not including 5)
substring = s[:5]  
print(substring)  # Output: "Ice c"
```

### 2. Slicing to the End

Leaving out the _end index_ will extend the range to the end of the string.  The default end index is -1 (minus 1):

```python
# Get characters from position 2 to the end
substring = s[2:]  
print(substring)  # Output: "e cream"
```

### 3. Negative Indexing

We can also use negative indexes to slice from the end of the string. For example:

```python
# Get characters from "o" (position -5) to "d" (position -2)
substring = s[-5:-2]  
print(substring)  # Output: "cre"
```

## Advanced Slicing Techniques

### 1. Skipping Characters

To skip characters while slicing, use a _step value_. The syntax is `start:end:step`. For instance:

```python
s = "Python is amazing!"
# Get characters from position 1 to 9, skipping every second character
substring = s[1:10:2]  
print(substring)  # Output: "yhni"
```

### 2. Reverse Slicing

To reverse a string, use a _negative step value_:

```python
# Get the entire string in reverse
reversed_string = s[::-1]  
print(reversed_string)  # Output: "!gnizama si nohtyP"
```
That read like a Harry Potter spell, right?

## Summary

String slicing is a powerful tool in Python for manipulating and extracting substrings. Remember the basics: specify the _start_ and _end_ indices, and optionally include a _step_ value for more advanced slicing.

Try not to get too frustrated if, initially, your code does not return what you originally intended; it happens to all of us, all the time. Persistence and, sometimes a good night of sleep, are all that will take to get things right.  

Wait!?! Why do I, all of a sudden, fancy a piece of toast?

Happy coding! 

References:
1. [W3Schools](https://www.w3schools.com/python/python_strings_slicing.asp)¹
2. [Real Python](https://realpython.com/lessons/string-slicing/)²
3. [Enterprise DNA](https://blog.enterprisedna.co/python-slice-string/)³
4. [llego.dev](https://llego.dev/posts/comprehensive-guide-string-indexing-slicing-python/)⁴
5. [GeeksforGeeks](https://www.geeksforgeeks.org/string-slicing-in-python/)⁵
