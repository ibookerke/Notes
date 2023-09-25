SVD - singular value decomposition
[[Matrix diagonalization]] is fine, however it cannot be applied to rectangular matrices or to matrices with not enough [[Eigenvector]]s so here comes an SVD

- It can be computed for Any Matrix A
- it will provide 2 sets of [[Eigenvector]]s u's and v's
- ==u's== come from AA^T (row space of A)
- ==v's== come from A^TA (column space of A)

Why are we doing it? Because AA^T and A^TA are rectangular and [[Matrix diagonalization]] can be applied to it
![[Screen Shot 2023-09-19 at 20.53.11.png]]