# NumPy Day 3 Learning Notes (Shape, Dimensions, Memory & Vectorization Deep Dive)

## Overview

This document contains detailed notes on some of the most important NumPy concepts:

- Why NumPy Exists
- Array Creation
- 1D, 2D, and 3D Arrays
- ndim
- shape
- size
- Continuous Memory
- Homogeneous Data
- Vectorization
- Shape vs Size
- Shape vs Dimensions
- Difference Between (3,) and (3,1)
- Difference Between (1,3) and (3,1)
- Why Shape Errors Occur
- Shape in Machine Learning
- Shape in Images
- Shape in Deep Learning

Understanding these concepts is critical because almost every Machine Learning, Deep Learning, Computer Vision, and Data Science project relies heavily on array shapes.

---

# 1. Why NumPy Exists

## Theory

Python lists are flexible and easy to use, but they are not optimized for numerical computations.

Example:

```python
numbers = [10, 20, 30, 40]
```

Python stores each element as a separate Python object.

This leads to:

- More memory consumption
- Slower computations
- Poor performance on large datasets

---

## Problems with Python Lists

### Memory Overhead

Python stores:

```text
Value
Type Information
Reference Information
```

for every element.

Example:

```python
numbers = [1, 2, 3, 4]
```

Internally:

```text
Object1
Object2
Object3
Object4
```

Lots of memory is wasted.

---

### Slow Mathematical Operations

Adding 1 to every element:

```python
numbers = [1,2,3,4]

result = []

for num in numbers:
    result.append(num + 1)
```

Requires looping.

---

## How NumPy Solves This

NumPy stores:

```text
Same Data Type
Continuous Memory
Optimized C Code
```

Result:

- Faster computations
- Less memory usage
- Efficient mathematical operations

---

## Real World Importance

Libraries built on NumPy:

- Pandas
- Scikit-Learn
- TensorFlow
- PyTorch
- OpenCV
- SciPy

Learning NumPy means learning the foundation of the entire Data Science ecosystem.

---

# 2. Creating Arrays

## Theory

The core data structure in NumPy is the ndarray.

Array means:

```text
Collection of elements stored together
```

---

## Creating a 1D Array

```python
import numpy as np

arr = np.array([10, 20, 30, 40])

print(arr)
```

Output:

```text
[10 20 30 40]
```

---

## Creating a 2D Array

```python
arr = np.array([
    [1,2,3],
    [4,5,6]
])
```

Output:

```text
[[1 2 3]
 [4 5 6]]
```

---

## Creating a 3D Array

```python
arr = np.array([
    [[1,2],[3,4]],
    [[5,6],[7,8]]
])
```

Output:

```text
[[[1 2]
  [3 4]]

 [[5 6]
  [7 8]]]
```

---

# 3. Understanding Dimensions

## Theory

Dimensions tell us how many axes an array has.

Think of dimensions as directions.

---

## 1D Array

```python
arr = np.array([1,2,3])
```

Visualization:

```text
1 2 3
```

Only one direction.

Dimension:

```text
1
```

---

## 2D Array

```python
arr = np.array([
    [1,2,3],
    [4,5,6]
])
```

Visualization:

```text
1 2 3
4 5 6
```

Directions:

```text
Rows
Columns
```

Dimensions:

```text
2
```

---

## 3D Array

```python
arr = np.array([
 [[1,2],[3,4]],
 [[5,6],[7,8]]
])
```

Visualization:

```text
Layer 1
1 2
3 4

Layer 2
5 6
7 8
```

Directions:

```text
Layers
Rows
Columns
```

Dimensions:

```text
3
```

---

# 4. ndim

## Theory

`ndim` means:

```text
Number of Dimensions
```

---

## Syntax

```python
arr.ndim
```

---

## Examples

### 1D

```python
arr = np.array([1,2,3])

print(arr.ndim)
```

Output:

```text
1
```

---

### 2D

```python
arr = np.array([
 [1,2],
 [3,4]
])

print(arr.ndim)
```

Output:

```text
2
```

---

### 3D

```python
arr = np.array([
 [[1,2]],
 [[3,4]]
])

print(arr.ndim)
```

Output:

```text
3
```

---

# 5. Shape

## Theory

Shape describes how data is organized.

Shape answers:

```text
How many elements exist in each dimension?
```

---

## Syntax

```python
arr.shape
```

---

## Example

```python
arr = np.array([
 [1,2,3],
 [4,5,6]
])
```

Output:

```python
print(arr.shape)
```

```text
(2,3)
```

Meaning:

```text
2 rows
3 columns
```

---

# 6. What Shape Really Means

## Most Important Concept

Humans see:

```text
1 2 3
4 5 6
```

NumPy sees:

```text
1 2 3 4 5 6
```

stored continuously.

Shape tells NumPy how to reconstruct data.

---

## Example

Shape:

```text
(2,3)
```

Means:

```text
2 rows
3 columns
```

---

## Another Example

Shape:

```text
(3,2)
```

Means:

```text
3 rows
2 columns
```

Visualization:

```text
1 2
3 4
5 6
```

---

# 7. Shape of 1D Arrays

```python
arr = np.array([1,2,3])
```

Output:

```python
arr.shape
```

```text
(3,)
```

---

## Important Note

Many beginners think:

```text
(3,)
=
(1,3)
```

Wrong.

These are completely different.

---

# 8. Shape of 2D Arrays

```python
arr = np.array([
 [1,2,3],
 [4,5,6]
])
```

Output:

```text
(2,3)
```

Meaning:

```text
2 rows
3 columns
```

---

# 9. Shape of 3D Arrays

```python
arr = np.array([
 [[1,2],[3,4]],
 [[5,6],[7,8]]
])
```

Output:

```text
(2,2,2)
```

Meaning:

```text
2 layers
2 rows
2 columns
```

---

# 10. Size

## Theory

Size means:

```text
Total number of elements
```

---

## Formula

```text
Size = Product of Shape Values
```

---

## Example

Shape:

```text
(2,3)
```

Size:

```text
2 × 3 = 6
```

---

## Example

```python
arr.size
```

Output:

```text
6
```

---

# 11. Shape vs Size

| Shape | Size |
|---------|---------|
| Structure | Total Elements |
| (2,3) | 6 |
| (4,5) | 20 |

---

## Example

```python
arr.shape
```

Output:

```text
(2,3)
```

```python
arr.size
```

Output:

```text
6
```

---

# 12. Shape vs Dimensions

| Shape | Dimensions |
|---------|---------|
| Organization | Number of Axes |
| (2,3) | 2 |
| (2,2,2) | 3 |

---

Example:

```python
arr.shape
```

```text
(2,3)
```

```python
arr.ndim
```

```text
2
```

---

# 13. Difference Between (3,) and (3,1)

## Shape (3,)

```python
arr = np.array([1,2,3])
```

Output:

```text
(3,)
```

This is:

```text
1D Array
```

Visualization:

```text
[1 2 3]
```

---

## Shape (3,1)

```python
arr = np.array([
 [1],
 [2],
 [3]
])
```

Output:

```text
(3,1)
```

This is:

```text
2D Array
```

Visualization:

```text
1
2
3
```

---

## Why Important?

Machine Learning algorithms often require:

```text
(3,1)
```

instead of:

```text
(3,)
```

Using the wrong shape can cause errors.

---

# 14. Difference Between (1,3) and (3,1)

## Shape (1,3)

```text
1 Row
3 Columns
```

Visualization:

```text
1 2 3
```

---

## Shape (3,1)

```text
3 Rows
1 Column
```

Visualization:

```text
1
2
3
```

---

## Important Interview Question

Are these equal?

```text
(1,3)
=
(3,1)
```

Answer:

```text
No
```

They represent completely different structures.

---

# 15. Why Shape Errors Occur

## Theory

Shape errors happen when dimensions are incompatible.

---

## Example

```python
a = np.array([
 [1,2],
 [3,4]
])

b = np.array([
 [1,2,3]
])

a + b
```

Error:

```text
ValueError
```

---

## Why?

Shapes:

```text
a → (2,2)

b → (1,3)
```

Cannot align.

---

## Common Beginner Mistake

```python
X.shape
```

Output:

```text
(100,)
```

Model expects:

```text
(100,1)
```

Training fails.

---

# 16. Continuous Memory

## Theory

NumPy stores data in adjacent memory locations.

Example:

```text
1 → 2 → 3 → 4 → 5 → 6
```

instead of scattered memory.

---

## Benefits

- Faster access
- Better cache performance
- Efficient processing

---

# 17. Homogeneous Data

## Theory

NumPy arrays contain one data type.

Example:

```python
np.array([1,2,3])
```

All integers.

---

## Edge Case

```python
np.array([1,2.5,3])
```

Output:

```text
[1.  2.5 3.]
```

Notice:

```text
1 becomes 1.0
3 becomes 3.0
```

NumPy converts everything to float.

---

## Why?

Because arrays must have a single data type.

---

# 18. Vectorization

## Theory

Vectorization means performing operations on entire arrays without explicit loops.

---

## Traditional Python

```python
numbers = [1,2,3]

result = []

for x in numbers:
    result.append(x + 10)
```

Output:

```text
[11,12,13]
```

---

## NumPy Vectorization

```python
arr = np.array([1,2,3])

arr + 10
```

Output:

```text
[11 12 13]
```

---

## Advantages

- Faster
- Cleaner code
- Less memory overhead

---

# 19. Shape in Machine Learning

## Theory

Most ML algorithms expect:

```text
(rows, features)
```

Shape Format:

```text
(samples, features)
```

---

## Example

Dataset:

```text
Age  Salary
20   30000
25   50000
30   70000
```

Shape:

```text
(3,2)
```

Meaning:

```text
3 samples
2 features
```

---

# 20. Shape in Images

## Grayscale Image

Shape:

```text
(height, width)
```

Example:

```text
(28,28)
```

---

## RGB Image

Shape:

```text
(height, width, channels)
```

Example:

```text
(224,224,3)
```

Where:

```text
3 → Red, Green, Blue
```

---

# 21. Shape in Deep Learning

## Theory

Deep Learning models often use:

```text
(batch_size,
 height,
 width,
 channels)
```

---

## Example

```text
(32,224,224,3)
```

Meaning:

```text
32 Images
224 Height
224 Width
3 Channels
```

---

# Key Takeaways

After completing Day 3, I learned:

- Why NumPy exists.
- How arrays are created.
- Difference between 1D, 2D, and 3D arrays.
- Meaning of ndim.
- Meaning of shape.
- Meaning of size.
- Difference between shape and size.
- Difference between shape and dimensions.
- Difference between (3,), (3,1), and (1,3).
- Why shape errors occur.
- Continuous memory storage.
- Homogeneous data storage.
- Vectorization and its advantages.
- Shape requirements in Machine Learning.
- Shape requirements in Images and Deep Learning.

These concepts are the foundation of NumPy, Machine Learning, Deep Learning, Computer Vision, and Scientific Computing.