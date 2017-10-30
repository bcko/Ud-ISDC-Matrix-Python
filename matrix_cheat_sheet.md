
# Matrix Cheat Sheet
## Glossary
* **Scalar** - A scalar is just a number like 1.2, -5, 0, or 239. When we use the word **scalar** it's usually to highlight that we are *not* talking about a **vector** or a **matrix**. 
* **Matrix** - A matrix is a rectangular grid of numbers. For example, this is a matrix with  **2 rows** and **3 columns** so we would call it a $2\times 3$ "2 by 3" matrix.:

$$\begin{bmatrix}1.5 & -9.2 & 0 \\
5.4 & 7 & 2.2\end{bmatrix}$$

* **Row / Column** - These terms describe the horizontal (row) and vertical (column) sequences of numbers in a matrix. For example, the first row in the matrix above is $\begin{bmatrix}1.5 & -9.2 & 0\end{bmatrix}$.
* **Vector** - A vector is a matrix where either the width or the height is 1. When the height is 1, it's called a **row vector**. When the width is 1 it's called a **column vector**.

* **Matrix Element** - The **element** in the first row and first column of the matrix given above is the number $1.5$

* **Square Matrix** - A matrix is square when its height is equal to its width.
* **Main Diagonal** - The main diagonal of a **square matrix** is the sequence of **elements** from the top left to bottom right. For the matrix below the main diagonal refers to the numbers 2 and 6.

$$\begin{bmatrix}2 & 9 \\ -4 & 6 \end{bmatrix} $$
* **Identity Matrix** - This is a special **square matrix** where all of the **elements** are equal to zero except those on the **main diagonal**, which are equal to 1. This is a $3\times 3$ identity matrix:

$$\begin{bmatrix}1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1\end{bmatrix}$$


## Matrix Notation
### Indexing with $\mathbf{A}_{ij}$

The numbers $i$ and $j$ are used to refer to the row number and column number of a matrix (respectively). 

**NOTE**: The top left element of a matrix is typically given by $\mathbf{A}_{11}$ and **not** $\mathbf{A}_{00}$.**


```python
# python demo

A = [
    ["A_1,1", "A_1,2", "A_1,3"],
    ["A_2,1", "A_2,2", "A_2,3"],
    ["A_3,1", "A_3,2", "A_3,3"],
    ["A_4,1", "A_4,2", "A_4,3"],
]

print("the bottom right entry in the A matrix is:", A[3][2])
```

    ('the bottom right entry in the A matrix is:', 'A_4,3')


### Summation with $\sum$

Summation is best described by example. 

$$\sum_{i=1}^n a_{nn}$$

This equation can be read as "The sum from i equals one to n of the matrix element at row $n$, column $n$."

When you see $\sum$ you should think "for loop". The code below demonstrates the following mathematical equation:

$$\sum_{i=1}^n \sum_{j=1}^m a_{ij}$$


```python
def sum_all_matrix_elements(A):
    """
    Computes the sum of ALL elements in some matrix A.
    """
    n = len(A)
    m = len(A[0])
    total = 0.0
    for i in range(n):
        for j in range(m):
            total = total + A[i][j]
    return total

example_matrix = [
    [1, 3, 5],
    [4, 2, 2],
]

print(sum_all_matrix_elements(example_matrix))
```

    17.0


## Matrix Equations

### Addition / Subtraction
Matrix addition and subtraction is an element by element operation. Two matrices must have the same dimensions in order to be added or subtracted.

$$\mathbf{A} + \mathbf{B} = \begin{bmatrix}
a_{11} & a_{12}  & \dots  & a_{1n}\\ 
a_{21} & a_{22}  & \dots &a_{2n} \\ 
\vdots & \vdots & \ddots  & \vdots \\ 
a_{m1} & a_{m2}  & \dots  & a_{mn}
\end{bmatrix} + \begin{bmatrix}
b_{11} & b_{12}  & \dots  & b_{1n}\\ 
b_{21} & b_{22}  & \dots &b_{2n} \\ 
\vdots & \vdots  & \ddots  & \vdots \\ 
b_{m1} & b_{m2}  &  \dots & b_{mn}
\end{bmatrix}$$

$$= \begin{bmatrix}
a_{11}+b_{11} & a_{12}+b_{12}  & \dots  & a_{1n}+b_{1n}\\ 
a_{21}+b_{21} & a_{22}+b_{22}  & \dots & a_{2n}+b_{2n} \\ 
\vdots & \vdots  & \ddots  & \vdots \\ 
a_{m1}+b_{m1} & a_{m2}+b_{m2}  &  \dots & a_{mn}+b_{mn}
\end{bmatrix}$$

### Scalar Multiplication
When multiplying a matrix $\mathbf{A}$ by a scalar $c$, all of the entries in $\mathbf{A}$ are multiplied by $c$:

$$c\mathbf{A} = c \begin{bmatrix}a_{11} & a_{12}  & \dots  & a_{1n}\\ 
a_{21} & a_{22}  & \dots &a_{2n} \\ 
\vdots & \vdots & \ddots  & \vdots \\ 
a_{m1} & a_{m2}  & \dots  & a_{mn}
\end{bmatrix} = \begin{bmatrix} ca_{11} & ca_{12}  & \dots  & ca_{1n}\\ 
ca_{21} & ca_{22}  & \dots &ca_{2n} \\ 
\vdots & \vdots & \ddots  & \vdots \\ 
ca_{m1} & ca_{m2}  & \dots  & ca_{mn}\end{bmatrix}$$

### Matrix Multiplication
Multiplication of Matrix $\mathbf{A}$ with matrix $\mathbf{B}$ is only possible if the width of $\mathbf{A}$ is equal to the height of $\mathbf{B}$

If $\mathbf{A}$ is an $m \times n$ matrix and $\mathbf{B}$ is an $n \times p$ matrix, their product $\mathbf{AB}$ is an $m \times p$ matrix.

When multiplying two matrices, we can calculate the value of the element at row $i$ and column $j$ with the following equation:

$$(\mathbf{AB})_{ij} = \sum_{k=1}^n a_{ik}b_{kj}$$

### Transpose
The transpose of a matrix $\mathbf{A}$ is given by $\mathbf{A^T}$ and can be thought of in several ways:

* The **rows** of $\mathbf{A^T}$ are the **columns** of $\mathbf{A}$.
* The **columns** of $\mathbf{A^T}$ are the **rows** of $\mathbf{A}$.

Mathematically, the element at row $i$ and column $j$ of the transpose is given by:

$$[\mathbf{A^T}]_{ij} = [\mathbf{A}]_{ji}$$

### Trace
The trace of an $n\times n$ square matrix $\mathbf{A}$ is the sum of the elements on the **main diagonal** of the matrix. 

$$\text{tr}\left(\mathbf{A}\right) = \sum_{i=1}^n a_{ii} = a_{11} + a_{22} + \dots + a_{nn}$$

### Determinant
The determinant is a useful value when describing a matrix. It can be denoted in one of three ways:

1. $\text{det } \left(\mathbf{A}\right)$
2. $\text{det } \mathbf{A}$
3. $|\mathbf{A}|$

**1x1 Matrices**

The determinant of a $1\times1$ matrix is just the value of the matrice's only element. For example if $\mathbf{A} = \begin{vmatrix}4\end{vmatrix}$, then the determinant of $\mathbf{A}$ is given by:

$$\begin{vmatrix}\mathbf{A}\end{vmatrix} = 4$$

**2x2 Matrices**

The determinant of a $2\times2$ matrix is given by:

$$\begin{vmatrix}\mathbf{A}\end{vmatrix} = \begin{vmatrix}
a & b \\
c & d \end{vmatrix} = ad - bc
$$

**Larger Matrices**

You will not be required to calculate the determinant for larger matrices. If you are interested in learning more you should look at the Wikipedia article: [Determinant](https://en.wikipedia.org/wiki/Determinant).

### Inverse
The inverse of a matrix $\mathbf{A}$ is given by $\mathbf{A^{-1}}$

A matrix $\mathbf{A}$ is **invertible** if there exists a matrix $\mathbf{B}$ such that the product of $\mathbf{A}$ and $\mathbf{B}$ is the **identity matrix** $\mathbf{I}$:

$$\mathbf{AB} = \mathbf{BA} = \mathbf{I}$$

**1x1 Matrices**

For a $1\times1$ matrix with a single element with value $a$, the inverse is simlpy $\frac{1}{a}$

**2x2 Matrices**

The inverse of a $2\times 2$ matrix is given by the following equation:

$$\mathbf{A}^{-1} = \frac{1}{\text{det }\mathbf{A}} \left[\left(\text{tr } \mathbf{A}\right) \mathbf{I} - \mathbf{A}\right]$$


**Larger Matrices**

You will not be required to invert larger matrices. If you are interested in learning more you should look at the Wikipedia article [Invertible Matrix](https://en.wikipedia.org/wiki/Invertible_matrix).


```python

```
