Generally the vector x changes direction when multiplied by A

However, there are some vectors x that are in the same direction as Ax:
$$ Ax = λx $$
-  These vectors x are known as eigenvectors
- λ is known as the [[Eigenvalue]] 
- λ can be any number, it scales x
- if A = I, Ax = x, i.e. all vectors are eigenvectors of I


Then given the [[Eigenvalue]] we can calculate the the eigenvectors :
For each λ solve (A - λI)x = 0 or Ax = λx to find the eigenvector x

## Finding [[Eigenvalue]]s and [[Eigenvector]]s

![[Screen Shot 2023-09-19 at 15.33.00.png]]

## Properties of [[Eigenvector]]s and [[eigenvalue]]s
![[Screen Shot 2023-09-19 at 15.36.52.png]]
Where [[Singular Matrix]] 

## [[Matrix Diagonalization]]
![[Screen Shot 2023-09-19 at 15.43.10.png]]
Where S^-1 - inverse of S

![[Screen Shot 2023-09-19 at 16.05.05.png]]
Where Ʌ - is a diagonal [[Eigenvalue]] matrix obtained from [[Matrix diagonalization]]
## Important Remarks
- if the [[Eigenvalue]]s λ1, λ2 ... λn are all different, then [[Eigenvector]]s x1, x2 ... xn are said to be [[Independent Vectors]]
- a matrix that has no repeated [[Eigenvalue]]s can be diagonalized
- [[Eigenvector]]s can be multiplied by any constant. An Ax = λx will remain true(often eigenvectors are normalizes to be unit vectors)
- the order of [[Eigenvector]]s in S corresponds to the order of [[Eigenvalue]]s in Ʌ
- some matrices have to few [[Eigenvector]]s so it cannot be diagonalized


![[Screen Shot 2023-09-19 at 16.17.38.png]]
![[Screen Shot 2023-09-19 at 16.19.36.png]]


## Symmetric matrices
1) A [[symmetric matrix]] has only **real [[eigenvalue]]s**
2) For [[Symmetric matrix]]es the [[eigenvector]]s can be chosen to be [[Orthonormal vectors]]
 

## Spectral theorem
![[Screen Shot 2023-09-19 at 19.20.54.png]] 
![[Screen Shot 2023-09-19 at 19.20.16.png]]
In the and we can observe the equation x^Tλ1y = x^Tλ2y, which should not make sense given that λ1 != λ2.

So in order for this equation to make sense X^Ty should be equal 0.
However scalar product of 2 vectors equals zero only if these vectors are orthogonal(perpendicular)


# Important notes
- [[pivot]]s are different from [[Eigenvalue]]s
- [[pivot]]s are derived by elimination while eigenvalues by solving det(A - λI) = 0
- However there is connection between them
- ==product of pivots = determinant of matrix = product of eigenvalues==
- [[Symmetric matrix]]es can always be diagonalized

For [[Symmetric matrix]] there is also another relation:
The number of positive [[Eigenvalue]]s is equal to a number of positive [[pivot]]s

For non-symmetric matrices:
If [[Eigenvalue]]s are repeated it can happen that there are not enough [[Eigenvector]]s to diagonalize the matrix


## [[Power method]] for [[Eigendecomposition]]
- this is how google estimates the pageRank
- it's also important for Principal Component Analysis

For [[Positive definite matrix]]
![[Screen Shot 2023-09-19 at 20.26.16.png]]
## Energy based definition
![[Screen Shot 2023-09-19 at 20.30.00.png]]

A is [[Positive definite matrix]] if x^TAx > 0 for every nonzero vector x:
$$ x^TAx > 0 $$
If the [[Eigenvalue]]s are positive then x^TAx > 0

There also such thing as 
### Positive Semidefinite matrix
which is quite similar to [[Positive definite matrix]] but 
- its smallest [[Eigenvalue]] = 0
![[Screen Shot 2023-09-19 at 20.40.18.png]]

