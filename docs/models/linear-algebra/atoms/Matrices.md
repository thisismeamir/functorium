---
sticker: lucide//atom
---
# Matrices: A Fundamental Representation

This document explains matrices, focusing solely on their structure and basic operations. We will *not* delve into linear transformations or vector spaces.  Think of a matrix as an organized arrangement of numbers.

## What is a Matrix?

A **matrix** is a rectangular array of numbers (real or complex) arranged in rows and columns. It's essentially a table of values.

$$
\begin{bmatrix}
a_{11} & a_{12} & \dots & a_{1n} \\
a_{21} & a_{22} & \dots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{m1} & a_{m2} & \dots & a_{mn}
\end{bmatrix}
$$

*   **Elements:** The individual numbers within the matrix are called **elements**.  Each element is identified by its row and column position. For example, `a<sub>ij</sub>` represents the element in the *i*-th row and *j*-th column.
*   **Rows:** A horizontal line of elements. In the above matrix, there are *m* rows.
*   **Columns:** A vertical line of elements.  In the above matrix, there are *n* columns.
*   **Dimensions/Size:** The dimensions of a matrix are described as *m x n*, where *m* is the number of rows and *n* is the number of columns. For example, a 3x2 matrix has 3 rows and 2 columns.

**Example Matrices:**

*   A 2x3 matrix:
    $$
    \begin{bmatrix}
    1 & 2 & 3 \\
    4 & 5 & 6
    \end{bmatrix}
    $$
*   A 3x3 matrix (also called a square matrix):
    $$
    \begin{bmatrix}
    7 & 8 & 9 \\
    10 & 11 & 12 \\
    13 & 14 & 15
    \end{bmatrix}
    $$
*   A 1x1 matrix:
    $$
    \begin{bmatrix}
    2
    \end{bmatrix}
    $$

## Matrix Operations

Here are some fundamental operations you can perform with matrices.  **Important:** For many of these operations, the dimensions of the matrices involved must be compatible (i.e., they have to "match" in a specific way).

### 1. Addition and Subtraction

To add or subtract two matrices, they *must* have the same dimensions (*m x n*).  You simply add or subtract corresponding elements.

$$
\begin{bmatrix}
a_{11} & a_{12} \\
a_{21} & a_{22}
\end{bmatrix} + \begin{bmatrix}
b_{11} & b_{12} \\
b_{21} & b_{22}
\end{bmatrix} = \begin{bmatrix}
a_{11}+b_{11} & a_{12}+b_{12} \\
a_{21}+b_{21} & a_{22}+b_{22}
\end{bmatrix}
$$

Similarly for subtraction:

$$
\begin{bmatrix}
a_{11} & a_{12} \\
a_{21} & a_{22}
\end{bmatrix} - \begin{bmatrix}
b_{11} & b_{12} \\
b_{21} & b_{22}
\end{bmatrix} = \begin{bmatrix}
a_{11}-b_{11} & a_{12}-b_{12} \\
a_{21}-b_{21} & a_{22}-b_{22}
\end{bmatrix}
$$

**Example:**

$$
\begin{bmatrix}
1 & 2 \\
3 & 4
\end{bmatrix} + \begin{bmatrix}
5 & 6 \\
7 & 8
\end{bmatrix} = \begin{bmatrix}
1+5 & 2+6 \\
3+7 & 4+8
\end{bmatrix} = \begin{bmatrix}
6 & 8 \\
10 & 12
\end{bmatrix}
$$

### 2. Scalar Multiplication

Scalar multiplication involves multiplying a matrix by a single number (a scalar).  You multiply each element of the matrix by that scalar.

$$
c \cdot \begin{bmatrix}
a_{11} & a_{12} \\
a_{21} & a_{22}
\end{bmatrix} = \begin{bmatrix}
c \cdot a_{11} & c \cdot a_{12} \\
c \cdot a_{21} & c \cdot a_{22}
\end{bmatrix}
$$

**Example:**

$$
3 \cdot \begin{bmatrix}
1 & 2 \\
3 & 4
\end{bmatrix} = \begin{bmatrix}
3 \cdot 1 & 3 \cdot 2 \\
3 \cdot 3 & 3 \cdot 4
\end{bmatrix} = \begin{bmatrix}
3 & 6 \\
9 & 12
\end{bmatrix}
$$

### 3. Matrix Multiplication

Matrix multiplication is more complex than addition or scalar multiplication.  To multiply matrix *A* (*m x n*) by matrix *B* (*p x q*), the number of columns in *A* must equal the number of rows in *B* (i.e., *n = p*). The resulting matrix will have dimensions *m x q*.

The element in the *i*-th row and *j*-th column of the product *AB* is calculated as follows:

$$
(AB)_{ij} = \sum_{k=1}^{n} a_{ik} b_{kj}
$$

This means you take the *i*-th row of *A*, multiply each element by the corresponding element in the *j*-th column of *B*, and then sum up those products.

**Example:**

Let  $A = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}$ and $B = \begin{bmatrix} 5 & 6 \\ 7 & 8 \end{bmatrix}$. Then:

$$
AB = \begin{bmatrix} (1\cdot5 + 2\cdot7) & (1\cdot6 + 2\cdot8) \\ (3\cdot5 + 4\cdot7) & (3\cdot6 + 4\cdot8) \end{bmatrix} = \begin{bmatrix} (5+14) & (6+16) \\ (15+28) & (18+32) \end{bmatrix} = \begin{bmatrix} 19 & 22 \\ 43 & 50 \end{bmatrix}
$$

**Important Note:** Matrix multiplication is *not* commutative.  In general, *AB ≠ BA*.

### 4. Transpose

The **transpose** of a matrix, denoted as *A<sup>T</sup>*, is obtained by interchanging its rows and columns. The element in the *i*-th row and *j*-th column of *A* becomes the element in the *j*-th row and *i*-th column of *A<sup>T</sup>*.

$$
\begin{bmatrix}
a_{11} & a_{12} \\
a_{21} & a_{22}
\end{bmatrix}^T = \begin{bmatrix}
a_{11} & a_{21} \\
a_{12} & a_{22}
\end{bmatrix}
$$

## Special Types of Matrices (Briefly)

*   **Square Matrix:**  Number of rows equals the number of columns (*m = n*).
*   **Row Matrix:** A matrix with only one row (*m = 1*).
*   **Column Matrix:** A matrix with only one column (*n = 1*).
*   **Identity Matrix (I):**  A square matrix with 1s on the main diagonal and 0s everywhere else. It acts as the multiplicative identity for matrices (AI = IA = A).
*   **Zero Matrix:** A matrix where all elements are zero.
