# Chapter 11 Reliability Engineering
Software reliability can be achieved by avoiding the introduction of faults, by detecting and removing faults before system deployment and by including fault tolerance facilities that allow the system to remain operational after a fault has caused a system failure.

Reliability requirements can be defined quantitatively in the system requirements specification.

Reliability metrics include probability of failure on demand (POFOD), rate of occurrence of failure (ROCOF) and availability (AVAIL).

Functional reliability requirements are requirements for system functionality, such as checking and redundancy requirements, which help the system meet its non-functional reliability requirements.

Dependable system architectures are system architectures that are designed for fault tolerance.

There are a number of architectural styles that support fault tolerance including protection systems, self-monitoring architectures and N-version programming

Software diversity is difficult to achieve because it is practically impossible to ensure that each version of the software is truly independent.

Dependable programming relies on including redundancy in a program as checks on the validity of inputs and the values of program variables.

Statistical testing is used to estimate software reliability. It relies on testing the system with test data that matches an operational profile, which reflects the distribution of inputs to the software when it is in use.


# Chapter 12 Safety Engineering
Hazard analysis involves identifying hazards and their root causes.

![[Pasted image 20221203020341.png]]

![[Pasted image 20221203020553.png]]

Safety engineering processes are based on reliability engineering processes

Regulators may require evidence that safety engineering processes have been used in system development
The specification of the system that has been developed and records of the checks made on that specification

## Agile and safety

Agile methods are not usually used for safety-critical systems engineering.

Process assurance involves defining a dependable process and ensuring that this process is followed during the system development.

Process assurance generates documentation
Agile processes therefore are rarely used for critical systems.

## Formal methods
²Formal methods can be used when a mathematical specification of the system is produced.

²They are the ultimate static verification technique that may be used at different stages in the development process:

Formal methods do not garantee safety:
I.e. The specification may not reflect desired requirements
Proofs may contain errors
proof may contain wrong argumentation

## Modal Checking
²Involves creating an extended finite state model of a system and, using a specialized system (a model checker), checking that model for errors.

²The model checker explores all possible paths through the model and checks that a user-specified property is valid for each path. 

²Model checking is particularly valuable for verifying concurrent systems, which are hard to test.

²Although model checking is computationally very expensive, it is now practical to use it in the verification of small to medium sized critical systems.

## Static analysis

Static analysis is an approach to V & V that examines the source code of a system, looking for errors and anomalies. It allows all parts of a program to be checked, not just those parts that are exercised by system tests
![[Pasted image 20221203021917.png]]

## Safety and Dependency cases
Safety and dependability cases are structured documents that set out detailed arguments and evidence that a required level of safety or dependability has been achieved.

# Chapter 13 Secutiry Engineering
## Secutiry Dimensions
- Confidentiality - accessibility of information by its authorization
- Integrity - info in system may be damaged or corrupted
- Availability - access to system may not be possible

![[Pasted image 20221203051941.png]]

## Threat types
- Interception threats that allow an attacker to gain access to an asset.
- The level of protection that is required for different types of asset
- The responsibilities of individual users, managers and the organization
- ruption threats that allow an attacker to make part of the system unavailable.
- Modification threats that allow an attacker to tamper with a system asset.
- Fabrication threats that allow an attacker to insert false information into a system.

**Resilience** is a system characteristic that reflects its ability to resist and recover from damaging events

## Security Policies
- The assets that must be protected
- The level of protection that is required for different types of asset
- The responsibilities of individual users, managers and the organization
- Existing security procedures and technologies that should be maintained


## Risk Management
- Preliminary risk assessment - identify generic risks
- Design risk assessment - changing secutiry requirements
- Operational risk assessment - focused on the use of the system


**Risk mitigation requirements** set out how the system should be designed so that it can recover from and restore system assets after some loss has occurred

Feasibility assessment - Assess the technical feasibility and cost of the controls(осуществимость)

Secutiry testing:
![[Pasted image 20221203053632.png]]


# Chapter 14 Resiling Engineering

The resilience of a system is a judgment of how well that system can maintain the continuity of its critical services in the presence of disruptive events, such as equipment failure and cyberattacks.

The idea that resilience is a judgment – there are no resilience metrics and resilience cannot be measured.

![[Pasted image 20221203054238.png]]

Resistance strategies may focus on isolating critical parts of the system so that they are unaffected by problems elsewhere

## CyberSecurity threats
- Threats to confidentiality of assets
- Threats to integrity of assets - data are managed
- Threats to availability of assets

Cyber Security resilence planning
- Asset Classification
- Threat Identification
- Threat Recognition
- Threat Resitance
- Asset Recovery
- Asset Reinstatement

Resilence Characteristics
- Ability to Respond(adapt processes in response to risk)
- Ability to Monitor
- Ability to Anticipate(предвидеть)
- Ability to learn

Swiss Chesse Model
Defensive layers has holes
Vulnerabilities are dynamic

Information provision
We should show people involved in processes a broader picture in order for them to have an ability to explain it.

Automation
System can detect problems, invoke cyberattack resistance if necessary and start automated recovery procedures.
But it may gone wrong and take incorrect actions.
Process automation can make it more difficult for people to cope with problems.

Resilient system design
- Identifying critical services and assets
- Designing system components that support problem recognition, resistance, recovery and reinstatement
- System understanding
- Critical service identification
- Attack simulation
- Survivability analysis

![[Pasted image 20221203060328.png]]


# Chapter 15 - Software ReUse

![[Pasted image 20221203061254.png]]

## Software Product Lines
Software product lines or application families are applications with generic functionality that can be adapted and configured for use in a specific context.

²A software product line is a set of applications with a common architecture and shared components, with each application specialized to reflect different requirements.

²Adaptation may involve:

- Component and system configuration;
- Adding new components to the system;
- Selecting from a library of existing components;
- Modifying components to meet new requirements.

![[Pasted image 20221203061650.png]]

![[Pasted image 20221203061708.png]]

COTS - Commercial off the shelf.

Integrated application systems are applications that include two or more application system products and/or legacy application systems. You may use this approach when there is no single application system that meets all of your needs or when you wish to integrate a new application system with systems that you already use.

A service-oriented approach means allowing access to the application system’s functionality through a standard service interface, with a service for each discrete unit of functionality.

# Chapter 16 - Component-based software engineering

Component-based software engineering - CBSE.
![[Pasted image 20221203063909.png]]

Components are accessed using **remote procedure calls** (RPCs).
Each component has a unique identifier (usually a URL) and can be referenced from any networked computer.
Therefore it can be called in a similar way as a procedure or method running on a local computer

![[Pasted image 20221203064144.png]]

To use services provided by a model, components are deployed in a **container**. This is a set of interfaces used to access the service implementations.

## Supporting processes
Component **acquisition** is the process of acquiring components for reuse or development into a reusable component.

![[Pasted image 20221203064727.png]]


## Types of component composition

- Sequential composition (1) where the composed components are executed in sequence. This involves composing the provides interfaces of each component.
- Hierarchical composition (2) where one component calls on the services of another component. The provides interface of one component is composed with the requires interface of another.
- Additive composition (3) where the interfaces of two components are put together to create a new component. Provides and requires interfaces of integrated component is a combination of interfaces of constituent components

The Object Constraint Language (OCL) has been designed to define constraints that are associated with UML models



# Chapter 17 - Distributed Software engineering

Information processing is distributed over several computers rather than confined to a single machine.

DS characteristics
- Resource Sharing
- Openness - Use of equipment and software from different vendors(Generally accepted standarts)
- Concurrency
- Scalability
- Fault tolerance

Transparency - To what extent should the distributed system appear to the user as a single system.

QoS - Quality of Service.

## Middleware
In a remote procedure call(RPC), one component calls another component as if it was a local procedure or method. The middleware in the system intercepts this call and passes it to a remote component.
Interaction support, where the middleware coordinates interactions between different components in the system

![[Pasted image 20221203070759.png]]

## Architectural Patterns
- **Master-slave** - The ‘master’ process is usually responsible for computation, coordination and communications and it controls the ‘slave’ processes. ‘Slave’ processes are dedicated to specific actions, such as the acquisition of data from an array of sensors.
- **two-tier client-server architecture** - the system is implemented as a single logical server plus an indefinite number of clients that use that server.
	- Thin-client model, where the presentation layer is implemented on the client and all other layers (data management, application processing and database) are implemented on a server.
	- Fat-client model, where some or all of the application processing is carried out on the client. Data management and database functions are implemented on the server.
- **multi-tier client–server architecture** - the different layers of the system, namely presentation, data management, application processing, and database, are separate processes that may execute on different processors.
![[Pasted image 20221203071330.png]]

## P2P architecture

![[Pasted image 20221203071720.png]]

P2P architectural models are usually decentralised or semi-centralised..

**Software as a Service** (SaaS) - involves hosting the software remotely and providing access to it over the Internet.
- Software is deployed on a server (or more commonly a number of servers) and is accessed through a web browser. It is not deployed on a local PC.
- The software is owned and managed by a software provider, rather than the organizations using the software.
- Users may pay for the software according to the amount of use they make of it or through an annual or monthly subscription

**Service-oriented** (SOA) architecture is an approach to structuring a software system as a set of separate, stateless services. These may be provided by multiple providers and may be distributed. Typically, transactions are short transactions where a service is called, does something then returns a result.


# Chapter 18 - Service-Oriented Software engineering

Web services standarts(old)
![[Pasted image 20221203073045.png]]

A critical distinction between a service and a component as defined in CBSE is that services are independent
- Services do not have a ‘requires’ interface
- Services rely on message-based communication with messages expressed in XML

Service interface in defined in WSDL.
What part of WSDL - service interface
How part of WSDL - binding that maps abstract interfaces to concrete protocols
Where part of WSDL - location of specific service(URL)

REST - Representational State Transfer.

![[Pasted image 20221203073816.png]]

## Three fundamental types of service
- Utility services that implement general functionality used by different business processes.
- Business services that are associated with a specific business function e.g., in a university, student registration.
- Coordination services that support composite processes such as ordering.
