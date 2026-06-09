# Pandas Day 1 Learning Notes (Beginner to Intermediate)

## Overview

This document contains detailed notes from my Day 1 Pandas learning journey. The focus was on understanding the fundamentals of Pandas, working with DataFrames and Series, loading datasets, selecting data, filtering records, performing basic analysis, handling missing values, and understanding GroupBy operations using the Titanic dataset.

---

# 1. Introduction to Pandas

## What is Pandas?

Pandas is a Python library used for:

- Data Analysis
- Data Manipulation
- Data Cleaning
- Data Exploration

It allows us to work with structured data efficiently.

### Real-World Example

Consider student data:

```python
names = ["Rahul", "Priya", "John"]
ages = [20, 21, 22]
marks = [90, 85, 95]
```

Managing multiple lists becomes difficult.

Pandas solves this problem by organizing data into rows and columns.

---

# 2. Core Data Structures in Pandas

Pandas revolves around two primary data structures:

## 2.1 Series

A Series is a one-dimensional labeled array.

### Example

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
```

### Key Points

- Represents a single column.
- Has an index.
- Similar to an array but more powerful.

---

## 2.2 DataFrame

A DataFrame is a two-dimensional table consisting of rows and columns.

### Example

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
    Name   Age
0  Rahul   20
1  Priya   21
2  John    22
```

### Key Points

- Collection of multiple Series.
- Similar to an Excel sheet.
- Most commonly used Pandas structure.

---

# 3. Understanding Index

Every row in a DataFrame has an index.

Example:

```text
    Name   Age
0  Rahul   20
1  Priya   21
2  John    22
```

Indexes:

```text
0
1
2
```

### Purpose

- Identifies rows uniquely.
- Enables row selection.
- Helps in filtering and analysis.

---

# 4. Creating DataFrames

## Method 1: Dictionary

```python
data = {
    "Name": ["Rahul", "Priya", "John"],
    "Age": [20, 21, 22]
}

df = pd.DataFrame(data)
```

---

## Method 2: List of Dictionaries

```python
data = [
    {"Name": "Rahul", "Age": 20},
    {"Name": "Priya", "Age": 21},
    {"Name": "John", "Age": 22}
]

df = pd.DataFrame(data)
```

Each dictionary represents a row.

---

## Method 3: List of Lists

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

Real-world data usually comes from CSV files.

## Loading a CSV

```python
import pandas as pd

df = pd.read_csv("titanic.csv")
```

### What Happens Internally?

1. Opens file.
2. Reads column names.
3. Reads data rows.
4. Creates a DataFrame.

---

# 6. Dataset Exploration

## 6.1 View First Rows

```python
df.head()
```

Shows first 5 rows.

---

## 6.2 Dataset Shape

```python
df.shape
```

Output:

```python
(rows, columns)
```

Example:

```python
(891, 12)
```

Meaning:

- 891 rows
- 12 columns

---

## 6.3 View Column Names

```python
df.columns
```

Output:

```text
Index(['PassengerId', 'Survived', ...])
```

---

## 6.4 Dataset Information

```python
df.info()
```

Displays:

- Total rows
- Total columns
- Data types
- Missing values
- Memory usage

---

# 7. Data Types in Pandas

## Integer

```text
int64
```

Example:

```python
20
50
100
```

---

## Float

```text
float64
```

Example:

```python
7.25
71.283
```

---

## Object

```text
object
```

Usually represents text.

Example:

```python
"male"
"female"
"John"
```

---

# 8. Selecting Columns

## Single Column

```python
df["Age"]
```

Returns:

```text
Series
```

---

## Multiple Columns

```python
df[["Age", "Fare"]]
```

Returns:

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

Filtering helps select specific rows.

---

## Condition

```python
df["Age"] > 30
```

Output:

```text
True
False
True
...
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

A Boolean Mask is a Series containing:

```text
True
False
True
False
...
```

Used for filtering rows.

---

# 11. Multiple Conditions

## AND Operator

```python
df[(df["Age"] > 30) & (df["Sex"] == "female")]
```

Meaning:

```text
Age > 30 AND Female
```

Both conditions must be true.

---

## OR Operator

```python
df[(df["Age"] < 10) | (df["Age"] > 60)]
```

Meaning:

```text
Age < 10 OR Age > 60
```

At least one condition must be true.

---

# 12. Descriptive Statistics

## Mean

```python
df["Age"].mean()
```

Calculates average age.

---

## Maximum

```python
df["Age"].max()
```

Returns oldest passenger age.

---

## Minimum

```python
df["Age"].min()
```

Returns youngest passenger age.

---

## Median

```python
df["Age"].median()
```

Returns middle value after sorting.

### Mean vs Median

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

Median is less affected by outliers.

---

# 13. Missing Values

Real-world datasets often contain missing information.

Pandas represents missing values using:

```python
NaN
```

---

## Detect Missing Values

```python
df.isnull()
```

Returns True or False for every cell.

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

Meaning:

- Age has 177 missing values.
- Cabin has 687 missing values.
- Embarked has 2 missing values.

---

# 14. GroupBy

One of the most powerful Pandas operations.

Used to split data into groups and perform calculations.

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

Example:

```text
female    0.74
male      0.19
```

Interpretation:

- 74% females survived.
- 19% males survived.

---

## Survival Rate by Passenger Class

```python
df.groupby("Pclass")["Survived"].mean()
```

Example:

```text
Pclass
1    0.63
2    0.47
3    0.24
```

Interpretation:

- First Class: 63% survived.
- Second Class: 47% survived.
- Third Class: 24% survived.

---

## Count Records in Groups

```python
df.groupby("Sex").size()
```

Example:

```text
female    314
male      577
```

---

# 15. Sorting Data

Sorting arranges records in ascending or descending order.

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

## Highest Fare

```python
df.sort_values("Fare", ascending=False).head(10)
```

Top 10 passengers who paid the highest fare.

---

# Key Takeaways

After completing Day 1, I learned:

- What Pandas is and why it is used.
- Difference between Series and DataFrame.
- Creating DataFrames in multiple ways.
- Reading CSV datasets.
- Exploring datasets using head(), shape(), columns(), and info().
- Selecting single and multiple columns.
- Filtering rows using Boolean masks.
- Applying multiple conditions using AND and OR.
- Performing statistical analysis.
- Detecting missing values.
- Grouping data using GroupBy.
- Sorting data and finding top records.

These concepts form the foundation for Data Cleaning, Data Visualization, Feature Engineering, Machine Learning, and Advanced Data Analysis.
