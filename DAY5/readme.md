# PHASE 1: FOUNDATIONS OF MATPLOTLIB

> Goal: Build a rock-solid understanding of Data Visualization, Matplotlib architecture, plotting workflow, and the internal concepts that power every chart you will create in the future.

---

# Learning Outcomes

After completing Phase 1, you will be able to:

- Understand the purpose of data visualization
- Explain why Matplotlib exists
- Install and configure Matplotlib
- Use the `pyplot` module effectively
- Understand Figures and Axes
- Understand the Artist hierarchy
- Understand Matplotlib backends
- Understand the rendering pipeline
- Understand the complete plot lifecycle
- Create your first professional plots
- Understand how Matplotlib works internally

---

# Module 1: What is Data Visualization?

## Definition

Data Visualization is the graphical representation of data using visual elements such as:

- Charts
- Graphs
- Maps
- Dashboards
- Heatmaps
- Statistical Plots

The primary purpose is to transform raw data into visual information that humans can understand quickly.

---

## Why Data Visualization Exists

Imagine receiving this data:

```python
sales = [120, 180, 250, 310, 400]
```

You can read the numbers.

But can you instantly identify:

- Growth trends?
- Acceleration?
- Patterns?
- Anomalies?

Not easily.

Now imagine the same data represented as a graph.

The trend becomes immediately visible.

This is why visualization exists.

---

## Problems Solved by Visualization

### 1. Pattern Detection

Visualization helps reveal:

- Trends
- Cycles
- Correlations
- Clusters

Example:

```python
temperature = [22,24,26,29,31,33]
```

A graph instantly shows a rising trend.

---

### 2. Outlier Detection

Example:

```python
salary = [40000,42000,41000,43000,1000000]
```

A graph quickly reveals the extreme value.

---

### 3. Communication

Managers, researchers, and stakeholders often understand charts more quickly than spreadsheets.

---

## Real World Applications

### Business Analytics

- Sales dashboards
- Revenue reports
- Customer analytics

### Data Science

- Exploratory Data Analysis (EDA)
- Model performance evaluation

### Machine Learning

- Loss curves
- Accuracy plots
- Confusion matrices

### Research

- Experimental results
- Publication figures

### Engineering

- Sensor monitoring
- Signal visualization

---

## Types of Visualizations

| Purpose        | Recommended Chart |
| -------------- | ----------------- |
| Trend Analysis | Line Plot         |
| Comparison     | Bar Plot          |
| Correlation    | Scatter Plot      |
| Distribution   | Histogram         |
| Spread         | Box Plot          |
| Composition    | Pie Chart         |
| Density        | Hexbin Plot       |

---

# Module 2: What is Matplotlib?

## Definition

Matplotlib is the most widely used Python visualization library for creating:

- Static charts
- Interactive charts
- Publication-quality figures
- Scientific visualizations

---

## Why Matplotlib Was Created

Before Matplotlib:

- Scientists relied heavily on MATLAB
- Python lacked a powerful plotting library

Matplotlib was created to bring MATLAB-style plotting capabilities to Python.

---

## Historical Background

Creator:

John D. Hunter

Release:

2002

Primary Goal:

```text
Scientific Visualization
+
Publication Quality Graphics
+
Python Integration
```

---

## Why Professionals Use Matplotlib

### Data Analysts

Create reports and dashboards.

### Data Scientists

Perform EDA and model analysis.

### Researchers

Generate publication-ready figures.

### ML Engineers

Visualize training and evaluation metrics.

---

## Strengths

- Highly customizable
- Industry standard
- Large ecosystem
- Publication-quality output
- Works with NumPy and Pandas

---

## Limitations

- Steeper learning curve
- More verbose than Seaborn
- Less interactive than Plotly

---

# Module 3: Installing Matplotlib

## Installation Using pip

```bash
pip install matplotlib
```

---

## Verify Installation

```python
import matplotlib

print(matplotlib.__version__)
```

---

## Installation Using Anaconda

```bash
conda install matplotlib
```

---

## Upgrade Matplotlib

```bash
pip install --upgrade matplotlib
```

---

## Common Installation Issues

### Module Not Found

```python
ModuleNotFoundError: No module named 'matplotlib'
```

Solution:

```bash
pip install matplotlib
```

---

### Multiple Python Versions

Check:

```bash
python --version
pip --version
```

Ensure both belong to the same environment.

---

# Module 4: Understanding pyplot

## What is pyplot?

`pyplot` is a collection of functions that make Matplotlib easy to use.

Import:

```python
import matplotlib.pyplot as plt
```

---

## Why pyplot Exists

Instead of manually creating:

- Figures
- Axes
- Canvases

Pyplot automatically manages them.

---

## Example

```python
import matplotlib.pyplot as plt

plt.plot([1,2,3],[4,5,6])
plt.show()
```

---

## Internal Workflow

When you call:

```python
plt.plot()
```

Matplotlib automatically:

1. Creates a Figure
2. Creates an Axes
3. Draws the line
4. Displays the chart

---

# Module 5: Understanding Figure

## Definition

A Figure is the entire plotting window.

Think of it as:

```text
Figure
 └── Axes
      └── Plot
```

---

## Creating a Figure

```python
import matplotlib.pyplot as plt

fig = plt.figure()
```

---

## Setting Figure Size

```python
fig = plt.figure(figsize=(8,5))
```

Meaning:

```python
width = 8 inches
height = 5 inches
```

---

## Figure Components

```text
Figure
├── Title
├── Axes
├── Legends
├── Labels
└── Plot Elements
```

---

# Module 6: Understanding Axes

## Definition

Axes represent the actual plotting area.

Many beginners confuse:

- Axis
- Axes

### Axis

Single coordinate line.

```text
X-axis
Y-axis
```

### Axes

Complete plotting area.

```text
+-------------+
|             |
|   Plot      |
|             |
+-------------+
```

---

## Creating Axes

```python
fig, ax = plt.subplots()
```

---

## Plotting on Axes

```python
fig, ax = plt.subplots()

ax.plot([1,2,3],[4,5,6])
```

---

## Why Professionals Prefer Axes

Better control.

Supports:

- Multiple plots
- Complex layouts
- Dashboards

---

# Module 7: Understanding Backends

## What is a Backend?

A backend is responsible for rendering the figure.

It converts:

```text
Python Objects
↓
Pixels
↓
Screen Output
```

---

## Backend Architecture

```text
Matplotlib
      ↓
Backend
      ↓
Renderer
      ↓
Screen/File
```

---

## Common Backends

| Backend | Purpose         |
| ------- | --------------- |
| Agg     | PNG Rendering   |
| TkAgg   | Desktop GUI     |
| QtAgg   | Advanced GUI    |
| PDF     | PDF Output      |
| SVG     | Vector Graphics |

---

## Check Current Backend

```python
import matplotlib

print(matplotlib.get_backend())
```

---

# Module 8: Artist Hierarchy

Everything in Matplotlib is an Artist.

Examples:

- Figure
- Axes
- Text
- Lines
- Labels
- Legends

All are Artists.

---

## Artist Tree

```text
Figure
│
├── Axes
│   ├── Line
│   ├── Title
│   ├── Labels
│   └── Ticks
│
└── Legend
```

---

## Why This Matters

Understanding Artists helps with:

- Customization
- Styling
- Advanced visualization

---

# Module 9: Plot Lifecycle

Every plot follows the same lifecycle.

---

## Step 1: Import

```python
import matplotlib.pyplot as plt
```

---

## Step 2: Create Figure

```python
fig = plt.figure()
```

---

## Step 3: Create Axes

```python
ax = fig.add_subplot(111)
```

---

## Step 4: Plot Data

```python
ax.plot(x,y)
```

---

## Step 5: Customize

```python
ax.set_title("Sales")
```

---

## Step 6: Render

```python
plt.show()
```

---

# Internal Rendering Pipeline

```text
User Code
      ↓
Pyplot API
      ↓
Figure Creation
      ↓
Axes Creation
      ↓
Artist Generation
      ↓
Backend Selection
      ↓
Renderer
      ↓
Canvas Drawing
      ↓
Screen/File Output
```

---

# First Professional Plot

```python
import matplotlib.pyplot as plt

months = ["Jan","Feb","Mar","Apr","May"]
sales = [100,150,180,250,320]

fig, ax = plt.subplots(figsize=(8,5))

ax.plot(months, sales)

ax.set_title("Monthly Sales")
ax.set_xlabel("Month")
ax.set_ylabel("Sales")

plt.show()
```

---

# Common Beginner Mistakes

## Forgetting plt.show()

```python
plt.plot(x,y)
```

No output may appear.

Solution:

```python
plt.show()
```

---

## Confusing Figure and Axes

Wrong:

```python
fig.plot()
```

Correct:

```python
ax.plot()
```

---

## Using Lists of Different Lengths

Wrong:

```python
x = [1,2,3]
y = [10,20]
```

Produces:

```python
ValueError
```

---

# Best Practices

- Prefer Object-Oriented API
- Label axes clearly
- Use meaningful titles
- Use consistent figure sizes
- Avoid unnecessary colors
- Keep charts simple
- Always verify data before plotting

---

# Interview Questions

## Beginner

1. What is Matplotlib?
2. Why is visualization important?
3. What is pyplot?
4. What is a Figure?
5. What is an Axes?

---

## Intermediate

1. Explain Figure vs Axes.
2. What are Matplotlib backends?
3. Explain the Artist hierarchy.
4. Explain the rendering process.
5. Why use the Object-Oriented API?

---

## Advanced

1. Explain Matplotlib's rendering pipeline.
2. How does backend selection affect performance?
3. What is the role of the renderer?
4. How does Matplotlib manage memory?
5. Explain Artist architecture in detail.

---

# Phase 1 Summary

By completing Phase 1, you now understand:

✅ Data Visualization Fundamentals

✅ Why Matplotlib Exists

✅ Installation and Setup

✅ pyplot Module

✅ Figure Object

✅ Axes Object

✅ Artist Hierarchy

✅ Backend Architecture

✅ Rendering Pipeline

✅ Plot Lifecycle

These concepts form the foundation for every chart and visualization you will build in the remaining phases.

# PHASE 2: BASIC CHARTS IN MATPLOTLIB

> Goal: Master the most important chart types used by Data Analysts, Data Scientists, ML Engineers, Researchers, and Business Intelligence professionals.

---

# Learning Outcomes

After completing Phase 2, you will be able to:

- Create professional line plots
- Build scatter plots for correlation analysis
- Design vertical and horizontal bar charts
- Create pie charts effectively
- Analyze distributions using histograms
- Detect outliers using box plots
- Select the right chart for the right problem
- Customize charts professionally
- Interpret visualizations correctly
- Answer interview questions confidently

---

# Chart Selection Guide

| Problem                         | Recommended Chart   |
| ------------------------------- | ------------------- |
| Trend Over Time                 | Line Plot           |
| Relationship Between Variables  | Scatter Plot        |
| Compare Categories              | Bar Plot            |
| Compare Categories Horizontally | Horizontal Bar Plot |
| Show Proportions                | Pie Chart           |
| Analyze Distribution            | Histogram           |
| Detect Outliers                 | Box Plot            |

---

# MODULE 1: LINE PLOT

---

# What is a Line Plot?

A Line Plot connects data points using straight lines.

Used primarily to visualize:

- Trends
- Growth
- Decline
- Time Series Data

---

## Real-World Uses

### Business

- Monthly Sales
- Revenue Growth
- Customer Growth

### Finance

- Stock Prices
- Portfolio Tracking

### Data Science

- Model Accuracy
- Training Loss

### Engineering

- Sensor Readings

---

# Basic Syntax

```python
plt.plot(x, y)
```

---

# Parameter Breakdown

```python
plt.plot(
    x,
    y,
    color='blue',
    linestyle='-',
    linewidth=2,
    marker='o',
    markersize=6,
    label='Sales'
)
```

| Parameter  | Purpose       |
| ---------- | ------------- |
| x          | X values      |
| y          | Y values      |
| color      | Line color    |
| linestyle  | Style of line |
| linewidth  | Thickness     |
| marker     | Point marker  |
| markersize | Marker size   |
| label      | Legend label  |

---

# Example

```python
import matplotlib.pyplot as plt

months = ["Jan","Feb","Mar","Apr","May"]
sales = [100,150,200,250,320]

plt.plot(months, sales)

plt.title("Monthly Sales")
plt.xlabel("Month")
plt.ylabel("Sales")

plt.show()
```

---

# Output Analysis

Displays:

```text
Sales
 ^
 |
320                 *
250            *
200       *
150   *
100 *
 +----------------------> Month
```

Shows upward growth trend.

---

# Common Mistakes

### Missing x values

```python
plt.plot(y)
```

Matplotlib auto-generates:

```python
0,1,2,3...
```

for x-axis.

---

### Different Length Arrays

```python
x=[1,2,3]
y=[10,20]
```

Error:

```python
ValueError
```

---

# Best Practices

- Use line plots for continuous data
- Add markers for clarity
- Label axes
- Include titles

---

# Interview Questions

### When should line plots be used?

Answer:

When visualizing continuous trends over time.

---

### Why not use line plots for categorical comparison?

Because lines imply continuity between points.

---

# Exercises

1. Plot daily temperatures.
2. Plot monthly expenses.
3. Plot website traffic for 30 days.

---

# MODULE 2: SCATTER PLOT

---

# What is a Scatter Plot?

A Scatter Plot displays individual observations as points.

Used for:

- Correlation
- Clustering
- Outlier Detection

---

## Real-World Uses

### Data Science

Relationship:

```text
Hours Studied
vs
Exam Score
```

---

### Business

```text
Advertising Spend
vs
Revenue
```

---

# Syntax

```python
plt.scatter(x, y)
```

---

# Advanced Syntax

```python
plt.scatter(
    x,
    y,
    c='red',
    s=100,
    alpha=0.7,
    marker='o'
)
```

---

# Parameter Table

| Parameter | Purpose      |
| --------- | ------------ |
| x         | X values     |
| y         | Y values     |
| c         | Color        |
| s         | Size         |
| alpha     | Transparency |
| marker    | Shape        |

---

# Example

```python
import matplotlib.pyplot as plt

hours=[1,2,3,4,5]
scores=[40,50,65,75,90]

plt.scatter(hours,scores)

plt.xlabel("Hours Studied")
plt.ylabel("Score")

plt.show()
```

---

# Interpretation

Positive correlation:

```text
 *
    *
       *
          *
             *
```

More study hours → Higher score.

---

# Common Mistakes

- Using scatter for trends with thousands of points
- Overlapping points

Solution:

```python
alpha=0.5
```

---

# Exercises

1. Height vs Weight
2. Age vs Salary
3. Experience vs Income

---

# MODULE 3: BAR PLOT

---

# What is a Bar Plot?

Used for comparing categories.

---

# Real-World Uses

- Product Sales
- Department Revenue
- Student Marks

---

# Syntax

```python
plt.bar(categories, values)
```

---

# Example

```python
products=["A","B","C","D"]
sales=[100,250,150,300]

plt.bar(products,sales)

plt.show()
```

---

# Output

```text
300 |       █
250 |   █   █
200 |
150 |   █ █ █
100 | █ █ █ █
```

---

# Parameters

| Parameter | Purpose      |
| --------- | ------------ |
| x         | Categories   |
| height    | Bar heights  |
| width     | Bar width    |
| color     | Bar color    |
| edgecolor | Border color |

---

# Best Practices

- Sort categories logically
- Avoid too many categories
- Use meaningful colors

---

# Exercises

1. Compare product sales.
2. Compare department profits.
3. Compare country populations.

---

# MODULE 4: HORIZONTAL BAR PLOT

---

# What is It?

Same as Bar Plot but horizontal.

Useful when category names are long.

---

# Syntax

```python
plt.barh(categories, values)
```

---

# Example

```python
languages=["Python","Java","C++","JavaScript"]
jobs=[90,75,60,80]

plt.barh(languages,jobs)

plt.show()
```

---

# When to Use

Use when labels become unreadable vertically.

---

# MODULE 5: PIE CHART

---

# What is a Pie Chart?

Shows proportions of a whole.

---

# Example

```python
market=[40,30,20,10]

plt.pie(market)

plt.show()
```

---

# Better Example

```python
labels=["A","B","C","D"]

plt.pie(
    market,
    labels=labels,
    autopct="%1.1f%%"
)

plt.show()
```

---

# Common Mistakes

Too many slices.

Bad:

```text
20+ categories
```

Good:

```text
4-6 categories
```

---

# Business Uses

- Market Share
- Budget Allocation
- Expense Breakdown

---

# Exercises

1. Budget distribution.
2. Market share visualization.
3. Expense categories.

---

# MODULE 6: HISTOGRAM

---

# What is a Histogram?

Shows distribution of numerical data.

---

# Why Important?

One of the most used plots in Data Science.

Helps identify:

- Normal distribution
- Skewness
- Outliers

---

# Syntax

```python
plt.hist(data)
```

---

# Example

```python
import numpy as np

data=np.random.normal(50,10,1000)

plt.hist(data)

plt.show()
```

---

# Important Parameter

```python
bins
```

Example:

```python
plt.hist(data,bins=20)
```

---

# Output Interpretation

Bell Shape:

```text
        ███
      ███████
    ███████████
      ███████
        ███
```

Normal distribution.

---

# Exercises

1. Student marks.
2. Employee salaries.
3. Product prices.

---

# Interview Questions

### What is the purpose of bins?

Answer:

Bins divide data into intervals.

---

# MODULE 7: BOX PLOT

---

# What is a Box Plot?

Shows:

- Median
- Quartiles
- Spread
- Outliers

---

# Why Important?

Extremely useful for:

- Statistical Analysis
- Data Cleaning
- Outlier Detection

---

# Syntax

```python
plt.boxplot(data)
```

---

# Example

```python
scores=[10,12,13,14,15,16,18,100]

plt.boxplot(scores)

plt.show()
```

---

# Box Plot Components

```text
Outlier
  *
  |
----- Q3
|   |
| M |
|   |
----- Q1
```

---

# Interpretation

Detect:

- Outliers
- Data spread
- Skewness

---

# Exercises

1. Employee salaries.
2. Student marks.
3. House prices.

---

# Common Mistakes Across All Charts

### Missing Labels

Bad:

```python
plt.plot(x,y)
```

Good:

```python
plt.xlabel("Month")
plt.ylabel("Sales")
```

---

### No Title

Always provide context.

---

### Wrong Chart Selection

Example:

Using pie chart for:

```text
50 categories
```

Bad visualization choice.

---

# Best Practices

- Use line plots for trends.
- Use scatter plots for relationships.
- Use bar plots for comparisons.
- Use histograms for distributions.
- Use box plots for outlier detection.
- Use pie charts sparingly.

---

# Mini Project

## Student Performance Dashboard

Visualize:

- Marks trend
- Subject comparison
- Marks distribution
- Outlier analysis

Use:

- Line Plot
- Bar Plot
- Histogram
- Box Plot

---

# Intermediate Project

## Sales Analytics Dashboard

Visualize:

- Monthly sales trend
- Product-wise revenue
- Sales distribution
- Regional comparisons

---

# Advanced Project

## Stock Market Analysis

Create:

- Price trend
- Volume comparison
- Return distribution
- Outlier detection

---

# Industry Project

## Business KPI Dashboard

Metrics:

- Revenue
- Profit
- Growth Rate
- Customer Acquisition

Use multiple chart types together.

---

# Interview Questions

## Beginner

1. Difference between line and scatter plot?
2. When should bar charts be used?
3. What is a histogram?
4. What is a box plot?
5. What are bins?

---

## Intermediate

1. Histogram vs Bar Plot?
2. Scatter Plot vs Line Plot?
3. Box Plot vs Histogram?
4. How to detect outliers?
5. Why use transparency in scatter plots?

---

## Advanced

1. How does Matplotlib render large scatter plots?
2. What factors affect histogram interpretation?
3. Explain quartiles in box plots.
4. How do chart choices influence business decisions?
5. When should pie charts be avoided?

---

# Phase 2 Summary

You now understand:

✅ Line Plot

✅ Scatter Plot

✅ Bar Plot

✅ Horizontal Bar Plot

✅ Pie Chart

✅ Histogram

✅ Box Plot

✅ Chart Selection Principles

✅ Visualization Best Practices

✅ Common Mistakes

✅ Interview Questions

These chart types form the foundation of nearly every Data Analysis, Data Science, Machine Learning, Research, and Business Intelligence workflow.

# PHASE 3: INTERMEDIATE CHARTS IN MATPLOTLIB

> Goal: Move beyond basic visualizations and learn powerful intermediate charts used by Data Scientists, Quantitative Analysts, Researchers, Engineers, and Business Intelligence teams for deeper analysis and professional reporting.

---

# Learning Outcomes

After completing Phase 3, you will be able to:

- Visualize cumulative trends using Area Plots
- Compare multiple cumulative series using Stack Plots
- Display discrete signals using Stem Plots
- Visualize step-wise processes using Step Plots
- Represent uncertainty using Error Bar Plots
- Analyze distributions using Violin Plots
- Visualize dense datasets using Hexbin Plots
- Select advanced charts appropriately
- Build professional analytical reports

---

# Intermediate Chart Selection Guide

| Problem                        | Recommended Chart |
| ------------------------------ | ----------------- |
| Cumulative Growth              | Area Plot         |
| Multiple Cumulative Categories | Stack Plot        |
| Discrete Signals               | Stem Plot         |
| Piecewise Processes            | Step Plot         |
| Measurement Uncertainty        | Error Bar Plot    |
| Distribution Comparison        | Violin Plot       |
| Millions of Scatter Points     | Hexbin Plot       |

---

# MODULE 1: AREA PLOT

---

# What is an Area Plot?

An Area Plot is similar to a line plot but fills the area beneath the line.

```text
Line Plot

    *
   *
  *
 *
*


Area Plot

    *
   *█
  *██
 *███
*████
```

---

## Why Use Area Plots?

They emphasize:

- Magnitude
- Volume
- Cumulative growth

---

## Real-World Uses

### Finance

- Portfolio value growth
- Investment returns

### Business

- Revenue growth
- User growth

### Analytics

- Website traffic trends

---

# Syntax

```python
plt.fill_between(x, y)
```

---

# Example

```python
import matplotlib.pyplot as plt

months = [1,2,3,4,5]
sales = [100,150,200,250,300]

plt.fill_between(months, sales)

plt.show()
```

---

# Parameter Breakdown

```python
plt.fill_between(
    x,
    y1,
    y2=0,
    color='skyblue',
    alpha=0.5
)
```

| Parameter | Purpose        |
| --------- | -------------- |
| x         | X values       |
| y1        | Upper boundary |
| y2        | Lower boundary |
| color     | Fill color     |
| alpha     | Transparency   |

---

# Output Analysis

Filled region shows total magnitude.

Useful when volume matters.

---

# Common Mistakes

### Using Too Many Series

Area plots become cluttered.

Bad:

```text
10+ overlapping areas
```

---

# Best Practice

Use for:

- 1–3 series maximum
- Trend emphasis

---

# Exercises

1. Monthly sales area chart
2. Website visitors
3. Electricity consumption

---

# MODULE 2: STACK PLOT

---

# What is a Stack Plot?

A Stack Plot shows multiple area plots stacked on top of each other.

---

# Purpose

Shows:

- Total value
- Individual contribution

---

# Example

```python
import matplotlib.pyplot as plt

days = [1,2,3,4,5]

productA = [10,20,30,40,50]
productB = [5,10,15,20,25]
productC = [2,5,8,10,12]

plt.stackplot(
    days,
    productA,
    productB,
    productC
)

plt.show()
```

---

# Visualization

```text
████████ Product C
████████ Product B
████████ Product A
-------------------
```

---

# Business Uses

- Product sales contribution
- Revenue breakdown
- Resource allocation

---

# Parameter Reference

| Parameter | Purpose       |
| --------- | ------------- |
| x         | X values      |
| y arrays  | Categories    |
| labels    | Legend labels |
| colors    | Area colors   |

---

# Common Mistakes

### Too Many Categories

Hard to interpret.

Limit:

```text
3–6 categories
```

---

# Exercises

1. Department budgets
2. Product sales
3. Energy source contribution

---

# MODULE 3: STEM PLOT

---

# What is a Stem Plot?

Displays discrete values using vertical lines.

---

# Visualization

```text
|
|
*
|
|
*
|
*
```

---

# Real-World Uses

### Signal Processing

- Digital signals

### Electronics

- Sampled data

### DSP

- Frequency analysis

---

# Syntax

```python
plt.stem(x, y)
```

---

# Example

```python
import matplotlib.pyplot as plt

x = [1,2,3,4,5]
y = [2,5,1,6,3]

plt.stem(x,y)

plt.show()
```

---

# Parameter Breakdown

| Parameter | Purpose        |
| --------- | -------------- |
| x         | X values       |
| y         | Stem heights   |
| linefmt   | Stem style     |
| markerfmt | Marker style   |
| basefmt   | Baseline style |

---

# Why Not Use Line Plot?

Stem plots emphasize:

```text
Discrete events
```

instead of continuous trends.

---

# Exercises

1. Sensor readings
2. Digital signal values
3. Event frequencies

---

# MODULE 4: STEP PLOT

---

# What is a Step Plot?

A Step Plot displays values changing at specific intervals.

---

# Example

Electricity tariff:

```text
0-100 units → ₹3
100-200 units → ₹5
```

Not continuous.

Step Plot is ideal.

---

# Syntax

```python
plt.step(x, y)
```

---

# Example

```python
import matplotlib.pyplot as plt

x=[1,2,3,4,5]
y=[10,10,20,20,30]

plt.step(x,y)

plt.show()
```

---

# Applications

### Finance

- Interest rates

### Engineering

- Digital circuits

### Operations

- Pricing slabs

---

# Important Parameter

```python
where=
```

Options:

```python
'pre'
'post'
'mid'
```

---

# Exercises

1. Pricing slabs
2. Tax brackets
3. Electricity billing

---

# MODULE 5: ERROR BAR PLOT

---

# What is an Error Bar Plot?

Shows uncertainty in measurements.

---

# Why Important?

Real-world data contains:

- Variability
- Noise
- Experimental error

---

# Visualization

```text
    |
    |
----*----
    |
    |
```

---

# Syntax

```python
plt.errorbar(x, y, yerr)
```

---

# Example

```python
import matplotlib.pyplot as plt

x=[1,2,3,4]
y=[10,20,15,30]
error=[1,2,1.5,3]

plt.errorbar(
    x,
    y,
    yerr=error
)

plt.show()
```

---

# Parameter Reference

| Parameter | Purpose          |
| --------- | ---------------- |
| x         | X values         |
| y         | Y values         |
| yerr      | Vertical error   |
| xerr      | Horizontal error |
| capsize   | Error cap size   |
| fmt       | Marker style     |

---

# Research Uses

- Laboratory experiments
- Clinical trials
- Scientific publications

---

# Exercises

1. Temperature measurements
2. Lab experiment results
3. Manufacturing tolerance analysis

---

# MODULE 6: VIOLIN PLOT

---

# What is a Violin Plot?

Combines:

```text
Box Plot
+
Distribution Density
```

---

# Why Use It?

Shows:

- Median
- Quartiles
- Density shape

---

# Visualization

```text
   /\
  /  \
 |    |
 |    |
  \  /
   \/
```

Looks like a violin.

---

# Syntax

```python
plt.violinplot(data)
```

---

# Example

```python
import matplotlib.pyplot as plt
import numpy as np

data = np.random.normal(
    100,
    15,
    1000
)

plt.violinplot(data)

plt.show()
```

---

# Advantages Over Box Plot

Shows:

- Distribution shape
- Multiple peaks
- Density concentration

---

# Applications

### Data Science

Feature distribution analysis

### Healthcare

Patient measurements

### Finance

Income distributions

---

# Exercises

1. Salary distribution
2. Exam score analysis
3. Customer spending

---

# MODULE 7: HEXBIN PLOT

---

# What is a Hexbin Plot?

Alternative to Scatter Plot for very large datasets.

---

# Problem

Scatter Plot:

```python
1,000,000 points
```

becomes unreadable.

---

# Solution

Hexbin groups points into hexagons.

---

# Visualization

```text
⬢ ⬢ ⬢
 ⬢ ⬢ ⬢
⬢ ⬢ ⬢
```

Color indicates density.

---

# Syntax

```python
plt.hexbin(x, y)
```

---

# Example

```python
import matplotlib.pyplot as plt
import numpy as np

x=np.random.randn(100000)
y=np.random.randn(100000)

plt.hexbin(x,y)

plt.show()
```

---

# Parameter Breakdown

```python
plt.hexbin(
    x,
    y,
    gridsize=30,
    cmap='viridis'
)
```

| Parameter | Purpose       |
| --------- | ------------- |
| x         | X values      |
| y         | Y values      |
| gridsize  | Hexagon count |
| cmap      | Color map     |
| mincnt    | Minimum count |

---

# Data Science Uses

- Large datasets
- Density analysis
- Geospatial analysis

---

# Advantages

Compared to Scatter Plot:

```text
Handles millions of points efficiently
```

---

# Common Mistakes Across Intermediate Charts

---

## Wrong Chart Selection

Using Area Plot when:

```text
Magnitude is irrelevant
```

---

## Too Many Categories in Stack Plot

Creates confusion.

---

## Ignoring Error Bars

Leads to misleading conclusions.

---

## Using Scatter Instead of Hexbin

For:

```python
1,000,000+ points
```

---

# Best Practices

- Use Area Plots for cumulative trends.
- Use Stack Plots for composition analysis.
- Use Stem Plots for discrete signals.
- Use Step Plots for piecewise processes.
- Use Error Bars for uncertainty.
- Use Violin Plots for distribution analysis.
- Use Hexbin Plots for dense datasets.

---

# Mini Project

## Website Traffic Analytics

Create:

- Area Plot for total visits
- Stack Plot for traffic sources

---

# Intermediate Project

## Sales Contribution Dashboard

Visualize:

- Product contributions
- Revenue growth
- Market share trends

---

# Advanced Project

## Scientific Experiment Analysis

Create:

- Error Bar Plot
- Violin Plot
- Distribution Analysis

---

# Industry Project

## Customer Behavior Analytics Platform

Use:

- Hexbin Plot
- Violin Plot
- Stack Plot

Analyze:

- Spending behavior
- Customer density
- Revenue contribution

---

# Interview Questions

## Beginner

1. What is an Area Plot?
2. What is a Stack Plot?
3. What is a Stem Plot?
4. Why use Step Plots?
5. What are Error Bars?

---

## Intermediate

1. Area Plot vs Line Plot?
2. Stack Plot vs Bar Plot?
3. Box Plot vs Violin Plot?
4. Error Bars vs Confidence Intervals?
5. Scatter Plot vs Hexbin Plot?

---

## Advanced

1. How does Hexbin improve performance?
2. Why are hexagons preferred over squares?
3. Explain density estimation in Violin Plots.
4. How are Error Bars interpreted statistically?
5. When should Stack Plots be avoided?

---

# Phase 3 Summary

You now understand:

✅ Area Plot

✅ Stack Plot

✅ Stem Plot

✅ Step Plot

✅ Error Bar Plot

✅ Violin Plot

✅ Hexbin Plot

✅ Intermediate Visualization Selection

✅ Distribution Analysis

✅ Density Visualization

✅ Uncertainty Representation

These charts are heavily used in professional analytics, scientific research, engineering systems, financial analysis, and large-scale data science workflows.

# PHASE 5: MATPLOTLIB CUSTOMIZATION & STYLING

> Goal: Learn how to transform basic plots into professional, publication-quality, dashboard-ready, and presentation-ready visualizations through advanced customization techniques.

---

# Learning Outcomes

After completing Phase 5, you will be able to:

- Master colors and colormaps
- Apply professional styles and themes
- Customize markers and line styles
- Design effective legends
- Create meaningful labels and titles
- Control ticks and tick formatting
- Add annotations and callouts
- Build publication-quality charts
- Follow data visualization best practices
- Create reusable styling systems

---

# Why Customization Matters

Consider two charts:

### Default Chart

```text
Simple
Unstyled
Hard to interpret
```

### Professional Chart

```text
Readable
Visually appealing
Insightful
Presentation-ready
```

Customization bridges the gap.

---

# CUSTOMIZATION ROADMAP

```text
Colors
   ↓
Colormaps
   ↓
Styles
   ↓
Themes
   ↓
Markers
   ↓
Linestyles
   ↓
Legends
   ↓
Labels
   ↓
Titles
   ↓
Ticks
   ↓
Annotations
```

---

# MODULE 1: COLORS

---

# What Are Colors?

Colors help communicate information visually.

They can:

- Differentiate categories
- Highlight trends
- Show importance
- Represent magnitude

---

# Basic Syntax

```python
plt.plot(x, y, color='red')
```

---

# Common Color Names

```python
'red'
'blue'
'green'
'black'
'orange'
'purple'
'yellow'
'cyan'
'magenta'
```

---

# Example

```python
import matplotlib.pyplot as plt

x=[1,2,3,4]
y=[10,20,15,30]

plt.plot(x,y,color='red')

plt.show()
```

---

# Hex Colors

Used heavily in professional dashboards.

```python
color='#FF5733'
```

Example:

```python
plt.plot(x,y,color='#3498DB')
```

---

# RGB Colors

```python
color=(0.1,0.5,0.8)
```

Range:

```python
0 → 1
```

---

# RGBA Colors

A = Alpha

```python
color=(1,0,0,0.5)
```

50% transparent red.

---

# Best Practices

✅ Use limited color palettes

✅ Maintain consistency

✅ Use color meaningfully

❌ Avoid rainbow overload

❌ Avoid random colors

---

# MODULE 2: COLORMAPS

---

# What Is a Colormap?

A colormap maps numerical values to colors.

Example:

```text
Low Value → Blue
Medium → Green
High Value → Red
```

---

# Why Important?

Used in:

- Heatmaps
- Density plots
- Scientific visualizations
- Geospatial analysis

---

# View Available Colormaps

```python
import matplotlib.pyplot as plt

print(plt.colormaps())
```

---

# Popular Colormaps

| Colormap | Use Case            |
| -------- | ------------------- |
| viridis  | Default             |
| plasma   | Scientific          |
| inferno  | High contrast       |
| magma    | Dark themes         |
| cividis  | Colorblind-friendly |
| coolwarm | Diverging data      |

---

# Example

```python
plt.scatter(
    x,
    y,
    c=z,
    cmap='viridis'
)
```

---

# Categories of Colormaps

---

## Sequential

```text
Light → Dark
```

Examples:

```python
viridis
plasma
inferno
```

Used for:

```text
Magnitude
Temperature
Density
```

---

## Diverging

```text
Negative ↔ Positive
```

Examples:

```python
coolwarm
seismic
bwr
```

Used for:

```text
Profit/Loss
Change
Deviation
```

---

## Qualitative

Different categories.

Examples:

```python
Set1
Set2
tab10
```

---

# MODULE 3: STYLES

---

# What Are Styles?

Styles apply predefined chart appearances.

---

# Available Styles

```python
plt.style.available
```

---

# Popular Styles

```python
'ggplot'
'seaborn-v0_8'
'fast'
'classic'
'dark_background'
'fivethirtyeight'
```

---

# Example

```python
plt.style.use('ggplot')
```

---

# Full Example

```python
import matplotlib.pyplot as plt

plt.style.use('ggplot')

plt.plot([1,2,3],[4,5,6])

plt.show()
```

---

# Benefits

- Consistency
- Professional appearance
- Reduced code

---

# MODULE 4: THEMES

---

# What Are Themes?

Themes define:

- Colors
- Fonts
- Grid styles
- Backgrounds

---

# Light Theme

```text
White Background
Dark Text
```

---

# Dark Theme

```python
plt.style.use('dark_background')
```

---

# Use Cases

### Light Theme

Reports

Publications

---

### Dark Theme

Dashboards

Presentations

Monitoring Systems

---

# MODULE 5: MARKERS

---

# What Are Markers?

Markers highlight individual data points.

---

# Example

```python
plt.plot(
    x,
    y,
    marker='o'
)
```

---

# Common Markers

| Marker | Shape    |
| ------ | -------- |
| o      | Circle   |
| s      | Square   |
| ^      | Triangle |
| \*     | Star     |
| x      | Cross    |
| D      | Diamond  |
| +      | Plus     |

---

# Marker Size

```python
plt.plot(
    x,
    y,
    marker='o',
    markersize=10
)
```

---

# Marker Color

```python
plt.plot(
    x,
    y,
    marker='o',
    markerfacecolor='red'
)
```

---

# Best Practices

Use markers when:

- Data points are important
- Dataset is small

Avoid when:

- Thousands of points

---

# MODULE 6: LINESTYLES

---

# What Are Linestyles?

Control appearance of lines.

---

# Common Styles

| Style | Meaning  |
| ----- | -------- |
| -     | Solid    |
| --    | Dashed   |
| -.    | Dash Dot |
| :     | Dotted   |

---

# Example

```python
plt.plot(
    x,
    y,
    linestyle='--'
)
```

---

# Line Width

```python
plt.plot(
    x,
    y,
    linewidth=3
)
```

---

# Professional Usage

Different linestyles can represent:

- Actual values
- Forecast values
- Targets
- Benchmarks

---

# MODULE 7: LEGENDS

---

# What Is a Legend?

A legend explains chart elements.

---

# Example

```python
plt.plot(
    x,
    y,
    label='Sales'
)

plt.legend()
```

---

# Multiple Lines

```python
plt.plot(x,y1,label='Product A')
plt.plot(x,y2,label='Product B')

plt.legend()
```

---

# Legend Positions

```python
plt.legend(
    loc='upper right'
)
```

---

# Common Locations

```python
'upper right'
'upper left'
'lower right'
'lower left'
'center'
```

---

# Best Practices

- Avoid overlapping data
- Use concise labels

---

# MODULE 8: LABELS

---

# What Are Labels?

Labels describe axes.

---

# X Label

```python
plt.xlabel("Month")
```

---

# Y Label

```python
plt.ylabel("Sales")
```

---

# Font Size

```python
plt.xlabel(
    "Month",
    fontsize=14
)
```

---

# Best Practices

Good:

```text
Monthly Revenue ($)
```

Bad:

```text
X
Y
```

---

# MODULE 9: TITLES

---

# Why Titles Matter

Titles provide context.

---

# Example

```python
plt.title(
    "Monthly Sales Report"
)
```

---

# Custom Title

```python
plt.title(
    "Monthly Sales Report",
    fontsize=18,
    fontweight='bold'
)
```

---

# Professional Formula

```text
Metric + Time Period + Context
```

Example:

```text
Quarterly Revenue Growth (2025)
```

---

# MODULE 10: TICKS

---

# What Are Ticks?

Ticks represent scale values.

---

# Example

```python
plt.xticks([1,2,3,4])
```

---

# Custom Labels

```python
plt.xticks(
    [1,2,3],
    ['Jan','Feb','Mar']
)
```

---

# Rotation

```python
plt.xticks(
    rotation=45
)
```

---

# Tick Size

```python
plt.tick_params(
    labelsize=12
)
```

---

# Why Important?

Improves readability.

---

# MODULE 11: ANNOTATIONS

---

# What Are Annotations?

Annotations highlight important points.

---

# Example

```python
plt.annotate(
    "Peak Sales",
    xy=(5,300)
)
```

---

# Full Example

```python
plt.annotate(
    "Highest Revenue",
    xy=(5,300),
    xytext=(3,350),
    arrowprops={
        'arrowstyle':'->'
    }
)
```

---

# Use Cases

### Business

Highlight:

- Revenue spikes
- Market crashes

---

### Research

Highlight:

- Critical observations

---

### Finance

Highlight:

- Stock highs/lows

---

# Professional Styling Example

```python
import matplotlib.pyplot as plt

months=["Jan","Feb","Mar","Apr","May"]
sales=[100,150,200,250,320]

plt.style.use('ggplot')

plt.figure(figsize=(8,5))

plt.plot(
    months,
    sales,
    color='blue',
    linewidth=3,
    marker='o',
    markersize=8,
    label='Sales'
)

plt.title(
    "Monthly Sales Report",
    fontsize=16
)

plt.xlabel("Month")
plt.ylabel("Sales")

plt.legend()

plt.grid(True)

plt.show()
```

---

# Common Mistakes

---

## Too Many Colors

Bad:

```text
Random rainbow charts
```

---

## Missing Labels

Bad:

```python
plt.plot(x,y)
```

---

## No Title

Users cannot understand context.

---

## Overusing Annotations

Creates clutter.

---

## Overlapping Legends

Makes charts unreadable.

---

# Best Practices

✅ Use color intentionally

✅ Use accessible palettes

✅ Use readable font sizes

✅ Add informative titles

✅ Use annotations sparingly

✅ Maintain consistency

✅ Prefer simple design

---

# Mini Project

## Personal Expense Dashboard

Create:

- Expense trends
- Category comparisons

Customize:

- Colors
- Markers
- Titles
- Legends

---

# Intermediate Project

## Sales Performance Dashboard

Features:

- Professional styling
- Custom legends
- Annotations
- Trend highlighting

---

# Advanced Project

## Financial Analytics Report

Create:

- Revenue analysis
- Profit trends
- Market performance

Apply publication-quality styling.

---

# Industry Project

## Executive KPI Dashboard

Visualize:

- Revenue
- Profit
- Customer Growth
- Retention

Using:

- Consistent theme
- Professional colors
- Annotations
- Custom labels

---

# Interview Questions

## Beginner

1. What are markers?
2. What are linestyles?
3. What is a legend?
4. Why use labels?
5. What are annotations?

---

## Intermediate

1. Difference between styles and themes?
2. What is a colormap?
3. Why use transparency?
4. How do legends improve readability?
5. When should annotations be used?

---

## Advanced

1. Explain sequential vs diverging colormaps.
2. How do colors influence perception?
3. What makes a visualization publication-quality?
4. How would you design an executive dashboard?
5. Explain accessibility considerations in chart design.

---

# Phase 5 Summary

You now understand:

✅ Colors

✅ Colormaps

✅ Styles

✅ Themes

✅ Markers

✅ Linestyles

✅ Legends

✅ Labels

✅ Titles

✅ Ticks

✅ Annotations

✅ Professional Styling Principles

✅ Dashboard Design Foundations

These customization techniques transform simple charts into professional-grade visualizations suitable for analytics, machine learning, research publications, executive reporting, and production dashboards.
