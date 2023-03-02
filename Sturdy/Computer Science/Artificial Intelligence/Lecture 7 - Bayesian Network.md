# <h1 style="text-align: center;">Representation</h1>

Using [Full joint Distribution] has problems such as:
- If there are many variables - hard to represent
- Hard to learn empirically(about more than few variables at a time)


Instead we may use [[Bayesian Net]]
![[Pasted image 20221103134608.png]]

In the simplest case, conditional distribution represented as a [conditional probability table] giving the distribution over Xi for each combination of parent values.

## Probabilities in [[Bayesian Net]]

BN **implicitly** encode joint distributions
- As a product of local conditional distributions
- To see what probability a BN gives to a full assignment, multiply all the relevant conditionals together:
![[Pasted image 20221103135616.png]]

### E.g. Conditional Independence and Chain Rule
Trivial decomposition:
- P(Traffic, Rain, Umbrella) = P(Rain) P(Traffic | Rain) P(Umbrella | Rain, Traffic)
With assumption of conditional Independence:
- P(Traffic, Rain, Umbrella) = P(Rain) P(Traffic | Rain) P(Umbrella | Rain)

### Example : Toothpaste, Catch, Cavity

![[Pasted image 20221103140327.png]]

- Weather is independent of the other variables
- Toothache and Catch are conditionally independent given Cavity

P(+cavity, +catch, -toothpaste) = P(+cavity) x P(+catch | +cavity) x P(-toothpaste | +cavity)
<br>
### Example: Alarm Network

- I’m at work, neighbor John calls to say my alarm is ringing, but neighbor Mary doesn’t call. Sometimes it’s set off by minor earthquakes. Is there a burglar?
- Variables: <span style="color:red;">Burglar, Earthquake, Alarm, JohnCalls, MaryCalls</span>
- Network topology reflects “causal” knowledge:
	- A burglar can set the alarm off
	- An earthquake can set the alarm off
	- The alarm can cause Mary to call
	- The alarm can cause John to call

![[Pasted image 20221103140851.png]]


## Compactness 

- A CPT for Boolean Xi with k Boolean parents has
	- 2^k rows for the combinations of parent values
	- Each row requires one number p for Xi = true (the number for Xi = false is just 1 - p)
- If each variable has no more than k parents, the complete network requires O(n · 2k) numbers
	- I.e., grows linearly with n, vs. O(2n) for the full joint distribution
- For alarm net:
	- 1 + 1 + 4 + 2 + 2 = 10 numbers (vs. 25 - 1 = 31)

## Global Semantics 
Global semantics defines the full joint distribution as the product of the local conditional distributions:
![[Pasted image 20221103141656.png]]

## Local Semantics
Local semantics: each node is conditionally independent of its nondescendants given its parents
![[Pasted image 20221103142055.png]]

## [[Markov Blanket]]

## Constructing Bayesian networks 
Need a method such that a series of locally testable assertions of conditional independence guarantees the required global semantics:
![[Pasted image 20221103142435.png]]


<br>
<br>

# <h1 style="text-align: center;">Exact inference</h1>
## Inference Tasks 
- [[Inference]]
- Optimal decisions: decision networks include utility information; 
	- probabilistic [[Inference]] required for P(outcome | action, evidence) 
- Simple queries: compute posterior marginal P(Xi | E = e) 
	- e.g., P(NoGas | Gauge = empty, Lights = on, Starts= false) 
- Conjunctive queries: P(Xi , Xj | E = e) = P(Xi | E = e) P(Xj | Xi , E = e)

## Inference By Enumeration
- Slightly intelligent way to sum out variables from the joint without actually constructing its explicit representation.
- Random variables: 
	- Evidence variables: E1 … Ek = e1 … ek
	- Query* variable: Q 
	- Hidden variables: H1 … Hm

### Steps
- select the entries consistent with the evidence.
- Sum out hidden variables H to get joint of Query and evidence
![[Pasted image 20221103143534.png]]
- Normalization
![[Pasted image 20221103143559.png]]

## Inference by Enumeration in Bayes’ Net
Given unlimited time, inference in Bayes Nets is easy
![[Pasted image 20221103143757.png]]

## Inference by Enumeration: Procedure
- Track objects called **factors**
- Initial factors are local CPTs (one per node)
- Select any know values
**Procedure**: Join all factors, eliminate all hidden variables, normalize
- Operation 1 - [[Joining Factors]]
- Operation 2 - marginalization or [[Elimination]]


## Inference by variable elimination
Inference by enumeration is slow because you join up the whole joint distribution before you sum out the hidden variables;

Solution: interleave joining and marginalizing!
- Called “Variable Elimination”
- Still NP-hard, but usually much faster than inference by enumeration
- Carry out summations right-to-left, storing intermediate results (factors) to avoid re-computation.

### Examples:
![[Pasted image 20221103145953.png]]
![[Pasted image 20221103150010.png]]


<br>
<br>

# <h1 style="text-align: center;">Sampling</h1>
**Sampling** - approximate Inference = repeated simulation 
E.g. predicting the weather, basketball games, ...

**Idea**:
- Draw N samples from a sampling distribution <span style="color:red;">S</span>
- Compute an approximate posterior probability <span style="color:red;">P</span>
- Show this converges to the true probability <span style="color:red;">P^</span>

<br>
<br>

# <h1 style="text-align: center;">Temporal Probability Models</h1>
