---

title: "Pandas 02"
subheadline: "Back to Basics"
date: 2024-04-16 18:15
header: 
    background-color: "#130654"
    caption: Three padlocks. One open and two closed.
    caption_url: https://unsplash.com/
category: ['Back to Basics', 'Pandas']
tags: ['back to basics', 'pandas']
image: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/WNHl-WwdwCs/upload/93e66a82cce1c0382b2ca9f31a7b7fa1.jpeg?w=1600&h=840&fit=crop&crop=entropy&auto=compress,format&format=webp
---

One of the most common tasks we perform with Pandas is data indexing and selection. We do that pretty much daily.

Let's delve into the world of **Pandas** and explore the differences between `loc()` and `iloc()` operators. These two methods are essential for data manipulation in Python, especially when working with **DataFrames**. Knowing how to apply those two well is the **key** to filtering a DataFrame efficiently. Did you get it? ***loc*** and ***key***? Nevermind! Let's jump in.

## Selecting with `loc()` and `iloc()`

### 1\. `loc()` - Label-Based Data Selection

The `loc()` function is a label-based data selection method. It allows us to select rows or columns based on their **labels** (i.e., row or column names) but may also be used with a boolean array with the same length as the row axis. Some key points about `loc()`:

* We pass the **name** of the row or column we want to select.
* It includes the **last element** of the range specified.
* It can accept **boolean data** for filtering.
* It's useful for selecting data based on specific conditions.

### 2\. `iloc()` - Integer-Based Data Selection

The `iloc()` function, on the other hand, is an integer-based data selection method. It uses **integer positions** to access data but may also be used with a boolean array. Here are some aspects of `iloc()` to keep in mind:

* We specify the **integer index** of the row or column we want to select.
* It **excludes** the endpoint when slicing (similar to the Python slicing convention).
* Like `loc[]`, it also accepts **boolean data** for filtering.
* It's ideal for accessing data by position.

## Examples

Let's demonstrate these concepts using a sample DataFrame containing information about cars:

```python
import pandas as pd
data = pd.DataFrame({
    'Brand': [
        'Ford', 'Hyundai', 'VW', 'Vauxhall', 'Ford', 
        'Hyundai', 'Renault', 'VW', 'Ford
    '],
    'Year': [
        2012, 2014, 2011, 2015, 2012, 
        2016, 2014, 2018, 2019
    ],
    'Kms Driven': [
        50000, 30000, 60000, 25000, 10000, 
        46000, 31000, 15000, 12000
    ],
    'City': [
        'Manchester', 'London', 'Birmingham', 'London', 'Birmingham', 
        'London', 'Birmingham', 'Liverpool', 'Nottingham'],
    'Mileage': [
        28, 27, 25, 26, 28, 29, 24, 21, 24
    ]
})
# Displaying the DataFrame
data
```

Displaying the DataFrame above we get:

| Brand | Year | Kms Driven | City | Mileage |
| --- | --- | --- | --- | --- |
| Maruti | 2012 | 50000 | Manchester | 28 |
| Hyundai | 2014 | 30000 | London | 27 |
| VW | 2011 | 60000 | Birmingham | 25 |
| Vauxhall | 2015 | 25000 | London | 26 |
| Ford | 2012 | 10000 | Birmingham | 28 |
| Hyundai | 2016 | 46000 | London | 29 |
| Renault | 2014 | 31000 | Birmingham | 24 |
| VW | 2018 | 15000 | Liverpool | 21 |
| Ford | 2019 | 12000 | Nottingham | 24 |

### Example 1: Conditional Selection Data

Let's use `loc()` to find Ford cars with a mileage greater than 25:

```python
display(data.loc[(data.Brand == 'Ford') & (data.Mileage > 25)])
```

Output:

| Brand | Year | Kms Driven | City | Mileage |
| --- | --- | --- | --- | --- |
| Ford | 2012 | 50000 | Manchester | 28 |
| Ford | 2012 | 10000 | Birmingham | 28 |

### Example 2: Row Selection using ranges

We'll use `iloc()` to extract rows with indices from 2 to 5 (inclusive):

```python
display(data.iloc[2:6])
```

Output:

| Brand | Year | Kms Driven | City | Mileage |
| --- | --- | --- | --- | --- |
| VW | 2011 | 60000 | Birmingham | 25 |
| Vauxhall | 2015 | 25000 | London | 26 |
| Ford | 2012 | 10000 | Birmingham | 28 |
| Hyundai | 2016 | 46000 | London | 29 |

## Summary
The Pandas `loc` and `iloc` are powerful tools for selecting and manipulating data within Pandas DataFrames and Series. Its utility ranges from simple row-and-column selections to more complex operations combined with other Pandas features like `groupby`. They can be adapted to work with boolean conditions, thereby offering a flexible approach to data manipulation tasks. Mastering `loc` and `iloc` will add flexibility to any Data Analyst's toolbox. 
