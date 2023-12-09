  

![Hessian matrix - Wikipedia](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTLDtVVg-muax0p0SLE-0PU-8YfqHTMwSmKVmupIprt5A&s)

In mathematics, the Hessian matrix, Hessian or (less commonly) Hesse matrix is a square matrix of second-order partial derivatives of a scalar-valued function, or scalar field. It **describes the local curvature of a function of many variables**.

![[Screen Shot 2023-09-27 at 01.07.24.png]]
Hij is symmetric only if:
Hij = Hji


# Hessian matrix's connection to function form:
- `f(x1, x2, ..., xn)` is [[convex function]] iff its `n*n` Hessian matrix is ==positive semidefinite== for all possible values  of `(x1, x2, ..., xn)`

- `f(x1, x2, ..., xn)` is not  [[convex function]] iff its `n*n` Hessian matrix is ==negative semidefinite== for all possible values  of `(x1, x2, ..., xn)`


Hessian matrix is ==positive semidefinite== if the scalar
$$ z^T * H * z $$
is ==non-negative== for every non-zero column vector z of n real numbers. 


Hessian matrix is ==negative semidefinite== if the scalar
$$ z^T * H * z $$
is ==negative== for every non-zero column vector z of n real numbers. 


Example:
Computing the Hessian matrix by taking the second derivative 
![[Pasted image 20230927012200.png]]
Checking if the `z^T * H * z` is positive or negative semidefinite and providing a conclusion about the function curve(it is [[convex function]])
![[Pasted image 20230927012114.png]]

