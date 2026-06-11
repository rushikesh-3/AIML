# 🚀 NumPy Broadcasting & Performance Optimization Notes

> Complete Notes on Broadcasting, Vectorization, Benchmarking, and NumPy Performance

---

# 📚 Table of Contents

1. Broadcasting

   * Scalar Broadcasting
   * Vector Broadcasting
   * Matrix Broadcasting
   * Row-wise Broadcasting
   * Column-wise Broadcasting
   * Shape Compatibility
   * Broadcasting Failures
   * Broadcasting in Machine Learning
   * Broadcasting in Computer Vision

2. Performance Optimization

   * Benchmarking
   * time.time()
   * timeit
   * Loop vs Vectorization
   * Why NumPy is Faster
   * Continuous Memory
   * Homogeneous Data
   * Optimized C Execution
   * Performance Mindset

---

# 1️⃣ Broadcasting

## What is Broadcasting?

Broadcasting is NumPy's mechanism that allows arithmetic operations between arrays of different shapes without explicitly copying data.

Instead of creating large temporary arrays, NumPy logically expands smaller arrays.

### Example

```python
import numpy as np

arr = np.array([1, 2, 3])

print(arr + 10)
```

Output:

```python
[11 12 13]
```

Here, scalar `10` is broadcasted to:

```python
[10 10 10]
```

---

# 2️⃣ Scalar Broadcasting

## Definition

A scalar value is automatically expanded to match the shape of an array.

### Example

```python
arr = np.array([1, 2, 3])

result = arr + 5

print(result)
```

Output:

```python
[6 7 8]
```

### Visualization

```text
[1 2 3]
+
    5

↓

[1 2 3]
+
[5 5 5]

↓

[6 7 8]
```

### Advantages

* Cleaner code
* No loops
* Faster execution

---

# 3️⃣ Vector Broadcasting

## Example

```python
A = np.array([[1,2,3],
              [4,5,6]])

B = np.array([10,20,30])

print(A + B)
```

Output:

```python
[[11 22 33]
 [14 25 36]]
```

### Visualization

```text
A Shape = (2,3)

[
 [1 2 3]
 [4 5 6]
]

B Shape = (3,)

[10 20 30]

Broadcasted To

[
 [10 20 30]
 [10 20 30]
]
```

---

# 4️⃣ Matrix Broadcasting

## Example

```python
A = np.array([[1,2],
              [3,4]])

B = np.array([[10,20],
              [30,40]])

print(A + B)
```

Output:

```python
[[11 22]
 [33 44]]
```

### Requirement

Both matrices must have compatible dimensions.

---

# 5️⃣ Row-wise Broadcasting

## Example

```python
matrix = np.array([
    [1,2,3],
    [4,5,6]
])

row = np.array([10,20,30])

print(matrix + row)
```

Output:

```python
[[11 22 33]
 [14 25 36]]
```

### Shape Analysis

```text
Matrix Shape = (2,3)

Row Shape = (3,)
```

NumPy expands row across all rows.

---

# 6️⃣ Column-wise Broadcasting

## Example

```python
matrix = np.array([
    [1,2,3],
    [4,5,6]
])

column = np.array([
    [10],
    [20]
])

print(matrix + column)
```

Output:

```python
[[11 12 13]
 [24 25 26]]
```

### Shape Analysis

```text
Matrix Shape = (2,3)

Column Shape = (2,1)
```

Broadcasted shape:

```text
(2,3)
```

---

# 7️⃣ Shape Compatibility

Two dimensions are compatible when:

```text
Dimension A == Dimension B
OR
One dimension is 1
```

### Example

Compatible

```text
(3,4)
(1,4)
```

Compatible

```text
(5,1)
(5,7)
```

Not Compatible

```text
(2,3)
(4,3)
```

---

# Broadcasting Rule

NumPy compares dimensions from right to left.

```text
(3,1)
(1,4)

↓

(3,4)
```

---

# 8️⃣ Broadcasting Failures

## Example

```python
A = np.array([[1,2,3]])
B = np.array([[1,2]])

print(A + B)
```

Output:

```python
ValueError:
operands could not be broadcast together
```

Reason:

```text
(1,3)

(1,2)

3 ≠ 2
```

Neither dimension equals 1.

---

# 9️⃣ Broadcasting in Machine Learning

Broadcasting is heavily used in ML.

---

## Feature Scaling

```python
X = np.array([
    [10,20],
    [30,40],
    [50,60]
])

mean = np.mean(X, axis=0)

X_centered = X - mean
```

### Why?

Subtract mean from every row.

No loops required.

---

## Standardization

```python
X_standardized = (X - mean) / std
```

Uses broadcasting twice.

---

## Neural Networks

Bias Addition

```python
Z = X @ W + b
```

Where:

```text
X Shape = (batch_size, features)

W Shape = (features, neurons)

b Shape = (neurons,)
```

Bias is broadcasted automatically.

---

# 🔟 Broadcasting in Computer Vision

Images are NumPy arrays.

---

## Brightness Adjustment

```python
image = image + 50
```

Broadcast scalar value.

---

## RGB Manipulation

```python
image = image * [1.2, 1.0, 0.8]
```

Adjust RGB channels.

---

## Normalization

```python
image = image / 255.0
```

Converts:

```text
0-255

↓

0-1
```

Used in Deep Learning.

---

# 1️⃣1️⃣ Benchmarking

## What is Benchmarking?

Benchmarking measures execution time and performance.

Used to compare:

* Loops
* Vectorization
* Algorithms

---

# 1️⃣2️⃣ time.time()

## Example

```python
import time

start = time.time()

sum(range(1000000))

end = time.time()

print(end - start)
```

Output:

```python
0.02 seconds
```

Approximate timing.

---

# 1️⃣3️⃣ timeit

More accurate.

```python
import timeit

execution_time = timeit.timeit(
    "sum(range(1000000))",
    number=100
)

print(execution_time)
```

Used for micro-benchmarks.

---

# 1️⃣4️⃣ Loop vs Vectorization

## Python Loop

```python
result = []

for i in range(len(arr)):
    result.append(arr[i] * 2)
```

---

## NumPy Vectorization

```python
result = arr * 2
```

### Advantages

* Cleaner
* Faster
* Less memory overhead

---

# Example Benchmark

```python
import numpy as np
import time

arr = np.arange(1000000)

start = time.time()

arr * 2

end = time.time()

print(end - start)
```

Typically much faster than loops.

---

# 1️⃣5️⃣ Why NumPy is Faster

Main reasons:

1. Continuous Memory
2. Homogeneous Data
3. Optimized C Code
4. Vectorization
5. Reduced Python Overhead

---

# 1️⃣6️⃣ Continuous Memory

Python List

```text
[1,2,3,4]
```

Memory:

```text
Pointer → Object
Pointer → Object
Pointer → Object
Pointer → Object
```

---

NumPy Array

```text
[1 2 3 4]
```

Memory:

```text
1000 → 1
1008 → 2
1016 → 3
1024 → 4
```

Stored continuously.

Benefits:

* Faster access
* Better CPU cache usage

---

# 1️⃣7️⃣ Homogeneous Data

Python List

```python
[1, "hello", 2.5]
```

Different data types.

---

NumPy Array

```python
[1,2,3,4]
```

Same data type.

Benefits:

* Predictable memory layout
* Faster processing

---

# 1️⃣8️⃣ Optimized C Execution

Python Loop

```python
for i in arr:
    total += i
```

Interpreter runs every iteration.

---

NumPy

```python
np.sum(arr)
```

Internally:

```text
Python
 ↓
Highly Optimized C
 ↓
Machine Code
```

Much faster.

---

# 1️⃣9️⃣ Performance Mindset

Always ask:

### Can I remove loops?

Use:

```python
Vectorization
Broadcasting
Built-in NumPy Functions
```

---

### Can I avoid copying data?

Prefer:

```python
Views
Broadcasting
In-place Operations
```

---

### Can I leverage NumPy internals?

Use:

```python
np.sum()
np.mean()
np.max()
np.min()
np.dot()
```

instead of manual loops.

---

# 🎯 Interview Questions

### Why is NumPy faster than Python Lists?

* Continuous memory
* Homogeneous data
* C implementation
* Vectorization

---

### What is Broadcasting?

Automatic expansion of smaller arrays to match larger arrays during operations.

---

### When does Broadcasting fail?

When dimensions are incompatible.

---

### Difference Between Row-wise and Column-wise Broadcasting?

Row-wise:

```text
(3,)
```

broadcast across rows.

Column-wise:

```text
(3,1)
```

broadcast across columns.

---

# 🧠 Quick Revision

```text
Scalar Broadcasting
      ↓
Vector Broadcasting
      ↓
Matrix Broadcasting
      ↓
Shape Compatibility
      ↓
Broadcasting Failures
      ↓
Machine Learning
      ↓
Computer Vision
      ↓
Benchmarking
      ↓
Vectorization
      ↓
Performance Optimization
```

---

# 📌 Key Takeaways

✅ Broadcasting removes explicit loops

✅ Broadcasting follows shape compatibility rules

✅ NumPy is fast because of continuous memory

✅ NumPy uses homogeneous data types

✅ Vectorization is faster than Python loops

✅ Most ML frameworks rely on broadcasting

✅ Benchmark before optimizing

✅ Use timeit for accurate performance measurement

✅ Think in arrays, not loops

⭐ Master Broadcasting and Vectorization to become an efficient Data Scientist, ML Engineer, and Python Developer.



# 🚀 Linear Algebra for Data Science & Machine Learning

> Complete Notes on Vectors, Matrices, Linear Transformations, and Machine Learning Applications

---

# 📚 Table of Contents

1. Vectors
2. Dot Product
3. Matrix Multiplication
4. Identity Matrix
5. Transpose
6. Determinant
7. Inverse
8. Rank
9. Eigenvalues & Eigenvectors
10. Solving Linear Equations
11. Linear Regression Intuition

---

# 1️⃣ Vectors

## What is a Vector?

A vector is an ordered collection of numbers representing magnitude and direction.

### Example

```python
import numpy as np

v = np.array([2, 4, 6])

print(v)
```

Output

```python
[2 4 6]
```

---

## Visualization

```text
v = [2, 4]

Y
↑
|
|      *
|    /
|  /
|/
+------------→ X
```

---

## Types of Vectors

### Row Vector

```python
[1 2 3]
```

Shape

```python
(3,)
```

---

### Column Vector

```python
[[1]
 [2]
 [3]]
```

Shape

```python
(3,1)
```

---

## Applications

* Machine Learning Features
* Computer Graphics
* Physics Simulations
* Neural Networks

---

# 2️⃣ Dot Product

## Definition

Measures similarity between two vectors.

### Formula

```text
A · B = Σ(Ai × Bi)
```

---

## Example

```python
import numpy as np

A = np.array([1,2,3])
B = np.array([4,5,6])

print(np.dot(A,B))
```

Output

```python
32
```

---

## Calculation

```text
(1×4)+(2×5)+(3×6)

4+10+18

32
```

---

## Geometric Interpretation

```text
A · B = |A||B|cosθ
```

---

### Special Cases

#### Same Direction

```text
cos(0°)=1
```

Maximum value.

---

#### Perpendicular

```text
cos(90°)=0
```

Dot Product = 0

---

## ML Applications

* Recommendation Systems
* Similarity Search
* Cosine Similarity
* NLP Embeddings

---

# 3️⃣ Matrix Multiplication

## Definition

Combines rows and columns.

### Rule

```text
(m × n)

×

(n × p)

=

(m × p)
```

---

## Example

```python
A = np.array([
    [1,2],
    [3,4]
])

B = np.array([
    [5,6],
    [7,8]
])

print(A @ B)
```

Output

```python
[[19 22]
 [43 50]]
```

---

## Calculation

```text
19 = (1×5)+(2×7)

22 = (1×6)+(2×8)

43 = (3×5)+(4×7)

50 = (3×6)+(4×8)
```

---

## ML Application

```text
Input
  ↓
Weights
  ↓
Predictions
```

Neural Networks rely heavily on matrix multiplication.

---

# 4️⃣ Identity Matrix

## Definition

Equivalent of number 1 for matrices.

### Example

```python
I = np.eye(3)

print(I)
```

Output

```python
[[1. 0. 0.]
 [0. 1. 0.]
 [0. 0. 1.]]
```

---

## Property

```text
A × I = A
```

---

## Example

```python
A = np.array([
    [1,2],
    [3,4]
])

I = np.eye(2)

print(A @ I)
```

Output

```python
[[1 2]
 [3 4]]
```

---

# 5️⃣ Transpose

## Definition

Rows become columns.

Columns become rows.

---

## Example

```python
A = np.array([
    [1,2,3],
    [4,5,6]
])

print(A.T)
```

Output

```python
[[1 4]
 [2 5]
 [3 6]]
```

---

## Visualization

```text
1 2 3
4 5 6

↓

1 4
2 5
3 6
```

---

## Applications

* Linear Regression
* Covariance Matrices
* Neural Networks

---

# 6️⃣ Determinant

## Definition

A scalar representing matrix scaling effect.

---

## Example

```python
A = np.array([
    [2,3],
    [1,4]
])

print(np.linalg.det(A))
```

Output

```python
5.0
```

---

## Formula

For 2×2 matrix

```text
|a b|
|c d|

det = ad − bc
```

---

## Interpretation

### Determinant = 0

Matrix is singular.

No inverse exists.

---

### Determinant ≠ 0

Inverse exists.

---

# 7️⃣ Inverse

## Definition

Matrix equivalent of reciprocal.

---

## Property

```text
A × A⁻¹ = I
```

---

## Example

```python
A = np.array([
    [4,7],
    [2,6]
])

print(np.linalg.inv(A))
```

---

## Verification

```python
print(A @ np.linalg.inv(A))
```

Output

```python
Identity Matrix
```

---

# 8️⃣ Rank

## Definition

Number of independent rows or columns.

---

## Example

```python
A = np.array([
    [1,2],
    [2,4]
])

print(np.linalg.matrix_rank(A))
```

Output

```python
1
```

---

## Why?

Row2 = 2 × Row1

No new information.

---

## Applications

* Feature Selection
* Detecting Redundancy
* Data Compression

---

# 9️⃣ Eigenvalues & Eigenvectors

## Definition

Special vectors whose direction remains unchanged after transformation.

---

## Formula

```text
Av = λv
```

Where

```text
A = Matrix

v = Eigenvector

λ = Eigenvalue
```

---

## Example

```python
A = np.array([
    [4,2],
    [1,3]
])

values, vectors = np.linalg.eig(A)

print(values)
print(vectors)
```

---

## Applications

### PCA

Principal Component Analysis

### Computer Vision

Face Recognition

### Recommendation Systems

Latent Factor Analysis

---

# 🔟 Solving Linear Equations

## System

```text
2x + y = 5

x + 3y = 6
```

---

## NumPy Solution

```python
A = np.array([
    [2,1],
    [1,3]
])

B = np.array([5,6])

solution = np.linalg.solve(A,B)

print(solution)
```

Output

```python
[1.8 1.4]
```

---

## Why Important?

Machine Learning is essentially solving large systems of equations.

---

# 1️⃣1️⃣ Linear Regression Intuition

## Goal

Find:

```text
y = mx + b
```

that best fits the data.

---

## Data

```text
Hours Studied

1 → 2

2 → 4

3 → 6

4 → 8
```

---

## Matrix Form

```text
Y = Xβ
```

Where

```text
Y = Target Values

X = Features

β = Parameters
```

---

## Normal Equation

```text
β = (XᵀX)⁻¹XᵀY
```

---

## NumPy Example

```python
X = np.array([
    [1,1],
    [1,2],
    [1,3],
    [1,4]
])

Y = np.array([
    2,4,6,8
])

beta = np.linalg.inv(
    X.T @ X
) @ X.T @ Y

print(beta)
```

---

## Why It Matters

Linear Regression combines:

✅ Vectors

✅ Dot Product

✅ Matrix Multiplication

✅ Transpose

✅ Inverse

All core Linear Algebra concepts.

---

# 🧠 Quick Revision Table

| Concept               | Key Idea                      |
| --------------------- | ----------------------------- |
| Vector                | Ordered collection of numbers |
| Dot Product           | Similarity between vectors    |
| Matrix Multiplication | Row × Column operation        |
| Identity Matrix       | Matrix version of 1           |
| Transpose             | Swap rows and columns         |
| Determinant           | Scaling factor                |
| Inverse               | Matrix reciprocal             |
| Rank                  | Independent information       |
| Eigenvalue            | Stretch factor                |
| Eigenvector           | Direction unchanged           |
| Linear Equations      | Solve unknown variables       |
| Linear Regression     | Best-fit line                 |

---

# 🎯 Interview Questions

### What is a Vector?

An ordered collection of numbers with magnitude and direction.

---

### What does Dot Product represent?

Similarity between vectors.

---

### Why must matrix dimensions match?

Inner dimensions must be equal.

```text
(m × n)

×

(n × p)
```

---

### When does a matrix have an inverse?

When:

```text
Determinant ≠ 0
```

---

### Why are Eigenvalues important in ML?

Used in PCA for dimensionality reduction.

---

### Why is Linear Algebra important in AI?

Because Machine Learning models are represented as matrix operations.

---

# 🚀 Key Takeaways

✅ Vectors represent data

✅ Dot Product measures similarity

✅ Matrix Multiplication powers neural networks

✅ Identity Matrix behaves like number 1

✅ Transpose swaps rows and columns

✅ Determinant tells invertibility

✅ Inverse solves systems

✅ Rank measures information

✅ Eigenvalues drive PCA

✅ Linear Regression combines all concepts

⭐ Master Linear Algebra to master Machine Learning, Deep Learning, Data Science, and AI.
