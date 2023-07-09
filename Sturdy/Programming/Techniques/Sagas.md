Sagas - mechanism used in microservice architecture in order to obtain data consistency.

# Problem
For instance:
You have two microservices with separate databases:
Customer service which uses customer database containing customer info and card balance and orders database which contains info about orders. 

However, we cannot consistently update both tables since we couldn't use transaction between two databases.

# Sagas' problem solution
Here where the sagas enters a game:
![[Pasted image 20230619011005.png]]

You design the transaction as a sequence of actions:
![[Pasted image 20230619011820.png]]

However Here comes a question: 
How to implement Rollbacks then?
The answer is that compensation transactions should be written for every sequence step: 
![[Pasted image 20230619012125.png]]

# Sequence organization
However, there should be a piece of code responsible for deciding which step should be next and organizes the sequence of saga transactions.

There are 2 popular models:
## Choreography
Choreography - distributed decision making
![[Pasted image 20230619014740.png]]
However this implementation leads to high coupling issues

## Orchestration
Orchestration - centralized decision making 
![[Pasted image 20230619014815.png]]
It is being considered as a Choreographycleaner approach
Orchestration realisation is just a bunch of state machines:
![[Pasted image 20230619014917.png]]

# Orchestration models

## Implicit Orchestration
![[Pasted image 20230619020514.png]]
Easier to implement when using [[Event Sourcing]]
But coordinating aggregate has overloaded responsibilities
So here comes another approach:

## Explicit Orchestration
![[Pasted image 20230619021059.png]]



Then in the end of saga processing when if we need to notify client or service about the fact that process has reached it final state we can make it using [[Polling]] 

