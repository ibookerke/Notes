# Independence
![[Screen Shot 2023-09-06 at 19.36.53.png]]

x_1*v_1 + v_2*v_2 + ... + x_n*v_n = zero vector,  only happens when all x's are zero!

- Vectors are ==linearly independent== if no combination of them leads to zero vector
- Vector pairs are linearly independent if they are not parallel.

Example:
![[Screen Shot 2023-09-06 at 19.41.11.png]]
Since, any values of (e, f) will allow as to reach any values for a,b and c,d.  
 
Matrices example:
![[Screen Shot 2023-09-06 at 19.45.16.png]]

Two vectors v, w are linear dependent iff 
$$ v = aw $$
# Basis for a vector space

**The basis vectors are linearly independent and they span the space**
span - охватывать

The row space of A is C(A_T)
Where A_T - transpose of A
C(A_T) - column space of A_T

Example:
![[Screen Shot 2023-09-06 at 19.51.19.png]]

- 2 vectors cannot span all of R^3
- 4 vectors cannot be independent, even if they span R^3
- a basis has enough vectors to span the space and not more

# Testing Linear Independence
We can always check if the vectors are linear independence:
![[Screen Shot 2023-09-06 at 19.59.12.png]]
We can do this using [[Gaussian Elimination]]

# Orthogonality - Orthogonal Bases
![[Screen Shot 2023-09-06 at 20.06.14.png]]
This means that:
- every q has length 1
- every q is orthogonal to all other q's

If all columns of a matrix are orthonormal vectors, then it is denoted as ==Q== 
![[Screen Shot 2023-09-06 at 20.10.22.png]]
Where I - [[Identity matrix]]

# Orthogonal Matrix
![[Screen Shot 2023-09-06 at 20.17.19.png]]
- If Q is square it is known as a ==Orthogonal Matrix==
- every [[Permutation Matrix]] is an orthogonal matrix
- ||Qx|| = ||x|| does not change the length of vectors (makes intuitive sense, since the columns are all unit vectors..)


# [[Nullspace of matrix]]

Example:
![[Screen Shot 2023-09-06 at 20.26.46.png]]
- All columns of A have pivots
- A is [[Invertible matrix]]
- The Nullspace of A is Z

==Z - contains only zero vector x = 0==

## Some more Examples:
Let's imagine Matrix B
![[Screen Shot 2023-09-06 at 20.35.17.png]]
Ok now Imagine another matrix C
![[Screen Shot 2023-09-06 at 20.35.31.png]]![[Screen Shot 2023-09-06 at 20.36.13.png]]
## Final notes:
if there are more columns than rows (n > m) then there will be at least one [[free variable]]

# Important termins:
- 
- [[Echelon form]]
- [[Rank of the matrix]]
- Dimension of subspace - number of the vectors in a basis

# Dimensions of the Four Subspaces
- The **row space** is C(A^T), a subspace of R^n
- The **column space** is C(A), a subspace of R^m
- The **null space**([[Nullspace of matrix]]) is N(A), a subspace of R^m
- The **left nullspace** is N(A^T), a subspace of R^m

## Examples:
![[Screen Shot 2023-09-06 at 20.54.28.png]]
Where r - [[Rank of the matrix]]
![[Screen Shot 2023-09-06 at 21.00.23.png]]![[Screen Shot 2023-09-06 at 21.00.31.png]]
![[Screen Shot 2023-09-06 at 21.01.32.png]]
Note that the special solutions form a basis

![[Screen Shot 2023-09-06 at 21.02.52.png]]

![[Screen Shot 2023-09-06 at 21.05.26.png]]

