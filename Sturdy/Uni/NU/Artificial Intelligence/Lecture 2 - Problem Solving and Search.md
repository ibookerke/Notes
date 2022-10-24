## Problem types
- **Deterministic, fully observable** =⇒ single-state problem 
	- Agent knows exactly which state it will be in; solution is a sequence 
- **Non-observable** =⇒ conformant problem 
	- Agent may have no idea where it is; solution (if any) is a sequence 
- **Nondeterministic** and/or partially observable =⇒ contingency problem 
	- percepts provide new information about current state solution is a contingent plan or a policy often interleave search, execution 
- **Unknown state space** =⇒ exploration problem (“online”) (first action -> then analysis)

## Search Strategies
A stratefy is defined by picking  the order of **node expansion** 
E.g. [[BFS]], [[DFS]] and [[Uniform cost Search]].

Strategy is being evaluated by:
- completeness - if strategy always find some solution if one exists
- time complexity
- space complexity
- optimality - if stategy finds a least-cost solution

Time and space complexity are measured in terms of:
- b - max branching factor(max number of children)
- d - depth of least-cost solution
- m - max depth of state space(may be ∞)



