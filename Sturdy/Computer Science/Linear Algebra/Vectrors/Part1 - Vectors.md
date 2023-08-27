Vector - can be understood as a point in a D-dimensional space

![[Pasted image 20230822181017.png]]

```python
import scipy as sp 
import pylab as pl 
v = sp.array([[1.],[0.5]]) 
pl.plot([0,v[0]],[0,v[1]]) 
pl.xlim([-2,2]) 
pl.ylim([-2,2]) 
grid()
```

# Transposed vector
![[Pasted image 20230822181227.png]]
```python
v = sp.array([[1],[0.5]]) 
v.shape (2, 1) 
v.T.shape (1, 2)
```

# Vector Operations
![[Pasted image 20230822181443.png]]
```python
v = sp.array([[1.],[0.5]]) 
v * 2 array([[ 2.], [ 1.]])
```

## Vector summation 
vector from the same space can be added to each other
```
| v1 + w1 |
| v2 + w2 |
|    .    |
|    :    |
| vD + wD |
```

## Scalar (Inner)/dot Product
The scalar product computes the similarity between two vectors v and w
![[Pasted image 20230822182503.png]]
vTw is often called projecting w onto v It is called scalar product because its result is a scalar.
```python
v = sp.array([[1.],[0.5]]) 
u = v * 2 u.T.dot(v) 
array([[ 2.5]]) 
sp.inner(u.T,v.T) 
array([[ 2.5]])
```

## Outer product
The outer product takes two vectors and computes a matrix
![[Pasted image 20230822182945.png]]
```python
v = sp.array([[1.],[0.5]]) 
u = v * 2 u.dot(v.T) 
array([[ 2. , 1. ], [ 1. , 0.5]]) 
sp.outer(u.T,v.T) 
array([[ 2. , 1. ], [ 1. , 0.5]])
```


# Norm of a vector
Norm - magnitude/length of a vector

There are 2 ways of measuring the magnitude of the vector:
## **Euclidian Norm** (2-Norm)
![[Pasted image 20230822235153.png]]
## Properties of the norm
![[Pasted image 20230822235436.png]]
The p-norm ||v||p of a D-dimensional vector v is defined as
![[Pasted image 20230822183504.png]]
Euclidian Norm in python
```python
norm(v) 
# 1.1180339887498949 
sqrt((v**2).sum()) 
# 1.1180339887498949

```

## **The 1-Norm
![[Pasted image 20230823000228.png]]

![[Pasted image 20230823000235.png]]

# Unit vectors
Every vector v can be scaled to length 1 by
$$ v <- v/||v||$$
This is useful because after normalizing each vector to unit length, our vector similarity measure v >w has a standardized meaning. 
Just divide the vector by its scalar length(norm)

![[Pasted image 20230823000943.png]]

# Angle between vectors 
The scalar product of unit vectors is the **cosine of the angle between vectors** 
![[Pasted image 20230823001807.png]]

# Angles between vectors and correlation coefficients

The correlation coefficient between x and y is defined as
![[Pasted image 20230823002647.png]]

## Example
![[Pasted image 20230823002712.png]]

```python
N,g = 1000,.5 
x = randn(N,1) 
y = g*(x) + sqrt(1-g**2)*randn(N,1) 
corrcoef(x.T,y.T) 
#array([[ 1. , 0.48415337], [ 0.48415337, 1. ]])
x.T.dot(y)/(norm(x)*norm(y)) 
#array([[ 0.48459541]]) 
c = x.T.dot(y)/(norm(x)*norm(y)) 
figure(figsize=(5,5)) 
plot(x.T,y.T,’.’) 
title("r=%0.2f"%c) 
savefig(’cors-python.pdf’)

```

## Pythagorean Theorem
![[Pasted image 20230823003010.png]]

Vector types:
- **==Orthogonal==** - perpendicular vectors
- ==**Orthonormal**== - perpendicular unit vectors


## Important Inequalities
- [[Cauchy-Schwarz-Buniakowsky inequality]]
- [[Triangle inequality]]


# Axioms of Vector Operations
- Associativity of addition 
$$ u + (v + w) = (u + v)  + w $$
- Commutativity of addition
$$ v + w = w + v $$
- Distributivity of scaling
$$ a(v + w) = aw + av $$

