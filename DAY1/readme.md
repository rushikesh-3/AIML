# Pandas Day 1 Learning Notes (Beginner to Intermediate)

## Overview

This document contains detailed notes from my Day 1 Pandas learning journey. The focus was on understanding Pandas fundamentals, Series, DataFrames, reading datasets, data exploration, filtering, descriptive statistics, missing values, GroupBy operations, and sorting data.

These concepts form the foundation for Data Analysis, Data Science, Machine Learning, and Data Engineering.

---

# 1. Introduction to Pandas

## What is Pandas?

Pandas is an open-source Python library used for working with structured data.

It provides powerful tools for:

- Data Analysis
- Data Cleaning
- Data Manipulation
- Data Exploration
- Data Transformation

Pandas allows us to organize data into rows and columns similar to Excel spreadsheets or SQL tables.

---

## Why Do We Need Pandas?

Before Pandas:

```python
names = ["Rahul", "Priya", "John"]
ages = [20, 21, 22]
marks = [90, 85, 95]
```

Managing multiple lists becomes difficult as data grows.

With Pandas:

```python
import pandas as pd

data = {
    "Name": ["Rahul", "Priya", "John"],
    "Age": [20, 21, 22],
    "Marks": [90, 85, 95]
}

df = pd.DataFrame(data)

print(df)
```

Output:

```text
    Name  Age  Marks
0  Rahul   20     90
1  Priya   21     85
2   John   22     95
```

Everything is organized into a table.

---

## Real-World Applications

Pandas is widely used in:

- Data Science
- Machine Learning
- Business Analytics
- Financial Analysis
- Data Visualization
- Research Projects

---

# 2. Core Data Structures in Pandas

Pandas has two main data structures:

1. Series
2. DataFrame

---

# 2.1 Series

## Theory

A Series is a one-dimensional labeled array.

It contains:

- Values
- Indexes

Think of a Series as a single column in an Excel sheet.

---

## Syntax

```python
pd.Series(data)
```

---

## Example

```python
import pandas as pd

marks = pd.Series([90, 85, 95])

print(marks)
```

Output:

```text
0    90
1    85
2    95
dtype: int64
```

---

## Internal Representation

| Index | Value |
| ----- | ----- |
| 0     | 90    |
| 1     | 85    |
| 2     | 95    |

---

## Accessing Elements

```python
print(marks[0])
```

Output:

```text
90
```

---

## Characteristics of Series

- One-dimensional
- Has an index
- Can store numbers, strings, or mixed data
- Similar to NumPy arrays but more powerful

---

## Real-World Examples

A Series can represent:

- Student Marks
- Employee Salaries
- Product Prices
- Monthly Sales

---

# 2.2 DataFrame

## Theory

A DataFrame is a two-dimensional table consisting of rows and columns.

A DataFrame is essentially a collection of multiple Series.

It is the most commonly used Pandas structure.

---

## Syntax

```python
pd.DataFrame(data)
```

---

## Example

```python
import pandas as pd

data = {
    "Name": ["Rahul", "Priya", "John"],
    "Age": [20, 21, 22]
}

df = pd.DataFrame(data)

print(df)
```

Output:

```text
    Name  Age
0  Rahul   20
1  Priya   21
2   John   22
```

---

## Structure

| Index | Name  | Age |
| ----- | ----- | --- |
| 0     | Rahul | 20  |
| 1     | Priya | 21  |
| 2     | John  | 22  |

---

## Characteristics of DataFrame

- Two-dimensional
- Contains rows and columns
- Supports different data types
- Similar to Excel sheets

---

## Real-World Examples

DataFrames can store:

- Student Databases
- Employee Records
- Hospital Data
- Banking Transactions
- Sales Reports

---

# 3. Understanding Index

## Theory

Every row in a DataFrame has a unique identifier called an Index.

Example:

```text
    Name  Age
0  Rahul  20
1  Priya 21
2  John  22
```

Indexes:

```text
0
1
2
```

---

## Why is Index Important?

Indexes help us:

- Locate rows
- Filter data
- Perform joins
- Access specific records

---

## Example

```python
print(df.index)
```

Output:

```text
RangeIndex(start=0, stop=3, step=1)
```

---

# 4. Creating DataFrames

There are multiple ways to create DataFrames.

---

## Method 1: Using Dictionary

### Theory

Most common method.

Each key becomes a column.

```python
data = {
    "Name": ["Rahul", "Priya", "John"],
    "Age": [20, 21, 22]
}

df = pd.DataFrame(data)
```

---

## Method 2: Using List of Dictionaries

### Theory

Each dictionary represents one row.

```python
data = [
    {"Name": "Rahul", "Age": 20},
    {"Name": "Priya", "Age": 21},
    {"Name": "John", "Age": 22}
]

df = pd.DataFrame(data)
```

---

## Method 3: Using List of Lists

### Theory

Useful when data comes in tabular form.

```python
data = [
    ["Rahul", 20],
    ["Priya", 21],
    ["John", 22]
]

df = pd.DataFrame(data, columns=["Name", "Age"])
```

---

# 5. Reading CSV Files

## Theory

CSV stands for Comma Separated Values.

Most datasets are stored in CSV format.

Pandas provides a built-in function to read CSV files.

---

## Syntax

```python
pd.read_csv("filename.csv")
```

---

## Example

```python
import pandas as pd

df = pd.read_csv("titanic.csv")
```

---

## What Happens Internally?

When Pandas reads a CSV:

1. Opens the file.
2. Reads column names.
3. Reads data rows.
4. Creates a DataFrame.
5. Stores data in memory.

---

# 6. Dataset Exploration

Before analyzing data, we must understand the dataset.

---

# 6.1 Viewing First Rows

## Theory

Used to quickly inspect data.

---

### Syntax

```python
df.head()
```

---

### Example

```python
df.head()
```

Output:

```text
First 5 rows of dataset
```

---

# 6.2 Shape of Dataset

## Theory

Returns number of rows and columns.

---

### Syntax

```python
df.shape
```

---

### Example

```python
print(df.shape)
```

Output:

```text
(891, 12)
```

Meaning:

- 891 rows
- 12 columns

---

# 6.3 Column Names

## Theory

Displays all column names.

---

### Syntax

```python
df.columns
```

Output:

```text
Index(['PassengerId','Survived','Pclass',...])
```

---

# 6.4 Dataset Information

## Theory

Provides a summary of the DataFrame.

---

### Syntax

```python
df.info()
```

---

### Information Provided

- Number of rows
- Number of columns
- Data types
- Missing values
- Memory usage

---

# 7. Data Types in Pandas

Each column has a data type.

---

## Integer (int64)

Stores whole numbers.

Example:

```python
20
45
100
```

---

## Float (float64)

Stores decimal values.

Example:

```python
7.25
71.283
```

---

## Object

Usually stores text data.

Example:

```python
"male"
"female"
"John"
```

---

# 8. Selecting Columns

## Theory

Selecting columns is one of the most common operations.

---

## Single Column

```python
df["Age"]
```

Output:

```text
Series
```

---

## Multiple Columns

```python
df[["Age", "Fare"]]
```

Output:

```text
DataFrame
```

---

## Difference

| Expression         | Returns   |
| ------------------ | --------- |
| df["Age"]          | Series    |
| df[["Age"]]        | DataFrame |
| df[["Age","Fare"]] | DataFrame |

---

# 9. Filtering Data

## Theory

Filtering means selecting rows that satisfy a condition.

---

## Example Condition

```python
df["Age"] > 30
```

Output:

```text
True
False
True
```

This is called a Boolean Mask.

---

## Actual Filtering

```python
df[df["Age"] > 30]
```

Meaning:

```text
Return rows where Age > 30
```

---

# 10. Boolean Masks

## Theory

A Boolean Mask contains:

```text
True
False
True
False
```

Pandas uses these values to decide which rows to keep.

---

## Example

```python
mask = df["Age"] > 30

print(mask)
```

---

# 11. Multiple Conditions

## AND Condition

### Theory

Both conditions must be true.

```python
df[(df["Age"] > 30) & (df["Sex"] == "female")]
```

---

## OR Condition

### Theory

At least one condition must be true.

```python
df[(df["Age"] < 10) | (df["Age"] > 60)]
```

---

# 12. Descriptive Statistics

Descriptive statistics summarize data.

---

## Mean

### Theory

Average value.

```python
df["Age"].mean()
```

---

## Maximum

### Theory

Largest value.

```python
df["Age"].max()
```

---

## Minimum

### Theory

Smallest value.

```python
df["Age"].min()
```

---

## Median

### Theory

Middle value after sorting.

```python
df["Age"].median()
```

---

## Mean vs Median

Example:

```text
1 2 3 4 100
```

Mean:

```text
22
```

Median:

```text
3
```

Median is less affected by extreme values.

---

# 13. Missing Values

## Theory

Real-world datasets often contain incomplete information.

Pandas represents missing values using:

```python
NaN
```

Meaning:

```text
Not a Number
```

---

## Detect Missing Values

```python
df.isnull()
```

---

## Count Missing Values

```python
df.isnull().sum()
```

Example:

```text
Age        177
Cabin      687
Embarked     2
```

---

# 14. GroupBy

## Theory

GroupBy is one of the most powerful Pandas operations.

It follows:

```text
Split → Apply → Combine
```

1. Split data into groups.
2. Apply operation.
3. Combine results.

---

## Average Age by Gender

```python
df.groupby("Sex")["Age"].mean()
```

Output:

```text
female    27.9
male      30.7
```

---

## Survival Rate by Gender

```python
df.groupby("Sex")["Survived"].mean()
```

Output:

```text
female    0.74
male      0.19
```

Interpretation:

- 74% females survived.
- 19% males survived.

---

## Count Records in Each Group

```python
df.groupby("Sex").size()
```

Output:

```text
female    314
male      577
```

---

# 15. Sorting Data

## Theory

Sorting arranges data in ascending or descending order.

---

## Sort by Age

```python
df.sort_values("Age")
```

Ascending order.

---

## Descending Order

```python
df.sort_values("Age", ascending=False)
```

Oldest passengers first.

---

## Top 5 Oldest Passengers

```python
df.sort_values("Age", ascending=False).head(5)
```

---

## Highest Fare Passengers

```python
df.sort_values("Fare", ascending=False).head(10)
```

Returns top 10 passengers who paid the highest fare.

---

# Key Takeaways

After completing Day 1, I learned:

- What Pandas is and why it is used.
- Difference between Series and DataFrame.
- Understanding indexes.
- Creating DataFrames in multiple ways.
- Reading CSV files.
- Exploring datasets.
- Understanding data types.
- Selecting columns.
- Filtering rows using Boolean masks.
- Applying multiple conditions.
- Descriptive statistics.
- Handling missing values.
- Using GroupBy operations.
- Sorting datasets.

These concepts form the foundation for Data Cleaning, Data Visualization, Feature Engineering, Machine Learning, and Advanced Data Analysis.
