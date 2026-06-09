# Pandas Day 2 Learning Notes (Advanced Data Analysis)

## Overview

This document contains detailed notes on advanced Pandas concepts including:

- Advanced Aggregations
- Pivot Tables
- Merge (Combining DataFrames)
- Concat
- Join
- Difference Between Concat, Merge, and Join

These operations are heavily used in Data Analysis, Data Science, Business Intelligence, Data Engineering, and Machine Learning projects.

---

# 1. Advanced Aggregations

## Theory

Aggregation means combining multiple values into a single summarized value.

Examples:

- Sum
- Mean
- Maximum
- Minimum
- Count
- Median

Aggregations help us understand large datasets quickly.

---

## Why Do We Need Aggregations?

Suppose we have sales data:

| Product | Sales |
| ------- | ----- |
| Laptop  | 50000 |
| Mobile  | 30000 |
| Laptop  | 60000 |
| Mobile  | 25000 |

Instead of viewing every row, we may want:

- Total Sales
- Average Sales
- Highest Sale
- Lowest Sale

Aggregation helps answer these questions.

---

## Common Aggregation Functions

| Function | Description        |
| -------- | ------------------ |
| sum()    | Total value        |
| mean()   | Average value      |
| max()    | Largest value      |
| min()    | Smallest value     |
| count()  | Number of values   |
| median() | Middle value       |
| std()    | Standard deviation |

---

## Example Dataset

```python
import pandas as pd

data = {
    "Product": ["Laptop","Laptop","Mobile","Mobile"],
    "Sales": [50000,60000,30000,25000]
}

df = pd.DataFrame(data)
```

---

## Sum

### Theory

Adds all values.

```python
df["Sales"].sum()
```

Output:

```text
165000
```

---

## Mean

### Theory

Calculates average.

```python
df["Sales"].mean()
```

Output:

```text
41250
```

---

## Maximum

```python
df["Sales"].max()
```

Output:

```text
60000
```

---

## Minimum

```python
df["Sales"].min()
```

Output:

```text
25000
```

---

## Multiple Aggregations

### Theory

Apply multiple aggregation functions simultaneously.

```python
df["Sales"].agg(["sum","mean","max","min"])
```

Output:

```text
sum     165000
mean     41250
max      60000
min      25000
```

---

# 2. GroupBy with Multiple Aggregations

## Theory

We can perform multiple calculations for each group.

---

## Example

```python
df.groupby("Product")["Sales"].agg(
    ["sum","mean","max","min"]
)
```

Output:

```text
         sum   mean   max   min
Product
Laptop 110000 55000 60000 50000
Mobile  55000 27500 30000 25000
```

---

## Real World Usage

Used for:

- Sales Reports
- Employee Performance Analysis
- Student Marks Analysis
- Financial Reports

---

# 3. Pivot Tables

## Theory

A Pivot Table is a powerful tool used to summarize, organize, and aggregate data.

It transforms rows into columns and creates a summarized report.

Think of Pivot Tables as advanced GroupBy operations.

---

## Why Use Pivot Tables?

Suppose we have sales data:

| Product | City   | Sales |
| ------- | ------ | ----- |
| Laptop  | Delhi  | 50000 |
| Mobile  | Delhi  | 30000 |
| Laptop  | Mumbai | 60000 |
| Mobile  | Mumbai | 25000 |

We may want:

```text
          Delhi   Mumbai
Laptop   50000   60000
Mobile   30000   25000
```

Pivot Tables make this easy.

---

## Syntax

```python
pd.pivot_table(
    data,
    index,
    columns,
    values,
    aggfunc
)
```

---

## Example

```python
data = {
    "Product":["Laptop","Mobile","Laptop","Mobile"],
    "City":["Delhi","Delhi","Mumbai","Mumbai"],
    "Sales":[50000,30000,60000,25000]
}

df = pd.DataFrame(data)
```

```python
pd.pivot_table(
    df,
    index="Product",
    columns="City",
    values="Sales",
    aggfunc="sum"
)
```

Output:

```text
City      Delhi   Mumbai
Product
Laptop    50000   60000
Mobile    30000   25000
```

---

## Multiple Aggregations in Pivot Table

```python
pd.pivot_table(
    df,
    index="Product",
    values="Sales",
    aggfunc=["sum","mean"]
)
```

Output:

```text
            sum     mean
Sales
Laptop   110000   55000
Mobile    55000   27500
```

---

# 4. Merge (Combining DataFrames)

## Theory

Merge combines two DataFrames based on a common column.

It works similarly to SQL JOIN operations.

This is one of the most important Pandas concepts.

---

## Why Merge?

Often data is stored in multiple tables.

### Students Table

| StudentID | Name  |
| --------- | ----- |
| 1         | Rahul |
| 2         | Priya |
| 3         | John  |

### Marks Table

| StudentID | Marks |
| --------- | ----- |
| 1         | 90    |
| 2         | 85    |
| 3         | 95    |

We need to combine them.

---

## Creating DataFrames

```python
students = pd.DataFrame({
    "StudentID":[1,2,3],
    "Name":["Rahul","Priya","John"]
})

marks = pd.DataFrame({
    "StudentID":[1,2,3],
    "Marks":[90,85,95]
})
```

---

## Merge Syntax

```python
pd.merge(
    left_df,
    right_df,
    on="column"
)
```

---

## Example

```python
pd.merge(
    students,
    marks,
    on="StudentID"
)
```

Output:

```text
   StudentID   Name  Marks
0          1  Rahul     90
1          2  Priya     85
2          3   John     95
```

---

# 5. Types of Merge

---

# Inner Merge

## Theory

Returns only matching rows.

```python
pd.merge(
    df1,
    df2,
    on="ID",
    how="inner"
)
```

---

# Left Merge

## Theory

Keeps all rows from left DataFrame.

```python
pd.merge(
    df1,
    df2,
    on="ID",
    how="left"
)
```

---

# Right Merge

## Theory

Keeps all rows from right DataFrame.

```python
pd.merge(
    df1,
    df2,
    on="ID",
    how="right"
)
```

---

# Outer Merge

## Theory

Keeps all rows from both DataFrames.

```python
pd.merge(
    df1,
    df2,
    on="ID",
    how="outer"
)
```

---

# Visual Understanding

```text
INNER JOIN

A ∩ B

Only common rows
```

```text
LEFT JOIN

All rows from A
+
Matching rows from B
```

```text
RIGHT JOIN

All rows from B
+
Matching rows from A
```

```text
OUTER JOIN

All rows from A and B
```

---

# 6. Concat

## Theory

Concat means stacking DataFrames together.

Unlike Merge, Concat does NOT require a common column.

---

## Vertical Concatenation

```python
df1 = pd.DataFrame({
    "Name":["Rahul","Priya"]
})

df2 = pd.DataFrame({
    "Name":["John","David"]
})
```

```python
pd.concat([df1,df2])
```

Output:

```text
    Name
0  Rahul
1  Priya
0   John
1  David
```

---

## Reset Index

```python
pd.concat(
    [df1,df2],
    ignore_index=True
)
```

Output:

```text
    Name
0  Rahul
1  Priya
2   John
3  David
```

---

## Horizontal Concatenation

```python
pd.concat(
    [df1,df2],
    axis=1
)
```

Output:

```text
   Name   Name
0 Rahul  John
1 Priya David
```

---

# 7. Join

## Theory

Join is similar to Merge but works primarily on indexes.

---

## Example

```python
df1.join(df2)
```

---

## When to Use Join?

Use Join when:

- DataFrames share indexes.
- Index-based combination is required.
- Faster syntax is preferred.

---

# Example

```python
df1 = pd.DataFrame(
    {"Name":["Rahul","Priya"]},
    index=[1,2]
)

df2 = pd.DataFrame(
    {"Marks":[90,85]},
    index=[1,2]
)
```

```python
df1.join(df2)
```

Output:

```text
    Name  Marks
1  Rahul     90
2  Priya     85
```

---

# 8. Concat vs Merge vs Join

## Theory

All three combine DataFrames, but they work differently.

---

## Comparison Table

| Feature              | Concat           | Merge              | Join               |
| -------------------- | ---------------- | ------------------ | ------------------ |
| Purpose              | Stack DataFrames | Combine on columns | Combine on indexes |
| Common Column Needed | ❌               | ✅                 | ❌                 |
| Uses Index           | Optional         | No                 | Yes                |
| SQL-like Behavior    | ❌               | ✅                 | Partial            |
| Most Powerful        | ❌               | ✅                 | Moderate           |

---

## When to Use Concat?

Use when:

- Appending rows
- Combining datasets vertically
- Combining datasets horizontally

Example:

```python
pd.concat([df1, df2])
```

---

## When to Use Merge?

Use when:

- DataFrames share a common key.
- Similar to SQL joins.
- Relational datasets.

Example:

```python
pd.merge(df1, df2, on="ID")
```

---

## When to Use Join?

Use when:

- DataFrames have matching indexes.
- Index-based operations.

Example:

```python
df1.join(df2)
```

---

# Real-World Applications

These operations are used in:

- Customer Analytics
- Sales Dashboards
- Banking Systems
- Healthcare Data
- Machine Learning Pipelines
- Data Warehouses
- Business Intelligence Reports

---

# Key Takeaways

After completing these topics, I learned:

- What aggregation means.
- Performing multiple aggregations.
- GroupBy with aggregations.
- Creating Pivot Tables.
- Summarizing data using Pivot Tables.
- Combining DataFrames using Merge.
- Understanding Inner, Left, Right, and Outer joins.
- Using Concat for stacking data.
- Using Join for index-based combinations.
- Differences between Concat, Merge, and Join.

These concepts are essential for advanced data manipulation and real-world data analysis projects.

# Pandas `iloc` – Complete Theory and Practical Guide

## What is `iloc`?

`iloc` stands for **Integer Location**.

It is a Pandas indexing method used to access rows and columns of a DataFrame using **integer positions (index numbers)** instead of row labels or column names.

In simple words, `iloc` allows us to select data based on where it is located in the DataFrame.

For example:

```python
df.iloc[0]
```

means:

> "Give me the first row of the DataFrame."

---

# Why Do We Need `iloc`?

When working with datasets, we often need to:

- Access specific rows
- Access specific columns
- Retrieve a particular value
- Extract subsets of data
- Split data into training and testing sets
- Select feature and target columns

Instead of using labels, sometimes it is easier to use row and column positions. `iloc` helps us achieve this.

---

# Understanding Positions in a DataFrame

Consider the following DataFrame:

```python
import pandas as pd

data = {
    "Name": ["John", "Alice", "Bob", "David"],
    "Age": [23, 25, 21, 30],
    "City": ["New York", "London", "Paris", "Tokyo"]
}

df = pd.DataFrame(data)

print(df)
```

Output:

```text
    Name   Age      City
0   John   23  New York
1  Alice   25    London
2    Bob   21     Paris
3  David   30     Tokyo
```

### Row Positions

| Position | Row   |
| -------- | ----- |
| 0        | John  |
| 1        | Alice |
| 2        | Bob   |
| 3        | David |

### Column Positions

| Position | Column |
| -------- | ------ |
| 0        | Name   |
| 1        | Age    |
| 2        | City   |

`iloc` works using these positions.

---

# Syntax of iloc

```python
df.iloc[row_selection, column_selection]
```

### Parameters

| Parameter        | Description        |
| ---------------- | ------------------ |
| row_selection    | Row position(s)    |
| column_selection | Column position(s) |

General format:

```python
df.iloc[rows, columns]
```

---

# 1. Selecting a Single Row

## Theory

To retrieve a specific row, pass its position inside `iloc`.

The first row has position `0`.

### Example

```python
df.iloc[0]
```

Output:

```text
Name         John
Age            23
City     New York
```

### Explanation

`0` represents the first row.

---

# 2. Selecting Multiple Rows

## Theory

We can pass a list of row positions.

### Example

```python
df.iloc[[0, 2]]
```

Output:

```text
   Name   Age      City
0  John   23  New York
2   Bob   21     Paris
```

### Explanation

Rows at positions `0` and `2` are selected.

---

# 3. Selecting a Single Column

## Theory

To select a column:

- Use `:` for all rows.
- Specify the column position.

### Example

```python
df.iloc[:, 0]
```

Output:

```text
0     John
1    Alice
2      Bob
3    David
```

### Explanation

```python
:
```

means all rows.

```python
0
```

means first column.

---

# 4. Selecting Multiple Columns

## Theory

Pass a list of column positions.

### Example

```python
df.iloc[:, [0, 2]]
```

Output:

```text
    Name      City
0   John  New York
1  Alice    London
2    Bob     Paris
3  David     Tokyo
```

---

# 5. Selecting a Specific Cell

## Theory

A cell is identified using:

```python
[row_position, column_position]
```

### Example

```python
df.iloc[1, 2]
```

Output:

```text
London
```

### Explanation

Row Position = 1 → Alice

Column Position = 2 → City

Result = London

---

# 6. Row Slicing

## Theory

Python slicing syntax:

```python
start:end
```

Important rule:

- Start index included
- End index excluded

### Example

```python
df.iloc[0:3]
```

Output:

```text
    Name   Age      City
0   John   23  New York
1  Alice   25    London
2    Bob   21     Paris
```

### Explanation

Rows selected:

```text
0
1
2
```

Row 3 is excluded.

---

# 7. Column Slicing

## Theory

Slicing can also be applied to columns.

### Example

```python
df.iloc[:, 0:2]
```

Output:

```text
    Name   Age
0   John   23
1  Alice   25
2    Bob   21
3  David   30
```

Columns selected:

```text
0 → Name
1 → Age
```

---

# 8. Row and Column Slicing Together

## Theory

We can simultaneously slice rows and columns.

### Example

```python
df.iloc[1:3, 0:2]
```

Output:

```text
    Name   Age
1  Alice   25
2    Bob   21
```

### Explanation

Rows:

```text
1, 2
```

Columns:

```text
0, 1
```

---

# 9. Negative Indexing

## Theory

Like Python lists, `iloc` supports negative indexing.

| Index | Meaning                |
| ----- | ---------------------- |
| -1    | Last row/column        |
| -2    | Second last row/column |
| -3    | Third last row/column  |

---

## Last Row

```python
df.iloc[-1]
```

Output:

```text
Name    David
Age        30
City    Tokyo
```

---

## Last Column

```python
df.iloc[:, -1]
```

Output:

```text
0    New York
1      London
2       Paris
3       Tokyo
```

---

# 10. Selecting Last N Rows

## Theory

Useful for viewing recent records.

### Example

```python
df.iloc[-2:]
```

Output:

```text
    Name   Age   City
2    Bob   21  Paris
3  David   30  Tokyo
```

---

# 11. Alternate Rows

## Theory

Python slicing supports a step value.

Syntax:

```python
start:end:step
```

### Example

```python
df.iloc[::2]
```

Output:

```text
   Name   Age      City
0  John   23  New York
2   Bob   21     Paris
```

Every second row is selected.

---

# 12. Reverse a DataFrame

## Theory

Using a negative step reverses the order.

### Example

```python
df.iloc[::-1]
```

Output:

```text
    Name   Age      City
3  David   30     Tokyo
2    Bob   21     Paris
1  Alice   25    London
0   John   23  New York
```

---

# 13. Selecting Specific Rows and Columns

## Theory

Lists can be used for both rows and columns.

### Example

```python
df.iloc[[0, 2], [0, 1]]
```

Output:

```text
   Name   Age
0  John   23
2   Bob   21
```

---

# Common Mistakes

## Mistake 1: Using Column Names

Wrong:

```python
df.iloc[:, "Name"]
```

Output:

```text
TypeError
```

### Why?

`iloc` only works with integer positions.

Correct:

```python
df.iloc[:, 0]
```

---

# Difference Between loc and iloc

| Feature                | loc | iloc |
| ---------------------- | --- | ---- |
| Uses labels            | ✅  | ❌   |
| Uses integer positions | ❌  | ✅   |
| Uses column names      | ✅  | ❌   |
| Uses column numbers    | ❌  | ✅   |
| End index included     | ✅  | ❌   |

### Example using loc

```python
df.loc[0, "Name"]
```

Output:

```text
John
```

### Example using iloc

```python
df.iloc[0, 0]
```

Output:

```text
John
```

---

# Real-World Machine Learning Applications

## Selecting Features

```python
X = df.iloc[:, :-1]
```

Theory:

- `:` → all rows
- `:-1` → all columns except the last

Used to create feature variables.

---

## Selecting Target Variable

```python
y = df.iloc[:, -1]
```

Theory:

- Selects the last column.

Used as the target/output variable.

---

## Splitting Dataset

```python
train = df.iloc[:800]
test = df.iloc[800:]
```

Theory:

- First 800 rows → Training Data
- Remaining rows → Testing Data

---

# Quick Revision Table

| Operation         | Code               |
| ----------------- | ------------------ |
| First Row         | `df.iloc[0]`       |
| Last Row          | `df.iloc[-1]`      |
| First Column      | `df.iloc[:,0]`     |
| Last Column       | `df.iloc[:,-1]`    |
| Specific Cell     | `df.iloc[0,1]`     |
| First 5 Rows      | `df.iloc[:5]`      |
| Last 5 Rows       | `df.iloc[-5:]`     |
| Multiple Rows     | `df.iloc[[0,2]]`   |
| Multiple Columns  | `df.iloc[:,[0,2]]` |
| Alternate Rows    | `df.iloc[::2]`     |
| Reverse DataFrame | `df.iloc[::-1]`    |
| Features          | `df.iloc[:,:-1]`   |
| Target Column     | `df.iloc[:,-1]`    |

---

# Summary

`iloc` is a position-based indexing method in Pandas that allows us to select rows and columns using integer positions.

### Key Points

- `iloc` stands for Integer Location.
- Uses row and column numbers.
- Supports slicing.
- Supports negative indexing.
- Supports lists.
- Does not accept column names.
- Widely used in Data Analysis and Machine Learning.
- Useful for feature selection, target selection, and dataset manipulation.

Mastering `iloc` is one of the most important skills for working efficiently with Pandas DataFrames.
