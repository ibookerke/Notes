
A rational decision depends on:
– the <span style="color:red;">relative importance</span> of various goals
– the <span style="color:red;">likelihood</span> they will be achieved 
– the <span style="color:red;">degree</span> to which they will be achieved


Degree of belief -> The agent cannot say whether a sentence is true, but only that is true x% of the times;

<hr>

**Probabillity Terms**:
**Ω** - sample space
**ω** ∈ Ω, where ω - sample point/possible world/atomic event
**Random variable** - function from sample points to some range. 
E.g. When rolling dies, the function Odd(x) will be showing if x is odd or not.
**P**() - probability distribution

**Base Terms:**
**Prior/Unconditional** probability - just prob of smth. like P(Rain) = 7/10;
**Probability Distribution** - gives values for all possible assignments
**Joint probability distribution** - specifies probability of every atomic event

**Random Variable Types:**
- **Propositional/Boolean**
	- E.g. Odd = true
- **Discrete**(finite or infinite)
	- E.g. Weather is one of <sunny, rain, cloudy, snow>
- **Continuous**(bounded or unbounded)
	- e.g. Temp < 22.0

<hr>

## Marginal Distribution
- Marginal distributions are sub-tables which eliminate variables
- Marginalization (summing out): Combine collapsed rows by adding

![[Pasted image 20221018204146.png]]
<hr>

## Conditional probability

Probability of a if b happened

![[Pasted image 20221018204316.png]]

**Conditional or #posterior distributions** are probability distributions over some variables given fixed values of others

<hr>

## Probabilistic Inference

Compute a desired probability from other known probabilities (e.g. conditional from joint)

### Inference By Enumeration

![[Pasted image 20221018205218.png]]

### Normalization

![[Pasted image 20221018225404.png]]


Denominator can be viewed as a <span style="color: red">normalization constant</span> - α

1. P(Cavity|Toothpaste) = α P(Cavity, Toothpaste) = 
	- Since there are 3 variables in distribution adding "Catch"
2.  = α ( P(Cavity, Toothpaste, Catch) + P(Cavity, Toothpaste, ¬Catch) ) = 
3.  = α ( <0.108, 0.016> + <0.012, 0.064> )
4.  = α ( 0.12, 0.08 )
	- Here comes the Normalization
	- Since the sum of the values should be equal to 1, so: α ( 0.12, 0.08 ) =  1
6.  = <0.6, 0.4>, where α = 1/(0.12 + 0.08) = 5

==General idea:== 
Compute distribution on #query variable by **fixing [[Evidence variable]]** and  **summing over** #hidden variables. 

Example: 
![[Pasted image 20221018231017.png]]


- Let X - be all the variables. Typically, we want the #posterior joint distribution of the #query variables  Y given specific values e for the [[Evidence variable]] E. 
- Let the #hidden variables be H = X - Y - E.
- Then the required summation of joint entries is done by summing out the hidden variables:
$$P(Y|E = e) = αP(Y, E = e) = Σ^a_hP(Y, E = e, H = h)$$

## Independece
A and B are independent iff:
**P(A|B)** = P(A) or P(B|A) = P(B) or P(A, B) = **P(A)P(B)**

### Conditional Independence
- If I have a cavity, the probability that the probe catches in it doesn’t depend on whether I have a toothache: 
- P(catch|toothache, cavity) = P(catch|cavity)
- The same independence holds if I haven’t got a cavity: 
- P(catch|toothache,¬cavity) = P(catch|¬cavity) 
- Catch is **conditionally independent** of Toothache given Cavity:
- P(Catch|Toothache, Cavity) = P(Catch|Cavity)


In most cases, the use of conditional independence reduces the size of the representation of the joint distribution from exponential in n to linear in n. 

Conditional independence is our most basic and robust form of knowledge about uncertain environments.


Bayes' Rule:
 ![[Pasted image 20221019003726.png]]
