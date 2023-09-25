# Matrix Multiplication
![[Screen Shot 2023-09-06 at 23.23.43.png]]
```python
A = array([[1,3],[-2,5]]) 
B = array([[2,-1],[-4,2]]) 
A.dot(B) 
# array([[-10, 5], [-24, 12]])
```

# Row Reduced Form
## Example:
![[Screen Shot 2023-09-06 at 23.24.45.png]]
The [[Rank of the matrix]] A is 2
# Matrices as Linear Mappings
![[Screen Shot 2023-09-06 at 23.45.04.png]]![[Screen Shot 2023-09-06 at 23.47.17.png]]

# Axioms of Matrix Operations
## Associativity 
$$ A(BV) = (AB)C $$
## Distributivity 
$$ A(B + C) = AB + AC, (A + B)C = AC + BC $$
## No Commutativity!
$$ AB ≠ BA $$

# Matrix Norms
In analogy to the norm as a measure of vector length, we would like to have a measure of matrix volume. 

The most common matrix norm is the [[Frobenius Norm]].
```python
A = array([[1,3],[-2,5]]) 
norm(A,’fro’) 
# 6.2449979983983983
```

# Matrix Determinant
The determinant det(A) of a square matrix A ∈ RM×M characterizes the linear mapping of A:
- If det(A) = 0, then A is not [[Invertible matrix]]
- If |det(A)| > 1, A will increase the volume of the data
- If |det(A)| < 1, A will decrease the volume of the data
- If det(A) < 0, A will reverse the orientation of the data

The determinant for a square matrices A ∈ R^(2×2) is defined as:
det(A) = A11A22 − A12A21

```python
A = array([[1,3],[-2,5]]) 
det(A)
11.000000000000002
```


# Matrix Trace
The Trace of a Matrix is defined only for a Square Matrix. It is **sum of its diagonal elements from the upper left to lower right, of matrix**.