---

title: "Pandas 01"
subheadline: "Back to Basics"
date: 2024-04-09 18:15
category: ['Back to Basics', 'Pandas']
tags: ['back to basics', 'pandas']
image: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/_9a-3NO5KJE/upload/a80714217496935f70f044601bf6186f.jpeg?w=1600&h=840&fit=crop&crop=entropy&auto=compress,format&format=webp
---

# Introduction to Pandas

[Pandas Official Documentation](https://pandas.pydata.org/docs/).

## What is Pandas?

As per the *Pandas Official Documentation* website:

> **Pandas** is an open source, BSD-licensed library providing high-performance, easy-to-use data structures and data analysis tools for the [Python](https://www.python.org/) programming language.

Pandas simplifies common data analysis tasks:

* Load data from numerous types of files and online sources

* Fast and efficient handling of large amounts of data

* Filtering, sorting, editing and processing of data

* Joining and aggregation of datasets

* Tools for time series and statistical analysis

* Display of data in tables and charts

## Pandas data structures: DataFrames & Series

### **DataFrame** (rows and columns)

> **DataFrame** is a 2-dimensional labelled data structure with columns of potentially different types. You can think of it like a spreadsheet, an SQL table, or a dictionary of Series objects. It is generally the most commonly used Pandas object. Like Series, DataFrame accepts many different kinds of input:

* Dict of 1D ndarrays, lists, dicts, or **Series**

* 2-D numpy.ndarray

* *Structured or record* ndarray

* A **Series**

* Another **DataFrame**

Notes on **Data Frames**:

* 2-dimensional labelled data structure made of rows and columns of 'potentially' different types.

* Similar principle of a spreadsheet or SQL table. The most commonly used data structure used in Pandas.

* Indexing starts from 0 (zero) for both rows and columns.

### Series (one-dimensional data)

> **Series** is a one-dimensional labelled array capable of holding any data type (integers, strings, floating point numbers, Python objects, etc.).

* It is a one-dimensional labelled data.

* An example of a Series is one column from a Data Frame.

* Indexing in a Series starts from 0 (zero).

The basic method to create a **Series** is to call:

```python
s = pd.Series(data, index=index)
```

A **Series** plus another **Series** equals a **Data Frame**.

## Pandas Common Data Types

| Data type | Description |
| --- | --- |
| **object** | Used for strings, or if the column contains a mix of data types |
| **int64** | Used for integers (*'64'* relates to memory usage) |
| **float64** | Used for floats, or where the column has both integers and *NaN* values |
| **bool** | Booleans, i.e., `True` or `False` |
| **datatime64** / **timedelta** | Time-based values |

## Pandas Missing Values

The `NaN` marker represents Pandas missing values or `NULL` values. In most cases, the terms *missing* and *null* are interchangeable. Date values use the **NaT** marker.

| Symbol | Description |
| --- | --- |
| **NaN** | Used to indicate missing values in most instances and is supported by the *floar* datatype. |
| **NaT** | Used to indicate missing values where a `date type` object may have been expected. |

## Exploratory Data Analysis - EDA

What is **EDA**?

> Exploratory data analysis (EDA) is used by data scientists to analyse and investigate data sets and summarise their main characteristics, often employing data visualisation methods.

**EDA** helps determine how best to manipulate data sources to get the answers needed, making it easier for data scientists to discover patterns, spot anomalies, test a hypothesis, or check assumptions.

**EDA** is primarily used to see what data can reveal beyond the *formal modelling* or *hypothesis testing* task and provides a better understanding of data set variables and their relationship. It can also help determine if the *statistical techniques* you are considering for data analysis are appropriate.

## Basic Pandas Data Frame exploration

### Importing Pandas (and NumPy)

The following lines will bring both **Pandas** and **NumPy** libraries to the working environment.

```python
import pandas as pd
import numpy as np
```

Data can be imported from various formats: *CVS*, *spreadsheets*, *JSON*, *databases*, etc.

The following line will import a *CSV* (Comma Separated Values) to the working sessions.

```python
df = pd.read_csv(<filepath>)
```

**Note:** different parameters can be used with the `.read_csv()` function. In its simplest form, only the *filepath* is required.

The "*Telco-Customer-Churn.csv*" dataset can be found [**here**](https://www.kaggle.com/datasets/blastchar/telco-customer-churn){:target="_blank"} at [Kaggle](www.kaggle.com){:target="_blank"}.

```python
# Will open the 'Telco-Customer-Churn.csv' in the 'data' folder
df = pd.read_csv("data/Telco-Customer-Churn.csv")
```

### Checking Top/Bottom rows

We can use the `.head()` and the `.tail()` functions to see the top first 5 rows, and the bottom last 5 rows, in *ascending order*.

> The `.head()` function returns the first n rows for the object based on position. It is useful for quickly testing if your object has the right type of data in it. The default is **5** rows.

> The `.tails()` function returns the last n rows from the object based on position. It is useful for quickly verifying data, for example, after sorting or appending rows. The default is **5** rows.

```python
# Returns the first 5 top rows in ASC order
df.head()

# Returns the last 5 bottom rows in ASC order
df.tail()
```

### Checking random sample rows

> The `.sample()` will return sample rows ***at random***. It offers an interesting look at the *body* of the Data Frame. The default is to return only **1** row.

```python
# Returns 10 random row samples.
.sample(10)
```

### Showing the Data Frame Dimensions

> The `.shape` method to display the `dataframe` dimensions: rows and columns.

```python
# In the 'Telco-Customer-Churn.csv' there are 7043 rows and 21 columns.
df.shape
(7043, 21)
```

### Displaying the Data Frame basic info

> The `.info()` prints information about a DataFrame including the index dtype and columns, non-null values and memory usage.

```python
# Print a concise summary of a DataFrame.
df.info()
```

Returns:

```python
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 7043 entries, 0 to 7042
Data columns (total 21 columns):
 #   Column            Non-Null Count  Dtype  
---  ------            --------------  -----  
 0   customerID        7043 non-null   object 
 1   gender            7043 non-null   object 
 2   SeniorCitizen     7043 non-null   int64  
 3   Partner           7043 non-null   object 
 4   Dependents        7043 non-null   object 
 5   tenure            7043 non-null   int64  
 6   PhoneService      7043 non-null   object 
 7   MultipleLines     7043 non-null   object 
 8   InternetService   7043 non-null   object 
 9   OnlineSecurity    7043 non-null   object 
 10  OnlineBackup      7043 non-null   object 
 11  DeviceProtection  7043 non-null   object 
 12  TechSupport       7043 non-null   object 
 13  StreamingTV       7043 non-null   object 
 14  StreamingMovies   7043 non-null   object 
 15  Contract          7043 non-null   object 
 16  PaperlessBilling  7043 non-null   object 
 17  PaymentMethod     7043 non-null   object 
 18  MonthlyCharges    7043 non-null   float64
 19  TotalCharges      7043 non-null   object 
 20  Churn             7043 non-null   object 
dtypes: float64(1), int64(2), object(18)
memory usage: 1.1+ MB
```

### Generating Descriptive Statistics

> The `.describe()` function generates descriptive statistics.

*Descriptive statistics* is the process of using current and historical data to identify trends and relationships. It includes those that summarize the central tendency, dispersion and shape of a dataset’s distribution, *excluding***NaN** values.

Analyzes both numeric and object series, as well as DataFrame column sets of mixed data types. The output will vary depending on what is provided.

It returns the following:

* count: Total number of non-missing values

* mean: The mean value

* std: The standard deviation

* min: The minimum value

* 25%: The value of the first quartile (25th percentile)

* 50%: The median value (50th percentile)

* 75%: The value of the third quartile (75th percentile)

* max: The maximum value

```python
df.describe()
```

Returns:

```python
      SeniorCitizen	    tenure	MonthlyCharges
count   7043.000000   7043.000000	   7043.000000
mean	   0.162147     32.371149	     64.761692
std	    0.368612	 24.559481	     30.090047
min	    0.000000      0.000000	     18.250000
25%	    0.000000      9.000000	     35.500000
50%	    0.000000	 29.000000	     70.350000
75%	    0.000000	 55.000000	     89.850000
max	    1.000000	 72.000000	    118.750000
```

### Sorting Values

> The `.sort_values()` function sorts by the values along either axis. it allows us to choose a 'column' to sort it by. The default is ***ASC***.

```python
# ascending=False will sort the column values in DESC order.
df.sort_values(by='monthlycharleges', ascending=False)
```

## Summary

As a high-level, data manipulation and analysis library, Pandas is a powerful and versatile tool in any Data Analyst arsenal. It is fast, easy to use, and very comprehensive to analyse and manipulate datasets.

Pandas' realm of functions and methods is vast, no doubt about it. Pandas is a must-have tool data analysts should be acquainted with and use with their daily tasks.