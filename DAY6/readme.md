# PHASE 6: ADVANCED VISUALIZATION IN MATPLOTLIB

> Goal: Master advanced plotting techniques used in Data Science, Machine Learning, Scientific Research, Engineering Simulations, Quantitative Finance, and Professional Analytics Dashboards.

---

# Learning Outcomes

After completing this phase, you will be able to:

✅ Encode information using colors

✅ Use professional colormaps

✅ Create colorbars

✅ Control transparency

✅ Configure figure size

✅ Add annotations

✅ Build bubble charts

✅ Add reference lines

✅ Master Object-Oriented Matplotlib

✅ Create advanced subplot layouts

✅ Share axes across charts

✅ Design dashboard layouts

✅ Build 3D visualizations

✅ Create surface plots

✅ Generate contour visualizations

---

# VISUALIZATION HIERARCHY

```text
Figure
 │
 ├── Axes
 │     │
 │     ├── Scatter
 │     ├── Bubble
 │     ├── 3D Plot
 │     ├── Surface Plot
 │     ├── Contour Plot
 │     └── Annotations
 │
 └── Colorbars
```

---

# MODULE 1: COLOR ENCODING IN SCATTER PLOTS

---

# What Is It?

Color Encoding means representing a third variable using colors.

Normally:

```python
plt.scatter(x,y)
```

shows:

```text
X Position
Y Position
```

only.

With color encoding:

```python
plt.scatter(x,y,c=z)
```

shows:

```text
X Position
Y Position
Color Value
```

---

# Why Do We Need It?

Without Color Encoding:

```text
Only 2 dimensions visible
```

With Color Encoding:

```text
3 dimensions visible
```

---

# Real World Applications

### Data Science

```text
Age
Income
Spending Score
```

Color → Spending Score

---

### Healthcare

```text
Weight
Height
Risk Score
```

Color → Risk

---

### Finance

```text
Return
Risk
Volume
```

Color → Trading Volume

---

# Syntax

```python
plt.scatter(
    x,
    y,
    c=z,
    cmap='viridis'
)
```

---

# Parameter Breakdown

| Parameter | Purpose           |
| --------- | ----------------- |
| x         | Horizontal values |
| y         | Vertical values   |
| c         | Color values      |
| cmap      | Colormap          |
| alpha     | Transparency      |
| s         | Size              |

---

# Example

```python
import matplotlib.pyplot as plt
import numpy as np

x=np.random.rand(100)
y=np.random.rand(100)
z=np.random.rand(100)

plt.scatter(
    x,
    y,
    c=z,
    cmap='viridis'
)

plt.show()
```

---

# Output Analysis

```text
Bright Color
↓
High Value

Dark Color
↓
Low Value
```

---

# Common Mistakes

❌ Using categorical data with continuous colormap

❌ Forgetting colorbar

---

# MODULE 2: COLORMAPS (cmap)

---

# What Is A Colormap?

A Colormap converts numeric values into colors.

```text
Value
 ↓
Color Mapping
 ↓
Displayed Color
```

---

# Why Important?

Humans understand colors faster than numbers.

---

# Popular Colormaps

| Colormap | Type        |
| -------- | ----------- |
| viridis  | Sequential  |
| plasma   | Sequential  |
| inferno  | Sequential  |
| magma    | Sequential  |
| coolwarm | Diverging   |
| seismic  | Diverging   |
| tab10    | Categorical |

---

# Syntax

```python
cmap='viridis'
```

---

# Example

```python
plt.scatter(
    x,
    y,
    c=z,
    cmap='plasma'
)
```

---

# Sequential Colormaps

Used for:

```text
Low → High
```

Examples:

```python
viridis
plasma
inferno
magma
```

---

# Diverging Colormaps

Used for:

```text
Negative ↔ Positive
```

Examples:

```python
coolwarm
bwr
seismic
```

---

# Best Practices

Use:

```python
viridis
```

as default.

Avoid:

```python
jet
```

for professional work.

---

# MODULE 3: COLORBARS

---

# What Is A Colorbar?

Colorbar explains the meaning of colors.

Without colorbar:

```text
Color exists
Meaning unknown
```

With colorbar:

```text
Blue = Low
Yellow = High
```

---

# Syntax

```python
plt.colorbar()
```

---

# Example

```python
scatter=plt.scatter(
    x,
    y,
    c=z,
    cmap='viridis'
)

plt.colorbar(scatter)

plt.show()
```

---

# Why Important?

Color without explanation is useless.

---

# Industry Use Cases

- Heatmaps
- Scientific plots
- Satellite imagery
- Density analysis

---

# MODULE 4: TRANSPARENCY (ALPHA)

---

# What Is Alpha?

Controls transparency.

Range:

```python
0 → 1
```

---

# Meaning

| Value | Effect             |
| ----- | ------------------ |
| 0     | Invisible          |
| 0.25  | Mostly Transparent |
| 0.5   | Semi Transparent   |
| 1     | Fully Visible      |

---

# Syntax

```python
alpha=0.5
```

---

# Example

```python
plt.scatter(
    x,
    y,
    alpha=0.4
)
```

---

# Why Important?

Reduces overplotting.

---

# Data Science Use

Large datasets:

```python
100000 points
```

become readable.

---

# MODULE 5: FIGURE SIZE (figsize)

---

# What Is figsize?

Controls chart dimensions.

---

# Syntax

```python
plt.figure(
    figsize=(8,5)
)
```

---

# Interpretation

```python
width=8 inches
height=5 inches
```

---

# Common Sizes

| Size   | Usage         |
| ------ | ------------- |
| (6,4)  | Default       |
| (8,5)  | Reports       |
| (12,6) | Dashboards    |
| (16,9) | Presentations |

---

# Example

```python
plt.figure(
    figsize=(12,6)
)
```

---

# Best Practices

Use larger figures for:

- Dashboards
- Presentations
- Research Papers

---

# MODULE 6: TEXT ANNOTATIONS

---

# What Is Annotation?

Annotations explain important observations.

---

# Syntax

```python
plt.annotate(
    text,
    xy=(x,y)
)
```

---

# Example

```python
plt.annotate(
    "Peak Sales",
    xy=(5,300)
)
```

---

# Advanced Example

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

- Peak detection
- Business milestones
- Market crashes
- Research findings

---

# MODULE 7: BUBBLE CHARTS

---

# What Is A Bubble Chart?

Scatter Plot + Size Encoding

Represents:

```text
X
Y
Size
```

---

# Syntax

```python
plt.scatter(
    x,
    y,
    s=size
)
```

---

# Example

```python
plt.scatter(
    income,
    spending,
    s=population
)
```

---

# Applications

### Business

```text
Revenue
Profit
Market Share
```

Market Share → Bubble Size

---

### Healthcare

Patient Risk Visualization

---

# MODULE 8: HORIZONTAL & VERTICAL REFERENCE LINES

---

# Why Needed?

Highlight thresholds.

Examples:

```text
Target
Average
Limit
```

---

# Horizontal Line

```python
plt.axhline(
    y=100
)
```

---

# Vertical Line

```python
plt.axvline(
    x=10
)
```

---

# Example

```python
plt.axhline(
    y=200,
    color='red'
)
```

---

# Applications

- Sales targets
- Risk thresholds
- Manufacturing limits

---

# MODULE 9: OBJECT-ORIENTED MATPLOTLIB

---

# Why OO Approach?

Professional projects use:

```python
fig, ax = plt.subplots()
```

instead of:

```python
plt.plot()
```

---

# Architecture

```text
Figure
   ↓
Axes
   ↓
Plot
```

---

# Example

```python
fig, ax = plt.subplots()

ax.plot(x,y)

ax.set_title("Sales")
```

---

# Benefits

✅ Better organization

✅ Dashboards

✅ Multiple charts

✅ Enterprise projects

---

# MODULE 10: SUBPLOTS

---

# What Are Subplots?

Multiple plots inside one figure.

---

# Syntax

```python
fig, ax = plt.subplots(
    2,
    2
)
```

---

# Layout

```text
+------+------+
|Plot1 |Plot2 |
+------+------+
|Plot3 |Plot4 |
+------+------+
```

---

# Example

```python
fig, ax = plt.subplots(
    2,
    2
)

ax[0,0].plot(x,y)
```

---

# MODULE 11: SHARED AXES

---

# Why Share Axes?

Ensures consistent scaling.

---

# Syntax

```python
fig, ax = plt.subplots(
    2,
    1,
    sharex=True
)
```

---

# Benefits

- Easier comparison
- Cleaner layout

---

# Common Use

Financial dashboards.

---

# MODULE 12: MULTIPLE LAYOUTS

---

# Tight Layout

```python
plt.tight_layout()
```

Automatically adjusts spacing.

---

# Constrained Layout

```python
fig, ax = plt.subplots(
    constrained_layout=True
)
```

---

# GridSpec

Advanced layout control.

```python
from matplotlib.gridspec import GridSpec
```

---

# Dashboard Example

```text
+----------------+
| Main Chart     |
+-------+--------+
| A     | B      |
+-------+--------+
```

---

# MODULE 13: 3D SCATTER PLOTS

---

# Why 3D?

Visualize:

```text
X
Y
Z
```

---

# Syntax

```python
from mpl_toolkits.mplot3d import Axes3D
```

---

# Example

```python
fig=plt.figure()

ax=fig.add_subplot(
    111,
    projection='3d'
)

ax.scatter(
    x,
    y,
    z
)
```

---

# Applications

- Clustering
- Physics
- Simulation

---

# MODULE 14: 3D LINE PLOTS

---

# Example

```python
ax.plot3D(
    x,
    y,
    z
)
```

---

# Uses

- Particle trajectories
- Flight paths
- Scientific simulations

---

# MODULE 15: SURFACE PLOTS

---

# What Is A Surface Plot?

Represents a continuous 3D surface.

---

# Example

```python
ax.plot_surface(
    X,
    Y,
    Z
)
```

---

# Applications

- Terrain mapping
- Optimization landscapes
- Engineering simulations

---

# MODULE 16: MESHGRID

---

# What Is Meshgrid?

Creates coordinate matrices.

---

# Example

```python
X,Y=np.meshgrid(
    x,
    y
)
```

---

# Visualization

```text
X Matrix
Y Matrix
```

used for:

```text
Surface Plots
Contour Plots
Heatmaps
```

---

# MODULE 17: CONTOUR PLOTS

---

# What Is A Contour Plot?

2D representation of a 3D surface.

---

# Syntax

```python
plt.contour(
    X,
    Y,
    Z
)
```

---

# Example

```python
plt.contour(
    X,
    Y,
    Z,
    levels=20
)
```

---

# Applications

- Weather forecasting
- Geography
- Engineering

---

# MODULE 18: FILLED CONTOUR PLOTS

---

# What Is It?

Filled version of contour plot.

---

# Syntax

```python
plt.contourf(
    X,
    Y,
    Z
)
```

---

# Example

```python
plt.contourf(
    X,
    Y,
    Z,
    cmap='viridis'
)

plt.colorbar()
```

---

# Why Better?

Shows density more clearly.

---

# Common Mistakes

❌ Using wrong colormap

❌ Missing colorbar

❌ Ignoring figure size

❌ Overusing annotations

❌ Using pyplot in large projects

❌ Not sharing axes

❌ Creating unreadable 3D plots

---

# Best Practices

✅ Use Object-Oriented API

✅ Add colorbars

✅ Use perceptually uniform colormaps

✅ Control transparency

✅ Use annotations sparingly

✅ Share axes when comparing

✅ Use GridSpec for dashboards

✅ Label everything

---

# Interview Questions

## Beginner

1. What is a colormap?
2. What is alpha?
3. Why use colorbars?
4. What is figsize?
5. What is annotation?

---

## Intermediate

1. Scatter Plot vs Bubble Chart?
2. Why use OO Matplotlib?
3. What are shared axes?
4. What is Meshgrid?
5. What is a contour plot?

---

## Advanced

1. Explain Matplotlib rendering in 3D plots.
2. How does Meshgrid work internally?
3. Surface Plot vs Contour Plot?
4. Why is viridis preferred?
5. Explain color encoding principles.

---

# Phase 6 Summary

You now understand:

✅ Color Encoding

✅ Colormaps

✅ Colorbars

✅ Alpha Transparency

✅ Figure Size

✅ Text Annotations

✅ Bubble Charts

✅ Reference Lines

✅ Object-Oriented Matplotlib

✅ Subplots

✅ Shared Axes

✅ Multiple Layouts

✅ 3D Scatter Plots

✅ 3D Line Plots

✅ Surface Plots

✅ Meshgrid

✅ Contour Plots

✅ Filled Contour Plots

These concepts form the foundation of advanced analytics dashboards, scientific visualizations, machine learning visualizations, geospatial analysis, engineering simulations, and research-grade graphics.
