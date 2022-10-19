## Agents and environments
![[Pasted image 20221019234026.png]]

#Agent include humans, robots, softbots, thermostats, etc. 
The agent function maps from percept histories to actions:
$$ f : P ∗ → A $$
//Agents function maps from percept history to actions
The agent program runs on the physical **architecture** to produce f

<hr>

## Rationality
**Perfomance measure** evaluates the environment sequence
**Rational agent** chooses action that maximises the expected value of perfomance measure **given percept sequence to date**

<hr>

## PEAS
Perfomance Measure | Environment | Actuators | Sensors
To design a rational agent we must specify **Task Environment**

<hr>

## Environment Types
**Observable** - if agent has access to complete state of environment at each point of time
**Deterministic** - if agent knows the current state of environment and know what is the next move, it should know the outcome of the next step of environment
**Episodic** - it can be separated into multiple **independent** episodes(When one move don't affect another) 
**Static** - at the moment agent calculates the decision the environment stops
**Discrete** - separable, not continious
**Single-agent** - when there is only one agent

<hr>

## Agent Types
- Simple reflex agent
- Reflex agent with state
- Goal based agent
- Utility based agents 

All of them could be turned into learning agent

![[Pasted image 20221020000148.png]]

![[Pasted image 20221020000241.png]]

![[Pasted image 20221020000305.png]]

![[Pasted image 20221020000316.png]]

![[Pasted image 20221020000326.png]]

